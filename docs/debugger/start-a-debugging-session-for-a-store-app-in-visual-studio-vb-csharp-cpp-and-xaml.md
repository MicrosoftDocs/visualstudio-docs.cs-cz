---
title: Spuštění ladicí relace pro aplikaci pro UWP | Microsoft Docs
ms.custom: seodec18
ms.date: 11/20/2018
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
- vs.debug.installedapppackagelauncher
- vs.debug.error.wwahost_scriptdebuggingdisabled
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- uwp
ms.openlocfilehash: c4504dda362c8a50f33168a12839e894a14316d7
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/16/2019
ms.locfileid: "72436016"
---
# <a name="start-a-debugging-session-for-a-uwp-app"></a>Spuštění ladicí relace aplikace pro UPW

Tento článek popisuje, jak spustit relaci ladění sady Visual Studio pro aplikaci Univerzální platforma Windows (UWP). Aplikace pro UWP můžou být napsané v C++jazyce XAML a C#, XAML a webový Basic. Pokud chcete začít ladit aplikaci UWP, nakonfigurujte relaci ladění a vyberte způsob, jak aplikaci spustit.

::: moniker range=">=vs-2019"
> [!NOTE]
> Od sady Visual Studio 2019 se aplikace pro UWP pro HTML a JavaScript už nepodporují.
::: moniker-end
::: moniker range="vs-2017"
V aplikaci Visual Studio 2017 většina příkazů a možností, které jsou uvedené v tomto článku, platí taky pro aplikace pro UWP v HTML a JavaScriptu. V případě, že se příkazy pro C++ správu a aplikace liší, jsou obvykle aplikace JavaScriptu stejné jako C++ příkazy pro aplikace UWP.
::: moniker-end

## <a name="BKMK_The_easy_way_to_start_debugging"></a>Spustit ladění na panelu nástrojů sady Visual Studio

Nejjednodušší způsob, jak nakonfigurovat a spustit ladění, je ze standardního panelu nástrojů sady Visual Studio.

![Ladění z panelu nástrojů](../debugger/media/vsrun_select_target_device.png)

1. V rozevíracím seznamu **Konfigurace** na **standardním** panelu nástrojů vyberte **ladit**.

1. V rozevíracím seznamu **platforma** vyberte cílovou platformu, pro kterou chcete vytvořit.

1. Z rozevíracího seznamu vedle zelené šipky vyberte cíl ladění. Můžete zvolit místní počítač, zařízení s přímým připojením, místní simulátor sady Visual Studio, vzdálené zařízení nebo emulátor.

1. Chcete-li spustit ladění, vyberte zelenou šipku **Start** na panelu nástrojů nebo vyberte možnost **ladění** > **Spustit ladění**nebo stiskněte klávesu **F5**.

   Visual Studio vytvoří a spustí aplikaci pomocí připojeného ladicího programu.

Ladění pokračuje, dokud není dosaženo zarážky, ručním zastavením spuštění, neošetřené výjimky nebo ukončení aplikace.

### <a name="BKMK_Choose_the_deployment_target"></a>Možnosti cíle nasazení

Můžete nastavit cíl ladění na panelu nástrojů sady Visual Studio nebo na stránce vlastností ladění projektu. Vyberte jednu z následujících možností:

|||
|-|-|
|**Místní počítač**|Ladit aplikaci v aktuální relaci na místním počítači.|
|**Simulátor**|Ladit aplikaci v simulátoru sady Visual Studio pro aplikace pro UWP Simulátor je okno plochy, které simuluje funkce zařízení, jako jsou dotyková gesta a rotace zařízení, které na místním počítači pravděpodobně neexistují. Možnost simulátoru je dostupná jenom v případě, že je **Minimální verze cílové platformy** vaší aplikace menší než nebo se rovná operačnímu systému v místním počítači. Další informace najdete v tématu [spouštění aplikací pro UWP v simulátoru](../debugger/run-windows-store-apps-in-the-simulator.md).|
|**Vzdálený počítač**|Ladit aplikaci na zařízení připojeném k místnímu počítači přes síť nebo síťový kabel Ethernet. Na vzdáleném zařízení musí být nainstalovaná a spuštěná Remote Tools for Visual Studio. Další informace najdete v tématu [spouštění aplikací pro UWP na vzdáleném počítači](../debugger/run-windows-store-apps-on-a-remote-machine.md).|
|**Zařízení**|Ladit aplikaci na zařízení připojeném k USB. Zařízení musí být odemknuté vývojářem a obrazovka je odemčená.|
|**Mobilní emulátor**|Spusťte emulátor zadaný v názvu emulátoru, nasaďte aplikaci a spusťte ladění. Emulátory jsou k dispozici pouze na počítačích s podporou technologie Hyper-V.|

