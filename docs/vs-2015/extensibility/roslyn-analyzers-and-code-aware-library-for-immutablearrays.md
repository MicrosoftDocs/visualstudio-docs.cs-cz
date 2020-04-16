---
title: Analyzátory Roslyn a knihovna podporující kód pro immutablearrays | Dokumenty společnosti Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: 0b0afa22-3fca-4d59-908e-352464c1d903
caps.latest.revision: 6
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 65849a3d9ad1cdd073551f96e61997fe5f91118a
ms.sourcegitcommit: 7b60e81414a82c6d34f6de1a1f56115c9cd26943
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2020
ms.locfileid: "81444892"
---
# <a name="roslyn-analyzers-and-code-aware-library-for-immutablearrays"></a>Analyzátory Roslyn a knihovny rozlišující kódy pro řešení ImmutableArrays
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[Platforma kompilátoru .NET](https://github.com/dotnet/roslyn) ("Roslyn") vám pomůže vytvářet knihovny podporující kód. Knihovna s ohledem na kód poskytuje funkce, které můžete použít a nástroje (analyzátory Roslyn), které vám pomohou používat knihovnu nejlepším způsobem nebo aby se zabránilo chybám. Toto téma ukazuje, jak vytvořit analyzátor Roslyn v reálném světě zachytit běžné chyby při použití [balíčku NIB: Neměnné kolekce](https://msdn.microsoft.com/library/33f4449d-7078-450a-8d60-d9229f66bbca) NuGet. Příklad také ukazuje, jak poskytnout opravu kódu pro problém s kódem zjištěný analyzátorem. Uživatelům se zobrazí opravy kódu v uživatelském uživatelském nastavení žárovky sady Visual Studio a mohou použít opravu pro kód automaticky.

## <a name="getting-started"></a>začínáme
K sestavení tohoto příkladu potřebujete následující:

- Visual Studio 2015 (ne Express Edition) nebo novější verze. Můžete použít bezplatnou [verzi Visual Studio Community Edition](https://www.visualstudio.com/products/visual-studio-community-vs)

- [Sada Visual Studio SDK](../extensibility/visual-studio-sdk.md). Při instalaci sady Visual Studio můžete také zkontrolovat nástroje rozšiřitelnosti sady Visual Studio v části Běžné nástroje a nainstalovat sadu SDK současně. Pokud jste již nainstalovali visual studio, můžete také nainstalovat tuto sadu SDK přejdete do hlavní nabídky **Soubor &#124; New &#124;Project ...**, výběrem C# v levém navigačním podokně a pak zvolte rozšiřitelnost. Pokud zvolíte šablonu projektu navigace s popisem cesty aplikace**Visual Studio,** zobrazí se výzva ke stažení a instalaci sady SDK.

- [Platforma kompilátoru .NET ("Roslyn") SDK](https://marketplace.visualstudio.com/items?itemName=VisualStudioProductTeam.NETCompilerPlatformSDK). Tuto sadu SDK můžete nainstalovat také tak, že přejdete do hlavní nabídky **Soubor &#124; Nový &#124; project ...**, v levém navigačním podokně **zvolíte C#a** pak zvolíte **možnost Rozšiřitelnost**. Pokud zvolíte "Stáhnout šablonu projektu s dračenou drasi pomocí platformy **.NET Compiler Platform SDK**", zobrazí se výzva ke stažení a instalaci sady SDK. Tato sada SDK obsahuje [vizualizér syntaxe Roslyn](https://github.com/dotnet/roslyn/wiki/Syntax%20Visualizer). Tento velmi užitečný nástroj vám pomůže zjistit, jaké typy modelů kódu byste měli hledat v analyzátoru. Infrastruktura analyzátoru volá do vašeho kódu pro konkrétní typy modelů kódu, takže váš kód se spustí pouze v případě potřeby a může se soustředit pouze na analýzu příslušného kódu.

## <a name="whats-the-problem"></a>V čem je problém?
Představte si, že poskytujete knihovnu s <xref:System.Collections.Immutable.ImmutableArray%601?displayProperty=fullName>podporou ImmutableArray (například). Vývojáři jazyka C# mají mnoho zkušeností s poli .NET. Však vzhledem k povaze ImmutableArrays a optimalizační techniky používané v implementaci C# vývojář intuice způsobit uživatelům knihovny psát poškozený kód, jak je vysvětleno níže. Kromě toho uživatelé neuvidí jejich chyby až do běhu, což není kvalitní prostředí, které jsou zvyklí v sadě Visual Studio s .NET.

Uživatelé jsou obeznámeni s psaním kódu, jako je následující:

```csharp
var a1 = new int[0];
Console.WriteLine("a1.Length = { 0}", a1.Length);
var a2 = new int[] { 1, 2, 3, 4, 5 };
Console.WriteLine("a2.Length = { 0}", a2.Length);

```

Vytvoření prázdných polí k vyplnění s následujícířádky kódu a pomocí syntaxe inicializátoru kolekce jsou velmi známé vývojářům jazyka C#. Psaní stejného kódu pro ImmutableArray však dojde k chybě za běhu:

```csharp
var b1 = new ImmutableArray<int>();
Console.WriteLine("b1.Length = { 0}", b1.Length);
var b2 = new ImmutableArray<int> { 1, 2, 3, 4, 5 };
Console.WriteLine("b2.Length = { 0}", b2.Length);

```

První chyba je způsobena implementací ImmutableArray pomocí struktury k zabalení podkladového úložiště dat. Structs musí mít konstruktory `default(T)` bez parametrů, aby výrazy mohly vrátit struktury se všemi nulovými nebo nulovými členy. Při přístupu `b1.Length`kódu je chyba null dereference, protože v struktuře ImmutableArray neexistuje žádné základní pole úložiště. Správný způsob, jak vytvořit prázdný ImmutableArray je `ImmutableArray<int>.Empty`.

 K chybě s inicializátory kolekce dojde, protože metoda ImmutableArray.Add vrátí nové instance při každém volání. Protože ImmutableArrays nikdy změnit, při přidání nového prvku, získáte zpět nový objekt ImmutableArray (který může sdílet úložiště z důvodů výkonu s dříve existující ImmutableArray). Vzhledem k tomu, `b2` že odkazuje `Add()` na první `b2` ImmutableArray před voláním pětkrát, je výchozí ImmutableArray. Volání Length na něm také dojde k chybě s chybou null dereference. Správný způsob, jak inicializovat ImmutableArray bez ručního volání Add je použití `ImmutableArray.CreateRange(new int[] {1, 2, 3, 4, 5})`.

## <a name="finding-relevant-syntax-node-types-to-trigger-your-analyzer"></a>Hledání relevantních typů syntaktických uzlů pro aktivaci analyzátoru
Chcete-li začít stavět analyzátor, nejprve zjistěte, jaký typ SyntaxNode musíte hledat.   Spusťte vizualizaci syntaxe z nabídky **Zobrazit &#124; ostatní windows &#124; Roslyn Syntax Visualizer**.

Umístěte stříška editoru na řádek, `b1`který deklaruje . Zobrazí se syntaxvisualizer ukazuje, že `LocalDeclarationStatement` jste v uzlu stromu syntaxe. Tento uzel má `VariableDeclaration`, který zase `VariableDeclarator`má , který `EqualsValueClause`zase má , `ObjectCreationExpression`a nakonec je . Když kliknete do stromu syntaxe vizualizéru uzlů, syntaxe v okně editoru zvýrazní vám kód reprezentovaný tímto uzlem. Názvy podtypů SyntaxNode odpovídají názvům použitým v gramatice jazyka C#.

## <a name="creating-the-analyzer-project"></a>Vytvoření projektu analyzátoru
Z hlavní nabídky zvolte **Soubor &#124; Nový &#124; projekt ...**. V dialogovém okně **Nový projekt** v části Projekty **Jazyka C#** na levém navigačním panelu zvolte Rozšiřitelnost a v pravém podokně zvolte **Analyzátor s šablonou** projektu Oprava kódu. Zadejte název a potvrďte dialogové okno.

Šablona otevře soubor DiagnosticAnalyzer.cs. Zvolte tuto kartu vyrovnávací paměti editoru. Tento soubor má třídu analyzátoru (vytvořenou z názvu, `DiagnosticAnalyzer` který jste dali projektu), která je odvozena z (typ rozhraní API Roslyn). Vaše nová třída `DiagnosticAnalyzerAttribute` má deklarující analyzátor je relevantní pro jazyk C#tak, aby kompilátor zjistí a načte analyzátor.

```csharp
[DiagnosticAnalyzer(LanguageNames.CSharp)]
public class ImmutableArrayAnalyzerAnalyzer : DiagnosticAnalyzer
{}
```

Můžete implementovat analyzátor pomocí jazyka Visual Basic, který se zaměřuje na kód Jazyka C# a naopak. V atributu DiagnosticAnalyzerAttribute je důležitější zvolit, zda analyzátor cílí na jeden nebo oba. Sofistikovanější analyzátory, které vyžadují podrobné modelování jazyka může cílit pouze na jeden jazyk. Pokud váš analyzátor, například pouze kontroluje názvy typů nebo názvy veřejných členů, může být možné použít společný jazykový model Roslyn nabízí v rámci jazyka Visual Basic a C#. Například FxCop varuje, že <xref:System.Runtime.Serialization.ISerializable>třída implementuje , <xref:System.SerializableAttribute> ale třída nemá atribut je nezávislý na jazyku a funguje pro visual basic a c# kód.

## <a name="initalizing-the-analyzer"></a>Initalizace analyzátoru
Posuňte `DiagnosticAnalyzer` se trochu `Initialize` dolů ve třídě, abyste viděli metodu. Kompilátor volá tuto metodu při aktivaci analyzátoru. Metoda trvá `AnalysisContext` objekt, který umožňuje analyzátoru získat informace o kontextu a zaregistrovat zpětná volání pro události pro druhy kódu, který chcete analyzovat.

```csharp
public override void Initialize(AnalysisContext context) {}
```

Otevřete nový řádek v této metodě a zadejte "kontext". zobrazíte seznam dokončení aplikace Intellisense. Můžete vidět v seznamu dokončení `Register…` existuje mnoho metod pro zpracování různých druhů událostí. Například první , `RegisterCodeBlockAction`volá zpět do kódu pro blok, což je obvykle kód mezi složené závorky. Registrace pro blok také volá zpět do kódu pro inicializátor pole, hodnotu přiřazenou atributu nebo hodnotu volitelného parametru.

Jako další `RegisterCompilationStartAction`příklad , volá zpět do kódu na začátku kompilace, což je užitečné, když potřebujete shromažďovat stav na mnoha místech. Můžete vytvořit datovou strukturu, řekněme, shromažďovat všechny použité symboly, a pokaždé, když váš analyzátor je volán zpět pro některé syntaxe nebo symbol, můžete uložit informace o každé umístění ve vaší datové struktuře. Když jste voláni zpět z důvodu konce kompilace, můžete analyzovat všechna uložená místa, například `using` hlásit, jaké symboly kód používá z každého příkazu.

Pomocí **syntaxe Visualizer**, jste zjistili, že chcete být volána při kompilátoru zpracovává ObjectCreationExpression. Tento kód slouží k nastavení zpětného volání:

```csharp

context.RegisterSyntaxNodeAction(c => AnalyzeObjectCreation(c),
                                 SyntaxKind.ObjectCreationExpression);
```

Zaregistrujete se pro syntaktický uzel a filtrujete pouze syntaxe objektů. Podle konvence autoři analyzátoru používají lambda při registraci akcí, což pomáhá udržovat analyzátory bezstavové. `AnalyzeObjectCreation` Metodu můžete vytvořit pomocí funkce Visual Studio Generovat z **použití.** Tím se vygeneruje správný typ parametru kontextu pro vás příliš.

## <a name="setting-properties-for-users-of-your-analyzer"></a>Nastavení vlastností pro uživatele analyzátoru
Aby se analyzátor v yomu visual studia správně zosazuje, vyhledejte a upravte následující řádek kódu k identifikaci analyzátoru:

```csharp
internal const string Category = "Naming";
```

Změnit `"Naming"` `"API Guidance"`na .

Dále vyhledejte a otevřete soubor Resources.resx v projektu pomocí **Průzkumníka řešení**. Můžete vložit popis analyzátoru, titulu atd. Prozatím můžete změnit hodnotu všech `“Don’t use ImmutableArray<T> constructor”` těchto hodnot. Argumenty formátování řetězce můžete vložit do{0}řetězce {1}( , , atd.) a později při volání `Diagnostic.Create()`můžete zadat pole argumentů params, které mají být předány.

## <a name="analyzing-an-object-creation-expression"></a>Analýza výrazu pro vytvoření objektu
Metoda `AnalyzeObjectCreation` trvá jiný typ kontextu dodané rozhraní analyzátoru kódu. Metoda Initialize `AnalysisContext` umožňuje zaregistrovat zpětná volání akce pro nastavení analyzátoru. Například `SyntaxNodeAnalysisContext`, `CancellationToken` má, které můžete předat. Pokud uživatel začne psát v editoru, Roslyn zruší spuštění analyzátorů uložit práci a zlepšit výkon. Jako další příklad tento kontext má vlastnost Uzel, který vrací uzel syntaxe vytvoření objektu.

Získejte uzel, který můžete předpokládat, je typ, pro který jste filtrovali akce uzlu syntaxe:

```csharp
var objectCreation = (ObjectCreationExpressionSyntax)context.Node;
```

### <a name="launching-visual-studio-with-your-analyzer-the-first-time"></a>První spuštění sady Visual Studio s analyzátorem
Spuštění sady Visual Studio sestavením a spuštěním analyzátoru (stiskněte **klávesu F5).** Vzhledem k tomu, že projekt při spuštění v **Průzkumníku řešení** je projekt VSIX, spuštění kódu vytvoří váš kód a VSIX a spustí visual studio s nainstalovaným VSIX. Při spuštění sady Visual Studio tímto způsobem se spustí s podregistrem odlišné registru tak, aby hlavní použití sady Visual Studio nebude ovlivněna testovací instance při vytváření analyzátory. Při prvním spuštění tímto způsobem Visual Studio provádí několik inicializace podobné při prvním spuštění sady Visual Studio po instalaci.

 Vytvořte projekt konzoly a zadejte kód pole do konzolových aplikací Hlavní metoda:

```csharp
var b1 = new ImmutableArray<int>();
Console.WriteLine("b1.Length = {0}", b1.Length);
var b2 = new ImmutableArray<int> { 1, 2, 3, 4, 5 };
Console.WriteLine("b2.Length = {0}", b2.Length);

```

Řádky kódu s `ImmutableArray` mají vlnovky, protože je potřeba získat neměnné `using` NuGet balíček a přidat příkaz do kódu. Stiskněte pravé tlačítko ukazatele na uzlu projektu v **Průzkumníku řešení** a zvolte **Spravovat balíčky NuGet ...**. Ve správci NuGet zadejte do vyhledávacího pole příkaz Neměnné a v levém podokně zvolte položku "System.Collections.Immutable" (nezvolte možnost Microsoft.Bcl.Immutable) a stiskněte tlačítko Instalovat v pravém podokně. Instalace balíčku přidá odkaz na odkazy na projekt.

Stále vidíte červené vlnovky pod `ImmutableArray`, takže umístěte stříšku v tomto identifikátoru a stiskněte **kombinaci kláves CTRL+.** (období) vyvolat navrhovanou nabídku opravy a zvolit `using` přidání příslušného prohlášení.

**Uložit vše a zavřít** druhou instanci Sady Visual Studio pro tuto chvíli, aby vás v čistém stavu pokračovat.

## <a name="finishing-the-analyzer-using-edit-and-continue"></a>Dokončení analyzátoru pomocí úprav a pokračování
V první instanci sady Visual Studio nastavte zarážku na začátku `AnalyzeObjectCreation` metody stisknutím **klávesy F9** s stříška na prvním řádku.

Spusťte analyzátor znovu s **F5**a ve druhé instanci sady Visual Studio znovu otevřete konzolovou aplikaci, kterou jste vytvořili naposledy.

Vrátíte se k první instanci Sady Visual Studio na zarážky, protože kompilátor Roslyn viděl výraz vytvoření objektu a volána do analyzátoru.

**Získejte uzel vytváření objektů.** Krok přes řádek, `objectCreation` který nastaví proměnnou stisknutím **F10**a `“objectCreation.ToString()”`v bezprostřední **okno** vyhodnotit výraz . Uvidíte, že uzel syntaxe proměnná `"new ImmutableArray<int>()"`odkazuje na je kód , jen to, co hledáte.

**Získejte Objekt ImmutableArray\<T> Type.** Je třeba zkontrolovat, zda je vytvářený typ ImmutableArray. Nejprve získáte objekt, který představuje tento typ. Zkontrolujte typy pomocí sémantického modelu, abyste zajistili, že máte přesně správný typ a neporovnáváte řetězec z ToString(). Na konec funkce uveďte následující řádek kódu:

```csharp

var immutableArrayOfTType =
    context.SemanticModel
           .Compilation
           .GetTypeByMetadataName("System.Collections.Immutable.ImmutableArray`1");

```

Obecné typy v metadatech určíte pomocí zpětných nabídek (') a počtu obecných parametrů. To je důvod, proč nevidíte "... ImmutableArray\<T>" v názvu metadat.

Sémantický model má mnoho užitečných věcí, které vám umožní klást otázky o symbolech, toku dat, proměnné životnosti atd. Roslyn odděluje syntaktické uzly od sémantického modelu z různých technických důvodů (výkon, modelování chybného kódu atd.). Chcete, aby model kompilace vyhledat informace obsažené v odkazech pro přesné porovnání.

Můžete přetáhnout žlutý ukazatel spuštění na levé straně okna editoru. Přetáhněte ji na čáru, `objectCreation` která nastaví proměnnou a krok přes nový řádek kódu pomocí **F10**. Pokud najedete myší na proměnnou `immutableArrayOfType`, zjistíte, že jsme našli přesný typ v sémantickém modelu.

**Získejte typ výrazu vytvoření objektu.** "Typ" se používá několika způsoby v tomto článku, ale to znamená, že pokud máte výraz "new Foo", musíte získat model Foo. Musíte získat typ výrazu vytvoření objektu, abyste zjistili, zda\<se jedná o typ> ImmutableArray T. Znovu použijte sémantický model k získání informací o symbolu symbolu typu (ImmutableArray) ve výrazu pro vytvoření objektu. Na konec funkce uveďte následující řádek kódu:

```csharp
var symbolInfo = context.SemanticModel.GetSymbolInfo(objectCreation.Type) as INamedTypeSymbol;

```

Vzhledem k tomu, že analyzátor potřebuje zpracovat neúplný nebo nesprávný kód ve vyrovnávacích vyrovnávacích paměťech editoru (například chybí `using` příkaz), měli byste zkontrolovat, `symbolInfo` zda jsou `null`. Chcete-li dokončit analýzu, musíte získat pojmenovaný typ (INamedTypeSymbol) z informačního objektu symbolu.

**Porovnejte typy.** Vzhledem k tomu, že je otevřený obecný typ T, který hledáme, a typ v kódu je konkrétní obecný typ, dotaz informace o symbolu `immutableArrayOfTType`pro co typ je vytvořen z (otevřený obecný typ) a porovnat tento výsledek s . Na konci metody zadejte následující:

```csharp
if (symbolInfo != null &&
    symbolInfo.ConstructedFrom.Equals(immutableArrayOfTType))
{}
```

**Nahlaste diagnostiku.** Hlášení diagnostiky je docela snadné. Pravidlo vytvořené pro vás v šabloně projektu, která je definována před metodou Initialize. Vzhledem k tomu, že tato situace v kódu je chyba, můžete změnit řádek, který inicializoval pravidlo nahradit `DiagnosticSeverity.Warning` (zelená vlnovka) s `DiagnosticSeverity.Error` (červená vlnovka). Zbytek pravidla inicializuje ze zdrojů, které jste upravili v blízkosti začátku návodu. Je také nutné nahlásit umístění vlnovky, což je umístění specifikace typu expresssion vytvoření objektu. Zadejte tento `if` kód do bloku:

```csharp
context.ReportDiagnostic(Diagnostic.Create(Rule, objectCreation.Type.GetLocation()));
```

Vaše funkce by měla vypadat takto (možná formátován jinak):

```csharp
private void AnalyzeObjectCreation(SyntaxNodeAnalysisContext context)
{
    var objectCreation = (ObjectCreationExpressionSyntax)context.Node;
    var immutableArrayOfTType =
        context.SemanticModel
               .Compilation
               .GetTypeByMetadataName(
                   "System.Collections.Immutable.ImmutableArray`1");
    var symbolInfo = context.SemanticModel.GetSymbolInfo(objectCreation.Type) as
        INamedTypeSymbol;
    if (symbolInfo != null &&
        symbolInfo.ConstructedFrom.Equals(immutableArrayOfTType))
    {
        context.ReportDiagnostic(
            Diagnostic.Create(Rule, objectCreation.Type.GetLocation()));
    }
}

```

Odeberte zarážku, abyste viděli, že analyzátor funguje (a přestaňte se vracet k první instanci sady Visual Studio). Přetáhněte ukazatel spuštění na začátek metody a stisknutím **klávesy F5** pokračujte v provádění. Když přepnete zpět na druhou instanci sady Visual Studio, kompilátor začne znovu prozkoumat kód a bude volat do analyzátoru. Můžete vidět klikyháky `ImmutableType<int>`pod .

## <a name="adding-a-code-fix-for-the-code-issue"></a>Přidání "Oprava kódu" pro problém s kódem
Než začnete, zavřete druhou instanci sady Visual Studio a zastavte ladění v první instanci sady Visual Studio (kde vyvíjíte analyzátor).

**Přidejte novou třídu.** Použijte místní nabídku (pravé tlačítko ukazatele) v uzlu projektu v Průzkumníku řešení a zvolte přidání nové položky. Přidejte třídu s názvem `BuildCodeFixProvider`. Tato třída musí `CodeFixProvider`být odvozena z programu a budete muset použít **kombinaci kláves CTRL+.** (období) vyvolat opravu kódu, která `using` přidá správný příkaz. Tato třída také musí být anotována s atributem `ExportCodeFixProvider` `using` a budete `LanguageNames` muset přidat příkaz k vyřešení výčtu. Měli byste mít soubor třídy s následujícím kódem:

```csharp
using Microsoft.CodeAnalysis;
using Microsoft.CodeAnalysis.CodeFixes;

namespace ImmutableArrayAnalyzer
{
    [ExportCodeFixProvider(LanguageNames.CSharp)]
    class BuildCodeFixProvider : CodeFixProvider
    {}

```

**Stub z odvozených členů.** Nyní umístěte stříšku editoru `CodeFixProvider` do identifikátoru a stiskněte **kombinaci kláves CTRL+.** (period) se zakázaným inzerováním implementace pro tuto abstraktní základní třídu. Tím se vygeneruje vlastnost a metoda pro vás.

**Implementujte vlastnost.** Vyplňte `FixableDiagnosticIds` `get` tělo nemovitosti následujícím kódem:

```csharp
return ImmutableArray.Create(ImmutableArrayAnalyzerAnalyzer.DiagnosticId);
```

Roslyn sdružuje diagnostiku a opravy porovnáním těchto identifikátorů, které jsou pouze řetězce. Šablona projektu pro vás vygenerovala diagnostické ID a můžete jej změnit. Kód ve vlastnosti pouze vrátí ID z třídy analyzátoru.

**Metoda RegisterCodeFixAsync přebírá kontext.** Kontext je důležité, protože oprava kódu lze použít pro více diagnostiky nebo může být více než jeden problém na řádku kódu. Pokud zadáte "kontext". v těle metody, intellisense dokončení seznamu vám ukáže některé užitečné členy. Je CancellationToken člen, který můžete zkontrolovat, zda něco chce zrušit opravu. Je document člen, který má spoustu užitečných členů a umožňuje získat k objektům projektu a modelu řešení. Je span člen, který je začátek a konec umístění kódu zadané při oznamování diagnostiky.

**Proveďte metodu asynchronní.** První věc, kterou musíte udělat, je opravit deklaraci generované metody jako metodu. `async` Oprava kódu pro stubbing z implementace abstraktní třídy `async` neobsahuje klíčové slovo `Task`i v případě, že metoda vrátí .

**Získejte kořen stromu syntaxe.** Chcete-li upravit kód, musíte vytvořit nový strom syntaxe se změnami, které provede oprava kódu. Chcete-li `Document` volat , `GetSyntaxRootAsync`potřebujete z kontextu . Toto je asynchronní metoda, protože je neznámá práce získat strom syntaxe, případně včetně získání souboru z disku, jeho analýzu a vytváření modelu kódu Roslyn pro něj. Visual Studio UI by měla reagovat `async` během této doby, která pomocí umožňuje. Řádek kódu v metodě se nahradí následujícím:

```csharp
var root = await context.Document
                        .GetSyntaxRootAsync(context.CancellationToken);
```

**Najít uzel s problémem.** Předáte v rozsahu kontextu, ale uzel, který najdete nemusí být kód, který musíte změnit. Hlášená diagnostika poskytla pouze rozsah identifikátoru typu (kam patřila vlnovka), ale je třeba nahradit `new` celý výraz vytvoření objektu, včetně keywoard na začátku a závorky na konci. Přidejte do metody následující kód (a použijte **kombinaci kláves CTRL+.** přidáte `using` příkaz pro `ObjectCreationExpressionSyntax`):

```csharp

var objectCreation = root.FindNode(context.Span)
                         .FirstAncestorOrSelf<ObjectCreationExpressionSyntax>();
```

 **Zaregistrujte opravu kódu pro ui žárovky.** Při registraci opravy kódu roslyn připojí do visual studio žárovky ujzlíku automaticky. Koncoví uživatelé uvidí, že mohou používat **kombinaci kláves CTRL+.** (tečka), kdy váš analyzátor vlní špatné `ImmutableArray<T>` použití konstruktoru. Vzhledem k tomu, že zprostředkovatel opravy kódu se spustí pouze v případě, že došlo k problému, můžete předpokládat, že máte výraz vytvoření objektu, který jste hledali. Z parametru context můžete zaregistrovat novou opravu kódu přidáním `RegisterCodeFixAsync` následujícího kódu na konec metody:

```csharp

context.RegisterCodeFix(
            CodeAction.Create("Use ImmutableArray<T>.Empty",
                              c => ChangeToImmutableArrayEmpty(objectCreation,
                                                               context.Document,
                                                               c)),
            context.Diagnostics[0]);
```

Musíte umístit editors stříšku v `CodeAction`identifikátoru, , pak použijte **CTRL +.** (tečka) pro `using` přidání příslušného prohlášení pro tento typ.

Pak umístěte stříšku editoru do identifikátoru `ChangeToImmutableArrayEmpty` a použijte **kombinaci kláves CTRL+.** znovu generovat tuto metodu se zakázaným inzerováním pro vás.

Tento poslední fragment kódu, který jste přidali, `CodeAction` zaregistruje opravu kódu předáním a diagnostického ID pro druh nalezeného problému. V tomto příkladu existuje pouze jedno diagnostické ID, které tento kód poskytuje opravy, takže můžete předat první prvek pole id diagnostiky. Při vytváření `CodeAction`, předáte v textu, který by měl použít ui žárovky jako popis opravy kódu. Také předat funkci, která má CancellationToken a vrátí nový dokument. Nový dokument má nový strom syntaxe, který `ImmutableArray.Empty`obsahuje opravený kód, který volá . Tento fragment kódu používá lambda tak, aby jej můžete zavřít přes objektVytvoření uzlu a dokumentu kontextu.

**Vytvořte nový strom syntaxe.** Do `ChangeToImmutableArrayEmpty` metody, jejíž zástupný kód jste vygenerovali dříve, zadejte řádek kódu: `ImmutableArray<int>.Empty;`. Pokud znovu zobrazíte okno nástroje Vizualizace syntaxe, uvidíte, že tato syntaxe je uzel SimpleMemberAccessExpression. To je to, co tato metoda potřebuje k vytvoření a vrácení v novém dokumentu.

První změna `ChangeToImmutableArrayEmpty` je přidat `async` `Task<Document>` před, protože generátory kódu nelze předpokládat, že metoda by měla být asynchronní.

Vyplňte tělo s následujícím kódem tak, aby vaše metoda vypadá podobně jako následující:

```csharp

private async Task<Document> ChangeToImmutableArrayEmpty(
    ObjectCreationExpressionSyntax objectCreation, Document document,
    CancellationToken c)
{
    var generator = SyntaxGenerator.GetGenerator(document);
    var memberAccess =
        generator.MemberAccessExpression(objectCreation.Type, "Empty");
    var oldRoot = await document.GetSyntaxRootAsync(c);
    var newRoot = oldRoot.ReplaceNode(objectCreation, memberAccess);
    return document.WithSyntaxRoot(newRoot);
}
```

Budete muset dát editoru stříšky `SyntaxGenerator` v identifikátoru a používat **CTRL +.** (tečka) pro `using` přidání příslušného prohlášení pro tento typ.

Tento kód `SyntaxGenerator`používá , což je velmi užitečný typ pro vytváření nového kódu. Po získání generátoru pro dokument, který `ChangeToImmutableArrayEmpty` `MemberAccessExpression`má problém s kódem, volání , předání typu, který má člen chceme získat přístup a předání jméno člena jako řetězec.

Dále metoda načte kořen dokumentu a protože to může zahrnovat libovolnou práci v obecném případě, kód čeká na toto volání a předá token zrušení. Modely kódu Roslyn jsou neměnné, jako je práce s řetězcem .NET; při aktualizaci řetězce získáte nový objekt řetězce na oplátku. Při volání `ReplaceNode`získáte zpět nový kořenový uzel. Většina stromu syntaxe je sdílena (protože je `objectCreation` neměnný), `memberAccess` ale uzel je nahrazen uzlem, stejně jako všechny nadřazené uzly až do kořene kořene stromu syntaxe.

## <a name="trying-your-code-fix"></a>Pokus o opravu kódu
Nyní můžete stisknutím **klávesy F5** spustit analyzátor v druhé instanci sady Visual Studio. Otevřete projekt konzoly, který jste používali dříve. Nyní byste měli vidět žárovku se zobrazí, `ImmutableArray<int>`kde je nový výraz pro vytvoření objektu pro . Pokud stisknete **kombinaci kláves CTRL+.** (tečka), pak uvidíte opravu kódu a v uzdvižně vygenerovaném náhledu rozdílu kódu. Roslyn to pro tebe vytvořila.

Pro Tip: Pokud spustíte druhou instanci sady Visual Studio a nevidíte žárovku s opravou kódu, bude pravděpodobně nutné vymazat mezipaměť komponent sady Visual Studio. Vymazání mezipaměti vynutí Visual Studio znovu prozkoumat součásti, takže Visual Studio by pak měl vyzvednout nejnovější součásti. Nejprve vypněte druhou instanci sady Visual Studio. Potom v Průzkumníkovi Windows přejděte do adresáře uživatelů (c:\users\\<userid\>) a najděte AppData\Local\Microsoft\VisualStudio\14.0Roslyn\\. V tomto adresáři odstraňte dílčí adresář ComponentModelCache. "14" změní verzi na verzi s Visual Studio.

## <a name="talk-video-and-finish-code-project"></a>Projekt talk videa a konečného kódu
Můžete vidět tento příklad vyvinut a diskutovány dále v [této řeči](https://channel9.msdn.com/events/Build/2015/3-725). Diskuse demonstruje pracovní analyzátor a provede vás jeho stavbou.

Můžete vidět všechny hotové kód [zde](https://github.com/DustinCampbell/CoreFxAnalyzers/tree/master/Source/CoreFxAnalyzers). Podsložky DoNotUseImmutableArrayCollectionInitializer a DoNotUseImmutableArrayCtor mají soubor C# pro hledání problémů a soubor Jazyka C#, který implementuje opravy kódu, které se zobrazují v uzlech žárovky Visual Studio. Všimněte si, že hotový kód má trochu více abstrakce, aby se zabránilo načítání objektu typu ImmutableArray\<T> znovu a znovu. Používá vnořené registrované akce k uložení objektu typu v kontextu, který je k dispozici při každém spuštění dílčích akcí (analýza vytváření objektů a analýzy inicializace kolekce).

## <a name="see-also"></a>Viz také
[\\\Build 2015 talk](https://channel9.msdn.com/events/Build/2015/3-725)
[Dokončený kód na GitHubu](https://github.com/DustinCampbell/CoreFxAnalyzers/tree/master/Source/CoreFxAnalyzers) 
[Několik příkladů na GitHubu, seskupených do tří druhů analyzátorů](https://github.com/dotnet/roslyn/blob/master/docs/analyzers/Analyzer%20Samples.md) 
Další dokumenty na webu 
[GitHub OSS](https://github.com/dotnet/roslyn/tree/master/docs/analyzers)[FxCop implementována s analyzátory Roslyn na GitHubu](https://github.com/dotnet/roslyn/tree/master/src/Features/Core/Portable/Diagnostics/Analyzers)
