---
title: 'Postupy: použití kontextu uživatelského rozhraní založeného na pravidlech pro rozšíření | Microsoft Docs'
ms.date: 11/15/2016
ms.topic: conceptual
ms.assetid: 8dd2cd1d-d8ba-49b9-870a-45acf3a3259d
caps.latest.revision: 8
ms.author: gregvanl
ms.openlocfilehash: 26f66f635b2c248af01067d9dbd96fd997593593
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/30/2020
ms.locfileid: "85535561"
---
# <a name="how-to-use-rule-based-ui-context-for-visual-studio-extensions"></a>Postupy: Použití kontextu uživatelského rozhraní založeného na pravidlech pro rozšíření sady Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio umožňuje načítání VSPackage v případě, že <xref:Microsoft.VisualStudio.Shell.UIContext> jsou aktivovány určité dobře známé typy. Tyto kontexty uživatelského rozhraní ale nejsou velmi jemné, takže autoři rozšíření nezvolí, ale chtějí vybrat dostupný kontext uživatelského rozhraní, který se aktivuje předtím, než si chce chtít VSPackage načíst. Seznam známých kontextů uživatelského rozhraní naleznete v tématu <xref:Microsoft.VisualStudio.Shell.KnownUIContexts> .

 Načítání balíčků může mít dopad na výkon a jejich načítání dřív, než je potřeba, není osvědčeným postupem. Visual Studio 2015 představil koncept kontextů uživatelského rozhraní založeného na pravidlech, mechanizmus, který správcům rozšíření umožňuje definovat přesné podmínky, za kterých je kontext uživatelského rozhraní aktivovaný a načítají se přidružené sady VSPackage.

## <a name="rule-based-ui-context"></a>Kontext uživatelského rozhraní založeného na pravidlech
 "Pravidlo" se skládá z nového kontextu uživatelského rozhraní (GUID) a logického výrazu, který odkazuje na jeden nebo více podmínek v kombinaci s logickými operacemi "a", "nebo", "nikoli". "Terms" jsou vyhodnocovány dynamicky za běhu a výraz je znovu vyhodnocován při každé změně jeho podmínek. Když je výraz vyhodnocen jako true, je aktivován přidružený kontext uživatelského rozhraní. V opačném případě je kontext uživatelského rozhraní deaktivovaný.

 Kontext uživatelského rozhraní založeného na pravidlech lze použít různými způsoby:

1. Zadejte omezení viditelnosti pro příkazy a okna nástrojů. Okna příkazů a nástrojů můžete skrýt, dokud nesplníte pravidlo kontextu uživatelského rozhraní.

2. Jako omezení automatického načtení: automaticky načíst balíčky pouze v případě splnění pravidla

3. Zpožděná úloha: zpožděné načítání až do zadaného intervalu a pravidlo se pořád splní.

   Mechanismus může použít jakékoli rozšíření sady Visual Studio.

## <a name="create-a-rule-based-ui-context"></a>Vytvoření kontextu uživatelského rozhraní založeného na pravidlech
 Předpokládejme, že máte rozšíření s názvem TestPackage, které nabízí příkaz nabídky, který se vztahuje pouze na soubory s příponou. config. Před VS2015 bylo nejlepší možností načíst TestPackage při <xref:Microsoft.VisualStudio.Shell.KnownUIContexts.SolutionExistsAndFullyLoadedContext%2A> aktivaci kontextu uživatelského rozhraní. To není efektivní, protože načtené řešení nemusí ani obsahovat soubor. config. Podíváme se, jak se kontext uživatelského rozhraní založeného na pravidlech dá použít k aktivaci kontextu uživatelského rozhraní jenom v případě, že je vybraný soubor s příponou. config, a když se tento kontext uživatelského rozhraní aktivuje, načte se TestPackage.

1. Definujte nový identifikátor GUID UIContext a přidejte ho do třídy VSPackage <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> a <xref:Microsoft.VisualStudio.Shell.ProvideUIContextRuleAttribute> .

    Řekněme například, že se přidá nový UIContext "UIContextGuid". Vytvořený identifikátor GUID (můžete vytvořit GUID kliknutím na nástroje-> vytvořit GUID) je "8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B". Pak do své třídy balíčku přidáte následující:

   ```csharp
   public const string UIContextGuid = "8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B";
   ```

    Pro atributy přidejte následující: (podrobnosti o těchto atributech budou vysvětleny později)

   ```csharp
   [ProvideAutoLoad(TestPackage.UIContextGuid)]
   [ProvideUIContextRule(TestPackage.UIContextGuid,
       name: "Test auto load",
       expression: "DotConfig",
       termNames: new[] { "DotConfig" },
       termValues: new[] { "HierSingleSelectionName:.config$" })]
   ```

    Tato metadata definují nový identifikátor GUID UIContext (8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B) a výraz odkazující na jeden výraz "DotConfig". Termín "DotConfig" se vyhodnocuje na hodnotu true, kdykoli aktuální výběr v aktivní hierarchii má název, který odpovídá vzoru regulárního výrazu " \\ . config $" (končí ". config"). Hodnota (výchozí) definuje nepovinný název pro pravidlo, které je užitečné pro ladění.

    Hodnoty atributu jsou přidány do pkgdef generované během doby sestavení později.