## <a name="BKMK_Open_the_debugging_property_page_for_the_project"></a>Konfigurace ladění na stránce vlastností projektu

Chcete-li nakonfigurovat další možnosti ladění, použijte stránku vlastnosti ladění projektu.

**Chcete-li otevřít vlastnosti ladění:**

1. V **Průzkumník řešení**vyberte projekt a pak vyberte ikonu **vlastnosti** , nebo klikněte pravým tlačítkem na projekt a vyberte **vlastnosti**.

1. Na levé straně podokna **vlastnosti** :

   - Pro C# aplikace a Visual Basic vyberte **ladit**.

     ![C#a Visual Basic stránce vlastností ladění projektu](../debugger/media/dbg_csvb_debugpropertypage.png)

   - Pro C++ aplikace vyberte možnost **Vlastnosti konfigurace** > **ladění**.

     ![C++Stránka vlastností ladění aplikace UWP](../debugger/media/dbg_cpp_debugpropertypage.png)

### <a name="BKMK_Choose_the_debugger_to_use"></a>Vyberte ladicí program, který se má použít.

Pro C# aplikace a Visual Basic aplikace Visual Studio ve výchozím nastavení ladit spravovaný kód. Můžete zvolit ladění dalších nebo dalších typů kódu. Můžete také nastavit hodnoty **typu ladicího programu** pro všechny úlohy na pozadí, které jsou součástí projektu.

V C++ aplikacích Visual Studio ve výchozím nastavení ladit nativní kód. Můžete se rozhodnout ladit konkrétní typy kódu namísto nebo kromě nativního kódu.

**Chcete-li určit typy kódu k ladění:**

- Pro C# a Visual Basic aplikace vyberte v rozevíracím seznamu typ **ladicího programu** na stránce vlastností **ladění** jeden z následujících ladicích programů z nabídky **Typ aplikace** a **typ procesu na pozadí** .

- V C++ případě aplikací vyberte jednu z následujících ladicích programů z rozevíracího seznamu **Typ ladicího programu** na stránce vlastností **ladění** .

|||
|-|-|
|**Jenom spravovaná**|Ladění spravovaného kódu ve vaší aplikaci. Kód jazyka JavaScript a nativníC++ kód jazyka C jsou ignorovány.|
|**Pouze nativní**|Ladění nativního jazykaC++ C/kódu ve vaší aplikaci. Spravovaný kód a kód jazyka JavaScript jsou ignorovány.|
|**Smíšený (spravovaný a nativní)**|Ladění nativního kóduC++ C/kódu a spravovaného kódu ve vaší aplikaci. JavaScriptový kód se ignoruje. V C++ projektech je tato možnost označována jako **spravovaná a nativní**.|
|**Pravidel**|Ladění kódu JavaScriptu ve vaší aplikaci. Spravovaný kód a nativní kód jsou ignorovány.|
|**Nativní se skriptem**|Ladění nativního kóduC++ C/kódu a JavaScriptu ve vaší aplikaci. Spravovaný kód se ignoruje. K dispozici pouze v projektech nebo úlohách na C++ pozadí.|
|**Pouze GPU (C++ amp)**|Ladění nativního C++ kódu, který běží na grafické jednotce procesoru (GPU). K dispozici pouze v C++ projektech.|

### <a name="BKMK__Optional__Disable_network_loopbacks"></a>Zakázat zpětné smyčky sítě (volitelné)

 V případě zabezpečení aplikace UWP, která je nainstalovaná standardním způsobem, nemůže v zařízení provádět síťová volání do zařízení, na kterém je nainstalovaná. Visual Studio ve výchozím nastavení nezbavuje nasazené aplikace od tohoto pravidla, takže můžete testovat komunikační postupy na jednom počítači. Před vydáním aplikace byste měli aplikaci otestovat bez výjimky.

**Odebrání výjimky zpětné smyčky sítě:**

- Pro C# aplikace a Visual Basic zrušte zaškrtnutí políčka **Povolení zpětné smyčky v místní síti** v části **Možnosti spuštění** na stránce vlastností **ladění** .

- V C++ případě aplikací vyberte v rozevíracím seznamu zapnout **zpětnou smyčku místní sítě** na stránce vlastností **ladění** možnost **ne** .

### <a name="BKMK__Optional__Reinstall_the_app_when_you_start_debugging"></a>Přeinstalace aplikace při spuštění ladění (volitelné)
 Chcete-li diagnostikovat problémy C# s instalací aplikace nebo Visual Basic, vyberte možnost **odinstalovat a poté znovu nainstalovat balíček** na stránce vlastností **ladění** . Tato možnost po spuštění ladění znovu vytvoří původní instalaci. Tato možnost není k dispozici pro C++ projekty.

### <a name="BKMK__Optional__Disable_authentication_requirement_to_start_the_remote_debugger"></a>Nastavení možností ověřování pro vzdálené ladění

Ve výchozím nastavení je nutné zadat přihlašovací údaje systému Windows pro spuštění vzdáleného ladicího programu, když jako cíl nasazení vyberete možnost **vzdálený počítač** . Požadavek na ověření můžete změnit.

**Univerzální (nešifrovaný protokol)** režim ověřování je pro zařízení IoT, Xbox a HoloLens a pro počítače s Windows 10, které jsou k nebo novější.

**Postup změny metody ověřování:**

- Pro C# a Visual Basic aplikace na stránce vlastností **ladění** vyberte jako **cílové zařízení**možnost **vzdálený počítač** . Potom pro **režim ověřování**vyberte možnost **žádný** nebo **univerzální (nešifrovaný protokol)** .

- Pro C++ aplikace vyberte na stránce vlastností **ladění** možnost **vzdálený počítač** v části **ladicí program, který se má spustit** . Pak pro **typ ověřování**vyberte možnost **bez ověřování** nebo **univerzální (nešifrovaný protokol)** .

> [!CAUTION]
> Při spuštění vzdáleného ladicího programu v režimu **žádného** nebo **univerzálního (nešifrovaného protokolu)** nedochází k zabezpečení sítě. Tyto režimy vyberte pouze v důvěryhodných sítích, u kterých jste si jisti, že nehrozí riziko škodlivého kódu nebo nepřátelských přenosů.

## <a name="BKMK_Start_the_debugging_session"></a>Možnosti spuštění ladění

Když vyberete možnost **ladění** > **Spustit ladění** nebo stisknout klávesu **F5**, aplikace Visual Studio spustí aplikaci pomocí připojeného ladicího programu. Spuštění pokračuje, dokud není dosaženo zarážky, ručním zastavením spuštění, neošetřené výjimky nebo ukončení aplikace.

### <a name="BKMK_Start_debugging__F5__but_delay_the_app_start"></a>Spustit ladění, ale zpozdit začátek aplikace

Ve výchozím nastavení Visual Studio spustí aplikaci ihned po spuštění ladění. Aplikaci můžete také nastavit tak, aby běžela v režimu ladění, ale spouštěla aplikaci mimo ladicí program. Například můžete chtít ladit spuštění aplikace z nabídky **Start** systému Windows nebo ladit proces na pozadí v aplikaci. Pokud zvolíte tuto možnost, aplikace se spustí při spuštění ladicího programu.

**Zakázání automatického spuštění aplikace:**

- Pro C# a Visual Basic aplikace vyberte možnost **nespouštět, ale ladit můj kód při spuštění** v části **Možnosti spuštění** na stránce vlastností **ladění** .

- V C++ rozevíracím seznamu **Spustit aplikaci** na stránce vlastností **ladění** vyberte v části aplikace možnost **ne** .

Další informace o ladění úloh na pozadí najdete v tématu [triggery pro pozastavení, obnovení a události na pozadí pro aplikace pro UWP](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md).

### <a name="BKMK_Start_an_installed_app_in_the_debugger"></a>Ladění nainstalované nebo spuštěné aplikace UWP

Pomocí **ladění nainstalovaného balíčku aplikace** můžete LADIT aplikaci UWP, která je už nainstalovaná nebo spuštěná na místním nebo vzdáleném zařízení. Je možné, že je aplikace nainstalovaná z Microsoft Store nebo se nejedná o projekt sady Visual Studio. Aplikace může mít například vlastní systém sestavení, který nepoužívá aplikaci Visual Studio.

Nainstalovanou aplikaci můžete okamžitě spustit, nebo ji můžete nastavit tak, aby běžela v ladicím programu při spuštění s jinou metodou. Další informace najdete v tématu [triggerování, obnovení a události na pozadí pro aplikace pro UWP](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md).

Pokud chcete spustit nainstalovanou nebo spuštěnou aplikaci UWP v ladicím programu, vyberte **ladit** > **další cíle ladění** > **ladění nainstalovaného balíčku aplikace**. Další pokyny najdete v tématu [ladění nainstalovaného balíčku aplikace](../debugger/debug-installed-app-package.md).

### <a name="BKMK_Attach_the_debugger_to_a_running_app_"></a>Připojení ladicího programu k běžící aplikaci Windows 8. x

Chcete-li připojit ladicí program k aplikaci [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)], je nutné použít Správce balíčků, který lze ladit, a nastavit aplikaci tak, aby běžela v režimu ladění. Správce balíčku, který lze ladit, je nainstalován s Remote Tools for Visual Studio.

