---
title: Spuštění ladicí relace pro aplikace pro UPW | Dokumentace Microsoftu
ms.custom: seodec18
ms.date: 11/20/2018
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
- vs.debug.installedapppackagelauncher
- vs.debug.error.wwahost_scriptdebuggingdisabled
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- uwp
ms.openlocfilehash: 181dec6bfa6ebe96528c39b74d68375b8eb7fcb8
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53062406"
---
# <a name="start-a-debugging-session-for-a-uwp-app"></a>Spuštění ladicí relace aplikace pro UPW
  
Tento článek popisuje způsob spuštění ladicí relace pro aplikace univerzální platformy Windows (UPW) sady Visual Studio. U aplikací pro UPW je možné psát v XAML, C++ a XAML a C#/Visual Basic, nebo HTML a JavaScript. Pro spuštění ladění aplikace pro UPW, nakonfigurujte relaci ladění a zvolte způsob, jak spustit aplikaci.  
  
##  <a name="BKMK_The_easy_way_to_start_debugging"></a>Spuštění ladění z panelu nástrojů sady Visual Studio 
  
Nejjednodušší způsob, jak nakonfigurovat a spustit ladění je z panelu nástrojů standardní sady Visual Studio. 

![Ladění na panelu nástrojů](../debugger/media/vsrun_select_target_device.png)  
  
1. Z **konfigurace** rozevírací seznam pro **standardní** nástrojů vyberte **ladění**.  
  
1. Z **platformy** rozevíracím seznamu vyberte cílovou platformu pro vytváření pro. 
   
1. Z rozevíracího seznamu vedle na zelenou šipku vyberte cíl ladění. Můžete vybrat místní počítač, přímo připojená zařízení, místní simulátor aplikace Visual Studio, vzdálené zařízení nebo emulátoru. 
   
1. Chcete-li spustit ladění, vyberte zelené **Start** šipku na panelu nástrojů nebo vyberte **ladění** > **spustit ladění**, nebo stiskněte klávesu **F5**. 
   
   Visual Studio vytvoří a spustí aplikaci s připojeným ladícím nástrojem. 

Ladění pokračuje, dokud není dosaženo zarážky, můžete ručně pozastavení provádění, dojde k neošetřené výjimce nebo ukončení aplikace.  
  
###  <a name="BKMK_Choose_the_deployment_target"></a> Target – možnosti nasazení 
  
Můžete nastavit cíl ladění na panelu nástrojů sady Visual Studio nebo projekt je ladění stránku vlastností. Vyberte jednu z následujících možností:

|||  
|-|-|  
|**Místní počítač**|Ladění aplikace v aktuální relaci na místním počítači.|  
|**Simulátor**|Ladění aplikace v simulátoru sady Visual Studio pro aplikace pro UPW. Simulátor není okno klasické pracovní plochy, která simuluje zařízení funkce, jako je touch gesta a otočení obrazovky, který neexistuje v místním počítači. Simulátor možnost je dostupná pouze tehdy, pokud vaše aplikace **Min cílové platformy. Verze** je menší než nebo rovna operačního systému na místním počítači. Další informace najdete v tématu [aplikace spustit UWP v simulátoru](../debugger/run-windows-store-apps-in-the-simulator.md).|  
|**Vzdálený počítač**|Ladění aplikace v zařízení připojeném do místního počítače prostřednictvím sítě nebo kabelu Ethernet. Remote Tools for Visual Studio musí být nainstalovaná a spuštěná na vzdáleném zařízení. Další informace najdete v tématu [aplikací pro UWP spuštění na vzdáleném počítači](../debugger/run-windows-store-apps-on-a-remote-machine.md).|  
|**zařízení**|Ladění aplikací na zařízení připojená přes USB. Zařízení musí být odemčené pro vývojáře a odemknutí obrazovky.|  
|**Mobilní emulátor**|Spuštění emulátoru zadaný v názvu emulátor, nasaďte aplikaci a spusťte ladění. Emulátory jsou dostupné pouze pro počítače Hyper-V povolena.|  

##  <a name="BKMK_Open_the_debugging_property_page_for_the_project"></a> Konfigurovat ladění na stránce vlastností projektu 

