---
title: MT úkol | Microsoft Docs
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3fad0b3ddf57167c6721371ae5f8e11f5b7a4c13
ms.sourcegitcommit: 257fc60eb01fefafa9185fca28727ded81b8bca9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2019
ms.locfileid: "72911230"
---
# <a name="mt-task"></a>MT – úloha
Zabalí Nástroj manifest společnosti Microsoft, *Mt. exe*. Další informace najdete v části [Mt. exe](/windows/desktop/SbsCs/mt-exe).

## <a name="parameters"></a>Parametry
 Následující tabulka popisuje parametry úlohy **Mt** . Většina parametrů úlohy a několik sad parametrů odpovídá možnosti příkazového řádku.

> [!NOTE]
> Dokumentace *Mt. exe* používá jako předponu pro možnosti příkazového řádku spojovník ( **-** ), ale toto téma používá lomítko ( **/** ). Obě předpony jsou přijatelné.

|Parametr|Popis|
|---------------|-----------------|
|**AdditionalManifestFiles**|Parametr volitelného **řetězce []** .<br /><br /> Určuje název jednoho nebo více souborů manifestu.<br /><br /> Další informace najdete v tématu možnost **/manifest** v [Mt. exe](/windows/desktop/SbsCs/mt-exe).|
|**AdditionalOptions**|Volitelný **řetězcový** parametr.<br /><br /> Seznam možností příkazového řádku Například/\<option1 >/\<option2 >/\<option # >. Pomocí tohoto parametru můžete zadat možnosti příkazového řádku, které nejsou reprezentované žádným jiným parametrem úlohy **Mt** .<br /><br /> Další informace najdete v části [Mt. exe](/windows/desktop/SbsCs/mt-exe).|
|**AssemblyIdentity**|Volitelný **řetězcový** parametr.<br /><br /> Určuje hodnoty atributu prvku **assemblyIdentity** manifestu. Zadejte seznam oddělený čárkami, kde první komponenta je hodnota atributu `name` následovaný jednou nebo více páry název/hodnota, které mají formulář, *\<název atributu > = < attribute_value >* .<br /><br /> Další informace najdete v tématu možnost **/identity** v [Mt. exe](/windows/desktop/SbsCs/mt-exe).|
|**ComponentFileName**|Volitelný **řetězcový** parametr.<br /><br /> Určuje název knihovny DLL, kterou chcete sestavit ze souborů *. rgs* nebo *. tlb* . Tento parametr je povinný, pokud zadáte parametry úlohy **RegistrarScriptFile** nebo **souborKnihovnyTypů** Mt.<br /><br /> Další informace najdete v tématu možnost **/DLL** v [Mt. exe](/windows/desktop/SbsCs/mt-exe).|
|**DependencyInformationFile**|Volitelný **řetězcový** parametr.<br /><br /> Určuje soubor informací o závislostech používaný aplikací Visual Studio ke sledování informací o závislostech sestavení pro nástroj manifest.|
|**EmbedManifest**|Volitelný parametr `Boolean`.<br /><br /> Pokud `true`, vloží soubor manifestu do sestavení. Pokud `false`, vytvoří soubor samostatného manifestu.|
|**EnableDPIAwareness**|Volitelný parametr `Boolean`.<br /><br /> Pokud `true`, přidá k informacím o manifestu, které aplikaci označí jako s podporou DPI. Psaní aplikace podporující DPI usnadňuje vzhled uživatelského rozhraní napříč širokou škálou nastavení displeje s vysokým rozlišením DPI.<br /><br /> Další informace najdete v tématu [vysoké rozlišení DPI](/windows/desktop/win7devguide/high-dpi).|
|**GenerateCatalogFiles**|Volitelný parametr `Boolean`.<br /><br /> Pokud `true`, vygeneruje soubory definice katalogu ( *. CDF*).<br /><br /> Další informace najdete v tématu možnost **/makecdfs** v [Mt. exe](/windows/desktop/SbsCs/mt-exe).|
|**GenerateCategoryTags**|Volitelný parametr `Boolean`.<br /><br /> Pokud `true`, způsobí vygenerování značek kategorií. Pokud je tento parametr `true`, musí být také zadán parametr úlohy **ManifestFromManagedAssemblyMT** .<br /><br /> Další informace najdete v tématu možnost **/Category** v [Mt. exe](/windows/desktop/SbsCs/mt-exe).|
|**InputResourceManifests**|Volitelný **řetězcový** parametr.<br /><br /> Zadejte manifest z prostředku typu RT_MANIFEST, který má zadaný identifikátor. Zadejte prostředek formuláře, \<soubor > [; [ #]\<resource_id >], kde Optional \<resource_id > parametr je nezáporné, 16bitové číslo.<br /><br /> Pokud není zadán žádný `resource_id`, je použita výchozí hodnota CREATEPROCESS_MANIFEST_RESOURCE (1).<br /><br /> Další informace najdete v tématu možnost **/inputresource** v [Mt. exe](/windows/desktop/SbsCs/mt-exe).|
|**ManifestFromManagedAssembly**|Volitelný **řetězcový** parametr.<br /><br /> Vygeneruje manifest ze zadaného spravovaného sestavení.<br /><br /> Další informace najdete v tématu možnost **/managedassemblyname** v [Mt. exe](/windows/desktop/SbsCs/mt-exe).|
|**ManifestToIgnore**|Volitelný **řetězcový** parametr.<br /><br /> (Nepoužívá se.)|
|**OutputManifestFile**|Volitelný **řetězcový** parametr.<br /><br /> Určuje název výstupního manifestu. Pokud je tento parametr vynechán a je-li provozován pouze jeden manifest, je tento manifest změněn na místě.<br /><br /> Další informace najdete v tématu možnost **/out** v [Mt. exe](/windows/desktop/SbsCs/mt-exe).|
|**OutputResourceManifests**|Volitelný **řetězcový** parametr.<br /><br /> Výstup manifestu do prostředku typu RT_MANIFEST, který má zadaný identifikátor. Prostředek má formát \<soubor > [; [ #]\<resource_id >], kde Optional \<resource_id > parametr je nezáporné, 16bitové číslo.<br /><br /> Pokud není zadán žádný `resource_id`, je použita výchozí hodnota CREATEPROCESS_MANIFEST_RESOURCE (1).<br /><br /> Další informace najdete v tématu možnost **/outputresource** v [Mt. exe](/windows/desktop/SbsCs/mt-exe).|
|**RegistrarScriptFile**|Volitelný **řetězcový** parametr.<br /><br /> Určuje název souboru skriptu registrátora ( *. rgs*), který se má použít pro podporu manifestu com bez registrace.<br /><br /> Další informace najdete v tématu možnost **/RGS** v [Mt. exe](/windows/desktop/SbsCs/mt-exe).|
|**ReplacementsFile**|Volitelný **řetězcový** parametr.<br /><br /> Určuje soubor, který obsahuje hodnoty pro nahraditelné řetězce v souboru skriptu registrátora ( *. rgs*).<br /><br /> Další informace najdete v tématu možnost **/replacements** v [Mt. exe](/windows/desktop/SbsCs/mt-exe).|
|**ResourceOutputFileName**|Volitelný **řetězcový** parametr.<br /><br /> Určuje výstupní soubor prostředků, který se používá k vložení manifestu do výstupu projektu.|
|**Prostředky**|Volitelný parametr `ITaskItem[]`.<br /><br /> Určuje seznam zdrojových souborů manifestu oddělených mezerami.<br /><br /> Další informace najdete v tématu možnost **/manifest** v [Mt. exe](/windows/desktop/SbsCs/mt-exe).|
|**SuppressDependencyElement**|Volitelný parametr `Boolean`.<br /><br /> Pokud `true`, vygeneruje manifest bez prvků závislosti. Pokud je tento parametr `true`, zadejte také parametr úlohy **ManifestFromManagedAssemblyMT** .<br /><br /> Další informace najdete v tématu možnost **/nodependency** v [Mt. exe](/windows/desktop/SbsCs/mt-exe).|
|**SuppressStartupBanner**|Volitelný parametr `Boolean`.<br /><br /> Pokud `true`, zabrání zobrazení zprávy o autorských právech a číslech verze při spuštění úlohy.<br /><br /> Další informace naleznete v možnosti **/nologo** v [Mt. exe](/windows/desktop/SbsCs/mt-exe).|
|**TrackerLogDirectory**|Volitelný parametr `String`.<br /><br /> Určuje zprostředkující adresář, ve kterém jsou uložené protokoly sledování pro tento úkol.|
|**SouborKnihovnyTypů**|Volitelný **řetězcový** parametr.<br /><br /> Určuje název souboru knihovny typů ( *. tlb*). Pokud zadáte tento parametr, zadejte také parametr úlohy **ComponentFileNameMT** .<br /><br /> Další informace najdete v tématu možnost **/TLB** v [Mt. exe](/windows/desktop/SbsCs/mt-exe).|
|**UpdateFileHashes**|Volitelný parametr `Boolean`.<br /><br /> Pokud `true`, vypočítá hodnotu hash souborů v cestě určené parametrem úlohy **UpdateFileHashesSearchPathMT** a poté aktualizuje hodnotu atributu **hash** elementu **File** v manifestu pomocí vypočítané hodnoty. .<br /><br /> Další informace najdete v tématu možnost **/hashupdate** v [Mt. exe](/windows/desktop/SbsCs/mt-exe). V této tabulce se také zobrazí parametr **UpdateFileHashesSearchPath** .|
|**UpdateFileHashesSearchPath**|Volitelný parametr `String`.<br /><br /> Určuje cestu hledání, která se použije při aktualizaci hodnot hash souborů. Tento parametr použijte s parametrem úlohy **UpdateFileHashesMT** .<br /><br /> Další informace najdete v parametru **UpdateFileHashes** v této tabulce.|
|**VerboseOutput**|Volitelný parametr `Boolean`.<br /><br /> Pokud `true`, zobrazí podrobné informace o ladění.<br /><br /> Další informace najdete v možnosti **/verbose** v [Mt. exe](/windows/desktop/SbsCs/mt-exe).|

## <a name="see-also"></a>Viz také:
- [Odkaz na úkol](../msbuild/msbuild-task-reference.md)