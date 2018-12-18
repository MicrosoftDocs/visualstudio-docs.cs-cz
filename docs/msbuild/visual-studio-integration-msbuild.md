---
title: Integrace sady Visual Studio (MSBuild)
titleSuffix: ''
ms.custom: seodec18
ms.date: 11/04/2016
ms.technology: msbuild
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7449e8585cd9f1db8a4a43cddf8092f1a92c9758
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53052420"
---
# <a name="visual-studio-integration-msbuild"></a>Integrace se sadou Visual Studio (MSBuild)
Visual Studio hostuje [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] k načtení a sestavení spravovaných projektů. Protože [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] je zodpovědné za projekt, téměř každý projekt ve [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] formát může být úspěšně použit v [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], i když byl autorem jiný nástroj a má vlastní proces sestavení projektu.  
  
 Tento článek popisuje konkrétní aspekty [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]společnosti [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] hostování, který by měl zvážit při přizpůsobení projektů a *.targets* soubory, které chcete k načtení a sestavení [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Ty vám pomohou Ujistěte se, že [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] funkce jako IntelliSense a ladění práce pro váš vlastní projekt.  
  
 Informace o projektech C++, naleznete v tématu [soubory projektu](/cpp/ide/project-files).  
  
## <a name="project-file-name-extensions"></a>Přípony názvů souborů projektu  
 *MSBuild.exe* rozpozná všechny příponu názvu souboru projektu odpovídající vzoru *.\* proj*. Ale [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] rozpozná pouze podmnožinu těchto přípon názvů souborů projektu, které určují projekt specifický pro jazyk systému, který načte projekt. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] nemá jazykově neutrální [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] systém projektu.  
  
 Například [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] projektu zatížení systému *.csproj* soubory, ale [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] není schopen načíst *.xxproj* souboru. Soubor projektu pro zdrojové soubory v libovolném jazyce musí používat stejnou příponu jako [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] nebo [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] soubory mají být načteny v projektu [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
## <a name="well-known-target-names"></a>Známé názvy cílů  
 Kliknutím **sestavení** v příkaz [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] spustí výchozí cíl v projektu. Často, má tento cíl také název `Build`. Výběr **znovu sestavit** nebo **Vyčistit** příkaz se pokusí provést cíl se stejným názvem v projektu. Kliknutím na **publikovat** spustí cíle s názvem `PublishOnly` v projektu.  
  
## <a name="configurations-and-platforms"></a>Konfigurace a platformy  
 Konfigurace jsou reprezentovány v [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] projekty podle vlastností seskupených v `PropertyGroup` element, který obsahuje `Condition` atribut. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] kontroluje tyto podmínky za účelem vytvoření seznamu projektových konfigurací a platforem pro zobrazení. Chcete-li úspěšně extrahovat tento seznam, musí být podmínky ve formátu podobném následujícímu:  
  
```xml  
Condition=" '$(Configuration)|$(Platform)' == 'Debug|AnyCPU' "  
Condition=" '$(Configuration)' == 'Release' "   
Condition=" '$(Something)|$(Configuration)|$(SomethingElse)' == 'xxx|Debug|yyy' "  
```  
  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] zkontroluje podmínky `PropertyGroup`, `ItemGroup`, `Import`, vlastnost a prvky položek pro tento účel.  
  
## <a name="additional-build-actions"></a>Další akce sestavení  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Umožňuje změnit název položky typu souboru v projektu s **akce sestavení** vlastnost **vlastnosti souboru** okna. **Kompilace**, **EmbeddedResource**, **obsahu**, a **žádný** názvy typů položek jsou vždy uvedeny v této nabídce a všechny další názvy typů položek již v váš projekt. Aby všechny vlastní názvy typů položek jsou vždy k dispozici v této nabídce můžete přidat názvy typů položek s názvem `AvailableItemName`. Například přidáním následujícího do vašeho souboru projektu bude přidán vlastní typ **JScript** k této nabídce pro všechny projekty, které importuje:  
  
```xml  
<ItemGroup>  
    <AvailableItemName Include="JScript"/>  
</ItemGroup>  
```  
  
> [!NOTE]
>  Některé názvy typů položek jsou pro [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] , ale nejsou uvedené v tomto rozevíracím seznamu.  
  
## <a name="in-process-compilers"></a>Vnitroprocesové kompilátory  
 Pokud je to možné, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] se pokusí použít verzi v procesu [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] kompilátoru pro zajištění zvýšeného výkonu. (Nevztahuje se na [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)].) Aby to fungovalo správně musí být splněny následující podmínky:  
  
