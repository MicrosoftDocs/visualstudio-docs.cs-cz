---
title: Ladění více procesů | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/20/2018
ms.technology: vs-ide-debug
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0b306bcca4ac8cc0568fc609ec25c8b335d18010
ms.sourcegitcommit: 81e9d90843ead658bc73b30c869f25921d99e116
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/26/2018
ms.locfileid: "52305647"
---
# <a name="debug-multiple-processes"></a>Ladění více procesů

Visual Studio dokáže ladit řešení, která má několik procesů. Můžete spustit a přepínání mezi procesy, přerušení, pokračovat a procházení zdroje, zastavení ladění a end nebo odpojení od jednotlivých procesů.  

##  <a name="start-debugging-with-multiple-processes"></a>Spuštění ladění pomocí několika procesů 

Když více než jeden projekt v řešení sady Visual Studio můžete spustit nezávisle na sobě, můžete zvolit projekt, které spustí ladicí program. Aktuální spouštěcí projekt, zobrazí se v nabízeném **Průzkumníku řešení**. 

Chcete-li změnit projekt při spuštění v **Průzkumníka řešení**, klikněte pravým tlačítkem na jiný projekt a vyberte **nastavit jako spouštěný projekt**.

Pro spuštění ladění projektu z **Průzkumníka řešení** bez toho, že projekt po spuštění, klikněte pravým tlačítkem na projekt a vyberte **ladění** > **zahájit novou instanci** nebo **krokování s vnořením do nové instance**. 

**Chcete-li nastavit projekt po spuštění nebo více projektů z řešení vlastnosti:**

1. Vyberte řešení v **Průzkumníka řešení** a pak vyberte **vlastnosti** ikonu na panelu nástrojů nebo kliknutím pravým tlačítkem řešení a vyberte **vlastnosti**.  
   
1. Na **vlastnosti** stránce **společné vlastnosti** > **spouštěný projekt**.
   
   ![Změna typu spouštění projektu](../debugger/media/dbg_execution_startmultipleprojects.png "DBG_Execution_StartMultipleProjects")  
   
1. Vyberte **aktuální výběr**, **jeden spouštěný projekt** a soubor projektu nebo **více projektů po spuštění**. 

   Pokud vyberete **více projektů po spuštění**, můžete změnit pořadí spouštění a akce, které se pro každý projekt: **Start**, **spustit bez ladění**, nebo **Žádný**.  
   
1. Vyberte **použít**, nebo **OK** pro použití a zavřete dialogové okno. 

###  <a name="BKMK_Attach_to_a_process"></a> Připojit k procesu  

Ladicí program může taky *připojit* pro aplikace spuštěné procesy mimo sadu Visual Studio, včetně na vzdálených zařízeních. Po připojení k aplikaci, můžete použít ladicího programu sady Visual Studio. Funkce ladění může být omezená. To závisí na tom, jestli aplikace byl sestaven s ladicími informacemi, určuje, zda máte přístup ke zdrojovému kódu aplikace a určuje, zda kompilátor JIT sleduje informace o ladění.  
  
Další informace najdete v tématu [připojení ke spuštěným procesům](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).  
  
**Připojit ke spuštěnému procesu:**  
  
1. Spuštěné aplikace, vyberte **ladění** > **připojit k procesu**. 

   ![Připojit k procesu – dialogové okno](../debugger/media/dbg_attachtoprocessdlg.png "připojit k procesu – dialogové okno")  
  
1. V **připojit k procesu** dialogové okno, vyberte proces **procesy k dispozici** seznamu a pak vyberte **připojit**.  
  
>[!NOTE]
>Ladicí program nepřipojí automaticky k podřízenému procesu, který je spuštěn procesem ladění i v případě, že je podřízený projekt ve stejném řešení. Chcete-li ladit podřízený proces, připojit k podřízenému procesu po jeho spuštění, nebo nakonfigurovat Editor registru Windows spustil podřízený proces v nové instanci ladicího programu.  
  
###  <a name="BKMK_Automatically_start_an_process_in_the_debugger"></a> Automaticky spustit proces v ladicím programu pomocí Editoru registru  

V některých případech může být třeba ladit spouštěcí kód pro aplikace, který je spouštěn jiným procesem. Příklady zahrnují služby a akce pro vlastní nastavení. Můžete mít ladicí program spustit a automaticky připojit k aplikaci. 

1. Spusťte Editor registru Windows spuštěním *regedit.exe*.  
   
1. V editoru registru přejděte na **HKEY_LOCAL_MACHINE\Software\Microsoft\Windows NT\CurrentVersion\Image File Execution Options**.  
  
1. Vyberte složku aplikace, kterou chcete spustit v ladicím programu.  
   
   Pokud aplikace není uveden jako podřízená složka, klikněte pravým tlačítkem na **Image File Execution Options**vyberte **nový** > **klíč**a zadejte název aplikace. Nebo klikněte pravým tlačítkem na nový klíč ve stromové struktuře vyberte **přejmenovat**a pak zadejte název aplikace. 
   
