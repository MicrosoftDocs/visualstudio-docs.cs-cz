---
title: Ladění více procesů | Dokumenty společnosti Microsoft
ms.date: 11/20/2018
ms.topic: conceptual
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 160e219b6fc2ab314f8d0dd91043c18101f2c3a5
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/13/2020
ms.locfileid: "79302222"
---
# <a name="debug-multiple-processes-c-visual-basic-c"></a>Ladění více procesů (C#, Visual Basic, C++)

Visual Studio můžete ladit řešení, které má několik procesů. Můžete spustit a přepínat mezi procesy, přerušit, pokračovat a krokovat zdroj, zastavit ladění a ukončit nebo odpojit od jednotlivých procesů.

## <a name="start-debugging-with-multiple-processes"></a>Zahájení ladění s více procesy

Pokud více než jeden projekt v řešení sady Visual Studio lze spustit nezávisle, můžete vybrat, který projekt ladicí program spustí. Aktuální projekt spuštění se zobrazí tučně v **Průzkumníku řešení**.

Chcete-li změnit projekt při spuštění, klepněte v **Průzkumníku řešení**pravým tlačítkem myši na jiný projekt a vyberte příkaz **Nastavit jako počáteční projekt**.

Chcete-li spustit ladění projektu z **Průzkumníka řešení,** aniž byste jej učinili projektem při spuštění, klepněte pravým tlačítkem myši na projekt a vyberte **možnost Ladění** > **spustit novou instanci** nebo Krok do nové **instance**.

**Nastavení spouštěcího projektu nebo více projektů z vlastností řešení:**

1. Vyberte řešení v **Průzkumníku řešení** a pak vyberte ikonu **Vlastnosti** na panelu nástrojů nebo klepněte pravým tlačítkem myši na řešení a vyberte **vlastnosti**.

1. Na stránce **Vlastnosti** vyberte **projekt spuštění běžných vlastností** > **Startup Project**.

   ![Změna typu spuštění projektu](../debugger/media/dbg_execution_startmultipleprojects.png "DBG_Execution_StartMultipleProjects")

1. Vyberte **možnost Aktuální výběr**, Jeden spouštěcí **projekt** a soubor projektu nebo Více projektů **po spuštění**.

   Pokud vyberete **více projektů při spuštění**, můžete změnit pořadí spuštění a akci pro každý projekt: **Start**, Start **bez ladění**nebo **Žádný**.

1. Vyberte **Použít**nebo **OK,** chcete-li použít a zavřít dialogové okno.

### <a name="attach-to-a-process"></a><a name="BKMK_Attach_to_a_process"></a>Připojení k procesu

Ladicí program se může *připojit* také k aplikacím spuštěných v procesech mimo Visual Studio, včetně vzdálených zařízení. Po připojení k aplikaci můžete použít ladicí program Visual Studia. Funkce ladění mohou být omezené. Záleží na tom, zda byla aplikace vytvořena s informacemi o ladění, zda máte přístup ke zdrojovému kódu aplikace a zda kompilátor JIT sleduje informace o ladění.

Další informace naleznete v [tématu Připojení ke spuštěné msti .](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)

**Připojení ke spuštěnému procesu:**

1. Když je aplikace spuštěná, vyberte **Debug** > **Attach to Process**.

   ![Dialogové okno Připojit k procesu](../debugger/media/dbg_attachtoprocessdlg.png "Dialogové okno Připojit k procesu")

1. V dialogovém okně **Připojit k procesu** vyberte proces ze seznamu **Dostupné procesy** a pak vyberte **Připojit**.

>[!NOTE]
>Ladicí program se automaticky nepřipojí k podřízenému procesu, který je spuštěn laděným procesem, a to i v případě, že podřízený projekt je ve stejném řešení. Chcete-li ladit podřízený proces, buď připojit k podřízenému procesu po jeho spuštění, nebo nakonfigurovat Editor registru systému Windows spustit podřízený proces v nové instanci ladicího programu.

### <a name="use-the-registry-editor-to-automatically-start-a-process-in-the-debugger"></a><a name="BKMK_Automatically_start_an_process_in_the_debugger"></a>Automatické spuštění procesu v ladicím programu pomocí Editoru registru

Někdy může být nutné ladit spouštěcí kód pro aplikaci, která je spuštěna jiným procesem. Příklady zahrnují služby a vlastní akce nastavení. Můžete mít ladicí program spustit a automaticky připojit k aplikaci.

1. Spusťte Editor registru systému Windows spuštěním *programu regedit.exe*.

1. V Editoru registru přejděte na **HKEY_LOCAL_MACHINE\Software\Microsoft\Windows NT\CurrentVersion\Image File Execution Options**.

