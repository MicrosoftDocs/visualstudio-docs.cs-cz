---
title: Integrace sady Visual Studio (MSBuild) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
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
caps.latest.revision: 26
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c90019aa24047524005ba70aa4f1aec75f89c71d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "67825426"
---
# <a name="visual-studio-integration-msbuild"></a>Integrace sady Visual Studio (MSBuild)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Hostitelé sady Visual Studio [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] načítají a sestavují spravované projekty. Vzhledem [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] k tomu, že je zodpovědný za projekt, téměř jakýkoli projekt ve [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] formátu může být úspěšně použit v [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , i když byl projekt vytvořen jiným nástrojem a má přizpůsobený proces sestavení.  
  
 Toto téma popisuje konkrétní aspekty [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] hostování, které by měly být zváženy při přizpůsobení projektů a. cílí na soubory, které chcete načíst a sestavit [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . Ty vám pomůžou zajistit, aby [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] funkce jako IntelliSense a ladění fungovaly pro váš vlastní projekt.  
  
 Další informace o projektech jazyka C++ naleznete v tématu [Project Files](/cpp/build/reference/project-files).  
  
## <a name="project-file-name-extensions"></a>Přípony názvů souborů projektu  
 MSBuild.exe rozpozná všechny přípony názvů souborů projektu, které odpovídají vzoru. * proj. Nicméně [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] rozpoznává pouze podmnožinu těchto přípon názvů souborů projektu, které určují systém projektu pro konkrétní jazyk, který načte projekt. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] nemá jazykově neutrální [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] projektový systém.  
  
 Například [!INCLUDE[csprcs](../includes/csprcs-md.md)] systém projektu načte soubory. csproj, ale není [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] schopn načíst soubor. xxproj. Soubor projektu pro zdrojové soubory v libovolném jazyce musí používat stejnou příponu jako [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] [!INCLUDE[csprcs](../includes/csprcs-md.md)] soubory projektu, které mají být načteny [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .  
  
## <a name="well-known-target-names"></a>Známé názvy cílů  
 Kliknutím na příkaz **sestavit** v nástroji [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] se spustí výchozí cíl v projektu. Tento cíl je často také pojmenován `Build` . Výběrem příkazu **znovu sestavit** nebo **vyčistit** se pokusíte spustit cíl se stejným názvem v projektu. Kliknutím na **publikovat** se spustí cíl s názvem `PublishOnly` v projektu.  
  
## <a name="configurations-and-platforms"></a>Konfigurace a platformy  
 Konfigurace jsou reprezentovány v [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] projektech podle vlastností seskupených v `PropertyGroup` prvku, který obsahuje `Condition` atribut. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] vyhledá tyto podmínky, aby bylo možné vytvořit seznam konfigurací projektu a platforem, které se mají zobrazit. Chcete-li úspěšně extrahovat tento seznam, podmínky musí mít formát podobný následujícímu:  
  
```  
Condition=" '$(Configuration)|$(Platform)' == 'Debug|AnyCPU' "  
Condition=" '$(Configuration)' == 'Release' "   
Condition=" '$(Something)|$(Configuration)|$(SomethingElse)' == 'xxx|Debug|yyy' "  
```  
  
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] vyhledá v `PropertyGroup` `ItemGroup` tomto účelu podmínky pro prvky,, `Import` , vlastnosti a položky.  
  
## <a name="additional-build-actions"></a>Další akce sestavení  
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] umožňuje změnit název typu položky souboru v projektu pomocí vlastnosti **Akce sestavení** okna [vlastností souboru](https://msdn.microsoft.com/013c4aed-08d6-4dce-a124-ca807ca08959) . `Compile``EmbeddedResource` `Content` `None` názvy typů položek,, a jsou vždy uvedeny v této nabídce společně s jinými názvy typů položek, které jsou již v projektu. Aby bylo zajištěno, že všechny vlastní názvy typů položek jsou v této nabídce vždy k dispozici, můžete názvy přidat k typu položky s názvem `AvailableItemName` . Například přidáním následujícího do souboru projektu se přidá vlastní typ `JScript` do této nabídky pro všechny projekty, které je importují:  
  
```  
<ItemGroup>  
    <AvailableItemName Include="JScript"/>  
</ItemGroup>  
```  
  
> [!NOTE]
> Některé názvy typů položek jsou speciální, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ale nejsou uvedené v tomto rozevíracím seznamu.  
  
## <a name="in-process-compilers"></a>Vnitroprocesové kompilátory  
 Pokud je to možné, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] pokusí se o použití vnitroprocesové verze [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] kompilátoru pro zvýšení výkonu. (Neplatí pro [!INCLUDE[csprcs](../includes/csprcs-md.md)] .) Aby to fungovalo správně, musí se splnit následující podmínky:  
  
