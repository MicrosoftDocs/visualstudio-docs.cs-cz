---
title: LIB – Úloha | Microsoft Docs
description: Naučte se, jak MSBuild používá úlohu LIB k zabalení nástroje Správce knihovny Microsoft 32, lib.exe, který vytváří a spravuje knihovnu souborů objektů COFF.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VC.Project.VCLibrarianTool.Name
- VC.Project.VCLibrarianTool.TreatLibWarningsAsErrors
- VC.Project.VCLibrarianTool.Verbose
- vc.task.lib
- VC.Project.VCLibrarianTool.ErrorReporting
- VC.Project.VCLibrarianTool.LinkLibraryDependencies
- VC.Project.VCLibrarianTool.LinkTimeCodeGeneration
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- MSBuild (C++), LIB task
- LIB task (MSBuild (C++))
ms.assetid: e062c7f9-cc69-4a83-9361-1bb5355e5fe8
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3bf1029d42ce40d33e6eea1fcbe5e6434ff85a36
ms.sourcegitcommit: f1d47655974a2f08e69704a9a0c46cb007e51589
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/28/2020
ms.locfileid: "92904448"
---
# <a name="lib-task"></a>LIB – úloha

Zabalí nástroj Správce bitových knihoven od společnosti Microsoft 32 *lib.exe* . Správce knihovny vytvoří a spravuje knihovnu souborů objektů COFF (Common Object File Format). Správce knihovny může také vytvářet soubory exportu a importovat knihovny pro odkazování na exportované definice. Další informace naleznete v tématu [lib reference](/cpp/build/reference/lib-reference) a [Running lib](/cpp/build/reference/running-lib).

## <a name="parameters"></a>Parametry

 Následující tabulka popisuje parametry úlohy **lib** . Většina parametrů úlohy odpovídá možnosti příkazového řádku.