1. Vyberte složku aplikace, kterou chcete spustit v ladicím programu.

   Pokud aplikace není uvedena jako podřízená složka, klikněte pravým tlačítkem na **Možnostspuštění souboru obrázku**, vyberte **Nový** > **klíč**a zadejte název aplikace. Nebo klikněte pravým tlačítkem myši na nový klíč ve stromu, vyberte **Přejmenovat**a zadejte název aplikace.

1. Klepněte pravým tlačítkem myši na nový klíč ve stromu a vyberte **nový** > **řetězec hodnotu**.

1. Změňte název nové hodnoty z nové `debugger`hodnoty **#1** na .

1. Klepněte pravým tlačítkem myši na **ladicí program** a vyberte **příkaz Změnit**.

   ![Dialogové okno Upravit řetězec](../debugger/media/dbg_execution_automaticstart_editstringdlg.png "Dialogové okno Upravit řetězec")

1. V dialogovém okně Upravit `vsjitdebugger.exe` **řetězec** zadejte datové pole **Hodnota** a pak vyberte **OK**.

   ![Automatické zahájení ladicího programu v programu regedit.exe](../debugger/media/dbg_execution_automaticstart_result.png "Automatické zahájení ladicího programu v programu regedit.exe")

## <a name="debug-with-multiple-processes"></a><a name="BKMK_Switch_processes__break_and_continue_execution__step_through_source"></a>Ladění s více procesy
<a name="BKMK_Configure_the_execution_behavior_of_multiple_processes"></a>

Při ladění aplikace s několika procesy, lámání, krokování a pokračující ladicí příkazy ovlivňují všechny procesy ve výchozím nastavení. Například při pozastavení procesu na zarážku, provádění všech ostatních procesů je také pozastavena. Toto výchozí chování můžete změnit, chcete-li získat větší kontrolu nad cíli příkazů provádění.

**Chcete-li změnit, zda jsou všechny procesy pozastaveny při přerušení jednoho procesu:**

- V **části Nástroje** (nebo **Ladění)**> **Možnosti** > **ladění** > **obecné**, zaškrtněte nebo zrušte **zaškrtnutí políčka Přerušit všechny procesy při přerušení jednoho procesu.**

### <a name="break-step-and-continue-commands"></a><a name="BKMK_Break__step__and_continue_commands"></a>Příkazy pro přerušení, krok a pokračování

Následující tabulka popisuje chování ladicích příkazů, když je zaškrtnuto nebo zaškrtnuto políčko **Přerušit všechny procesy, když** je jeden proces přerušit nebo zrušit:

|**Příkaz**|Vybráno|Odznačeno|
|-|-|-|
|**Ladění**  > **zalomení všech**|Všechny procesy se přeruší.|Všechny procesy se přeruší.|
|**Ladění** > **pokračovat**|Všechny procesy pokračovat.|Všechny pozastavené procesy pokračují.|
|**Ladění** > **kroku do**, krok **přes**, nebo krok **ven**|Všechny procesy jsou spuštěny v aktuálních krocích procesu. <br />Pak se všechny procesy přeruší.|Aktuální kroky procesu. <br />Pozastavené procesy pokračovat. <br />Spuštěné procesy pokračují.|
|**Ladění kroku** > **do aktuálního procesu**, **krok přes aktuální proces**nebo krok ven aktuální **proces**|Není dostupné.|Aktuální kroky procesu.<br />Ostatní procesy zachovat jejich stávající stav (pozastaveno nebo spuštěno).|
|**Zakácení** zdrojového okna|Všechny procesy se přeruší.|Pouze konce procesu zdrojového okna.|
|Zdrojové okno **Spustit kurzorem**<br />Zdrojové okno musí být v aktuálním procesu.|Všechny procesy spustit, zatímco proces zdrojového okna běží na kurzor a potom přeruší.<br />Pak se všechny ostatní procesy přeruší.|Proces zdrojového okna běží na kurzor.<br />Ostatní procesy zachovat jejich stávající stav (pozastaveno nebo spuštěno).|
|**Okno proces ulomení procesu** **> procesu procesu procesu procesu**|Není dostupné.|Vybrané konce procesu.<br />Ostatní procesy zachovat jejich stávající stav (pozastaveno nebo spuštěno).|
|**Okno procesy** > **Pokračovat v procesu**|Není dostupné.|Vybraný proces pokračuje.<br />Ostatní procesy zachovat jejich stávající stav (pozastaveno nebo spuštěno).|

