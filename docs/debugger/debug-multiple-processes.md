---
title: Ladění více procesů | Microsoft Docs
description: Ladění více procesů v aplikaci Visual Studio. Spuštění a přepínání mezi procesy, přerušení, pokračování, krokování zdroje a ukončení nebo odpojení od jednotlivých procesů.
ms.custom: SEO-VS-2020
ms.date: 11/20/2018
ms.topic: how-to
f1_keywords:
- vs.debug.programs
- vs.debug.processes.attaching
- vs.debug.activeprogram
- vs.debug.attaching
- vs.debug.attachedprocesses
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: bde37134-66af-4273-b02e-05b3370c31ab
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: fdb86d0c0140c7d0c30b3a56fbf875215d1e626e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99873281"
---
# <a name="debug-multiple-processes-c-visual-basic-c"></a>Ladění více procesů (C#, Visual Basic, C++)

Visual Studio může ladit řešení, které má několik procesů. Můžete spouštět a přepínat mezi procesy, přerušit, pokračovat a krokovat se zdrojem, zastavit ladění a ukončit nebo odpojit od jednotlivých procesů.

## <a name="start-debugging-with-multiple-processes"></a>Spustit ladění s více procesy

V případě, že více než jeden projekt v řešení sady Visual Studio může běžet nezávisle, můžete vybrat projekt, který ladicí program spustí. Aktuální spouštěcí projekt se zobrazí tučně v **Průzkumník řešení**.

Chcete-li změnit projekt po spuštění, klikněte v **Průzkumník řešení** pravým tlačítkem myši na jiný projekt a vyberte **nastavit jako spouštěný projekt**.

Chcete-li spustit ladění projektu z **Průzkumník řešení** bez jeho spuštění, klikněte pravým tlačítkem myši na projekt a vyberte možnost **ladit**  >  **spustit novou instanci** nebo **Krok do nové instance**.

**Nastavení spouštěného projektu nebo více projektů z vlastností řešení:**

1. Vyberte řešení v **Průzkumník řešení** a pak na panelu nástrojů vyberte ikonu **vlastnosti** , nebo klikněte pravým tlačítkem na řešení a vyberte **vlastnosti**.

1. Na stránce **vlastnosti** vyberte **společné vlastnosti**  >  **spouštěný projekt**.

   ![Změna typu spuštění projektu](../debugger/media/dbg_execution_startmultipleprojects.png "DBG_Execution_StartMultipleProjects")

1. Vyberte možnost **aktuální výběr**, **jeden spouštěný projekt** a soubor projektu nebo **více projektů po spuštění**.

   Pokud vyberete **více projektů po spuštění**, můžete změnit pořadí spouštění a akci, která má být provedena pro každý projekt **: spustit**, **Spustit bez ladění** nebo **žádný**.

1. Chcete-li použít a zavřít dialogové okno, vyberte **použít**, nebo **OK** .

### <a name="attach-to-a-process"></a><a name="BKMK_Attach_to_a_process"></a> Připojit k procesu

Ladicí program se může také *připojit* k aplikacím běžícím v procesech mimo sadu Visual Studio, včetně na vzdálených zařízeních. Po připojení k aplikaci můžete použít ladicí program sady Visual Studio. Funkce ladění můžou být omezené. Závisí na tom, zda byla aplikace sestavena s ladicími informacemi, zda máte přístup ke zdrojovému kódu aplikace a zda kompilátor JIT sleduje informace o ladění.

Další informace najdete v tématu [připojení ke spuštěným procesům](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).

**Připojení ke spuštěnému procesu:**

1. Když je aplikace spuštěná, vyberte **ladit**  >  **připojit k procesu**.

   ![Dialogové okno připojit k procesu](../debugger/media/dbg_attachtoprocessdlg.png "Dialogové okno připojit k procesu")

1. V dialogovém okně **připojit k procesu** vyberte proces v seznamu **procesy k dispozici** a pak vyberte **připojit**.

>[!NOTE]
>Ladicí program se automaticky nepřipojí k podřízenému procesu, který je spuštěn laděným procesem, a to i v případě, že je podřízený projekt ve stejném řešení. Chcete-li ladit podřízený proces, buď se připojte k podřízenému procesu po jeho spuštění, nebo nakonfigurujte Editor registru systému Windows pro spuštění podřízeného procesu v nové instanci ladicího programu.

### <a name="use-the-registry-editor-to-automatically-start-a-process-in-the-debugger"></a><a name="BKMK_Automatically_start_an_process_in_the_debugger"></a> Použití Editoru registru k automatickému spuštění procesu v ladicím programu

V některých případech může být nutné ladit spouštěcí kód aplikace, kterou spouští jiný proces. Příklady zahrnují služby a akce vlastního nastavení. Je možné, že se ladicí program spustí a automaticky se připojí k aplikaci.

1. Spuštěním *regedit.exe* spusťte Editor registru Windows.

1. V editoru registru přejděte na **HKEY_LOCAL_MACHINE\Software\Microsoft\Windows NT\CurrentVersion\Image File Execution Options**.

