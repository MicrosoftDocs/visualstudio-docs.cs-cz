---
title: MT – úloha | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
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
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c9b14de0b9e80379736dd7f6a02cb374d475fcda
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49214925"
---
# <a name="mt-task"></a>MT – úloha
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Zabalí nástroj Microsoft Manifest mt.exe. Další informace najdete v tématu "Mt.exe" na [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) webu.  
  
## <a name="parameters"></a>Parametry  
 Následující tabulka popisuje parametry **MT** úloh. Většinu úkolů parametrů a několik sad parametrů, odpovídají možnost příkazového řádku.  
  
> [!NOTE]
>  Dokumentace mt.exe používá pomlčkou (**-**) jako předponu pro možnosti příkazového řádku, ale toto téma používá lomítko (**/**). Buď předpona je přijatelné.  
  
|Parametr|Popis|  
|---------------|-----------------|  
|**AdditionalManifestFiles**|Volitelné **String []** parametru.<br /><br /> Určuje název jednoho nebo více souborů manifestu.<br /><br /> Další informace najdete v tématu **/manifest** možnost "Mt.exe" na [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) webu.|  
|**AdditionalOptions**|Volitelné **řetězec** parametru.<br /><br /> Seznam možností příkazového řádku. Například "*/option1 /option2 /option#*". Tento parametr použijte k určení možnosti příkazového řádku, které nejsou reprezentovány jakýkoli jiný **MT** parametr úlohy.<br /><br /> Další informace najdete v tématu "Mt.exe" na [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) webu.|  
|**Vlastnost assemblyIdentity**|Volitelné **řetězec** parametru.<br /><br /> Určuje atribut hodnoty **assemblyIdentity** elementu v manifestu. Zadejte čárkami oddělený seznam, kde je hodnota první součásti `name` atribut, za nímž následuje jedna nebo více dvojice název/hodnota, které mít formát _služba ._protokol,  *\<atribut name > = < attribute_value >*.<br /><br /> Další informace najdete v tématu **/identity** možnost "Mt.exe" na [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) webu.|  
|**ComponentFileName**|Volitelné **řetězec** parametru.<br /><br /> Určuje název knihovny DLL, které máte v úmyslu vytvořit ze souborů .rgs nebo .tlb. Tento parametr je povinný, pokud zadáte **RegistrarScriptFile** nebo **Souborknihovnytypů** MT parametry úlohy.<br /><br /> Další informace najdete v tématu **/dll** možnost "Mt.exe" na [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) webu.|  
|**DependencyInformationFile**|Volitelné **řetězec** parametru.<br /><br /> Určuje soubor informací o závislostech používaný aplikací Visual Studio ke sledování informací o závislostech sestavení pro nástroj manifest.|  
|**EmbedManifest**|Volitelné `Boolean` parametru.<br /><br /> Pokud `true`, vloží soubor manifestu sestavení. Pokud `false`, vytvoří jako samostatný soubor manifestu.|  
|**EnableDPIAwareness**|Volitelné `Boolean` parametru.<br /><br /> Pokud `true`, přidá do informace o manifestu, který aplikaci označí jako rozlišením DPI. Zápis rozlišením DPI aplikace díky uživatelské rozhraní vypadat konzistentně dobrá napříč celou řadu nastavení zobrazení vysokých hodnot DPI.<br /><br /> Další informace najdete v tématu "Vysoké rozlišení DPI" na [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) webu.|  
|**GenerateCatalogFiles**|Volitelné `Boolean` parametru.<br /><br /> Pokud `true`, vygeneruje katalog souborů definic (CDF).<br /><br /> Další informace najdete v tématu **/makecdfs** možnost "Mt.exe" na [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) webu.|  
|**GenerateCategoryTags**|Volitelné `Boolean` parametru.<br /><br /> Pokud `true`, způsobí, že se budou generovat značky kategorií. Pokud je tento parametr `true`, **ManifestFromManagedAssemblyMT** musí být zadán také parametr úkolu.<br /><br /> Další informace najdete v tématu **/category** možnost "Mt.exe" na [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) webu.|  
|**InputResourceManifests**|Volitelné **řetězec** parametru.<br /><br /> Vstup manifestu z prostředku typu RT_MANIFEST, který má zadaný identifikátor. Zadejte prostředek ve formátu,  _\<soubor > [_**;** _[_**#**_] < ID_prostředku >]_, kde nepovinný `resource_id` parametr je nastaven na nezáporné 16bitové číslo.<br /><br /> Pokud ne `resource_id` je zadán, použije se výchozí hodnota CREATEPROCESS_MANIFEST_RESOURCE (1).<br /><br /> Další informace najdete v tématu **/inputresource** možnost "Mt.exe" na [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) webu.|  
|**ManifestFromManagedAssembly**|Volitelné **řetězec** parametru.<br /><br /> Generuje manifest ze zadané spravované sestavení.<br /><br /> Další informace najdete v tématu **/managedassemblyname** možnost "Mt.exe" na [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) webu.|  
|**ManifestToIgnore**|Volitelné **řetězec** parametru.<br /><br /> (Nepoužívá.)|  
|**OutputManifestFile**|Volitelné **řetězec** parametru.<br /><br /> Určuje název výstupním manifestu. Pokud je tento parametr vynechán, pracuje jen jeden manifest na tento manifest se upraví na místě.<br /><br /> Další informace najdete v tématu **/out** možnost "Mt.exe" na [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) webu.|  
|**OutputResourceManifests**|Volitelné **řetězec** parametru.<br /><br /> Výstup manifestu do prostředku typu RT_MANIFEST, který má zadaný identifikátor. Prostředek je ve formuláři,  _\<soubor > [_**;** _[_**#**_] < ID_prostředku >]_, kde nepovinný `resource_id` parametr je nastaven na nezáporné 16bitové číslo.<br /><br /> Pokud ne `resource_id` je zadán, použije se výchozí hodnota CREATEPROCESS_MANIFEST_RESOURCE (1).<br /><br /> Další informace najdete v tématu **/outputresource** možnost "Mt.exe" na [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) webu.|  
|**RegistrarScriptFile**|Volitelné **řetězec** parametru.<br /><br /> Určuje název manifestu podpora bez registrace modelu COM pomocí soubor skriptu (.rgs).<br /><br /> Další informace najdete v tématu **/rgs** možnost "Mt.exe" na [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) webu.|  
|**ReplacementsFile**|Volitelné **řetězec** parametru.<br /><br /> Určuje soubor, který obsahuje hodnoty pro nahraditelné řetězce v soubor skriptu (.rgs).<br /><br /> Další informace najdete v tématu **/replacements** možnost "Mt.exe" na [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) webu.|  
|**ResourceOutputFileName**|Volitelné **řetězec** parametru.<br /><br /> Určuje výstupní soubor prostředků pro vložení manifestu do výstupu projektu.|  
|**Zdroje**|Volitelné `ITaskItem[]` parametru.<br /><br /> Určuje seznam souborů manifestu zdroj oddělené mezerami.<br /><br /> Další informace najdete v tématu **/manifest** možnost "Mt.exe" na [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) webu.|  
|**SuppressDependencyElement**|Volitelné `Boolean` parametru.<br /><br /> Pokud `true`, generuje manifest bez elementy dependency. Pokud je tento parametr `true`, také určit **ManifestFromManagedAssemblyMT** parametr úlohy.<br /><br /> Další informace najdete v tématu **/nodependency** možnost "Mt.exe" na [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) webu.|  
|**SuppressStartupBanner**|Volitelné `Boolean` parametru.<br /><br /> Pokud `true`, zabraňuje zobrazování čísel zprávu o autorských právech a verze při spuštění úlohy.<br /><br /> Další informace najdete v tématu **/nologo** možnost "Mt.exe" na [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) webu.|  
|**TrackerLogDirectory**|Volitelné `String` parametru.<br /><br /> Určuje zprostředkující adresář, kde jsou uloženy protokoly sledování pro tuto úlohu.|  
|**TypeLibraryFile**|Volitelné **řetězec** parametru.<br /><br /> Určuje název souboru typu knihovna (.tlb). Pokud zadáte tento parametr, zadat také **ComponentFileNameMT** parametr úlohy.<br /><br /> Další informace najdete v tématu **/TLB** možnost "Mt.exe" na [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) webu.|  
|**UpdateFileHashes**|Volitelné `Boolean` parametru.<br /><br /> Pokud `true`, vypočítá hodnotu hash souboru v cestě určené **UpdateFileHashesSearchPathMT** parametr úlohy a pak aktualizuje hodnotu **hash** atribut **souboru** elementu v manifestu pomocí vypočtená hodnota.<br /><br /> Další informace najdete v tématu **/hashupdate** možnost "Mt.exe" na [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) webu. Viz také **UpdateFileHashesSearchPath** parametr v této tabulce.|  
|**UpdateFileHashesSearchPath**|Volitelné `String` parametru.<br /><br /> Určuje cestu hledání pro použití při aktualizaci hodnoty hash souborů. Použitím tohoto parametru s **UpdateFileHashesMT** parametr úlohy.<br /><br /> Další informace najdete v tématu **UpdateFileHashes** parametr v této tabulce.|  
|**VerboseOutput**|Volitelné `Boolean` parametru.<br /><br /> Pokud `true`, zobrazí podrobné informace o ladění.<br /><br /> Další informace najdete v tématu **/ verbose** možnost "Mt.exe" na [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) webu.|  
  
## <a name="remarks"></a>Poznámky  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace úlohy](../msbuild/msbuild-task-reference.md)



