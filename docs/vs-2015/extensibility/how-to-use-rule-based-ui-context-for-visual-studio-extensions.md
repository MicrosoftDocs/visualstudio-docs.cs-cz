---
title: 'Postupy: použití kontextu uživatelského rozhraní založeného na pravidlo pro rozšíření | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8dd2cd1d-d8ba-49b9-870a-45acf3a3259d
caps.latest.revision: 8
ms.author: gregvanl
ms.openlocfilehash: 431f9b53fd9b678e16e7fddeeb997ddfcfea6f11
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53062542"
---
# <a name="how-to-use-rule-based-ui-context-for-visual-studio-extensions"></a>Postupy: použití kontextu uživatelského rozhraní založeného na pravidlo pro rozšíření sady Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio umožňuje načítání rozšíření VSPackages při některých dobře známé <xref:Microsoft.VisualStudio.Shell.UIContext>s aktivují. Ale kontexty uživatelského rozhraní nejsou velmi dobře grained, byste museli opustit autoři rozšíření žádná volba, ale k výběru dostupná kontextu uživatelského rozhraní, který se aktivuje před bodem VSPackage načíst opravdu chtěli. Seznam dobře známé uživatelské rozhraní kontextech najdete v tématu <xref:Microsoft.VisualStudio.Shell.KnownUIContexts>.

 Načítají se balíčky může mít dopad na výkon a jejich načtení dříve, než se v případě potřeby zapíná není nejlepším postupem. Visual Studio 2015 představil nový koncept kontexty uživatelského rozhraní založeného na pravidlech, mechanismus, který umožňuje autorům rozšíření určit přesné podmínky, za kterých se aktivuje kontextu uživatelského rozhraní a načíst přidružené balíčky VSPackages.

## <a name="rule-based-ui-context"></a>Kontext založený na pravidlech uživatelského rozhraní
 "Pravidlo" se skládá z nového kontextu uživatelského rozhraní (GUID) a logický výraz, který odkazuje na jeden nebo více "Terms" kombinovat pomocí logické "a", "nebo", "not" operace. "Terms" jsou vyhodnoceny dynamicky za běhu a výraz se znovu zhodnotí pokaždé, když některý z jeho podmínek změny. Pokud je výraz vyhodnocen jako true, je aktivováno souvisejícího kontextu uživatelského rozhraní. V opačném případě je deaktivován kontextu uživatelského rozhraní.

 Podle pravidel kontextu uživatelského rozhraní lze použít v mnoha různými způsoby:

1. Zadejte omezení viditelnost příkazů a oken nástrojů. Příkazy a nástroje pro windows můžete skrýt, až do splnění pravidla kontextu uživatelského rozhraní.

2. Jako automatické omezení zatížení: automatické načtení balíčků jenom v případě splnění pravidla

3. Zpožděná úloha: zpoždění načítání až do uplynutí zadaného intervalu a pravidlo je stále splněny.

   Mechanismu, který mohou využívat všechny rozšíření sady Visual Studio.

## <a name="create-a-rule-based-ui-context"></a>Vytvoření uživatelského rozhraní založeného na pravidlo kontextu
 Předpokládejme, že máte rozšíření volá TestPackage, která nabízí příkaz nabídky, která se vztahuje pouze na soubory s příponou ".config". Před VS2015, nejlepší možností je načíst TestPackage při <xref:Microsoft.VisualStudio.Shell.KnownUIContexts.SolutionExistsAndFullyLoadedContext%2A> kontextu uživatelského rozhraní se aktivovala. Toto není efektivní, protože načtené řešení nesmí obsahovat i soubor .config. Dejte nám najdete v tématu Jak kontextu uživatelského rozhraní založeného na pravidlech lze aktivovat pouze v případě, že soubor s příponou .config kontextu uživatelského rozhraní je vybraná a zatížení TestPackage při aktivaci tohoto kontextu uživatelského rozhraní.