|Parametr|Popis|
|---------------|-----------------|
|**AdditionalDependencies**|Parametr volitelného **řetězce []** .<br /><br /> Určuje další položky, které se mají přidat do příkazového řádku.|
|**AdditionalLibraryDirectories**|Parametr volitelného **řetězce []** .<br /><br /> Přepíše cestu ke knihovně prostředí. Zadejte název adresáře.<br /><br /> Další informace najdete v tématu [/LIBPATH (Další Libpath)](/cpp/build/reference/libpath-additional-libpath).|
|**AdditionalOptions**|Volitelný **řetězcový** parametr.<br /><br /> Seznam možností *lib.exe* , jak jsou zadány na příkazovém řádku. Například/ \<option1>  / \<option2>  / \<option#> . Pomocí tohoto parametru lze zadat *lib.exe* možnosti, které nejsou reprezentovány žádným jiným parametrem úlohy **lib** .<br /><br /> Další informace najdete v tématu [spuštění knihovny LIB](/cpp/build/reference/running-lib).|
|**DisplayLibrary**|Volitelný **řetězcový** parametr.<br /><br /> Zobrazí informace o výstupní knihovně. Zadejte název souboru pro přesměrování informací do souboru. Zadejte "CON" nebo nic pro přesměrování informací do konzoly.<br /><br /> Tento parametr odpovídá možnosti **/list** *lib.exe* .|
|**ErrorReporting**|Volitelný **řetězcový** parametr.<br /><br /> Určuje, jak se Microsoftu pošle informace o interní chybě, pokud *lib.exe* v době běhu selžou.<br /><br /> Zadejte jednu z následujících hodnot, z nichž každá odpovídá možnosti příkazového řádku.<br /><br /> -   **NoErrorReport**  -  **/errorreport: none**<br />-   **Vyzvat okamžitě**  -  **/errorreport: prompt**<br />-   **QueueForNextLogin**  -  **/errorreport: Queue**<br />-   **SendErrorReport**  -  **/errorreport: Send**<br /><br /> Další informace naleznete v možnosti příkazového řádku **/errorreport** ve [spuštění lib](/cpp/build/reference/running-lib).|
|**ExportNamedFunctions**|Parametr volitelného **řetězce []** .<br /><br /> Určuje jednu nebo více funkcí k exportu.<br /><br /> Tento parametr odpovídá parametru **/Export:** *lib.exe* .|
|**ForceSymbolReferences**|Volitelný **řetězcový** parametr.<br /><br /> Vynutí, aby *lib.exe* zahrnoval odkaz na zadaný symbol.<br /><br /> Tento parametr odpovídá **/include:** možnost *lib.exe* .|
|**IgnoreAllDefaultLibraries**|Volitelný `Boolean` parametr.<br /><br /> Pokud `true` , odebere všechny výchozí knihovny ze seznamu knihoven, které *lib.exe* vyhledává při řešení externích odkazů.<br /><br /> Tento parametr odpovídá parametru **/NODEFAULTLIB** možnosti, která je menší než parametr *lib.exe* .|
|**IgnoreSpecificDefaultLibraries**|Parametr volitelného **řetězce []** .<br /><br /> Odebere zadané knihovny ze seznamu knihoven, které *lib.exe* vyhledává při řešení externích odkazů.<br /><br /> Tento parametr odpovídá možnosti **/NODEFAULTLIB** *lib.exe* , která přebírá `library` argument.|
|**LinkLibraryDependencies**|Volitelný `Boolean` parametr.<br /><br /> Pokud `true` Určuje, že výstupy knihoven ze závislostí projektu jsou automaticky propojeny v.|
|**LinkTimeCodeGeneration**|Volitelný `Boolean` parametr.<br /><br /> Pokud `true` , Určuje generování kódu při propojování.<br /><br /> Tento parametr odpovídá možnosti **/LCTG** *lib.exe* .|
|**Určovat minimumRequiredVersion**|Volitelný **řetězcový** parametr.<br /><br /> Určuje minimální požadovanou verzi subsystému. Zadejte čárkami oddělený seznam desítkových čísel v rozsahu 0 až 65535.|
|**ModuleDefinitionFile**|Volitelný **řetězcový** parametr.<br /><br /> Určuje název souboru definice modulu ( *. def* ).<br /><br /> Tento parametr odpovídá možnosti **/DEF** *lib.exe* , která přebírá `filename` argument.|
|**Název**|Volitelný **řetězcový** parametr.<br /><br /> Při sestavení knihovny importů Určuje název knihovny DLL, pro kterou se knihovna importů sestavuje.<br /><br /> Tento parametr odpovídá parametru **/name** *lib.exe* , který přebírá `filename` argument.|
|**OutputFile**|Volitelný **řetězcový** parametr.<br /><br /> Přepíše výchozí název a umístění programu, který *lib.exe* vytvoří.<br /><br /> Tento parametr odpovídá parametru **/out** *lib.exe* , který přebírá `filename` argument.|
|**RemoveObjects**|Parametr volitelného **řetězce []** .<br /><br /> Vynechá zadaný objekt z výstupní knihovny. *Lib.exe* vytvoří knihovnu výstupu kombinací všech objektů (ať už v objektových souborech nebo knihovnách) a pak odstraní všechny objekty, které jsou zadané pomocí této možnosti.<br /><br /> Tento parametr odpovídá možnosti **/remove** *lib.exe* , která přebírá `membername` argument.|
|**Prostředky**|Požadovaný parametr `ITaskItem[]`.<br /><br /> Určuje seznam zdrojových souborů oddělených mezerami.|
|**Provozuschopn**|Volitelný **řetězcový** parametr.<br /><br /> Určuje prostředí pro spustitelný soubor. Volba subsystému ovlivní symbol vstupního bodu nebo funkci vstupního bodu.<br /><br /> Zadejte jednu z následujících hodnot, z nichž každá odpovídá možnosti příkazového řádku.<br /><br /> -   **Konzola**  -  nástroje **/SUBSYSTEM: konzola**<br />-   **Systém Windows**  -  **/SUBSYSTEM: Windows**<br />-   **Nativní**  -  **/SUBSYSTEM: nativní**<br />-   **Aplikace EFI**  -  **/SUBSYSTEM: EFI_APPLICATION**<br />-   Ovladač spouštěcí služby **EFI**  -  **/SUBSYSTEM: EFI_BOOT_SERVICE_DRIVER**<br />-   **EFI ROM**  -  **/SUBSYSTEM: EFI_ROM**<br />-   **Modul runtime EFI**  -  **/SUBSYSTEM: EFI_RUNTIME_DRIVER**<br />-   **WindowsCE**  -  **/SUBSYSTEM: WindowsCE**<br />-   **POSIX**  -  **/SUBSYSTEM: POSIX**<br /><br /> Další informace najdete v tématu [/Subsystem (určení subsystému)](/cpp/build/reference/subsystem-specify-subsystem).|
|**SuppressStartupBanner**|Volitelný **logický** parametr.<br /><br /> Pokud `true` aplikace zabrání zobrazení zprávy o autorských právech a číslech verze při spuštění úlohy.<br /><br /> Další informace naleznete v možnosti **/nologo** v [běhu lib](/cpp/build/reference/running-lib).|
|**TargetMachine**|Volitelný **řetězcový** parametr.<br /><br /> Určuje cílovou platformu pro program nebo knihovnu DLL.<br /><br /> Zadejte jednu z následujících hodnot, z nichž každá odpovídá možnosti příkazového řádku.<br /><br /> -   **MachineARM**  -  **/Machine: ARM**<br />-   **MachineEBC**  -  **/Machine: EBC**<br />-   **MachineIA64**  -  **/Machine: ia64**<br />-   **MachineMIPS**  -  **/Machine: MIPS**<br />-   **MachineMIPS16**  -  **/Machine: MIPS16**<br />-   **MachineMIPSFPU**  - **/Machine: MIPSFPU**<br />-   **MachineMIPSFPU16**  -  **/Machine: MIPSFPU16**<br />-   **MachineSH4**  -  **/Machine: sh4**<br />-   **MachineTHUMB**  -  **/Machine: palec**<br />-   **MachineX64**  -  **/Machine: x64**<br />-   **MachineX86**  -  **/Machine: x86**<br /><br /> Další informace najdete v tématu [/Machine (určení cílové platformy)](/cpp/build/reference/machine-specify-target-platform).|
|**TrackerLogDirectory**|Volitelný **řetězcový** parametr.<br /><br /> Určuje adresář protokolu sledování.|
|**TreatLibWarningAsErrors**|Volitelný **logický** parametr.<br /><br /> Pokud `true` Nástroj způsobí, že úloha **lib** negeneruje výstupní soubor, pokud *lib.exe* vygeneruje upozornění. Pokud `false` je vygenerován výstupní soubor.<br /><br /> Další informace naleznete v možnosti **/WX** v tématu [spuštění lib](/cpp/build/reference/running-lib).|
|**UseUnicodeResponseFiles**|Volitelný **logický** parametr.<br /><br /> Pokud `true` aplikace nastaví systém projektu tak, aby při vytváření Librarian vygeneroval soubory odezvy Unicode. Určete `true` , kdy soubory v projektu mají cesty Unicode.|
|**Podrobné**|Volitelný **logický** parametr.<br /><br /> Pokud `true` se zobrazí podrobnosti o průběhu relace; zahrnuje názvy přidaných souborů *. obj* . Informace se odesílají do standardního výstupu a dají se přesměrovat na soubor.<br /><br /> Další informace naleznete v možnosti **/verbose** v tématu [spuštění lib](/cpp/build/reference/running-lib).|

## <a name="see-also"></a>Viz také

- [Referenční dokumentace úlohy](../msbuild/msbuild-task-reference.md)