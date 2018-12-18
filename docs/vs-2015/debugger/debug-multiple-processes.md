---
title: Ladění více procesů | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.programs
- vs.debug.processes.attaching
- vs.debug.activeprogram
- vs.debug.attaching
- vs.debug.attachedprocesses
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: bde37134-66af-4273-b02e-05b3370c31ab
caps.latest.revision: 19
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 56982a3b5c0a0d8a5cb0b682ab67b6f5eb133dd1
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51793045"
---
# <a name="debug-multiple-processes"></a>Ladění více procesů
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tady je postup spuštění procesů ladění, přepínání mezi procesy, přerušení a pokračování v provádění, procházení zdroje, zastavení ladění a ukončit nebo odpojit od procesů.  
  
##  <a name="BKMK_Contents"></a> Obsah  
 [Konfigurace chování spuštění více procesů](#BKMK_Configure_the_execution_behavior_of_multiple_processes)  
  
 [Hledání zdroje a symbolů (PDB) souborů](#BKMK_Find_the_source_and_symbol___pdb__files)  
  
 [Spustit více procesů v řešení VS, připojit k procesu, automaticky spustit proces v ladicím programu](#BKMK_Start_multiple_processes_in_a_VS_solution__attach_to_a_process__automatically_start_a_process_in_the_debugger)  
  
 [Přepnout procesy, přerušení a pokračování v provádění, procházet zdroj](#BKMK_Switch_processes__break_and_continue_execution__step_through_source)  
  
 [Zastavit ladění, ukončit nebo odpojit od procesů](#BKMK_Stop_debugging__terminate_or_detach_from_processes)  
  
##  <a name="BKMK_Configure_the_execution_behavior_of_multiple_processes"></a> Konfigurace chování spuštění více procesů  
 Ve výchozím nastavení když běží více procesů v ladicím programu, nejnovější, krokování a příkazy zastavení ladicího programu obvykle mít vliv na všechny procesy. Například když jeden proces pozastaven na zarážce, spuštění všech procesů je také pozastaveno. Můžete změnit toto výchozí chování získat větší kontrolu nad cíli prováděcích příkazů.  
  
1. Na **ladění** nabídce zvolte **možnosti a nastavení**.  
  
2. Na **ladění**, **Obecné** zrušte **přerušit všechny procesy při přerušení jednoho procesu** zaškrtávací políčko.  
  
   ![Zpět na začátek](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [obsah](#BKMK_Contents)  
  
##  <a name="BKMK_Find_the_source_and_symbol___pdb__files"></a> Hledání zdroje a symbolů (PDB) souborů  
 Chcete-li procházet zdrojový kód procesu, ladicí program potřebuje přístup ke zdrojové soubory a soubory symbolů procesu. Zobrazit [zadání symbolu (.pdb) a zdrojové soubory](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).  
  
 Pokud nelze získat přístup k souborům pro proces, můžete procházet pomocí okno zpětný překlad. Zobrazit [postupy: použití okna zpětného překladu](../debugger/how-to-use-the-disassembly-window.md)  
  
 ![Zpět na začátek](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [obsah](#BKMK_Contents)  
  
##  <a name="BKMK_Start_multiple_processes_in_a_VS_solution__attach_to_a_process__automatically_start_a_process_in_the_debugger"></a> Spustit více procesů v řešení VS, připojit k procesu, automaticky spustit proces v ladicím programu  
  
-   [Spustit ladění více procesů v řešení sady Visual Studio](#BKMK_Start_debugging_multiple_processes_in_a_Visual_Studio_solution) • [změňte spouštěný projekt](#BKMK_Change_the_startup_project) • [spuštění určitého projektu v řešení](#BKMK_Start_a_specific_project_in_a_solution) • [spustit více projektů v řešení](#BKMK_Start_multiple_projects_in_a_solution) • [připojit k procesu](#BKMK_Attach_to_a_process) • [automaticky spustit proces v ladicím programu](#BKMK_Automatically_start_an_process_in_the_debugger)  
  
> [!NOTE]
>  Ladicí program nepřipojí automaticky k podřízenému procesu, který je spuštěn procesem ladění i v případě, že je podřízený projekt ve stejném řešení. Ladění podřízeného procesu:  
> 
> - Připojte se k podřízenému procesu po jeho spuštění.  
> 
>   -nebo-  
>   -   Konfigurace Windows automaticky spustil podřízený proces v nové instanci ladicího programu.  
  
###  <a name="BKMK_Start_debugging_multiple_processes_in_a_Visual_Studio_solution"></a> Spustit ladění více procesů v řešení sady Visual Studio  
 Pokud máte více než jeden projekt v řešení sady Visual Studio, které lze spustit samostatně (projekty, které běží v samostatných procesech), můžete vybrat projekty, které spustí ladicí program.  
  
 ![Změna typu spouštění projektu](../debugger/media/dbg-execution-startmultipleprojects.png "DBG_Execution_StartMultipleProjects")  
  
####  <a name="BKMK_Change_the_startup_project"></a> Změňte spouštěný projekt  
 Chcete-li změnit projekt po spuštění pro řešení, vyberte projekt v Průzkumníku řešení a klikněte na tlačítko **nastavit jako spouštěný projekt** v místní nabídce.  
  
####  <a name="BKMK_Start_a_specific_project_in_a_solution"></a> Spuštění určitého projektu v řešení  
 Chcete-li zahájit projekt pro řešení bez změny výchozího projektu po spuštění, vyberte projekt v Průzkumníku řešení a zvolte **ladění** v místní nabídce. Pak můžete vybrat **zahájit novou instanci** nebo **krok do nové instance**.  
  
 ![Zpět na začátek](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [spustit více procesů v řešení VS, připojit k procesu, automaticky spustit proces v ladicím programu](../debugger/debug-multiple-processes.md#BKMK_Start_multiple_processes_in_a_VS_solution__attach_to_a_process__automatically_start_a_process_in_the_debugger)  
  
 ![Zpět na začátek](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [obsah](#BKMK_Contents)  
  
####  <a name="BKMK_Start_multiple_projects_in_a_solution"></a> Spustit více projektů v řešení  
  
1. V Průzkumníku řešení vyberte řešení a klikněte na tlačítko **vlastnosti** v místní nabídce.  
  
2. Vyberte **společné vlastnosti**, **spouštěný projekt** na **vlastnosti** dialogové okno.  
  
3. Pro každý projekt, který chcete změnit, zvolte buď **Start**, **spustit bez ladění**, nebo **žádný**.  
  
   ![Zpět na začátek](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [spustit více procesů v řešení VS, připojit k procesu, automaticky spustit proces v ladicím programu](../debugger/debug-multiple-processes.md#BKMK_Start_multiple_processes_in_a_VS_solution__attach_to_a_process__automatically_start_a_process_in_the_debugger)  
  
   ![Zpět na začátek](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [obsah](#BKMK_Contents)  
  
###  <a name="BKMK_Attach_to_a_process"></a> Připojit k procesu  
 Ladicí program se můžete také *připojit* programy, které mají spuštěné procesy mimo sadu Visual Studio, včetně programů, které běží na vzdáleném zařízení. Po připojení k programu, můžete použít příkazy spuštění ladicího programu, kontrolovat stav programu a tak dále. Vaše schopnost kontrolovat program může být omezená, v závislosti na tom, zda byl program sestaven s ladicími informacemi a zda máte přístup ke zdrojovému kódu programu a zda kompilátor JIT společného běhového modulu jazyka sleduje informace o ladění.  
  
 Zobrazit [připojení k běžící procesy](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md) Další informace.  
  
 **Připojit k procesu, která běží na místním počítači**  
  
 Zvolte **ladění**, **připojit k procesu**. Na **připojit k procesu** dialogového okna, vyberte proces **procesy k dispozici** seznamu a klikněte na tlačítko **připojit**.  
  
 ![Připojit k procesu – dialogové okno](../debugger/media/dbg-attachtoprocessdlg.png "DBG_AttachToProcessDlg")  
  
 ![Zpět na začátek](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [obsah](#BKMK_Contents)  
  
###  <a name="BKMK_Automatically_start_an_process_in_the_debugger"></a> Automaticky spustit proces v ladicím programu  
 V některých případech může být třeba ladit spouštěcí kód programu, který je spouštěn jiným procesem. Příklady zahrnují služby a akce pro vlastní nastavení. V těchto případech můžete mít ladicí program spuštěn a automaticky připojen při spuštění aplikace.  
  
1. Spusťte Editor registru (**regedit.exe**).  
  
2. Přejděte **HKEY_LOCAL_MACHINE\Software\Microsoft\Windows NT\CurrentVersion\Image File Execution Options** složky.  
  
3. Vyberte složku aplikace, kterou chcete spustit v ladicím programu.  
  
    Pokud aplikace není uveden jako podřízená složka, vyberte **Image File Execution Options** a klikněte na tlačítko **nový**, **klíč** v místní nabídce. Vyberte nový klíč, zvolte **přejmenovat** v místní nabídce a zadejte název aplikace.  
  
4. V kontextové nabídce složky aplikace, zvolte **nový**, **řetězcovou hodnotu**.  
  
5. Změňte název nové hodnoty z **novou hodnotu** k `debugger`.  
  
6. V kontextové nabídce položky ladicího programu, zvolte **změnit**.  
  
7. V dialogovém okně Upravit řetězec zadejte `vsjitdebugger.exe` v **údaj hodnoty** pole.  
  
    ![Řetězec dialogové okno Upravit](../debugger/media/dbg-execution-automaticstart-editstringdlg.png "DBG_Execution_AutomaticStart_EditStringDlg")  
  
   ![Automatické ladicí program spustit záznam v regedit.exe](../debugger/media/dbg-execution-automaticstart-result.png "DBG_Execution_AutomaticStart_Result")  
  
   ![Zpět na začátek](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [obsah](#BKMK_Contents)  
  
##  <a name="BKMK_Switch_processes__break_and_continue_execution__step_through_source"></a> Přepnout procesy, přerušení a pokračování v provádění, procházet zdroj  
  
-   [Přepínání mezi procesy](#BKMK_Switch_between_processes) • [přerušení, kroku a pokračovat příkazy](#BKMK_Break__step__and_continue_commands)  
  
###  <a name="BKMK_Switch_between_processes"></a> Přepínání mezi procesy  
 Můžete se připojit k více procesům při ladění, ale pouze jeden proces je v daném okamžiku aktivní v ladicím programu. Lze nastavit aktivní nebo *aktuální* zpracovat v panelu nástrojů umístění ladění nebo **procesy** okna. Chcete-li přepnout mezi procesy, oba procesy musí být v režimu pozastavení.  
  
 **Chcete-li nastavit aktuální proces**  
  
- Na panelu nástrojů umístění ladění **procesu** zobrazíte **procesu** pole se seznamem. Vyberte proces, který chcete nastavit jako aktuální proces.  
  
   ![Přepínání mezi procesy](../debugger/media/dbg-execution-switchbetweenmodules.png "DBG_Execution_SwitchBetweenModules")  
  
   Pokud **umístění ladění** nástrojů se nezobrazuje, vyberte **nástroje**, **vlastní**. Na **panely nástrojů** kartě **umístění ladění**.  
  
- Otevřít **procesy** okno (místní **Ctrl + Alt + Z**), vyhledejte proces, který chcete nastavit jako aktuální proces a poklepejte na něj.  
  
   ![Procesy – okno](../debugger/media/dbg-processeswindow.png "DBG_ProcessesWindow")  
  
   Aktuální proces je označen žlutou šipkou.  
  
  Přepnutí do projektu ji nastaví aktuální proces pro účely ladění. Jakékoli okno ladicího programu, která se zobrazují se zobrazí stav pro aktuální proces a všechny příkazy krokování ovlivní pouze aktuální proces.  
  
  ![Zpět na začátek](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [přepnout procesy, přerušení a pokračování v provádění, procházet zdroj](../debugger/debug-multiple-processes.md#BKMK_Switch_processes__break_and_continue_execution__step_through_source)  
  
  ![Zpět na začátek](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [obsah](#BKMK_Contents)  
  
###  <a name="BKMK_Break__step__and_continue_commands"></a> Přerušit, krokovat a pokračovat příkazy  
  
> [!NOTE]
>  Ve výchozím nastavení "break", pokračovat a kroku ladicího programu příkazy vliv na všechny procesy, které jsou právě laděny. Chcete-li toto chování změnit, přečtěte si téma [konfigurace chování spuštění více procesů](#BKMK_Configure_the_execution_behavior_of_multiple_processes)  
  
||||  
|-|-|-|  
|**Příkaz**|**Přerušit všechny procesy při přerušení jednoho procesu**<br /><br /> Zkontrolováno (výchozí)|**Přerušit všechny procesy při přerušení jednoho procesu**<br /><br /> Vymazat|  
|**Ladění** nabídky:<br /><br /> -   **Přerušit vše**|Budou přerušeny všechny procesy.|Budou přerušeny všechny procesy.|  
|**Ladění** nabídky:<br /><br /> -   **pokračovat**|Obnoví se všechny procesy.|Všechny pozastavené procesy budou pokračovat.|  
|**Ladění** nabídky:<br /><br /> -   **Krokovat s vnořením**<br />-   **Krok přes**<br />-   **Krokovat s Vystoupením**|Všechny procesy jsou spuštěny během kroků aktuálního procesu.<br /><br /> Pak budou přerušeny všechny procesy.|Aktuální kroky procesu.<br /><br /> Pokračování pozastavených procesů.<br /><br /> Spuštěné procesy pokračují.|  
|**Ladění** nabídky:<br /><br /> -   **Krok do aktuálního procesu**<br />-   **Krok přes aktuální proces**<br />-   **Krok z aktuálního procesu**|Není k dispozici|Aktuální kroky procesu.<br /><br /> Jiné procesy udržují svůj stávající stav (pozastaveno nebo spuštěno).|  
|Okno zdroje<br /><br /> -   **Zarážky**|Budou přerušeny všechny procesy.|Pouze zdrojové okno proces bude ukončen.|  
|Kontextová nabídka okna zdroje:<br /><br /> -   **Spustit ke kurzoru**<br /><br /> Okno zdroje musí být v aktuálním procesu.|Všechny procesy jsou spuštěny během procesu zdrojového okna je spuštěn na kurzoru a poté se přeruší.<br /><br /> Pak budou přerušeny všechny procesy.|Proces zdrojového okna je spuštěn na kurzoru.<br /><br /> Jiné procesy udržují svůj stávající stav (pozastaveno nebo spuštěno).|  
|**Procesy** Kontextová nabídka okna:<br /><br /> -   **Ukončit proces**|Není k dispozici|Vybraný proces bude ukončen.<br /><br /> Jiné procesy udržují svůj stávající stav (pozastaveno nebo spuštěno).|  
|**Procesy** Kontextová nabídka okna:<br /><br /> -   **Pokračování procesu**|Není k dispozici|Vybraný proces bude pokračovat.<br /><br /> Jiné procesy udržují svůj stávající stav (pozastaveno nebo spuštěno).|  
  
 ![Zpět na začátek](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [přepnout procesy, přerušení a pokračování v provádění, procházet zdroj](../debugger/debug-multiple-processes.md#BKMK_Switch_processes__break_and_continue_execution__step_through_source)  
  
 ![Zpět na začátek](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [obsah](#BKMK_Contents)  
  
##  <a name="BKMK_Stop_debugging__terminate_or_detach_from_processes"></a> Zastavit ladění, ukončit nebo odpojit od procesů  
  
- [Zastavit, ukončit a odebrat příkazy](#BKMK_Stop__terminate__and_detach_commands)  
  
  Ve výchozím nastavení, když zvolíte **ladění**, **Zastavit ladění** při otevřeno více procesů v ladicím programu, ladicí program se ukončí nebo odpojí od všech procesů v závislosti na tom, jak byl proces otevřít v ladicí program:  
  
- Pokud byl aktuální proces spuštěn v ladicím programu, tento proces bude ukončen.  
  
- Pokud jste se připojili k aktuálnímu procesu ladicího programu, ladicí program se odpojí z procesu a ponechá proces spuštěný.  
  
  Například pokud spustíte ladění procesu v řešení sady Visual Studio, připojit k jiným procesem, který je již spuštěn a klikněte na tlačítko **Zastavit ladění**, relace ladění skončí, proces spuštěný v sadě Visual Studio je ukončen, zatímco proces, který jste připojili, zůstane spuštěn. Následující postupy můžete použít k řízení způsobu, jakým zastavujete ladění.  
  
> [!NOTE]
>  **Přerušit všechny procesy při přerušení jednoho procesu** možnost nemá vliv na zastavení ladění nebo ukončení a odpojení od procesů.  
  
 **Chcete-li změnit Zastavit ladění vliv na jednotlivé procesy**  
  
-   Otevřít **procesy** okno (místní **Ctrl + Alt + Z**). Vyberte proces a pak zaškrtněte nebo zrušte **odpojit při zastavení ladění** zaškrtávací políčko.  
  
###  <a name="BKMK_Stop__terminate__and_detach_commands"></a> Zastavit, ukončit a odebrat příkazy  
  
|||  
|-|-|  
|**Příkaz**|**Popis**|  
|**Ladění** nabídky:<br /><br /> -   **Zastavit ladění**|Pokud se změní chování podle **procesy** okno **odpojit při zastavení ladění** možnost:<br /><br /> 1.  Procesy spuštěné ladicím programem jsou ukončeny.<br />2.  Připojené procesy jsou odpojeny od ladicího programu.|  
|**Ladění** nabídky:<br /><br /> -   **Ukončit vše**|Všechny procesy budou ukončeny.|  
|**Ladění** nabídky:<br /><br /> -   **Odpojit vše**|Ladicí program se odpojí od všech procesů.|  
|**Procesy** Kontextová nabídka okna:<br /><br /> -   **Odpojit proces**|Ladicí program se odpojí z vybraných procesů.<br /><br /> Jiné procesy udržují svůj stávající stav (pozastaveno nebo spuštěno).|  
|**Procesy** Kontextová nabídka okna:<br /><br /> -   **Ukončit proces**|Vybraný proces je ukončen.<br /><br /> Jiné procesy udržují svůj stávající stav (pozastaveno nebo spuštěno).|  
|**Procesy** Kontextová nabídka okna:<br /><br /> -   **Odpojit při zastavení ladění**|Přepíná chování **ladění**, **Zastavit ladění** u vybraného procesu:<br /><br /> -Kontrola: Ladicí program se odpojí z procesu.<br />-Zrušeno: Proces je ukončen.|  
  
 ![Zpět na začátek](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Zastavit ladění, ukončit nebo odpojit od procesů](../debugger/debug-multiple-processes.md#BKMK_Stop_debugging__terminate_or_detach_from_processes)  
  
 ![Zpět na začátek](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [obsah](#BKMK_Contents)  
  
## <a name="see-also"></a>Viz také  
 [Zadání symbolu (.pdb) a zdrojové soubory](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)   
 [Připojení ke spuštěným procesům](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [Procházení kódu s ladicím programem](../debugger/navigating-through-code-with-the-debugger.md)   
 [Ladění Just-In-Time](../debugger/just-in-time-debugging-in-visual-studio.md)   
 [Ladění vícevláknových aplikací](../debugger/debug-multithreaded-applications-in-visual-studio.md)



