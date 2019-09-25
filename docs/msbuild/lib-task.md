---
title: LIB – Úloha | Microsoft Docs
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
- MSBuild (Visual C++), LIB task
- LIB task (MSBuild (Visual C++))
ms.assetid: e062c7f9-cc69-4a83-9361-1bb5355e5fe8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0c9d80da9fea46ddcc2afe2f935fa66a892d90c1
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2019
ms.locfileid: "71254534"
---
# <a name="lib-task"></a>LIB – úloha
Zabalí nástroj Správce bitových knihoven Microsoft 32, *lib. exe*. Správce knihovny vytvoří a spravuje knihovnu souborů objektů COFF (Common Object File Format). Správce knihovny může také vytvářet soubory exportu a importovat knihovny pro odkazování na exportované definice. Další informace naleznete v tématu [lib reference](/cpp/build/reference/lib-reference) a [Running lib](/cpp/build/reference/running-lib).

## <a name="parameters"></a>Parametry
 Následující tabulka popisuje parametry úlohy **lib** . Většina parametrů úlohy odpovídá možnosti příkazového řádku.

|Parametr|Popis|
|---------------|-----------------|
|**AdditionalDependencies**|Parametr volitelného **řetězce []** .<br /><br /> Určuje další položky, které se mají přidat do příkazového řádku.|
|**AdditionalLibraryDirectories**|Parametr volitelného **řetězce []** .<br /><br /> Přepíše cestu ke knihovně prostředí. Zadejte název adresáře.<br /><br /> Další informace najdete v tématu [/LIBPATH (Další Libpath)](/cpp/build/reference/libpath-additional-libpath).|
|**AdditionalOptions**|Volitelný **řetězcový** parametr.<br /><br /> Seznam možností *lib. exe* , jak je uvedeno na příkazovém řádku. Například/\<možnost1 >/\<možnost2 >/\<Option # >. Tento parametr použijte k určení možností *lib. exe* , které nejsou reprezentovány žádným jiným parametrem úlohy **lib** .<br /><br /> Další informace najdete v tématu [spuštění knihovny LIB](/cpp/build/reference/running-lib).|
|**DisplayLibrary**|Volitelný **řetězcový** parametr.<br /><br /> Zobrazí informace o výstupní knihovně. Zadejte název souboru pro přesměrování informací do souboru. Zadejte "CON" nebo nic pro přesměrování informací do konzoly.<br /><br /> Tento parametr odpovídá parametru **/list** příkazu *lib. exe*.|
|**ErrorReporting**|Volitelný **řetězcový** parametr.<br /><br /> Určuje, jak odeslat informace o interní chybě společnosti Microsoft, pokud *lib. exe* v době běhu selhává.<br /><br /> Zadejte jednu z následujících hodnot, z nichž každá odpovídá možnosti příkazového řádku.<br /><br /> -   NoErrorReport -  **/errorreport: none**<br />-   Vyzvatokamžitě -  **/errorreport: prompt**<br />-   **QueueForNextLogin** -  **/ERRORREPORT:QUEUE**<br />-   SendErrorReport -  **/errorreport: Send**<br /><br /> Další informace naleznete v možnosti příkazového řádku **/errorreport** ve [spuštění lib](/cpp/build/reference/running-lib).|
|**ExportNamedFunctions**|Parametr volitelného **řetězce []** .<br /><br /> Určuje jednu nebo více funkcí k exportu.<br /><br /> Tento parametr odpovídá parametru **/Export:** v souboru *lib. exe*.|
|**ForceSymbolReferences**|Volitelný **řetězcový** parametr.<br /><br /> Vynutí *lib. exe* , aby zahrnoval odkaz na zadaný symbol.<br /><br /> Tento parametr odpovídá parametru **/include:** *lib. exe*.|
|**IgnoreAllDefaultLibraries**|Volitelný `Boolean` parametr.<br /><br /> Pokud `true`, odebere všechny výchozí knihovny ze seznamu knihoven, které soubor *lib. exe* vyhledává při překladu externích odkazů.<br /><br /> Tento parametr odpovídá parametru **/NODEFAULTLIB** možnosti *lib. exe*, která je bez parametrů.|
|**IgnoreSpecificDefaultLibraries**|Parametr volitelného **řetězce []** .<br /><br /> Odebere zadané knihovny ze seznamu knihoven, které soubor *lib. exe* vyhledává při překladu externích odkazů.<br /><br /> Tento parametr odpovídá možnosti **/NODEFAULTLIB** souboru *lib. exe* `library` , který přebírá argument.|
|**LinkLibraryDependencies**|Volitelný `Boolean` parametr.<br /><br /> Pokud `true`určuje, že výstupy knihoven ze závislostí projektu jsou automaticky propojeny v.|
|**LinkTimeCodeGeneration**|Volitelný `Boolean` parametr.<br /><br /> Pokud `true`, Určuje generování kódu při propojování.<br /><br /> Tento parametr odpovídá možnosti **/LCTG** souboru *lib. exe*.|
|**MinimumRequiredVersion**|Volitelný **řetězcový** parametr.<br /><br /> Určuje minimální požadovanou verzi subsystému. Zadejte čárkami oddělený seznam desítkových čísel v rozsahu 0 až 65535.|
|**ModuleDefinitionFile**|Volitelný **řetězcový** parametr.<br /><br /> Určuje název souboru definice modulu ( *. def*).<br /><br /> Tento parametr odpovídá možnosti **/def** souboru *lib. exe* `filename` , který přebírá argument.|
|**Název**|Volitelný **řetězcový** parametr.<br /><br /> Při sestavení knihovny importů Určuje název knihovny DLL, pro kterou se knihovna importů sestavuje.<br /><br /> Tento parametr odpovídá parametru **/Name** souboru *lib. exe* `filename` , který přebírá argument.|
|**OutputFile**|Volitelný **řetězcový** parametr.<br /><br /> Přepíše výchozí název a umístění programu, který vytvoří *lib. exe* .<br /><br /> Tento parametr odpovídá možnosti **/out** `filename` , *lib. exe* , která přebírá argument.|
|**RemoveObjects**|Parametr volitelného **řetězce []** .<br /><br /> Vynechá zadaný objekt z výstupní knihovny. *Lib. exe* vytvoří knihovnu výstupu kombinováním všech objektů (ať už v objektových souborech nebo knihovnách) a pak odstraní všechny objekty, které jsou určeny touto možností.<br /><br /> Tento parametr odpovídá možnosti **/Remove** souboru *lib. exe* `membername` , který přebírá argument.|
|**Prostředky**|Povinný `ITaskItem[]` parametr.<br /><br /> Určuje seznam zdrojových souborů oddělených mezerami.|
|**Provozuschopn**|Volitelný **řetězcový** parametr.<br /><br /> Určuje prostředí pro spustitelný soubor. Volba subsystému ovlivní symbol vstupního bodu nebo funkci vstupního bodu.<br /><br /> Zadejte jednu z následujících hodnot, z nichž každá odpovídá možnosti příkazového řádku.<br /><br /> -   Konzola -  **/SUBSYSTEM: konzola**<br />-   **Windows** -  **/SUBSYSTEM:WINDOWS**<br />-   Nativní -  **/SUBSYSTEM: nativní**<br />-   **EFI Application** -  **/SUBSYSTEM: EFI_APPLICATION**<br />-   **EFI Boot Service Driver** -  **/SUBSYSTEM:EFI_BOOT_SERVICE_DRIVER**<br />-   **EFI ROM** -  **/SUBSYSTEM: EFI_ROM**<br />-   **EFI Runtime** -  **/SUBSYSTEM:EFI_RUNTIME_DRIVER**<br />-   **WindowsCE** -  **/SUBSYSTEM:WINDOWSCE**<br />-   **POSIX** -  **/SUBSYSTEM:POSIX**<br /><br /> Další informace najdete v tématu [/Subsystem (určení subsystému)](/cpp/build/reference/subsystem-specify-subsystem).|
|**SuppressStartupBanner**|Volitelný **logický** parametr.<br /><br /> Pokud `true`aplikace zabrání zobrazení zprávy o autorských právech a číslech verze při spuštění úlohy.<br /><br /> Další informace naleznete v možnosti **/nologo** v [běhu lib](/cpp/build/reference/running-lib).|
|**TargetMachine**|Volitelný **řetězcový** parametr.<br /><br /> Určuje cílovou platformu pro program nebo knihovnu DLL.<br /><br /> Zadejte jednu z následujících hodnot, z nichž každá odpovídá možnosti příkazového řádku.<br /><br /> -   MachineARM -  **/Machine: ARM**<br />-   MachineEBC -  **/Machine: EBC**<br />-   MachineIA64 -  **/Machine: ia64**<br />-   MachineMIPS -  **/Machine: MIPS**<br />-   MachineMIPS16 -  **/Machine: MIPS16**<br />-   MachineMIPSFPU - **/Machine: MIPSFPU**<br />-   **MachineMIPSFPU16** -  **/MACHINE:MIPSFPU16**<br />-   **MachineSH4** -  **/MACHINE:SH4**<br />-   MachineTHUMB -  **/Machine: palec**<br />-   MachineX64 -  **/Machine: x64**<br />-   MachineX86 -  **/Machine: x86**<br /><br /> Další informace najdete v tématu [/Machine (určení cílové platformy)](/cpp/build/reference/machine-specify-target-platform).|
|**TrackerLogDirectory**|Volitelný **řetězcový** parametr.<br /><br /> Určuje adresář protokolu sledování.|
|**TreatLibWarningAsErrors**|Volitelný **logický** parametr.<br /><br /> Pokud `true`nástroj způsobí, že úloha **lib** negeneruje výstupní soubor, pokud *lib. exe* vygeneruje upozornění. Pokud `false`je vygenerován výstupní soubor.<br /><br /> Další informace naleznete v možnosti **/WX** v tématu [spuštění lib](/cpp/build/reference/running-lib).|
|**UseUnicodeResponseFiles**|Volitelný **logický** parametr.<br /><br /> Pokud `true`aplikace nastaví systém projektu tak, aby při vytváření Librarian vygeneroval soubory odezvy Unicode. Určete `true` , kdy soubory v projektu mají cesty Unicode.|
|**Verbose**|Volitelný **logický** parametr.<br /><br /> Pokud `true`se zobrazí podrobnosti o průběhu relace; zahrnuje názvy přidaných souborů *. obj* . Informace se odesílají do standardního výstupu a dají se přesměrovat na soubor.<br /><br /> Další informace naleznete v možnosti **/verbose** v tématu [spuštění lib](/cpp/build/reference/running-lib).|

## <a name="see-also"></a>Viz také:
- [Odkaz na úkol](../msbuild/msbuild-task-reference.md)