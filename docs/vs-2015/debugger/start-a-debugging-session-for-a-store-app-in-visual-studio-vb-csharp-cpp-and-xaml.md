---
title: Spuštění ladicí relace pro Store app (VB, C#, C++ a XAML) | Dokumentace Microsoftu
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
manager: ghogen
ms.openlocfilehash: 847e4144c8846f0247d735ec640fc878a75fa82e
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53051815"
---
# <a name="start-a-debugging-session-for-a-store-app-in-visual-studio-vb-c-c-and-xaml"></a>Spuštění ladicí relace pro Store app v sadě Visual Studio (VB, C#, C++ a XAML)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Platí pro Windows a Windows Phone] (.. /Image/windows_and_phone_content.png "windows_and_phone_content")

 Toto téma popisuje způsob spuštění ladicí relace pro Store aplikace napsané v XAML a Visual C++, Visual C# nebo Visual Basic. Ladění aplikace zahrnuje konfiguraci relace ladění i volba způsob, jak spustit aplikaci.

> [!NOTE]
>  Pro aplikace napsané v jazyce JavaScript a HTML naleznete v tématu [spustíte relaci ladění (JavaScript)](../debugger/start-a-debugging-session-for-store-apps-in-visual-studio-javascript.md).

##  <a name="BKMK_In_this_topic"></a> V tomto tématu
 [Snadný způsob, jak spustit ladění](#BKMK_The_easy_way_to_start_debugging)

 [Konfigurace relace ladění](#BKMK_Configure_the_debugging_session)

- [Otevření stránky vlastnosti ladění pro projekt](#BKMK_Open_the_debugging_property_page_for_the_project)

- [Vybrat možnosti konfigurace sestavení](#BKMK_Choose_the_build_configuration_options)

- [Zvolte cíl nasazení](#BKMK_Choose_the_deployment_target)

- [Zvolte možnost použít ladicí program](#BKMK_Choose_the_debugger_to_use)

- [(Volitelné) Prodleva spuštění relace ladění](#BKMK__Optional__Delay_starting_the_debug_session)

- [(Volitelné) Zakázat vytváření zpětných sítě smyček](#BKMK__Optional__Disable_network_loopbacks)

- [(Volitelné) Nainstalujte aplikaci znovu při spuštění ladění](#BKMK__Optional__Reinstall_the_app_when_you_start_debugging)

- [(Volitelné) Zakázat ověřování požadavek na spuštění vzdáleného ladicího programu](#BKMK__Optional__Disable_authentication_requirement_to_start_the_remote_debugger)

  [Spuštění ladicí relace](#BKMK_Start_the_debugging_session)

- [Spustit ladění (F5)](#BKMK_Start_debugging__F5_)

- [Spustit ladění (F5), ale zpoždění spuštění aplikace](#BKMK_Start_debugging__F5__but_delay_the_app_start)

- [Spustit nainstalovanou aplikaci v ladicím programu](#BKMK_Start_an_installed_app_in_the_debugger)

- [Připojit ladicí modul k běžící aplikaci](#BKMK_Attach_the_debugger_to_a_running_app_)

  -   [Nastavte aplikaci spustit v režimu ladění](#BKMK_Set_the_app_to_run_in_debug_mode)

  -   [Připojit ladicí program](#BKMK_Attach_the_debugger)

##  <a name="BKMK_The_easy_way_to_start_debugging"></a> Snadný způsob, jak spustit ladění

1. Otevřete aplikaci řešení v sadě Visual Studio.

2. Vyberte tlačítko F5.

   Visual Studio vytvoří a spustí aplikaci s připojeným ladícím nástrojem. Provádění pokračuje, dokud není dosaženo zarážky, můžete ručně pozastavení provádění, dojde k výjimce zrušení zpracování, nebo ukončení aplikace. Další informace najdete v tématu [přechod na relaci ladění (Xaml a C#)](../debugger/navigate-a-debugging-session-in-visual-studio-xaml-and-csharp.md) .

##  <a name="BKMK_Configure_the_debugging_session"></a> Konfigurace relace ladění

###  <a name="BKMK_Open_the_debugging_property_page_for_the_project"></a> Otevření stránky vlastnosti ladění pro projekt

1.  V Průzkumníku řešení vyberte projekt. V místní nabídce zvolte **vlastnosti**.

2.  Proveďte to k otevření stránky vlastnosti ladění pro projekt:

    -   Pro aplikace Visual C# a Visual Basic, zvolte **ladění**.

         ![C&#35; &#47; stránky vlastnosti ladění projektu VB](../debugger/media/dbg-csvb-debugpropertypage.png "DBG_CsVb_DebugPropertyPage")

    -   U aplikací v jazyce Visual C++, rozbalte **vlastnosti konfigurace** uzlu a pak zvolte **ladění**.

         ![C&#43; &#43; ladění stránka vlastností aplikace Windows Store](../debugger/media/dbg-cpp-debugpropertypage.png "DBG_CPP_DebugPropertyPage")

###  <a name="BKMK_Choose_the_build_configuration_options"></a> Vybrat možnosti konfigurace sestavení

1.  Z **konfigurace** klikněte na položku **ladění** nebo **(aktivní) ladění**.

2.  Z **platformy** seznamu zvolte cílovou platformu pro vytváření pro. Ve většině případů **jakýkoli procesor** (**všechny platformy** v jazyce Visual C++) je nejlepší volbou.

###  <a name="BKMK_Choose_the_deployment_target"></a> Zvolte cíl nasazení
 ![Platí pouze pro Windows](../debugger/media/windows-only-content.png "windows_only_content")

 Můžete nasadit a ladit aplikace Windows Store na počítač s Visual Studio, simulátoru sady Visual Studio na místním počítači nebo na vzdáleném zařízení.

- Pro aplikace C# a Visual Basic, zvolte příslušný cíl v **cílové zařízení** seznamu **ladění** stránku vlastností pro projekt.

- Pro aplikace v C++, zvolte příslušný cíl v **ladicí program ke spuštění** seznamu **ladění** stránky vlastností:

  Vyberte jednu z těchto možností:

|||
|-|-|
|**Místní počítač**|Ladění aplikace v aktuální relaci na místním počítači. Zobrazit [aplikace Windows Store spustit na místním počítači](../debugger/run-windows-store-apps-on-the-local-machine.md).|
|**Simulátor**|Ladění aplikace v simulátoru sady Visual Studio pro [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] aplikace. Simulátor není okno klasické pracovní plochy, která umožňuje ladit funkce zařízení, jako je například gesta dotykového ovládání a otočení obrazovky –, které nejsou k dispozici v místním počítači. Zobrazit [aplikace spustit Windows Store v simulátoru](../debugger/run-windows-store-apps-in-the-simulator.md).|
|**Vzdálený počítač**|Ladění aplikací na zařízení, který je připojený k místním počítači v síti intranet nebo přímo pomocí kabelu Ethernet. Pro vzdálené ladění, vzdálené nástroje sady Visual Studio musí být nainstalovaná a spuštěná na vzdáleném zařízení. Zobrazit [aplikace Windows Store spustit ve vzdáleném počítači](../debugger/run-windows-store-apps-on-a-remote-machine.md).|

 Pokud se rozhodnete **vzdálený počítač**, zadejte název nebo IP adresu vzdáleného počítače v jednom z těchto způsobů:

- Zadejte název nebo IP adresu vzdáleného počítače.

  -   Pro aplikace C# a Visual Basic, zadejte název nebo IP adresu **vzdálený počítač** pole.

  -   Pro aplikace v C++, zadejte název nebo IP adresu **název počítače** pole.

- Vyberte vzdálený počítač z **vyberte připojení vzdáleného ladicího programu** dialogové okno.

   Chcete-li otevřít dialogové okno:

  - Pro aplikace C# a Visual Basic, zvolte **najít**.

  - Pro aplikace v C++, klikněte na šipku dolů v **název počítače** pole a tlačítko  **\<najít... >**.

    ![Dialogové okno Vyberte připojení vzdáleného ladicího programu](../debugger/media/vsrun-selectremotedebuggerdlg.png "VSRUN_SelectRemoteDebuggerDlg")

  > [!NOTE]
  >  **Vyberte připojení vzdáleného ladicího programu** dialogové okno zobrazí počítače, které jsou na místní podsíť a počítačů, které jsou připojené přímo k sadě Visual Studio počítači pomocí kabelu Ethernet. Chcete-li určit jiný počítač, zadejte název do **název počítače** pole.

  ![Platí pouze pro Windows Phone](../debugger/media/phone-only-content.png "phone_only_content")

  Můžete nasadit a ladit aplikace Windows Phone Store na zařízení nebo na serveru, emulátory phone sady Visual Studio. Vyberte zařízení nebo emulátor z **cílové zařízení** seznamu.

###  <a name="BKMK_Choose_the_debugger_to_use"></a> Zvolte možnost použít ladicí program
 Ve výchozím nastavení Visual Studio ladí spravovaného kódu v aplikacích jazyka C# a Visual Basic.

 Pro aplikace C# a Visual Basic můžete ladit jak spravovaný a nativní kód C/C++ v aplikaci. Vyberte **povolit ladění nespravovaného kódu** zaškrtnutím políčka Zahrnout nativního kódu během vaší relace ladění.

 Ve výchozím nastavení Visual Studio ladí nativního kódu v aplikaci C++.

 Pro aplikace v C++ můžete ladit konkrétní typy kódu, které jsou součástí vaší aplikace, místo nebo kromě nativní kód. Zadejte kód pro ladění ve **typ ladicího programu** seznamu **ladění** stránku vlastností projektu aplikace.

 Vyberte jednu z těchto ladicí programy z **proces aplikace** seznamu:

|||
|-|-|
|**Jenom skript**|Ladění kódu JavaScript ve vaší aplikaci. Nativní a spravovaný kód jsou ignorovány.|
|**Pouze nativní**|Ladění nativního kódu C/C++ v aplikaci. Spravovaný kód a kód jazyka JavaScript jsou ignorovány.|
|**Režim pouze spravovaný**|Ladit spravovaný kód ve vaší aplikaci. Kód jazyka JavaScript a nativního kódu C/C++ jsou ignorovány.|
|**Smíšený (spravovaný a nativní)**|Ladění nativního kódu C/C++ a spravovaném kódu ve vaší aplikaci. Kód jazyka JavaScript se ignoruje.|
|**Jenom grafický procesor**|Ladění nativního kódu C++, na které poběží grafický procesor (GPU).|

 ![Platí pouze pro Windows Phone](../debugger/media/phone-only-content.png "phone_only_content")

 Pro aplikace Windows Store Phone, můžete také zvolit ladicí program pro procesy na pozadí **proces úlohy na pozadí**.

###  <a name="BKMK__Optional__Delay_starting_the_debug_session"></a> (Volitelné) Prodleva spuštění relace ladění
 Ve výchozím nastavení spustí aplikace Visual Studio okamžitě aplikace při spuštění ladění. Můžete také spustit relaci ladění, ale zpoždění spuštění vaší aplikace. Když vyberete tuto možnost, spuštění aplikace v ladicím programu při jeho spuštění na obrazovce Start nebo kliknutím kontrakt aktivace nebo při spuštění jiným procesem nebo metody. Také zpozdíte spuštění vaší aplikace, pokud chcete ladit úlohu na pozadí, když se aplikace.

 Chcete-li zpoždění spuštění vaší aplikace, můžete:

-   Pro aplikace Visual C# a Visual Basic, vyberte **nespouštět, ale ladit můj kód při spuštění** na **ladění** stránku vlastností.

-   Aplikace Visual C++, zvolte **Ano** z **spustit aplikaci** seznamu **ladění** stránku vlastností.

###  <a name="BKMK__Optional__Disable_network_loopbacks"></a> (Volitelné) Zakázat vytváření zpětných sítě smyček
 ![Platí pouze pro Windows](../debugger/media/windows-only-content.png "windows_only_content")

 Z bezpečnostních důvodů aplikace Windows Store, nainstalovaný ve standardním způsobem nepovoluje volat síťových zařízení, ve kterých je nainstalované. Ve výchozím nastavení nasazení sady Visual Studio vytvoří výjimku z tohoto pravidla pro aplikace nasazené. Tato výjimka umožňuje testovat postupy komunikace na jednom počítači. Před odesláním aplikace do Windows Store, měli byste otestovat vaši aplikaci bez výjimky.

 Chcete-li odebrat výjimku zpětnou smyčku sítě:

-   Pro aplikace Visual C# a Visual Basic, zrušte **povolit zpětnou smyčku sítě** zaškrtávací políčko na **ladění** stránku vlastností.

-   U aplikací v jazyce Visual C++, zvolte **č** z **povolit zpětnou smyčku sítě** seznamu na **ladění** stránku vlastností.

###  <a name="BKMK__Optional__Reinstall_the_app_when_you_start_debugging"></a> (Volitelné) Nainstalujte aplikaci znovu při spuštění ladění
 K diagnostice problémů s instalací a počáteční konfiguraci aplikace Visual C# nebo Visual Basic, zvolte **odinstalovat a pak přeinstalovat Můj balíček** na **ladění** znovu vytvořit na stránce vlastností původní instalace při zahájení ladění. Tato možnost není k dispozici pro projekty Visual C++.

###  <a name="BKMK__Optional__Disable_authentication_requirement_to_start_the_remote_debugger"></a> (Volitelné) Zakázat ověřování požadavek na spuštění vzdáleného ladicího programu
 ![Platí pouze pro Windows](../debugger/media/windows-only-content.png "windows_only_content")

 Ve výchozím nastavení musíte zadat přihlašovací údaje ke spuštění vzdáleného ladicího programu.

> [!IMPORTANT]
>  Můžete také spustit vzdálený ladicí program v režimu bez ověřování, ale tento režim se rozhodně nedoporučuje. Při spuštění v tomto režimu není žádné zabezpečení sítě. Na možnost Režim bez ověřování klikněte pouze v případě, že jste si jisti, že není síť ohrožena škodlivými nebo nevyžádanými daty.

 Chcete-li odebrat požadavek na ověření:

1. Pro aplikace Visual C# a Visual Basic, zrušte **použít ověřování** zaškrtávací políčko na **ladění** stránku vlastností.

2. U aplikací v jazyce Visual C++, zvolte **č** z **vyžadují ověřování** seznamu na **ladění** stránku vlastností.

   [V tomto tématu](#BKMK_In_this_topic)

##  <a name="BKMK_Start_the_debugging_session"></a> Spuštění ladicí relace

###  <a name="BKMK_Start_debugging__F5_"></a> Spustit ladění (F5)
 Pokud zvolíte **spustit ladění** (klávesnice: F5) na **ladění** nabídce sady Visual Studio spustí aplikaci s připojeným ladícím nástrojem. Provádění pokračuje, dokud není dosaženo zarážky, můžete ručně pozastavení provádění, dojde k výjimce nebo ukončení aplikace.

###  <a name="BKMK_Start_debugging__F5__but_delay_the_app_start"></a> Spustit ladění (F5), ale zpoždění spuštění aplikace
 Můžete nastavit aplikaci spustit v režimu ladění, ale spusťte ji pomocí jiné metody než ladicí program. Můžete například, chcete-li ladit spuštění vaší aplikace z nabídky Start nebo chcete-li ladit proces na pozadí v aplikaci bez spuštění aplikace. Chcete-li zpoždění spuštění aplikace, postupujte takto:

- Na **ladění** stránka vlastností aplikace (**ladění** v jazyce Visual C++)

  -   Pro aplikace Visual C# a Visual Basic, zvolte **nespouštět, ale ladit můj kód při spuštění**.

  -   U aplikací v jazyce Visual C++, zvolte **Ano** z **spustit aplikaci** seznamu.

- Zvolte **spustit ladění** na **ladění** nabídce (klávesnice: F5).

- Aplikaci spusťte z nabídky Start, kontrakt provádění nebo jiný postup.

  Spuštění aplikace v režimu ladění. Provádění pokračuje, dokud není dosaženo zarážky, můžete ručně pozastavení provádění, dojde k neošetřené výjimce nebo ukončení aplikace.

  . Další informace o ladění úlohy na pozadí, naleznete v tématu [aktivační události pozastavení, obnovení a událostí na pozadí pro Windows Store)](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md).

###  <a name="BKMK_Start_an_installed_app_in_the_debugger"></a> Spustit nainstalovanou aplikaci v ladicím programu
 Při spuštění ladění pomocí F5, Visual Studio vytvoří a nasadí aplikaci, nastaví aplikaci spustit v režimu ladění a pak spustí. Chcete-li spustit aplikaci, která je již nainstalována v zařízení, použijte dialogové okno ladit nainstalovaný balíček aplikace. Tento postup je užitečný, když budete chtít ladit aplikaci, která byla nainstalovaná z Windows storu nebo, pokud mají zdrojové soubory pro aplikaci, ale není nutné projekt sady Visual Studio pro aplikaci. Například může mít vlastní sestavovací systém, který nepoužívá projektů sady Visual Studio nebo řešení.

 Aplikaci můžete nainstalovat na místním zařízení, nebo může být na vzdáleném zařízení.  Aplikaci můžete spustit okamžitě, nebo můžete nastavit jeho spouštění v ladicím programu při spuštění jiným procesem nebo metody, například z nabídky Start nebo kontrakt aktivace, můžete také nastavit aplikaci spustit v režimu ladění, když chcete ladit proces na pozadí bez spuštění aplikace. Další informace najdete v tématu [aktivační události pozastavení, obnovení a událostí na pozadí pro Windows Store)](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md).

 Chcete-li nastavit nainstalovanou aplikaci pro spuštění v režimu ladění, postupujte takto:

> [!NOTE]
>  Když spustíte tento postup, nesmí být spuštěná aplikace.

1. Na **ladění** nabídce zvolte **ladit nainstalovaný balíček aplikace**

2. Ze seznamu vyberte jednu z následujících možností:


   |                    |                                                                                                                                                                                                                                                                                                                                                                                                           |
   |--------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   | **Místní počítač**  |                                                                                                                Ladění aplikace v aktuální relaci na místním počítači. Zobrazit [aplikace Windows Store spustit na místním počítači](../debugger/run-windows-store-apps-on-the-local-machine.md).                                                                                                                 |
   |   **Simulátor**    | Ladění aplikace v simulátoru sady Visual Studio pro [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] aplikace. Simulátor není okno klasické pracovní plochy, která umožňuje ladit funkce zařízení, jako je například gesta dotykového ovládání a otočení obrazovky –, které nejsou k dispozici v místním počítači. Zobrazit [aplikace spustit Windows Store v simulátoru](../debugger/run-windows-store-apps-in-the-simulator.md). |
   | **Vzdálený počítač** |                          Ladění aplikací na zařízení, který je připojený k místním počítači v síti intranet nebo přímo pomocí kabelu Ethernet. Pro vzdálené ladění, vzdálené nástroje sady Visual Studio musí být nainstalovaná a spuštěná na vzdáleném zařízení. Zobrazit [aplikace Windows Store spustit ve vzdáleném počítači](../debugger/run-windows-store-apps-on-a-remote-machine.md).                           |


3. Vyberte aplikaci ze **nainstalované balíčky aplikací** seznamu.

4. Zvolte ladicího stroje ze **ladit tento typ kódu** seznamu.

5. (Volitelné). Zvolte **nespouštět, ale ladit můj kód při spuštění** k ladění aplikace při spuštění pomocí některé jiné metody nebo chcete-li ladit proces na pozadí.

   Po kliknutí na **Start**, aplikace se spustí nebo je nastaven na spouštění v režimu ladění.

###  <a name="BKMK_Attach_the_debugger_to_a_running_app_"></a> Připojit ladicí modul k běžící aplikaci
 Připojit ladicí program [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] aplikace, musíte použít laditelný Správce balíčků pro nastavení aplikace pro spuštění v režimu ladění. Laditelný Správce balíčků je nainstalované s Visual Studio Remote Tools.

 Připojování ladicího programu do aplikace je užitečné, když budete chtít ladit aplikace již nainstalována, jako je například aplikaci, která byla nainstalována ze [!INCLUDE[win8_appstore_long](../includes/win8-appstore-long-md.md)]. Připojení se vyžaduje, pokud mají zdrojové soubory pro aplikaci, ale není nutné projekt sady Visual Studio pro aplikaci. Například může mít vlastní sestavovací systém, který nepoužívá projektů sady Visual Studio nebo řešení.

 Připojování ladicího programu do aplikace vyžaduje tyto kroky:

1.  Nastavte aplikaci spustit v režimu ladění. To je nutné provést při není aplikace spuštěna.

2.  Spusťte aplikaci. Aplikaci můžete spustit z úvodní obrazovky, kontrakt provádění nebo některé jiné metody.

3.  Připojte ladicí modul k běžící aplikaci.

####  <a name="BKMK_Set_the_app_to_run_in_debug_mode"></a> Nastavte aplikaci spustit v režimu ladění

1.  Nainstalujte na zařízení nainstalovanou aplikaci Visual Studio Remote Tools. Zobrazit [instalace vzdálených nástrojů](http://msdn.microsoft.com/library/windows/apps/hh441469.aspx#BKMK_Installing_the_Remote_Tools).

2.  Na obrazovce Start, vyhledejte `Debuggable Package Manager` a spusťte jej.

     Zobrazí se okno prostředí PowerShell správně nakonfigurovaný pro rutiny AppxDebug.

3.  Pokud chcete povolit ladění aplikace, je nutné zadat identifikátor Úplnýnázevbalíčku aplikace. Chcete-li zobrazit seznam všech aplikací, které zahrnuje Úplnýnázevbalíčku, zadejte `Get-AppxPackage` řádku Powershellu.

4.  Na příkazovém řádku tento příkaz prostředí PowerShell, zadejte `Enable-AppxDebug` *PackageFullName* kde *PackageFullName* je identifikátor Úplnýnázevbalíčku aplikace.

####  <a name="BKMK_Attach_the_debugger"></a> Připojit ladicí program
 Připojení ladicího programu:

1. Na **ladění** nabídce zvolte **připojit k procesu**.

    **Připojit k procesu** zobrazí se dialogové okno.

2. Připojit k aplikaci na vzdáleném zařízení, zadejte vzdáleného zařízení **kvalifikátor** pole. Můžeš:

   -   Zadejte název do pole **kvalifikátor** pole.

   -   Zvolte šipku dolů u **kvalifikátor** a pak vyberte zařízení ze seznamu zařízení, které jste připojili k před.

   -   Zvolte **najít** vyberte zařízení ze seznamu zařízení v místní podsíti.

3. Zadejte kód, který chcete ladit v **připojit k** pole.

    Zvolte **vyberte** a udělejte jednu z následujících akcí:

   -   Zvolte **automaticky určit typ kódu k ladění**

   -   Zvolte **ladit tyto typy kódu** a ze seznamu vyberte jeden nebo více typů.

4. V **procesy k dispozici** klikněte na položku procesu aplikace.

5. Zvolte **připojit**.

   Visual Studio připojí ladicí program k procesu. Provádění pokračuje, dokud není dosaženo zarážky, můžete ručně pozastavení provádění, dojde k neošetřené výjimce nebo ukončení aplikace.

   [V tomto tématu](#BKMK_In_this_topic)

## <a name="see-also"></a>Viz také
 [Ladění aplikací v sadě Visual Studio](../debugger/debug-store-apps-in-visual-studio.md) [přechod na relaci ladění (Xaml a C#)](../debugger/navigate-a-debugging-session-in-visual-studio-xaml-and-csharp.md)
