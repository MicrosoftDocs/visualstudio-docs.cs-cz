---
title: Aktivovat události pozastavení/obnovení/pozadí při ladění UWP
description: Přečtěte si, jak aktivovat události pozastavení, obnovení a na pozadí při ladění aplikací Univerzální platforma Windows (UWP) v aplikaci Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 01/16/2018
ms.topic: how-to
f1_keywords:
- vs.debug.error.background_task_activate_failure
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- uwp
ms.openlocfilehash: 5b3fa6ea89b91ccfc2c24b0b2eea162760eae29c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99896532"
---
# <a name="how-to-trigger-suspend-resume-and-background-events-while-debugging-uwp-apps-in-visual-studio"></a>Jak aktivovat události pozastavení, obnovení a na pozadí při ladění aplikací pro UWP v aplikaci Visual Studio

Pokud neladíte, **řízení životnosti procesů** systému Windows (PLM) řídí stav provádění vaší aplikace – spuštění, pozastavení, obnovení a ukončení aplikace v reakci na akce uživatele a stav zařízení. Když ladíte, systém Windows tyto aktivační události zakáže. Toto téma popisuje, jak v ladicím programu vyvolat tyto události.

Toto téma také popisuje, jak ladit **úlohy na pozadí**. Úlohy na pozadí umožňují provádět určité operace v procesu na pozadí, a to i v případě, že vaše aplikace není spuštěná. Můžete použít ladicí program k umístění aplikace v režimu ladění a pak – bez spuštění uživatelského rozhraní – spusťte a ladit úlohu na pozadí.

Další informace o správě životního cyklu procesu a úlohách na pozadí najdete v tématu [spouštění, obnovování a](/windows/uwp/launch-resume/index)práce s více úlohami.

## <a name="trigger-process-lifetime-management-events"></a><a name="BKMK_Trigger_Process_Lifecycle_Management_events"></a> Aktivovat události správy životnosti procesů
 Systém Windows může aplikaci pozastavit, když uživatel z ní přepne nebo když systém Windows přejde do úsporného režimu. Můžete reagovat na událost a `Suspending` Uložit relevantní data aplikace a uživatele do trvalého úložiště a uvolnit prostředky. Když se aplikace obnoví z **pozastaveného** stavu, vstoupí do stavu **spuštěno** a pokračuje od místa, kde byla pozastavena. Můžete reagovat na `Resuming` událost pro obnovení nebo obnovení stavu aplikace a uvolnění prostředků.

 I když se Windows v paměti pokusí zachovat tolik pozastavených aplikací, může Windows aplikaci ukončit, pokud není k dispozici dostatek prostředků, aby je bylo možné uchovat v paměti. Uživatel může aplikaci taky explicitně zavřít. Neexistuje žádná zvláštní událost, která by označovala, že uživatel zavřel aplikaci.

 V ladicím programu sady Visual Studio můžete aplikace ručně pozastavit, obnovit a ukončit a ladit tak události životního cyklu procesu. Ladění události životního cyklu procesu:

1. Nastavte zarážku v obslužné rutině události, kterou chcete ladit.

2. Stisknutím klávesy **F5** spusťte ladění.

3. Na panelu nástrojů **umístění ladění** vyberte událost, kterou chcete aktivovat:

     ![Úlohy pozastavení, obnovení, ukončení a na pozadí](../debugger/media/dbg_suspendresumebackground.png)

     **Pozastavení a ukončení** ukončí aplikaci a ukončí relaci ladění.

## <a name="trigger-background-tasks"></a><a name="BKMK_Trigger_background_tasks"></a> Aktivovat úlohy na pozadí
 Každá aplikace může zaregistrovat úlohu na pozadí pro reakci na určité systémové události, a to i v případě, že aplikace není spuštěná. Úlohy na pozadí nemůžou spustit kód, který přímo aktualizuje uživatelské rozhraní. místo toho zobrazují informace uživateli s aktualizacemi dlaždic, aktualizacemi oznámení a informačními zprávami. Další informace najdete v tématu [Podpora vaší aplikace s úlohami na pozadí](/previous-versions/windows/apps/hh977046(v=win.10)).

 Události, které spouštějí úlohy na pozadí aplikace, můžete aktivovat z ladicího programu.

> [!NOTE]
> Ladicí program může aktivovat pouze události, které neobsahují data, například události, které indikují změnu stavu v zařízení. Je nutné ručně aktivovat úlohy na pozadí, které vyžadují vstup uživatele nebo jiná data.

 Nejúčinnější způsob, jak aktivovat událost úlohy na pozadí, je v případě, že vaše aplikace není spuštěná. Nicméně je podporována i aktivace události ve standardní relaci ladění.

### <a name="trigger-a-background-task-event-from-a-standard-debug-session"></a><a name="BKMK_Trigger_a_background_task_event_from_a_standard_debug_session"></a> Aktivace události úlohy na pozadí ze standardní relace ladění

