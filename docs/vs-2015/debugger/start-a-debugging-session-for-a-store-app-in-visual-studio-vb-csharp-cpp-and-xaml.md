---
title: Spuštění ladicí relace pro Store app (VB, C#, C++ a XAML) | Dokumentace Microsoftu
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
ms.openlocfilehash: f12d6cde30dec9062dd67a18558bd0571e6fe6b1
ms.sourcegitcommit: 3154387056160bf4c36ac8717a7fdc0cd9faf3f9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2020
ms.locfileid: "78409700"
---
# <a name="start-a-debugging-session-for-a-store-app-in-visual-studio-vb-c-c-and-xaml"></a>Spuštění ladicí relace pro Store app v sadě Visual Studio (VB, C#, C++ a XAML)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Platí pro Windows a Windows Phone] (.. /Image/windows_and_phone_content.png "windows_and_phone_content")

 Toto téma popisuje způsob spuštění ladicí relace pro Store aplikace napsané v XAML a Visual C++, Visual C# nebo Visual Basic. Ladění aplikace zahrnuje konfiguraci relace ladění i volba způsob, jak spustit aplikaci.

> [!NOTE]
> Pro aplikace napsané v JavaScriptu a HTML viz [spustit relaci ladění (JavaScript)](../debugger/start-a-debugging-session-for-store-apps-in-visual-studio-javascript.md).

## <a name="BKMK_In_this_topic"></a>V tomto tématu
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

## <a name="BKMK_The_easy_way_to_start_debugging"></a>Snadný způsob, jak spustit ladění

1. Otevřete aplikaci řešení v sadě Visual Studio.

2. Vyberte tlačítko F5.

   Visual Studio vytvoří a spustí aplikaci s připojeným ladícím nástrojem. Provádění pokračuje, dokud není dosaženo zarážky, můžete ručně pozastavení provádění, dojde k výjimce zrušení zpracování, nebo ukončení aplikace. Další informace najdete v tématu [Navigace v relaci ladění (XAML a C#)](../debugger/navigate-a-debugging-session-in-visual-studio-xaml-and-csharp.md) .

## <a name="BKMK_Configure_the_debugging_session"></a>Konfigurace relace ladění

### <a name="BKMK_Open_the_debugging_property_page_for_the_project"></a>Otevřete stránku vlastností ladění pro projekt.

1. V Průzkumníku řešení vyberte projekt. V místní nabídce vyberte možnost **vlastnosti**.

2. Proveďte to k otevření stránky vlastnosti ladění pro projekt:

    - Pro Visual C# a Visual Basic aplikace vyberte možnost **ladit**.

         ![Stránka&#35; &#47; vlastností ladění projektu jazyka C VB](../debugger/media/dbg-csvb-debugpropertypage.png "DBG_CsVb_DebugPropertyPage")

    - Pro Visual C++ aplikace rozbalte uzel **Vlastnosti konfigurace** a pak zvolte možnost **ladění**.

         ![Stránka&#43; &#43; vlastností ladění aplikace pro Windows Store v jazyce C](../debugger/media/dbg-cpp-debugpropertypage.png "DBG_CPP_DebugPropertyPage")

### <a name="BKMK_Choose_the_build_configuration_options"></a>Zvolit možnosti konfigurace sestavení

1. V seznamu **Konfigurace** vyberte **ladění** nebo **(aktivní) ladění**.

2. V seznamu **platforma** vyberte cílovou platformu, pro kterou chcete vytvořit. Ve většině případů je nejlepší volbou **Libovolný procesor** (**všechny platformy** v jazyce Visual C++).

### <a name="BKMK_Choose_the_deployment_target"></a>Zvolit cíl nasazení
 ![Platí jenom pro Windows.](../debugger/media/windows-only-content.png "windows_only_content")

 Můžete nasadit a ladit aplikace Windows Store na počítač s Visual Studio, simulátoru sady Visual Studio na místním počítači nebo na vzdáleném zařízení.

- Pro C# aplikace a Visual Basic vyberte cíl ze seznamu **cílové zařízení** na stránce vlastností **ladění** projektu.

- Pro C++ aplikace vyberte cíl ze seznamu **Spustit ladicí program** na stránce vlastností **ladění** :

  Vyberte jednu z těchto možností:

|||
|-|-|
|**Místní počítač**|Ladění aplikace v aktuální relaci na místním počítači. Viz [spuštění aplikací pro Windows Store na místním počítači](../debugger/run-windows-store-apps-on-the-local-machine.md).|
|**Simulátor**|Ladit aplikaci v simulátoru sady Visual Studio pro aplikace [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)]. Simulátor není okno klasické pracovní plochy, která umožňuje ladit funkce zařízení, jako je například gesta dotykového ovládání a otočení obrazovky –, které nejsou k dispozici v místním počítači. Viz [spuštění aplikací pro Windows Store v simulátoru](../debugger/run-windows-store-apps-in-the-simulator.md).|
|**Vzdálený počítač**|Ladění aplikací na zařízení, který je připojený k místním počítači v síti intranet nebo přímo pomocí kabelu Ethernet. Pro vzdálené ladění, vzdálené nástroje sady Visual Studio musí být nainstalovaná a spuštěná na vzdáleném zařízení. Viz [spuštění aplikací pro Windows Store ve vzdáleném počítači](../debugger/run-windows-store-apps-on-a-remote-machine.md).|

 Pokud zvolíte možnost **vzdálený počítač**, zadejte název nebo IP adresu vzdáleného počítače jedním z následujících způsobů:

- Zadejte název nebo IP adresu vzdáleného počítače.

  - Pro C# aplikace a Visual Basic zadejte název nebo IP adresu do pole **vzdálený počítač** .

  - Do C++ pole **název počítače** zadejte název nebo IP adresu pro aplikace.

- V dialogovém okně **Vybrat připojení vzdáleného ladicího programu** zvolte vzdálený počítač.

   Chcete-li otevřít dialogové okno:

  - Pro C# aplikace a Visual Basic vyberte **Najít**.

  - V C++ případě aplikací klikněte na šipku dolů v poli **název počítače** a vyberte **\<najít... >** .

    ![Dialogové okno vybrat připojení vzdáleného ladicího programu](../debugger/media/vsrun-selectremotedebuggerdlg.png "VSRUN_SelectRemoteDebuggerDlg")

  > [!NOTE]
  > V dialogovém okně **Vybrat připojení vzdáleného ladicího programu** se zobrazí počítače, které jsou v místní podsíti a počítače, které jsou přímo připojené k počítači sady Visual Studio pomocí kabelu Ethernet. Pokud chcete zadat jiný počítač, zadejte název do pole **název počítače** .

  ![Platí jenom pro Windows Phone](../debugger/media/phone-only-content.png "phone_only_content")

  Můžete nasadit a ladit aplikace Windows Phone Store na zařízení nebo na serveru, emulátory phone sady Visual Studio. V seznamu **cílové zařízení** vyberte zařízení nebo emulátor.

### <a name="BKMK_Choose_the_debugger_to_use"></a>Vyberte ladicí program, který se má použít.
 Ve výchozím nastavení Visual Studio ladí spravovaného kódu v aplikacích jazyka C# a Visual Basic.

 Pro aplikace C# a Visual Basic můžete ladit jak spravovaný a nativní kód C/C++ v aplikaci. Zaškrtněte políčko **Povolit ladění nespravovaného kódu** pro zahrnutí nativního kódu do relace ladění.

 Ve výchozím nastavení Visual Studio ladí nativního kódu v aplikaci C++.

 Pro aplikace v C++ můžete ladit konkrétní typy kódu, které jsou součástí vaší aplikace, místo nebo kromě nativní kód. Kód, který chcete ladit, určíte v seznamu **Typ ladicího programu** na stránce vlastností **ladění** projektu aplikace.

 V seznamu **aplikačních procesů** vyberte jeden z těchto ladicích programů:

|||
|-|-|
|**Pouze skript**|Ladění kódu JavaScript ve vaší aplikaci. Nativní a spravovaný kód jsou ignorovány.|
|**Pouze nativní**|Ladění nativního kódu C/C++ v aplikaci. Spravovaný kód a kód jazyka JavaScript jsou ignorovány.|
|**Jenom spravovaná**|Ladit spravovaný kód ve vaší aplikaci. Kód jazyka JavaScript a nativního kódu C/C++ jsou ignorovány.|
|**Smíšený (spravovaný a nativní)**|Ladění nativního kódu C/C++ a spravovaném kódu ve vaší aplikaci. Kód jazyka JavaScript se ignoruje.|
|**Pouze GPU**|Ladění nativního kódu C++, na které poběží grafický procesor (GPU).|

 ![Platí jenom pro Windows Phone](../debugger/media/phone-only-content.png "phone_only_content")

 Pro aplikace Windows Store Phone můžete také zvolit ladicí program, který se má použít pro procesy na pozadí z **procesu úlohy na pozadí**.

### <a name="BKMK__Optional__Delay_starting_the_debug_session"></a>Volitelné Zpoždění spuštění relace ladění
 Ve výchozím nastavení spustí aplikace Visual Studio okamžitě aplikace při spuštění ladění. Můžete také spustit relaci ladění, ale zpoždění spuštění vaší aplikace. Když vyberete tuto možnost, spuštění aplikace v ladicím programu při jeho spuštění na obrazovce Start nebo kliknutím kontrakt aktivace nebo při spuštění jiným procesem nebo metody. Také zpozdíte spuštění vaší aplikace, pokud chcete ladit úlohu na pozadí, když se aplikace.

 Chcete-li zpoždění spuštění vaší aplikace, můžete:

- Pro Visual C# a Visual Basic aplikace vyberte možnost **nespouštět, ale ladit můj kód při spuštění** na stránce vlastností **ladění** .

- V případě C++ vizuálních aplikací vyberte v seznamu **Spustit aplikaci** na stránce vlastností **ladění** možnost **Ano** .

### <a name="BKMK__Optional__Disable_network_loopbacks"></a>Volitelné Zakázat zpětné smyčky sítě
 ![Platí jenom pro Windows.](../debugger/media/windows-only-content.png "windows_only_content")

 Z bezpečnostních důvodů aplikace Windows Store, nainstalovaný ve standardním způsobem nepovoluje volat síťových zařízení, ve kterých je nainstalované. Ve výchozím nastavení nasazení sady Visual Studio vytvoří výjimku z tohoto pravidla pro aplikace nasazené. Tato výjimka umožňuje testovat postupy komunikace na jednom počítači. Před odesláním aplikace do Windows Store, měli byste otestovat vaši aplikaci bez výjimky.

 Chcete-li odebrat výjimku zpětnou smyčku sítě:

- U aplikací C# Visual a Visual Basic zrušte zaškrtnutí políčka **Povolení zpětné smyčky sítě** na stránce vlastností **ladění** .

- V případě C++ vizuálních aplikací vyberte ze seznamu **povolená smyčka sítě** na stránce vlastností **ladění** možnost **ne** .

### <a name="BKMK__Optional__Reinstall_the_app_when_you_start_debugging"></a>Volitelné Přeinstalujte aplikaci při spuštění ladění.
 Chcete-li diagnostikovat problémy s instalací a počáteční konfigurací vaší C# aplikace nebo aplikace Visual Basic, zvolte možnost **odinstalovat a poté opětovná instalace balíčku** na stránce vlastností **ladění** , aby se při spuštění ladění znovu vytvořila původní instalace. Tato možnost není k dispozici pro projekty Visual C++.

### <a name="BKMK__Optional__Disable_authentication_requirement_to_start_the_remote_debugger"></a>Volitelné Zakázat požadavek na ověření pro spuštění vzdáleného ladicího programu
 ![Platí jenom pro Windows.](../debugger/media/windows-only-content.png "windows_only_content")

 Ve výchozím nastavení musíte zadat přihlašovací údaje ke spuštění vzdáleného ladicího programu.

> [!IMPORTANT]
> Můžete také spustit vzdálený ladicí program v režimu bez ověřování, ale tento režim se rozhodně nedoporučuje. Při spuštění v tomto režimu není žádné zabezpečení sítě. Na možnost Režim bez ověřování klikněte pouze v případě, že jste si jisti, že není síť ohrožena škodlivými nebo nevyžádanými daty.

 Chcete-li odebrat požadavek na ověření:

1. U vizuálů C# a Visual Basic aplikací zrušte zaškrtnutí políčka **použít ověřování** na stránce vlastností **ladění** .

2. V případě C++ vizuálních aplikací vyberte v seznamu **vyžadovat ověření** na stránce vlastností **ladění** možnost **ne** .

   [V tomto tématu](#BKMK_In_this_topic)

## <a name="BKMK_Start_the_debugging_session"></a>Spuštění relace ladění

### <a name="BKMK_Start_debugging__F5_"></a>Spustit ladění (F5)
 Zvolíte-li možnost **Spustit ladění** (klávesnice: F5) v nabídce **ladění** , aplikace Visual Studio spustí aplikaci pomocí připojeného ladicího programu. Provádění pokračuje, dokud není dosaženo zarážky, můžete ručně pozastavení provádění, dojde k výjimce nebo ukončení aplikace.

### <a name="BKMK_Start_debugging__F5__but_delay_the_app_start"></a>Spustit ladění (F5), ale zpozdit začátek aplikace
 Můžete nastavit aplikaci spustit v režimu ladění, ale spusťte ji pomocí jiné metody než ladicí program. Můžete například, chcete-li ladit spuštění vaší aplikace z nabídky Start nebo chcete-li ladit proces na pozadí v aplikaci bez spuštění aplikace. Chcete-li zpoždění spuštění aplikace, postupujte takto:

- Na stránce vlastností **ladění** aplikace (**ladění** v vizuálu C++)

  - U vizuálů C# a Visual Basic aplikací vyberte možnost **nespouštět, ale při spuštění ladit můj kód**.

  - V případě C++ vizuálních aplikací vyberte v seznamu **Spustit aplikaci** možnost **Ano** .

- V nabídce **ladění** klikněte na příkaz **Spustit ladění** (klávesnice: F5).

- Aplikaci spusťte z nabídky Start, kontrakt provádění nebo jiný postup.

  Spuštění aplikace v režimu ladění. Provádění pokračuje, dokud není dosaženo zarážky, můžete ručně pozastavení provádění, dojde k neošetřené výjimce nebo ukončení aplikace.

  . Další informace o ladění úloh na pozadí naleznete v tématu [aktivační událost pozastavit, obnovit a události na pozadí pro Windows Store)](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md).

### <a name="BKMK_Start_an_installed_app_in_the_debugger"></a>Spustit nainstalovanou aplikaci v ladicím programu
 Při spuštění ladění pomocí F5, Visual Studio vytvoří a nasadí aplikaci, nastaví aplikaci spustit v režimu ladění a pak spustí. Chcete-li spustit aplikaci, která je již nainstalována v zařízení, použijte dialogové okno ladit nainstalovaný balíček aplikace. Tento postup je užitečný, když budete chtít ladit aplikaci, která byla nainstalovaná z Windows storu nebo, pokud mají zdrojové soubory pro aplikaci, ale není nutné projekt sady Visual Studio pro aplikaci. Například může mít vlastní sestavovací systém, který nepoužívá projektů sady Visual Studio nebo řešení.

 Aplikaci můžete nainstalovat na místním zařízení, nebo může být na vzdáleném zařízení.  Aplikaci můžete spustit okamžitě, nebo můžete nastavit jeho spouštění v ladicím programu při spuštění jiným procesem nebo metody, například z nabídky Start nebo kontrakt aktivace, můžete také nastavit aplikaci spustit v režimu ladění, když chcete ladit proces na pozadí bez spuštění aplikace. Další informace najdete v tématu [triggery pro pozastavení, obnovení a události na pozadí pro Windows Store](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md).

 Chcete-li nastavit nainstalovanou aplikaci pro spuštění v režimu ladění, postupujte takto:

> [!NOTE]
> Když spustíte tento postup, nesmí být spuštěná aplikace.

1. V nabídce **ladění** vyberte **ladit nainstalovaný balíček aplikace** .

2. Ze seznamu vyberte jednu z následujících možností:

   |                    |                                                                                                                                                                                                                                                                                                                                                                                                           |
   |--------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   | **Místní počítač**  |                                                                                                                Ladění aplikace v aktuální relaci na místním počítači. Viz [spuštění aplikací pro Windows Store na místním počítači](../debugger/run-windows-store-apps-on-the-local-machine.md).                                                                                                                 |
   |   **Simulátor**    | Ladit aplikaci v simulátoru sady Visual Studio pro aplikace [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)]. Simulátor není okno klasické pracovní plochy, která umožňuje ladit funkce zařízení, jako je například gesta dotykového ovládání a otočení obrazovky –, které nejsou k dispozici v místním počítači. Viz [spuštění aplikací pro Windows Store v simulátoru](../debugger/run-windows-store-apps-in-the-simulator.md). |
   | **Vzdálený počítač** |                          Ladění aplikací na zařízení, který je připojený k místním počítači v síti intranet nebo přímo pomocí kabelu Ethernet. Pro vzdálené ladění, vzdálené nástroje sady Visual Studio musí být nainstalovaná a spuštěná na vzdáleném zařízení. Viz [spuštění aplikací pro Windows Store ve vzdáleném počítači](../debugger/run-windows-store-apps-on-a-remote-machine.md).                           |

3. Vyberte aplikaci ze seznamu **nainstalovaných balíčků aplikací** .

4. Vyberte ladicí stroj, který chcete použít, v seznamu **ladit tento typ kódu** .

5. (Volitelné). Vyberte možnost **nespouštět, ale ladit můj kód při spuštění** ladění aplikace, když je spuštěna jinou metodou, nebo pro ladění procesu na pozadí.

   Když kliknete na tlačítko **Start**, aplikace se spustí nebo se nastaví pro spuštění v režimu ladění.

### <a name="BKMK_Attach_the_debugger_to_a_running_app_"></a>Připojení ladicího programu ke spuštěné aplikaci
 Chcete-li připojit ladicí program k aplikaci [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)], je nutné použít Správce balíčků, který lze ladit, a nastavit aplikaci tak, aby běžela v režimu ladění. Laditelný Správce balíčků je nainstalované s Visual Studio Remote Tools.

 Připojení ladicího programu k aplikaci je užitečné v případě, že potřebujete ladit už nainstalovanou aplikaci, například aplikaci, která byla nainstalovaná z [!INCLUDE[win8_appstore_long](../includes/win8-appstore-long-md.md)]. Připojení se vyžaduje, pokud mají zdrojové soubory pro aplikaci, ale není nutné projekt sady Visual Studio pro aplikaci. Například může mít vlastní sestavovací systém, který nepoužívá projektů sady Visual Studio nebo řešení.

 Připojování ladicího programu do aplikace vyžaduje tyto kroky:

1. Nastavte aplikaci spustit v režimu ladění. To je nutné provést při není aplikace spuštěna.

2. Spusťte aplikaci. Aplikaci můžete spustit z úvodní obrazovky, kontrakt provádění nebo některé jiné metody.

3. Připojte ladicí modul k běžící aplikaci.

#### <a name="BKMK_Set_the_app_to_run_in_debug_mode"></a>Nastavení aplikace, která se má spustit v režimu ladění

1. Nainstalujte na zařízení nainstalovanou aplikaci Visual Studio Remote Tools. Viz [Instalace nástrojů Remote Tools](https://msdn.microsoft.com/library/windows/apps/hh441469.aspx#BKMK_Installing_the_Remote_Tools).

2. Na obrazovce Start vyhledejte `Debuggable Package Manager` a pak ho spusťte.

     Zobrazí se okno prostředí PowerShell správně nakonfigurovaný pro rutiny AppxDebug.

3. Pokud chcete povolit ladění aplikace, je nutné zadat identifikátor Úplnýnázevbalíčku aplikace. Pokud chcete zobrazit seznam všech aplikací, které obsahují PackageFullName, zadejte do příkazového řádku PowerShellu `Get-AppxPackage`.

4. Na příkazovém řádku PowerShellu zadejte `Enable-AppxDebug` *PackageFullName* , kde *PackageFullName* je identifikátor PackageFullName aplikace.

#### <a name="BKMK_Attach_the_debugger"></a>Připojit ladicí program
 Připojení ladicího programu:

1. V nabídce **ladění** vyberte možnost **připojit k procesu**.

    Zobrazí se dialogové okno **připojit k procesu** .

2. Pokud se chcete připojit k aplikaci na vzdáleném zařízení, zadejte vzdálené zařízení do pole **kvalifikátor** . Můžete:

   - Zadejte název do pole **kvalifikátor** .

   - Zvolte šipku dolů v poli **kvalifikátor** a pak zvolte zařízení ze seznamu zařízení, ke kterým jste se připojili.

   - Zvolte **Najít** , pokud chcete zařízení vybrat ze seznamu zařízení v místní podsíti.

3. V poli **připojit k** zadejte typ kódu, který chcete ladit.

    Zvolte **Vybrat** a pak proveďte jednu z následujících akcí:

   - Vyberte **automaticky určit typ kódu, který se má ladit** .

   - Zvolte možnost **ladit tyto typy kódu** a pak v seznamu vyberte jeden nebo více typů.

4. V seznamu **procesy k dispozici** vyberte proces aplikace.

5. Klikněte na tlačítko **připojit**.

   Visual Studio připojí ladicí program k procesu. Provádění pokračuje, dokud není dosaženo zarážky, můžete ručně pozastavení provádění, dojde k neošetřené výjimce nebo ukončení aplikace.

   [V tomto tématu](#BKMK_In_this_topic)

## <a name="see-also"></a>Viz také
 [Ladění aplikací v aplikaci Visual Studio navigace v](../debugger/debug-store-apps-in-visual-studio.md) [relaci ladění (XAML C#a)](../debugger/navigate-a-debugging-session-in-visual-studio-xaml-and-csharp.md)