1. Klikněte pravým tlačítkem na nový klíč ve stromu a vyberte **nový** > **řetězcovou hodnotu**.  
   
1. Změňte název nové hodnoty z **nová hodnota #1** k `debugger`.  
   
1. Klikněte pravým tlačítkem na **ladicí program** a vyberte **změnit**.  
   
   ![Řetězec dialogové okno Upravit](../debugger/media/dbg_execution_automaticstart_editstringdlg.png "dialogové okno Upravit řetězec")  
   
1. V **Upravit řetězec** dialogovém okně `vsjitdebugger.exe` v **údaj hodnoty** a potom vyberte **OK**.  
   
   ![Automatické ladicí program spustit záznam v regedit.exe](../debugger/media/dbg_execution_automaticstart_result.png "automatické ladicí program spustit záznam v regedit.exe")  
   
##  <a name="BKMK_Switch_processes__break_and_continue_execution__step_through_source"></a> Ladění více procesů 
<a name="BKMK_Configure_the_execution_behavior_of_multiple_processes"></a> 

Při ladění aplikace pomocí několika procesů, ladicí program příkazy zásadní, krokování a pokračování vliv na všechny procesy ve výchozím nastavení. Například když proces pozastaven na zarážce, spuštění všech procesů je také pozastaveno. Můžete změnit toto výchozí chování, chcete-li získat lepší kontrolu nad cíli prováděcích příkazů.  

**Chcete-li změnit, zda všechny procesy jsou pozastavené, když se jeden přeruší:**

- V části **nástroje** (nebo **ladění**) > **možnosti** > **ladění** > **Obecné**zaškrtněte nebo zrušte **přerušit všechny procesy při přerušení jednoho procesu** zaškrtávací políčko.  
  
###  <a name="BKMK_Break__step__and_continue_commands"></a> Přerušit, krokovat a pokračovat příkazy  
  
Následující tabulka popisuje chování ladění příkazů, kdy **přerušit všechny procesy při přerušení jednoho procesu** zaškrtávací políčko zaškrtnuto nebo možnost:

|**Příkaz**|Vybrané|Vybraná|  
|-|-|-|  
|**Ladění**  > **přerušit vše**|Budou přerušeny všechny procesy.|Budou přerušeny všechny procesy.|  
|**Ladění** > **pokračovat**|Obnoví se všechny procesy.|Všechny pozastavené procesy budou pokračovat.|  
|**Ladění** > **Krokovat s vnořením**, **krok přes**, nebo **Krokovat s Vystoupením**|Všechny procesy jsou spuštěny během kroků aktuálního procesu. <br />Pak budou přerušeny všechny procesy.|Aktuální kroky procesu. <br />Pokračování pozastavených procesů. <br />Spuštěné procesy pokračují.|  
|**Ladění** > **krok do aktuálního procesu**, **krok přes aktuální proces**, nebo **krok z aktuálního procesu**|Není k dispozici|Aktuální kroky procesu.<br />Jiné procesy udržují svůj stávající stav (pozastaveno nebo spuštěno).|  
|Okno zdroje **zarážku**|Budou přerušeny všechny procesy.|Pouze zdrojové okno proces bude ukončen.|  
|Okno zdroje **spustit ke kurzoru**<br />Okno zdroje musí být v aktuálním procesu.|Všechny procesy jsou spuštěny během procesu zdrojového okna je spuštěn na kurzoru a poté se přeruší.<br />Pak budou přerušeny všechny procesy.|Proces zdrojového okna je spuštěn na kurzoru.<br />Jiné procesy udržují svůj stávající stav (pozastaveno nebo spuštěno).|  
|**Procesy** okna > **přerušit proces**|Není k dispozici|Vybraný proces bude ukončen.<br />Jiné procesy udržují svůj stávající stav (pozastaveno nebo spuštěno).|  
|**Procesy** okna > **pokračovat v procesu**|Není k dispozici|Vybraný proces bude pokračovat.<br />Jiné procesy udržují svůj stávající stav (pozastaveno nebo spuštěno).|  

###  <a name="BKMK_Find_the_source_and_symbol___pdb__files"></a> Hledání zdroje a symbolů (PDB) souborů  
Chcete-li procházet zdrojový kód procesu, ladicí program potřebuje přístup k jejím zdrojové soubory a soubory symbolů. Další informace najdete v tématu [zadání symbolu (.pdb) a zdrojových souborů](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).  
  
Pokud nelze získat přístup k souborům pro proces, můžete procházet pomocí **zpětný překlad** okna. Další informace najdete v tématu [postupy: použití okna zpětného překladu](../debugger/how-to-use-the-disassembly-window.md).  

