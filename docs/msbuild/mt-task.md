---
title: MT úkol | Microsoft Docs
description: Přečtěte si o parametrech a možnostech příkazového řádku úlohy MSBuild MT, která zabalí Nástroj manifest společnosti Microsoft mt.exe.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: a023c58e528b2cda74fa42fcce46fd9c39059459
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99905444"
---
# <a name="mt-task"></a>MT – úloha

Zabalí Nástroj manifest společnosti Microsoft, *mt.exe*. Další informace najdete v tématu [Mt.exe](/windows/desktop/SbsCs/mt-exe).

## <a name="parameters"></a>Parametry

 Následující tabulka popisuje parametry úlohy **Mt** . Většina parametrů úlohy a několik sad parametrů odpovídá možnosti příkazového řádku.

> [!NOTE]
> Dokumentace k *mt.exe* používá **-** jako předponu pro možnosti příkazového řádku spojovník (), ale toto téma používá lomítko ( **/** ). Obě předpony jsou přijatelné.

|Parametr|Popis|
|---------------|-----------------|
|**AdditionalManifestFiles**|Parametr volitelného **řetězce []** .<br /><br /> Určuje název jednoho nebo více souborů manifestu.<br /><br /> Další informace naleznete v možnosti **/manifest** v [Mt.exe](/windows/desktop/SbsCs/mt-exe).|
|**AdditionalOptions**|Volitelný **řetězcový** parametr.<br /><br /> Seznam možností příkazového řádku Například/ \<option1>  / \<option2>  / \<option#> . Pomocí tohoto parametru můžete zadat možnosti příkazového řádku, které nejsou reprezentované žádným jiným parametrem úlohy **Mt** .<br /><br /> Další informace najdete v tématu [Mt.exe](/windows/desktop/SbsCs/mt-exe).|
|**AssemblyIdentity**|Volitelný **řetězcový** parametr.<br /><br /> Určuje hodnoty atributu prvku **assemblyIdentity** manifestu. Zadejte seznam oddělený čárkami, kde první komponenta je hodnota `name` atributu následovaný jednou nebo více páry název/hodnota, které mají formu *\<attribute name> =<ATTRIBUTE_VALUE>*.<br /><br /> Další informace naleznete v možnosti **/identity** v [Mt.exe](/windows/desktop/SbsCs/mt-exe).|
|**ComponentFileName**|Volitelný **řetězcový** parametr.<br /><br /> Určuje název knihovny DLL, kterou chcete sestavit ze souborů *. rgs* nebo *. tlb* . Tento parametr je povinný, pokud zadáte parametry úlohy **RegistrarScriptFile** nebo **souborKnihovnyTypů** Mt.<br /><br /> Další informace naleznete v možnosti **/DLL** v [Mt.exe](/windows/desktop/SbsCs/mt-exe).|
|**DependencyInformationFile**|Volitelný **řetězcový** parametr.<br /><br /> Určuje soubor informací o závislostech používaný aplikací Visual Studio ke sledování informací o závislostech sestavení pro nástroj manifest.|
|**EmbedManifest**|Volitelný `Boolean` parametr.<br /><br /> Pokud `true` aplikace vloží soubor manifestu do sestavení. Pokud `false` , vytvoří jako samostatný soubor manifestu.|
|**EnableDPIAwareness**|Volitelný `Boolean` parametr.<br /><br /> Pokud `true` , přidá k informacím o manifestu, které aplikaci označí jako podporující dpi. Psaní aplikace podporující DPI usnadňuje vzhled uživatelského rozhraní napříč širokou škálou nastavení displeje s vysokým rozlišením DPI.<br /><br /> Další informace najdete v tématu [vysoké rozlišení DPI](/windows/desktop/win7devguide/high-dpi).|
|**GenerateCatalogFiles**|Volitelný `Boolean` parametr.<br /><br /> Pokud `true` , vygeneruje soubory definice katalogu (*. CDF*).<br /><br /> Další informace naleznete v možnosti **/makecdfs** v [Mt.exe](/windows/desktop/SbsCs/mt-exe).|
|**GenerateCategoryTags**|Volitelný `Boolean` parametr.<br /><br /> Pokud `true` , způsobí vygenerování značek kategorií. Pokud je tento parametr `true` , musí být zadán také parametr úlohy **ManifestFromManagedAssemblyMT** .<br /><br /> Další informace naleznete v možnosti **/Category** v [Mt.exe](/windows/desktop/SbsCs/mt-exe).|
|**InputResourceManifests**|Volitelný **řetězcový** parametr.<br /><br /> Zadejte manifest z prostředku typu RT_MANIFEST, který má zadaný identifikátor. Zadejte prostředek formuláře, \<file> [; [ #] \<resource_id> ], kde volitelný \<resource_id> parametr je nezáporné, 16bitové číslo.<br /><br /> Pokud `resource_id` není zadán, je použita výchozí hodnota CREATEPROCESS_MANIFEST_RESOURCE (1).<br /><br /> Další informace naleznete v možnosti **/inputresource** v [Mt.exe](/windows/desktop/SbsCs/mt-exe).|
|**ManifestFromManagedAssembly**|Volitelný **řetězcový** parametr.<br /><br /> Vygeneruje manifest ze zadaného spravovaného sestavení.<br /><br /> Další informace naleznete v možnosti **/managedassemblyname** v [Mt.exe](/windows/desktop/SbsCs/mt-exe).|
|**ManifestToIgnore**|Volitelný **řetězcový** parametr.<br /><br /> (Nepoužívá se.)|
|**OutputManifestFile**|Volitelný **řetězcový** parametr.<br /><br /> Určuje název výstupního manifestu. Pokud je tento parametr vynechán a je-li provozován pouze jeden manifest, je tento manifest změněn na místě.<br /><br /> Další informace naleznete v tématu možnost **/out** v [Mt.exe](/windows/desktop/SbsCs/mt-exe).|
|**OutputResourceManifests**|Volitelný **řetězcový** parametr.<br /><br /> Výstup manifestu do prostředku typu RT_MANIFEST, který má zadaný identifikátor. Prostředek má tvar, \<file> [; [ #] \<resource_id> ], kde volitelný \<resource_id> parametr je nezáporné, 16bitové číslo.<br /><br /> Pokud `resource_id` není zadán, je použita výchozí hodnota CREATEPROCESS_MANIFEST_RESOURCE (1).<br /><br /> Další informace naleznete v možnosti **/outputresource** v [Mt.exe](/windows/desktop/SbsCs/mt-exe).|
|**RegistrarScriptFile**|Volitelný **řetězcový** parametr.<br /><br /> Určuje název souboru skriptu registrátora (*. rgs*), který se má použít pro podporu manifestu com bez registrace.<br /><br /> Další informace naleznete v možnosti **/RGS** v [Mt.exe](/windows/desktop/SbsCs/mt-exe).|
|**ReplacementsFile**|Volitelný **řetězcový** parametr.<br /><br /> Určuje soubor, který obsahuje hodnoty pro nahraditelné řetězce v souboru skriptu registrátora (*. rgs*).<br /><br /> Další informace naleznete v možnosti **/replacements** v [Mt.exe](/windows/desktop/SbsCs/mt-exe).|
|**ResourceOutputFileName**|Volitelný **řetězcový** parametr.<br /><br /> Určuje výstupní soubor prostředků, který se používá k vložení manifestu do výstupu projektu.|
|**zdroje**|Volitelný `ITaskItem[]` parametr.<br /><br /> Určuje seznam zdrojových souborů manifestu oddělených mezerami.<br /><br /> Další informace naleznete v možnosti **/manifest** v [Mt.exe](/windows/desktop/SbsCs/mt-exe).|
|**SuppressDependencyElement**|Volitelný `Boolean` parametr.<br /><br /> Pokud `true` , vygeneruje manifest bez prvků závislosti. Pokud je tento parametr `true` , zadejte také parametr úlohy **ManifestFromManagedAssemblyMT** .<br /><br /> Další informace naleznete v možnosti **/nodependency** v [Mt.exe](/windows/desktop/SbsCs/mt-exe).|
|**SuppressStartupBanner**|Volitelný `Boolean` parametr.<br /><br /> Pokud `true` aplikace zabrání zobrazení zprávy o autorských právech a číslech verze při spuštění úlohy.<br /><br /> Další informace naleznete v tématu možnost **/nologo** v [Mt.exe](/windows/desktop/SbsCs/mt-exe).|
|**TrackerLogDirectory**|Volitelný `String` parametr.<br /><br /> Určuje zprostředkující adresář, ve kterém jsou uložené protokoly sledování pro tento úkol.|
|**SouborKnihovnyTypů**|Volitelný **řetězcový** parametr.<br /><br /> Určuje název souboru knihovny typů (*. tlb*). Pokud zadáte tento parametr, zadejte také parametr úlohy **ComponentFileNameMT** .<br /><br /> Další informace naleznete v možnosti **/TLB** v [Mt.exe](/windows/desktop/SbsCs/mt-exe).|
|**UpdateFileHashes**|Volitelný `Boolean` parametr.<br /><br /> Pokud `true` , vypočítá hodnotu hash souborů v cestě určené parametrem úlohy **UpdateFileHashesSearchPathMT** a poté aktualizuje hodnotu atributu **hash** prvku **souboru** manifestu pomocí vypočítané hodnoty.<br /><br /> Další informace naleznete v možnosti **/hashupdate** v [Mt.exe](/windows/desktop/SbsCs/mt-exe). V této tabulce se také zobrazí parametr **UpdateFileHashesSearchPath** .|
|**UpdateFileHashesSearchPath**|Volitelný `String` parametr.<br /><br /> Určuje cestu hledání, která se použije při aktualizaci hodnot hash souborů. Tento parametr použijte s parametrem úlohy **UpdateFileHashesMT** .<br /><br /> Další informace najdete v parametru **UpdateFileHashes** v této tabulce.|
|**VerboseOutput**|Volitelný `Boolean` parametr.<br /><br /> Pokud `true` se zobrazí podrobné informace o ladění.<br /><br /> Další informace najdete v tématu možnost **/verbose** v [Mt.exe](/windows/desktop/SbsCs/mt-exe).|

## <a name="see-also"></a>Viz také

- [Referenční dokumentace úlohy](../msbuild/msbuild-task-reference.md)