Pokud chcete nakonfigurovat další možnosti ladění, použijte stránky vlastnosti ladění projektu. 

**Chcete-li otevřít vlastnosti ladění:**

1. V **Průzkumníka řešení**, vyberte projekt a pak vyberte **vlastnosti** ikonu, nebo klikněte pravým tlačítkem na projekt a vyberte **vlastnosti**.  
   
1. Na levé straně **vlastnosti** podokna:
   
   - Pro C# a Visual Basic aplikací, vyberte **ladění**.  
     
     ![C#a stránky vlastnosti ladění projektu jazyka Visual Basic](../debugger/media/dbg_csvb_debugpropertypage.png)  
   
   - U aplikací C++ a JavaScript, vyberte **vlastnosti konfigurace** > **ladění**.  
     
     ![Stránka vlastností ladění aplikace C++ UWP](../debugger/media/dbg_cpp_debugpropertypage.png)  

###  <a name="BKMK_Choose_the_debugger_to_use"></a> Zvolte možnost použít ladicí program  

Pro C# a aplikace Visual Basic, Visual Studio ladí spravovaného kódu ve výchozím nastavení. Můžete ladit kód jiné nebo další typy. Můžete také nastavit **typ ladicího programu** hodnoty pro všechny úlohy na pozadí, které jsou součástí projektu.

V aplikacích jazyka C++ Visual Studio ladí nativního kódu ve výchozím nastavení. V aplikacích jazyka JavaScript sady Visual Studio ladí skript ve výchozím nastavení. Můžete ladit konkrétní typy kódu místo nebo kromě nativní kód. 

**Chcete-li určit typy kódu k ladění:**

- Pro C# a Visual Basic aplikací, vyberte jednu z následujících ladicí programy z **typ aplikace** a **typ procesu na pozadí** rozevírací seznamy v části **typ ladicího programu** na **ladění** stránku vlastností.  
  
- Pro C + +/ aplikací jazyka JavaScript, vyberte jednu z následujících ladicí programy z **typ ladicího programu** rozevírací seznam pro **ladění** stránku vlastností.

|||  
|-|-|  
|**Režim pouze spravovaný**|Ladit spravovaný kód ve vaší aplikaci. Kód jazyka JavaScript a nativního kódu C/C++ jsou ignorovány.|  
|**Pouze nativní**|Ladění nativního kódu C/C++ v aplikaci. Spravovaný kód a kód jazyka JavaScript jsou ignorovány.|  
|**Smíšený (spravovaný a nativní)**|Ladění nativního kódu C/C++ a spravovaném kódu ve vaší aplikaci. Kód jazyka JavaScript se ignoruje. V projektech C++, je tato možnost volat **spravovaný a nativní**.|  
|**skript**|Ladění kódu JavaScript ve vaší aplikaci. Nativní a spravovaný kód jsou ignorovány.|  
|**Nativní pomocí skriptu**|Ladění nativního kódu C/C++ a jazyka JavaScript v aplikaci. Spravovaný kód se ignoruje. K dispozici v projektech C++ nebo pouze úlohy na pozadí.|  
|**Jenom grafický procesor (C++ AMP)**|Ladění nativního kódu C++, na které poběží grafický procesor (GPU). K dispozici v pouze projekty C++.|  

  
###  <a name="BKMK__Optional__Disable_network_loopbacks"></a> Zakázat network vytváření zpětných smyček (volitelné) 
  
 Pro zabezpečení nemůže aplikace pro UPW, který je nainstalován standardním způsobem provádět síťových voláních do zařízení, ve kterých je nainstalované. Visual Studio stanoví nasazené aplikace toto pravidlo ve výchozím nastavení, abyste mohli otestovat postupy komunikace na jednom počítači. Před vydáním aplikace, měli byste otestovat vaši aplikaci bez výjimky.  
  
**Chcete-li odebrat výjimku zpětnou smyčku sítě:**  
  
-   Pro C# a zrušte zaškrtnutí možnosti aplikace Visual Basic **povolit zpětnou smyčku místní sítě** zaškrtávací políčko v oblasti **možnosti spuštění** na **ladění** stránku vlastností.  
  
-   U aplikací Visual C++ a JavaScript, vyberte **ne** z **povolit zpětnou smyčku místní sítě** rozevírací seznam pro **ladění** stránku vlastností.  
  
###  <a name="BKMK__Optional__Reinstall_the_app_when_you_start_debugging"></a> Nainstalujte aplikaci znovu při spuštění ladění (volitelné) 
 Diagnostikovat problémy instalace s C# nebo na aplikaci Visual Basic, vyberte **odinstalovat a přeinstalovat Můj balíček** na **ladění** stránku vlastností. Tato možnost obnoví původní instalace při zahájení ladění. Tato možnost není k dispozici pro projekty jazyka C++ a JavaScript.  
  
###  <a name="BKMK__Optional__Disable_authentication_requirement_to_start_the_remote_debugger"></a> Nastavit možnosti ověřování pro vzdálené ladění  
  
Ve výchozím nastavení, musíte zadat přihlašovací údaje Windows pro spuštění vzdáleného ladicího programu při výběru **vzdálený počítač** jako cíl nasazení. Požadavek na ověření můžete změnit. 

**Univerzální (nešifrovaný protokol)** režim ověřování je pro zařízení IoT a Xbox, HoloLens a autora Update nebo novější počítače s Windows 10.  

**Chcete-li změnit metodu ověřování:**  

- Pro C# a Visual Basic aplikací, na **ladění** stránky vlastností, vyberte **vzdálený počítač** jako **cílové zařízení**. Vyberte **žádný** nebo **univerzální (nešifrovaný protokol)** pro **režim ověřování**. 
  
- U aplikací C++ a JavaScript, vyberte **vzdálený počítač** pod **ladicí program ke spuštění** na **ladění** stránku vlastností. Vyberte **bez ověřování** nebo **univerzální (nešifrovaný protokol)** pro **typ ověřování**. 
  
> [!CAUTION]
> Neexistuje žádné zabezpečení sítě při spuštění vzdáleného ladicího programu v **žádný** nebo **univerzální (nešifrovaný protokol)** režimy. Zvolte těchto režimech jenom v důvěryhodných sítích, které jste jisti nejsou riziko zneužití škodlivým kódem nebo nebezpečný provoz.  
  
##  <a name="BKMK_Start_the_debugging_session"></a> Možnosti spuštění ladění  
  
Když vyberete **ladění** > **spustit ladění** nebo stiskněte klávesu **F5**, Visual Studio spustí aplikaci s připojeným ladícím nástrojem. Provádění pokračuje, dokud není dosaženo zarážky, můžete ručně pozastavení provádění, dojde k neošetřené výjimce nebo ukončení aplikace.  
  
###  <a name="BKMK_Start_debugging__F5__but_delay_the_app_start"></a> Spuštění ladění ale zpoždění spuštění aplikace  

Visual Studio ve výchozím nastavení spustí aplikaci hned po spuštění ladění. Můžete také nastavit aplikace ke spuštění v režimu ladění, ale spustí aplikaci mimo ladicí program. Například můžete chtít ladit spuštění aplikace z Windows **Start** nabídky nebo ladicí proces na pozadí v aplikaci. Pokud zvolíte tuto možnost, spuštění v ladicím programu při spuštění aplikace. 

**Chcete-li zakázat automatické aplikace při spuštění:**  
  
- Pro C# a Visual Basic aplikací, vyberte **nespouštět, ale ladit můj kód při spuštění** pod **možnosti spuštění** na **ladění** stránku vlastností.  
   
- U aplikací C++ a JavaScript, vyberte **ne** z **spustit aplikaci** rozevírací seznam pro **ladění** stránku vlastností.  
  
Další informace o ladění úlohy na pozadí, naleznete v tématu [aktivační události pozastavení, obnovení a událostí na pozadí pro aplikace UWP](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md).  
  
###  <a name="BKMK_Start_an_installed_app_in_the_debugger"></a> Ladit aplikaci UPW nainstalován nebo není spuštěn 

Můžete použít **ladit nainstalovaný balíček aplikace** ladit aplikace pro UPW, která je již nainstalována nebo spuštěna na místním nebo vzdáleném zařízení. Aplikace může být nainstalována z Microsoft Store nebo nemusí být projekt sady Visual Studio. Například aplikace může mít vlastní sestavovací systém, který nepoužívá sady Visual Studio.  
  
Nainstalovanou aplikaci mohou spustit okamžitě, nebo můžete nastavit jeho spouštění v ladicím programu, když se spustí s jinou metodu. Další informace najdete v tématu [aktivační události pozastavení, obnovení a událostí na pozadí pro aplikace UPW)](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md).  
  
