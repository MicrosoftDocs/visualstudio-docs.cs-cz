---
title: Integrace sady Visual Studio (MSBuild)
titleSuffix: ''
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, reference resolution
- MSBuild, well-known target names
- MSBuild, hosting
- MSBuild, editing project files
- MSBuild, Visual Studio integration
- MSBuild, IntelliSense
- MSBuild, output groups
- MSBuild, in-process compilers
- MSBuild, design-time target execution
ms.assetid: 06cd6d7f-8dc1-4e49-8a72-cc9e331d7bca
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3468ab5a6a185a759ab43229758c0ff4e9d00e35
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "77631195"
---
# <a name="visual-studio-integration-msbuild"></a>Integrace visual studia (MSBuild)

Visual Studio hostuje MSBuild načíst a sestavit spravované projekty. Vzhledem k tomu, že MSBuild je zodpovědný za projekt, téměř každý projekt ve formátu MSBuild lze úspěšně použít v sadě Visual Studio, i v případě, že projekt byl vytvořen jiným nástrojem a má vlastní proces sestavení.

 Tento článek popisuje konkrétní aspekty visual studio je MSBuild hosting, který by měl být považován při přizpůsobení projektů a *.cíle* soubory, které chcete načíst a sestavit v sadě Visual Studio. Ty vám pomohou zajistit, že funkce sady Visual Studio, jako je Technologie IntelliSense a ladění, fungují pro váš vlastní projekt.

 Informace o projektech jazyka C++ naleznete [v tématu Project files](/cpp/build/reference/project-files).

## <a name="project-file-name-extensions"></a>Přípony názvů souborů projektu

 *Nástroj MSBuild.exe* rozpozná všechny přípony názvu souboru projektu odpovídající vzoru *.\* proj*. Visual Studio však rozpozná pouze podmnožinu těchto přípon názvů souborů projektu, které určují systém projektu specifické pro jazyk, který bude načítat projekt. Visual Studio nemá jazykově neutrální systém projektu založené na MSBuild.

 Například systém projektu C# načte soubory *CSProJ,* ale Visual Studio není schopno načíst soubor *XXProJ.* Soubor projektu pro zdrojové soubory v libovolném jazyce musí používat stejnou příponu jako soubory projektu jazyka Visual Basic nebo C#, které mají být načteny v sadě Visual Studio.

## <a name="well-known-target-names"></a>Známá cílová jména

 Kliknutím na příkaz **Sestavit** v sadě Visual Studio se spustí výchozí cíl v projektu. Často je tento cíl `Build`také pojmenován . Výběr příkazu **Znovu sestavit** nebo **Vyčistit** se pokusí provést cíl se stejným názvem v projektu. Kliknutím na **publikovat** spustíte cíl pojmenovaný `PublishOnly` v projektu.

## <a name="configurations-and-platforms"></a>Konfigurace a platformy

 Konfigurace jsou reprezentovány v projektech MSBuild `PropertyGroup` vlastnostmi `Condition` seskupenými do prvku, který obsahuje atribut. Visual Studio se dívá na tyto podmínky za účelem vytvoření seznamu konfigurace projektu a platformy pro zobrazení. Chcete-li úspěšně extrahovat tento seznam, podmínky musí mít formát podobný následujícímu:

```xml
Condition=" '$(Configuration)|$(Platform)' == 'Debug|AnyCPU' "
Condition=" '$(Configuration)' == 'Release' " 
Condition=" '$(Something)|$(Configuration)|$(SomethingElse)' == 'xxx|Debug|yyy' "
```

 Visual Studio se dívá `PropertyGroup` `ItemGroup`na `Import`podmínky na , , vlastnost a položky prvky pro tento účel.

## <a name="additional-build-actions"></a>Další akce sestavení

 Visual Studio umožňuje změnit název typu položky souboru v projektu pomocí **vlastnosti Build Action** okna **Vlastnosti souboru.** V této nabídce jsou vždy uvedeny názvy typů **kompilace**, **EmbeddedResource**, **Content**a **None** jsou vždy uvedeny spolu s dalšími názvy typů položek, které jsou již v projektu uvedeny. Chcete-li zajistit, aby v této nabídce byly vždy k dispozici `AvailableItemName`názvy typů vlastních položek, můžete je přidat k typu s názvem . Například přidáním následujícího textu do souboru projektu přidáte do této nabídky vlastní typ **Jazyka JScript** pro všechny projekty, které jej importují:

```xml
<ItemGroup>
    <AvailableItemName Include="JScript"/>
</ItemGroup>
```

