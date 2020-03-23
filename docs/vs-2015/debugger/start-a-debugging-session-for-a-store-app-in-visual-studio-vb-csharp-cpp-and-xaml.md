---
title: Spuštění relace ladění pro aplikaci pro Store (VB, C#, C++ a XAML) | Dokumenty společnosti Microsoft
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
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/13/2020
ms.locfileid: "79302474"
---
# <a name="start-a-debugging-session-for-a-store-app-in-visual-studio-vb-c-c-and-xaml"></a>Spuštění ladicí relace pro aplikaci pro Store v sadě Visual Studio (jazyk Visual Basic, C#, C++ a XAML)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Platí pro Windows a Windows Phone](.. /Obrázek/windows_and_phone_content.png "windows_and_phone_content")

 Toto téma popisuje, jak spustit relaci ladění pro aplikace pro Store napsané v XAML a Visual C++, Visual C# nebo Visual Basic. Ladění aplikace zahrnuje konfiguraci relace ladění a výběr způsobu spuštění aplikace.

> [!NOTE]
> Aplikace napsané v Jazyce JavaScript a HTML najdete v [tématu Spuštění ladicí relace (JavaScript).](../debugger/start-a-debugging-session-for-store-apps-in-visual-studio-javascript.md)

## <a name="in-this-topic"></a><a name="BKMK_In_this_topic"></a>V tomto tématu
 [Snadný způsob, jak začít ladit](#BKMK_The_easy_way_to_start_debugging)

 [Konfigurace relace ladění](#BKMK_Configure_the_debugging_session)

- [Otevření stránky vlastností ladění pro projekt](#BKMK_Open_the_debugging_property_page_for_the_project)

- [Výběr možností konfigurace sestavení](#BKMK_Choose_the_build_configuration_options)

- [Výběr cíle nasazení](#BKMK_Choose_the_deployment_target)

- [Vyberte ladicí program, který chcete použít.](#BKMK_Choose_the_debugger_to_use)

- [(Nepovinné) Zpoždění při zahájení relace ladění](#BKMK__Optional__Delay_starting_the_debug_session)

- [(Nepovinné) Zakázání síťových zpěticích smyček](#BKMK__Optional__Disable_network_loopbacks)

- [(Nepovinné) Přeinstalace aplikace při spuštění ladění](#BKMK__Optional__Reinstall_the_app_when_you_start_debugging)

- [(Nepovinné) Zakázání požadavku na ověření pro spuštění vzdáleného ladicího programu](#BKMK__Optional__Disable_authentication_requirement_to_start_the_remote_debugger)

  [Spuštění relace ladění](#BKMK_Start_the_debugging_session)

- [Zahájení ladění (F5)](#BKMK_Start_debugging__F5_)

- [Spuštění ladění (F5), ale zpoždění spuštění aplikace](#BKMK_Start_debugging__F5__but_delay_the_app_start)

- [Spuštění nainstalované aplikace v ladicím programu](#BKMK_Start_an_installed_app_in_the_debugger)

- [Připojení ladicího programu ke spuštěné aplikaci](#BKMK_Attach_the_debugger_to_a_running_app_)

  - [Nastavení spuštění aplikace v režimu ladění](#BKMK_Set_the_app_to_run_in_debug_mode)

  - [Připojit ladicí program](#BKMK_Attach_the_debugger)

## <a name="the-easy-way-to-start-debugging"></a><a name="BKMK_The_easy_way_to_start_debugging"></a>Snadný způsob, jak začít ladit

1. Otevřete řešení aplikace v Sadě Visual Studio.

2. Zvolte F5.

   Visual Studio vytvoří a spustí aplikaci s připojeným ladicím programem. Spuštění pokračuje, dokud je dosaženo zarážky, ručně pozastavit provádění, dojde k nezpracované výjimce nebo ukončení aplikace. Další informace naleznete [v tématu Navigate relace ladění (Xaml a C#)](../debugger/navigate-a-debugging-session-in-visual-studio-xaml-and-csharp.md) .

## <a name="configure-the-debugging-session"></a><a name="BKMK_Configure_the_debugging_session"></a>Konfigurace relace ladění

### <a name="open-the-debugging-property-page-for-the-project"></a><a name="BKMK_Open_the_debugging_property_page_for_the_project"></a>Otevření stránky vlastností ladění pro projekt

1. V Průzkumníku řešení vyberte projekt. V místní nabídce zvolte **Vlastnosti**.

2. Chcete-li otevřít stránku vlastností ladění projektu :

    - Pro aplikace Visual C# a Visual Basic zvolte **Ladění**.

         ![Stránka vlastností vlastností ladění projektu C&#35; &#47; VB](../debugger/media/dbg-csvb-debugpropertypage.png "DBG_CsVb_DebugPropertyPage")

    - U aplikací Visual C++ rozbalte uzel **Vlastnosti konfigurace** a pak zvolte **Ladění**.

         ![Stránka vlastností vlastností aplikace Pro Windows Store&#43;&#43; Windows Store](../debugger/media/dbg-cpp-debugpropertypage.png "DBG_CPP_DebugPropertyPage")

### <a name="choose-the-build-configuration-options"></a><a name="BKMK_Choose_the_build_configuration_options"></a>Výběr možností konfigurace sestavení

1. V seznamu **Konfigurace** zvolte **Ladění** nebo **(Aktivní) Ladění**.

2. Ze seznamu **Platforma** vyberte cílovou platformu, pro kterou chcete vytvořit. Ve většině případů **všechny procesory** **(všechny platformy** v jazyce Visual C++) je nejlepší volbou.

### <a name="choose-the-deployment-target"></a><a name="BKMK_Choose_the_deployment_target"></a>Výběr cíle nasazení
 ![Platí pouze pro Windows](../debugger/media/windows-only-content.png "windows_only_content")

 Aplikaci pro Windows Store můžete nasadit a ladit na počítači SAG, v simulátoru Visual Studia na místním počítači nebo na vzdáleném zařízení.

- Pro aplikace jazyka C# a Visual Basic zvolte cíl ze seznamu **Cílové zařízení** na stránce vlastností **Ladění** pro projekt.

- Pro aplikace jazyka C++ zvolte cíl ze seznamu **debuggeru a spusťte** seznam na stránce **vlastností Ladění:**

  Zvolte jednu z těchto možností:

|||
|-|-|
|**Místní počítač**|Ladění aplikace v aktuální relaci v místním počítači. Viz [Spuštění aplikací pro Windows Store na místním počítači](../debugger/run-windows-store-apps-on-the-local-machine.md).|
|**Simulátor**|Ladění aplikace v simulátoru Visual [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] Studio pro aplikace. Simulátor je okno plochy, které umožňuje ladit funkce zařízení , které nejsou k dispozici v místním počítači. Viz [Spuštění aplikací pro Windows Store v simulátoru](../debugger/run-windows-store-apps-in-the-simulator.md).|
|**Vzdálený stroj**|Ladění aplikace na zařízení, které je připojeno k místnímu počítači přes intranet nebo přímo připojené pomocí ethernetového kabelu. Chcete-li ladit vzdáleně, vzdálené nástroje sady Visual Studio musí být nainstalovány a spuštěny na vzdáleném zařízení. Viz [Spouštění aplikací pro Windows Store na vzdáleném počítači](../debugger/run-windows-store-apps-on-a-remote-machine.md).|

 Pokud zvolíte **vzdálený počítač**, zadejte název nebo IP adresu vzdáleného počítače jedním z těchto způsobů:

- Zadejte název nebo IP adresu vzdáleného počítače.

  - Pro aplikace jazyka C# a Visual Basic zadejte název nebo ADRESU IP do pole **Vzdálený počítač.**

  - Pro aplikace c++ zadejte název nebo IP adresu do pole **Název počítače.**

- Zvolte vzdálený počítač z dialogového okna **Vybrat vzdálené připojení ladicího programu.**

   Otevření dialogového okna:

  - Pro aplikace C# a Visual Basic zvolte **Najít**.

  - U aplikací pro C++ zvolte šipku dolů v poli **Název počítače** a zvolte ** \<Vyhledat...>**.

    ![Dialogové okno Vybrat vzdálené připojení ladicího programu](../debugger/media/vsrun-selectremotedebuggerdlg.png "VSRUN_SelectRemoteDebuggerDlg")

  > [!NOTE]
  > Dialogové okno **Vybrat vzdálené připojení ladicího programu** zobrazuje počítače, které jsou v místní podsíti, a počítače, které jsou přímo připojeny k počítači Visual Studio pomocí ethernetového kabelu. Chcete-li zadat jiný počítač, zadejte název do pole **Název počítače.**

  ![Platí pouze pro Windows Phone.](../debugger/media/phone-only-content.png "phone_only_content")

  Aplikaci pro Windows Phone Store můžete nasadit a ladit na zařízení nebo v jednom z emulátorů telefonu Visual Studio. Vyberte zařízení nebo emulátor ze seznamu **Cílové zařízení.**

### <a name="choose-the-debugger-to-use"></a><a name="BKMK_Choose_the_debugger_to_use"></a>Vyberte ladicí program, který chcete použít.
 Ve výchozím nastavení Visual Studio debugs spravovaný kód v jazyce C# a visual basic aplikace.

 Pro aplikace jazyka C# a Visual Basic můžete ladit spravovaný i nativní kód C/C++ ve vaší aplikaci. Zaškrtněte políčko **Povolit ladění nespravovaného kódu,** chcete-li do relace ladění zahrnout nativní kód.

 Ve výchozím nastavení Visual Studio odvápne nativní kód ve vaší aplikaci C++.

 Pro aplikace c++ můžete ladit konkrétní typy kódu, které jsou v součástech vaší aplikace namísto nebo kromě nativního kódu. Kód pro ladění zadáte v seznamu **Typ ladicího programu** na stránce **vlastností ladění** projektu aplikace.

 Vyberte jeden z těchto ladicích programů ze seznamu **Proces aplikace:**

|||
|-|-|
|**Pouze skript**|Ladění kódu JavaScript ve vaší aplikaci. Spravovaný kód a nativní kód jsou ignorovány.|
|**Pouze nativní**|Ladění nativního kódu C/C++ ve vaší aplikaci. Spravovaný kód a kód JavaScript jsou ignorovány.|
|**Pouze spravované**|Ladění spravovaného kódu ve vaší aplikaci. Kód JavaScripta a nativní kód C/C++ jsou ignorovány.|
|**Smíšené (spravované a nativní)**|Ladění nativního kódu C/C++ a spravovaného kódu ve vaší aplikaci. Kód JavaScriptu je ignorován.|
|**Pouze GPU**|Ladění nativního kódu Jazyka C++, který běží na grafické procesorové jednotce (GPU).|

 ![Platí pouze pro Windows Phone.](../debugger/media/phone-only-content.png "phone_only_content")

 U aplikací pro Windows Store Phone můžete také zvolit ladicí program, který se má použít pro procesy na pozadí z **procesu úlohy na pozadí**.

### <a name="optional-delay-starting-the-debug-session"></a><a name="BKMK__Optional__Delay_starting_the_debug_session"></a>(Nepovinné) Zpoždění při zahájení relace ladění
 Ve výchozím nastavení Visual Studio okamžitě spustí aplikaci při spuštění ladění. Můžete také spustit relaci ladění, ale zpozdit spuštění aplikace. Pokud zvolíte tuto možnost, aplikace se spustí v ladicím programu při spuštění z úvodní obrazovky nebo aktivační smlouvy nebo při spuštění jiným procesem nebo metodou. Také zpoždění spuštění aplikace, pokud chcete ladit úlohu na pozadí, když samotná aplikace není spuštěna.

 Chcete-li odložit spuštění aplikace, můžete:

- Pro aplikace Visual C# a Visual Basic vyberte **Nespouštět, ale ladit můj kód při spuštění** na stránce **vlastnosti ladění.**

- Pro aplikace Visual C++ zvolte **Ano** ze seznamu **Spustit aplikaci** na stránce **vlastností Ladění.**

### <a name="optional-disable-network-loopbacks"></a><a name="BKMK__Optional__Disable_network_loopbacks"></a>(Nepovinné) Zakázání síťových zpěticích smyček
 ![Platí pouze pro Windows](../debugger/media/windows-only-content.png "windows_only_content")

 Z bezpečnostních důvodů není aplikace pro Windows Store, která je nainstalována standardním způsobem, povolena pro volání do sítě zařízení, na které je nainstalovaná. Ve výchozím nastavení nasazení visual studia vytvoří výjimku z tohoto pravidla pro nasazenou aplikaci. Tato výjimka umožňuje testovat komunikační postupy na jednom počítači. Než aplikaci odešlete do Windows Storu, měli byste ji otestovat bez výjimky.

 Odebrání výjimky zpětné smyčky sítě:

- U aplikací Visual C# a Visual Basic zrušte zaškrtnutí políčka **Povolit síťovou zpětnou vazbu** na stránce vlastností **Ladění.**

- Pro aplikace Visual C++ zvolte **Ne** ze seznamu **Povolit síťovou zpětnou vazbu** na stránce **vlastností Ladění.**

### <a name="optional-reinstall-the-app-when-you-start-debugging"></a><a name="BKMK__Optional__Reinstall_the_app_when_you_start_debugging"></a>(Nepovinné) Přeinstalace aplikace při spuštění ladění
 Chcete-li diagnostikovat problémy s instalací a počáteční konfigurací aplikace Visual C# nebo Visual Basic, zvolte **Odinstalovat a znovu nainstalovat balíček** na stránce **vlastnosti Ladění** znovu vytvořit původní instalaci při spuštění ladění. Tato možnost není k dispozici pro projekty visual c++.

### <a name="optional-disable-authentication-requirement-to-start-the-remote-debugger"></a><a name="BKMK__Optional__Disable_authentication_requirement_to_start_the_remote_debugger"></a>(Nepovinné) Zakázání požadavku na ověření pro spuštění vzdáleného ladicího programu
 ![Platí pouze pro Windows](../debugger/media/windows-only-content.png "windows_only_content")

 Ve výchozím nastavení je nutné zadat pověření pro spuštění vzdáleného ladicího programu.

> [!IMPORTANT]
> Vzdálený ladicí program můžete spustit v režimu Bez ověřování, ale tento režim se důrazně nedoporučuje. Při spuštění v tomto režimu není žádné zabezpečení sítě. Na možnost Režim bez ověřování klikněte pouze v případě, že jste si jisti, že není síť ohrožena škodlivými nebo nevyžádanými daty.

 Odebrání požadavku na ověření:

1. U aplikací Visual C# a Visual Basic zrušte zaškrtnutí políčka **Použít ověřování** na stránce vlastností **Ladění.**

2. U aplikací Visual C++ zvolte **Ne** ze seznamu **Vyžadovat ověření** na stránce **vlastností Ladění.**

   [V tomto tématu](#BKMK_In_this_topic)

## <a name="start-the-debugging-session"></a><a name="BKMK_Start_the_debugging_session"></a>Spuštění relace ladění

### <a name="start-debugging-f5"></a><a name="BKMK_Start_debugging__F5_"></a>Zahájení ladění (F5)
 Když v nabídce **Ladění** zvolíte **Spustit ladění** (Klávesnice: F5), Visual Studio spustí aplikaci s připojeným ladicím programem. Spuštění pokračuje, dokud je dosaženo zarážky, ručně pozastavit provádění, dojde k výjimce nebo ukončení aplikace.

### <a name="start-debugging-f5-but-delay-the-app-start"></a><a name="BKMK_Start_debugging__F5__but_delay_the_app_start"></a>Spuštění ladění (F5), ale zpoždění spuštění aplikace
 Můžete nastavit aplikaci spustit v režimu ladění, ale spustit ji metodou jinou metodu než ladicí program. Můžete například chtít ladit spuštění aplikace z nabídky Start nebo ladit proces na pozadí v aplikaci bez spuštění aplikace. Chcete-li odložit spuštění aplikace, udělejte toto:

- Na stránce **vlastností Ladění** aplikace **(Ladění** ve Visual C++)

  - Pro aplikace Visual C# a Visual Basic zvolte **Nespouštět, ale ladit můj kód při spuštění**.

  - Pro aplikace Visual C++ zvolte **Ano** ze seznamu **Spouštět aplikace.**

- V nabídce **Ladění** zvolte **Spustit ladění** (Klávesnice: F5).

- Spusťte aplikaci z nabídky Start, smlouvy o provedení nebo jiným postupem.

  Aplikace se spustí v režimu ladění. Spuštění pokračuje, dokud je dosaženo zarážky, ručně pozastavit provádění, dojde k neošetřené výjimce nebo ukončení aplikace.

  . Další informace o ladění úloh na pozadí najdete [v tématu Trigger suspend, resume a background events for Windows Store).](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md)

### <a name="start-an-installed-app-in-the-debugger"></a><a name="BKMK_Start_an_installed_app_in_the_debugger"></a>Spuštění nainstalované aplikace v ladicím programu
 Když začnete ladění pomocí F5, Visual Studio vytvoří a nasadí aplikaci, nastaví aplikaci spustit v režimu ladění a pak ji spustí. Chcete-li spustit aplikaci, která je již nainstalovaná v zařízení, použijte dialogové okno Balíček nainstalované aplikace ladění. Tento postup je užitečný, když potřebujete ladit aplikaci, která byla nainstalovaná z Windows Store, nebo když máte zdrojové soubory pro aplikaci, ale nemáte projekt Visual Studio pro aplikaci. Můžete mít například vlastní systém sestavení, který nepoužívá projekty nebo řešení sady Visual Studio.

 Aplikace může být nainstalována na místním zařízení nebo může být na vzdáleném zařízení.  Aplikaci můžete spustit okamžitě, nebo ji můžete nastavit tak, aby se spustila v ladicím programu, když je spuštěna jiným procesem nebo metodou, například z nabídky Start nebo aktivační smlouvy, Můžete také nastavit spuštění aplikace v režimu ladění, když chcete ladit proces na pozadí bez spuštění aplikace. Další informace najdete [v tématu Trigger suspend, resume a background events for Windows Store)](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md).

 Chcete-li nastavit spuštění nainstalované aplikace v režimu ladění, proveďte toto:

> [!NOTE]
> Aplikace nesmí být spuštěna při spuštění tohoto postupu.

1. V nabídce **Ladění** zvolte **Ladění nainstalovaného balíčku aplikace.**

2. Vyberte jednu z následujících možností ze seznamu:

   |                    |                                                                                                                                                                                                                                                                                                                                                                                                           |
   |--------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   | **Místní počítač**  |                                                                                                                Ladění aplikace v aktuální relaci v místním počítači. Viz [Spuštění aplikací pro Windows Store na místním počítači](../debugger/run-windows-store-apps-on-the-local-machine.md).                                                                                                                 |
   |   **Simulátor**    | Ladění aplikace v simulátoru Visual [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] Studio pro aplikace. Simulátor je okno plochy, které umožňuje ladit funkce zařízení , které nejsou k dispozici v místním počítači. Viz [Spuštění aplikací pro Windows Store v simulátoru](../debugger/run-windows-store-apps-in-the-simulator.md). |
   | **Vzdálený stroj** |                          Ladění aplikace na zařízení, které je připojeno k místnímu počítači přes intranet nebo přímo připojené pomocí ethernetového kabelu. Chcete-li ladit vzdáleně, vzdálené nástroje sady Visual Studio musí být nainstalovány a spuštěny na vzdáleném zařízení. Viz [Spouštění aplikací pro Windows Store na vzdáleném počítači](../debugger/run-windows-store-apps-on-a-remote-machine.md).                           |

3. Vyberte aplikaci ze seznamu **Balíčky nainstalovaných aplikací.**

4. Zvolte ladicí modul, který chcete použít ze seznamu **Ladit tento typ kódu.**

5. (Nepovinné). Zvolte **Nespouštět, ale ladit můj kód, když začne** ladit aplikaci při spuštění jinou metodou nebo ladit proces na pozadí.

   Když kliknete na **start**, aplikace se spustí nebo je nastavena na spuštění v režimu ladění.

### <a name="attach-the-debugger-to-a-running-app"></a><a name="BKMK_Attach_the_debugger_to_a_running_app_"></a>Připojení ladicího programu ke spuštěné aplikaci
 Chcete-li připojit ladicí program k [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] aplikaci, musíte použít Laditelný Správce balíčků k nastavení aplikace pro spuštění v režimu ladění. Správce ladicích balíčků je nainstalován pomocí vzdálených nástrojů sady Visual Studio.

 Připojení ladicího programu k aplikaci je užitečné, když potřebujete ladit již nainstalovanou aplikaci, [!INCLUDE[win8_appstore_long](../includes/win8-appstore-long-md.md)]například aplikaci, která byla nainstalovaná z aplikace . Připojení je vyžadováno, pokud máte zdrojové soubory pro aplikaci, ale nemáte projekt Sady Visual Studio pro aplikaci. Můžete mít například vlastní systém sestavení, který nepoužívá projekty nebo řešení sady Visual Studio.

 Připojení ladicího programu k aplikaci vyžaduje následující kroky:

1. Nastavte aplikaci tak, aby běžela v režimu ladění. To musí být provedeno, když aplikace není spuštěna.

2. Spusťte aplikaci. Aplikaci můžete spustit z úvodní obrazovky, smlouvy o provedení nebo jiné metody.

3. Připojte ladicí program ke spuštěné aplikaci.

#### <a name="set-the-app-to-run-in-debug-mode"></a><a name="BKMK_Set_the_app_to_run_in_debug_mode"></a>Nastavení spuštění aplikace v režimu ladění

1. Nainstalujte vzdálené nástroje Visual Studia do zařízení, kde je aplikace nainstalovaná. Viz [Instalace vzdálených nástrojů](https://msdn.microsoft.com/library/windows/apps/hh441469.aspx#BKMK_Installing_the_Remote_Tools).

2. Na úvodní obrazovce vyhledejte `Debuggable Package Manager` a spusťte ji.

     Zobrazí se okno Prostředí PowerShell správně nakonfigurované pro rutinu AppxDebug.

3. Chcete-li povolit ladění aplikace, musíte zadat identifikátor PackageFullName aplikace. Chcete-li zobrazit seznam všech aplikací, které `Get-AppxPackage` obsahují PackageFullName, zadejte na výzvu PowerShell.

4. Na výzvu Prostředí `Enable-AppxDebug` PowerShell zadejte *PackageFullName,* kde *PackageFullName* je identifikátor PackageFullName aplikace.

#### <a name="attach-the-debugger"></a><a name="BKMK_Attach_the_debugger"></a>Připojení ladicího programu
 Připojení ladicího programu:

1. V nabídce **Ladění** zvolte **Připojit ke zpracování**.

    Zobrazí se dialogové okno **Připojit k procesu.**

2. Chcete-li se připojit k aplikaci na vzdáleném zařízení, zadejte vzdálené zařízení do pole **Kvalifikátor.** Můžete:

   - Zadejte název do pole **Kvalifikátor.**

   - V poli **Kvalifikátor** zvolte šipku dolů a pak zvolte zařízení ze seznamu zařízení, ke kterým jste se připojili dříve.

   - Zvolte **Najít,** chcete-li vybrat zařízení ze seznamu zařízení v místní podsíti.

3. Zadejte typ kódu, který chcete ladit v poli **Připojit k.**

    Zvolte **Vybrat** a proveďte jednu z následujících akcí:

   - Zvolte **Automaticky určit typ kódu, který chcete ladit.**

   - Zvolte **Ladit tyto typy kódu** a pak zvolte jeden nebo více typů ze seznamu.

4. V seznamu **Dostupné procesy** zvolte proces aplikace.

5. Zvolte **Připojit**.

   Visual Studio připojí ladicí program k procesu. Spuštění pokračuje, dokud je dosaženo zarážky, ručně pozastavit provádění, dojde k neošetřené výjimce nebo ukončení aplikace.

   [V tomto tématu](#BKMK_In_this_topic)

## <a name="see-also"></a>Viz také
 [Ladění aplikací v Sadě Visual Studio](../debugger/debug-store-apps-in-visual-studio.md) Navigace relace ladění [(Xaml a C#)](../debugger/navigate-a-debugging-session-in-visual-studio-xaml-and-csharp.md)
