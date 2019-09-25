---
title: 'Postupy: Použití kontextu uživatelského rozhraní založeného na pravidlech pro rozšíření sady Visual Studio | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 8dd2cd1d-d8ba-49b9-870a-45acf3a3259d
author: madskristensen
ms.author: madsk
ms.workload:
- vssdk
ms.openlocfilehash: fd7e091192e0111a9dcf0997af8316daef364adb
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2019
ms.locfileid: "71252331"
---
# <a name="how-to-use-rule-based-ui-context-for-visual-studio-extensions"></a>Postupy: Použití kontextu uživatelského rozhraní založeného na pravidlech pro rozšíření sady Visual Studio

Visual Studio umožňuje načítání rozšíření VSPackages při některých dobře známé <xref:Microsoft.VisualStudio.Shell.UIContext>s aktivují. Tyto kontexty UI nejsou ale jemně odstupňované, což nechává autorům rozšíření žádnou volbu, ale k výběru dostupného kontextu uživatelského rozhraní, který se aktivuje předtím, než to opravdu požadovalo, aby VSPackage mohl načíst. Seznam dobře známé uživatelské rozhraní kontextech najdete v tématu <xref:Microsoft.VisualStudio.Shell.KnownUIContexts>.

Načítání balíčků může mít dopad na výkon a jejich načítání dřív, než je potřeba, není osvědčeným postupem. Visual Studio 2015 představil koncept kontextů uživatelského rozhraní založeného na pravidlech, mechanizmus, který správcům rozšíření umožňuje definovat přesné podmínky, za kterých je kontext uživatelského rozhraní aktivovaný a jsou načteny přidružené sady VSPackage.

## <a name="rule-based-ui-context"></a>Kontext založený na pravidlech uživatelského rozhraní

"Pravidlo" se skládá z nového kontextu uživatelského rozhraní (GUID) a logický výraz, který odkazuje na jeden nebo více "Terms" kombinovat pomocí logické "a", "nebo", "not" operace. "Terms" jsou vyhodnocovány dynamicky za běhu a výraz je znovu vyhodnocen při každé změně jeho podmínek. Pokud je výraz vyhodnocen jako true, je aktivováno souvisejícího kontextu uživatelského rozhraní. V opačném případě je deaktivován kontextu uživatelského rozhraní.

Kontext uživatelského rozhraní založeného na pravidlech lze použít různými způsoby:

1. Zadejte omezení viditelnost příkazů a oken nástrojů. Příkazy a nástroje pro windows můžete skrýt, až do splnění pravidla kontextu uživatelského rozhraní.

2. Jako omezení automatického načtení: automaticky načíst balíčky pouze v případě, že je pravidlo splněno.

3. Jako zpožděný úkol: zpoždění načítání až do uplynutí zadaného intervalu a pravidlo se pořád splní.

   Mechanismu, který mohou využívat všechny rozšíření sady Visual Studio.

## <a name="create-a-rule-based-ui-context"></a>Vytvoření kontextu uživatelského rozhraní založeného na pravidlech
 Předpokládejme, že máte rozšíření s názvem TestPackage, které nabízí příkaz nabídky, který se vztahuje pouze na soubory s příponou *. config* . Před VS2015, nejlepší možností je načíst TestPackage při <xref:Microsoft.VisualStudio.Shell.KnownUIContexts.SolutionExistsAndFullyLoadedContext%2A> kontextu uživatelského rozhraní se aktivovala. Načtení TestPackage tímto způsobem není efektivní, protože načtené řešení nemusí ani obsahovat soubor *. config* . Tyto kroky ukazují, jak se kontext uživatelského rozhraní založeného na pravidlech dá použít k aktivaci kontextu uživatelského rozhraní jenom v případě, že je vybraný soubor s příponou *. config* , a když se tento kontext uživatelského rozhraní aktivuje, načte se TestPackage.

1. Definovat nový identifikátor GUID UIContext a přidejte do třídy balíčku VSPackage <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> a <xref:Microsoft.VisualStudio.Shell.ProvideUIContextRuleAttribute>.

    Řekněme například, že se přidá nový UIContext "UIContextGuid". Vytvořený identifikátor GUID (můžete vytvořit GUID kliknutím na **nástroje** > **vytvořit GUID**) je "8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B". Do třídy balíčku pak přidáte následující deklaraci:

   ```csharp
   public const string UIContextGuid = "8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B";
   ```

    Pro atributy přidejte následující hodnoty: (Podrobnosti o těchto atributech budou vysvětleny později)

   ```csharp
   [ProvideAutoLoad(TestPackage.UIContextGuid)]
   [ProvideUIContextRule(TestPackage.UIContextGuid,
       name: "Test auto load",
       expression: "DotConfig",
       termNames: new[] { "DotConfig" },
       termValues: new[] { "HierSingleSelectionName:.config$" })]
   ```

    Tato metadata definovat nový identifikátor GUID UIContext (8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B) a výraz odkazuje na jeden termín "DotConfig". Termín "DotConfig" se vyhodnocuje na hodnotu true, kdykoli aktuální výběr v aktivní hierarchii má název, který odpovídá vzoru regulárního výrazu "\\. config $" (končí *příponou. config*). (Výchozí) Určuje volitelný název pravidla, které jsou užitečné pro ladění.

    Hodnoty atributu jsou přidány do pkgdef generovány během doby sestavení později.