- V cíli projektu, musí být úkol s názvem `Vbc` pro [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] projekty.  
  
- `UseHostCompilerIfAvailable` Parametr úkolu musí být nastaven na hodnotu true.  
  
## <a name="design-time-intellisense"></a>Technologie IntelliSense v době návrhu  
 Chcete-li získat podporu technologie IntelliSense [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] předtím, než sestavení vygeneruje výstupné sestavení, musí být splněny následující podmínky:  
  
-   Musí existovat cíl s názvem `Compile`.  
  
-   Buď `Compile` cíl nebo některá z jeho závislostí musí volat úkol kompilátoru pro projekt, jako například `Csc` nebo `Vbc`.  
  
-   Buď `Compile` cíl nebo některá z jeho závislostí musí způsobit, že kompilátor získá všechny potřebné parametry pro technologii IntelliSense, zvláště všechny odkazy.  
  
-   Podmínky uvedené v [vnitroprocesové kompilátory](#in-process-compilers) oddílu musí být splněny.  
  
## <a name="build-solutions"></a>Vytváření řešení  
 V rámci [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], soubor řešení a pořadí sestavení projektu řízeno pomocí [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] samotný. Při sestavování řešení s *msbuild.exe* na příkazovém řádku [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] analyzuje soubor řešení a příkazy sestavení projektu. V obou případech jsou projekty sestaveny jednotlivě v pořadí závislosti a z odkazů typu projekt na projekt nejsou provázány. Naopak pokud jednotlivé projekty jsou vybaveny *msbuild.exe*, z odkazů typu projekt na projekt jsou provázány.  
  
 Při vytváření uvnitř [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], vlastnost `$(BuildingInsideVisualStudio)` je nastavena na `true`. To lze použít v projektu nebo *.targets* soubory sestavení, aby chovat odlišně.  
  
## <a name="display-properties-and-items"></a>Zobrazení vlastností a položek  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] rozpoznává určité názvy vlastností a hodnot. Například následující vlastnost v projektu způsobí, že **aplikace Windows** se zobrazí v **typ aplikace** pole **Návrháře projektu**.  
  
```xml  
<OutputType>WinExe</OutputType>  
```  
  
 Hodnota vlastnosti můžete upravovat v **Návrháře projektu** a uloženy v souboru projektu. Pokud takové vlastnosti je předána neplatná hodnota pomocí ruční úpravy [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] se zobrazí upozornění při načtení projektu a nahradí neplatnou hodnotu výchozí hodnotou.  
  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] chápe výchozí hodnoty pro některé vlastnosti. Tyto vlastnosti, nebudou trvale uloženy v souboru projektu, pokud mají jiné než výchozí hodnoty.  
  
 Vlastnosti libovolného jména nejsou zobrazeny v [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Chcete-li změnit libovolné vlastnosti v [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], musíte otevřít soubor projektu v editoru XML a upravit je ručně. Další informace najdete v tématu [upravit soubory projektu v sadě Visual Studio](#edit-project-files-in-visual-studio) později v tomto tématu.  
  
 Položky definované v projektu s libovolným typem názvů položek jsou ve výchozím nastavení zobrazeny v **Průzkumníka řešení** pod jejich uzlem projektu. Chcete-li skrýt zobrazenou položku, nastavte `Visible` metadata, aby `false`. Například následující položka bude účastnit v procesu sestavení, ale nezobrazí se v **Průzkumníka řešení**.  
  
```xml  
<ItemGroup>  
    <IntermediateFile Include="cache.temp">  
        <Visible>false</Visible>  
    </IntermediateFile>  
</ItemGroup>  
```  
  
 Ve výchozím nastavení se nezobrazují položky deklarované v souborech importovaných do projektu. Položky vytvořené během procesu sestavení nejsou nikdy zobrazeny v **Průzkumníka řešení**.  
  
## <a name="conditions-on-items-and-properties"></a>Podmínky pro položky a vlastnosti  
 Během sestavení jsou všechny podmínky úplně dodrženy.  
  
 Při určování hodnot pro zobrazení, vlastnosti, která [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] považuje za závislé na konfiguraci, jsou vyhodnocovány jinak než vlastnosti považuje konfiguraci za nezávislé. Pro vlastnosti považuje konfiguraci za závislou, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] nastaví `Configuration` a `Platform` vlastnosti správně a předá instrukci [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] pro přehodnocení projektu. Pro vlastnosti považuje konfiguraci za nezávislou, že je neurčité, jak se vyhodnotí podmínky.  
  
 Podmíněné výrazy položek jsou vždy ignorovány pro účely rozhodování o tom, zda má být položka zobrazena v **Průzkumníka řešení**.  
  
## <a name="debugging"></a>Ladění  
 Pokud chcete najít a spustit sestavení výstupu a připojit ladicí program, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] potřebuje vlastnosti `OutputPath`, `AssemblyName`, a `OutputType` správně definované. Ladicí program se nepodaří připojit, pokud proces vytváření nezpůsobil, kompilátor vygeneruje *PDB* souboru.  
  
