---
title: Jak aktivovat pozastavení, obnovení a událostí na pozadí pro aplikace Windows Store
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
- vs.debug.error.background_task_activate_failure
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 824ff3ca-fedf-4cf5-b3e2-ac8dc82d40ac
caps.latest.revision: 20
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 610614614b47caa04115b8a469793cfca94c666b
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53061877"
---
# <a name="how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio"></a>Jak aktivovat události pozastavení a obnovení a události na pozadí pro aplikace pro Windows Store v sadě Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pokud jste nejsou ladění, Windows **proces správy životního cyklu** (PLM) řídí stav spuštění aplikace – spuštění, pozastavení, pokračování a ukončení aplikace v reakci na akce uživatelů a stav zařízení. Při ladění, zakáže Windows tyto aktivační události. Toto téma popisuje, jak vyvolat tyto události v ladicím programu.

 Toto téma také popisuje, jak ladit **úloh na pozadí**. Úlohy na pozadí umožňují provádět určité operace v procesech na pozadí, i když je aplikace neběží. Ladicí program můžete umístit vaše aplikace v režimu ladění a pak – bez spuštění uživatelského rozhraní – spuštění a ladění úloh na pozadí.

 Další informace o úlohách proces správy životního cyklu a na pozadí v tématu [spouštění, obnovení a multitaskingu](http://msdn.microsoft.com/en-us/04307b1b-05af-46a6-b639-3f35e297f71b).

##  <a name="BKMK_In_this_topic"></a> V tomto tématu
 [Aktivační proces správy životního cyklu události](#BKMK_Trigger_Process_Lifecycle_Management_events)

 [Úlohy na pozadí trigger](#BKMK_Trigger_background_tasks)

- [Aktivační událost úlohy pozadí ze standardní ladicí relaci](#BKMK_Trigger_a_background_task_event_from_a_standard_debug_session)

- [Aktivuje úlohu na pozadí, když není aplikace spuštěna](#BKMK_Trigger_a_background_task_when_the_app_is_not_running)

  [Aktivovat události proces správy životního cyklu a úloh z nainstalovaných aplikací na pozadí](#BKMK_Trigger_Process_Lifetime_Management_events_and_background_tasks_from_an_installed_app)

  [Diagnostika chyb aktivace úlohy na pozadí](#BKMK_Diagnosing_background_task_activation_errors)

##  <a name="BKMK_Trigger_Process_Lifecycle_Management_events"></a> Aktivační proces správy životního cyklu události
 Windows může pozastavení aplikace, když uživatel přejde od nebo když Windows vstupuje do stavu snížené spotřeby energie. Můžete reagovat `Suspending` události uložte příslušné aplikace a uživatelská data do trvalého úložiště a uvolnění prostředků. Při obnovení aplikace ze **pozastaveno** stavu, přešel do **systémem** stavu a bude pokračovat od kdy byl při bylo pozastaveno. Můžete reagovat `Resuming` událostí k obnovení nebo obnovit stav aplikace a uvolnit prostředky.

 I když se Windows pokusí mějte na paměti co nejvíce tolik pozastavenou aplikaci, můžete Windows aplikaci ukončit, pokud nejsou k dispozici dostatek prostředků, aby byl v paměti. Uživatele můžete také explicitně zavřít aplikaci. Neexistuje žádná speciální událost označující, že uživatel zavřel aplikace.

 V ladicím programu sady Visual Studio můžete ručně pozastavení, obnovení a Ukončit ladění zpracování událostí životního cyklu aplikací. Chcete-li ladit událost životního cyklu procesu:

1.  Nastavte breakpooint v obslužné rutině události, ke které chcete ladit.

2.  Stisknutím klávesy **F5** pro spuštění ladění.

3.  Na **umístění ladění** nástrojů, zvolte události, ke které chcete, aby se mohly aktivovat:

     ![Pozastavení, obnovení, ukončit a úloh na pozadí](../debugger/media/dbg-suspendresumebackground.png "DBG_SuspendResumeBackground")

     Všimněte si, že **pozastavit a ukončit** aplikace se zavře a ukončení relace ladění.

##  <a name="BKMK_Trigger_background_tasks"></a> Úlohy na pozadí trigger
 Libovolná aplikace můžete zaregistrovat úlohu na pozadí na určité události systému, i když není aplikace spuštěna. Úlohy na pozadí nelze spustit kód, který přímo aktualizací uživatelského rozhraní; Místo toho zobrazí informace o uživateli s aktualizace dlaždice, oznámení "BADGE" aktualizace a informační zprávy. Další informace najdete v tématu [podpoře vaší aplikace v rámci úlohy na pozadí](http://msdn.microsoft.com/en-us/4c7bb148-eb1f-4640-865e-41f627a46e8e)

 Můžete aktivovat události, které spustí úlohy na pozadí pro aplikaci z ladicího programu.

> [!NOTE]
>  Ladicí program může spustit pouze události, které neobsahují data, jako jsou události, které signalizovat změnu stavu v zařízení. Budete muset ručně aktivovat úlohy na pozadí, které vyžadují vstup uživatele nebo jiná data.

 Většina realistické způsob, jak spouštět událost úlohy na pozadí při vaší aplikace neběží. Aktivuje událost ve standardní relaci ladění je však také podporováno.

###  <a name="BKMK_Trigger_a_background_task_event_from_a_standard_debug_session"></a> Aktivační událost úlohy pozadí ze standardní ladicí relaci

1.  Nastavte zarážku v kódu úlohy na pozadí, který chcete ladit.

2.  Stisknutím klávesy **F5** pro spuštění ladění.

3.  V seznamu událostí na **umístění ladění** nástrojů, zvolte úlohu na pozadí, který chcete spustit.

     ![Pozastavení, obnovení, ukončit a úloh na pozadí](../debugger/media/dbg-suspendresumebackground.png "DBG_SuspendResumeBackground")

###  <a name="BKMK_Trigger_a_background_task_when_the_app_is_not_running"></a> Aktivuje úlohu na pozadí, když není aplikace spuštěna

1.  Nastavte zarážku v kódu úlohy na pozadí, který chcete ladit.

2.  Otevření stránky vlastnosti ladění pro počáteční projekt. V Průzkumníku řešení vyberte projekt. Na **ladění** nabídce zvolte **vlastnosti**.

     Pro projekty C++, možná budete muset Rozbalit **vlastnosti konfigurace** a klikněte na tlačítko **ladění**.

3.  Proveďte jednu z těchto akcí:

    -   Pro projekty Visual C# a Visual Basic, zvolte **nespouštět, ale ladit můj kód při spuštění**

         ![C&#35;&#47;VB ladění spouštěcí aplikace vlastnost](../debugger/media/dbg-csvb-dontlaunchapp.png "DBG_CsVb_DontLaunchApp")

    -   Pro projekty jazyka JavaScript a Visual C++, zvolte **ne** z **spuštění aplikace** seznamu.

         ![C&#43;&#43;&#47;VB spuštění vlastnosti ladění aplikace](../debugger/media/dbg-cppjs-dontlaunchapp.png "DBG_CppJs_DontLaunchApp")

4.  Stisknutím klávesy **F5** do aplikace v režimu ladění. Poznámka: **procesu** seznamu **umístění ladění** nástrojů zobrazí název balíčku aplikace, která označuje, že je v režimu ladění.

     ![Seznam procesů úloh na pozadí](../debugger/media/dbg-backgroundtask-processlist.png "DBG_BackgroundTask_ProcessList")

5.  V seznamu událostí na **umístění ladění** nástrojů, zvolte úlohu na pozadí, který chcete spustit.

     ![Pozastavení, obnovení, ukončit a úloh na pozadí](../debugger/media/dbg-suspendresumebackground.png "DBG_SuspendResumeBackground")

##  <a name="BKMK_Trigger_Process_Lifetime_Management_events_and_background_tasks_from_an_installed_app"></a> Aktivovat události proces správy životního cyklu a úloh z nainstalovaných aplikací na pozadí
 Použijte dialogové okno ladění nainstalovaná aplikace načíst aplikaci, která je již nainstalována do ladicího programu. Například může ladit aplikaci, která byla nainstalovaná z Windows storu, nebo ladění aplikace, když máte zdrojových souborů pro aplikace, ale ne sady Visual Studio projekt pro aplikaci. Dialogové okno ladění nainstalovaná aplikace umožňuje že spustit aplikaci v režimu ladění v sadě Visual Studio počítači nebo na vzdáleném zařízení, nebo chcete-li nastavit aplikaci spustit v režimu ladění, ale nelze spustit. Najdete v článku **spustit nainstalovanou aplikaci v ladicím programu** části buď [JavaScript](../debugger/start-a-debugging-session-for-store-apps-in-visual-studio-javascript.md#BKMK_Start_an_installed_app_in_the_debugger) nebo [Visual C++, Visual C# a Visual Basic](../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md#BKMK_Start_an_installed_app_in_the_debugger) verzích **spuštění ladicí relace** Další informace.

 Po načtení aplikace do ladicího programu, můžete některé z výše popsaných postupů.

##  <a name="BKMK_Diagnosing_background_task_activation_errors"></a> Diagnostika chyb aktivace úlohy na pozadí
 Diagnostické protokoly v prohlížeči událostí Windows pro infrastrukturu pozadí obsažené podrobné informace, které můžete použít k diagnostice a řešení potíží s chybami úloh na pozadí. Chcete-li zobrazit v protokolu:

1.  Otevřete Prohlížeč událostí aplikace.

2.  V **akce** podokně zvolte **zobrazení** a ujistěte se, že **zobrazit protokoly ladění a analýzu** je zaškrtnuté políčko.

3.  Na **Prohlížeč událostí (místní)** stromu, rozbalte uzly **protokoly aplikací a služeb** / **Microsoft** / **Windows**   /  **BackgroundTasksInfrastructure**.

4.  Zvolte **diagnostických** protokolu.

## <a name="see-also"></a>Viz také
 [Testování aplikací pro Store pomocí sady Visual Studio](../test/testing-store-apps-with-visual-studio.md) [ladění aplikací v sadě Visual Studio](../debugger/debug-store-apps-in-visual-studio.md) [životního cyklu aplikací](http://msdn.microsoft.com/en-us/53cdc987-c547-49d1-a5a4-fd3f96b2259d) [spouštění, obnovení a multitaskingu](http://msdn.microsoft.com/en-us/04307b1b-05af-46a6-b639-3f35e297f71b)
