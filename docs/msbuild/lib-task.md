---
title: Lib – úloha | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: df6011cb1c706069135a133dd37a34e54203b22b
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/17/2018
ms.locfileid: "39079621"
---
# <a name="lib-task"></a>LIB – úloha
Zabalí nástroj Správce 32bitové Microsoft knihovny *lib.exe*. Správce knihovny vytváří a spravuje knihovnu objektových souborů Common Object File Format (COFF). Správce knihovny můžete vytvořit soubory exportu a importu knihovny odkaz exportovat definice. Další informace najdete v tématu [LIB odkaz](/cpp/build/reference/lib-reference) a [spuštění knihovny LIB](/cpp/build/reference/running-lib).  
  
## <a name="parameters"></a>Parametry  
 Následující tabulka popisuje parametry **LIB** úloh. Většina úkolů parametry odpovídají možnost příkazového řádku.  
  
|Parametr|Popis|  
|---------------|-----------------|  
|**AdditionalDependencies**|Volitelné **String []** parametru.<br /><br /> Určuje další položky pro přidání do příkazového řádku.|  
|**AdditionalLibraryDirectories**|Volitelné **String []** parametru.<br /><br /> Přepíše cestu ke knihovně prostředí. Zadejte název adresáře.<br /><br /> Další informace najdete v tématu [/Libpath (další proměnná Libpath)](/cpp/build/reference/libpath-additional-libpath).|  
|**AdditionalOptions**|Volitelné **řetězec** parametru.<br /><br /> Seznam *lib.exe* možnosti, jak je uvedeno v příkazovém řádku. Třeba /\<možnost1 > /\<možnost2 > /\<možnost #>. Tento parametr použijte k určení *lib.exe* možnosti, které nejsou reprezentovány jakýkoli jiný **LIB** parametr úlohy.<br /><br /> Další informace najdete v tématu [spuštění knihovny LIB](/cpp/build/reference/running-lib).|  
|**DisplayLibrary**|Volitelné **řetězec** parametru.<br /><br /> Zobrazí informace o výstupní knihovně. Zadejte název souboru pro přesměrování informace do souboru. Zadejte "CON" nebo nic přesměrovat informace do konzoly.<br /><br /> Tento parametr **/LIST** možnost *lib.exe*.|  
|**ErrorReporting**|Volitelné **řetězec** parametru.<br /><br /> Určuje, jak odeslat informace o interní chybě společnosti Microsoft, pokud *lib.exe* selže v době běhu.<br /><br /> Zadejte jednu z následujících hodnot, z nichž každý odpovídá možnosti příkazového řádku.<br /><br /> -   **NoErrorReport** -   **/errorreport: žádné**<br />-   **PromptImmediately** - **/ERRORREPORT:PROMPT**<br />-   **QueueForNextLogin** - **/ERRORREPORT:QUEUE**<br />-   **SendErrorReport** -   **/errorreport: Send**<br /><br /> Další informace najdete v tématu **/errorreport** možnost příkazového řádku na [spuštění knihovny LIB](/cpp/build/reference/running-lib).|  
|**ExportNamedFunctions**|Volitelné **String []** parametru.<br /><br /> Určuje jednu nebo více funkcí pro export.<br /><br /> Tento parametr **/EXPORT:** možnost *lib.exe*.|  
|**ForceSymbolReferences**|Volitelné **řetězec** parametru.<br /><br /> Vynutí *lib.exe* zahrnout odkaz na zadaný symbol.<br /><br /> Tento parametr **/INCLUDE:** možnost *lib.exe*.|  
|**IgnoreAllDefaultLibraries**|Volitelné `Boolean` parametru.<br /><br /> Pokud `true`, odebere všechny výchozí knihovny ze seznamu knihoven, které *lib.exe* prohledává při překladu externích odkazů.<br /><br /> Tento parametr odpovídá formě bez parametrů **: / NODEFAULTLIB** možnost *lib.exe*.|  
|**IgnoreSpecificDefaultLibraries**|Volitelné **String []** parametru.<br /><br /> Odebere zadaný knihoven ze seznamu knihoven, které *lib.exe* prohledává při překladu externích odkazů.<br /><br /> Tento parametr **: / NODEFAULTLIB** možnost *lib.exe* , která přijímá `library` argument.|  
|**LinkLibraryDependencies**|Volitelné `Boolean` parametru.<br /><br /> Pokud `true`, určuje, že knihovny vytvořené jako výstupy závislostí projektu automaticky připojeny.|  
|**LinkTimeCodeGeneration**|Volitelné `Boolean` parametru.<br /><br /> Pokud `true`, určuje generování kódu při propojování.<br /><br /> Tento parametr **/LCTG** možnost *lib.exe*.|  
|**MinimumRequiredVersion**|Volitelné **řetězec** parametru.<br /><br /> Určuje minimální požadovanou verzi subsystému. Zadejte čárkami oddělený seznam desetinná čísla v rozsahu 0 až 65535.|  
|**ModuleDefinitionFile**|Volitelné **řetězec** parametru.<br /><br /> Určuje název souboru definice modulu (*.def*).<br /><br /> Tento parametr **def** možnost *lib.exe* , která přijímá `filename` argument.|  
|**Jméno**|Volitelné **řetězec** parametru.<br /><br /> Při vytváření knihovny importu, určuje název knihovny DLL pro kterou má být sestaven knihovny importu.<br /><br /> Tento parametr **/NAME** možnost *lib.exe* , která přijímá `filename` argument.|  
|**Výstupní soubor**|Volitelné **řetězec** parametru.<br /><br /> Přepíše výchozí název a umístění programu, který *lib.exe* vytvoří.<br /><br /> Tento parametr **/OUT** možnost *lib.exe* , která přijímá `filename` argument.|  
|**RemoveObjects**|Volitelné **String []** parametru.<br /><br /> Vynechá zadaný objekt z výstupní knihovně. *Lib.exe* vytvoří výstupní knihovnu tak, že zkombinuje všechny objekty (ať už v souborech objektů nebo knihoven) a poté odstraní všechny objekty, které jsou určeny tuto možnost.<br /><br /> Tento parametr **/REMOVE** možnost *lib.exe* , která přijímá `membername` argument.|  
|**Zdroje**|Vyžaduje `ITaskItem[]` parametru.<br /><br /> Určuje seznam zdrojových souborů, oddělené mezerami.|  
|**Subsystém**|Volitelné **řetězec** parametru.<br /><br /> Určuje prostředí pro spustitelný soubor. Volba subsystému ovlivňuje symbol vstupního bodu nebo funkci vstupního bodu.<br /><br /> Zadejte jednu z následujících hodnot, z nichž každý odpovídá možnosti příkazového řádku.<br /><br /> -   **Konzola** -   **/Subsystem: Console**<br />-   **Windows** -   **/Subsystem: Windows**<br />-   **Nativní** - **souboru**<br />-   **Aplikace EFI** - **/SUBSYSTEM:EFI_APPLICATION**<br />-   **Ovladač spouštěcí služby EFI** - **/SUBSYSTEM:EFI_BOOT_SERVICE_DRIVER**<br />-   **PAMĚŤ ROM EFI** - **/SUBSYSTEM:EFI_ROM**<br />-   **Modul Runtime EFI** - **/SUBSYSTEM:EFI_RUNTIME_DRIVER**<br />-   **WindowsCE** - **/SUBSYSTEM:WINDOWSCE**<br />-   **POSIX** - **/SUBSYSTEM:POSIX**<br /><br /> Další informace najdete v tématu [/Subsystem (určení subsystému)](/cpp/build/reference/subsystem-specify-subsystem).|  
|**SuppressStartupBanner**|Volitelné **logická** parametru.<br /><br /> Pokud `true`, zabraňuje zobrazování čísel zprávu o autorských právech a verze při spuštění úlohy.<br /><br /> Další informace najdete v tématu **/nologo** možnost v [spuštění knihovny LIB](/cpp/build/reference/running-lib).|  
|**TargetMachine**|Volitelné **řetězec** parametru.<br /><br /> Určuje cílovou platformu pro program nebo knihovnu DLL.<br /><br /> Zadejte jednu z následujících hodnot, z nichž každý odpovídá možnosti příkazového řádku.<br /><br /> -   **MachineARM** - **/MACHINE:ARM**<br />-   **MachineEBC** - **/MACHINE:EBC**<br />-   **MachineIA64** - **/MACHINE:IA64**<br />-   **MachineMIPS** - **/MACHINE:MIPS**<br />-   **MachineMIPS16** - **/MACHINE:MIPS16**<br />-   **MachineMIPSFPU** -**/MACHINE:MIPSFPU**<br />-   **MachineMIPSFPU16** - **/MACHINE:MIPSFPU16**<br />-   **MachineSH4** - **/MACHINE:SH4**<br />-   **MachineTHUMB** - **/MACHINE:THUMB**<br />-   **MachineX64** - **/MACHINE:X 64**<br />-   **MachineX86** - **/MACHINE:X 86**<br /><br /> Další informace najdete v tématu [/Machine (zadání cílové platformy)](/cpp/build/reference/machine-specify-target-platform).|  
|**TrackerLogDirectory**|Volitelné **řetězec** parametru.<br /><br /> Určuje adresář protokolu sledovacího modulu.|  
|**TreatLibWarningAsErrors**|Volitelné **logická** parametru.<br /><br /> Pokud `true`, způsobí, že **LIB** úkolů nelze vytvořit výstupní soubor, pokud *lib.exe* vygeneruje upozornění. Pokud `false`, vygeneruje výstupní soubor.<br /><br /> Další informace najdete v tématu **/WX** možnost v [spuštění knihovny LIB](/cpp/build/reference/running-lib).|  
|**UseUnicodeResponseFiles**|Volitelné **logická** parametru.<br /><br /> Pokud `true`, nastaví systém projektu při není vytvořen nástrojem librarian generoval soubory odezvy UNICODE. Zadejte `true` Pokud soubory v projektu mají cesty UNICODE.|  
|**Verbose**|Volitelné **logická** parametru.<br /><br /> Pokud `true`, se zobrazí podrobnosti o průběhu relace; to zahrnuje názvy *.obj* přidávané soubory. Informace odeslány na standardní výstup a je možné přesměrovat do souboru.<br /><br /> Další informace najdete v tématu **/VERBOSE** možnost [spuštění knihovny LIB](/cpp/build/reference/running-lib).|  
  
## <a name="see-also"></a>Viz také:  
 [Referenční dokumentace úlohy](../msbuild/msbuild-task-reference.md)