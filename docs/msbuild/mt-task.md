---
title: MT Úkol | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VC.Project.VCManifestTool.ResourceOutputFileName
- VC.Project.VCManifestTool.SuppressDependencyElement
- VC.Project.VCManifestTool.ManifestFromManagedAssembly
- VC.Project.VCManifestTool.GenerateCategoryTags
- VC.Project.VCManifestTool.EnableDPIAwareness
- vc.task.mt
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- MSBUILD (C++), MT task
- MT task (MSBuild (C++))
ms.assetid: bb94913c-1042-4968-9f08-b394518e899f
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5fe0ce106fc471431d3aac088eb3f45cfb28c564
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633054"
---
# <a name="mt-task"></a>MT – úloha

Zabalí nástroj Microsoft Manifest *Tool, mt.exe*. Další informace naleznete v tématu [Mt.exe](/windows/desktop/SbsCs/mt-exe).

## <a name="parameters"></a>Parametry

 Následující tabulka popisuje parametry úlohy **MT.** Většina parametrů úlohy a několik sad parametrů odpovídají možnosti příkazového řádku.

> [!NOTE]
> Dokumentace *mt.exe* používá pomlčku**-**( ) jako předponu pro možnosti příkazového**/** řádku, ale toto téma používá lomítko ( ). Buď je přijatelná předpona.

|Parametr|Popis|
|---------------|-----------------|
|**AdditionalManifestFiles**|Volitelný **parametr String[].**<br /><br /> Určuje název jednoho nebo více souborů manifestu.<br /><br /> Další informace naleznete v tématu **/manifest** možnost [Mt.exe](/windows/desktop/SbsCs/mt-exe).|
|**Další možnosti**|Volitelný **parametr String.**<br /><br /> Seznam možností příkazového řádku. Například /\<option1\<> /\<option2> / option#>. Tento parametr slouží k určení možností příkazového řádku, které nejsou reprezentovány žádným jiným parametrem úlohy **MT.**<br /><br /> Další informace naleznete v tématu [Mt.exe](/windows/desktop/SbsCs/mt-exe).|
|**Assemblyidentity**|Volitelný **parametr String.**<br /><br /> Určuje hodnoty atributů elementu **assemblyIdentity** manifestu. Zadejte seznam oddělený čárkami, kde první komponentou je `name` hodnota atributu, následovaný jedním nebo více dvojicemi název/hodnota, které mají formulář, * \<název atributu>=<attribute_value>*.<br /><br /> Další informace naleznete v tématu **/identity** option in [Mt.exe](/windows/desktop/SbsCs/mt-exe).|
|**Název_komponenty**|Volitelný **parametr String.**<br /><br /> Určuje název dynamické knihovny, kterou chcete vytvořit ze souborů *RGS* nebo *TLB.* Tento parametr je povinný, pokud zadáte parametry úlohy **RegistrarScriptFile** nebo **TypeLibraryFile** MT.<br /><br /> Další informace naleznete v tématu **/dll** možnost [mt.exe](/windows/desktop/SbsCs/mt-exe).|
|**Soubor DependencyInformationFile**|Volitelný **parametr String.**<br /><br /> Určuje soubor informací o závislostech používaný sadou Visual Studio ke sledování informací o závislostech sestavení pro nástroj manifestu.|
|**Vložitmanifest**|Volitelný `Boolean` parametr.<br /><br /> Pokud `true`vloží soubor manifestu do sestavení. Pokud `false`se vytvoří jako samostatný soubor manifestu.|
|**EnableDPIAwareness**|Volitelný `Boolean` parametr.<br /><br /> Pokud `true`, přidá k manifestu informace, které označí aplikaci jako DPI vědomi. Psaní aplikace podporující DPI dělá uživatelské rozhraní vypadat konzistentně dobře v celé řadě nastavení zobrazení s vysokým DPI.<br /><br /> Další informace naleznete [v tématu High DPI](/windows/desktop/win7devguide/high-dpi).|
|**GenerateCatalogFiles**|Volitelný `Boolean` parametr.<br /><br /> Pokud `true`vygeneruje soubor definice katalogu (*CDF*).<br /><br /> Další informace naleznete v tématu **/makecdfs** option in [Mt.exe](/windows/desktop/SbsCs/mt-exe).|
|**Generovatznačky kategorií**|Volitelný `Boolean` parametr.<br /><br /> Pokud `true`způsobí , že značky kategorií budou generovány. Pokud je `true`tento parametr , musí být zadán také parametr úlohy **ManifestFromManagedAssemblyMT.**<br /><br /> Další informace naleznete v tématu **/category** option in [Mt.exe](/windows/desktop/SbsCs/mt-exe).|
|**InputResourceManifests**|Volitelný **parametr String.**<br /><br /> Zadejte manifest ze zdroje typu RT_MANIFEST, který má zadaný identifikátor. Zadejte zdroj formuláře, \<soubor>[;[ #]\<resource_id>], \<kde je volitelný parametr resource_id> nezáporné, 16bitové číslo.<br /><br /> Pokud `resource_id` není zadána žádná, CREATEPROCESS_MANIFEST_RESOURCE výchozí hodnota (1).<br /><br /> Další informace naleznete v tématu **/inputresource** option in [Mt.exe](/windows/desktop/SbsCs/mt-exe).|
|**ManifestFromManagedAssembly**|Volitelný **parametr String.**<br /><br /> Generuje manifest ze zadaného spravovaného sestavení.<br /><br /> Další informace naleznete v tématu **/managedassemblyname** option in [Mt.exe](/windows/desktop/SbsCs/mt-exe).|
|**ManifestToignore**|Volitelný **parametr String.**<br /><br /> (Nepoužívá se.)|
|**OutputManifestFile**|Volitelný **parametr String.**<br /><br /> Určuje název výstupního manifestu. Pokud je tento parametr vynechán a je provozován pouze jeden manifest, je tento manifest změněn na místě.<br /><br /> Další informace naleznete v tématu **/out** možnost [Mt.exe](/windows/desktop/SbsCs/mt-exe).|
|**OutputResourceManifests**|Volitelný **parametr String.**<br /><br /> Výstup manifestu do prostředku typu RT_MANIFEST, který má zadaný identifikátor. Prostředek je formuláře, \<soubor>[;[ #]\<resource_id>], \<kde je volitelný parametr resource_id> nezáporné, 16bitové číslo.<br /><br /> Pokud `resource_id` není zadána žádná, CREATEPROCESS_MANIFEST_RESOURCE výchozí hodnota (1).<br /><br /> Další informace naleznete v tématu **/outputresource** option in [Mt.exe](/windows/desktop/SbsCs/mt-exe).|
|**Soubor RegistrarScriptFile**|Volitelný **parametr String.**<br /><br /> Určuje název souboru skriptu registrátora (*.rgs),* který má být používán pro podporu manifestu com bez registrace.<br /><br /> Další informace naleznete v tématu **/rgs** možnost [Mt.exe](/windows/desktop/SbsCs/mt-exe).|
|**Soubor náhrad**|Volitelný **parametr String.**<br /><br /> Určuje soubor, který obsahuje hodnoty nahraditelných řetězců v souboru skriptu registrátora (*RGS*).<br /><br /> Další informace naleznete v tématu **/replacements** option in [Mt.exe](/windows/desktop/SbsCs/mt-exe).|
|**ResourceOutputFileName**|Volitelný **parametr String.**<br /><br /> Určuje soubor výstupních prostředků použitý k vložení manifestu do výstupu projektu.|
|**Zdrojů**|Volitelný `ITaskItem[]` parametr.<br /><br /> Určuje seznam zdrojových souborů manifestu oddělených mezerami.<br /><br /> Další informace naleznete v tématu **/manifest** možnost [Mt.exe](/windows/desktop/SbsCs/mt-exe).|
|**Potlačení prvku**|Volitelný `Boolean` parametr.<br /><br /> Pokud `true`, generuje manifest bez prvků závislostí. Pokud je `true`tento parametr , zadejte také parametr **úlohy ManifestFromManagedAssemblyMT.**<br /><br /> Další informace naleznete v tématu **/nodependency** možnost [Mt.exe](/windows/desktop/SbsCs/mt-exe).|
|**PotlačitStartupBanner**|Volitelný `Boolean` parametr.<br /><br /> Pokud `true`aplikace zabraňuje zobrazení zprávy o autorských právech a čísle verze při spuštění úlohy.<br /><br /> Další informace naleznete v tématu **/nologo** option in [Mt.exe](/windows/desktop/SbsCs/mt-exe).|
|**TrackerLogDirectory**|Volitelný `String` parametr.<br /><br /> Určuje zprostředkující adresář, ve kterém jsou uloženy protokoly sledování pro tuto úlohu.|
|**Soubor TypeLibraryFile**|Volitelný **parametr String.**<br /><br /> Určuje název souboru knihovny typů (*TLB).* Pokud zadáte tento parametr, zadejte také parametr **úlohy ComponentFileNameMT.**<br /><br /> Další informace naleznete v tématu **/tlb** option in [Mt.exe](/windows/desktop/SbsCs/mt-exe).|
|**UpdateFileHashes**|Volitelný `Boolean` parametr.<br /><br /> Pokud `true`vypočítá hodnotu hash souborů na cestě určené parametrem **úlohy UpdateFileHashesSearchPathMT** a potom aktualizuje hodnotu atributu **hash** elementu **souboru** manifestu pomocí vypočítané hodnoty.<br /><br /> Další informace naleznete v tématu **/hashupdate** možnost [mt.exe](/windows/desktop/SbsCs/mt-exe). Viz také parametr **UpdateFileHashesSearchPath** v této tabulce.|
|**AktualizovatSouborHashesSearchPath**|Volitelný `String` parametr.<br /><br /> Určuje cestu hledání, která se má použít při aktualizaci hashe souborů. Tento parametr použijte s parametrem **úlohy UpdateFileHashesMT.**<br /><br /> Další informace naleznete v parametru **UpdateFileHashes** v této tabulce.|
|**VerboseOutput**|Volitelný `Boolean` parametr.<br /><br /> Pokud `true`zobrazí podrobné informace o ladění.<br /><br /> Další informace naleznete v tématu **/verbose** option in [Mt.exe](/windows/desktop/SbsCs/mt-exe).|

## <a name="see-also"></a>Viz také

- [Odkaz na úkol](../msbuild/msbuild-task-reference.md)