###  <a name="BKMK_Switch_between_processes"></a> Přepínání mezi procesy  

Můžete se připojit k více procesům při ladění, ale pouze jeden proces je v daném okamžiku aktivní v ladicím programu. Lze nastavit aktivní nebo *aktuální* zpracovat v **umístění ladění** nástrojů, nebo **procesy** okna. Chcete-li přepnout mezi procesy, oba procesy musí být v režimu pozastavení.  
  
**Chcete-li nastavit aktuální proces na panelu nástrojů umístění ladění:**  
  
1. Chcete-li otevřít **umístění ladění** nástrojů vyberte **zobrazení** > **panely nástrojů** > **umístění ladění**.  
   
1. Během ladění na **umístění ladění** nástrojů vyberte proces, který chcete nastavit jako aktuální proces **procesu** rozevíracího seznamu.  
  
   ![Přepínání mezi procesy](../debugger/media/dbg_execution_switchbetweenmodules.png "DBG_Execution_SwitchBetweenModules")  
  
**Chcete-li nastavit aktuální proces z okna procesy:**  
  
1. Chcete-li otevřít **procesy** okně během ladění, **ladění** > **Windows** > **procesy**. 

1. V **procesy** okna aktuální proces je označen žlutou šipkou. Dvakrát klikněte na proces, který chcete nastavit jako aktuální proces.  
  
   ![Procesy – okno](../debugger/media/dbg_processeswindow.png "DBG_ProcessesWindow")  

Přepínání procesu nastaví jako aktuální proces pro účely ladění. Ladicí program systému windows zobrazit stav pro aktuální proces a příkazy krokování ovlivní pouze aktuální proces.  
  
## <a name="stop-debugging-with-multiple-processes"></a>Zastavit ladění pomocí několika procesů  
  
Ve výchozím nastavení, když vyberete **ladění** > **Zastavit ladění**, ladicí program ukončí nebo odpojí od všech procesů. 
  
- Pokud byl aktuální proces spuštěn v ladicím programu, je ukončen.  
  
- Pokud jste se připojili k aktuálnímu procesu ladicího programu, ladicí program se odpojí z procesu a ponechá proces spuštěný.  
  
Pokud spustíte ladění procesu v řešení sady Visual Studio, připojte k jinému procesu, který je již spuštěn a klikněte na tlačítko **Zastavit ladění**se neukončí relace ladění. Ukončení procesu, která byla spuštěna v sadě Visual Studio, zatímco stále spuštěný proces, kterým jste se připojili k. 

K řízení způsobu, který **Zastavit ladění** má vliv na jednotlivé procesy v **procesy** okna, klikněte pravým tlačítkem na procesu a pak zaškrtněte nebo zrušte **odpojit při zastavení ladění** zaškrtávací políčko.  
  
>[!NOTE]
>**Přerušit všechny procesy při přerušení jednoho procesu** volba ladicího programu nemá vliv na zastavení, ukončení nebo odpojení od procesů.  
  
###  <a name="stop-terminate-and-detach-commands"></a>Zastavit, ukončit a odebrat příkazy  
  
Následující tabulka popisuje chování zastavení ladicího programu, ukončit a odebrat příkazy pomocí několika procesů: 

|**Příkaz**|**Popis**|  
|-|-| 
|**Ladění** > **Zastavit ladění**|Pokud toto chování změněno v **procesy** okně procesy spuštěné ladicím programem jsou ukončeny a připojené procesy jsou odpojeny.|  
|**Ladění** > **ukončit vše**|Všechny procesy jsou ukončeny.|  
|**Ladění** > **Odpojit vše**|Ladicí program se odpojí od všech procesů.|  
|**Procesy** okna > **odpojit proces**|Ladicí program se odpojí z vybraných procesů.<br />Jiné procesy udržují svůj stávající stav (pozastaveno nebo spuštěno).|  
|**Procesy** okna > **ukončit proces**|Vybraný proces je ukončen.<br />Jiné procesy udržují svůj stávající stav (pozastaveno nebo spuštěno).|  
|**Procesy** okna > **odpojit při zastavení ladění**|Pokud je zaškrtnuto, **ladění** > **Zastavit ladění** odpojí z vybraných procesů. <br />Pokud není vybrána, **ladění** > **Zastavit ladění** vybraný proces ukončí. |  
## <a name="see-also"></a>Viz také:  
 [Zadání symbolu (.pdb) a zdrojových souborů](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)   
 [Připojení ke spuštěným procesům](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [Procházení kódu s ladicím programem](../debugger/navigating-through-code-with-the-debugger.md)   
 [Ladění Just-In-Time](../debugger/just-in-time-debugging-in-visual-studio.md)   
 [Ladění vícevláknových aplikací](../debugger/debug-multithreaded-applications-in-visual-studio.md)