Chcete-li spustit aplikaci UPW nainstalován nebo není spuštěn v ladicím programu, vyberte **ladění** > **jiné cíle ladění** > **ladit nainstalovaný balíček aplikace**. Další pokyny najdete v tématu [ladění balíčku nainstalované aplikace](../debugger/debug-installed-app-package.md).

###  <a name="BKMK_Attach_the_debugger_to_a_running_app_"></a> Připojit ladicí modul k běžící aplikaci Windows 8.x

Připojit ladicí program [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] aplikace, musíte použít laditelný Správce balíčků pro nastavení aplikace pro spuštění v režimu ladění. Laditelný Správce balíčků se instaluje s nástroji Remote Tools for Visual Studio.  
  
1. Instalovat nástroje Remote Tools for Visual Studio na zařízení, ve kterém je aplikace nainstalovaná. Další informace najdete v tématu [instalace vzdálených nástrojů](../debugger/remote-debugging.md).  
   
1. V Windows **Start** obrazovky, vyhledejte a spusťte **správce Laditelného balíku**.  
   
   Zobrazí se okno prostředí PowerShell správně nakonfigurovaný pro rutiny AppxDebug.  
   
1. Zadejte identifikátor Úplnýnázevbalíčku aplikace. 
   
   1. Chcete-li zobrazit seznam, který zahrnuje Úplnýnázevbalíčku všechny aplikace, zadejte `Get-AppxPackage` řádku Powershellu.  
   
   1. Na příkazovém řádku tento příkaz prostředí PowerShell, zadejte `Enable-AppxDebug <PackageFullName>`, kde \<Celynazevbalicku > je identifikátor Úplnýnázevbalíčku aplikace.  
   