2. Do souboru VSCT pro příkazy TestPackage přidejte příznak "DynamicVisibility" do příslušných příkazů:

   ```xml
   <CommandFlag>DynamicVisibility</CommandFlag>
   ```

3. V části viditelnosti v VSCT se spojí příslušné příkazy k novému identifikátoru GUID UIContext definovanému v #1:

   ```xml
   <VisibilityConstraints>
       <VisibilityItem guid="guidTestPackageCmdSet" id="TestId"  context="guidTestUIContext"/>
   </VisibilityConstraints>
   ```

4. V části symboly přidejte definici UIContext:

   ```xml
   <GuidSymbol name="guidTestUIContext" value="{8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B}" />
   ```

    Nyní budou příkazy místní nabídky pro soubory *. config viditelné pouze v případě, že je vybraná položka v Průzkumníku řešení soubor ". config" a balíček nebude načten, dokud není vybrán některý z těchto příkazů.

   Teď použijeme ladicí program k potvrzení, že se balíček načte jenom v případě, že to očekáváme. Ladění TestPackage:

5. Nastavte zarážku v <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> metodě.

6. Sestavte TestPackage a spusťte ladění.

7. Vytvořte projekt nebo ho otevřete.

8. Vyberte libovolný soubor s příponou jinou než. config. Zarážka by neměla být přístupná.

9. Vyberte soubor App.Config.

   TestPackage načte a zastaví na zarážce.

## <a name="adding-more-rules-for-ui-context"></a>Přidání dalších pravidel pro kontext uživatelského rozhraní
 Vzhledem k tomu, že pravidla kontextu uživatelského rozhraní jsou logické výrazy, můžete přidat více pravidel s omezením pro kontext uživatelského rozhraní. Například ve výše uvedeném kontextu uživatelského rozhraní můžete určit, že se pravidlo bude vztahovat pouze v případě, že je načteno řešení s projektem. Tímto způsobem se příkazy nezobrazí, pokud otevřete soubor ". config" jako samostatný soubor, nikoli jako součást projektu.

```csharp
[ProvideAutoLoad(TestPackage.UIContextGuid)]
[ProvideUIContextRule(TestPackage.UIContextGuid,
    name: "Test auto load",
    expression: "(SingleProject | MultipleProjects) & DotConfig",
    termNames: new[] { "SingleProject", "MultipleProjects","DotConfig" },
    termValues: new[] { VSConstants.UICONTEXT_SolutionHasSingleProject_string , VSConstants.UICONTEXT_SolutionHasMultipleProjects_string , "HierSingleSelectionName:.config$" })]
```

 Nyní výraz odkazuje na tři výrazy. První dvě slova "SingleProject" a "MultipleProjects" odkazují na další dobře známé kontexty uživatelského rozhraní (podle jejich identifikátorů GUID). Třetí výraz "DotConfig" je kontext uživatelského rozhraní založeného na pravidlech, který jsme definovali dříve.

## <a name="delayed-activation"></a>Opožděná aktivace
 Pravidla mohou mít volitelné "zpoždění". Zpoždění je zadáno v milisekundách. Pokud je přítomen, zpoždění způsobí, že aktivace nebo deaktivace kontextu uživatelského rozhraní pravidla bude zpožděna v daném časovém intervalu. Pokud se pravidlo změní zpátky před intervalem zpoždění, nedojde k žádné akci. Tento mechanismus lze použít k "uspořádání" inicializačních kroků – zejména při jednorázové inicializaci bez spoléhání na časovače nebo registrace pro nečinné oznámení.

 Například můžete zadat pravidlo zátěže testu, které bude mít zpoždění 100 milisekund:

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
 Tady jsou různé typy termínů, které jsou podporované:

|Typ podmínky|Popis|
|-|-|
|{nnnnnnnn-nnnn-nnnn-nnnn-nnnnnnnnnnnn}|Identifikátor GUID odkazuje na kontext uživatelského rozhraní. Pokud je kontext uživatelského rozhraní aktivní a v opačném případě false, bude podmínka pravdivá.|
|HierSingleSelectionName:\<pattern>|Podmínka bude pravdivá vždy, když je výběr v aktivní hierarchii jedinou položkou a název vybrané položky odpovídá regulárnímu výrazu .NET, který je dán "vzorem".|
|UserSettingsStoreQuery:\<query>|dotaz představuje úplnou cestu do úložiště uživatelských nastavení, která se musí vyhodnotit na nenulovou hodnotu. Dotaz je rozdělen na "shromažďování" a "propertyName" na poslední lomítko.|
|ConfigSettingsStoreQuery:\<query>|dotaz představuje úplnou cestu do úložiště nastavení konfigurace, která se musí vyhodnotit na nenulovou hodnotu. Dotaz je rozdělen na "shromažďování" a "propertyName" na poslední lomítko.|
|ActiveProjectFlavor:\<projectTypeGuid>|Termín bude platit vždy, když je aktuálně zvolený projekt ve formátu (agregovaný) a má charakter, který odpovídá zadanému identifikátoru GUID typu projektu.|
|ActiveEditorContentType:\<contentType>|Pokud je vybraný dokument textový editor s daným typem obsahu, bude podmínka pravdivá.|
|ActiveProjectCapability:\<Expression>|Podmínka je pravdivá, pokud aktivní možnosti projektu odpovídají poskytnutému výrazu. Výraz může být například VB &#124; CSharp|
|SolutionHasProjectCapability:\<Expression>|Podobně jako v tomto případě je podmínka pravdivá, pokud řešení obsahuje libovolný načtený projekt, který odpovídá výrazu.|
|SolutionHasProjectFlavor:\<projectTypeGuid>|Podmínka bude pravdivá vždy, když má řešení projekt, který má charakter (agregovaný) a má charakter odpovídající danému identifikátoru GUID typu projektu.|

## <a name="compatibility-with-cross-version-extension"></a>Kompatibilita s rozšířením pro různé verze
 Kontexty uživatelského rozhraní založené na pravidlech je nová funkce v aplikaci Visual Studio 2015 a nelze ji přenést na starší verze. Tím se vytvoří problém s rozšířeními/balíčky, které cílí na více verzí sady Visual Studio, které by musely být automaticky načteny do Visual Studio 2013 a dříve, ale mohou těžit z kontextů uživatelského rozhraní založeného na pravidlech, aby nedocházelo k automatickému načítání v aplikaci Visual Studio 2015.

 Aby bylo možné podporovat takové balíčky, mohou položky AutoLoadPackages v registru nyní v poli hodnota poskytnout příznak označující, že by položka měla být v aplikaci Visual Studio 2015 nebo vyšší. To lze provést přidáním možnosti Flags do <xref:Microsoft.VisualStudio.Shell.PackageAutoLoadFlags> . Sady VSPackage teď můžou do svého atributu přidat možnost **SkipWhenUIContextRulesActive** <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> , která značí, že by položka měla být v aplikaci Visual Studio 2015 a vyšší.

## <a name="extensible-ui-context-rules"></a>Pravidla rozšiřitelného kontextu uživatelského rozhraní
 V některých případech balíčky nemůžou používat pravidla statických kontextů uživatelského rozhraní. Předpokládejme například, že máte balíček podporující rozšiřitelnost, takže stav příkazu je založen na typech editorů, které jsou podporovány importovanými zprostředkovateli MEF. Příkaz je povolen, pokud existuje rozšíření podporující aktuální typ úprav. V takových případech samotný balíček nemůže použít pravidlo kontextu statického uživatelského rozhraní, protože se tyto výrazy mění v závislosti na tom, která rozšíření MEF jsou k dispozici.

 Aby bylo možné podporovat takové balíčky, kontexty uživatelského rozhraní založeného na pravidlech podporují výraz pevně zakódované "*", který označuje všechny níže uvedené výrazy, které budou spojeny s nebo. To umožňuje hlavnímu balíčku definovat známý kontext uživatelského rozhraní na základě pravidel a spojit svůj stav příkazu s tímto kontextem. Pak jakékoli rozšíření MEF cílené pro hlavní balíček může přidat své výrazy pro editory, které podporuje, aniž by to ovlivnilo jiné výrazy nebo hlavní výraz.

 V dokumentaci k konstruktoru se <xref:Microsoft.VisualStudio.Shell.ProvideExtensibleUIContextRuleAttribute.%23ctor%2A> zobrazuje syntaxe pro pravidla kontextu rozšiřitelného uživatelského rozhraní.