1. Definovat nový identifikátor GUID UIContext a přidejte do třídy balíčku VSPackage <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> a <xref:Microsoft.VisualStudio.Shell.ProvideUIContextRuleAttribute>.

    Například předpokládejme, že nové UIContext "UIContextGuid" se má přidat. Vytvoří identifikátor GUID (identifikátor GUID můžete vytvořit kliknutím na Nástroje -> vytvořit guid) je "8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B". Pak přidejte následující uvnitř třídy balíčku:

   ```csharp
   public const string UIContextGuid = "8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B";
   ```

    Atributy, přidejte následující: (podrobnosti o těchto atributů budou vysvětlena dále)

   ```csharp
   [ProvideAutoLoad(TestPackage.UIContextGuid)]
   [ProvideUIContextRule(TestPackage.UIContextGuid,
       name: "Test auto load",
       expression: "DotConfig",
       termNames: new[] { "DotConfig" },
       termValues: new[] { "HierSingleSelectionName:.config$" })]
   ```

    Tato metadata definovat nový identifikátor GUID UIContext (8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B) a výraz odkazuje na jeden termín "DotConfig". Termín "DotConfig" vyhodnotí jako true, vždy, když aktuální výběr v aktivní hierarchii má název, který odpovídá vzoru regulárního výrazu "\\.config$" (končí řetězcem ".config"). (Výchozí) Určuje volitelný název pravidla, které jsou užitečné pro ladění.

    Hodnoty atributu jsou přidány do pkgdef generovány během doby sestavení později.

2. V souboru VSCT pro příkazy TestPackage přidejte příznak "DynamicVisibility" příslušnými příkazy:

   ```xml
   <CommandFlag>DynamicVisibility</CommandFlag>
   ```

3. V části viditelnosti VSCT tie příslušné příkazy, které nový UIContext GUID definované v #1:

   ```xml
   <VisibilityConstraints>
       <VisibilityItem guid="guidTestPackageCmdSet" id="TestId"  context="guidTestUIContext"/>
   </VisibilityConstraints>
   ```

4. V části symboly přidáte definici UIContext:

   ```xml
   <GuidSymbol name="guidTestUIContext" value="{8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B}" />
   ```

    Příkazy místní nabídky pro soubory *.config teď budou viditelné pouze v případě, že na vybranou položku v Průzkumníku řešení je soubor ".config" a balíčku nebudou načteny, dokud jeden z těchto příkazů je vybrána.

   V dalším kroku použijeme ladicího programu k potvrzení, že načte balíček pouze při Očekáváme, že ho chcete. Chcete-li ladit TestPackage:

5. Nastavit zarážku <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> metody.

6. Sestavení TestPackage a spusťte ladění.

7. Vytvoření projektu nebo některou aplikaci otevřete.

8. Vyberte libovolný soubor s příponou jinou než .config. By neměl být zarážka dosažena.

9. Vyberte soubor App.Config.

   TestPackage načte a zastaví na zarážce.

## <a name="adding-more-rules-for-ui-context"></a>Přidání další pravidla pro kontext uživatelského rozhraní
 Vzhledem k tomu, že pravidla kontextu uživatelského rozhraní jsou logické výrazy, můžete přidat více omezený pravidla pro kontext uživatelského rozhraní. Například v rámci výše uvedené uživatelské rozhraní, můžete určit, že pravidlo platí, pouze když je načtené řešení s projektem. Tímto způsobem příkazy nezobrazí Pokud můžete otevřít soubor ".config" jako samostatný soubor, nikoli jako součást projektu.

```csharp
[ProvideAutoLoad(TestPackage.UIContextGuid)]
[ProvideUIContextRule(TestPackage.UIContextGuid,
    name: "Test auto load",
    expression: "(SingleProject | MultipleProjects) & DotConfig",
    termNames: new[] { "SingleProject", "MultipleProjects","DotConfig" },
    termValues: new[] { VSConstants.UICONTEXT_SolutionHasSingleProject_string , VSConstants.UICONTEXT_SolutionHasMultipleProjects_string , "HierSingleSelectionName:.config$" })]
```

 Nyní odkazuje na výraz tří podmínek. První dvě podmínky, "SingleProject" a "MultipleProjects", najdete v jiných kontextech dobře známé uživatelské rozhraní (pomocí jejich identifikátorů GUID). Třetí výraz "DotConfig" je založený na pravidlech kontextu uživatelského rozhraní jsme definovali dříve.

## <a name="delayed-activation"></a>Odloženou aktivací
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

## <a name="term-types"></a>Typy termín
 Tady jsou různé typy podmínek, které jsou podporovány:

|||
|-|-|
|{nnnnnnnn-nnnn-nnnn-nnnn-nnnnnnnnnnnn}|Identifikátor GUID odkazuje na kontextu uživatelského rozhraní. Výraz bude mít hodnotu true, pokaždé, když se kontextu uživatelského rozhraní v opačném případě je aktivní a false.|
|HierSingleSelectionName:\<vzor >|Výraz bude mít hodnotu true, pokaždé, když se výběr v aktivní hierarchii je jednu položku a název vybrané položky odpovídající regulární výraz platformy .net Dal "vzor".|
|UserSettingsStoreQuery:\<dotaz >|"dotaz" představuje úplnou cestu do úložiště uživatelských nastavení, která se musí vyhodnotit na nenulovou hodnotu. Dotaz je rozdělit na "kolekce" a "propertyName" za poslední lomítko.|
|ConfigSettingsStoreQuery:\<dotaz >|"dotaz" představuje úplnou cestu do úložiště nastavení konfigurace, který musí být vyhodnocen na nenulovou hodnotu. Dotaz je rozdělit na "kolekce" a "propertyName" za poslední lomítko.|
|ActiveProjectFlavor:\<projectTypeGuid >|Výraz bude mít hodnotu true, pokaždé, když je aktuálně vybraného projektu flavored (souhrn) a má flavor odpovídající danému projektu typu GUID.|
|ActiveEditorContentType:\<contentType >|Termín se být pravdivá, když je vybraný dokument s daným typem obsahu textového editoru.|
|ActiveProjectCapability:\<výrazu >|Termín má hodnotu true, když zadaného výrazu odpovídá možnosti aktivního projektu. Výraz může být třeba VB &#124; CSharp|
|SolutionHasProjectCapability:\<výrazu >|Podobně jako výše, ale termín je true, pokud řešení obsahuje načtený projekt, který odpovídá výrazu.|
|SolutionHasProjectFlavor:\<projectTypeGuid >|Výraz bude mít hodnotu true, vždy, když řešení obsahuje projekt, který je flavored (souhrn) a má flavor odpovídající danému projektu typu GUID.|



## <a name="compatibility-with-cross-version-extension"></a>Kompatibilita s verzí rozšíření
 Pravidla na základě kontextu uživatelského rozhraní je nová funkce v sadě Visual Studio 2015 a nebude přenést do starší verze. Vzniká tak problém s rozšíření/balíčky, které cílí více verzí sady Visual Studio, který by mohl být automaticky načíst v sadě Visual Studio 2013 a starší, ale může přinést pravidlo na základě uživatelského rozhraní kontexty zabránit automatické načítání v aplikaci Visual Studio 2015.

 Za účelem podpory těchto balíčků teď AutoLoadPackages položky v registru můžete zadat příznak v poli hodnota označující, že má být položka vynecháno v sadě Visual Studio 2015 a vyšší. To můžete udělat tak, že přidáte příznaky možnost <xref:Microsoft.VisualStudio.Shell.PackageAutoLoadFlags>. Teď můžete přidávat rozšíření VSPackages **SkipWhenUIContextRulesActive** umožňuje jejich <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> atribut označuje položku v sadě Visual Studio 2015 a novější ignorovat.

## <a name="extensible-ui-context-rules"></a>Rozšiřitelné kontextu pravidla
 V některých případech balíčky nelze použít statická pravidla kontextu uživatelského rozhraní. Například předpokládejme, že máte balíček podporuje rozšiřitelnost tak, aby stav příkaz je založen na editoru typy podporovaných poskytovateli importované MEF. Pokud je rozšíření podporuje aktuální typ upravit, je příkaz povolen. V takových případech samotném balíčku nelze statické kontextu uživatelského rozhraní pravidlo použít, protože podmínky změní v závislosti na tom, jaké MEF rozšíření jsou k dispozici.

 Za účelem podpory těchto balíčků, pravidlo na základě kontextu uživatelského rozhraní podporují výraz pevně zakódované "*", který označuje všechny níže uvedené podmínky se jde připojit k nebo. Tato možnost povoluje pro hlavní balíček k definování známé pravidlo na základě kontextu uživatelského rozhraní a provázat postupy stavu příkazu k tomuto kontextu. Později můžete přidat jakékoli MEF rozšíření určená pro hlavní balíček její podmínky pro editorů, které podporuje bez dopadu na ostatní podmínky nebo hlavní výraz.

 Konstruktor <xref:Microsoft.VisualStudio.Shell.ProvideExtensibleUIContextRuleAttribute.%23ctor%2A> dokumentaci ukazuje syntaxi pro extensible pravidla kontextu uživatelského rozhraní.
