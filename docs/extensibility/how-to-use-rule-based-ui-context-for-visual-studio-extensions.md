---
title: 'Postup: Použití kontextu ui založené na pravidlech pro rozšíření sady Visual Studio | Dokumenty společnosti Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 8dd2cd1d-d8ba-49b9-870a-45acf3a3259d
author: acangialosi
ms.author: anthc
ms.workload:
- vssdk
ms.openlocfilehash: de1a1e0a2022482433f81b0b2810b0d201ab7b8f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710599"
---
# <a name="how-to-use-rule-based-ui-context-for-visual-studio-extensions"></a>Postup: Použití kontextu ui založené na pravidlech pro rozšíření sady Visual Studio

Visual Studio umožňuje načítání VSPackages při <xref:Microsoft.VisualStudio.Shell.UIContext>určité známé s jsou aktivovány. Tyto kontexty ui však nejsou jemně zrnité, což ponechává autorům rozšíření jinou možnost než vybrat dostupný kontext ui, který se aktivuje před bodem, který opravdu chtěli, aby se VSPackage načetl. Seznam známých kontextů ui naleznete <xref:Microsoft.VisualStudio.Shell.KnownUIContexts>v tématu .

Načítání balíčků může mít dopad na výkon a jejich načítání dříve, než je potřeba, není osvědčeným postupem. Visual Studio 2015 představil koncept kontexty ui založené na pravidlech, mechanismus, který umožňuje autoři rozšíření definovat přesné podmínky, za kterých je aktivován kontext ui a přidružené VSPackages jsou načteny.

## <a name="rule-based-ui-context"></a>Kontext una založené na pravidlech

"Pravidlo" se skládá z nového kontextu uživatelského rozhraní (GUID) a logického výrazu, který odkazuje na jeden nebo více "Termíny" v kombinaci s logickými operacemi "a", "nebo", "ne". "Termíny" jsou vyhodnocovány dynamicky za běhu a výraz je přehodnocen vždy, když se změní některý z jeho podmínek. Když se výraz vyhodnotí jako true, aktivuje se přidružený kontext ui. V opačném případě je kontext ui deaktivován.

Kontext ui založené na pravidlech lze použít různými způsoby:

1. Určete omezení viditelnosti pro příkazy a okna nástrojů. Okna příkazů/nástrojů můžete skrýt, dokud nebude splněno pravidlo kontextu ui.

2. Jako omezení automatického zatížení: automatické načítání balíčků pouze v případě, že je splněno pravidlo.

3. Jako zpožděný úkol: zpoždění načítání, dokud neuplynul zadaný interval a pravidlo je stále splněno.

   Mechanismus může být použit libovolné rozšíření sady Visual Studio.

## <a name="create-a-rule-based-ui-context"></a>Vytvoření kontextu ui založeného na pravidlech
 Předpokládejme, že máte rozšíření s názvem TestPackage, který nabízí příkaz nabídky, který se vztahuje pouze na soubory s příponou *.config.* Před VS2015 nejlepší možností bylo načíst <xref:Microsoft.VisualStudio.Shell.KnownUIContexts.SolutionExistsAndFullyLoadedContext%2A> TestPackage při aktivaci kontextu ui. Načítání testpackage tímto způsobem není efektivní, protože načtené řešení nemusí obsahovat ani *soubor .config.* Tyto kroky ukazují, jak lze kontext ui založené na pravidlech použít k aktivaci kontextu ui pouze v případě, že je vybrán soubor s příponou *.config,* a načíst testpackage při aktivaci kontextu ui.

1. Definujte nový identifikátor GUID UIContext a <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> přidejte do třídy VSPackage a <xref:Microsoft.VisualStudio.Shell.ProvideUIContextRuleAttribute>.

    Předpokládejme například, že má být přidán nový UIContext "UIContextGuid". Vytvořený identifikátor GUID (můžete vytvořit identifikátor GUID kliknutím na **nástroje** > **vytvořit GUID)** je "8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B". Potom přidáte následující prohlášení uvnitř třídy balíčku:

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

    Tato metadata definují nový identifikátor GUID UIContext (8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B) a výraz odkazující na jeden termín "DotConfig". Termín "DotConfig" je vyhodnocen jako true vždy, když má aktuální výběr\\v aktivní hierarchii název, který odpovídá vzoru regulárního výrazu .config$" (končí *.config*). Hodnota (Výchozí) definuje volitelný název pravidla užitečného pro ladění.

    Hodnoty atributu jsou přidány do pkgdef generované během doby sestavení později.

