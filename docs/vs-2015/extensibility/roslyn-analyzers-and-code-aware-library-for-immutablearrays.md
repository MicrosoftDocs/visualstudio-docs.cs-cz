---
title: Analyzátory Roslyn a knihovny pro řešení ImmutableArrays | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0b0afa22-3fca-4d59-908e-352464c1d903
caps.latest.revision: 6
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f4c5b7f145438d6c61ae58a18176d2dae579b128
ms.sourcegitcommit: 75e02ed88a1ace6e8265fd4e3a82a1bc78f3adca
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/13/2018
ms.locfileid: "53348548"
---
# <a name="roslyn-analyzers-and-code-aware-library-for-immutablearrays"></a>Analyzátory Roslyn a knihovny rozlišující kódy pro řešení ImmutableArrays
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[.NET Compiler Platform](https://github.com/dotnet/roslyn) ("Roslyn") vám pomůže sestavit s ohledem na kód knihovny. S ohledem na kód knihovny poskytuje funkce, které můžete použít nástroje (analyzátory Roslyn), které vám pomohou při použití knihovny nejlepším způsobem, nebo aby nedocházelo k chybám. V tomto tématu se dozvíte, jak vytvářet analyzátoru Roslyn reálného světa zachytit běžných chyb při použití [NIB: Neměnné kolekce](http://msdn.microsoft.com/library/33f4449d-7078-450a-8d60-d9229f66bbca) balíček NuGet. Tento příklad také ukazuje, jak zajistit opravu kódu pro kód problém najít analyzátor. Uživatelé uvidí opravy kódu v sadě Visual Studio žárovky uživatelského rozhraní a provést opravu kódu automaticky.

## <a name="getting-started"></a>Začínáme
Budete potřebovat následující sestavení tohoto příkladu:

- Visual Studio 2015 (ne verzi Express) nebo novější. Můžete použít bezplatnou [Visual Studio Community Edition](https://www.visualstudio.com/products/visual-studio-community-vs)

- [Visual Studio SDK](../extensibility/visual-studio-sdk.md). Můžete také při instalaci sady Visual Studio, zkontrolovat Visual Studio Extensibility Tools v části Common Tools do instalace sady SDK ve stejnou dobu. Pokud jste již nainstalovali Visual Studio, můžete také nainstalovat tuto sadu SDK tak, že přejdete do hlavní nabídky **souboru &#124; nový &#124;projektu...** , výběr jazyka C# v levém navigačním podokně a následným výběrem rozšiřitelnosti. Pokud zvolíte "**nainstalovat Visual Studio Extensibility Tools**" šablony projektu s popisem cesty, budete vyzváni ke stažení a instalaci sadu SDK.

- [.NET compiler Platform ("Roslyn") SDK](http://aka.ms/roslynsdktemplates). Můžete také nainstalovat tuto sadu SDK tak, že přejdete do hlavní nabídky **souboru &#124; nový &#124; projektu...** zvolíte možnost **jazyka C#** v levém navigačním podokně a pak výběrem **rozšiřitelnost**. Při výběru možnosti "**stáhnout sadu SDK platformy kompilátoru .NET**" šablony projektu s popisem cesty, budete vyzváni ke stažení a instalaci sadu SDK. Tato sada SDK zahrnuje [Roslyn Syntax Visualizer](https://github.com/dotnet/roslyn/wiki/Syntax%20Visualizer). Tato velmi užitečným nástrojem pomůže zjistit, jaké typy kódu modelu je vhodné vyhledat ve vaší analyzátor. Analyzátor infrastruktury volání do kódu pro typy modelu konkrétního kódu, tak, aby váš kód pouze provede v případě potřeby a soustředit se jenom na analýzu příslušný kód.

## <a name="whats-the-problem"></a>V čem je problém?
Představte si ImmutableArray je poskytnout knihovny (například <xref:System.Collections.Immutable.ImmutableArray%601?displayProperty=fullName>) podporují. C# vývojářům k dispozici spoustu zkušeností s poli .NET. Ale vzhledem k povaze řešení ImmutableArrays a optimalizace techniky, které využívají v implementaci intuitions pro vývojáře v C# uživatelům způsobit knihovny zápisu poškozený kód, jak je popsáno níže. Uživatelé navíc nezobrazí jejich chyby až do spuštění, který není kvalitu prostředí, na které se používají v sadě Visual Studio pomocí rozhraní .NET.

Uživatelé obeznámeni s psaním kódu takto:

```csharp
var a1 = new int[0];
Console.WriteLine("a1.Length = { 0}", a1.Length);
var a2 = new int[] { 1, 2, 3, 4, 5 };
Console.WriteLine("a2.Length = { 0}", a2.Length);

```

Vytvoření prázdné pole tak, aby vyplnil pomocí následující řádky kódu a pomocí syntaxe inicializátoru kolekce jsou pro vývojáře v C# velmi srozumitelná. Ale stejné psaní kódu pro ImmutableArray dojde k chybě za běhu:

```csharp
var b1 = new ImmutableArray<int>();
Console.WriteLine("b1.Length = { 0}", b1.Length);
var b2 = new ImmutableArray<int> { 1, 2, 3, 4, 5 };
Console.WriteLine("b2.Length = { 0}", b2.Length);

```

První chyba je způsobena ImmutableArray implementace zabalení základního úložiště dat pomocí struktury. Struktur musí mít konstruktor bez parametrů, aby `default(T)` výrazů může vrátit struktury se všemi nula nebo null členy. Když kód přistupuje k `b1.Length`, existuje s hodnotou null v době běhu dereference chyba, protože neexistuje žádná základní pole úložišť ve struktuře ImmutableArray. Správný způsob, jak vytvořit prázdný ImmutableArray je `ImmutableArray<int>.Empty`.

 Chyba s inicializátory kolekce se stane, protože metoda ImmutableArray.Add vrátí nové instance pokaždé, když ji volat. Protože řešení ImmutableArrays nikdy nezmění, když přidáte nový prvek, získáte zpět nový objekt ImmutableArray (které můžou sdílet úložiště z důvodů výkonu s dříve existující ImmutableArray). Protože `b2` odkazuje na první ImmutableArray před voláním `Add()` pětkrát, `b2` je výchozí ImmutableArray. Volání délky na něm také chyby s hodnotou null přistoupit přes ukazatel chyby. Správný způsob, jak inicializovat ImmutableArray, bez volání ručně přidat, je použít `ImmutableArray.CreateRange(new int[] {1, 2, 3, 4, 5})`.

## <a name="finding-relevant-syntax-node-types-to-trigger-your-analyzer"></a>Typy uzlů relevantní syntaxi hledání pro aktivaci vaší analyzátoru
Chcete-li začít vytvářet analyzátor, nejdřív zjistit, jaký typ SyntaxNode, budete muset vyhledat.   Spustit z nabídky Vizualizéru syntaxe **zobrazení &#124; ostatní Windows &#124; Roslyn Syntax Visualizer**.

Umístit blikající kurzor editoru na řádek, který deklaruje `b1`. Zobrazí se vám zobrazuje Vizualizéru syntaxe jsou v `LocalDeclarationStatement` uzel stromu syntaxe. Tento uzel má `VariableDeclaration`, která naopak má `VariableDeclarator`, která naopak má `EqualsValueClause`a nakonec je `ObjectCreationExpression`. Při klepnutí ve stromu syntaxe Vizualizéru uzlů, zvýrazní syntaxe v okně editoru zobrazit kódu představovaného k uzlu. Názvy typů sub SyntaxNode shodovat s názvy používanými v gramatice jazyka C#.

## <a name="creating-the-analyzer-project"></a>Vytvoření projektu analyzátoru
V hlavní nabídce zvolte **souboru &#124; nový &#124; projektu...** . V **nový projekt** dialogového okna, v části **jazyka C#** projekty v levém navigačním panelu vyberte rozšíření a v pravém podokně vyberte **analyzátor s opravu kódu** projektu Šablona. Zadejte název a potvrďte dialogového okna.

Šablona se otevře soubor DiagnosticAnalyzer.cs. Vyberte tento editor kartu vyrovnávací paměti. Tento soubor obsahuje třídu analyzer (vytvořený z názvu dáte projektu), která je odvozena z `DiagnosticAnalyzer` (typ rozhraní Roslyn API). Obsahuje novou třídu `DiagnosticAnalyzerAttribute` deklarace vaše analyzer je relevantní pro jazyk C#, tak, aby kompilátor vyhledá a načte vaše analyzátor.

```csharp
[DiagnosticAnalyzer(LanguageNames.CSharp)]
public class ImmutableArrayAnalyzerAnalyzer : DiagnosticAnalyzer
{}
```

Můžete implementovat analyzátor jazyka Visual Basic, který cílí na kód jazyka C#, a naopak. Je důležité v DiagnosticAnalyzerAttribute zvolit, jestli vaše analyzátor cílí na jeden jazyk nebo obojí. Složitější analyzátory, které vyžadují podrobné modelování jazyka můžete cílit pouze jeden jazyk. Pokud analyzátor, například zkontroluje pouze názvy typů nebo názvy veřejného člena, je možné použít common language model, který nabízí Roslyn v jazyce Visual Basic a C#. Například FxCop vás upozorní, že třída implementuje <xref:System.Runtime.Serialization.ISerializable>, ale třída nemá <xref:System.SerializableAttribute> atribut je nezávislým na jazyku a funguje i pro kód jazyka Visual Basic a C#.

## <a name="initalizing-the-analyzer"></a>Initalizing analyzátoru
Posuňte se dolů o něco v `DiagnosticAnalyzer` třídy zobrazíte `Initialize` metoda. Kompilátor volá tuto metodu při aktivaci analyzátor. Tato metoda přebírá `AnalysisContext` objekt, který umožňuje vaší analyzátor v kontextové informace a registrace zpětných volání pro události pro různé druhy kódu, které chcete analyzovat.

```csharp
public override void Initialize(AnalysisContext context) {}
```

Začít nový řádek v této metody a typu "kontextu." Pokud chcete zobrazit seznam doplňování technologie Intellisense. Můžete zobrazit v seznamu pro doplňování existuje několik instancí `Register…` metody pro zpracování různých druhů událostí. Například první z nich, `RegisterCodeBlockAction`, volání zpět do kódu pro blok, což je obvykle kód mezi složenými závorkami. Registrace pro blok také zavolá zpět do kódu pro inicializátor pole, hodnota atributu nebo hodnota volitelného parametru.

Další příklad – `RegisterCompilationStartAction`, volání zpátky do vašeho kódu na začátku kompilace, což je užitečné, když budete chtít shromažďování stavů mnoho míst. Můžete vytvořit datové struktury, například ke shromažďování všech symboly použité, a pokaždé, když vaše analyzer je zpětné volání pro některé syntaxe nebo symbolu, můžete uložit informace o jednotlivých umístěních datové struktury. Pokud jste zpětné volání z důvodu ukončení kompilace, můžete analyzovat všechna místa, které jste uložili, například jaké symboly tento kód použije z každého hlášení `using` příkazu.

Použití **Syntax Visualizer**, jste zjistili, že chcete volat v případě, že kompilátor zpracovává ObjectCreationExpression. Pomocí tohoto kódu k nastavení zpětné volání:

```csharp

context.RegisterSyntaxNodeAction(c => AnalyzeObjectCreation(c),
                                 SyntaxKind.ObjectCreationExpression);
```

Registraci pro uzel syntaxe a filtrovat pouze objekt vytvoření syntaxe uzly. Podle konvence autoři analyzátor používat lambda při registraci akce, které pomáhá chránit analyzátory bezstavové. Můžete použít funkce sady Visual Studio **Generovat z využití** vytvořit `AnalyzeObjectCreation` metody. Tím se vytvoří správný typ kontextový parametr pro vás moc.

## <a name="setting-properties-for-users-of-your-analyzer"></a>Nastavení vlastností pro uživatele vaší analyzátoru
Tak, aby vaše Analyzátor se zobrazí v uživatelském rozhraní aplikace Visual Studio správně, Hledat a upravte následující řádek kódu k identifikaci vaší analyzer:

```csharp
internal const string Category = "Naming";
```

Změna `"Naming"` k `"API Guidance"`.

Poté vyhledejte a otevřete soubor Resources.resx v projektu pomocí **Průzkumníka řešení**. Můžete umístit v popisu pro analyzátor, title, atd. Můžete změnit hodnotu pro všechny z nich k `“Don’t use ImmutableArray<T> constructor”` teď. Můžete vložit řetězce formátování argumentů do řetězce ({0}, {1}atd) a později při volání `Diagnostic.Create()`, můžete zadat parametry pole argumentů, které mají být předány.

## <a name="analyzing-an-object-creation-expression"></a>Analýza výrazu vytvoření objektu
`AnalyzeObjectCreation` Metoda má jiný typ kontextu poskytnutých rozhraní analyzátor kódu. Metoda Initialize `AnalysisContext` umožňuje registrovat akci zpětná volání k nastavení vašeho analyzátor. `SyntaxNodeAnalysisContext`, Třeba `CancellationToken` , kterou můžete předat kolem. Pokud uživatel spustí psaní v editoru, Roslyn zruší běžící analyzátory uložte práci a zlepšit výkon. Další příklad má tento kontext uzel vlastnost, která vrací uzel syntaxe vytváření objektu.

Získejte uzlu, na kterém je typ, pro kterou filtrovat akce uzlu syntaxe, můžete předpokládat:

```csharp
var objectCreation = (ObjectCreationExpressionSyntax)context.Node;
```

### <a name="launching-visual-studio-with-your-analyzer-the-first-time"></a>Spuštění sady Visual Studio s vaší první analyzátor
Spusťte sadu Visual Studio tak, že vytváření a spouštění vašeho analyzer (stiskněte **F5**). Vzhledem k tomu, že počáteční projekt **Průzkumníka řešení** je projekt VSIX, spouštění kódu sestavení kódu a rozšíření VSIX a pak spustí sadu Visual Studio pomocí tohoto VSIX nainstalovaná. Když spustíte Visual Studio tímto způsobem, spustí s distinct podregistru tak, aby vaše testovací instance neovlivní hlavní používání sady Visual Studio při vytváření analyzátory. Při prvním spuštění tímto způsobem, Visual Studio provede několik inicializací podobně jako když je prvním spuštění sady Visual Studio po její instalaci.

 Vytvoření projektu konzolové a pak zadejte kód pole do konzoly metodu Main aplikace:

```csharp
var b1 = new ImmutableArray<int>();
Console.WriteLine("b1.Length = {0}", b1.Length);
var b2 = new ImmutableArray<int> { 1, 2, 3, 4, 5 };
Console.WriteLine("b2.Length = {0}", b2.Length);

```

Řádky kódu s `ImmutableArray` mít podtržení vlnovkou, protože je potřeba získat nezměnitelný balíček NuGet a přidejte `using` příkaz do vašeho kódu. Stiskněte tlačítko vpravo ukazatel myši na uzel projektu v **Průzkumníka řešení** a zvolte **spravovat balíčky NuGet...** . Ve Správci NuGet, zadejte do vyhledávacího pole "Neměnné" a vyberte položku "System.Collections.Immutable" (nevybírejte "Microsoft.Bcl.Immutable") v levém podokně a klepněte na tlačítko nainstalovat v pravém podokně. Instalace balíčku přidává odkaz na odkazy projektu.

Se stále zobrazuje v části červenou vlnovkou `ImmutableArray`, proto umístěte blikající kurzor do tento identifikátor a stiskněte klávesu **CTRL +.** (tečka) se vyvolali navrhované opravy nabídku a zvolte Přidat odpovídající `using` příkazu.

**Uložte a zavřete** druhou instanci aplikace Visual Studio teď můžete umístit do čistého stavu, abyste mohli pokračovat.

## <a name="finishing-the-analyzer-using-edit-and-continue"></a>Dokončení analyzátor pomocí operace upravit a pokračovat
V první instanci aplikace Visual Studio nastavte zarážku na začátek vašeho `AnalyzeObjectCreation` metoda stisknutím kombinace kláves **F9** s blikající kurzor na první řádek.

Spuštění vaší analyzátoru s **F5**a v druhé instanci aplikace Visual Studio, otevřete znovu vaší konzolové aplikace, které jste vytvořili čas poslední.

Můžete vrátit k první instanci sady Visual Studio na zarážce, protože kompilátor Roslyn viděli výrazu vytvoření objektu a volat do vaší analyzátor.

**Získáte uzel vytvoření objektu.** Krok přes řádek, který nastaví `objectCreation` proměnné stisknutím klávesy **F10**a **podokna** vyhodnocení výrazu `“objectCreation.ToString()”`. Uvidíte, že se uzel syntaxe proměnná odkazuje na kód `"new ImmutableArray<int>()"`, stačí co jste hledali.

**Získat ImmutableArray\<T > typ objektu.** Je potřeba zkontrolovat, zda je typ vytváří ImmutableArray. Nejprve získejte objekt, který představuje tohoto typu. Můžete zkontrolovat typy použití sémantického modelu, abyste zajistili jste právě správný typ a není porovnat řetězec z ToString(). Zadejte následující řádek kódu na konec funkce:

```csharp

var immutableArrayOfTType =
    context.SemanticModel
           .Compilation
           .GetTypeByMetadataName("System.Collections.Immutable.ImmutableArray`1");

```

Můžete určit obecné typy v metadatech s backquotes (') a počet obecných parametrů. To je důvod, proč nevidíte "... ImmutableArray\<T > "v názvu metadat.

Sémantický model má mnoho užitečných věcí, které umožňují pokládání otázek na symboly, tok dat, životnost proměnné atd. Roslyn odděluje syntaxe uzly z sémantického modelu z různých důvodů engineering (výkonem, modelování chybný kód atd.). Chcete, aby model kompilace při hledání informací obsažených v odkazech pro přesné porovnání.

Můžete přetáhnout žlutou spuštění ukazatele na levé straně okna editoru. Přetáhněte až po řádek, který nastaví `objectCreation` proměnné a krok přes svůj nový řádek kódu pomocí **F10**. Pokud se při umístění ukazatele myši nad proměnnou `immutableArrayOfType`, uvidíte, že jsme součástí přesný typ sémantického modelu.

**Získáte typ výrazu pro vytvoření objektu.** "Type" se používá v několika způsoby, jak v tomto článku, ale to znamená, že pokud máte "nové Foo" výrazu, je potřeba získat model Foo. Je potřeba získat typ výrazu vytváření objektů chcete zobrazit, pokud je ImmutableArray je\<T > typu. Chcete-li získat informace o symbolech pro typ symbolu (ImmutableArray) v objektovém výrazu vytváření sémantického modelu znovu použijte. Zadejte následující řádek kódu na konec funkce:

```csharp
var symbolInfo = context.SemanticModel.GetSymbolInfo(objectCreation.Type) as INamedTypeSymbol;

```

Protože vaše analyzer je potřeba zpracovat neúplné nebo nesprávný kód v editoru vyrovnávací paměti (například je chybějící `using` příkaz), by měla vyhledávat `symbolInfo` se `null`. Je nutné získat pojmenovaného typu (INamedTypeSymbol) z objektu informací o symbolu na dokončení analýzy.

**Porovnání typů.** Protože je otevřený obecný typ. t, která hledáme a typ v kódu je konkrétní obecného typu, dotazovat informace o symbolech pro jaký typ je vytvořen z (otevřený obecný typ.) a porovnat výsledek s `immutableArrayOfTType`. Zadejte na konec metody:

```csharp
if (symbolInfo != null &&
    symbolInfo.ConstructedFrom.Equals(immutableArrayOfTType))
{}
```

**Zprávy diagnostiky.** Vytváření sestav diagnostiky je poměrně snadné. Použijete pravidlo vytvořeno v šabloně projektu, který je definován před voláním metody Initialize. Protože tato situace v kódu k chybě, můžete změnit na řádek, který je inicializován pravidla nahrazení `DiagnosticSeverity.Warning` (zelená vlnovku) s `DiagnosticSeverity.Error` (červená vlnovka). Zbývající pravidla se inicializuje z prostředků, které jste upravili na začátku průvodce. Potřebujete sestavu umístění vlnovka, který je umístěním specifikace typu možným vytvoření objektu. Zadejte tento kód `if` blok:

```csharp
context.ReportDiagnostic(Diagnostic.Create(Rule, objectCreation.Type.GetLocation()));
```

Funkce by měl vypadat takto (třeba formátovány odlišně):

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

Odeberte zarážku, takže můžete vidět vaše pracovní analyzer (a zastavit vrací první instanci aplikace Visual Studio). Přetáhněte ukazatel spuštění na začátek metodu a stiskněte klávesu **F5** pro pokračování v provádění. Když přepnete zpět do druhé instanci aplikace Visual Studio, kompilátor se spustí znovu prozkoumat kód a zavolá váš analyzátor. Můžete zobrazit vlnovku v rámci `ImmutableType<int>`.

## <a name="adding-a-code-fix-for-the-code-issue"></a>Přidání "Opravu kódu" pro problém v kódu
Než začnete, zavřete druhou instanci aplikace Visual Studio a Zastavit ladění v první instance sady Visual Studio (Pokud vyvíjíte analyzátor).

**Přidejte novou třídu.** Pomocí místní nabídky (tlačítko vpravo ukazatel) na uzel projektu v Průzkumníku řešení a zvolte Přidat novou položku. Přidejte třídu s názvem `BuildCodeFixProvider`. Tato třída musí být odvozen od `CodeFixProvider`, a budete muset použít **CTRL +.** (tečka) k vyvolání opravu kódu, který přidá správnou `using` příkazu. Tato třída také musí být komentována atributem `ExportCodeFixProvider` atribut a je potřeba přidat `using` příkaz vyřešit `LanguageNames` výčtu. Měli byste soubor třídy v něm následujícím kódem:

```csharp
using Microsoft.CodeAnalysis;
using Microsoft.CodeAnalysis.CodeFixes;

namespace ImmutableArrayAnalyzer
{
    [ExportCodeFixProvider(LanguageNames.CSharp)]
    class BuildCodeFixProvider : CodeFixProvider
    {}

```

**Zástupné procedury na odvozené členy.** Nyní umístěte blikající kurzor editoru v identifikátoru `CodeFixProvider` a stiskněte klávesu **CTRL +.** (tečka) se zakázaným o provedení této abstraktní základní třídy. Tím se vygeneruje vlastnost a metodu pro vás.

**Implementuje vlastnost.** Vyplňte `FixableDiagnosticIds` vlastnosti `get` tělo s následujícím kódem:

```csharp
return ImmutableArray.Create(ImmutableArrayAnalyzerAnalyzer.DiagnosticId);
```

Roslyn přináší společně diagnostiky a oprav to provede spárováním odpovídajících tyto identifikátory, které jsou pouze řetězce. Šablona projektu vygeneruje ID diagnostiky pro vás a můžete libovolně změnit. Kód ve vlastnosti právě vrátí ID ze třídy analyzátor.

**Metoda RegisterCodeFixAsync přebírá kontext.** Kontext je důležité, protože opravu kódu můžete použít pro více diagnostiky nebo může být více než jeden problém na řádek kódu. Pokud zadáte "kontext". v těle metody seznamu doplňování technologie Intellisense se zobrazí některé užitečné členy. Existuje CancellationToken člena, který můžete zkontrolovat, zobrazit, pokud něco chce zrušit opravy. Není člen dokumentu, který má spoustu užitečných členů a umožňuje dosáhnout na objekty modelu projektu a řešení. Existuje Span člena, který je začátek a konec umístění v kódu zadat, když jste nahlásili diagnostiky.

**Ujistěte se, být asynchronní metody.** První věc, kterou je potřeba je opravit deklaraci vytvořena metoda bude `async` metody. Neobsahuje opravu kódu pro vytváření zástupných procedur na implementaci abstraktní třídy `async` – klíčové slovo, i když metoda vrátí `Task`.

**Získá kořen stromu syntaxe.** Úprava kódu, které potřebujete k tvorbě nového stromu syntaxe se změnami díky opravu vašeho kódu. Je nutné `Document` z kontextu volat `GetSyntaxRootAsync`. Totiž asynchronní metody je neznámý práce získat strom syntaxe verzovaným získávání souboru z disku, je analýza kódu a sestavení modelu kódu Roslyn pro něj. Visual Studio UI by měl být responzivní během této doby, které pomocí `async` umožňuje. Nahraďte řádek kódu v metodě následujícími způsoby:

```csharp
var root = await context.Document
                        .GetSyntaxRootAsync(context.CancellationToken);
```

**Najdete uzel s problémem.** Můžete předat značka span objektu context, ale na uzel, který vás nemusí být kód, který je nutné změnit. Značka span ohlášená Diagnostika poskytují jenom pro identifikátor typu (kde piktogram patřil), ale je třeba nahradit výraz vytvoření celý objekt, včetně `new` keywoard na začátku a na konci závorky. Přidejte následující kód k metodě (a použít **CTRL +.** Chcete-li přidat `using` příkaz pro `ObjectCreationExpressionSyntax`):

```csharp

var objectCreation = root.FindNode(context.Span)
                         .FirstAncestorOrSelf<ObjectCreationExpressionSyntax>();
```

 **Zaregistrujte svou opravu kódu pro návrhy uživatelského rozhraní.** Když si zaregistrujete kód opravit, Roslyn zpřístupní žárovku uživatelského rozhraní sady Visual Studio automaticky. Koncoví uživatelé uvidí, můžete použít **CTRL +.** (tečka), když vaše analyzátor squiggles chybný `ImmutableArray<T>` použijte konstruktor. Vzhledem k tomu, že váš poskytovatel opravu kódu se provede jenom v případě dochází k nějakému problému, můžete předpokládat, že máte výraz vytvoření objektu, kterou jste hledali. Z kontextového parametru, můžete zaregistrovat nové opravu kódu přidáním následujícího kódu na konec `RegisterCodeFixAsync` metody:

```csharp

context.RegisterCodeFix(
            CodeAction.Create("Use ImmutableArray<T>.Empty",
                              c => ChangeToImmutableArrayEmpty(objectCreation,
                                                               context.Document,
                                                               c)),
            context.Diagnostics[0]);
```

Je potřeba umístit blikající kurzor editoru identifikátor `CodeAction`, pak použijte **CTRL +.** (tečka) Chcete-li přidat odpovídající `using` pro tento typ příkazu.

Umístěte kurzor editoru v `ChangeToImmutableArrayEmpty` identifikátor a použití **CTRL +.** znovu se generovat podložení tuto metodu za vás.

Tento poslední fragment kódu, který jste přidali zaregistruje předáním opravu kódu `CodeAction` a ID diagnostiky pro typ nalezen problém. V tomto příkladu existuje pouze jeden ID diagnostiky, který poskytuje tento kód opraví, takže předáte na první prvek diagnostické pole ID. Při vytváření `CodeAction`, předáte do textu, který žárovky uživatelského rozhraní by měly používat jako popis opravu kódu. Můžete také předat ve funkci, která přijímá CancellationToken a vrací nový dokument. Nový dokument má nové stromu syntaxe, která zahrnuje verzi kódu, který volá `ImmutableArray.Empty`. Tento fragment kódu používá výraz lambda, takže můžete zavřít nad uzel objectCreation a objektu context dokumentu.

**Vytvoření nového stromu syntaxe.** V `ChangeToImmutableArrayEmpty` metoda, jejíž zástupné procedury jste vygenerovali dříve, zadejte na řádek kódu: `ImmutableArray<int>.Empty;`. Pokud zobrazíte nástroj okno Vizualizéru syntaxe, uvidíte, že tato syntaxe je SimpleMemberAccessExpression uzlu. Je to, co tato metoda je potřeba vytvořit a vraťte se nový dokument.

První změna `ChangeToImmutableArrayEmpty` je přidání `async` před `Task<Document>` protože generátory kódu nelze předpokládat, metoda by měla být asynchronní.

Zadejte obsah následujícím kódem, aby vaše metoda vypadá nějak takto:

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

Budete muset vložit blikající kurzor editoru `SyntaxGenerator` identifikátor a použití **CTRL +.** (tečka) Chcete-li přidat odpovídající `using` pro tento typ příkazu.

Tento kód používá `SyntaxGenerator`, což je velmi užitečné typ pro tvorbu nového kódu. Po získání generátor pro dokument, který má problém v kódu `ChangeToImmutableArrayEmpty` volání `MemberAccessExpression`, předávání typ, který má člen chceme, aby pro přístup k a předáním názvu členu jako řetězec.

V dalším kroku metodu načte kořen dokumentu, a protože to může zahrnovat libovolný práce v tomto obecném případě, kód čeká na toto volání a předává token zrušení. Modely kódu Roslyn jsou neměnné, podobně jako při práci s řetězcem .NET; Při aktualizaci řetězec získáte nový objekt řetězce na oplátku. Při volání `ReplaceNode`, můžete se vrátit nový kořenový uzel. Většina stromu syntaxe je sdílený (protože je neměnný), ale `objectCreation` nahradí uzlu `memberAccess` uzlu, jakož i všechny nadřazené uzly až po kořen stromu syntaxe.

## <a name="trying-your-code-fix"></a>Při operaci opravy kódu
Nyní můžete stisknout **F5** pro spuštění vašeho analyzátor ve druhé instanci aplikace Visual Studio. Otevřete konzoly projekt, který jste použili dříve. Teď byste měli vidět žárovky objevit, ve kterém je váš nový výraz vytvoření objektu pro `ImmutableArray<int>`. Pokud stisknete **CTRL +.** (interval) pak se zobrazí váš kód opravit, a zobrazí se v verzi preview rozdíl automaticky generovaného kódu v žárovky uživatelského rozhraní. To vytvoří Roslyn.

Tipu pro: Pokud spustíte druhou instanci aplikace Visual Studio a nevidíte žárovka s kód opravit, budete muset vymazat mezipaměť komponenty Visual Studio. Vymazání mezipaměti vynutí Visual Studio a znovu zkontrolujte součásti, takže sady Visual Studio by měl pak nejnovější komponenty. Nejdřív vypněte druhou instanci aplikace Visual Studio. V Průzkumníku Windows přejděte do adresáře uživatele (c:\users\\< userid\>) a najděte AppData\Local\Microsoft\VisualStudio\14.0Roslyn\\. V tomto adresáři odstraňte podadresáře ComponentModelCache. "14" změny na verzi pomocí sady Visual Studio.

## <a name="talk-video-and-finish-code-project"></a>Přednáška Video a dokončení kódu projektu
Zobrazí se v tomto příkladu vyvinul a popsané dále v [předváděcí](http://channel9.msdn.com/events/Build/2015/3-725). Posluchačů ukazuje analyzátor pracovní a provede vás jeho sestavení.

Zobrazí všechny dokončené kód [tady](https://github.com/DustinCampbell/CoreFxAnalyzers/tree/master/Source/CoreFxAnalyzers). Podsložek DoNotUseImmutableArrayCollectionInitializer a DoNotUseImmutableArrayCtor mít soubor jazyka C# pro vyhledání problémů a soubor jazyka C#, která implementuje opravy kódu, které se zobrazí v sadě Visual Studio žárovky uživatelského rozhraní. Mějte na paměti, Dokončený kód je trochu více abstrakce, aby se zabránilo načítání ImmutableArray je\<T > pořád dokola typu object. Používá vnořené registrované akce Uložit objekt typu, v kontextu, který je k dispozici pokaždé, když se akce sub (analýza vytvoření objektu a analyzovat inicializace kolekce) provést.

## <a name="see-also"></a>Viz také
[\\\Build 2015 Přednáška](http://channel9.msdn.com/events/Build/2015/3-725)
[dokončení kódu na Githubu](https://github.com/DustinCampbell/CoreFxAnalyzers/tree/master/Source/CoreFxAnalyzers) 
[několik příkladů na Githubu, seskupených do tři druhy analyzátory](https://github.com/dotnet/roslyn/blob/master/docs/analyzers/Analyzer%20Samples.md)  
 [Další dokumenty na webu GitHub OSS](https://github.com/dotnet/roslyn/tree/master/docs/analyzers) 
[pravidel FxCop implementovaných s analyzátory Roslyn na Githubu](https://github.com/dotnet/roslyn/tree/master/src/Diagnostics/FxCop)

