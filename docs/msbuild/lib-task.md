---
title: Lib Úkol | Dokumenty společnosti Microsoft
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
ms.openlocfilehash: a5794d059a17f39531a7788895b604ae0e9590ce
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633587"
---
# <a name="lib-task"></a>LIB – úloha

Zabalí nástroj Správce 32bitové knihovny společnosti Microsoft, *lib.exe*. Správce knihovny vytváří a spravuje knihovnu souborů objektů COFF (Common Object File Format). Správce knihovny může také vytvářet exportní soubory a knihovny importu pro odkaz na exportované definice. Další informace naleznete v [tématu ODKAZ LIB](/cpp/build/reference/lib-reference) a [spuštění LIB](/cpp/build/reference/running-lib).

## <a name="parameters"></a>Parametry

 Následující tabulka popisuje parametry úlohy **LIB.** Většina parametrů úlohy odpovídá možnosti příkazového řádku.

|Parametr|Popis|
|---------------|-----------------|
|**Další závislosti**|Volitelný **parametr String[].**<br /><br /> Určuje další položky, které mají být přidejte do příkazového řádku.|
|**Další adresáře knihovny**|Volitelný **parametr String[].**<br /><br /> Přepíše cestu knihovny prostředí. Zadejte název adresáře.<br /><br /> Další informace naleznete v tématu [/LIBPATH (Additional Libpath)](/cpp/build/reference/libpath-additional-libpath).|
|**Další možnosti**|Volitelný **parametr String.**<br /><br /> Seznam možností *lib.exe* určený na příkazovém řádku. Například /\<option1\<> /\<option2> / option#>. Tento parametr slouží k určení možností *lib.exe,* které nejsou reprezentovány žádným jiným parametrem úlohy **LIB.**<br /><br /> Další informace naleznete v [tématu Running LIB](/cpp/build/reference/running-lib).|
|**Knihovna zobrazení**|Volitelný **parametr String.**<br /><br /> Zobrazí informace o výstupní knihovně. Zadejte název souboru, který chcete přesměrovat informace do souboru. Zadejte "CON" nebo nic přesměrovat informace do konzoly.<br /><br /> Tento parametr odpovídá možnosti **/LIST** *souboru lib.exe*.|
|**Hlášení chyb**|Volitelný **parametr String.**<br /><br /> Určuje způsob odeslání informací o vnitřní chybě společnosti Microsoft, pokud *program lib.exe* za běhu selže.<br /><br /> Zadejte jednu z následujících hodnot, z nichž každá odpovídá možnosti příkazového řádku.<br /><br /> -   **NoErrorReport** - **/ERRORREPORT:NONE**<br />-   **PromptImmediately** - **/ERRORREPORT:VÝZVA**<br />-   **QueueForNextLogin** - **/ERRORREPORT:FRONTA**<br />-   **SendErrorReport** - **/ERRORREPORT:ODESLAT**<br /><br /> Další informace naleznete v příkazovém řádku **/ERRORREPORT** v [části Spuštění LIB](/cpp/build/reference/running-lib).|
|**Funkce ExportNamed**|Volitelný **parametr String[].**<br /><br /> Určuje jednu nebo více funkcí, které chcete exportovat.<br /><br /> Tento parametr odpovídá parametru **/EXPORT:** parametr *lib.exe*.|
|**ForceSymbolReferences**|Volitelný **parametr String.**<br /><br /> Vynutí, aby *odkaz lib.exe* obsahoval odkaz na zadaný symbol.<br /><br /> Tento parametr odpovídá možnosti **/INCLUDE:** *lib.exe*.|
|**Ignorovatvšechny výchozí knihovny**|Volitelný `Boolean` parametr.<br /><br /> Pokud `true`odebere všechny výchozí knihovny ze seznamu knihoven, které *lib.exe* hledá při řešení externích odkazů.<br /><br /> Tento parametr odpovídá formě bez parametrů možnosti **/NODEFAULTLIB** *příkazu lib.exe*.|
|**IgnoreSpecificDefaultKnihovny**|Volitelný **parametr String[].**<br /><br /> Odebere zadané knihovny ze seznamu knihoven, které *lib.exe* prohledává při řešení externích odkazů.<br /><br /> Tento parametr odpovídá **/NODEFAULTLIB** možnost *lib.exe,* `library` který trvá argument.|
|**Závislostí knihovny propojení**|Volitelný `Boolean` parametr.<br /><br /> Pokud `true`aplikace určuje, že výstupy knihovny ze závislostí projektu jsou automaticky propojeny.|
|**Generování kódu LinkTime**|Volitelný `Boolean` parametr.<br /><br /> Pokud `true`určuje generování kódu v době propojení.<br /><br /> Tento parametr odpovídá možnosti **/LCTG** *souboru lib.exe*.|
|**Minimální požadovaná verze**|Volitelný **parametr String.**<br /><br /> Určuje minimální požadovanou verzi subsystému. Zadejte seznam desetinných čísel oddělený čárkami v rozsahu 0 až 65535.|
|**ModuleDefinitionFile**|Volitelný **parametr String.**<br /><br /> Určuje název souboru definice modulu (*.def*).<br /><br /> Tento parametr odpovídá možnosti **/DEF** *souboru lib.exe,* která přebírá `filename` argument.|
|**Název**|Volitelný **parametr String.**<br /><br /> Při sestrojování knihovny importu určuje název knihovny DLL, pro kterou je knihovna importu právě vytvořena.<br /><br /> Tento parametr odpovídá možnosti **/NAME** souboru *lib.exe,* která přebírá `filename` argument.|
|**Výstupní soubor**|Volitelný **parametr String.**<br /><br /> Přepíše výchozí název a umístění programu, který *vytvoří program lib.exe.*<br /><br /> Tento parametr odpovídá **/OUT** možnost *lib.exe,* `filename` který trvá argument.|
|**Odebrat objekty**|Volitelný **parametr String[].**<br /><br /> Vynese zadaný objekt z výstupní knihovny. *Lib.exe* vytvoří výstupní knihovnu kombinací všech objektů (ať už v objektových souborech nebo knihovnách) a následným odstraněním všech objektů, které jsou určeny touto volbou.<br /><br /> Tento parametr odpovídá možnosti **/REMOVE** souboru *lib.exe,* která přebírá `membername` argument.|
|**Zdrojů**|Požadovaný parametr `ITaskItem[]`.<br /><br /> Určuje seznam zdrojových souborů oddělených mezerami.|
|**Subsystému**|Volitelný **parametr String.**<br /><br /> Určuje prostředí pro spustitelný soubor. Volba subsystému ovlivňuje symbol vstupního bodu nebo funkci vstupního bodu.<br /><br /> Zadejte jednu z následujících hodnot, z nichž každá odpovídá možnosti příkazového řádku.<br /><br /> -   **Konzola** - **/SUBSYSTÉM:KONZOLA**<br />-   **Windows** - **/SUBSYSTÉM:WINDOWS**<br />-   **Nativní** - **/SUBSYSTEM:NATIVNÍ**<br />-   **Aplikace EFI** - **/SUBSYSTÉM:EFI_APPLICATION**<br />-   **Ovladač spouštěcí služby EFI** - **/SUBSYSTEM:EFI_BOOT_SERVICE_DRIVER**<br />-   **EFI ROM** - **/SUBSYSTÉM:EFI_ROM**<br />-   **EFI Runtime** - **/SUBSYSTÉM:EFI_RUNTIME_DRIVER**<br />-   **WindowsCE** - **/SUBSYSTÉM:WINDOWSCE**<br />-   **POSIX** - **/SUBSYSTÉM:POSIX**<br /><br /> Další informace naleznete v tématu [/SUBSYSTEM (Specify subsystem)](/cpp/build/reference/subsystem-specify-subsystem).|
|**PotlačitStartupBanner**|Volitelný **logický** parametr.<br /><br /> Pokud `true`aplikace zabraňuje zobrazení zprávy o autorských právech a čísle verze při spuštění úlohy.<br /><br /> Další informace naleznete v tématu **/NOLOGO** option at [Running LIB](/cpp/build/reference/running-lib).|
|**TargetMachine**|Volitelný **parametr String.**<br /><br /> Určuje cílovou platformu pro program nebo dll.<br /><br /> Zadejte jednu z následujících hodnot, z nichž každá odpovídá možnosti příkazového řádku.<br /><br /> -   **MachineARM** - **/ STROJ: ARM**<br />-   **MachineEBC** - **/STROJ:EBC**<br />-   **MachineIA64** - **/STROJ:IA64**<br />-   **MachineMIPS** - **/STROJ:MIPS**<br />-   **MachineMIPS16** - **/STROJ:MIPS16**<br />-   **MachineMIPSFPU** -**/STROJ:MIPSFPU**<br />-   **MachineMIPSFPU16** - **/STROJ:MIPSFPU16**<br />-   **StrojSH4** - **/STROJ:SH4**<br />-   **MachineTHUMB** - **/ STROJ: PALEC**<br />-   **StrojX64** - **/STROJ:X64**<br />-   **StrojX86** - **/STROJ:X86**<br /><br /> Další informace naleznete v tématu [/MACHINE (Zadat cílovou platformu).](/cpp/build/reference/machine-specify-target-platform)|
|**TrackerLogDirectory**|Volitelný **parametr String.**<br /><br /> Určuje adresář protokolu sledování.|
|**TreatLibWarningAsErrors**|Volitelný **logický** parametr.<br /><br /> Pokud `true`způsobí, že úloha **LIB** nevygeneruje výstupní soubor, pokud *lib.exe* generuje upozornění. Pokud `false`je vygenerován výstupní soubor.<br /><br /> Další informace naleznete v tématu **/WX** možnost [spuštění LIB](/cpp/build/reference/running-lib).|
|**UseUnicodeResponseFiles**|Volitelný **logický** parametr.<br /><br /> Pokud `true`, pokyn systému projektu ke generování UNICODE soubory odpovědí, když knihovník je plodil. Určete, `true` kdy mají soubory v projektu cesty UNICODE.|
|**Podrobné**|Volitelný **logický** parametr.<br /><br /> Pokud `true`se zobrazí podrobnosti o průběhu relace; To zahrnuje názvy přidávaných souborů *OBJ.* Informace jsou odeslány do standardního výstupu a mohou být přesměrovány do souboru.<br /><br /> Další informace naleznete v tématu **/VERBOSE** možnost [spuštění LIB](/cpp/build/reference/running-lib).|

## <a name="see-also"></a>Viz také

- [Odkaz na úkol](../msbuild/msbuild-task-reference.md)