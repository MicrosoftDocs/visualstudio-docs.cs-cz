---
title: Analyzátory Roslyn a knihovna pro kódování kódu pro ImmutableArrays | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: 0b0afa22-3fca-4d59-908e-352464c1d903
caps.latest.revision: 6
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 65849a3d9ad1cdd073551f96e61997fe5f91118a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "81444892"
---
# <a name="roslyn-analyzers-and-code-aware-library-for-immutablearrays"></a>Analyzátory Roslyn a knihovny rozlišující kódy pro řešení ImmutableArrays
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[.NET Compiler Platform](https://github.com/dotnet/roslyn) ("Roslyn") pomáhá vytvářet knihovny podporující kód. Knihovna pro práci s kódem poskytuje funkce nástroje a nástrojů (Roslyn Analyzer), které vám pomůžou s používáním knihovny nejlepším způsobem nebo k tomu, aby se předešlo chybám. V tomto tématu se dozvíte, jak vytvořit Real World Roslyn Analyzer k zachycení běžných chyb při použití balíčku NuGet [NIB: unmutable Collections](https://msdn.microsoft.com/library/33f4449d-7078-450a-8d60-d9229f66bbca) . Příklad také ukazuje, jak poskytnout opravu kódu pro problém kódu nalezený analyzátorem. Uživatelé uvidí opravy kódu v uživatelském rozhraní žárovky aplikace Visual Studio a můžou automaticky použít opravu kódu.

## <a name="getting-started"></a>začínáme
K sestavení tohoto příkladu potřebujete následující:

- Visual Studio 2015 (ne Express Edition) nebo novější verze. Můžete použít bezplatnou [edici Visual Studio Community Edition](https://www.visualstudio.com/products/visual-studio-community-vs) .

- [Sada Visual Studio SDK](../extensibility/visual-studio-sdk.md). Při instalaci sady Visual Studio můžete také zaškrtnout Visual Studio Extensibility Tools v části společné nástroje pro instalaci sady SDK ve stejnou dobu. Pokud jste již nainstalovali sadu Visual Studio, můžete tuto sadu SDK nainstalovat také tak, že v levém navigačním podokně kliknete na soubor hlavní nabídky **&#124; nový &#124;projekt...**, vyberte C# a pak zvolte Rozšiřitelnost. Když vyberete šablonu projektu s popisem cesty "**nainstalovat Visual Studio Extensibility Tools**", zobrazí se výzva ke stažení a instalaci sady SDK.

- [.NET Compiler Platform ("Roslyn") SDK](https://marketplace.visualstudio.com/items?itemName=VisualStudioProductTeam.NETCompilerPlatformSDK). Tuto sadu SDK můžete nainstalovat také tak, že v levém navigačním podokně vyberete soubor hlavní nabídky **&#124; nový &#124; projekt...**, vyberte **C#** a pak zvolte **rozšiřitelnost**. Když vyberete možnost stáhnout šablonu projektu s popisem cesty **.NET COMPILER Platform SDK**, zobrazí se výzva ke stažení a instalaci sady SDK. Tato sada SDK zahrnuje [Roslyn syntax visualizer](https://github.com/dotnet/roslyn/wiki/Syntax%20Visualizer). Tento extrémně užitečný nástroj vám pomůže zjistit, jaké typy modelů kódu byste měli v analyzátoru najít. Infrastruktura analyzátoru volá do vašeho kódu pro konkrétní typy modelu kódu, takže váš kód se v případě potřeby spustí pouze v případě potřeby a může se zaměřit pouze na analýzu relevantního kódu.

## <a name="whats-the-problem"></a>Jaký je problém?
Představte si, že zadáváte knihovnu s podporou ImmutableArray (například <xref:System.Collections.Immutable.ImmutableArray%601?displayProperty=fullName> ). Vývojáři v jazyce C# mají spoustu zkušeností s poli .NET. Vzhledem k povaze ImmutableArrays a optimalizačních technik používaných v implementaci ale vývojář jazyka C# intuitions způsobí, že uživatelé vaší knihovny budou zapisovat poškozený kód, jak je vysvětleno níže. Kromě toho uživatelé nevidí své chyby, dokud neproběhne doba běhu, což není prostředí kvality, které se používá v aplikaci Visual Studio s .NET.

Uživatelé mají zkušenosti s psaním kódu podobného následujícímu:

```csharp
var a1 = new int[0];
Console.WriteLine("a1.Length = { 0}", a1.Length);
var a2 = new int[] { 1, 2, 3, 4, 5 };
Console.WriteLine("a2.Length = { 0}", a2.Length);

```

Vytváření prázdných polí pro vyplnění dalšími řádky kódu a používání syntaxe inicializátoru kolekce je velmi známé vývojářům v jazyce C#. Nicméně zápis stejného kódu pro ImmutableArray havárií za běhu:

```csharp
var b1 = new ImmutableArray<int>();
Console.WriteLine("b1.Length = { 0}", b1.Length);
var b2 = new ImmutableArray<int> { 1, 2, 3, 4, 5 };
Console.WriteLine("b2.Length = { 0}", b2.Length);

```

První chyba je způsobená implementací ImmutableArray k zabalení základního úložiště dat pomocí struktury. Struktury musí mít konstruktory bez parametrů, aby `default(T)` výrazy mohly vracet struktury se všemi nula nebo null členy. Při přístupu ke kódu dojde k `b1.Length` chybě při dereference hodnoty null doby běhu, protože v ImmutableArray struktuře neexistuje žádné podkladové pole úložiště. Správný způsob vytvoření prázdného ImmutableArray je `ImmutableArray<int>.Empty` .

 Chyba se inicializátory kolekce je způsobena tím, že metoda ImmutableArray. Add vrátí nové instance pokaždé, když ji zavoláte. Vzhledem k tomu, že se ImmutableArrays nikdy nemění, při přidání nového prvku se vrátí nový objekt ImmutableArray (který může sdílet úložiště z důvodů výkonu s dříve existující ImmutableArray). Protože `b2` odkazuje na první ImmutableArray před voláním `Add()` pětkrát, `b2` je výchozí ImmutableArray. Při volání délky dojde také k chybě s zpětným odkazem na hodnotu null. Správný způsob, jak inicializovat ImmutableArray bez ručního volání metody Add, je použít `ImmutableArray.CreateRange(new int[] {1, 2, 3, 4, 5})` .

## <a name="finding-relevant-syntax-node-types-to-trigger-your-analyzer"></a>Hledání relevantních typů uzlů syntaxe pro aktivaci vašeho analyzátoru
Chcete-li začít sestavovat analyzátor, nejprve nahlaste, jaký typ SyntaxNode je třeba vyhledat.   Spusťte Syntax Visualizer v nabídce **zobrazení &#124; další syntax visualizer Windows &#124; Roslyn**.

Umístěte blikající kurzor editoru na řádek, který deklaruje `b1` . Uvidíte, že Syntax Visualizer se zobrazí v `LocalDeclarationStatement` uzlu stromu syntaxe. Tento uzel má `VariableDeclaration` , který zase má a `VariableDeclarator` , který má `EqualsValueClause` a nakonec je `ObjectCreationExpression` . Po kliknutí na stromové struktuře Syntax Visualizer uzlů zobrazí syntaxe v okně editoru zvýraznění kódu reprezentovaného tímto uzlem. Názvy podtypů SyntaxNode odpovídají názvům používaným v gramatice jazyka C#.

## <a name="creating-the-analyzer-project"></a>Vytváření projektu analyzátoru
V hlavní nabídce vyberte **soubor &#124; nový &#124; projekt...**. V dialogovém okně **Nový projekt** v části projekty **C#** v levém navigačním panelu vyberte možnost rozšiřitelnost a v pravém podokně vyberte položku **analyzátor s opravou kódu** projektu šablona. Zadejte název a potvrďte dialog.

Šablona otevře soubor DiagnosticAnalyzer.cs. Vyberte tuto kartu vyrovnávací paměti editoru. Tento soubor obsahuje třídu analyzátoru (vytvořenou z názvu, který jste přiřadili projektu), který je odvozený od `DiagnosticAnalyzer` (typ rozhraní Roslyn API). Vaše nová třída má `DiagnosticAnalyzerAttribute` deklaraci vašeho analyzátoru, který je relevantní pro jazyk C#, aby kompilátor vyhledá a načte váš analyzátor.

```csharp
[DiagnosticAnalyzer(LanguageNames.CSharp)]
public class ImmutableArrayAnalyzerAnalyzer : DiagnosticAnalyzer
{}
```

Analyzátor můžete implementovat pomocí Visual Basic, která cílí na kód jazyka C# a naopak. V DiagnosticAnalyzerAttribute je důležitější, aby bylo možné zvolit, zda se analyzátor zaměřuje na jeden nebo oba jazyky. Propracovanější analyzátory, které vyžadují podrobné modelování jazyka, mohou být pouze zaměřeny na jeden jazyk. Pokud váš analyzátor například kontroluje pouze názvy typů nebo názvy veřejných členů, může být možné použít Roslyn a C# Visual Basic nabídky Common Language Model. Například FxCop upozorňuje, že třída implementuje <xref:System.Runtime.Serialization.ISerializable> , ale třída nemá <xref:System.SerializableAttribute> atribut je nezávislý na jazyce a funguje pro Visual Basic i kód jazyka C#.

## <a name="initalizing-the-analyzer"></a>Initalizing analyzátor
Posuňte se o něco dolů ve `DiagnosticAnalyzer` třídě, aby se zobrazila `Initialize` metoda. Kompilátor volá tuto metodu při aktivaci analyzátoru. Metoda přebírá `AnalysisContext` objekt, který umožňuje analyzátoru získat informace o kontextu a registrovat zpětná volání pro události pro typy kódu, který chcete analyzovat.

```csharp
public override void Initialize(AnalysisContext context) {}
```

V této metodě otevřete nový řádek a zadejte "Context". zobrazí se seznam pro doplňování technologie IntelliSense. V seznamu pro doplňování si můžete prohlédnout mnoho `Register…` metod, jak zpracovávat různé druhy událostí. Například první z nich `RegisterCodeBlockAction` volá zpět do kódu pro blok, který je obvykle kód mezi složenými závorkami. Registrace pro blok také volá zpět do kódu pro inicializátor pole, hodnotu poskytnutou atributu nebo hodnotu volitelného parametru.

Jako jiný příklad, `RegisterCompilationStartAction` volá zpět na váš kód na začátku kompilace, což je užitečné v případě, že potřebujete shromáždit stav v mnoha umístěních. Můžete vytvořit datovou strukturu, vyslovit ke shromáždění všech používaných symbolů a pokaždé, když je analyzátor volán zpět pro určitou syntaxi nebo symbol, můžete uložit informace o každém umístění v datové struktuře. Pokud jste volali zpět z důvodu ukončení kompilace, můžete analyzovat všechna umístění, která jste uložili, například k hlášení, které symboly používá kód z jednotlivých `using` příkazů.

Pomocí **syntax visualizer**jste zjistili, že chcete volat, když kompilátor zpracovává ObjectCreationExpression. Tento kód použijete k nastavení zpětného volání:

```csharp

context.RegisterSyntaxNodeAction(c => AnalyzeObjectCreation(c),
                                 SyntaxKind.ObjectCreationExpression);
```

Zaregistrujete se pro uzel syntaxe a filtr pouze pro uzly syntaxe pro vytvoření objektu. Podle úmluvy používají autoři analyzátoru lambda při registraci akcí, které pomáhají udržet bezstavové analyzátory. K vytvoření metody můžete použít funkci sady Visual Studio **generovanou z využití** `AnalyzeObjectCreation` . Tím se vygeneruje správný typ kontextového parametru.

## <a name="setting-properties-for-users-of-your-analyzer"></a>Nastavení vlastností pro uživatele analyzátoru
Aby se analyzátor zobrazil správně v uživatelském rozhraní sady Visual Studio, vyhledejte a upravte následující řádek kódu k identifikaci vašeho analyzátoru:

```csharp
internal const string Category = "Naming";
```

Změňte `"Naming"` na `"API Guidance"` .

Dále vyhledejte a otevřete v projektu soubor Resources. resx pomocí **Průzkumník řešení**. Můžete vložit popis pro svůj analyzátor, název atd. Můžete změnit hodnotu pro všechny z nich na `“Don’t use ImmutableArray<T> constructor”` nyní. Můžete vložit argumenty formátování řetězce do řetězce ( {0} , {1} atd.) a později při volání `Diagnostic.Create()` , můžete dodat pole parametrů argumentů, které mají být předány.

## <a name="analyzing-an-object-creation-expression"></a>Analýza výrazu pro vytvoření objektu
`AnalyzeObjectCreation`Metoda přebírá jiný typ kontextu dodaný rozhraním analyzátoru kódu. Metoda Initialize `AnalysisContext` umožňuje registrovat zpětná volání akcí pro nastavení analyzátoru. `SyntaxNodeAnalysisContext`Například má, `CancellationToken` který je možné předat. Pokud uživatel spustí psaní v editoru, Roslyn zruší spouštění analyzátorů, aby ušetřili práci a vylepšili výkon. V dalším příkladu má tento kontext vlastnost Node, která vrací uzel syntaxe pro vytvoření objektu.

Získejte uzel, který můžete předpokládat je typ, pro který jste vyfiltroval akci uzlu syntaxe:

```csharp
var objectCreation = (ObjectCreationExpressionSyntax)context.Node;
```

### <a name="launching-visual-studio-with-your-analyzer-the-first-time"></a>První spuštění sady Visual Studio s analyzátorem
Spusťte Visual Studio tak, že sestavíte a spustíte analyzátor (stisknete klávesu **F5**). Vzhledem k tomu, že spouštěcí projekt v **Průzkumník řešení** je projekt VSIX, spuštění kódu sestaví kód a VSIX a potom spustí aplikaci Visual Studio s nainstalovaným souborem VSIX. Při spuštění sady Visual Studio tímto způsobem se spustí s odlišným podregistrem, aby vaše vaše testovací instance během vytváření analyzátorů neovlivnila Vaše hlavní použití sady Visual Studio. Při prvním spuštění tímto způsobem provede aplikace Visual Studio několik inicializací, jako při prvním spuštění sady Visual Studio po její instalaci.

 Vytvořte projekt konzoly a potom zadejte kód pole do vaší hlavní metody konzolové aplikace:

```csharp
var b1 = new ImmutableArray<int>();
Console.WriteLine("b1.Length = {0}", b1.Length);
var b2 = new ImmutableArray<int> { 1, 2, 3, 4, 5 };
Console.WriteLine("b2.Length = {0}", b2.Length);

```

Řádky kódu s podtržením `ImmutableArray` jsou vlnovkou, protože potřebujete získat neproměnlivý balíček NuGet a přidat `using` příkaz do kódu. Stiskněte pravý ukazatel myši na uzlu projektu v **Průzkumník řešení** a zvolte možnost **Spravovat balíčky NuGet...**. Ve Správci NuGet zadejte do vyhledávacího pole "neměnný" a zvolte položku "System. Collections. unmutable" (nevybírejte "Microsoft. BCL. unmutable") v levém podokně a stiskněte tlačítko instalovat v pravém podokně. Při instalaci balíčku se přidá odkaz na odkazy na projekt.

V části se pořád zobrazují červené vlnovky `ImmutableArray` , takže umístěte blikající kurzor do tohoto identifikátoru a stiskněte **kombinaci kláves CTRL +.** (tečka) pro uvedení nabídky Navrhovaná oprava a zvolení přidání příslušného `using` příkazu.

**Uložte všechny a zavřete** druhou instanci sady Visual Studio, aby se teď do čistého stavu dalo pokračovat.

## <a name="finishing-the-analyzer-using-edit-and-continue"></a>Dokončení analyzátoru pomocí úpravy a pokračování
V první instanci sady Visual Studio nastavte zarážku na začátku vaší `AnalyzeObjectCreation` metody stisknutím klávesy **F9** se blikajícím kurzorem na prvním řádku.

Znovu spusťte analyzátor pomocí klávesy **F5**a ve druhé instanci aplikace Visual Studio znovu otevřete konzolovou aplikaci, kterou jste vytvořili naposledy.

Vrátíte se k první instanci sady Visual Studio na zarážce, protože kompilátor Roslyn viděl výraz pro vytvoření objektu a volal do vašeho analyzátoru.

**Získá uzel pro vytvoření objektu.** Krok za řádkem, který nastaví `objectCreation` proměnnou stisknutím klávesy **F10**a v **příkazovém podokně** se vyhodnotí výraz `“objectCreation.ToString()”` . Vidíte, že uzel syntaxe, na kterou proměnná odkazuje, je kód `"new ImmutableArray<int>()"` , přesně co hledáte.

**Získá \<T> objekt typu ImmutableArray.** Je nutné ověřit, zda je vytvořen typ ImmutableArray. Nejprve získáte objekt, který představuje tento typ. Zkontrolujte typy pomocí sémantického modelu, abyste měli jistotu, že máte přesně správný typ a řetězec neporovnat z metody ToString (). Na konci funkce zadejte následující řádek kódu:

```csharp

var immutableArrayOfTType =
    context.SemanticModel
           .Compilation
           .GetTypeByMetadataName("System.Collections.Immutable.ImmutableArray`1");

```

Určíte obecné typy v metadatech pomocí apostrofů (') a počtu obecných parametrů. Proto nevidíte "... ImmutableArray \<T> "v názvu metadat.

Sémantický model má mnoho užitečných věcí, které vám pomůžou klást otázky ke symbolům, toku dat, proměnlivé životnosti atd. Roslyn odděluje uzly syntaxe od sémantického modelu pro různé technické důvody (výkon, chybný kód modelování atd.). Chcete, aby model kompilace vyhledal informace obsažené v odkazech pro přesné porovnání.

Žlutý ukazatel spuštění lze přetáhnout na levou stranu okna editoru. Přetáhněte ji až na řádek, který nastaví `objectCreation` proměnnou a krok nad novým řádkem kódu pomocí nástroje **F10**. Pokud ukazatel myši najedete na proměnnou `immutableArrayOfType` , uvidíte, že jsme v sémantickém modelu našli přesný typ.

**Získá typ výrazu pro vytvoření objektu.** "Type" se používá v několika způsobech tohoto článku, ale to znamená, že pokud máte výraz "New foo", budete muset získat model foo. Musíte získat typ výrazu pro vytvoření objektu, abyste viděli, zda se jedná o \<T> typ ImmutableArray. Použijte znovu sémantický model a získejte informace o symbolech pro symbol typu (ImmutableArray) ve výrazu pro vytvoření objektu. Na konci funkce zadejte následující řádek kódu:

```csharp
var symbolInfo = context.SemanticModel.GetSymbolInfo(objectCreation.Type) as INamedTypeSymbol;

```

Vzhledem k tomu, že analyzátor potřebuje zpracovat neúplný nebo nesprávný kód v vyrovnávací paměti editoru (například chybí `using` příkaz), měli byste je kontrolovat `symbolInfo` `null` . K dokončení analýzy musíte získat pojmenovaný typ (INamedTypeSymbol) z objektu informací o symbolu.

**Porovnejte typy.** Vzhledem k tomu, že existuje otevřený obecný typ T, který hledáme, a typ v kódu je konkrétní obecný typ, vydáte dotaz na informace o tom, co je typ vytvořený (otevřený obecný typ), a porovnejte výsledek s `immutableArrayOfTType` . Zadejte následující na konci metody:

```csharp
if (symbolInfo != null &&
    symbolInfo.ConstructedFrom.Equals(immutableArrayOfTType))
{}
```

**Nahlaste diagnostiku.** Generování sestav diagnostiky je poměrně snadné. Použijete pravidlo vytvořené pro vás v šabloně projektu, která je definována před metodou Initialize. Vzhledem k tomu, že tato situace v kódu je chyba, můžete změnit řádek, který pravidlo inicializuje, aby nahradilo `DiagnosticSeverity.Warning` (zeleně vlnovkou) `DiagnosticSeverity.Error` (červená vlnovka). Zbytek pravidla inicializuje z prostředků, které jste upravili na začátku tohoto návodu. Také je nutné vykázat umístění pro vlnovkou, což je umístění specifikace typu pro vytvoření objektu možným návratovým. Zadejte tento kód do `if` bloku:

```csharp
context.ReportDiagnostic(Diagnostic.Create(Rule, objectCreation.Type.GetLocation()));
```

Funkce by měla vypadat takto (může se formátovat jinak):

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

Odeberte zarážku, abyste viděli, jak analyzátor funguje (a zastavil návrat na první instanci sady Visual Studio). Přetáhněte ukazatel spuštění na začátek metody a stisknutím klávesy **F5** pokračujte v provádění. Když přepnete zpět na druhou instanci aplikace Visual Studio, kompilátor spustí znovu kontrolu kódu a bude volat do vašeho analyzátoru. V části můžete vidět vlnovku `ImmutableType<int>` .

## <a name="adding-a-code-fix-for-the-code-issue"></a>Přidání "opravy kódu" pro problém s kódem
Než začnete, zavřete druhou instanci aplikace Visual Studio a ukončete ladění v první instanci sady Visual Studio (kde vyvíjíte analyzátor).

**Přidejte novou třídu.** Použijte místní nabídku (pravé tlačítko myši) na uzlu projektu v Průzkumník řešení a vyberte možnost Přidat novou položku. Přidejte třídu s názvem `BuildCodeFixProvider` . Tato třída musí být odvozena od `CodeFixProvider` a bude nutné použít **kombinaci kláves CTRL +.** (period) k vyvolání opravy kódu, která přidá správný `using` příkaz. Tato třída také musí být opatřena poznámkou s `ExportCodeFixProvider` atributem a budete muset přidat `using` příkaz pro vyřešení `LanguageNames` výčtu. Měli byste mít soubor třídy, který obsahuje následující kód:

```csharp
using Microsoft.CodeAnalysis;
using Microsoft.CodeAnalysis.CodeFixes;

namespace ImmutableArrayAnalyzer
{
    [ExportCodeFixProvider(LanguageNames.CSharp)]
    class BuildCodeFixProvider : CodeFixProvider
    {}

```

**Odvozené odvozené členy** Nyní umístěte blikající kurzor editoru do identifikátoru `CodeFixProvider` a stiskněte klávesovou **zkratku CTRL +.** (period) pro zástupnou proceduru pro implementaci této abstraktní základní třídy. Tím se vygeneruje vlastnost a metoda pro vás.

**Implementujte vlastnost.** Do `FixableDiagnosticIds` těla vlastnosti zadejte `get` následující kód:

```csharp
return ImmutableArray.Create(ImmutableArrayAnalyzerAnalyzer.DiagnosticId);
```

Roslyn spojuje diagnostiku a opravy porovnáním těchto identifikátorů, což jsou pouze řetězce. Šablona projektu vygenerovala ID diagnostiky za vás a Vy ji můžete změnit. Kód ve vlastnosti jednoduše vrátí ID z třídy Analyzer.

**Metoda RegisterCodeFixAsync přebírá kontext.** Kontext je důležitý, protože oprava kódu může být použita na více diagnostických nástrojů, nebo může být více než jeden problém na řádku kódu. Pokud zadáte "Context". v těle metody se v seznamu dokončení IntelliSense zobrazí několik užitečných členů. K dispozici je člen CancellationTokenu, který vám umožní zjistit, jestli je potřeba tuto opravu zrušit. Existuje člen dokumentu, který má spoustu užitečných členů a umožňuje získat objekty modelu projektu a řešení. Je členem rozsahu, který je na začátku a na konci umístění kódu zadaného při nahlášení diagnostiky.

**Nastavte tuto metodu jako asynchronní.** První věc, kterou potřebujete udělat, je opravit deklaraci generované metody, aby byla `async` metodou. Oprava kódu pro podkládá z implementace abstraktní třídy nezahrnuje `async` klíčové slovo, i když metoda vrátí hodnotu `Task` .

**Získejte kořen stromu syntaxe.** Chcete-li upravit kód, který je potřeba k vytvoření nového stromu syntaxe se změnami, které provádí oprava kódu. `Document`Pro volání budete potřebovat z kontextu `GetSyntaxRootAsync` . Jedná se o asynchronní metodu, protože existuje neznámá práce pro získání stromu syntaxe, případně k získání souboru z disku, jeho analýzy a sestavení modelu kódu Roslyn. Uživatelské rozhraní sady Visual Studio by mělo během této doby reagovat, což používá možnost `async` Povolit. Nahraďte řádek kódu v metodě následujícím kódem:

```csharp
var root = await context.Document
                        .GetSyntaxRootAsync(context.CancellationToken);
```

**Vyhledejte uzel s problémem.** Předáte do rozsahu kontextu, ale nalezený uzel nemusí být kód, který je třeba změnit. Nahlášená Diagnostika poskytuje pouze rozpětí pro identifikátor typu (kde je začínaná vlnovkou), ale je potřeba nahradit celý výraz pro vytvoření objektu, včetně `new` keywoard na začátku a závorek na konci. Do metody přidejte následující kód (a použijte **kombinaci kláves CTRL +.** Přidání `using` příkazu pro `ObjectCreationExpressionSyntax` ):

```csharp

var objectCreation = root.FindNode(context.Span)
                         .FirstAncestorOrSelf<ObjectCreationExpressionSyntax>();
```

 **Zaregistrujte opravu kódu pro uživatelské rozhraní žárovky.** Když zaregistrujete opravu kódu, Roslyn se do uživatelského rozhraní aplikace Visual Studio automaticky připojí k uživatelskému rozhraní žárovky. Koncovým uživatelům uvidí, že můžou používat **kombinaci kláves CTRL +.** (tečka), pokud analyzátor vytvoří nesprávné `ImmutableArray<T>` použití konstruktoru. Vzhledem k tomu, že se poskytovatel opravy kódu spustí pouze v případě, že dojde k problému, můžete předpokládat, že máte hledaný výraz pro vytvoření objektu. Z kontextového parametru můžete zaregistrovat novou opravu kódu přidáním následujícího kódu na konec `RegisterCodeFixAsync` metody:

```csharp

context.RegisterCodeFix(
            CodeAction.Create("Use ImmutableArray<T>.Empty",
                              c => ChangeToImmutableArrayEmpty(objectCreation,
                                                               context.Document,
                                                               c)),
            context.Diagnostics[0]);
```

Je nutné umístit blikající kurzor editoru do identifikátoru, `CodeAction` a pak použít **kombinaci kláves CTRL +.** (tečka) pro přidání odpovídajícího `using` příkazu pro tento typ.

Pak umístěte blikající kurzor editoru do `ChangeToImmutableArrayEmpty` identifikátoru a použijte **kombinaci kláves CTRL +.** znovu pro vygenerování tohoto zástupného kódu metody.

Tento poslední fragment kódu, který jste přidali, registruje opravu kódu předáním `CodeAction` a ID diagnostiky pro druh problému, který byl nalezen. V tomto příkladu je k dispozici pouze jedno ID diagnostiky, pro který tento kód poskytuje opravy, takže můžete jednoduše předat první prvek pole ID diagnostiky. Když vytvoříte `CodeAction` , předáte text, který by měl uživatelské rozhraní žárovky používat jako Popis opravy kódu. Předáte také funkci, která přijímá CancellationToken a vrátí nový dokument. Nový dokument má nový strom syntaxe, který obsahuje váš opravený kód, který volá `ImmutableArray.Empty` . Tento fragment kódu používá výraz lambda tak, aby se mohl zavřít v uzlu objectCreation a v dokumentu kontextu.

**Vytvořte nový strom syntaxe.** V `ChangeToImmutableArrayEmpty` metodě, jejíž dříve vygenerovali testovací proceduru, zadejte řádek kódu: `ImmutableArray<int>.Empty;` . Pokud znovu zobrazíte okno Syntax Visualizer nástrojů, uvidíte tuto syntaxi uzel SimpleMemberAccessExpression. To je to, co tato metoda potřebuje k sestavení a vrácení v novém dokumentu.

První změna, která se má `ChangeToImmutableArrayEmpty` Přidat `async` dřív, `Task<Document>` protože generátory kódu nemůžou předpokládat, že by metoda měla být asynchronní.

Vyplňte text následujícím kódem, aby vaše metoda vypadala podobně jako v následujícím příkladu:

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

V identifikátoru bude nutné vložit blikající kurzor `SyntaxGenerator` a použít **kombinaci kláves CTRL +.** (tečka) pro přidání odpovídajícího `using` příkazu pro tento typ.

Tento kód používá `SyntaxGenerator` , což je velmi užitečný typ pro vytváření nového kódu. Po získání generátoru pro dokument, který má problém s kódem, `ChangeToImmutableArrayEmpty` volání `MemberAccessExpression` předávají typu, který má člena, pro který chceme získat přístup, a předání názvu člena jako řetězce.

V dalším kroku metoda načte kořen dokumentu a protože to může zahrnovat libovolnou práci v obecném případě, kód očekává toto volání a předá token zrušení. Modely kódu Roslyn jsou neměnné, jako při práci s řetězcem .NET; Při aktualizaci řetězce se při návratu zobrazí nový objekt řetězce. Při volání `ReplaceNode` se vrátí nový kořenový uzel. Většina stromu syntaxe je sdílena (protože je neproměnlivá), ale `objectCreation` uzel je nahrazen `memberAccess` uzlem a také všechny nadřazené uzly až do kořenového adresáře stromu syntaxe.

## <a name="trying-your-code-fix"></a>Pokus o opravu kódu
Nyní můžete stisknutím klávesy **F5** spustit Analyzátor ve druhé instanci aplikace Visual Studio. Otevřete projekt konzoly, který jste použili dříve. Nyní by se měla zobrazit žárovka, kde je nový výraz pro vytvoření objektu pro `ImmutableArray<int>` . Pokud stisknete **kombinaci kláves CTRL +.** (tečka), zobrazí se oprava kódu a v uživatelském rozhraní žárovky se zobrazí automaticky vygenerovaný náhled rozdílů kódu. Roslyn to vytvoří za vás.

Tip pro: Pokud spustíte druhou instanci sady Visual Studio a žárovku s opravou kódu nevidíte, možná budete muset vymazat mezipaměť komponent sady Visual Studio. Vymazání mezipaměti vynutí, aby aplikace Visual Studio znovu prozkoumala komponenty, takže Visual Studio by pak mělo vybrat nejnovější komponentu. Nejprve vypněte druhou instanci aplikace Visual Studio. Pak v Průzkumníkovi Windows přejdete do adresáře uživatelů (c:\Users \\<UserID \> ) a vyhledáte AppData\Local\Microsoft\VisualStudio\14.0Roslyn \\ . V tomto adresáři odstraňte podadresář ComponentModelCache. Verze "14" mění verzi pro verzi sady Visual Studio.

## <a name="talk-video-and-finish-code-project"></a>Pohovořit video a dokončit projekt kódu
Tento příklad můžete zobrazit v [tomto rozhovoru](https://channel9.msdn.com/events/Build/2015/3-725)a podrobněji na něm. Tento rozhovor ukazuje pracovní analyzátor a provede vás procesem jeho sestavení.

[Zde](https://github.com/DustinCampbell/CoreFxAnalyzers/tree/master/Source/CoreFxAnalyzers)můžete zobrazit veškerý dokončený kód. Podsložky DoNotUseImmutableArrayCollectionInitializer a DoNotUseImmutableArrayCtor mají každý soubor C# pro hledání problémů a soubor C#, který implementuje opravy kódu, které se zobrazují v uživatelském rozhraní žárovky sady Visual Studio. Všimněte si, že dokončený kód má trochu větší abstrakci, aby se předešlo tomu, že se nenačítá \<T> objekt typu ImmutableArray. Používá vnořené zaregistrované akce k uložení objektu typu v kontextu, který je k dispozici vždy, když se spustí dílčí akce (analýza inicializace objektů a analýza kolekcí).

## <a name="see-also"></a>Viz také
[ \\ \Build 2015 hovoří](https://channel9.msdn.com/events/Build/2015/3-725)o 
 [dokončeném kódu na GitHubu](https://github.com/DustinCampbell/CoreFxAnalyzers/tree/master/Source/CoreFxAnalyzers)  
 [několik příkladů na GitHubu, seskupené do tří druhů analyzátorů,](https://github.com/dotnet/roslyn/blob/master/docs/analyzers/Analyzer%20Samples.md)které  
 [jsou další dokumenty na](https://github.com/dotnet/roslyn/tree/master/docs/analyzers)GitHubu na webu GitHub –  
 [FxCop pravidla implementovaná pomocí analyzátorů Roslyn na GitHubu](https://github.com/dotnet/roslyn/tree/master/src/Features/Core/Portable/Diagnostics/Analyzers)
