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
ms.openlocfilehash: 9a48725c0877110e969a98deb8c03b3181d31153
ms.sourcegitcommit: 68f893f6e472df46f323db34a13a7034dccad25a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/15/2020
ms.locfileid: "77277698"
---
# <a name="visual-studio-integration-msbuild"></a>Integrace se sadou Visual Studio (MSBuild)
Visual Studio je hostitelem [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] načtení a sestavení spravovaných projektů. Vzhledem k tomu, že [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] zodpovídá za projekt, téměř jakýkoli projekt ve formátu [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] lze úspěšně použít v [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], a to i v případě, že projekt byl vytvořen jiným nástrojem a má přizpůsobený proces sestavení.

 Tento článek popisuje konkrétní aspekty [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] hostování [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], které byste měli vzít v úvahu při přizpůsobování projektů a *. cílí* na soubory, které chcete načíst a sestavit v [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. To vám pomůže zajistit [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] funkce jako IntelliSense a ladění pro vlastní projekt.

 Další informace o C++ projektech naleznete v tématu [Project Files](/cpp/build/reference/project-files).

## <a name="project-file-name-extensions"></a>Přípony názvů souborů projektu
 Nástroj *MSBuild. exe* rozpoznává všechny přípony názvů souborů projektu, které odpovídají vzoru *.\*proj*. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] však rozpoznává pouze podmnožinu těchto přípon názvů souborů projektu, které určují systém projektu specifický pro jazyk, který načte projekt. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] nemá jazykově neutrální [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] systém projektu.

 Například systém projektu [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] načítá soubory *. csproj* , ale [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] není schopna načíst soubor *. xxproj* . Soubor projektu pro zdrojové soubory v libovolném jazyce musí používat stejné rozšíření jako [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] nebo [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] soubory projektu, které mají být načteny do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].

## <a name="well-known-target-names"></a>Známé názvy cílů
 Kliknutím na příkaz **sestavit** v [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] spustí výchozí cíl v projektu. Tento cíl je často také pojmenován `Build`. Výběrem příkazu **znovu sestavit** nebo **vyčistit** se pokusíte spustit cíl se stejným názvem v projektu. Kliknutím na **publikovat** se spustí cíl s názvem `PublishOnly` v projektu.

## <a name="configurations-and-platforms"></a>Konfigurace a platformy
 Konfigurace jsou reprezentovány v [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] projektech podle vlastností seskupených v `PropertyGroup` elementu, který obsahuje atribut `Condition`. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] prohlíží tyto podmínky, aby bylo možné vytvořit seznam konfigurací projektu a platforem, které se mají zobrazit. Chcete-li úspěšně extrahovat tento seznam, musí být podmínky ve formátu podobném následujícímu:

```xml
Condition=" '$(Configuration)|$(Platform)' == 'Debug|AnyCPU' "
Condition=" '$(Configuration)' == 'Release' " 
Condition=" '$(Something)|$(Configuration)|$(SomethingElse)' == 'xxx|Debug|yyy' "
```

 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] se pro tento účel vyhledají podmínky pro prvky `PropertyGroup`, `ItemGroup`, `Import`, Property a Item.

## <a name="additional-build-actions"></a>Další akce sestavení
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] umožňuje změnit název typu položky souboru v projektu pomocí vlastnosti **Akce sestavení** okna **vlastností souboru** . Názvy typů položek **kompilovat**, **EmbeddedResource**, **Content**a **none** jsou vždy uvedeny v této nabídce společně s jinými názvy typů položek, které jsou již v projektu. Aby bylo zajištěno, že všechny vlastní názvy typů položek jsou vždy k dispozici v této nabídce, můžete přidat názvy k typu položky s názvem `AvailableItemName`. Například přidáním následujícího do souboru projektu se přidá vlastní typ **JScript** do této nabídky pro všechny projekty, které je naimportují:

```xml
<ItemGroup>
    <AvailableItemName Include="JScript"/>
</ItemGroup>
```

> [!NOTE]
> Některé názvy typů položek jsou speciální pro [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], ale nejsou uvedeny v tomto rozevíracím seznamu.

## <a name="in-process-compilers"></a>Vnitroprocesové kompilátory
 Pokud je to možné, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] se pokusí o zvýšení výkonu pomocí vnitroprocesové verze kompilátoru [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]. (Netýká se [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)].) Aby to fungovalo správně, musí se splnit následující podmínky:

- V cíli projektu musí existovat úkol s názvem `Vbc` pro [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] projekty.

- Parametr `UseHostCompilerIfAvailable` úlohy musí být nastaven na hodnotu true.

## <a name="design-time-intellisense"></a>Technologie IntelliSense v době návrhu
 Chcete-li získat podporu technologie IntelliSense v [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] před tím, než sestavení vygenerovalo výstupní sestavení, musí být splněny následující podmínky:

- Musí existovat cíl s názvem `Compile`.

- Buď cíl `Compile` nebo jedna z jeho závislostí musí volat úlohu kompilátoru pro projekt, například `Csc` nebo `Vbc`.

- Buď cíl `Compile` nebo jedna z jeho závislostí musí způsobit, že kompilátor obdrží všechny nezbytné parametry pro technologii IntelliSense, zejména všechny odkazy.

- Podmínky uvedené v části [kompilátory v rámci procesu](#in-process-compilers) musí být splněné.

## <a name="build-solutions"></a>Vytváření řešení
 V rámci [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]je řazení souborů řešení a sestavení projektu řízeno [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] sebe sama. Při sestavování řešení pomocí nástroje *MSBuild. exe* v příkazovém řádku [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] analyzuje soubor řešení a seřadí sestavení projektu. V obou případech jsou projekty sestaveny jednotlivě v pořadí závislosti a z odkazů typu projekt na projekt nejsou provázány. Naopak když jsou jednotlivé projekty sestaveny pomocí nástroje *MSBuild. exe*, jsou odkazy na projekt na projekt procházeny.

 Při sestavování uvnitř [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]vlastnost `$(BuildingInsideVisualStudio)` nastavena na `true`. To lze použít ve vašem projektu nebo souborech *. targets* , aby se sestavení mohlo chovat jinak.

## <a name="display-properties-and-items"></a>Zobrazení vlastností a položek
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] rozpoznává určité názvy vlastností a jejich hodnoty. Například následující vlastnost v projektu způsobí, že se **aplikace systému Windows** zobrazí v poli **Typ aplikace** v **Návrháři projektu**.

```xml
<OutputType>WinExe</OutputType>
```

 Hodnotu vlastnosti lze upravit v **Návrháři projektu** a Uložit do souboru projektu. Pokud je takové vlastnosti předána neplatnou hodnotou ruční úpravou, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] zobrazí upozornění, když je projekt načten, a nahradí neplatnou hodnotu výchozí hodnotou.

 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] rozumí výchozím nastavením pro některé vlastnosti. Tyto vlastnosti, nebudou trvale uloženy v souboru projektu, pokud mají jiné než výchozí hodnoty.

 Vlastnosti s libovolnými názvy nejsou v [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]zobrazeny. Chcete-li upravit libovolné vlastnosti v [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], je nutné otevřít soubor projektu v editoru XML a upravit je ručně. Další informace naleznete v části [Úpravy souborů projektu v aplikaci Visual Studio](#edit-project-files-in-visual-studio) dále v tomto tématu.

 Položky definované v projektu s libovolnými názvy typů položek jsou ve výchozím nastavení zobrazeny v **Průzkumník řešení** pod jejich uzlem projektu. Chcete-li skrýt položku ze zobrazení, nastavte metadata `Visible` na hodnotu `false`. Například následující položka se bude účastnit procesu sestavení, ale nebude se zobrazovat v **Průzkumník řešení**.

```xml
<ItemGroup>
    <IntermediateFile Include="cache.temp">
        <Visible>false</Visible>
    </IntermediateFile>
</ItemGroup>
```

> [!NOTE]
> Metadata `Visible` jsou **Průzkumník řešení** pro C++ projekty ignorována. Položky budou vždy zobrazeny, i když je `Visible` nastaveno na hodnotu NEPRAVDA.

 Ve výchozím nastavení se nezobrazují položky deklarované v souborech importovaných do projektu. Položky vytvořené během procesu sestavení nejsou nikdy zobrazeny v **Průzkumník řešení**.

## <a name="conditions-on-items-and-properties"></a>Podmínky pro položky a vlastnosti
 Během sestavení jsou všechny podmínky úplně dodrženy.

 Při určování zobrazovaných hodnot vlastností se vlastnosti, které [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] považují za závislé na konfiguraci, vyhodnocuje jinak než vlastnosti, které považují za nezávislé na konfiguraci. Pro vlastnosti, které považuje za závislé na konfiguraci, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] nastaví správné vlastnosti `Configuration` a `Platform` a pokyn [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] k opakovanému vyhodnocení projektu. Pro vlastnosti považuje konfiguraci za nezávislou, že je neurčité, jak se vyhodnotí podmínky.

 Podmíněné výrazy u položek se vždycky ignorují pro účely rozhodování o tom, jestli se má položka zobrazit v **Průzkumník řešení**.