1. Nainstalujte Remote Tools for Visual Studio do zařízení, ve kterém je aplikace nainstalovaná. Další informace najdete v tématu [Instalace nástrojů Remote Tools](../debugger/remote-debugging.md).

1. Na obrazovce **Start** systému Windows vyhledejte a spusťte **laditelné správce balíčků**.

   Zobrazí se okno PowerShellu správně nakonfigurované pro rutinu AppxDebug.

1. Zadejte identifikátor PackageFullName aplikace.

   1. Pokud chcete zobrazit seznam, který obsahuje PackageFullName všech aplikací, zadejte do příkazového řádku PowerShellu `Get-AppxPackage`.

   1. Na příkazovém řádku PowerShellu zadejte `Enable-AppxDebug <PackageFullName>`, kde \<PackageFullName > je PackageFullName identifikátor aplikace.

1. Vyberte možnost **ladění** > **připojit k procesu**.

1. V dialogovém okně **připojit k procesu** zadejte vzdálené zařízení do pole **cíl připojení** .

   Můžete zadat název zařízení, vybrat ho z rozevíracího seznamu v poli **cíl připojení** nebo vybrat **Najít** pro vyhledání zařízení v dialogovém okně **vzdálené připojení** .

1. Chcete-li zadat typ kódu, který chcete ladit, vyberte vedle pole **připojit k** možnost **Vybrat**.