## <a name="design-time-target-execution"></a>Provádění cílů v době návrhu  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] pokusy o spuštění cílů s některými názvy při načítání projektu. Tyto cíle zahrnují `Compile`, `ResolveAssemblyReferences`, `ResolveCOMReferences`, `GetFrameworkPaths`, a `CopyRunEnvironmentFiles`. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Spustí tyto cíle, tak, aby kompilátor může být inicializován k zajištění technologie IntelliSense, ladicí program může být inicializována a zobrazení odkazů v Průzkumníku řešení může být vyřešený. Pokud tyto cíle nejsou přítomny, projekt se načtou a sestaví správně ale možnosti času návrhu v [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] nebudou plně funkční.  
  
##  <a name="edit-project-files-in-visual-studio"></a>Upravit soubory projektu v sadě Visual Studio  
 Chcete-li upravit [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] projektu přímo, můžete otevřít soubor projektu v editoru XML pro Visual Studio.  
  
#### <a name="to-unload-and-edit-a-project-file-in-visual-studio"></a>Uvolnění projektu a jeho úprava v sadě Visual Studio  
  
1.  V **Průzkumníka řešení**, otevřete místní nabídku pro projekt a klikněte na tlačítko **uvolnit projekt**.  
  
     Projekt je označen **(není k dispozici)**.  
  
2.  V **Průzkumníka řešení**, otevřete místní nabídku pro nedostupný projekt a klikněte na tlačítko **upravit \<soubor projektu >**.  
  
     Soubor projektu se otevře v editoru XML sady Visual Studio.  
  
3.  Upravte, uložte a zavřete soubor projektu.  
  
4.  V **Průzkumníka řešení**, otevřete místní nabídku pro nedostupný projekt a klikněte na tlačítko **znovu načíst projekt**.  
  
## <a name="intellisense-and-validation"></a>Technologie IntelliSense a ověřování  
 Při použití editoru XML k úpravám souborů projektu, technologie IntelliSense a ověřování řízeno souborem [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] soubory schémat. Tyto jsou nainstalovány v mezipaměti schématu, který se nachází v  *\<instalačního adresáře sady Visual Studio > \Xml\Schemas\1033\MSBuild*.  
  
 Základní [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] typy jsou definovány v *Microsoft.Build.Core.xsd* a běžné typy používané [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] jsou definovány v *Microsoft.Build.CommonTypes.xsd*. Chcete-li přizpůsobit, abyste měli IntelliSense a ověřování pro vlastní názvy typů položek, vlastnosti a úkoly, můžete buď úpravy *Microsoft.Build.xsd*, nebo vytvořit vlastní schéma, která zahrnuje CommonTypes nebo Core schémata. Pokud vytvoříte vlastní schéma, budete muset instruovat XML editor pro hledání pomocí **vlastnosti** okna.  
  
## <a name="edit-loaded-project-files"></a>Úpravy načtených souborů projektu  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ukládá do mezipaměti obsah projektových souborů a souborů importovaných projektovými soubory. Pokud upravíte načtený soubor projektu, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] vás automaticky vyzve k opětovnému načtení projektu tak, aby se změny projevily. Ale pokud upravíte soubor importovaný načteným projektem, nebudou bez výzvy znovu načíst a musíte odebrat a znovu načtěte projekt ručně, aby se změny projevily.  
  
## <a name="output-groups"></a>Skupiny výstupu  
 Některé cíle definované v *cílů Microsoft.Common.targets* mají jména končící na `OutputGroups` nebo `OutputGroupDependencies`. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] volá tyto cíle pro získání určitých seznamů výstupů projektu. Například `SatelliteDllsProjectOutputGroup` cílové vytvoří seznam všech satelitních sestavení vytvoří sestavení. Tyto skupiny výstupu jsou používány funkce, jako je publikování, nasazení a meziprojektové odkazy. Projekty, které je nedefinují, se načtou a sestaví [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], ale některé funkce nemusí fungovat správně.  
  