1. Nastavte zarážku v kódu úlohy na pozadí, který chcete ladit.

2. Stisknutím klávesy **F5** spusťte ladění.

3. V seznamu události na panelu nástrojů **umístění ladění** vyberte úlohu na pozadí, kterou chcete spustit.

     ![Úlohy pozastavení, obnovení, ukončení a na pozadí](../debugger/media/dbg_suspendresumebackground.png)

### <a name="trigger-a-background-task-when-the-app-is-not-running"></a><a name="BKMK_Trigger_a_background_task_when_the_app_is_not_running"></a> Spustí úlohu na pozadí, když aplikace není spuštěná.

1. Nastavte zarážku v kódu úlohy na pozadí, který chcete ladit.

2. Otevřete stránku vlastností ladění pro spouštěcí projekt. V Průzkumník řešení vyberte projekt. V nabídce **ladění** vyberte možnost **vlastnosti**.

     V případě projektů v jazyce C++ rozbalte položku **Vlastnosti konfigurace** a pak zvolte možnost **ladění**.

3. Proveďte některou z následujících akcí:

    - V případě projektů v jazyce Visual C# a Visual Basic vyberte možnost **nespouštět, ale ladit můj kód při spuštění**

         ![Vlastnost pro spuštění ladění v jazyce C&#35;&#47;VB](../debugger/media/dbg_csvb_dontlaunchapp.png "DBG_CsVb_DontLaunchApp")

    - V případě projektů v jazyce C++ vyberte v seznamu **Spustit aplikaci** možnost **ne** .

         ![&&#43;&#43;&#47;VB spustit vlastnost ladění aplikace](../debugger/media/dbg_cppjs_dontlaunchapp.png "DBG_CppJs_DontLaunchApp")

4. Stisknutím klávesy **F5** aplikaci vložte do režimu ladění. Všimněte si, že seznam **procesů** na panelu nástrojů **umístění ladění** zobrazuje název balíčku aplikace, který označuje, že jste v režimu ladění.

     ![Seznam procesů úloh na pozadí](../debugger/media/dbg_backgroundtask_processlist.png "DBG_BackgroundTask_ProcessList")

5. V seznamu události na panelu nástrojů **umístění ladění** vyberte úlohu na pozadí, kterou chcete spustit.

     ![Úlohy pozastavení, obnovení, ukončení a na pozadí](../debugger/media/dbg_suspendresumebackground.png "DBG_SuspendResumeBackground")

## <a name="trigger-process-lifetime-management-events-and-background-tasks-from-an-installed-app"></a><a name="BKMK_Trigger_Process_Lifetime_Management_events_and_background_tasks_from_an_installed_app"></a> Aktivace událostí správy životnosti procesů a úloh na pozadí z nainstalované aplikace
 Pomocí dialogového okna **ladit nainstalovaný balíček aplikace** načtěte aplikaci, která je už nainstalovaná do ladicího programu. Můžete například ladit aplikaci, která byla nainstalovaná z Microsoft Store, nebo ladit aplikaci, když máte zdrojové soubory aplikace, ale ne projekt sady Visual Studio pro aplikaci. Dialogové okno **ladit nainstalovaný balíček aplikace** umožňuje spustit aplikaci v režimu ladění na počítači aplikace Visual Studio nebo na vzdáleném zařízení nebo nastavit aplikaci tak, aby běžela v režimu ladění, ale ne ji spustit. Další informace najdete v tématu [ladění nainstalovaného balíčku aplikace](../debugger/debug-installed-app-package.md).

 Po načtení aplikace do ladicího programu můžete použít kterýkoli z kroků popsaných výše.

## <a name="diagnosing-background-task-activation-errors"></a><a name="BKMK_Diagnosing_background_task_activation_errors"></a> Diagnostikování chyb aktivace úlohy na pozadí
 Diagnostické protokoly ve Windows Prohlížeč událostí pro infrastrukturu na pozadí obsahují podrobné informace, které můžete použít k diagnostice a odstraňování chyb úloh na pozadí. Postup zobrazení protokolu:

1. Otevřete aplikaci Prohlížeč událostí.

2. V podokně **Akce** klikněte na možnost **Zobrazit** a zkontrolujte, zda je zaškrtnuto políčko **Zobrazit protokoly pro analýzu a ladění** .

3. Ve stromové struktuře **Prohlížeč událostí (místní)** rozbalte uzly **aplikace a protokoly služby**  >  **Microsoft**  >  **Windows**  >  **BackgroundTasksInfrastructure**.

4. Vyberte **diagnostický** protokol.

## <a name="see-also"></a>Viz také
- [Testování aplikací pro UWP se sadou Visual Studio](../test/unit-test-your-code.md)
- [Ladění aplikací v sadě Visual Studio](debugging-windows-store-and-windows-universal-apps.md)
- [Životní cyklus aplikace](/windows/uwp/launch-resume/app-lifecycle)
- [Spouštění, obnovování a práce s více úlohami](/windows/uwp/launch-resume/index)