- V cíli projektu musí existovat úkol s názvem `Vbc` pro [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] projekty.  
  
- `UseHostCompilerIfAvailable`Parametr úlohy musí být nastaven na hodnotu true.  
  
## <a name="design-time-intellisense"></a>Technologie IntelliSense v době návrhu  
 Chcete-li získat podporu technologie IntelliSense v [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] před tím, než sestavení vygenerovalo výstupní sestavení, musí být splněny následující podmínky:  
  
- Musí existovat cíl s názvem `Compile` .  
  
- Buď `Compile` cíl nebo jedna z jeho závislostí musí volat úlohu kompilátoru pro projekt, například `Csc` nebo `Vbc` .  
  
- Buď `Compile` cíl nebo jedna z jeho závislostí musí způsobit, že kompilátor obdrží všechny nezbytné parametry pro technologii IntelliSense, zejména všechny odkazy.  
  
- Podmínky, které jsou uvedeny v části "vnitroprocesové kompilátory", musí být splněny.  
  
## <a name="building-solutions"></a>Sestavování řešení  
 V nástroji je [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] řazení souborů řešení a sestavení projektu kontrolováno [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] sám o sobě. Při sestavování řešení s msbuild.exe v příkazovém řádku [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] analyzuje soubor řešení a seřadí sestavení projektu. V obou případech jsou projekty sestaveny jednotlivě v pořadí závislosti a odkazy z projektu na projekt nejsou procházeny. Na rozdíl od toho, když jsou jednotlivé projekty sestaveny s msbuild.exe, jsou odkazy z projektu na projekt procházeny.  
  
 Při sestavování uvnitř je [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] vlastnost `$(BuildingInsideVisualStudio)` nastavena na `true` . To lze použít ve vašem projektu nebo souborech. targets, aby se sestavení mohlo chovat jinak.  
  
## <a name="displaying-properties-and-items"></a>Zobrazení vlastností a položek  
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] rozpoznává určité názvy vlastností a jejich hodnoty. Například následující vlastnost v projektu způsobí, že se **aplikace systému Windows** zobrazí v poli **Typ aplikace** v **Návrháři projektu**.  
  
```  
<OutputType>WinExe</OutputType>  
```  
  
 Hodnotu vlastnosti lze upravit v **Návrháři projektu** a Uložit do souboru projektu. Pokud je tato vlastnost předána neplatnou hodnotou ruční úpravou, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] zobrazí se upozornění, když se projekt načte a nahradí neplatnou hodnotu výchozí hodnotou.  
  
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] pochopí výchozí hodnoty některých vlastností. Tyto vlastnosti nebudou uchovány do souboru projektu, pokud nemají hodnoty, které nejsou výchozími hodnotami.  
  
 Vlastnosti s libovolnými názvy se nezobrazí v [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . Chcete-li upravit libovolné vlastnosti v nástroji [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , je nutné otevřít soubor projektu v editoru XML a upravit je ručně. Další informace naleznete v části [Úpravy souborů projektu v aplikaci Visual Studio](#BKMK_EditingProjects) dále v tomto tématu.  
  
 Položky definované v projektu s libovolnými názvy typů položek jsou ve výchozím nastavení zobrazeny v Průzkumník řešení pod jejich uzlem projektu. Chcete-li skrýt položku ze zobrazení, nastavte `Visible` metadata na `false` . Například následující položka se bude účastnit procesu sestavení, ale nebude se zobrazovat v Průzkumník řešení.  
  
```  
<ItemGroup>  
    <IntermediateFile Include="cache.temp">  
        <Visible>false</Visible>  
    </IntermediateFile>  
</ItemGroup>  
```  
  
 Položky deklarované v souborech importovaných do projektu se ve výchozím nastavení nezobrazují. Položky vytvořené během procesu sestavení nejsou nikdy zobrazeny v Průzkumník řešení.  
  
## <a name="conditions-on-items-and-properties"></a>Podmínky pro položky a vlastnosti  
 Během sestavení jsou všechny podmínky plně dodržovány.  
  
 Při určování hodnot vlastností k zobrazení se vlastnosti, které [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] považují závislé na konfiguraci, vyhodnocují jinak než vlastnosti, které považují za nezávislé na konfiguraci. Pro vlastnosti, které považuje za závislé na konfiguraci, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] nastaví `Configuration` odpovídající vlastnosti a a provede `Platform` pokyn [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] k opětovnému vyhodnocení projektu. U vlastností, které považuje za nezávislé na konfiguraci, je neurčité, jak budou podmínky vyhodnoceny.  
  
 Podmíněné výrazy u položek se vždycky ignorují pro účely rozhodování o tom, jestli se má položka zobrazit v Průzkumník řešení.  
  
## <a name="debugging"></a>Ladění  
 Aby bylo možné najít a spustit výstupní sestavení a připojit ladicí program, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] musí mít vlastnosti `OutputPath` , `AssemblyName` a `OutputType` správně definovány. Ladicí program se nepodaří připojit, pokud proces sestavení nezpůsobil, že kompilátor vygeneroval soubor. pdb.  
  
## <a name="design-time-target-execution"></a>Provádění cílů v době návrhu  
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] při načtení projektu se pokusí provést cíle s určitými názvy. Mezi tyto cíle patří,,, `Compile` `ResolveAssemblyReferences` `ResolveCOMReferences` `GetFrameworkPaths` a `CopyRunEnvironmentFiles` . [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] spustí tyto cíle, aby bylo možné inicializovat kompilátor pro poskytování technologie IntelliSense, ladicí program lze inicializovat a odkazy zobrazené v Průzkumník řešení lze vyřešit. Pokud tyto cíle nejsou k dispozici, projekt se načte a sestaví správně, ale prostředí v době návrhu nebude [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] plně funkční.  
  