## <a name="reference-resolution"></a>Překlad odkazů  
 Referenční řešení je proces vyhledání skutečných sestavení pomocí referenčních položek uložených v souboru projektu. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] musí spustit řešení odkazu pro zobrazení detailních vlastnosti pro každý odkaz v **vlastnosti** okna. Následující seznam popisuje tři typy odkazů a jejich výsledek.  
  
- Odkazy na sestavení:  
  
   Projektový systém volá cíl s dobře známým názvem `ResolveAssemblyReferences`. Tento cíl by měl vytvářet položky s názvem položky typu `ReferencePath`. Každá z těchto položek by měla mít specifikaci položky (hodnota `Include` atribut položky) obsahující úplnou cestu k odkazu. Položky by měly mít všechna metadata ze vstupních položek prošla kromě následujících nových metadat:  
  
  - `CopyLocal`, která udává, zda sestavení má být zkopírováno do výstupní složky, nastavte na hodnotu true nebo false.  
  
  - `OriginalItemSpec`, obsahující specifikace původní položky odkazu.  
  
  - `ResolvedFrom`, pokud bylo vyřešeno z nastavte na "{TargetFrameworkDirectory}" [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] adresáře.  
  
- Odkazy modelu COM:  
  
   Projektový systém volá cíl s dobře známým názvem `ResolveCOMReferences`. Tento cíl by měl vytvářet položky s názvem položky typu `ComReferenceWrappers`. Každá z těchto položek by měla mít specifikaci obsahující úplnou cestu ke zprostředkovatelům sestavení pro odkaz COM. Položky by měly mít všechna metadata ze vstupních položek předaných, kromě nových metadat s názvem `CopyLocal`, která udává, zda sestavení má být zkopírováno do výstupní složky, nastavte na hodnotu true nebo false.  
  
- Nativní odkazy  
  
   Projektový systém volá cíl s dobře známým názvem `ResolveNativeReferences`. Tento cíl by měl vytvářet položky s názvem položky typu `NativeReferenceFile`. Položky by měly mít všechna metadata ze vstupních položek prošla kromě nových metadat s názvem `OriginalItemSpec`, obsahující specifikace původní položky odkazu.  
  
## <a name="performance-shortcuts"></a>Klávesové zkratky výkonu  
 Pokud spustíte ladění v rozhraní Visual Studia (buď volbou klávesy F5 nebo výběrem **ladění** > **spustit ladění** na řádku nabídek), proces sestavení použije rychlou aktualizaci ke zlepšení výkon. V některých případech, kde přizpůsobená sestavení vytvoří soubory, které zase získají sestavení kontrola rychlé aktualizace nesprávně identifikuje změněné soubory. Projekty, které vyžadují důkladnější kontroly aktualizací můžete vypnout rychlé kontroly nastavením proměnné prostředí `DISABLEFASTUPTODATECHECK=1`. Alternativně projekty můžete nastavit to jako vlastnost MSBuild v projektu nebo v souboru, který importuje.  
  
 Pro pravidelná sestavení v sadě Visual Studio se nevztahuje kontrola rychlé aktualizace a projekt bude sestaven jako kdyby jste vyvolali sestavení z příkazového řádku.  
  
## <a name="see-also"></a>Viz také:  
 [Postupy: rozšíření procesu sestavení sady Visual Studio](../msbuild/how-to-extend-the-visual-studio-build-process.md)   
 [Spuštění sestavení z integrovaného vývojového prostředí](../msbuild/starting-a-build-from-within-the-ide.md)   
 [Registrace rozšíření rozhraní .NET Framework](../msbuild/registering-extensions-of-the-dotnet-framework.md)   
 [Koncepty nástroje MSBuild](../msbuild/msbuild-concepts.md)   
 [Item – element (MSBuild)](../msbuild/item-element-msbuild.md)   
 [Property – element (MSBuild)](../msbuild/property-element-msbuild.md)   
 [Target – element (MSBuild)](../msbuild/target-element-msbuild.md)   
 [CSC – úloha](../msbuild/csc-task.md)   
 [Vbc – úloha](../msbuild/vbc-task.md)