## <a name="debugging"></a>Ladění
 Aby bylo možné najít a spustit výstupní sestavení a připojit ladicí program, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] potřebuje vlastnosti `OutputPath`, `AssemblyName`a `OutputType` správně definované. Ladicí program se nepodaří připojit, pokud proces sestavení nezpůsobil, že kompilátor vygeneroval soubor *. pdb* .

## <a name="design-time-target-execution"></a>Provádění cílů v době návrhu
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] se při načtení projektu pokusí provést cíle s určitými názvy. Mezi tyto cíle patří `Compile`, `ResolveAssemblyReferences`, `ResolveCOMReferences`, `GetFrameworkPaths`a `CopyRunEnvironmentFiles`. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] spouští tyto cíle, aby bylo možné inicializovat kompilátor pro poskytování technologie IntelliSense, ladicí program lze inicializovat a odkazy zobrazené v Průzkumník řešení lze vyřešit. Pokud tyto cíle nejsou k dispozici, projekt se načte a sestaví správně, ale prostředí pro dobu návrhu v [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] nebude plně funkční.

## <a name="edit-project-files-in-visual-studio"></a>Upravit soubory projektu v sadě Visual Studio
 Chcete-li upravit [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] projekt přímo, můžete otevřít soubor projektu v editoru XML sady Visual Studio.

#### <a name="to-unload-and-edit-a-project-file-in-visual-studio"></a>Uvolnění projektu a jeho úprava v sadě Visual Studio

1. V **Průzkumník řešení**otevřete místní nabídku pro projekt a pak zvolte **Uvolnit projekt**.

     Projekt je označený **(není k dispozici)** .

2. V **Průzkumník řešení**otevřete místní nabídku pro nedostupný projekt a pak zvolte **Upravit \<soubor projektu >** .

     Soubor projektu se otevře v editoru XML sady Visual Studio.

3. Upravte, uložte a zavřete soubor projektu.

4. V **Průzkumník řešení**otevřete místní nabídku pro nedostupný projekt a pak zvolte **znovu načíst projekt**.

## <a name="intellisense-and-validation"></a>Technologie IntelliSense a ověřování
 Při použití editoru XML k úpravám souborů projektu technologie IntelliSense a ověřování je ovládána soubory schématu [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]. Tyto soubory jsou nainstalovány v mezipaměti schématu, které lze nalézt v *\<instalační adresář sady Visual Studio > \Xml\Schemas\1033\MSBuild*.

 Základní [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] typy jsou definovány v *Microsoft. Build. Core. xsd* a běžné typy používané [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] jsou definovány v *Microsoft. Build. CommonTypes. xsd*. Chcete-li přizpůsobit schémata, abyste měli IntelliSense a ověřování pro vlastní názvy typů položek, vlastnosti a úkoly, můžete buď upravit *Microsoft. Build. xsd*, nebo vytvořit vlastní schéma, které obsahuje schémata CommonTypes nebo Core. Pokud vytvoříte vlastní schéma, budete muset nasměrovat editor XML, abyste ho našli pomocí okna **vlastnosti** .

## <a name="edit-loaded-project-files"></a>Úpravy načtených souborů projektu
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ukládá do mezipaměti obsah souborů projektu a souborů importovaných soubory projektu. Pokud upravíte načtený soubor projektu, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] vás automaticky vyzve k opětovnému načtení projektu, aby se změny projevily. Ale pokud upravíte soubor importovaný načteným projektem, nebudou bez výzvy znovu načíst a musíte odebrat a znovu načtěte projekt ručně, aby se změny projevily.

## <a name="output-groups"></a>Skupiny výstupu
 Několik cílů definovaných v *Microsoft. Common. targets* má názvy končící na `OutputGroups` nebo `OutputGroupDependencies`. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] volá tyto cíle pro získání konkrétních seznamů výstupů projektu. Například cíl `SatelliteDllsProjectOutputGroup` vytvoří seznam všech satelitních sestavení, které vytvoří sestavení. Tyto skupiny výstupu jsou používány funkce, jako je publikování, nasazení a meziprojektové odkazy. Projekty, které je nedefinují, budou načteny a sestaveny v [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], ale některé funkce nemusí fungovat správně.