2. V souboru VSCT pro příkazy TestPackage přidejte příznak DynamicVisibility do příslušných příkazů:

   ```xml
   <CommandFlag>DynamicVisibility</CommandFlag>
   ```

3. V části Viditelnost v VSCT navážete příslušné příkazy na nový identifikátor GUID UIContext definovaný v #1:

   ```xml
   <VisibilityConstraints>
       <VisibilityItem guid="guidTestPackageCmdSet" id="TestId"  context="UIContextGuid"/>
   </VisibilityConstraints>
   ```

4. V části Symboly přidejte definici kontextu uicontext:

   ```xml
   <GuidSymbol name="UIContextGuid" value="{8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B}" />
   ```

    Příkazy kontextové nabídky * \** pro soubory .config budou viditelné pouze v případě, že vybraná položka v průzkumníku řešení je *soubor .config* a balíček nebude načten, dokud nebude vybrán jeden z těchto příkazů.

   Dále použijte ladicí program k potvrzení, že balíček načte pouze v případě, že očekáváte, že. Ladění balíčku TestPackage:

5. Nastavte zarážku <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> v metodě.

6. Vytvořte testpackage a spusťte ladění.

7. Vytvořte projekt nebo otevřete.

8. Vyberte libovolný soubor s jinou příponou než *.config*. Zarážka by neměla být přístupů.

9. Vyberte soubor *App.Config.*

   TestPackage načte a zastaví na zarážky.

## <a name="add-more-rules-for-ui-context"></a>Přidání dalších pravidel pro kontext ui
 Vzhledem k tomu, že pravidla kontextu ui jsou logické výrazy, můžete přidat další pravidla s omezeným přístupem pro kontext ui. Například ve výše uvedeném kontextu ui můžete určit, že pravidlo platí pouze při načtení řešení s projektem. Tímto způsobem se příkazy nezobrazí, pokud otevřete soubor *.config* jako samostatný soubor, nikoli jako součást projektu.

```csharp
[ProvideAutoLoad(TestPackage.UIContextGuid)]
[ProvideUIContextRule(TestPackage.UIContextGuid,
    name: "Test auto load",
    expression: "(SingleProject | MultipleProjects) & DotConfig",
    termNames: new[] { "SingleProject", "MultipleProjects","DotConfig" },
    termValues: new[] { VSConstants.UICONTEXT_SolutionHasSingleProject_string , VSConstants.UICONTEXT_SolutionHasMultipleProjects_string , "HierSingleSelectionName:.config$" })]
```

 Nyní výraz odkazuje na tři termíny. První dva termíny, "SingleProject" a "MultipleProjects", odkazují na jiné známé kontexty uživatelského rozhraní (podle jejich GUID). Třetí termín "DotConfig" je kontext ui založené na pravidlech definované dříve v tomto článku.

## <a name="delayed-activation"></a>Zpožděná aktivace
 Pravidla mohou mít volitelné "Zpoždění". Zpoždění je zadáno v milisekundách. Pokud je k dispozici, zpoždění způsobí, že aktivace nebo deaktivace kontextu ui pravidla se zpožděním v tomto časovém intervalu. Pokud se pravidlo změní zpět před intervalem zpoždění, nic se nestane. Tento mechanismus lze použít k "roztavit" inicializační kroky - zejména jednorázové inicializace bez spoléhání se na časovače nebo registraci pro oznámení nečinnosti.

 Můžete například zadat pravidlo zatížení testu, které má zpoždění 100 milisekund:

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

Zde jsou různé typy termínů, které jsou podporovány:

|Označení|Popis|
|-|-|
|{nnnnnnnn-nnnn-nnnn-nnnn-nnnn-nnnnnnnnnnnn}|Identifikátor GUID odkazuje na kontext uživatelského rozhraní. Termín bude true vždy, když kontext ui je aktivní a false jinak.|
|HierSingleSelectionName:\<vzor>|Termín bude splněn vždy, když je výběr v aktivní hierarchii jedinou položkou a název vybrané položky odpovídá regulárnímu výrazu .Net zadanému "vzorem".|
|UserSettingsStoreQuery:\<> dotazu|"dotaz" představuje úplnou cestu do úložiště uživatelských nastavení, které musí vyhodnotit na nenulovou hodnotu. Dotaz je rozdělen do "kolekce" a "propertyName" na poslední lomítko.|
|ConfigSettingsStoreQuery:\<dotaz>|"dotaz" představuje úplnou cestu do úložiště nastavení konfigurace, která musí být vyhodnocena na nenulovou hodnotu. Dotaz je rozdělen do "kolekce" a "propertyName" na poslední lomítko.|
|ActiveProjectFlavor:\<projectTypeGuid>|Termín bude true vždy, když je aktuálně vybraný projekt ochucený (agregován) a má chuť odpovídající zadanému identifikátoru GUID typu projektu.|
|ActiveEditorContentType:\<contentType>|Termín bude splněn, pokud je vybraný dokument textovým editorem s daným typem obsahu. Poznámka: Při přejmenování vybraného dokumentu se tento termín neaktualizuje, dokud není soubor uzavřen a znovu otevřen.|
|ActiveProjectCapability:\<> výraz|Termín je splněn, pokud aktivní možnosti projektu odpovídají poskytnutému výrazu. Výraz může být něco jako VB &#124; CSharp.|
|SolutionHasProjectCapability:\<Výraz>|Podobně jako výše, ale termín je true, pokud řešení má všechny načtený projekt, který odpovídá výrazu.|
|SolutionHasProjectFlavor:\<projectTypeGuid>|Termín bude true vždy, když řešení má projekt, který je ochucené (agregované) a má chuť odpovídající daný typ projektu GUID.|
|ProjectAddedItem:\<> vzoru| Termín je true, když soubor odpovídající "vzor" je přidán do projektu v rozpustku, který je otevřen.|
|ActiveProjectOutputType:\<outputType>|Termín je true, když typ výstupu pro aktivní projekt přesně odpovídá.  OutputType může být celé číslo <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROJOUTPUTTYPE> nebo typ.|
|ActiveProjectBuildProperty:\<buildProperty\<>=> regulárního výrazu|Termín je true, pokud aktivní projekt má zadanou vlastnost sestavení a hodnota vlastnosti odpovídá filtru regulárního výrazu. Další podrobnosti o vlastnostech sestavení naleznete v části [Trvalá data v souborech projektu MSBuild.](internals/persisting-data-in-the-msbuild-project-file.md)|
|SolutionHasProjectBuildProperty:\<buildProperty\<>= regulární>|Termín je true, pokud řešení má načtený projekt se zadanou vlastnost sestavení a hodnota vlastnosti odpovídá regulární filtr k dispozici.|

## <a name="compatibility-with-cross-version-extension"></a>Kompatibilita s rozšířením s křížovou verzí

Kontexty ui založené na pravidlech je nová funkce v sadě Visual Studio 2015 a nebude přenesena na předchozí verze. Není portování na starší verze vytvoří problém s rozšíření/balíčky, které se zaměřují na více verzí sady Visual Studio. Tyto verze by musely být automaticky načteny v sadě Visual Studio 2013 a starší, ale mohou využívat kontexty ui založené na pravidlech, aby se zabránilo automatickému načítání v sadě Visual Studio 2015.

Za účelem podpory těchto balíčků, AutoLoadPackages položky v registru nyní můžete poskytnout příznak ve svém poli hodnoty označující, že položka by měla být přeskočena v sadě Visual Studio 2015 a vyšší. To lze provést přidáním možnosti příznaky . <xref:Microsoft.VisualStudio.Shell.PackageAutoLoadFlags> VSPackages nyní můžete přidat **SkipWhenUIContextRulesActive** možnost jejich <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> atribut označující položka by měla být ignorována v sadě Visual Studio 2015 a vyšší.
## <a name="extensible-ui-context-rules"></a>Rozšiřitelná kontextová pravidla ui

V některých případě balíčky nelze použít statické pravidla kontextu ui. Předpokládejme například, že máte balíček podporující rozšiřitelnost tak, aby stav příkazu byl založen na typech editoru, které jsou podporovány importovanými zprostředkovateli MEF. Příkaz je povolen, pokud existuje rozšíření podporující aktuální typ úprav. V takových případech balíček sám nelze použít statické pravidlo kontextu rozhraní a uzamulovat, protože podmínky by se změnit v závislosti na rozšíření MEF jsou k dispozici.

Za účelem podpory těchto balíčků, kontexty ui založené na pravidlech podporují pevně zakódovaný výraz "*", který označuje všechny níže uvedené podmínky, které budou spojeny s OR. To umožňuje hlavní balíček definovat známý kontext ui založené na pravidlech a svázat jeho stav příkazu do tohoto kontextu. Poté jakékoli rozšíření MEF určené pro hlavní balíček můžete přidat své termíny pro editory, které podporuje bez ovlivnění jiných termínů nebo hlavnívýraz.

Dokumentace konstruktoru <xref:Microsoft.VisualStudio.Shell.ProvideExtensibleUIContextRuleAttribute.%23ctor%2A> zobrazuje syntaxi pro rozšiřitelná pravidla kontextu ui.