> [!NOTE]
> Některé názvy typů položek jsou pro visual studio zvláštní, ale nejsou uvedeny v tomto rozevíracím seznamu.

## <a name="in-process-compilers"></a>Neprocesové kompilátory

 Pokud je to možné, Visual Studio se pokusí použít v procesu verzi kompilátoru jazyka Visual Basic pro zvýšení výkonu. (Nevztahuje se na C#.) Aby to fungovalo správně, musí být splněny následující podmínky:

- V cíli projektu musí být úkol pojmenovaný `Vbc` pro projekty jazyka.

- Parametr `UseHostCompilerIfAvailable` úlohy musí být nastaven na hodnotu true.

## <a name="design-time-intellisense"></a>Technologie IntelliSense v době návrhu

 Chcete-li získat podporu Technologie IntelliSense v sadě Visual Studio dříve, než sestavení vygeneruje výstupní sestavení, musí být splněny následující podmínky:

- Musí být cíl `Compile`s názvem .

- `Compile` Cíl nebo jedna z jeho závislostí musí volat úkol kompilátoru pro projekt, například `Csc` nebo `Vbc`.

- `Compile` Cíl nebo jedna z jeho závislostí musí způsobit, že kompilátor obdrží všechny potřebné parametry pro technologie IntelliSense, zejména všechny odkazy.

- Musí být splněny podmínky uvedené v části [Kompilátory v procesu.](#in-process-compilers)

## <a name="build-solutions"></a>Vytváření řešení

 V rámci sady Visual Studio jsou soubor řešení a pořadí sestavení projektu řízeny samotným Visual Studio. Při vytváření řešení s *msbuild.exe* na příkazovém řádku MSBuild analyzuje soubor řešení a objednávky sestavení projektu. V obou případech jsou projekty sestaveny jednotlivě v pořadí závislostí a odkazy na projekt nejsou provázány. Naopak při vytváření jednotlivých projektů pomocí *msbuild.exe*jsou provázány odkazy na projekt.

 Při vytváření uvnitř sady `$(BuildingInsideVisualStudio)` Visual Studio `true`je vlastnost nastavena na . To lze použít v projektu nebo *.targets* soubory způsobit sestavení chovat odlišně.

## <a name="display-properties-and-items"></a>Zobrazit vlastnosti a položky

 Visual Studio rozpozná určité názvy vlastností a hodnoty. Například následující vlastnost v projektu **způsobí,** že aplikace systému Windows se zobrazí v poli **Typ aplikace** v **Návrháři projektu**.

```xml
<OutputType>WinExe</OutputType>
```

 Hodnotu vlastnosti lze upravit v **návrháři projektu** a uložit do souboru projektu. Pokud taková vlastnost je dána neplatnou hodnotu ruční úpravy, Visual Studio zobrazí upozornění při načtení projektu a nahradit neplatnou hodnotu s výchozí hodnotou.

 Visual Studio chápe výchozí hodnoty pro některé vlastnosti. Tyto vlastnosti nebudou trvalé do souboru projektu, pokud nemají jiné než výchozí hodnoty.

 Vlastnosti s libovolnými názvy nejsou v sadě Visual Studio zobrazeny. Chcete-li upravit libovolné vlastnosti v sadě Visual Studio, musíte otevřít soubor projektu v editoru XML a upravit je ručně. Další informace naleznete v části [Úpravy souborů projektu v sadě Visual Studio](#edit-project-files-in-visual-studio) dále v tomto tématu.

 Položky definované v projektu s libovolnými názvy typů položek jsou ve výchozím nastavení zobrazeny v **Průzkumníku řešení** v rámci uzlu projektu. Chcete-li položku skrýt `Visible` ze zobrazení, nastavte metadata na . `false` Například následující položka se bude podílet na procesu sestavení, ale nebudou zobrazeny v **Průzkumníku řešení**.

```xml
<ItemGroup>
    <IntermediateFile Include="cache.temp">
        <Visible>false</Visible>
    </IntermediateFile>
</ItemGroup>
```

> [!NOTE]
> Metadata `Visible` jsou ignorovány **Průzkumníkem řešení** pro projekty jazyka C++. Položky se vždy `Visible` zobrazí, i když je nastavena na false.

 Položky deklarované v souborech importovaných do projektu nejsou ve výchozím nastavení zobrazeny. Položky vytvořené během procesu sestavení se nikdy nezobrazí v **Průzkumníku řešení**.

## <a name="conditions-on-items-and-properties"></a>Podmínky pro položky a vlastnosti

 Během sestavení jsou plně respektovány všechny podmínky.

 Při určování hodnoty vlastností k zobrazení, vlastnosti, které Visual Studio považuje za závislé na konfiguraci jsou vyhodnocovány jinak než vlastnosti považuje konfiguraci nezávislé. Pro vlastnosti, které považuje za `Configuration` závislé `Platform` na konfiguraci, Visual Studio nastaví vlastnosti a vhodně a pokyn MSBuild převyhodnotit projekt. Pro vlastnosti, které považuje za nezávislé konfigurace, je neurčitý, jak budou vyhodnoceny podmínky.

 Podmíněné výrazy na položky jsou vždy ignorovány pro účely rozhodování, zda má být položka zobrazena v **Průzkumníku řešení**.

## <a name="debugging"></a>ladění

 Chcete-li najít a spustit výstupní sestavení a připojit ladicí `OutputPath` `AssemblyName`program, `OutputType` visual studio potřebuje vlastnosti , a správně definovány. Ladicí program se nepodaří připojit, pokud proces sestavení nezpůsobil, že kompilátor vygeneroval soubor *PDB.*

## <a name="design-time-target-execution"></a>Provedení cíle v době návrhu

 Visual Studio se pokusí spustit cíle s určitými názvy při načtení projektu. Mezi tyto `Compile` `ResolveAssemblyReferences`cíle `ResolveCOMReferences` `GetFrameworkPaths`patří `CopyRunEnvironmentFiles`, , , a . Visual Studio spustí tyto cíle tak, aby kompilátor lze inicializovat poskytnout IntelliSense, ladicí program lze inicializovat a odkazy zobrazené v Průzkumníku řešení lze vyřešit. Pokud tyto cíle nejsou k dispozici, projekt se načte a sestavení správně, ale prostředí návrhu v sadě Visual Studio nebude plně funkční.

## <a name="edit-project-files-in-visual-studio"></a>Úpravy souborů projektu v sadě Visual Studio

 Chcete-li přímo upravit projekt MSBuild, můžete otevřít soubor projektu v editoru XML sady Visual Studio.

#### <a name="to-unload-and-edit-a-project-file-in-visual-studio"></a>Uvolnění projektu a jeho úprava v sadě Visual Studio

1. V **Průzkumníku řešení**otevřete místní nabídku projektu a pak zvolte **Uvolnit projekt**.

     Projekt je označen **(není k dispozici).**

2. V **Průzkumníku řešení**otevřete místní nabídku pro nedostupný projekt a pak zvolte **Upravit \<soubor projektu>**.

     Soubor projektu se otevře v editoru XML sady Visual Studio.

3. Upravte, uložte a zavřete soubor projektu.

4. V **Průzkumníku řešení**otevřete místní nabídku pro nedostupný projekt a pak zvolte **Znovu načíst Project**.

## <a name="intellisense-and-validation"></a>Technologie IntelliSense a validace

 Při použití editoru XML k úpravám souborů projektu je technologie IntelliSense a ověřování řízena soubory schématu MSBuild. Ty jsou nainstalovány v mezipaměti schématu, kterou lze nalézt v * \<instalačním adresáři sady Visual Studio>\Xml\Schemas\1033\MSBuild*.

 Základní typy MSBuild jsou definovány v *Microsoft.Build.Core.xsd* a běžné typy používané visual studio jsou definovány v *Microsoft.Build.CommonTypes.xsd*. Chcete-li přizpůsobit schémata tak, aby měla technologie IntelliSense a ověřování vlastních názvů typů položek, vlastností a úkolů, můžete buď upravit *soubor Microsoft.Build.xsd*, nebo vytvořit vlastní schéma, které obsahuje schémata CommonTypes nebo Core. Pokud vytvoříte vlastní schéma, budete muset nasměrovat editor XML, aby ho našel pomocí okna **Vlastnosti.**

## <a name="edit-loaded-project-files"></a>Úprava načtených souborů projektu

 Visual Studio ukládá do mezipaměti obsah souborů projektu a soubory importované soubory projektu. Pokud upravíte načtený soubor projektu, Visual Studio vás automaticky vyzve k opětovnému načtení projektu tak, aby se změny projevily. Pokud však upravíte soubor importovaný načteným projektem, nebude žádná výzva k opětovnému načtení a je nutné projekt uvolnit a znovu načíst ručně, aby se změny projevily.

## <a name="output-groups"></a>Výstupní skupiny

 Několik cílů definovaných v *souboru Microsoft.Common.targets* má názvy končící na `OutputGroups` . `OutputGroupDependencies` Visual Studio volá tyto cíle získat konkrétní seznamy výstupů projektu. `SatelliteDllsProjectOutputGroup` Cíl například vytvoří seznam všech satelitních sestavení, která sestavení vytvoří. Tyto výstupní skupiny jsou používány funkcemi, jako je publikování, nasazení a projekt na odkazy na projekt. Projekty, které je nedefinují, se načtou a vytvoří v sadě Visual Studio, ale některé funkce nemusí fungovat správně.

## <a name="reference-resolution"></a>Referenční rozlišení

 Rozlišení odkazů je proces použití referenčních položek uložených v souboru projektu k vyhledání skutečných sestavení. Visual Studio musí aktivovat rozlišení odkazů, aby bylo možné zobrazit podrobné vlastnosti pro každý odkaz v okně **Vlastnosti.** Následující seznam popisuje tři typy odkazů a způsob jejich řešení.

- Odkazy na montáž:

   Systém projektu volá cíl s dobře `ResolveAssemblyReferences`známý název . Tento cíl by měl vyrábět `ReferencePath`položky s názvem typu položky . Každá z těchto položek by měla mít `Include` specifikaci položky (hodnotu atributu položky) obsahující úplnou cestu k odkazu. Položky by měly mít všechna metadata ze vstupních položek prošel kromě následující nová metadata:

  - `CopyLocal`, označující, zda má být sestavení zkopírováno do výstupní složky, nastaveno na hodnotu true nebo false.

  - `OriginalItemSpec`, který obsahuje původní specifikaci položky odkazu.

  - `ResolvedFrom`, nastavte na "{TargetFrameworkDirectory}", pokud byl vyřešen z adresáře rozhraní .NET Framework.

- Odkazy com:

   Systém projektu volá cíl s dobře `ResolveCOMReferences`známý název . Tento cíl by měl vyrábět `ComReferenceWrappers`položky s názvem typu položky . Každá z těchto položek by měla mít specifikaci položky obsahující úplnou cestu k sestavení interop pro odkaz COM. Položky by měly mít všechna metadata ze vstupních položek předávané, kromě nových metadat s názvem `CopyLocal`, označující, zda má být sestavení zkopírováno do výstupní složky, nastaveno na hodnotu true nebo false.

- Nativní odkazy

   Systém projektu volá cíl s dobře `ResolveNativeReferences`známý název . Tento cíl by měl vyrábět `NativeReferenceFile`položky s názvem typu položky . Položky by měly mít všechna metadata ze vstupních položek prošel, `OriginalItemSpec`kromě nové části metadat s názvem , obsahující původní specifikace položky odkazu.

## <a name="performance-shortcuts"></a>Zástupce výkonu

 Pokud použijete IDE sady Visual Studio ke spuštění ladění (buď výběrem klávesy F5 nebo **výběrem** > ladění**start ladění** na řádku nabídek) nebo k sestavení projektu (například **sestavení** > **sestavení řešení**), proces sestavení používá rychlou kontrolu aktualizace ke zlepšení výkonu. V některých případech, kdy vlastní sestavení vytvořit soubory, které získat vestavěný zase, rychlá kontrola aktualizace není správně identifikovat změněné soubory. Projekty, které vyžadují důkladnější kontroly aktualizací, mohou `DISABLEFASTUPTODATECHECK=1`rychle zkontrolovat nastavením proměnné prostředí . Alternativně projekty můžete nastavit jako MSBuild vlastnost v projektu nebo v souboru, který projekt importuje.

 Pro pravidelné sestavení v sadě Visual Studio, rychlé kontroly aktualizace neplatí a projekt bude stavět, jako byste vyvolali sestavení na příkazovém řádku.

## <a name="see-also"></a>Viz také

- [Postup: Rozšíření procesu sestavení sady Visual Studio](../msbuild/how-to-extend-the-visual-studio-build-process.md)
- [Spuštění sestavení z ide](../msbuild/starting-a-build-from-within-the-ide.md)
- [Registrace rozšíření rozhraní .NET Framework](../msbuild/registering-extensions-of-the-dotnet-framework.md)
- [Koncepty MSBuild](../msbuild/msbuild-concepts.md)
- [Prvek položky (MSBuild)](../msbuild/item-element-msbuild.md)
- [Element vlastnosti (MSBuild)](../msbuild/property-element-msbuild.md)
- [Cílový prvek (MSBuild)](../msbuild/target-element-msbuild.md)
- [Úkol CsC](../msbuild/csc-task.md)
- [Úloha Vbc](../msbuild/vbc-task.md)
