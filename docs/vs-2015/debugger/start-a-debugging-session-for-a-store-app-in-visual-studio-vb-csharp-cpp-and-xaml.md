---
title: Spuštění ladicí relace pro aplikaci pro Store (VB, C#, C++ a XAML) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- VC.Project.IVCAppHostRemoteDebugPageObject.MachineName
- VC.Project.IVCAppHostRemoteDebugPageObject.BreakpointBehavior
- VC.Project.IVCAppHostLocalDebugPageObject.GPUDebuggerTargetType
- VC.Project.IVCAppHostTetheredDebugPageObject.DebuggerType
- VC.Project.IVCAppHostLocalDebugPageObject.BreakpointBehavior
- VC.Project.IVCAppHostRemoteDebugPageObject.LaunchApplication
- VC.Project.IVCAppHostRemoteDebugPageObject.GPUDebuggerTargetType
- VC.Project.IVCAppHostLocalDebugPageObject.DebuggerType
- VC.Project.IVCAppHostSimulatorDebugPageObject.DebuggerType
- ImmersiveProjects.Properties.Debug
- VC.Project.IVCAppHostTetheredDebugPageObject.LaunchApplication
- VC.Project.IVCAppHostSimulatorDebugPageObject.LaunchApplication
- VC.Project.IVCAppHostSimulatorDebugPageObject.GPUDebuggerTargetType
- VC.Project.IVCAppHostLocalDebugPageObject.LaunchApplication
- VC.Project.IVCAppHostLocalDebugPageObject.AllowLocalNetworkLoopback
- AppPackage.Properties.Debug
- VC.Project.IVCAppHostRemoteDebugPageObject.Authentication
- VC.Project.IVCAppHostRemoteDebugPageObject.DebuggerType
- VC.Project.IVCAppHostSimulatorDebugPageObject.BreakpointBehavior
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 66ec0e79-8261-4c19-a618-3fd1b3f71bbd
caps.latest.revision: 23
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: bd0a89ac1d96e2d1af829ba04e6e164f8fae7f8f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85542178"
---
# <a name="start-a-debugging-session-for-a-store-app-in-visual-studio-vb-c-c-and-xaml"></a>Spuštění ladicí relace pro aplikaci pro Store v sadě Visual Studio (jazyk Visual Basic, C#, C++ a XAML)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Platí pro Windows a Windows Phone] (.. /Image/windows_and_phone_content.png "windows_and_phone_content")

 Toto téma popisuje, jak spustit relaci ladění pro aplikace pro Store napsané v jazyce XAML a Visual C++, Visual C# nebo Visual Basic. Ladění aplikace zahrnuje konfiguraci relace ladění a výběr způsobu spuštění aplikace.

> [!NOTE]
> Pro aplikace napsané v JavaScriptu a HTML viz [spustit relaci ladění (JavaScript)](../debugger/start-a-debugging-session-for-store-apps-in-visual-studio-javascript.md).

## <a name="in-this-topic"></a><a name="BKMK_In_this_topic"></a> V tomto tématu
 [Snadný způsob, jak spustit ladění](#BKMK_The_easy_way_to_start_debugging)

 [Konfigurace relace ladění](#BKMK_Configure_the_debugging_session)

- [Otevřete stránku vlastností ladění pro projekt.](#BKMK_Open_the_debugging_property_page_for_the_project)

- [Zvolit možnosti konfigurace sestavení](#BKMK_Choose_the_build_configuration_options)

- [Zvolit cíl nasazení](#BKMK_Choose_the_deployment_target)

- [Vyberte ladicí program, který se má použít.](#BKMK_Choose_the_debugger_to_use)

- [Volitelné Zpoždění spuštění relace ladění](#BKMK__Optional__Delay_starting_the_debug_session)

- [Volitelné Zakázat zpětné smyčky sítě](#BKMK__Optional__Disable_network_loopbacks)

- [Volitelné Přeinstalujte aplikaci při spuštění ladění.](#BKMK__Optional__Reinstall_the_app_when_you_start_debugging)

- [Volitelné Zakázat požadavek na ověření pro spuštění vzdáleného ladicího programu](#BKMK__Optional__Disable_authentication_requirement_to_start_the_remote_debugger)

  [Spuštění relace ladění](#BKMK_Start_the_debugging_session)

- [Spustit ladění (F5)](#BKMK_Start_debugging__F5_)

- [Spustit ladění (F5), ale zpozdit začátek aplikace](#BKMK_Start_debugging__F5__but_delay_the_app_start)

- [Spustit nainstalovanou aplikaci v ladicím programu](#BKMK_Start_an_installed_app_in_the_debugger)

- [Připojení ladicího programu ke spuštěné aplikaci](#BKMK_Attach_the_debugger_to_a_running_app_)

  - [Nastavení aplikace, která se má spustit v režimu ladění](#BKMK_Set_the_app_to_run_in_debug_mode)

  - [Připojit ladicí program](#BKMK_Attach_the_debugger)

## <a name="the-easy-way-to-start-debugging"></a><a name="BKMK_The_easy_way_to_start_debugging"></a> Snadný způsob, jak spustit ladění

1. Otevřete řešení aplikace v aplikaci Visual Studio.

2. Vyberte F5.

   Visual Studio vytvoří a spustí aplikaci pomocí připojeného ladicího programu. Spuštění pokračuje, dokud není dosaženo zarážky, ručním zastavením spuštění, výskytu neošetřené výjimky nebo ukončení aplikace. Další informace najdete v tématu [Navigace v relaci ladění (XAML a C#)](../debugger/navigate-a-debugging-session-in-visual-studio-xaml-and-csharp.md) .

## <a name="configure-the-debugging-session"></a><a name="BKMK_Configure_the_debugging_session"></a> Konfigurace relace ladění

### <a name="open-the-debugging-property-page-for-the-project"></a><a name="BKMK_Open_the_debugging_property_page_for_the_project"></a> Otevřete stránku vlastností ladění pro projekt.

1. V Průzkumník řešení vyberte projekt. V místní nabídce vyberte možnost **vlastnosti**.

2. Chcete-li otevřít stránku vlastností ladění projektu:

    - Pro Visual C# a Visual Basic aplikace vyberte možnost **ladit**.

         ![Stránka vlastností ladění projektu v jazyce C&#35; &#47; VB](../debugger/media/dbg-csvb-debugpropertypage.png "DBG_CsVb_DebugPropertyPage")

    - Pro Visual C++ aplikace rozbalte uzel **Vlastnosti konfigurace**  a pak zvolte možnost **ladění**.

         ![Stránka vlastností ladění aplikace pro Windows Store v jazyce C&#43;&#43; ](../debugger/media/dbg-cpp-debugpropertypage.png "DBG_CPP_DebugPropertyPage")

### <a name="choose-the-build-configuration-options"></a><a name="BKMK_Choose_the_build_configuration_options"></a> Zvolit možnosti konfigurace sestavení

1. V seznamu **Konfigurace** vyberte **ladění** nebo **(aktivní) ladění**.

2. V seznamu **platforma** vyberte cílovou platformu, pro kterou chcete vytvořit. Ve většině případů je nejlepší volbou **Libovolný procesor** (**všechny platformy** v Visual C++).

### <a name="choose-the-deployment-target"></a><a name="BKMK_Choose_the_deployment_target"></a> Zvolit cíl nasazení
 ![Platí jenom pro Windows.](../debugger/media/windows-only-content.png "windows_only_content")

 Aplikaci pro Windows Store můžete nasadit a ladit na počítači aplikace Visual Studio, v simulátoru sady Visual Studio v místním počítači nebo na vzdáleném zařízení.

- V případě aplikací C# a Visual Basic vyberte cíl ze seznamu **cílové zařízení** na stránce vlastností **ladění** projektu.

- V případě aplikací pro C++ vyberte na stránce vlastností **ladění** cíl ze seznamu **Spustit ladicí program** :

  Vyberte jednu z těchto možností:

|Možnost|Popis|
|-|-|
|**Místní počítač**|Ladit aplikaci v aktuální relaci na místním počítači. Viz [spuštění aplikací pro Windows Store na místním počítači](../debugger/run-windows-store-apps-on-the-local-machine.md).|
|**Simulátor**|Ladit aplikaci v simulátoru sady Visual Studio pro [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] aplikace. Simulátor je okno plochy, které umožňuje ladění funkcí zařízení, jako jsou dotyková gesta a rotace zařízení, které nejsou k dispozici na místním počítači. Viz [spuštění aplikací pro Windows Store v simulátoru](../debugger/run-windows-store-apps-in-the-simulator.md).|
|**Vzdálený počítač**|Ladit aplikaci na zařízení, které je připojené k místnímu počítači přes intranet nebo přímo připojené pomocí kabelu Ethernet. Chcete-li provést ladění vzdáleně, musí být na vzdáleném zařízení nainstalovány a spuštěny nástroje Visual Studio Remote Tools. Viz [spuštění aplikací pro Windows Store ve vzdáleném počítači](../debugger/run-windows-store-apps-on-a-remote-machine.md).|

 Pokud zvolíte možnost **vzdálený počítač**, zadejte název nebo IP adresu vzdáleného počítače jedním z následujících způsobů:

- Zadejte název nebo IP adresu vzdáleného počítače.

  - V případě aplikací C# a Visual Basic zadejte do pole **vzdálený počítač** název nebo IP adresu.

  - V případě aplikací pro C++ zadejte do pole **název počítače** název nebo IP adresu.

- V dialogovém okně **Vybrat připojení vzdáleného ladicího programu** zvolte vzdálený počítač.

   Otevření dialogového okna:

  - Pro C# a Visual Basic aplikace vyberte **Najít**.

  - V případě aplikací pro C++ klikněte v poli **název počítače** na šipku dolů a vyberte **\<Locate...>** .

    ![Dialogové okno vybrat připojení vzdáleného ladicího programu](../debugger/media/vsrun-selectremotedebuggerdlg.png "VSRUN_SelectRemoteDebuggerDlg")

  > [!NOTE]
  > V dialogovém okně **Vybrat připojení vzdáleného ladicího programu** se zobrazí počítače, které jsou v místní podsíti a počítače, které jsou přímo připojené k počítači sady Visual Studio pomocí kabelu Ethernet. Pokud chcete zadat jiný počítač, zadejte název do pole **název počítače** .

  ![Platí jenom pro Windows Phone](../debugger/media/phone-only-content.png "phone_only_content")

  Aplikaci Windows Phone Storu můžete nasadit a ladit na zařízení nebo na jednom z emulátorů pro telefon sady Visual Studio. V seznamu **cílové zařízení** vyberte zařízení nebo emulátor.

### <a name="choose-the-debugger-to-use"></a><a name="BKMK_Choose_the_debugger_to_use"></a> Vyberte ladicí program, který se má použít.
 Ve výchozím nastavení Visual Studio ladit spravovaný kód v C# a Visual Basic aplikace.

 Pro C# a Visual Basic aplikace můžete zvolit ladění spravovaného i nativního kódu C/C++ ve vaší aplikaci. Zaškrtněte políčko **Povolit ladění nespravovaného kódu** pro zahrnutí nativního kódu do relace ladění.

 Ve výchozím nastavení Visual Studio ladí nativní kód v aplikaci C++.

 Pro aplikace v jazyce C++ se můžete rozhodnout, že chcete ladit konkrétní typy kódu, které jsou součástí vaší aplikace, místo, nebo kromě nativního kódu. Kód, který chcete ladit, určíte v seznamu **Typ ladicího programu** na stránce vlastností **ladění** projektu aplikace.

 V seznamu **aplikačních procesů** vyberte jeden z těchto ladicích programů:

|Typ ladicího programu|Popis|
|-|-|
|**Pouze skript**|Ladění kódu JavaScriptu ve vaší aplikaci. Spravovaný kód a nativní kód jsou ignorovány.|
|**Pouze nativní**|Ladění nativního kódu C/C++ ve vaší aplikaci. Spravovaný kód a kód jazyka JavaScript jsou ignorovány.|
|**Jenom spravovaná**|Ladění spravovaného kódu ve vaší aplikaci. Kód JavaScriptu a nativní kód jazyka C/C++ jsou ignorovány.|
|**Smíšený (spravovaný a nativní)**|Ladění nativního kódu C/C++ a spravovaného kódu ve vaší aplikaci. JavaScriptový kód se ignoruje.|
|**Pouze GPU**|Ladit nativní kód jazyka C++, který je spuštěn na grafické jednotce procesoru (GPU).|

 ![Platí jenom pro Windows Phone](../debugger/media/phone-only-content.png "phone_only_content")

 Pro aplikace Windows Store Phone můžete také zvolit ladicí program, který se má použít pro procesy na pozadí z **procesu úlohy na pozadí**.

### <a name="optional-delay-starting-the-debug-session"></a><a name="BKMK__Optional__Delay_starting_the_debug_session"></a> Volitelné Zpoždění spuštění relace ladění
 Ve výchozím nastavení Visual Studio hned spustí aplikaci při spuštění ladění. Můžete také spustit ladicí relaci, ale zpozdit začátek aplikace. Když vyberete tuto možnost, aplikace se spustí v ladicím programu při spuštění z obrazovky Start nebo podle aktivační smlouvy nebo když ji spustí jiný proces nebo metoda. Můžete také zpozdit začátek aplikace, pokud chcete ladit úlohu na pozadí, když aplikace sama není spuštěná.

 Ke zpoždění spuštění vaší aplikace můžete:

- Pro Visual C# a Visual Basic aplikace vyberte možnost **nespouštět, ale ladit můj kód při spuštění** na stránce vlastností **ladění** .

- U Visual C++ch aplikací vyberte v seznamu **Spustit aplikaci** na stránce vlastností **ladění** možnost **Ano** .

### <a name="optional-disable-network-loopbacks"></a><a name="BKMK__Optional__Disable_network_loopbacks"></a> Volitelné Zakázat zpětné smyčky sítě
 ![Platí jenom pro Windows.](../debugger/media/windows-only-content.png "windows_only_content")

 Z bezpečnostních důvodů není v aplikaci pro Windows Store, která je nainstalovaná standardním způsobem, povoleno provádět síťová volání do zařízení, na kterém je nainstalovaná. Ve výchozím nastavení vytvoří nasazení sady Visual Studio výjimku z tohoto pravidla pro nasazenou aplikaci. Tato výjimka umožňuje testovat komunikační postupy na jednom počítači. Před odesláním aplikace do Windows Storu byste měli aplikaci testovat bez výjimky.

 Odebrání výjimky zpětné smyčky sítě:

- V případě aplikací Visual C# a Visual Basic zrušte zaškrtnutí políčka **Povolení zpětné smyčky sítě** na stránce vlastností **ladění** .

- V případě Visual C++ch aplikací vyberte ze seznamu **povolená smyčka sítě** na stránce vlastností **ladění** možnost **ne** .

### <a name="optional-reinstall-the-app-when-you-start-debugging"></a><a name="BKMK__Optional__Reinstall_the_app_when_you_start_debugging"></a> Volitelné Přeinstalujte aplikaci při spuštění ladění.
 Chcete-li diagnostikovat problémy s instalací a počáteční konfigurací aplikace v jazyce Visual C# nebo Visual Basic, zvolte možnost **odinstalovat a poté opětovná instalace balíčku** na stránce vlastností **ladění**  , aby se při spuštění ladění znovu vytvořila původní instalace. Tato možnost není k dispozici pro Visual C++ projekty.

### <a name="optional-disable-authentication-requirement-to-start-the-remote-debugger"></a><a name="BKMK__Optional__Disable_authentication_requirement_to_start_the_remote_debugger"></a> Volitelné Zakázat požadavek na ověření pro spuštění vzdáleného ladicího programu
 ![Platí jenom pro Windows.](../debugger/media/windows-only-content.png "windows_only_content")

 Ve výchozím nastavení je nutné zadat přihlašovací údaje ke spuštění vzdáleného ladicího programu.

> [!IMPORTANT]
> Můžete zvolit spuštění vzdáleného ladicího programu v režimu bez ověřování, ale tento režim se důrazně nedoporučuje. Při spuštění v tomto režimu není žádné zabezpečení sítě. Na možnost Režim bez ověřování klikněte pouze v případě, že jste si jisti, že není síť ohrožena škodlivými nebo nevyžádanými daty.

 Postup odebrání požadavku na ověření:

1. V případě aplikací Visual C# a Visual Basic zrušte zaškrtnutí políčka **použít ověřování** na stránce vlastností **ladění** .

2. U Visual C++ch aplikací vyberte v seznamu **vyžadovat ověření** na stránce vlastností **ladění** možnost **ne** .

   [V tomto tématu](#BKMK_In_this_topic)

## <a name="start-the-debugging-session"></a><a name="BKMK_Start_the_debugging_session"></a> Spuštění relace ladění

### <a name="start-debugging-f5"></a><a name="BKMK_Start_debugging__F5_"></a> Spustit ladění (F5)
 Zvolíte-li možnost **Spustit ladění** (klávesnice: F5) v nabídce **ladění** , aplikace Visual Studio spustí aplikaci pomocí připojeného ladicího programu. Spuštění pokračuje, dokud není dosaženo zarážky, dojde k ručnímu pozastavení provádění, výskytu výjimky nebo ukončení aplikace.

### <a name="start-debugging-f5-but-delay-the-app-start"></a><a name="BKMK_Start_debugging__F5__but_delay_the_app_start"></a> Spustit ladění (F5), ale zpozdit začátek aplikace
 Aplikaci můžete nastavit tak, aby běžela v režimu ladění, ale spouštěla ji metodou jinou než ladicí program. Například můžete chtít ladit spuštění aplikace z nabídky Start nebo ladit proces na pozadí v aplikaci bez spuštění aplikace. Při zpoždění spuštění aplikace proveďte tento postup:

- Na stránce vlastností **ladění** aplikace (**ladění** v Visual C++)

  - Pro Visual C# a Visual Basic aplikace vyberte možnost **nespouštět, ale při spuštění ladit můj kód**.

  - U Visual C++ch aplikací vyberte v seznamu **Spustit aplikaci** možnost **Ano** .

- V nabídce **ladění** klikněte na příkaz **Spustit ladění** (klávesnice: F5).

- Spusťte aplikaci z nabídky Start, z prováděcí smlouvy nebo jiného postupu.

  Aplikace se spustí v režimu ladění. Spuštění pokračuje, dokud není dosaženo zarážky, ručním zastavením spuštění, neošetřené výjimky nebo ukončení aplikace.

  . Další informace o ladění úloh na pozadí naleznete v tématu [aktivační událost pozastavit, obnovit a události na pozadí pro Windows Store)](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md).

### <a name="start-an-installed-app-in-the-debugger"></a><a name="BKMK_Start_an_installed_app_in_the_debugger"></a> Spustit nainstalovanou aplikaci v ladicím programu
 Když spustíte ladění pomocí F5, sada Visual Studio sestaví a nasadí aplikaci, nastaví aplikaci tak, aby běžela v režimu ladění, a pak ji spustí. Pokud chcete spustit aplikaci, která je už na zařízení nainstalovaná, použijte dialogové okno ladit nainstalovaný balíček aplikace. Tento postup je užitečný v případě, že potřebujete ladit aplikaci, která byla nainstalovaná z Windows Storu, nebo když máte zdrojové soubory pro aplikaci, ale nemáte pro aplikaci Visual Studio projekt. Můžete mít například vlastní systém sestavení, který nepoužívá projekty nebo řešení sady Visual Studio.

 Aplikaci můžete nainstalovat na místní zařízení, nebo se může nacházet na vzdáleném zařízení.  Aplikaci můžete spustit hned, nebo ji můžete nastavit tak, aby běžela v ladicím programu, když je spuštěná jiným procesem nebo metodou, jako je například z nabídky Start nebo z kontraktu pro aktivaci, a pokud chcete ladit proces na pozadí bez spuštění aplikace, můžete také nastavit, aby se aplikace spouštěla v režimu ladění. Další informace najdete v tématu [triggery pro pozastavení, obnovení a události na pozadí pro Windows Store](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md).

 Chcete-li nastavit nainstalovanou aplikaci tak, aby běžela v režimu ladění, postupujte takto:

> [!NOTE]
> Aplikace nesmí být spuštěna při spuštění tohoto postupu.

1. V nabídce **ladění** vyberte **ladit nainstalovaný balíček aplikace** .

2. V seznamu vyberte jednu z následujících možností:

   |                    |                                                                                                                                                                                                                                                                                                                                                                                                           |
   |--------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   | **Místní počítač**  |                                                                                                                Ladit aplikaci v aktuální relaci na místním počítači. Viz [spuštění aplikací pro Windows Store na místním počítači](../debugger/run-windows-store-apps-on-the-local-machine.md).                                                                                                                 |
   |   **Simulátor**    | Ladit aplikaci v simulátoru sady Visual Studio pro [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] aplikace. Simulátor je okno plochy, které umožňuje ladění funkcí zařízení, jako jsou dotyková gesta a rotace zařízení, které nejsou k dispozici na místním počítači. Viz [spuštění aplikací pro Windows Store v simulátoru](../debugger/run-windows-store-apps-in-the-simulator.md). |
   | **Vzdálený počítač** |                          Ladit aplikaci na zařízení, které je připojené k místnímu počítači přes intranet nebo přímo připojené pomocí kabelu Ethernet. Chcete-li provést ladění vzdáleně, musí být na vzdáleném zařízení nainstalovány a spuštěny nástroje Visual Studio Remote Tools. Viz [spuštění aplikací pro Windows Store ve vzdáleném počítači](../debugger/run-windows-store-apps-on-a-remote-machine.md).                           |

3. Vyberte aplikaci ze seznamu **nainstalovaných balíčků aplikací** .

4. Vyberte ladicí stroj, který chcete použít, v seznamu **ladit tento typ kódu** .

5. (Volitelné). Vyberte možnost **nespouštět, ale ladit můj kód při spuštění** ladění aplikace, když je spuštěna jinou metodou, nebo pro ladění procesu na pozadí.

   Když kliknete na tlačítko **Start**, aplikace se spustí nebo se nastaví pro spuštění v režimu ladění.

### <a name="attach-the-debugger-to-a-running-app"></a><a name="BKMK_Attach_the_debugger_to_a_running_app_"></a> Připojení ladicího programu ke spuštěné aplikaci
 Chcete-li připojit ladicí program k [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] aplikaci, je nutné použít Správce balíčků, který lze ladit, a nastavit aplikaci tak, aby běžela v režimu ladění. Laděný správce balíčků se instaluje s nástroji Visual Studio Remote Tools.

 Připojení ladicího programu k aplikaci je užitečné v případě, že potřebujete ladit již nainstalovanou aplikaci, například aplikaci, která byla nainstalována z [!INCLUDE[win8_appstore_long](../includes/win8-appstore-long-md.md)] . Připojení se vyžaduje v případě, že máte zdrojové soubory aplikace, ale nemáte k dispozici projekt sady Visual Studio pro aplikaci. Můžete mít například vlastní systém sestavení, který nepoužívá projekty nebo řešení sady Visual Studio.

 Připojení ladicího programu k aplikaci vyžaduje tyto kroky:

1. Nastavte aplikaci tak, aby běžela v režimu ladění. To je potřeba udělat, když aplikace není spuštěná.

2. Spusťte aplikaci. Aplikaci můžete spustit z obrazovky Start, z prováděcí smlouvy nebo jiné metody.

3. Připojte ladicí program ke spuštěné aplikaci.

#### <a name="set-the-app-to-run-in-debug-mode"></a><a name="BKMK_Set_the_app_to_run_in_debug_mode"></a> Nastavení aplikace, která se má spustit v režimu ladění

1. Na zařízení, ve kterém je aplikace nainstalovaná, nainstalujte nástroje Visual Studio Remote Tools. Viz [Instalace nástrojů Remote Tools](https://msdn.microsoft.com/library/windows/apps/hh441469.aspx#BKMK_Installing_the_Remote_Tools).

2. Na obrazovce Start vyhledejte `Debuggable Package Manager` a spusťte ji.

     Zobrazí se okno PowerShellu správně nakonfigurované pro rutinu AppxDebug.

3. Pokud chcete povolit ladění aplikace, musíte zadat PackageFullName identifikátor aplikace. Pokud chcete zobrazit seznam všech aplikací, které obsahují PackageFullName, zadejte `Get-AppxPackage` na příkazovém řádku PowerShellu.

4. Na příkazovém řádku PowerShellu zadejte `Enable-AppxDebug` *PackageFullName* , kde *PackageFullName* je identifikátor PackageFullName aplikace.

#### <a name="attach-the-debugger"></a><a name="BKMK_Attach_the_debugger"></a> Připojit ladicí program
 Postup připojení ladicího programu:

1. V nabídce **ladění** vyberte možnost **připojit k procesu**.

    Zobrazí se dialogové okno **připojit k procesu** .

2. Pokud se chcete připojit k aplikaci na vzdáleném zařízení, zadejte vzdálené zařízení do pole **kvalifikátor** . Další možnosti:

   - Zadejte název do pole **kvalifikátor** .

   - Zvolte šipku dolů v poli **kvalifikátor** a pak zvolte zařízení ze seznamu zařízení, ke kterým jste se připojili.

   - Zvolte **Najít** , pokud chcete zařízení vybrat ze seznamu zařízení v místní podsíti.

3. V poli **připojit k** zadejte typ kódu, který chcete ladit.

    Zvolte **Vybrat** a pak proveďte jednu z následujících akcí:

   - Vyberte **automaticky určit typ kódu, který se má ladit** .

   - Zvolte možnost **ladit tyto typy kódu** a pak v seznamu vyberte jeden nebo více typů.

4. V seznamu **procesy k dispozici**  vyberte proces aplikace.

5. Klikněte na tlačítko **připojit**.

   Visual Studio připojí ladicí program k procesu. Spuštění pokračuje, dokud není dosaženo zarážky, ručním zastavením spuštění, neošetřené výjimky nebo ukončení aplikace.

   [V tomto tématu](#BKMK_In_this_topic)

## <a name="see-also"></a>Viz také
 [Ladění aplikací v aplikaci Visual Studio navigace v](../debugger/debug-store-apps-in-visual-studio.md) [ladicí relaci (XAML a C#)](../debugger/navigate-a-debugging-session-in-visual-studio-xaml-and-csharp.md)