1. Vyberte **ladění** > **připojit k procesu**.  
   
1. V **připojit k procesu** dialogového okna zadejte vzdáleného zařízení **cíl připojení** pole. 
   
   Můžete zadat název zařízení, vyberte z rozevíracího seznamu v **cíl připojení** pole, nebo vyberte **najít** vyhledat v zařízení **vzdálená připojení** dialogové okno.  
   
1. Chcete-li určit typ kódu, který chcete ladit, vedle položky **připojit k** vyberte **vyberte**.  
   
1. V **vybrat typ kódu** dialogové okno Vyberte buď:
   - **Automaticky určit typ kódu k ladění**, nebo 
   - **Ladit tyto typy kódu**a pak ze seznamu vyberte jeden nebo více typů kódu.  
   
1. V **procesy k dispozici** vyberte aplikaci proces pro ladění.  
   
1. Vyberte **připojit**.  
  
 Visual Studio připojí ladicí program k procesu. Provádění pokračuje, dokud není dosaženo zarážky, můžete ručně pozastavení provádění, dojde k neošetřené výjimce nebo ukončení aplikace.

> [!NOTE]
> Spouštění aplikací jazyka JavaScript v instanci *wwahost.exe* procesu. Pokud je více než jeden JavaScript aplikace spuštěná, musíte znát id číselné procesu (PID) vaší aplikace *wwahost.exe* proces pro připojení k němu.  
> 
> Zavřete všechny ostatní aplikace jazyka JavaScript je nejjednodušší způsob, jak se připojit k vaší aplikaci pro JavaScript. Nebo jste si PID spuštění *wwahost.exe* procesy ve Windows Správce úloh před spuštěním vaší aplikace. Při spuštění aplikace, jeho *wwahost.exe* PID bude ten, který se liší od těch, které jste si předtím poznamenali.  

## <a name="see-also"></a>Viz také:  
 [Ladění aplikací v sadě Visual Studio](../debugger/debug-store-apps-in-visual-studio.md)   