2. Do souboru VSCT pro příkazy TestPackage přidejte příznak "DynamicVisibility" do příslušných příkazů:

   ```xml
   <CommandFlag>DynamicVisibility</CommandFlag>
   ```

3. V části viditelnosti VSCT tie příslušné příkazy, které nový UIContext GUID definované v #1:

   ```xml
   <VisibilityConstraints>
       <VisibilityItem guid="guidTestPackageCmdSet" id="TestId"  context="UIContextGuid"/>
   </VisibilityConstraints>
   ```

4. V části symboly přidáte definici UIContext:

   ```xml
   <GuidSymbol name="UIContextGuid" value="{8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B}" />
   ```

    Nyní budou příkazy kontextové nabídky pro  *\*soubory. config* viditelné pouze v případě, že je vybraná položka v Průzkumníku řešení soubor *. config* a balíček nebude načten, dokud jeden z těchto příkazů není vybrán.

   Dále pomocí ladicího programu potvrďte, že se balíček načte jenom v případě, že ho očekáváte. Chcete-li ladit TestPackage:

5. Nastavit zarážku <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> metody.

6. Sestavení TestPackage a spusťte ladění.

7. Vytvoření projektu nebo některou aplikaci otevřete.

8. Vyberte libovolný soubor s příponou jinou než *. config*. By neměl být zarážka dosažena.

9. Vyberte soubor *App. config* .

   TestPackage načte a zastaví na zarážce.

## <a name="add-more-rules-for-ui-context"></a>Přidat další pravidla pro kontext uživatelského rozhraní
 Vzhledem k tomu, že pravidla kontextu uživatelského rozhraní jsou logické výrazy, můžete přidat více omezený pravidla pro kontext uživatelského rozhraní. Například v rámci výše uvedené uživatelské rozhraní, můžete určit, že pravidlo platí, pouze když je načtené řešení s projektem. Tímto způsobem se příkazy nezobrazí při otevření souboru *. config* jako samostatného souboru, nikoli jako součást projektu.

```csharp
[ProvideAutoLoad(TestPackage.UIContextGuid)]
[ProvideUIContextRule(TestPackage.UIContextGuid,
    name: "Test auto load",
    expression: "(SingleProject | MultipleProjects) & DotConfig",
    termNames: new[] { "SingleProject", "MultipleProjects","DotConfig" },
    termValues: new[] { VSConstants.UICONTEXT_SolutionHasSingleProject_string , VSConstants.UICONTEXT_SolutionHasMultipleProjects_string , "HierSingleSelectionName:.config$" })]
```

 Nyní odkazuje na výraz tří podmínek. První dvě podmínky, "SingleProject" a "MultipleProjects", najdete v jiných kontextech dobře známé uživatelské rozhraní (pomocí jejich identifikátorů GUID). Třetí výraz "DotConfig" je kontext uživatelského rozhraní založeného na pravidlech definovaný dříve v tomto článku.

## <a name="delayed-activation"></a>Opožděná aktivace
 Pravidla můžou mít volitelné "zpoždění". Zpoždění se zadává v milisekundách. Pokud jsou k dispozici, způsobí zpoždění aktivace nebo deaktivace kontextu uživatelského rozhraní pravidla k změnit podle tohoto časového intervalu. Pokud pravidlo zpět před interval prodlevy, pak nic se nestane. Tento mechanismus je možné "rozložte" kroků inicializace – zejména jednorázová inicializace bez spoléhání se na časovače nebo registrace k oznámením nečinnosti.

 Můžete například zadat pravidla zkušební zatížení mít ke zpoždění 100 milisekund:

```csharp
[ProvideAutoLoad(TestPackage.UIContextGuid)]
[ProvideUIContextRule(TestPackage.UIContextGuid,
    name: "Test auto load",
    expression: "DotConfig",
    termNames: new[] { "DotConfig" },
    termValues: new[] { "HierSingleSelectionName:.config$" },
    delay: 100)]
```

## <a name="term-types"></a>Typy termínů

Tady jsou různé typy podmínek, které jsou podporovány:

