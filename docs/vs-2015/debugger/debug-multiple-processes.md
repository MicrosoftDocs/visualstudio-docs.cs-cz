---
title: Ladění více procesů | Dokumenty společnosti Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
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
manager: jillfra
ms.openlocfilehash: 9a2679825d41a6360dde05e7511d607f8be69dfa
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/13/2020
ms.locfileid: "79302551"
---
# <a name="debug-multiple-processes"></a>Ladění více procesů
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tady je postup, jak spustit procesy ladění, přepínat mezi procesy, přerušit a pokračovat v provádění, krokovat zdroj, zastavit ladění a ukončit nebo odpojit od procesů.  
  
## <a name="contents"></a><a name="BKMK_Contents"></a>Obsah  
 [Konfigurace chování provádění více procesů](#BKMK_Configure_the_execution_behavior_of_multiple_processes)  
  
 [Vyhledání zdrojových a symbolových souborů (.pdb)](#BKMK_Find_the_source_and_symbol___pdb__files)  
  
 [Spuštění více procesů v řešení VS, připojení k procesu, automatické spuštění procesu v ladicím programu](#BKMK_Start_multiple_processes_in_a_VS_solution__attach_to_a_process__automatically_start_a_process_in_the_debugger)  
  
 [Přepínat procesy, přerušit a pokračovat v provádění, krokprocházet zdrojem](#BKMK_Switch_processes__break_and_continue_execution__step_through_source)  
  
 [Zastavení ladění, ukončení nebo odpojení od procesů](#BKMK_Stop_debugging__terminate_or_detach_from_processes)  
  
## <a name="configure-the-execution-behavior-of-multiple-processes"></a><a name="BKMK_Configure_the_execution_behavior_of_multiple_processes"></a>Konfigurace chování provádění více procesů  
 Ve výchozím nastavení, pokud je v ladicím programu spuštěno více procesů, příkazy ladicího programu, které se lámou, ladijí a zastavují, obvykle ovlivňují všechny procesy. Například při pozastavení jednoho procesu na zarážku, provádění všech ostatních procesů je také pozastavena. Toto výchozí chování můžete změnit, chcete-li získat větší kontrolu nad cíli příkazů provádění.  
  
1. V nabídce **Ladění** zvolte **Možnosti a Nastavení**.  
  
2. Na stránce **Ladění**, **Obecné** zrušte zaškrtnutí políčka Přerušit **všechny procesy, když jeden proces přeruší.**  
  
   ![Zpět na začátek](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Obsah](#BKMK_Contents)  
  
## <a name="find-the-source-and-symbol-pdb-files"></a><a name="BKMK_Find_the_source_and_symbol___pdb__files"></a>Vyhledání zdrojových a symbolových souborů (.pdb)  
 Chcete-li procházet zdrojový kód procesu, ladicí program potřebuje přístup ke zdrojovým souborům a souborům symbolů procesu. Viz [Určení symbolu (.pdb) a zdrojových souborů](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).  
  
 Pokud nemáte přístup k souborům pro proces, můžete přejít pomocí okna Disassemby. Viz [Postup: Použití okna demontáže](../debugger/how-to-use-the-disassembly-window.md)  
  
 ![Zpět na začátek](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Obsah](#BKMK_Contents)  
  
## <a name="start-multiple-processes-in-a-vs-solution-attach-to-a-process-automatically-start-a-process-in-the-debugger"></a><a name="BKMK_Start_multiple_processes_in_a_VS_solution__attach_to_a_process__automatically_start_a_process_in_the_debugger"></a>Spuštění více procesů v řešení VS, připojení k procesu, automatické spuštění procesu v ladicím programu  
  
- [Zahájení ladění více procesů v řešení sady Visual Studio](#BKMK_Start_debugging_multiple_processes_in_a_Visual_Studio_solution) • Změna projektu [spuštění](#BKMK_Change_the_startup_project) • [Spuštění konkrétního projektu v řešení](#BKMK_Start_a_specific_project_in_a_solution) • Spuštění více projektů v [řešení](#BKMK_Start_multiple_projects_in_a_solution) • Připojení [k procesu](#BKMK_Attach_to_a_process) • [Automatické spuštění procesu v ladicím programu](#BKMK_Automatically_start_an_process_in_the_debugger)  
  
> [!NOTE]
> Ladicí program se automaticky nepřipojí k podřízenému procesu, který je spuštěn laděným procesem, a to i v případě, že podřízený projekt je ve stejném řešení. Ladění podřízeného procesu:  
> 
> - Připojte se k podřízenému procesu po jeho spuštění.  
> 
>   -nebo-  
>   - Nakonfigurujte systém Windows tak, aby automaticky spustil podřízený proces v nové instanci ladicího programu.  
  
### <a name="start-debugging-multiple-processes-in-a-visual-studio-solution"></a><a name="BKMK_Start_debugging_multiple_processes_in_a_Visual_Studio_solution"></a>Zahájení ladění více procesů v řešení sady Visual Studio  
 Pokud máte více než jeden projekt v řešení sady Visual Studio, který lze spustit nezávisle (projekty, které běží v samostatných procesech), můžete vybrat, které projekty ladicí program spustí.  
  
 ![Změna typu spuštění projektu](../debugger/media/dbg-execution-startmultipleprojects.png "DBG_Execution_StartMultipleProjects")  
  
#### <a name="change-the-startup-project"></a><a name="BKMK_Change_the_startup_project"></a>Změna spouštěcího projektu  
 Chcete-li změnit projekt spuštění řešení, vyberte projekt v Průzkumníku řešení a pak z kontextové nabídky zvolte **Nastavit jako spouštěcí projekt.**  
  
#### <a name="start-a-specific-project-in-a-solution"></a><a name="BKMK_Start_a_specific_project_in_a_solution"></a>Zahájení konkrétního projektu v řešení  
 Chcete-li spustit projekt řešení bez změny výchozího projektu při spuštění, vyberte projekt v Průzkumníku řešení a pak z kontextové nabídky zvolte **Ladění.** Potom můžete zvolit **Spustit novou instanci** nebo **Krok do nové instance**.  
  
 ![Zpět na začátek](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Spustit více procesů v řešení VS, připojit k procesu, automaticky spustit proces v ladicím programu](../debugger/debug-multiple-processes.md#BKMK_Start_multiple_processes_in_a_VS_solution__attach_to_a_process__automatically_start_a_process_in_the_debugger)  
  
 ![Zpět na začátek](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Obsah](#BKMK_Contents)  
  
#### <a name="start-multiple-projects-in-a-solution"></a><a name="BKMK_Start_multiple_projects_in_a_solution"></a>Zahájení více projektů v řešení  
  
1. Vprůzkumníka řešení vyberte a v místní nabídce zvolte **Vlastnosti.**  
  
2. V dialogovém okně **Vlastnosti** vyberte **možnost Společné vlastnosti**, Projekt **po spuštění.**  
  
3. Pro každý projekt, který chcete změnit, zvolte buď **Start**, **Start bez ladění**, nebo **Žádný**.  
  
   ![Zpět na začátek](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Spustit více procesů v řešení VS, připojit k procesu, automaticky spustit proces v ladicím programu](../debugger/debug-multiple-processes.md#BKMK_Start_multiple_processes_in_a_VS_solution__attach_to_a_process__automatically_start_a_process_in_the_debugger)  
  
   ![Zpět na začátek](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Obsah](#BKMK_Contents)  
  
### <a name="attach-to-a-process"></a><a name="BKMK_Attach_to_a_process"></a>Připojení k procesu  
 Ladicí program lze také *připojit* k programům, které jsou spuštěny v procesech mimo visual studio, včetně programů, které jsou spuštěny na vzdáleném zařízení. Po připojení k programu můžete použít příkazy pro spuštění ladicího programu, zkontrolovat stav programu a tak dále. Vaše možnost kontrolovat program může být omezena, v závislosti na tom, zda byl program vytvořen s informacemi o ladění a zda máte přístup ke zdrojovému kódu programu a zda kompilátor JIT v běžném jazyce sleduje informace o ladění.  
  
 Další informace naleznete [v tématu Připojení ke spuštěné mši.](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)  
  
 **Připojení k procesu spuštěného v místním počítači**  
  
 Zvolte **Ladění**, **Připojit ke zpracování**. V dialogovém okně **Připojit k procesu** vyberte proces ze seznamu **Dostupné procesy** a pak zvolte **Připojit**.  
  
 ![Dialogové okno Připojit k procesu](../debugger/media/dbg-attachtoprocessdlg.png "DBG_AttachToProcessDlg")  
  
 ![Zpět na začátek](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Obsah](#BKMK_Contents)  
  
### <a name="automatically-start-a-process-in-the-debugger"></a><a name="BKMK_Automatically_start_an_process_in_the_debugger"></a>Automatické spuštění procesu v ladicím programu  
 Někdy může být nutné ladit spouštěcí kód programu, který je spuštěn jiným procesem. Příklady zahrnují služby a vlastní akce nastavení. V těchto scénářích můžete mít ladicí program spustit a automaticky připojit při spuštění aplikace.  
  
1. Spusťte Editor registru (**regedit.exe**).  
  
2. Přejděte do složky **HKEY_LOCAL_MACHINE\Software\Microsoft\Windows NT\CurrentVersion\Image File Execution Options.**  
  
3. Vyberte složku aplikace, kterou chcete spustit v ladicím programu.  
  
    Pokud název aplikace není uveden jako podřízená složka, vyberte **Možnosti spuštění souboru obrázku** a pak v místní nabídce zvolte **Nový**, **Klíč.** Vyberte novou klávesu, v místní nabídce zvolte **Přejmenovat** a zadejte název aplikace.  
  
4. V místní nabídce složky aplikace zvolte **Nový**, **Hodnota řetězce**.  
  
5. Změňte název nové hodnoty z `debugger`New **Value** na .  
  
6. V místní nabídce položky ladicího programu zvolte **Změnit**.  
  
7. V dialogovém okně Upravit `vsjitdebugger.exe` řetězec zadejte datové pole **Hodnota.**  
  
    ![Dialogové okno Upravit řetězec](../debugger/media/dbg-execution-automaticstart-editstringdlg.png "DBG_Execution_AutomaticStart_EditStringDlg")  
  
   ![Automatické zahájení ladicího programu v programu regedit.exe](../debugger/media/dbg-execution-automaticstart-result.png "DBG_Execution_AutomaticStart_Result")  
  
   ![Zpět na začátek](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Obsah](#BKMK_Contents)  
  
## <a name="switch-processes-break-and-continue-execution-step-through-source"></a><a name="BKMK_Switch_processes__break_and_continue_execution__step_through_source"></a>Přepínat procesy, přerušit a pokračovat v provádění, krokprocházet zdrojem  
  
- [Přepínání mezi procesy](#BKMK_Switch_between_processes) • [Příkazy break, step a continue](#BKMK_Break__step__and_continue_commands)  
  
### <a name="switch-between-processes"></a><a name="BKMK_Switch_between_processes"></a>Přepínání mezi procesy  
 Při ladění můžete připojit k více procesům, ale v ladicím programu je v daném okamžiku aktivní pouze jeden proces. Aktivní nebo *aktuální* proces můžete nastavit na panelu nástrojů Umístění ladění nebo v okně **Procesy.** Chcete-li přepínat mezi procesy, musí být oba procesy v režimu přerušení.  
  
 **Nastavení aktuálního procesu**  
  
- Na panelu nástrojů Umístění ladění zvolte **Proces,** chcete-li zobrazit seznam **Proces.** Vyberte proces, který chcete označit jako aktuální proces.  
  
   ![Přepínání mezi procesy](../debugger/media/dbg-execution-switchbetweenmodules.png "DBG_Execution_SwitchBetweenModules")  
  
   Pokud panel nástrojů **Umístění ladění** není viditelný, zvolte **Nástroje**, **Přizpůsobit**. Na kartě **Panely nástrojů** zvolte **Umístění ladění**.  
  
- Otevřete okno **Procesy** **(zkratka Ctrl+Alt+Z**), vyhledejte proces, který chcete nastavit jako aktuální proces, a poklepejte na něj.  
  
   ![Okno Procesy](../debugger/media/dbg-processeswindow.png "DBG_ProcessesWindow")  
  
   Aktuální proces je označen žlutou šipkou.  
  
  Přepnutí mů e-li do být zaměnit se za aktuální proces doladit účely. Všechny okno ladicího programu, které zobrazíte, zobrazí stav aktuálního procesu a všechny příkazy krokování ovlivní pouze aktuální proces.  
  
  ![Zpět na začátek](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [procesy přepínače, přerušení a pokračování provádění, krokování zdroje](../debugger/debug-multiple-processes.md#BKMK_Switch_processes__break_and_continue_execution__step_through_source)  
  
  ![Zpět na začátek](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Obsah](#BKMK_Contents)  
  
### <a name="break-step-and-continue-commands"></a><a name="BKMK_Break__step__and_continue_commands"></a>Příkazy pro přerušení, krok a pokračování  
  
> [!NOTE]
> Ve výchozím nastavení příkazy ladicího programu break, continue a step ovlivňují všechny procesy, které jsou laděny. Chcete-li toto chování změnit, přečtěte si téma [Konfigurace chování provádění více procesů.](#BKMK_Configure_the_execution_behavior_of_multiple_processes)  
  
||||  
|-|-|-|  
|**Příkaz**|**Přerušení všech procesů při přerušení jednoho procesu**<br /><br /> Zaškrtnuto (výchozí)|**Přerušení všech procesů při přerušení jednoho procesu**<br /><br /> Vymazány|  
|**Nabídka ladění:**<br /><br /> -   **Přerušit vše**|Všechny procesy se přeruší.|Všechny procesy se přeruší.|  
|**Nabídka ladění:**<br /><br /> -   **Pokračovat**|Všechny procesy pokračovat.|Všechny pozastavené procesy pokračují.|  
|**Nabídka ladění:**<br /><br /> -   **Krok do**<br />-   **Krok přes**<br />-   **Krok ven**|Všechny procesy jsou spuštěny v aktuálních krocích procesu.<br /><br /> Pak se všechny procesy přeruší.|Aktuální kroky procesu.<br /><br /> Pozastavené procesy pokračovat.<br /><br /> Spuštěné procesy pokračují.|  
|**Nabídka ladění:**<br /><br /> -   **Krok do aktuálního procesu**<br />-   **Krok přes aktuální proces**<br />-   **Krok out aktuální proces**|Není dostupné.|Aktuální kroky procesu.<br /><br /> Ostatní procesy zachovat jejich stávající stav (pozastaveno nebo spuštěno).|  
|Zdrojové okno<br /><br /> -   **Zarážka**|Všechny procesy se přeruší.|Pouze konce procesu zdrojového okna.|  
|Kontextová nabídka zdrojového okna:<br /><br /> -   **Spustit na kurzor**<br /><br /> Zdrojové okno musí být v aktuálním procesu.|Všechny procesy spustit, zatímco proces zdrojového okna běží na kurzor a potom přeruší.<br /><br /> Pak se všechny ostatní procesy přeruší.|Proces zdrojového okna běží na kurzor.<br /><br /> Ostatní procesy zachovat jejich stávající stav (pozastaveno nebo spuštěno).|  
|Kontextové menu okna **procesy:**<br /><br /> -   **Proces přerušení**|Není dostupné.|Vybrané konce procesu.<br /><br /> Ostatní procesy zachovat jejich stávající stav (pozastaveno nebo spuštěno).|  
|Kontextové menu okna **procesy:**<br /><br /> -   **Pokračovat v procesu**|Není dostupné.|Vybraný proces pokračuje.<br /><br /> Ostatní procesy zachovat jejich stávající stav (pozastaveno nebo spuštěno).|  
  
 ![Zpět na začátek](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [procesy přepínače, přerušení a pokračování provádění, krokování zdroje](../debugger/debug-multiple-processes.md#BKMK_Switch_processes__break_and_continue_execution__step_through_source)  
  
 ![Zpět na začátek](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Obsah](#BKMK_Contents)  
  
## <a name="stop-debugging-terminate-or-detach-from-processes"></a><a name="BKMK_Stop_debugging__terminate_or_detach_from_processes"></a>Zastavení ladění, ukončení nebo odpojení od procesů  
  
- [Příkazy Stop, terminate a detach](#BKMK_Stop__terminate__and_detach_commands)  
  
  Ve výchozím nastavení, pokud zvolíte **Ladění**, **Zastavit ladění,** když je v ladicím programu otevřeno více procesů, ladicí program ukončí nebo odpojí od všech procesů v závislosti na tom, jak byl proces otevřen v ladicím programu:  
  
- Pokud byl aktuální proces spuštěn v ladicím programu, je tento proces ukončen.  
  
- Pokud jste připojili ladicí program k aktuálnímu procesu, ladicí program se odpojí od procesu a ponechá proces spuštěný.  
  
  Pokud například spustíte ladění procesu z řešení sady Visual Studio, připojte se k jinému procesu, který je již spuštěn, a pak zvolte **Zastavit ladění**, relace ladění skončí, proces, který byl spuštěn v sadě Visual Studio, je ukončen, zatímco proces, který jste připojili, je ponechán spuštěn. Následující postupy můžete použít k řízení způsobu, jakým můžete zastavit ladění.  
  
> [!NOTE]
> **Přerušit všechny procesy, když jeden proces přeruší** možnost nemá vliv na zastavení ladění nebo ukončení a odpojení od procesů.  
  
 **Změna způsobu, jakým stop ladění ovlivňuje jednotlivé procesy**  
  
- Otevřete okno **Procesy** **(zkratka Ctrl+Alt+Z).** Zaškrtněte proces a potom zaškrtněte nebo zrušte zaškrtnutí **políčka Odpojit při ladění zastaveno.**  
  
### <a name="stop-terminate-and-detach-commands"></a><a name="BKMK_Stop__terminate__and_detach_commands"></a>Příkazy Stop, terminate a detach  
  
|||  
|-|-|  
|**Příkaz**|**Popis**|  
|**Nabídka ladění:**<br /><br /> -   **Zastavit ladění**|Pokud se chování nezmění **pomocí možnosti** **Odpojit** okno Procesy při ladění zarážky:<br /><br /> 1. Procesy zahájené ladicím programem jsou ukončeny.<br />2. Připojené procesy jsou odděleny od ladicího programu.|  
|**Nabídka ladění:**<br /><br /> -   **Ukončit vše**|Všechny procesy jsou ukončeny.|  
|**Nabídka ladění:**<br /><br /> -   **Odpojit vše**|Ladicí program se odpojí od všech procesů.|  
|Kontextové menu okna **procesy:**<br /><br /> -   **Proces odpojení**|Ladicí program se odpojí od vybraného procesu.<br /><br /> Ostatní procesy zachovat jejich stávající stav (pozastaveno nebo spuštěno).|  
|Kontextové menu okna **procesy:**<br /><br /> -   **Ukončit proces**|Vybraný proces je ukončen.<br /><br /> Ostatní procesy zachovat jejich stávající stav (pozastaveno nebo spuštěno).|  
|Kontextové menu okna **procesy:**<br /><br /> -   **Odpojení při zastavení ladění**|Přepíná chování **ladění**, **Zastavit ladění** pro vybraný proces:<br /><br /> - Zaškrtnuto: Ladicí program se odpojí od procesu.<br />- Vymazáno: Proces je ukončen.|  
  
 ![Zpět na začátek](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Zastavit ladění, ukončit nebo odpojit od procesů](../debugger/debug-multiple-processes.md#BKMK_Stop_debugging__terminate_or_detach_from_processes)  
  
 ![Zpět na začátek](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Obsah](#BKMK_Contents)  
  
## <a name="see-also"></a>Viz také  
 [Určení symbolu (.pdb) a zdrojových souborů](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)   
 [Připojit se ke spuštěné msti](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [Navigace v kódu pomocí ladicího programu](../debugger/navigating-through-code-with-the-debugger.md)   
 [Ladění just-in-time](../debugger/just-in-time-debugging-in-visual-studio.md)   
 [Ladění vícevláknových aplikací](../debugger/debug-multithreaded-applications-in-visual-studio.md)