### <a name="find-the-source-and-symbol-pdb-files"></a><a name="BKMK_Find_the_source_and_symbol___pdb__files"></a>Vyhledání zdrojových a symbolových souborů (.pdb)
K navigaci ve zdrojovém kódu procesu potřebuje ladicí program přístup ke svým zdrojovým souborům a souborům symbolů. Další informace naleznete [v tématu Specify symbol (.pdb) a zdrojové soubory](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

Pokud nemáte přístup k souborům pro proces, můžete přejít pomocí okna **Demontáž.** Další informace naleznete v [tématu Postup: Použití okna Demontáže](../debugger/how-to-use-the-disassembly-window.md).

### <a name="switch-between-processes"></a><a name="BKMK_Switch_between_processes"></a>Přepínání mezi procesy

Při ladění se můžete připojit k více procesům, ale v ladicím programu je v daném okamžiku aktivní pouze jeden proces. Aktivní nebo *aktuální* proces můžete nastavit na panelu nástrojů **Umístění ladění** nebo v okně **Procesy.** Chcete-li přepínat mezi procesy, musí být oba procesy v režimu přerušení.

**Postup nastavení aktuálního procesu z panelu nástrojů Umístění ladění:**

1. Chcete-li otevřít panel nástrojů **Umístění ladění,** vyberte **možnost Zobrazit** > **panely nástrojů** > **ladění umístění**.

1. Během ladění vyberte na panelu nástrojů **Umístění ladění** proces, který chcete nastavit jako aktuální proces z rozevíracího okna **Proces.**

   ![Přepínání mezi procesy](../debugger/media/dbg_execution_switchbetweenmodules.png "DBG_Execution_SwitchBetweenModules")

**Postup nastavení aktuálního procesu z okna Procesy:**

1. Chcete-li otevřít okno **Procesy,** vyberte při ladění **možnost** > Ladění**procesů systému****Windows** > .

1. V okně **Procesy** je aktuální proces označen žlutou šipkou. Poklepejte na proces, který chcete nastavit jako aktuální proces.

   ![Okno Procesy](../debugger/media/dbg_processeswindow.png "DBG_ProcessesWindow")

Přepnutí na proces nastaví jako aktuální proces pro účely ladění. Okna ladicího programu zobrazují stav aktuálního procesu a příkazy krokování ovlivňují pouze aktuální proces.

## <a name="stop-debugging-with-multiple-processes"></a>Zastavení ladění s více procesy

Ve výchozím nastavení, když vyberete **Ladění** > **Stop Ladění**, ladicí program končí nebo odpojí od všech procesů.

- Pokud byl aktuální proces spuštěn v ladicím programu, proces je ukončen.

- Pokud jste připojili ladicí program k aktuálnímu procesu, ladicí program se odpojí od procesu a ponechá proces spuštěný.

Pokud začnete ladit proces z řešení sady Visual Studio, připojte se k jinému procesu, který je již spuštěn, a pak zvolte **Zastavit ladění**, relace ladění končí. Proces, který byl spuštěn v sadě Visual Studio končí, zatímco proces, který jste připojili k stále běží.

Chcete-li řídit způsob, jakým **stop ladění** ovlivňuje jednotlivé **procesy,** v okně Procesy klepněte pravým tlačítkem myši na proces a potom zaškrtněte nebo zrušte zaškrtnutí **políčka Odpojit při zastavení ladění.**

>[!NOTE]
>**Přerušit všechny procesy, když jeden proces přeruší** ladicí program možnost nemá vliv na zastavení, ukončení nebo odpojení od procesů.

### <a name="stop-terminate-and-detach-commands"></a>Příkazy Stop, terminate a detach

Následující tabulka popisuje chování příkazů stop, terminate a detach ladicího programu s více procesy:

|**Příkaz**|**Popis**|
|-|-|
|**Ladění** > **ladění stop**|Pokud se chování nezmění v okně **Procesy,** procesy zahájené ladicím programem jsou ukončeny a připojené procesy jsou odpojeny.|
|**Ladění** > **ukončit vše**|Všechny procesy jsou ukončeny.|
|**Ladění** > **odpojit všechny**|Ladicí program se odpojí od všech procesů.|
|**Okno procesu** **> odpojit**|Ladicí program se odpojí od vybraného procesu.<br />Ostatní procesy zachovat jejich stávající stav (pozastaveno nebo spuštěno).|
|**Okno procesy** > **Ukončit proces**|Vybraný proces je ukončen.<br />Ostatní procesy zachovat jejich stávající stav (pozastaveno nebo spuštěno).|
|**Zpracuje** okno > **Odpojit při** ladění zastaví|Pokud je tato možnost vybrána, **ladění** > **stop ladění** odpojí od vybraného procesu. <br />Pokud není **vybráno, ladění ladění stop** > **ladění** ukončí vybraný proces. |

## <a name="see-also"></a>Viz také

- [Určení symbolu (.pdb) a zdrojových souborů](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)
- [Připojení ke spuštěných procesům](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)
- [Navigace v kódu pomocí ladicího programu](../debugger/navigating-through-code-with-the-debugger.md)
- [Ladění just-in-time](../debugger/just-in-time-debugging-in-visual-studio.md)
- [Ladění vícevláknových aplikací](../debugger/debug-multithreaded-applications-in-visual-studio.md)