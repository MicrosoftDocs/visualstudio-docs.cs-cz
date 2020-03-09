---
title: Ladění více procesů | Microsoft Docs
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
ms.sourcegitcommit: 3154387056160bf4c36ac8717a7fdc0cd9faf3f9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2020
ms.locfileid: "78410440"
---
# <a name="debug-multiple-processes"></a>Ladění více procesů
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Zde je postup spuštění procesů ladění, přepínání mezi procesy, přerušení a pokračování v provádění, krokování prostřednictvím zdroje, zastavení ladění a ukončení nebo odpojení od procesů.  
  
## <a name="BKMK_Contents"></a>Obsah  
 [Konfigurace chování při provádění více procesů](#BKMK_Configure_the_execution_behavior_of_multiple_processes)  
  
 [Hledání zdrojových souborů a souborů symbolů (. pdb)](#BKMK_Find_the_source_and_symbol___pdb__files)  
  
 [Spuštění více procesů v řešení VS, připojení k procesu, automatické spuštění procesu v ladicím programu](#BKMK_Start_multiple_processes_in_a_VS_solution__attach_to_a_process__automatically_start_a_process_in_the_debugger)  
  
 [Přepínání procesů, přerušení a pokračování v provádění, krokování prostřednictvím zdroje](#BKMK_Switch_processes__break_and_continue_execution__step_through_source)  
  
 [Zastavení ladění, ukončení nebo odpojení od procesů](#BKMK_Stop_debugging__terminate_or_detach_from_processes)  
  
## <a name="BKMK_Configure_the_execution_behavior_of_multiple_processes"></a>Konfigurace chování při provádění více procesů  
 Ve výchozím nastavení, pokud je v ladicím programu spuštěno více procesů, mají příkazy pro přerušení, krokování a zastavení ladicího programu obvykle vliv na všechny procesy. Například když je jeden proces pozastaven na zarážce, spuštění všech ostatních procesů je také pozastaveno. Toto výchozí chování můžete změnit a získat větší kontrolu nad cíli příkazů provádění.  
  
1. V nabídce **ladění** vyberte **Možnosti a nastavení**.  
  
2. Na stránce **ladění**, **Obecné** zrušte zaškrtnutí políčka **přerušit všechny procesy při přerušení jednoho procesu** .  
  
   ![Zpět na obsah nejvyšší úrovně](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [](#BKMK_Contents)  
  
## <a name="BKMK_Find_the_source_and_symbol___pdb__files"></a>Hledání zdrojových souborů a souborů symbolů (. pdb)  
 Pro procházení zdrojového kódu procesu potřebuje ladicí program přístup ke zdrojovým souborům a souborům symbolů procesu. Viz [určení symbolu (. pdb) a zdrojových souborů](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).  
  
 Pokud nemůžete získat přístup k souborům pro určitý proces, můžete navigovat pomocí okna Disassemby. Viz [Postupy: použití okna](../debugger/how-to-use-the-disassembly-window.md) zpětného překladu  
  
 ![Zpět na obsah nejvyšší úrovně](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [](#BKMK_Contents)  
  
## <a name="BKMK_Start_multiple_processes_in_a_VS_solution__attach_to_a_process__automatically_start_a_process_in_the_debugger"></a>Spuštění více procesů v řešení VS, připojení k procesu, automatické spuštění procesu v ladicím programu  
  
- [Spuštění ladění více procesů v řešení aplikace Visual Studio](#BKMK_Start_debugging_multiple_processes_in_a_Visual_Studio_solution) • [Změna spouštěného projektu](#BKMK_Change_the_startup_project) • [spuštění konkrétního projektu v řešení](#BKMK_Start_a_specific_project_in_a_solution) • [spuštění více projektů v řešení • spustit více projektů v řešení](#BKMK_Start_multiple_projects_in_a_solution) • [připojit k procesu](#BKMK_Attach_to_a_process) • [automaticky spustit proces v ladicím programu](#BKMK_Automatically_start_an_process_in_the_debugger)  
  
> [!NOTE]
> Ladicí program se automaticky nepřipojí k podřízenému procesu, který je spuštěn laděným procesem, a to i v případě, že je podřízený projekt ve stejném řešení. Ladění podřízeného procesu:  
> 
> - Připojte se k podřízenému procesu po jeho spuštění.  
> 
>   -nebo-  
>   - Nakonfigurujte systém Windows tak, aby automaticky spouštěl podřízený proces v nové instanci ladicího programu.  
  
### <a name="BKMK_Start_debugging_multiple_processes_in_a_Visual_Studio_solution"></a>Spuštění ladění více procesů v řešení sady Visual Studio  
 Pokud máte více než jeden projekt v řešení sady Visual Studio, který může běžet nezávisle (projekty, které běží v samostatných procesech), můžete vybrat, které projekty bude ladicí program spuštěn.  
  
 ![Změna typu spuštění projektu](../debugger/media/dbg-execution-startmultipleprojects.png "DBG_Execution_StartMultipleProjects")  
  
#### <a name="BKMK_Change_the_startup_project"></a>Změna spouštěného projektu  
 Chcete-li změnit projekt po spuštění pro řešení, vyberte projekt v Průzkumník řešení a pak zvolte **nastavit jako projekt po spuštění** z kontextové nabídky.  
  
#### <a name="BKMK_Start_a_specific_project_in_a_solution"></a>Spuštění konkrétního projektu v řešení  
 Chcete-li spustit projekt pro řešení, aniž byste změnili výchozí spouštěný projekt, vyberte projekt v Průzkumník řešení a pak zvolte možnost **ladit** z kontextové nabídky. Pak můžete zvolit možnost **spustit novou instanci** nebo **Krokovat do nové instance**.  
  
 ![Zpět k hornímu](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [začátku více procesů v řešení VS, připojení k procesu, automatické spuštění procesu v ladicím programu](../debugger/debug-multiple-processes.md#BKMK_Start_multiple_processes_in_a_VS_solution__attach_to_a_process__automatically_start_a_process_in_the_debugger)  
  
 ![Zpět na obsah nejvyšší úrovně](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [](#BKMK_Contents)  
  
#### <a name="BKMK_Start_multiple_projects_in_a_solution"></a>Spuštění více projektů v řešení  
  
1. Vyberte řešení v Průzkumník řešení a potom v kontextové nabídce zvolte možnost **vlastnosti** .  
  
2. V dialogovém okně **vlastnosti** vyberte **společné vlastnosti**, **projekt po spuštění** .  
  
3. Pro každý projekt, který chcete změnit, vyberte možnost **Spustit**, **Spustit bez ladění**nebo **žádný**.  
  
   ![Zpět k hornímu](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [začátku více procesů v řešení VS, připojení k procesu, automatické spuštění procesu v ladicím programu](../debugger/debug-multiple-processes.md#BKMK_Start_multiple_processes_in_a_VS_solution__attach_to_a_process__automatically_start_a_process_in_the_debugger)  
  
   ![Zpět na obsah nejvyšší úrovně](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [](#BKMK_Contents)  
  
### <a name="BKMK_Attach_to_a_process"></a>Připojit k procesu  
 Ladicí program se také může *připojit* k programům, které jsou spuštěny v procesech mimo sadu Visual Studio, včetně programů, které jsou spuštěny na vzdáleném zařízení. Po připojení k programu můžete použít příkazy spuštění ladicího programu, kontrolovat stav programu a tak dále. Vaše schopnost kontrolovat program může být omezená, v závislosti na tom, zda byl program sestaven s ladicími informacemi a zda máte přístup ke zdrojovému kódu programu a zda kompilátor JIT CLR (Common Language Runtime) sleduje informace o ladění.  
  
 Další informace najdete v tématu [připojení ke spuštěným procesům](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md) .  
  
 **Připojte se k procesu, který běží na vašem místním počítači.**  
  
 Vyberte **ladit**, **připojit k procesu**. V dialogovém okně **připojit k procesu** vyberte proces v seznamu **procesy k dispozici** a pak zvolte možnost **připojit**.  
  
 ![Dialogové okno připojit k procesu](../debugger/media/dbg-attachtoprocessdlg.png "DBG_AttachToProcessDlg")  
  
 ![Zpět na obsah nejvyšší úrovně](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [](#BKMK_Contents)  
  
### <a name="BKMK_Automatically_start_an_process_in_the_debugger"></a>Automaticky spustit proces v ladicím programu  
 V některých případech může být nutné ladit spouštěcí kód pro program, který je spuštěn jiným procesem. Příklady zahrnují služby a akce vlastního nastavení. V těchto scénářích lze ladicí program spustit a automaticky připojit při spuštění aplikace.  
  
1. Spusťte Editor registru (**Regedit. exe**).  
  
2. Přejděte do složky **Možnosti spuštění souboru HKEY_LOCAL_MACHINE \Software\microsoft\windows NT\CurrentVersion\Image File Execution** .  
  
3. Vyberte složku aplikace, kterou chcete spustit v ladicím programu.  
  
    Pokud název aplikace není uveden jako podřízená složka, vyberte **možnost možnosti spuštění souboru bitové kopie** a v místní nabídce zvolte možnost **Nový**, **klíč** . Vyberte nový klíč, v místní nabídce zvolte **Přejmenovat** a pak zadejte název aplikace.  
  
4. V kontextové nabídce složky aplikace vyberte možnost **Nová**, **hodnota řetězce**.  
  
5. Změňte název nové hodnoty z **Nová hodnota** na `debugger`.  
  
6. V kontextové nabídce položky ladicího programu vyberte možnost **změnit**.  
  
7. V dialogovém okně Upravit řetězec zadejte do pole **Údaj hodnoty** `vsjitdebugger.exe`.  
  
    ![Dialogové okno Upravit řetězec](../debugger/media/dbg-execution-automaticstart-editstringdlg.png "DBG_Execution_AutomaticStart_EditStringDlg")  
  
   ![Automatické spuštění ladicího programu v regedit. exe](../debugger/media/dbg-execution-automaticstart-result.png "DBG_Execution_AutomaticStart_Result")  
  
   ![Zpět na obsah nejvyšší úrovně](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [](#BKMK_Contents)  
  
## <a name="BKMK_Switch_processes__break_and_continue_execution__step_through_source"></a>Přepínání procesů, přerušení a pokračování v provádění, krokování prostřednictvím zdroje  
  
- [Přepínání mezi procesy](#BKMK_Switch_between_processes) • [příkazy Break, Step a Continue](#BKMK_Break__step__and_continue_commands)  
  
### <a name="BKMK_Switch_between_processes"></a>Přepínání mezi procesy  
 Můžete se připojit k více procesům při ladění, ale v ladicím programu je v daném okamžiku aktivní pouze jeden proces. Aktivní nebo *aktuální* proces můžete nastavit na panelu nástrojů umístění ladění nebo v okně **procesy** . Chcete-li přepínat mezi procesy, musí být oba procesy v režimu pozastavení.  
  
 **Nastavení aktuálního procesu**  
  
- Na panelu nástrojů umístění ladění vyberte možnost **proces** , aby se zobrazilo pole se seznamem **procesů** . Vyberte proces, který chcete nastavit jako aktuální proces.  
  
   ![Přepínání mezi procesy](../debugger/media/dbg-execution-switchbetweenmodules.png "DBG_Execution_SwitchBetweenModules")  
  
   Pokud panel nástrojů **umístění ladění** není zobrazený, vyberte **nástroje**, **přizpůsobit**. Na kartě **panely nástrojů** vyberte **umístění ladění**.  
  
- Otevřete okno **procesy** (Klávesová zkratka **CTRL + ALT + Z**), najděte proces, který chcete nastavit jako aktuální proces, a dvakrát na něj klikněte.  
  
   ![Okno procesů](../debugger/media/dbg-processeswindow.png "DBG_ProcessesWindow")  
  
   Aktuální proces je označen žlutou šipkou.  
  
  Přepnutí na projekt nastaví aktuální proces pro účely ladění. Jakékoli okno ladicího programu, které zobrazíte, zobrazí stav aktuálního procesu a všechny příkazy krokování budou mít vliv pouze na aktuální proces.  
  
  ![Zpět na Hlavní](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [přepínání procesů, přerušení a pokračování v provádění, krokování prostřednictvím zdroje](../debugger/debug-multiple-processes.md#BKMK_Switch_processes__break_and_continue_execution__step_through_source)  
  
  ![Zpět na obsah nejvyšší úrovně](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [](#BKMK_Contents)  
  
### <a name="BKMK_Break__step__and_continue_commands"></a>Příkazy Break, Step a Continue  
  
> [!NOTE]
> Ve výchozím nastavení mají příkazy Break, Continue a Step Debugger vliv na všechny procesy, které jsou právě laděny. Chcete-li toto chování změnit, přečtěte si téma [Konfigurace chování při provádění více procesů](#BKMK_Configure_the_execution_behavior_of_multiple_processes) .  
  
||||  
|-|-|-|  
|**Příkaz**|**Přerušit všechny procesy při přerušení jednoho procesu**<br /><br /> Zaškrtnuto (výchozí)|**Přerušit všechny procesy při přerušení jednoho procesu**<br /><br /> Vymazat|  
|Nabídka **ladění** :<br /><br /> -   **přerušit vše**|Všechny procesy jsou přerušeny.|Všechny procesy jsou přerušeny.|  
|Nabídka **ladění** :<br /><br /> -   **pokračovat**|Obnoví se všechny procesy.|Obnoví se všechny pozastavené procesy.|  
|Nabídka **ladění** :<br /><br /> -   **Krokovat do**<br />-   **Krokovat**<br />-   **Krokovat**|Všechny procesy jsou spuštěny během aktuálních kroků procesu.<br /><br /> Pak budou přerušeny všechny procesy.|Aktuální kroky procesu.<br /><br /> Pozastavené procesy budou obnoveny.<br /><br /> Spuštěné procesy pokračují.|  
|Nabídka **ladění** :<br /><br /> -   **Krok do aktuálního procesu**<br />-   **Krokovat s aktuálním procesem**<br />-   **Krok ven z aktuálního procesu**|neuvedeno|Aktuální kroky procesu.<br /><br /> Jiné procesy udržují svůj stávající stav (pozastaveno nebo spuštěno).|  
|Okno zdroje<br /><br /> -   **zarážku**|Všechny procesy jsou přerušeny.|Je rozdělen pouze proces zdrojového okna.|  
|Místní nabídka zdrojového okna:<br /><br /> -   **Spustit ke kurzoru**<br /><br /> Zdrojové okno musí být v aktuálním procesu.|Všechny procesy jsou spuštěny během spuštění procesu zdrojového okna do kurzoru a poté jsou přerozděleny.<br /><br /> Pak všechny ostatní procesy přeruší.|Proces zdrojového okna se spouští do kurzoru.<br /><br /> Jiné procesy udržují svůj stávající stav (pozastaveno nebo spuštěno).|  
|Místní nabídka okna **procesy** :<br /><br /> **proces přerušení** -   |neuvedeno|Přerušení vybraného procesu.<br /><br /> Jiné procesy udržují svůj stávající stav (pozastaveno nebo spuštěno).|  
|Místní nabídka okna **procesy** :<br /><br /> **pokračovat v procesu** -   |neuvedeno|Vybraný proces pokračuje.<br /><br /> Jiné procesy udržují svůj stávající stav (pozastaveno nebo spuštěno).|  
  
 ![Zpět na Hlavní](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [přepínání procesů, přerušení a pokračování v provádění, krokování prostřednictvím zdroje](../debugger/debug-multiple-processes.md#BKMK_Switch_processes__break_and_continue_execution__step_through_source)  
  
 ![Zpět na obsah nejvyšší úrovně](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [](#BKMK_Contents)  
  
## <a name="BKMK_Stop_debugging__terminate_or_detach_from_processes"></a>Zastavení ladění, ukončení nebo odpojení od procesů  
  
- [Příkazy zastavit, ukončit a odpojit](#BKMK_Stop__terminate__and_detach_commands)  
  
  Ve výchozím nastavení, když zvolíte možnost **ladění**, **Zastavit ladění** , pokud je v ladicím programu otevřeno více procesů, ladicí program se ukončí nebo odpojí od všech procesů v závislosti na tom, jak byl proces otevřen v ladicím programu:  
  
- Pokud byl aktuální proces spuštěn v ladicím programu, tento proces je ukončen.  
  
- Pokud jste ladicí program připojili k aktuálnímu procesu, ladicí program se odpojí z procesu a ponechá proces spuštěný.  
  
  Například pokud začnete ladit proces z řešení sady Visual Studio, připojíte se k jinému procesu, který je již spuštěn, a poté zvolíte možnost **Zastavit ladění**, relace ladění skončí, proces, který byl spuštěn v aplikaci Visual Studio, bude ukončen, zatímco proces, který jste připojili, zůstane spuštěný. Následující postupy můžete použít k řízení způsobu, jakým zastavíte ladění.  
  
> [!NOTE]
> Možnost **přerušit všechny procesy, když jeden proces přeruší** , neovlivní zastavení ladění nebo ukončení a odpojení od procesů.  
  
 **Změna způsobu, jakým má funkce zastavit ladění vliv na jednotlivé procesy**  
  
- Otevřete okno **procesy** (Klávesová zkratka **CTRL + ALT + Z**). Vyberte proces a zaškrtněte nebo zrušte zaškrtnutí políčka **Odpojit při zastavení ladění** .  
  
### <a name="BKMK_Stop__terminate__and_detach_commands"></a>Příkazy zastavit, ukončit a odpojit  
  
|||  
|-|-|  
|**Příkaz**|**Popis**|  
|Nabídka **ladění** :<br /><br /> -   **Zastavit ladění**|Pokud se chování nezmění pomocí okna procesy **Odpojit při zastavení ladění** :<br /><br /> 1. procesy spuštěné pomocí ladicího programu jsou ukončeny.<br />2. připojené procesy se odpojí z ladicího programu.|  
|Nabídka **ladění** :<br /><br /> -   **Ukončit vše**|Všechny procesy jsou ukončeny.|  
|Nabídka **ladění** :<br /><br /> -   **Odpojit vše**|Ladicí program se odpojí ze všech procesů.|  
|Místní nabídka okna **procesy** :<br /><br /> -   **proces odpojení**|Ladicí program se odpojí od vybraného procesu.<br /><br /> Jiné procesy udržují svůj stávající stav (pozastaveno nebo spuštěno).|  
|Místní nabídka okna **procesy** :<br /><br /> **Ukončit proces** -   |Vybraný proces je ukončen.<br /><br /> Jiné procesy udržují svůj stávající stav (pozastaveno nebo spuštěno).|  
|Místní nabídka okna **procesy** :<br /><br /> -   **Odpojit při zastavení ladění**|Přepne chování **ladění**, **zastaví ladění** pro vybraný proces:<br /><br /> -Zaškrtnuto: ladicí program se odpojí od procesu.<br />-Smazáno: proces je ukončen.|  
  
 ![Zpět na začátek](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [ladění, ukončení nebo odpojení od procesů](../debugger/debug-multiple-processes.md#BKMK_Stop_debugging__terminate_or_detach_from_processes)  
  
 ![Zpět na obsah nejvyšší úrovně](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [](#BKMK_Contents)  
  
## <a name="see-also"></a>Viz také  
 [Zadejte symbol (PDB) a zdrojové soubory](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)   
 [Připojit ke spuštěným procesům](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [Procházení kódu pomocí ladicího programu](../debugger/navigating-through-code-with-the-debugger.md)   
   [ladění za běhu](../debugger/just-in-time-debugging-in-visual-studio.md)  
 [Ladění vícevláknových aplikací](../debugger/debug-multithreaded-applications-in-visual-studio.md)