## <a name="editing-project-files-in-visual-studio"></a><a name="BKMK_EditingProjects"></a> Úpravy souborů projektu v aplikaci Visual Studio  
 Chcete-li upravit [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] projekt přímo, můžete otevřít soubor projektu v editoru XML sady Visual Studio.  
  
#### <a name="to-unload-and-edit-a-project-file-in-visual-studio"></a>Uvolnění projektu a jeho úprava v sadě Visual Studio  
  
1. V **Průzkumník řešení**otevřete místní nabídku pro projekt a pak zvolte **Uvolnit projekt**.  
  
     Projekt je označený **(není k dispozici)**.  
  
2. V **Průzkumník řešení**otevřete místní nabídku pro nedostupný projekt a pak zvolte **Upravit \<Project File> **.  
  
     Soubor projektu se otevře v editoru XML sady Visual Studio.  
  
3. Upravte, uložte a zavřete soubor projektu.  
  
4. V **Průzkumník řešení**otevřete místní nabídku pro nedostupný projekt a pak zvolte **znovu načíst projekt**.  
  
## <a name="intellisense-and-validation"></a>Technologie IntelliSense a ověřování  
 Při použití editoru XML k úpravám souborů projektu je technologie IntelliSense a ověřování řízena [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] soubory schématu. Ty jsou nainstalované v mezipaměti schématu, které najdete v *\<Visual Studio installation directory>* \Xml\Schemas\1033\MSBuild..  
  
 Základní [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] typy jsou definovány v Microsoft. Build. Core. xsd a běžné typy, které používá, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] jsou definovány v Microsoft. Build. CommonTypes. xsd. Chcete-li přizpůsobit schémata, abyste měli IntelliSense a ověřování pro vlastní názvy typů položek, vlastnosti a úkoly, můžete buď upravit Microsoft. Build. xsd, nebo vytvořit vlastní schéma, které obsahuje schémata CommonTypes nebo Core. Pokud vytvoříte vlastní schéma, budete muset nasměrovat editor XML, abyste ho našli pomocí okna **vlastnosti** .  
  
## <a name="editing-loaded-project-files"></a>Úpravy načtených souborů projektu  
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ukládá do mezipaměti obsah souborů projektu a souborů importovaných soubory projektu. Pokud upravíte načtený soubor projektu, aplikace [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] vás automaticky vyzve k opětovnému načtení projektu, aby se změny projevily. Pokud však upravíte soubor importovaný načteným projektem, nezobrazí se výzva k opakovanému načtení a je nutné znovu načíst a znovu načíst projekt, aby se změny projevily.  
  