|Termín|Popis|
|-|-|
|{nnnnnnnn-nnnn-nnnn-nnnn-nnnnnnnnnnnn}|Identifikátor GUID odkazuje na kontextu uživatelského rozhraní. Výraz bude mít hodnotu true, pokaždé, když se kontextu uživatelského rozhraní v opačném případě je aktivní a false.|
|HierSingleSelectionName:\<vzor >|Výraz bude mít hodnotu true, pokaždé, když se výběr v aktivní hierarchii je jednu položku a název vybrané položky odpovídající regulární výraz platformy .net Dal "vzor".|
|UserSettingsStoreQuery:\<dotaz >|dotaz představuje úplnou cestu do úložiště uživatelských nastavení, která se musí vyhodnotit na nenulovou hodnotu. Dotaz je rozdělit na "kolekce" a "propertyName" za poslední lomítko.|
|ConfigSettingsStoreQuery:\<dotaz >|dotaz představuje úplnou cestu do úložiště nastavení konfigurace, která se musí vyhodnotit na nenulovou hodnotu. Dotaz je rozdělit na "kolekce" a "propertyName" za poslední lomítko.|
|ActiveProjectFlavor:\<projectTypeGuid >|Výraz bude mít hodnotu true, pokaždé, když je aktuálně vybraného projektu flavored (souhrn) a má flavor odpovídající danému projektu typu GUID.|
|ActiveEditorContentType:\<contentType >|Termín se být pravdivá, když je vybraný dokument s daným typem obsahu textového editoru.|
|ActiveProjectCapability:\<výrazu >|Podmínka je pravdivá, pokud aktivní možnosti projektu odpovídají poskytnutému výrazu. Výraz může být něco jako VB &#124; CSharp.|
|SolutionHasProjectCapability:\<výrazu >|Podobně jako výše, ale termín je true, pokud řešení obsahuje načtený projekt, který odpovídá výrazu.|
|SolutionHasProjectFlavor:\<projectTypeGuid >|Výraz bude mít hodnotu true, vždy, když řešení obsahuje projekt, který je flavored (souhrn) a má flavor odpovídající danému projektu typu GUID.|
|ProjectAddedItem:\<vzor >| Podmínka je pravdivá, pokud je do projektu v soluion, který je otevřen, přidán soubor odpovídající "vzoru".|
|ActiveProjectOutputType:\<element outputType >|Podmínka je pravdivá, pokud typ výstupu pro aktivní projekt přesně odpovídá.  Element outputType může být celé číslo nebo <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROJOUTPUTTYPE> typ.|
|ActiveProjectBuildProperty:\<buildProperty>=\<regex>|Podmínka je pravdivá, pokud aktivní projekt má zadanou vlastnost sestavení a hodnota vlastnosti odpovídá poskytnutému filtru Regex. Podrobnější informace o vlastnostech sestavení naleznete [v tématu trvalá data v souborech projektu MSBuild](internals/persisting-data-in-the-msbuild-project-file.md) .|
|SolutionHasProjectBuildProperty:\<buildProperty>=\<regex>|Podmínka je pravdivá, pokud má řešení načtený projekt se zadanou vlastností buildu a hodnotou vlastnosti se shoduje s poskytnutým filtrem Regex.|

## <a name="compatibility-with-cross-version-extension"></a>Kompatibilita s verzí rozšíření

Kontexty uživatelského rozhraní založeného na pravidlech je nová funkce v aplikaci Visual Studio 2015 a nedají se přenést na starší verze. Nepřenosování na starší verze vytvoří problém s rozšířeními/balíčky, které cílí na více verzí sady Visual Studio. Tyto verze by musely být automaticky načteny do Visual Studio 2013 a dříve, ale mohou těžit z kontextů uživatelského rozhraní založeného na pravidlech, aby nedocházelo k automatickému načítání v aplikaci Visual Studio 2015.

Za účelem podpory těchto balíčků teď AutoLoadPackages položky v registru můžete zadat příznak v poli hodnota označující, že má být položka vynecháno v sadě Visual Studio 2015 a vyšší. To můžete udělat tak, že přidáte příznaky možnost <xref:Microsoft.VisualStudio.Shell.PackageAutoLoadFlags>. Teď můžete přidávat rozšíření VSPackages **SkipWhenUIContextRulesActive** umožňuje jejich <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> atribut označuje položku v sadě Visual Studio 2015 a novější ignorovat.
## <a name="extensible-ui-context-rules"></a>Pravidla rozšiřitelného kontextu uživatelského rozhraní

V některých případech balíčky nelze použít statická pravidla kontextu uživatelského rozhraní. Například předpokládejme, že máte balíček podporuje rozšiřitelnost tak, aby stav příkaz je založen na editoru typy podporovaných poskytovateli importované MEF. Pokud je rozšíření podporuje aktuální typ upravit, je příkaz povolen. V takových případech samotný balíček nemůže použít pravidlo kontextu statického uživatelského rozhraní, protože se tyto výrazy mění v závislosti na tom, jaká rozšíření MEF jsou k dispozici.

Aby bylo možné podporovat takové balíčky, kontexty uživatelského rozhraní založeného na pravidlech podporují výraz pevně zakódované "*", který označuje všechny níže uvedené výrazy, které budou spojeny s nebo. To umožňuje hlavnímu balíčku definovat známý kontext uživatelského rozhraní na základě pravidel a spojit jeho stav příkazů s tímto kontextem. Později můžete přidat jakékoli MEF rozšíření určená pro hlavní balíček její podmínky pro editorů, které podporuje bez dopadu na ostatní podmínky nebo hlavní výraz.

Konstruktor <xref:Microsoft.VisualStudio.Shell.ProvideExtensibleUIContextRuleAttribute.%23ctor%2A> dokumentaci ukazuje syntaxi pro extensible pravidla kontextu uživatelského rozhraní.