1. V dialogovém okně **Vybrat typ kódu** vyberte jednu z těchto akcí:
   - **Automaticky určit typ kódu pro ladění**, nebo
   - Proveďte **ladění těchto typů kódu**a potom v seznamu vyberte jeden nebo více typů kódu.

1. V seznamu **procesy k dispozici** vyberte proces aplikace, který se má ladit.

1. Vyberte **připojit**.

 Visual Studio připojí ladicí program k procesu. Spuštění pokračuje, dokud není dosaženo zarážky, ručním zastavením spuštění, neošetřené výjimky nebo ukončení aplikace.

::: moniker range="vs-2017"
> [!NOTE]
> Aplikace JavaScriptu běží v instanci procesu *wwahost. exe* . Pokud je spuštěná víc než jedna aplikace JavaScriptu, budete muset znát číslo ID procesu (PID) procesu *wwahost. exe* vaší aplikace, abyste se k němu připojili.
>
> Nejjednodušší způsob, jak se připojit k aplikaci JavaScriptu, je zavřít všechny ostatní aplikace JavaScriptu. Můžete si také všimnout, že se PID spouštění procesů *wwahost. exe* ve Správci úloh systému Windows před zahájením aplikace poznamenat. Při spuštění aplikace bude *wwahost. exe* PID ten, který se liší od dříve popsaných.
::: moniker-end

## <a name="see-also"></a>Viz také:

- [Ladění aplikací v sadě Visual Studio](../debugger/debugging-windows-store-and-windows-universal-apps.md)