1. Vyberte složku aplikace, kterou chcete spustit v ladicím programu.

   Pokud aplikace není uvedená jako podřízená složka, klikněte pravým tlačítkem myši na možnost **spuštění souboru bitové kopie**, vyberte možnost **Nový**  >  **klíč** a zadejte název aplikace. Nebo klikněte pravým tlačítkem na nový klíč ve stromu, vyberte **Přejmenovat** a pak zadejte název aplikace.

1. Klikněte pravým tlačítkem na nový klíč ve stromu a vyberte možnost **Nová**  >  **hodnota řetězce**.

1. Změňte název nové hodnoty z **nové hodnoty #1** na `debugger` .

1. Klikněte pravým tlačítkem na **ladicí program** a vyberte **změnit**.

   ![Dialogové okno Upravit řetězec](../debugger/media/dbg_execution_automaticstart_editstringdlg.png "Dialogové okno Upravit řetězec")

1. V dialogovém okně **Upravit řetězec** zadejte `vsjitdebugger.exe` do pole **Údaj hodnoty** a pak vyberte **OK**.

   ![Automatické spuštění ladicího programu v regedit.exe](../debugger/media/dbg_execution_automaticstart_result.png "Automatické spuštění ladicího programu v regedit.exe")

## <a name="debug-with-multiple-processes"></a><a name="BKMK_Switch_processes__break_and_continue_execution__step_through_source"></a> Ladění pomocí více procesů
<a name="BKMK_Configure_the_execution_behavior_of_multiple_processes"></a>

Při ladění aplikace s několika procesy ovlivní příkazy pro přerušení, krokování a pokračování ladicího programu všechny procesy ve výchozím nastavení. Například když je proces pozastaven na zarážce, spuštění všech ostatních procesů je také pozastaveno. Toto výchozí chování můžete změnit, pokud chcete získat větší kontrolu nad cíli příkazů provádění.

**Chcete-li změnit, zda jsou všechny procesy při přerušení jednoho procesu pozastaveny:**

- V části **nástroje** (nebo **ladění**) > **Možnosti**  >  **ladění**  >  **obecně** zaškrtněte nebo zrušte zaškrtnutí políčka **přerušit všechny procesy při přerušení jednoho procesu** .

### <a name="break-step-and-continue-commands"></a><a name="BKMK_Break__step__and_continue_commands"></a> Příkazy Break, Step a Continue

Následující tabulka popisuje chování příkazů ladění v případě, že je zaškrtnuté políčko **přerušit všechny procesy při přerušení jednoho procesu** :

|**Příkaz**|Vybráno|Zrušení výběru|
|-|-|-|
|**Ladit**   >  **Přerušit vše**|Všechny procesy jsou přerušeny.|Všechny procesy jsou přerušeny.|
|**Ladit**  >  **Pokračovat**|Obnoví se všechny procesy.|Obnoví se všechny pozastavené procesy.|
|**Ladit**  >  **Krok dovnitř**, **krokování** nebo **krokování**|Všechny procesy jsou spuštěny během aktuálních kroků procesu. <br />Pak budou přerušeny všechny procesy.|Aktuální kroky procesu. <br />Pozastavené procesy budou obnoveny. <br />Spuštěné procesy pokračují.|
|**Ladit**  >  **Krokovat do aktuálního procesu**, **Krokovat** s aktuálním procesem nebo **Krokovat aktuální proces**|–|Aktuální kroky procesu.<br />Jiné procesy udržují svůj stávající stav (pozastaveno nebo spuštěno).|
|Zarážka  zdrojového okna|Všechny procesy jsou přerušeny.|Je rozdělen pouze proces zdrojového okna.|
|Okno zdrojového kódu **se spustí se kurzorem**<br />Zdrojové okno musí být v aktuálním procesu.|Všechny procesy jsou spuštěny během spuštění procesu zdrojového okna do kurzoru a poté jsou přerozděleny.<br />Pak všechny ostatní procesy přeruší.|Proces zdrojového okna se spouští do kurzoru.<br />Jiné procesy udržují svůj stávající stav (pozastaveno nebo spuštěno).|
|**Proces přerušení** okna > **procesů**|–|Přerušení vybraného procesu.<br />Jiné procesy udržují svůj stávající stav (pozastaveno nebo spuštěno).|
|Okno **procesů** > **pokračovat v procesu**|–|Vybraný proces pokračuje.<br />Jiné procesy udržují svůj stávající stav (pozastaveno nebo spuštěno).|