## <a name="reference-resolution"></a>Překlad odkazů
 Referenční řešení je proces vyhledání skutečných sestavení pomocí referenčních položek uložených v souboru projektu. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] musí aktivovat řešení odkazů, aby se zobrazily podrobné vlastnosti pro každý odkaz v okně **vlastnosti** . Následující seznam popisuje tři typy odkazů a jejich výsledek.

- Odkazy na sestavení:

   Systém projektu zavolá cíl s známým názvem `ResolveAssemblyReferences`. Tento cíl by měl vypracovávat položky s názvem typu položky `ReferencePath`. Každá z těchto položek by měla mít specifikaci položky (hodnota atributu `Include` položky) obsahující úplnou cestu k odkazu. Položky by měly mít všechna metadata ze vstupních položek prošla kromě následujících nových metadat:

  - `CopyLocal`, která označuje, zda má být sestavení zkopírováno do výstupní složky, nastavte na hodnotu true nebo false.

  - `OriginalItemSpec`obsahující specifikaci původní položky odkazu.

  - Pokud byla přeložena z adresáře .NET Framework, je `ResolvedFrom`nastavena na hodnotu {TargetFrameworkDirectory}.

- Odkazy modelu COM:

   Systém projektu zavolá cíl s známým názvem `ResolveCOMReferences`. Tento cíl by měl vypracovávat položky s názvem typu položky `ComReferenceWrappers`. Každá z těchto položek by měla mít specifikaci obsahující úplnou cestu ke zprostředkovatelům sestavení pro odkaz COM. Položky by měly mít všechna metadata ze vstupních položek předaných do, kromě nových metadat s názvem `CopyLocal`, určující, zda má být sestavení zkopírováno do výstupní složky, nastaveno na hodnotu true nebo false.

- Nativní odkazy

   Systém projektu zavolá cíl s známým názvem `ResolveNativeReferences`. Tento cíl by měl vypracovávat položky s názvem typu položky `NativeReferenceFile`. Položky by měly mít všechna metadata ze vstupních položek předaných spolu s novou částí metadat s názvem `OriginalItemSpec`, která obsahuje specifikaci původní položky odkazu.

## <a name="performance-shortcuts"></a>Klávesové zkratky výkonu
 Použijete-li prostředí Visual Studio IDE pro spuštění ladění (buď výběrem klávesy F5, nebo výběrem možnosti **ladit** > **Spustit ladění** na panelu nabídek), nebo chcete-li sestavit projekt (například řešení **sestavení** > **sestavení**), proces sestavení používá funkci Rychlá aktualizace ke zvýšení výkonu. V některých případech, kde přizpůsobená sestavení vytvoří soubory, které zase získají sestavení kontrola rychlé aktualizace nesprávně identifikuje změněné soubory. Projekty, které vyžadují důkladnější kontroly aktualizace, mohou vypnout rychlou kontrolu nastavením proměnné prostředí `DISABLEFASTUPTODATECHECK=1`. Alternativně projekty můžete nastavit to jako vlastnost MSBuild v projektu nebo v souboru, který importuje.

 Pro pravidelná sestavení v sadě Visual Studio se nevztahuje kontrola rychlé aktualizace a projekt bude sestaven jako kdyby jste vyvolali sestavení z příkazového řádku.

## <a name="see-also"></a>Viz také
- [Postupy: rozšiřování procesu sestavení sady Visual Studio](../msbuild/how-to-extend-the-visual-studio-build-process.md)
- [Spuštění sestavení z integrovaného vývojového prostředí (IDE)](../msbuild/starting-a-build-from-within-the-ide.md)
- [Registrovat rozšíření .NET Framework](../msbuild/registering-extensions-of-the-dotnet-framework.md)
- [Koncepty nástroje MSBuild](../msbuild/msbuild-concepts.md)
- [Item – Element (MSBuild)](../msbuild/item-element-msbuild.md)
- [Property – element (MSBuild)](../msbuild/property-element-msbuild.md)
- [Target – element (MSBuild)](../msbuild/target-element-msbuild.md)
- [CSc – úloha](../msbuild/csc-task.md)
- [Vbc – úloha](../msbuild/vbc-task.md)
