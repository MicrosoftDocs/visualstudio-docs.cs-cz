---
title: MT – úloha | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
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
- MSBUILD (Visual C++), MT task
- MT task (MSBuild (Visual C++))
ms.assetid: bb94913c-1042-4968-9f08-b394518e899f
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c6e4298fa9482674232dea2cae98bb25ba51be30
ms.sourcegitcommit: d462dd10746624ad139f1db04edd501e7737d51e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/29/2018
ms.locfileid: "50219871"
---
# <a name="mt-task"></a>MT – úloha
Zabalí nástroj Microsoft manifestu *mt.exe*. Další informace najdete v tématu [Mt.exe](https://docs.microsoft.com/windows/desktop/SbsCs/mt-exe).  
  
## <a name="parameters"></a>Parametry  
 Následující tabulka popisuje parametry **MT** úloh. Většinu úkolů parametrů a několik sad parametrů, odpovídají možnost příkazového řádku.  
  
> [!NOTE]
>  *Mt.exe* dokumentace používá pomlčkou (**-**) jako předponu pro možnosti příkazového řádku, ale toto téma používá lomítko (**/**). Buď předpona je přijatelné.  
  
|Parametr|Popis|  
|---------------|-----------------|  
|**AdditionalManifestFiles**|Volitelné **String []** parametru.<br /><br /> Určuje název jednoho nebo více souborů manifestu.<br /><br /> Další informace najdete v tématu **/manifest** možnost [Mt.exe](https://docs.microsoft.com/windows/desktop/SbsCs/mt-exe).|  
|**AdditionalOptions**|Volitelné **řetězec** parametru.<br /><br /> Seznam možností příkazového řádku. Třeba /\<možnost1 > /\<možnost2 > /\<možnost #>. Tento parametr použijte k určení možnosti příkazového řádku, které nejsou reprezentovány jakýkoli jiný **MT** parametr úlohy.<br /><br /> Další informace najdete v tématu [Mt.exe](https://docs.microsoft.com/windows/desktop/SbsCs/mt-exe).|  
|**Vlastnost assemblyIdentity**|Volitelné **řetězec** parametru.<br /><br /> Určuje atribut hodnoty **assemblyIdentity** elementu v manifestu. Zadejte čárkami oddělený seznam, kde je hodnota první součásti `name` atribut, za nímž následuje jedna nebo více dvojice název/hodnota, které mít formát _služba ._protokol,  *\<atribut name > = < attribute_value >*.<br /><br /> Další informace najdete v tématu **/identity** možnost [Mt.exe](https://docs.microsoft.com/windows/desktop/SbsCs/mt-exe).|  
|**ComponentFileName**|Volitelné **řetězec** parametru.<br /><br /> Určuje název knihovny DLL máte v úmyslu vytvořit ze *.rgs* nebo *.tlb* soubory. Tento parametr je povinný, pokud zadáte **RegistrarScriptFile** nebo **Souborknihovnytypů** MT parametry úlohy.<br /><br /> Další informace najdete v tématu **/dll** možnost [Mt.exe](https://docs.microsoft.com/windows/desktop/SbsCs/mt-exe).|  
|**DependencyInformationFile**|Volitelné **řetězec** parametru.<br /><br /> Určuje soubor informací o závislostech používaný aplikací Visual Studio ke sledování informací o závislostech sestavení pro nástroj manifest.|  
|**EmbedManifest**|Volitelné `Boolean` parametru.<br /><br /> Pokud `true`, vloží soubor manifestu sestavení. Pokud `false`, vytvoří jako samostatný soubor manifestu.|  
|**EnableDPIAwareness**|Volitelné `Boolean` parametru.<br /><br /> Pokud `true`, přidá do informace o manifestu, který aplikaci označí jako rozlišením DPI. Zápis rozlišením DPI aplikace díky uživatelské rozhraní vypadat konzistentně dobrá napříč celou řadu nastavení zobrazení vysokých hodnot DPI.<br /><br /> Další informace najdete v tématu [vysokého nastavení DPI](https://docs.microsoft.com/windows/desktop/win7devguide/high-dpi).|  
|**GenerateCatalogFiles**|Volitelné `Boolean` parametru.<br /><br /> Pokud `true`, vygeneruje definici katalogu (*.CDF pro tvorbu*) soubory.<br /><br /> Další informace najdete v tématu **/makecdfs** možnost [Mt.exe](https://docs.microsoft.com/windows/desktop/SbsCs/mt-exe).|  
|**GenerateCategoryTags**|Volitelné `Boolean` parametru.<br /><br /> Pokud `true`, způsobí, že se budou generovat značky kategorií. Pokud je tento parametr `true`, **ManifestFromManagedAssemblyMT** musí být zadán také parametr úkolu.<br /><br /> Další informace najdete v tématu **/category** možnost [Mt.exe](https://docs.microsoft.com/windows/desktop/SbsCs/mt-exe).|  
|**InputResourceManifests**|Volitelné **řetězec** parametru.<br /><br /> Vstup manifestu z prostředku typu RT_MANIFEST, který má zadaný identifikátor. Zadejte prostředek ve formátu, \<soubor > [; [ #]\<ID_prostředku >], kde nepovinný \<ID_prostředku > parametr je nastaven na nezáporné 16bitové číslo.<br /><br /> Pokud ne `resource_id` je zadán, použije se výchozí hodnota CREATEPROCESS_MANIFEST_RESOURCE (1).<br /><br /> Další informace najdete v tématu **/inputresource** možnost [Mt.exe](https://docs.microsoft.com/windows/desktop/SbsCs/mt-exe).|  
|**ManifestFromManagedAssembly**|Volitelné **řetězec** parametru.<br /><br /> Generuje manifest ze zadané spravované sestavení.<br /><br /> Další informace najdete v tématu **/managedassemblyname** možnost [Mt.exe](https://docs.microsoft.com/windows/desktop/SbsCs/mt-exe).|  
|**ManifestToIgnore**|Volitelné **řetězec** parametru.<br /><br /> (Nepoužívá.)|  
|**OutputManifestFile**|Volitelné **řetězec** parametru.<br /><br /> Určuje název výstupním manifestu. Pokud je tento parametr vynechán, pracuje jen jeden manifest na tento manifest se upraví na místě.<br /><br /> Další informace najdete v tématu **/out** možnost [Mt.exe](https://docs.microsoft.com/windows/desktop/SbsCs/mt-exe).|  
|**OutputResourceManifests**|Volitelné **řetězec** parametru.<br /><br /> Výstup manifestu do prostředku typu RT_MANIFEST, který má zadaný identifikátor. Prostředek je ve formuláři, \<soubor > [; [ #]\<ID_prostředku >], kde nepovinný \<ID_prostředku > parametr je nastaven na nezáporné 16bitové číslo.<br /><br /> Pokud ne `resource_id` je zadán, použije se výchozí hodnota CREATEPROCESS_MANIFEST_RESOURCE (1).<br /><br /> Další informace najdete v tématu **/outputresource** možnost [Mt.exe](https://docs.microsoft.com/windows/desktop/SbsCs/mt-exe).|  
|**RegistrarScriptFile**|Volitelné **řetězec** parametru.<br /><br /> Určuje název skriptu registrátoru (*.rgs*) soubor manifestu podpora bez registrace modelu COM pomocí.<br /><br /> Další informace najdete v tématu **/rgs** možnost [Mt.exe](https://docs.microsoft.com/windows/desktop/SbsCs/mt-exe).|  
|**ReplacementsFile**|Volitelné **řetězec** parametru.<br /><br /> Určuje soubor, který obsahuje hodnoty pro nahraditelné řetězce ve skriptu registrátoru (*.rgs*) soubor.<br /><br /> Další informace najdete v tématu **/replacements** možnost [Mt.exe](https://docs.microsoft.com/windows/desktop/SbsCs/mt-exe).|  
|**ResourceOutputFileName**|Volitelné **řetězec** parametru.<br /><br /> Určuje výstupní soubor prostředků pro vložení manifestu do výstupu projektu.|  
|**Zdroje**|Volitelné `ITaskItem[]` parametru.<br /><br /> Určuje seznam souborů manifestu zdroj oddělené mezerami.<br /><br /> Další informace najdete v tématu **/manifest** možnost [Mt.exe](https://docs.microsoft.com/windows/desktop/SbsCs/mt-exe).|  
|**SuppressDependencyElement**|Volitelné `Boolean` parametru.<br /><br /> Pokud `true`, generuje manifest bez elementy dependency. Pokud je tento parametr `true`, také určit **ManifestFromManagedAssemblyMT** parametr úlohy.<br /><br /> Další informace najdete v tématu **/nodependency** možnost [Mt.exe](https://docs.microsoft.com/windows/desktop/SbsCs/mt-exe).|  
|**SuppressStartupBanner**|Volitelné `Boolean` parametru.<br /><br /> Pokud `true`, zabraňuje zobrazování čísel zprávu o autorských právech a verze při spuštění úlohy.<br /><br /> Další informace najdete v tématu **/nologo** možnost [Mt.exe](https://docs.microsoft.com/windows/desktop/SbsCs/mt-exe).|  
|**TrackerLogDirectory**|Volitelné `String` parametru.<br /><br /> Určuje zprostředkující adresář, kde jsou uloženy protokoly sledování pro tuto úlohu.|  
|**TypeLibraryFile**|Volitelné **řetězec** parametru.<br /><br /> Určuje název knihovny typů (*.tlb*) soubor. Pokud zadáte tento parametr, zadat také **ComponentFileNameMT** parametr úlohy.<br /><br /> Další informace najdete v tématu **/TLB** možnost [Mt.exe](https://docs.microsoft.com/windows/desktop/SbsCs/mt-exe).|  
|**UpdateFileHashes**|Volitelné `Boolean` parametru.<br /><br /> Pokud `true`, vypočítá hodnotu hash souboru v cestě určené **UpdateFileHashesSearchPathMT** parametr úlohy a pak aktualizuje hodnotu **hash** atribut **souboru** elementu v manifestu pomocí vypočtená hodnota.<br /><br /> Další informace najdete v tématu **/hashupdate** možnost [Mt.exe](https://docs.microsoft.com/windows/desktop/SbsCs/mt-exe). Viz také **UpdateFileHashesSearchPath** parametr v této tabulce.|  
|**UpdateFileHashesSearchPath**|Volitelné `String` parametru.<br /><br /> Určuje cestu hledání pro použití při aktualizaci hodnoty hash souborů. Použitím tohoto parametru s **UpdateFileHashesMT** parametr úlohy.<br /><br /> Další informace najdete v tématu **UpdateFileHashes** parametr v této tabulce.|  
|**VerboseOutput**|Volitelné `Boolean` parametru.<br /><br /> Pokud `true`, zobrazí podrobné informace o ladění.<br /><br /> Další informace najdete v tématu **/ verbose** možnost [Mt.exe](https://docs.microsoft.com/windows/desktop/SbsCs/mt-exe).|  
  
## <a name="see-also"></a>Viz také:  
 [Referenční dokumentace úlohy](../msbuild/msbuild-task-reference.md)