### <a name="find-the-source-and-symbol-pdb-files"></a><a name="BKMK_Find_the_source_and_symbol___pdb__files"></a> Hledání zdrojových souborů a souborů symbolů (. pdb)
Pro procházení zdrojového kódu procesu potřebuje ladicí program přístup ke svým zdrojovým souborům a souborům symbolů. Další informace naleznete v tématu [určení symbolu (. pdb) a zdrojových souborů](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

Pokud nemůžete získat přístup k souborům pro určitý proces, můžete navigovat pomocí okna **zpětný překlad** . Další informace naleznete v tématu [How to: Use a reassembly Window](../debugger/how-to-use-the-disassembly-window.md).

### <a name="switch-between-processes"></a><a name="BKMK_Switch_between_processes"></a> Přepínání mezi procesy

Můžete se připojit k více procesům při ladění, ale v ladicím programu je v daném okamžiku aktivní pouze jeden proces. Můžete nastavit aktivní nebo *aktuální* proces na panelu nástrojů **umístění ladění** nebo v okně **procesy** . Chcete-li přepínat mezi procesy, musí být oba procesy v režimu pozastavení.

**Nastavení aktuálního procesu z panelu nástrojů umístění ladění:**

1. Chcete-li otevřít panel nástrojů **umístění ladění** , vyberte možnost **Zobrazit**  >  **panely nástrojů**  >  **umístění ladění**.

1. Během ladění na panelu nástrojů **umístění ladění** vyberte proces, který chcete nastavit jako aktuální proces z rozevíracího seznamu **proces** .

   ![Přepínání mezi procesy](../debugger/media/dbg_execution_switchbetweenmodules.png "DBG_Execution_SwitchBetweenModules")

**Nastavení aktuálního procesu z okna procesy:**

1. Chcete-li otevřít okno **procesy** , při ladění vyberte možnost **ladit**  >  **procesy systému Windows**  >  .

1. V okně **procesy** je aktuální proces označen žlutou šipkou. Dvakrát klikněte na proces, který chcete nastavit jako aktuální proces.

   ![Okno procesů](../debugger/media/dbg_processeswindow.png "DBG_ProcessesWindow")

Přepnutí na proces nastaví jako aktuální proces pro účely ladění. Okna ladicího programu zobrazují stav aktuálního procesu a příkazy krokování ovlivňují pouze aktuální proces.

## <a name="stop-debugging-with-multiple-processes"></a>Zastavit ladění s více procesy

Ve výchozím nastavení, když vyberete **ladění**  >  **Zastavit ladění**, ladicí program ukončí nebo odpojí všechny procesy.

- Pokud byl aktuální proces spuštěn v ladicím programu, proces je ukončen.

- Pokud jste ladicí program připojili k aktuálnímu procesu, ladicí program se odpojí z procesu a ponechá proces spuštěný.

Pokud spustíte ladění procesu z řešení sady Visual Studio, pak se připojte k jinému procesu, který je již spuštěn, a poté zvolte možnost **Zastavit ladění**, relace ladění skončí. Proces, který byl spuštěn v aplikaci Visual Studio, končí, zatímco proces, který jste připojili, zůstane spuštěný.

Chcete-li řídit způsob, jakým **zastaví ladění** vliv na jednotlivé procesy, klikněte v okně **procesy** pravým tlačítkem myši na proces a potom zaškrtněte nebo zrušte zaškrtnutí políčka **Odpojit při zastavení ladění** .

>[!NOTE]
>Možnost **přerušit všechny procesy, když jeden proces přeruší** ladicí program, nemá vliv na zastavení, ukončení nebo odpojení od procesů.

### <a name="stop-terminate-and-detach-commands"></a>Příkazy zastavit, ukončit a odpojit

Následující tabulka popisuje chování ladicího programu zastavit, ukončit a odpojit příkazy s více procesy:

|**Příkaz**|**Popis**|
|-|-|
|**Ladit**  >  **Zastavit ladění**|Pokud se v okně **procesy** nezmění chování, procesy spouštěné ladicím programem se ukončí a připojené procesy se odpojí.|
|**Ladit**  >  **Ukončit vše**|Všechny procesy jsou ukončeny.|
|**Ladit**  >  **Odpojit vše**|Ladicí program se odpojí ze všech procesů.|
|Okno **procesů** > **odpojení procesu**|Ladicí program se odpojí od vybraného procesu.<br />Jiné procesy udržují svůj stávající stav (pozastaveno nebo spuštěno).|
|Okno **procesů** > **ukončení procesu**|Vybraný proces je ukončen.<br />Jiné procesy udržují svůj stávající stav (pozastaveno nebo spuštěno).|
|Okno **procesy** > **Odpojit při zastavení ladění**|Pokud je toto políčko zaškrtnuté, **ladění**  >  **ukončí ladění** odpojí od vybraného procesu. <br />Pokud není vybraná, **ladění**  >  **zastaví ladění** ukončí vybraný proces. |

## <a name="see-also"></a>Viz také

- [Zadat symbol (PDB) a zdrojové soubory](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)
- [Připojit ke spuštěným procesům](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)
- [Navigace v kódu pomocí ladicího programu](../debugger/navigating-through-code-with-the-debugger.md)
- [Ladění za běhu](../debugger/just-in-time-debugging-in-visual-studio.md)
- [Ladění vícevláknových aplikací](../debugger/debug-multithreaded-applications-in-visual-studio.md)