---
title: MT úkol | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
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
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6bc6fe1c581cfcc506eeb985b0b138edfab12112
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2019
ms.locfileid: "74295537"
---
# <a name="mt-task"></a>MT – úloha
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Zabalí Nástroj manifest společnosti Microsoft, MT. exe. Další informace naleznete v části Mt. exe na webu [MSDN](https://go.microsoft.com/fwlink/?LinkId=737) .  
  
## <a name="parameters"></a>Parametry  
 Následující tabulka popisuje parametry úlohy **Mt** . Většina parametrů úlohy a několik sad parametrů odpovídá možnosti příkazového řádku.  
  
> [!NOTE]
> Dokumentace Mt. exe používá jako předponu pro možnosti příkazového řádku spojovník ( **-** ), ale toto téma používá lomítko ( **/** ). Obě předpony jsou přijatelné.  
  
|Parametr|Popis|  
|---------------|-----------------|  
|**AdditionalManifestFiles**|Parametr volitelného **řetězce []** .<br /><br /> Určuje název jednoho nebo více souborů manifestu.<br /><br /> Další informace najdete na webu [MSDN](https://go.microsoft.com/fwlink/?LinkId=737) v možnosti **/manifest** na Mt. exe.|  
|**AdditionalOptions**|Volitelný **řetězcový** parametr.<br /><br /> Seznam možností příkazového řádku Například " */option1/option2/Option #* ". Pomocí tohoto parametru můžete zadat možnosti příkazového řádku, které nejsou reprezentované žádným jiným parametrem úlohy **Mt** .<br /><br /> Další informace naleznete v části Mt. exe na webu [MSDN](https://go.microsoft.com/fwlink/?LinkId=737) .|  
|**AssemblyIdentity**|Volitelný **řetězcový** parametr.<br /><br /> Určuje hodnoty atributu prvku **assemblyIdentity** manifestu. Zadejte seznam oddělený čárkami, kde první komponenta je hodnota atributu `name` následovaný jednou nebo více páry název/hodnota, které mají formulář, *\<název atributu > = < attribute_value >* .<br /><br /> Další informace najdete na webu [MSDN](https://go.microsoft.com/fwlink/?LinkId=737) v možnosti **/identity** na Mt. exe.|  
|**ComponentFileName**|Volitelný **řetězcový** parametr.<br /><br /> Určuje název knihovny DLL, kterou chcete sestavit ze souborů. rgs nebo. tlb. Tento parametr je povinný, pokud zadáte parametry úlohy **RegistrarScriptFile** nebo **souborKnihovnyTypů** Mt.<br /><br /> Další informace najdete na webu [MSDN](https://go.microsoft.com/fwlink/?LinkId=737) v možnosti **/DLL** na Mt. exe.|  
|**DependencyInformationFile**|Volitelný **řetězcový** parametr.<br /><br /> Určuje soubor informací o závislostech používaný aplikací Visual Studio ke sledování informací o závislostech sestavení pro nástroj manifest.|  
|**EmbedManifest**|Volitelný parametr `Boolean`.<br /><br /> Pokud `true`, vloží soubor manifestu do sestavení. Pokud `false`, vytvoří soubor samostatného manifestu.|  
|**EnableDPIAwareness**|Volitelný parametr `Boolean`.<br /><br /> Pokud `true`, přidá k informacím o manifestu, které aplikaci označí jako s podporou DPI. Psaní aplikace podporující DPI usnadňuje vzhled uživatelského rozhraní napříč širokou škálou nastavení displeje s vysokým rozlišením DPI.<br /><br /> Další informace najdete v části "vysoké rozlišení DPI" na webu [MSDN](https://go.microsoft.com/fwlink/?LinkId=737) .|  
|**GenerateCatalogFiles**|Volitelný parametr `Boolean`.<br /><br /> Pokud `true`, vygeneruje soubory definice katalogu (. CDF).<br /><br /> Další informace najdete na webu [MSDN](https://go.microsoft.com/fwlink/?LinkId=737) v možnosti **/makecdfs** na Mt. exe.|  
|**GenerateCategoryTags**|Volitelný parametr `Boolean`.<br /><br /> Pokud `true`, způsobí vygenerování značek kategorií. Pokud je tento parametr `true`, musí být také zadán parametr úlohy **ManifestFromManagedAssemblyMT** .<br /><br /> Další informace najdete na webu [MSDN](https://go.microsoft.com/fwlink/?LinkId=737) v možnosti **/Category** na Mt. exe.|  
|**InputResourceManifests**|Volitelný **řetězcový** parametr.<br /><br /> Zadejte manifest z prostředku typu RT_MANIFEST, který má zadaný identifikátor. Zadejte prostředek formuláře, _\<soubor > [_ **;** _[_ **#** _] < resource_id >]_ , kde volitelný parametr `resource_id` je nezáporné, 16bitové číslo.<br /><br /> Pokud není zadán žádný `resource_id`, je použita výchozí hodnota CREATEPROCESS_MANIFEST_RESOURCE (1).<br /><br /> Další informace najdete na webu [MSDN](https://go.microsoft.com/fwlink/?LinkId=737) v možnosti **/inputresource** na Mt. exe.|  
|**ManifestFromManagedAssembly**|Volitelný **řetězcový** parametr.<br /><br /> Vygeneruje manifest ze zadaného spravovaného sestavení.<br /><br /> Další informace najdete na webu [MSDN](https://go.microsoft.com/fwlink/?LinkId=737) v možnosti **/managedassemblyname** na Mt. exe.|  
|**ManifestToIgnore**|Volitelný **řetězcový** parametr.<br /><br /> (Nepoužívá se.)|  
|**OutputManifestFile**|Volitelný **řetězcový** parametr.<br /><br /> Určuje název výstupního manifestu. Pokud je tento parametr vynechán a je-li provozován pouze jeden manifest, je tento manifest změněn na místě.<br /><br /> Další informace naleznete na webu [MSDN](https://go.microsoft.com/fwlink/?LinkId=737) v možnosti **/out** na Mt. exe.|  
|**OutputResourceManifests**|Volitelný **řetězcový** parametr.<br /><br /> Výstup manifestu do prostředku typu RT_MANIFEST, který má zadaný identifikátor. Prostředek má formát _\<soubor > [_ **;** _[_ **#** _] < resource_id >]_ , kde volitelný parametr `resource_id` je nezáporné, 16bitové číslo.<br /><br /> Pokud není zadán žádný `resource_id`, je použita výchozí hodnota CREATEPROCESS_MANIFEST_RESOURCE (1).<br /><br /> Další informace najdete na webu [MSDN](https://go.microsoft.com/fwlink/?LinkId=737) v možnosti **/outputresource** na Mt. exe.|  
|**RegistrarScriptFile**|Volitelný **řetězcový** parametr.<br /><br /> Určuje název souboru skriptu registrátora (. rgs), který se má použít pro podporu manifestu COM bez registrace.<br /><br /> Další informace najdete na webu [MSDN](https://go.microsoft.com/fwlink/?LinkId=737) v možnosti **/RGS** na Mt. exe.|  
|**ReplacementsFile**|Volitelný **řetězcový** parametr.<br /><br /> Určuje soubor, který obsahuje hodnoty pro nahraditelné řetězce v souboru skriptu registrátora (. rgs).<br /><br /> Další informace najdete na webu [MSDN](https://go.microsoft.com/fwlink/?LinkId=737) v možnosti **/replacements** na Mt. exe.|  
|**ResourceOutputFileName**|Volitelný **řetězcový** parametr.<br /><br /> Určuje výstupní soubor prostředků, který se používá k vložení manifestu do výstupu projektu.|  
|**Prostředky**|Volitelný parametr `ITaskItem[]`.<br /><br /> Určuje seznam zdrojových souborů manifestu oddělených mezerami.<br /><br /> Další informace najdete na webu [MSDN](https://go.microsoft.com/fwlink/?LinkId=737) v možnosti **/manifest** na Mt. exe.|  
|**SuppressDependencyElement**|Volitelný parametr `Boolean`.<br /><br /> Pokud `true`, vygeneruje manifest bez prvků závislosti. Pokud je tento parametr `true`, zadejte také parametr úlohy **ManifestFromManagedAssemblyMT** .<br /><br /> Další informace najdete na webu [MSDN](https://go.microsoft.com/fwlink/?LinkId=737) v možnosti **/nodependency** na Mt. exe.|  
|**SuppressStartupBanner**|Volitelný parametr `Boolean`.<br /><br /> Pokud `true`, zabrání zobrazení zprávy o autorských právech a číslech verze při spuštění úlohy.<br /><br /> Další informace naleznete na webu [MSDN](https://go.microsoft.com/fwlink/?LinkId=737) v možnosti **/nologo** na Mt. exe.|  
|**TrackerLogDirectory**|Volitelný parametr `String`.<br /><br /> Určuje zprostředkující adresář, ve kterém jsou uložené protokoly sledování pro tento úkol.|  
|**TypeLibraryFile**|Volitelný **řetězcový** parametr.<br /><br /> Určuje název souboru knihovny typů (. tlb). Pokud zadáte tento parametr, zadejte také parametr úlohy **ComponentFileNameMT** .<br /><br /> Další informace najdete na webu [MSDN](https://go.microsoft.com/fwlink/?LinkId=737) v možnosti **/TLB** na Mt. exe.|  
|**UpdateFileHashes**|Volitelný parametr `Boolean`.<br /><br /> Pokud `true`, vypočítá hodnotu hash souborů v cestě určené parametrem úlohy **UpdateFileHashesSearchPathMT** a poté aktualizuje hodnotu atributu **hash** prvku **souboru** manifestu pomocí vypočítané hodnoty.<br /><br /> Další informace najdete na webu [MSDN](https://go.microsoft.com/fwlink/?LinkId=737) v možnosti **/hashupdate** na Mt. exe. V této tabulce se také zobrazí parametr **UpdateFileHashesSearchPath** .|  
|**UpdateFileHashesSearchPath**|Volitelný parametr `String`.<br /><br /> Určuje cestu hledání, která se použije při aktualizaci hodnot hash souborů. Tento parametr použijte s parametrem úlohy **UpdateFileHashesMT** .<br /><br /> Další informace najdete v parametru **UpdateFileHashes** v této tabulce.|  
|**VerboseOutput**|Volitelný parametr `Boolean`.<br /><br /> Pokud `true`, zobrazí podrobné informace o ladění.<br /><br /> Další informace najdete na webu [MSDN](https://go.microsoft.com/fwlink/?LinkId=737) v možnosti **/verbose** (Mt. exe).|  
  
## <a name="remarks"></a>Poznámky  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace úlohy](../msbuild/msbuild-task-reference.md)