## <a name="output-groups"></a>Skupiny výstupu  
 Několik cílů definovaných v Microsoft. Common. targets má názvy končící `OutputGroups` nebo `OutputGroupDependencies` . [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] volá tyto cíle pro získání konkrétních seznamů výstupů projektu. Například `SatelliteDllsProjectOutputGroup` cíl vytvoří seznam všech satelitních sestavení, které vytvoří sestavení. Tyto výstupní skupiny jsou používány funkcemi, jako je publikování, nasazení a projekt, na odkazy na projekt. Projekty, které je nedefinují, se načítají a sestavují v [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , ale některé funkce nemusí fungovat správně.  
  
## <a name="reference-resolution"></a>Překlad odkazů  
 Řešení odkazů je proces použití referenčních položek uložených v souboru projektu k vyhledání aktuálních sestavení. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] aby bylo možné zobrazit podrobné vlastnosti pro každý odkaz v okně **vlastnosti** , je nutné aktivovat řešení odkazů. Následující seznam popisuje tři typy odkazů a jejich řešení.  
  
- Odkazy na sestavení:  
  
  Systém projektu volá cíl se známým názvem `ResolveAssemblyReferences` . Tento cíl by měl vydávat položky s názvem typu položky `ReferencePath` . Každá z těchto položek by měla mít specifikaci položky (hodnota `Include` atributu položky) obsahující úplnou cestu k odkazu. Položky by měly mít všechna metadata ze vstupních položek předaných spolu s následujícími novými metadaty:  

  - `CopyLocal`, označuje, zda má být sestavení zkopírováno do výstupní složky, nastavte na hodnotu true nebo false.  

  - `OriginalItemSpec`obsahuje specifikaci původní položky odkazu.  

  - `ResolvedFrom`, nastavte na "{TargetFrameworkDirectory}", pokud byla vyřešena z [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] adresáře.  
  
- Odkazy modelu COM:  
  
     Systém projektu volá cíl se známým názvem `ResolveCOMReferences` . Tento cíl by měl vydávat položky s názvem typu položky `ComReferenceWrappers` . Každá z těchto položek by měla mít specifikaci položky obsahující úplnou cestu k definičnímu sestavení pro odkaz COM. Položky by měly mít všechna metadata ze vstupních položek předaných do, kromě nových metadat s názvem `CopyLocal` , což označuje, zda má být sestavení zkopírováno do výstupní složky, nastaveno na hodnotu true nebo false.  
  
- Nativní odkazy  
  
     Systém projektu volá cíl se známým názvem `ResolveNativeReferences` . Tento cíl by měl vydávat položky s názvem typu položky `NativeReferenceFile` . Položky by měly mít všechna metadata ze vstupních položek předaných spolu s novou částí metadat s názvem `OriginalItemSpec` , která obsahuje specifikaci původní položky odkazu.  
  
## <a name="performance-shortcuts"></a>Zkrácení postupu pro zvýšení výkonu  
 Pokud spustíte ladění v uživatelském rozhraní sady Visual Studio (buď výběrem klávesy F5, nebo výběrem možnosti **ladit**, **Spustit ladění** na panelu nabídek), proces sestavení používá k vylepšení výkonu funkci rychlé aktualizace. V některých případech, kdy přizpůsobená sestavení vytváří soubory, které jsou sestaveny, nerozpozná funkce Rychlá aktualizace změněné soubory správně. Projekty, které vyžadují důkladnější kontroly aktualizace, mohou vypnout rychlou kontrolu nastavením proměnné prostředí `DISABLEFASTUPTODATECHECK=1` . Projekty lze také nastavit jako vlastnost MSBuild v projektu nebo v souboru, který projekt importuje.  
  
 Pro běžná sestavení v sadě Visual Studio se nepoužívá kontroler rychlé aktualizace a projekt se vytvoří, jako kdyby jste vyvolali sestavení na příkazovém řádku.  
  
## <a name="see-also"></a>Viz také  
 [Postupy: rozšiřování procesu sestavení sady Visual Studio](../msbuild/how-to-extend-the-visual-studio-build-process.md)   
 [Spuštění sestavení z integrovaného vývojového prostředí (IDE)](../msbuild/starting-a-build-from-within-the-ide.md)   
 [Registrace rozšíření .NET Framework](../msbuild/registering-extensions-of-the-dotnet-framework.md)   
 [Koncepty nástroje MSBuild](../msbuild/msbuild-concepts.md)   
 [Item – Element (MSBuild)](../msbuild/item-element-msbuild.md)   
 [Property – element (MSBuild)](../msbuild/property-element-msbuild.md)   
 [Target – element (MSBuild)](../msbuild/target-element-msbuild.md)   
 [CSc – úloha](../msbuild/csc-task.md)   
 [Vbc – úloha](../msbuild/vbc-task.md)
