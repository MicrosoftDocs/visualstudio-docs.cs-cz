---
title: Spuštění ladicí relace pro aplikace pro Store (JavaScript) | Dokumentace Microsoftu
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
- vs.debug.installedapppackagelauncher
- vs.debug.error.wwahost_scriptdebuggingdisabled
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: fb91203f-2cf4-44d3-8ed9-93bc5aaa50b8
caps.latest.revision: 27
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6e4105d8dda298dd0235acd113a9a0612265fbc0
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53055888"
---
# <a name="start-a-debugging-session-for-store-apps-in-visual-studio-javascript"></a>Spuštění ladicí relace pro aplikace pro Store v sadě Visual Studio (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Platí pro Windows a Windows Phone] (.. /Image/windows_and_phone_content.png "windows_and_phone_content")

 Toto téma popisuje způsob spuštění ladicí relace pro aplikace Windows Store v JavaScriptu a HTML5. Ladění jednoho jedním stisknutím tlačítka lze spustit, nebo můžete nakonfigurovat ladicí relace pro konkrétní scénáře a pak zvolte způsob, jak spustit aplikaci.

> [!NOTE]
>  Pro aplikace napsané v XAML a Visual C#, Visual C++ nebo Visual Basic, naleznete v tématu [spustíte relaci ladění (VB, C#, C++ a XAML)](../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md)

##  <a name="BKMK_In_this_topic"></a> V tomto tématu
 [V tomto tématu](#BKMK_In_this_topic)

 [Snadný způsob, jak spustit ladění](#BKMK_The_easy_way_to_start_debugging)

 [Konfigurace relace ladění](#BKMK_Configure_the_debugging_session)

- [Otevření stránky vlastnosti ladění pro projekt](#BKMK_Open_the_debugging_property_page_for_the_project)

- [Vybrat možnosti konfigurace sestavení](#BKMK_Choose_the_build_configuration_options)

- [Zvolte cíl nasazení](#BKMK_Choose_the_deployment_target)

- [Zvolte možnost použít ladicí program](#BKMK_Choose_the_debugger_to_use)

- [(Volitelné) Zpoždění spuštění aplikace během relace ladění](#BKMK__Optional__Delay_starting_app_in_the_debug_session)

- [(Volitelné) Zakázat vytváření zpětných sítě smyček](#BKMK__Optional__Disable_network_loopbacks)

  [Spuštění ladicí relace](#BKMK_Start_the_debugging_session)

- [Spustit ladění (F5)](#BKMK_Start_debugging__F5_)

- [Spustit ladění (F5), ale zpoždění spuštění aplikace](#BKMK_Start_debugging__F5__but_delay_the_app_start)

  [Spustit nainstalovanou aplikaci v ladicím programu](#BKMK_Start_an_installed_app_in_the_debugger)

  [Připojit ladicí modul k běžící aplikaci](#BKMK_Attach_the_debugger_to_a_running_app_)

- [Nastavte aplikaci spustit v režimu ladění](#BKMK_Set_the_app_to_run_in_debug_mode)

- [Připojit ladicí program](#BKMK_Attach_the_debugger)

##  <a name="BKMK_The_easy_way_to_start_debugging"></a> Snadný způsob, jak spustit ladění
 ![Platí pouze pro Windows](../debugger/media/windows-only-content.png "windows_only_content")

1. Otevřete aplikaci řešení v sadě Visual Studio.

2. Pokud řešení obsahuje projekty pro aplikace pro Windows Store a Windows Store Phone, ujistěte se, že je projekt, který chcete ladit spuštění projektu. V řešení prozkoumat, vyberte projekt a klikněte na tlačítko **nastavit jako spouštěný projekt** v místní nabídce.

3. Stiskněte klávesu F5.

   ![Platí pouze pro Windows Phone](../debugger/media/phone-only-content.png "phone_only_content")

   Visual Studio vytvoří a spustí aplikaci s připojeným ladícím nástrojem. Provádění pokračuje, dokud není dosaženo zarážky, můžete ručně pozastavení provádění, dojde k neošetřené výjimce nebo ukončení aplikace. Další informace najdete v tématu [rychlý start: ladění kódu HTML a CSS](../debugger/quickstart-debug-html-and-css.md).

##  <a name="BKMK_Configure_the_debugging_session"></a> Konfigurace relace ladění
 Protože skriptu není kompilována, nemůžete použít nastavení konfigurace a platforma sestavení. Pokud ladíte C++ nebo spravované součásti, nastavte **konfigurace** k **ladění** a zvolte cílovou platformu z **konfigurace** dialogového okna.

###  <a name="BKMK_Open_the_debugging_property_page_for_the_project"></a> Otevření stránky vlastnosti ladění pro projekt

1.  V Průzkumníku řešení vyberte projekt. V místní nabídce zvolte **vlastnosti**.

2.  Rozbalte **vlastnosti konfigurace** uzlu a pak zvolte **ladění**

###  <a name="BKMK_Choose_the_build_configuration_options"></a> Vybrat možnosti konfigurace sestavení

1.  Z **konfigurace** klikněte na položku **ladění** nebo **(aktivní) ladění**.

2.  Z **platformy** seznamu zvolte cílovou platformu pro vytváření pro. Ve většině případů **jakýkoli procesor** je nejlepší volbou.

###  <a name="BKMK_Choose_the_deployment_target"></a> Zvolte cíl nasazení
 Můžete nasadit a ladit aplikaci na počítač s Visual Studio, simulátoru sady Visual Studio na místním počítači nebo ve vzdáleném počítači. Zvolte cíle z **ladicí program ke spuštění** seznamu **ladění** stránku vlastností pro projekt.

 ![Platí pouze pro Windows](../debugger/media/windows-only-content.png "windows_only_content")

 Aplikace pro Windows Store, zvolte jednu z těchto možností z **cílové zařízení** seznamu:

|||
|-|-|
|**Místní počítač**|Ladění aplikace v aktuální relaci na místním počítači. Zobrazit [aplikace Windows Store spustit na místním počítači](../debugger/run-windows-store-apps-on-the-local-machine.md).|
|**Simulátor**|Ladění aplikace v simulátoru sady Visual Studio pro [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] aplikace. Simulátor není okno klasické pracovní plochy, která umožňuje ladit funkce zařízení, jako je například gesta dotykového ovládání a otočení obrazovky –, které nejsou k dispozici v místním počítači. Zobrazit [aplikace spustit Windows Store v simulátoru](../debugger/run-windows-store-apps-in-the-simulator.md).|
|**Vzdálený počítač**|Ladění aplikací na zařízení, který je připojený k místním počítači v síti intranet nebo přímo pomocí kabelu Ethernet. Pro vzdálené ladění, vzdálené nástroje sady Visual Studio musí být nainstalovaná a spuštěná na vzdáleném zařízení. Zobrazit [aplikace Windows Store spustit ve vzdáleném počítači](../debugger/run-windows-store-apps-on-a-remote-machine.md).|

 Pokud se rozhodnete **vzdálený počítač**, zadejte název nebo IP adresu vzdáleného počítače v jednom z těchto způsobů:

- Zadejte název nebo IP adresu vzdáleného počítače v **název počítače** pole.

- Klikněte na šipku dolů v **název počítače** pole a tlačítko  **\<najít... >**. Vyberte vzdálený počítač z **vyberte připojení vzdáleného ladicího programu** dialogové okno.

   ![Vyberte připojení vzdáleného ladicího programu](../debugger/media/vsrun-pro-selectremotedebuggerdlg.png "VSRUN_PRO_SelectRemoteDebuggerDlg")

  > [!NOTE]
  >  V dialogovém okně vyberte připojení vzdáleného ladicího programu zobrazí počítače, které jsou na místní podsíť a počítačů, které jsou připojené přímo k sadě Visual Studio počítači pomocí kabelu Ethernet. Chcete-li určit jiný počítač, zadejte název do **název počítače** pole.

  ![Platí pouze pro Windows Phone](../debugger/media/phone-only-content.png "phone_only_content")

  Pro aplikace Windows Store Phone, zvolte **zařízení** nebo jeden z emulátorů z **cílové zařízení** seznamu.

###  <a name="BKMK_Choose_the_debugger_to_use"></a> Zvolte možnost použít ladicí program
 Ve výchozím nastavení ladicí program připojí do kódu jazyka JavaScript v aplikaci. Můžete ladit nativní kód C++ a spravovaném kódu komponentami vaší aplikace namísto kódu jazyka JavaScript. Zadejte kód pro ladění ve **typ ladicího programu** seznamu **ladění** stránku vlastností projektu aplikace.

 Vyberte jednu z těchto ladicí programy z **typ ladicího programu** seznamu:

|||
|-|-|
|**Jenom skript**|Ladění kódu JavaScript ve vaší aplikaci. Nativní a spravovaný kód jsou ignorovány.|
|**Pouze nativní**|Ladění nativního kódu C/C++ v aplikaci. Spravovaný kód a kód jazyka JavaScript jsou ignorovány.|
|**Nativní pomocí skriptu**|Ladění nativního kódu jazyka C++ a jazyka JavaScript v aplikaci.|
|**Režim pouze spravovaný**|Ladit spravovaný kód ve vaší aplikaci. Kód jazyka JavaScript a nativního kódu C/C++ jsou ignorovány.|
|**Smíšený (spravovaný a nativní)**|Ladění nativního kódu C/C++ a spravovaném kódu ve vaší aplikaci. Kód jazyka JavaScript se ignoruje.|

###  <a name="BKMK__Optional__Delay_starting_app_in_the_debug_session"></a> (Volitelné) Zpoždění spuštění aplikace během relace ladění
 Ve výchozím nastavení spustí aplikace Visual Studio okamžitě aplikace při spuštění ladění. Můžete také spustit relaci ladění, ale zpoždění spuštění vaší aplikace. Když se spustí z nabídky Start nebo kontrakt aktivace nebo při spuštění jiným procesem nebo metoda je aplikace spuštěná v ladicím programu. Také vám pomůže zpožděné spuštění ladění události na pozadí ve vaší aplikaci, kterou chcete dojít, když není aplikace spuštěna.

 Určete, jestli zpoždění spuštění aplikace v rámci **spustit aplikaci** seznamu **ladění** stránku vlastností projektu aplikace. Vyberte jednu z těchto možností:

-   Zvolte **ne** zpoždění spuštění vaší aplikace.

-   Zvolte **Ano** aplikaci spustit okamžitě.

###  <a name="BKMK__Optional__Disable_network_loopbacks"></a> (Volitelné) Zakázat vytváření zpětných sítě smyček
 ![Platí pouze pro Windows](../debugger/media/windows-only-content.png "windows_only_content")

 Z bezpečnostních důvodů aplikace Windows Store, nainstalovaný ve standardním způsobem nepovoluje volat síťových zařízení, ve kterých je nainstalované. Ve výchozím nastavení nasazení sady Visual Studio vytvoří výjimku z tohoto pravidla pro aplikace nasazené. Tato výjimka umožňuje testovat postupy komunikace na jednom počítači. Před odesláním aplikace do Windows Store, měli byste otestovat vaši aplikaci bez výjimky.

 Chcete-li odebrat výjimku zpětnou smyčku sítě, zvolte **č** z **povolit zpětnou smyčku sítě** seznamu **ladění** stránku vlastností.

##  <a name="BKMK_Start_the_debugging_session"></a> Spuštění ladicí relace

###  <a name="BKMK_Start_debugging__F5_"></a> Spustit ladění (F5)
 Při výběru **spustit ladění** na **ladění** nabídce (klávesnice: F5), Visual Studio spustí aplikaci s připojeným ladícím nástrojem. Provádění pokračuje, dokud není dosaženo zarážky, můžete ručně pozastavení provádění, dojde k neošetřené výjimce nebo ukončení aplikace.

###  <a name="BKMK_Start_debugging__F5__but_delay_the_app_start"></a> Spustit ladění (F5), ale zpoždění spuštění aplikace
 Můžete nastavit aplikaci spustit v režimu ladění, ale ten spustit pomocí jiné metody než ladicí program. Můžete například, chcete-li ladit spuštění vaší aplikace z nabídky Start nebo chcete-li ladit proces na pozadí v aplikaci bez spuštění aplikace. Chcete-li zpoždění spuštění aplikace, postupujte takto:

1. Na **ladění** stránky aplikace vlastnosti projektu, zvolte **ne** z **spustit aplikaci** seznamu.

2. Zvolte **spustit ladění** na **ladění** nabídce (klávesnice: F5).

3. Aplikaci spusťte z nabídky Start, kontrakt provádění nebo jiný postup.

   Spuštění aplikace v režimu ladění. Provádění pokračuje, dokud není dosaženo zarážky, můžete ručně pozastavení provádění, dojde k neošetřené výjimce nebo ukončení aplikace.

   . Další informace o ladění úlohy na pozadí, naleznete v tématu [aktivační události pozastavení, obnovení a událostí na pozadí pro Windows Store)](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md).

##  <a name="BKMK_Start_an_installed_app_in_the_debugger"></a> Spustit nainstalovanou aplikaci v ladicím programu
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

##  <a name="BKMK_Attach_the_debugger_to_a_running_app_"></a> Připojit ladicí modul k běžící aplikaci
 Připojit ladicí program [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] aplikace, musíte použít laditelný Správce balíčků pro nastavení aplikace pro spuštění v režimu ladění. Laditelný Správce balíčků je nainstalované s Visual Studio Remote Tools.

 Připojování ladicího programu do aplikace je užitečné, když budete potřebovat k ladění aplikace již nainstalována, jako jsou aplikace nainstalované z Windows uložit. Připojení se vyžaduje, pokud mají zdrojové soubory pro aplikaci, ale není nutné projekt sady Visual Studio pro aplikaci. Například může mít vlastní sestavovací systém, který nepoužívá projektů sady Visual Studio nebo řešení.

 Připojit k aplikaci:

1.  Nastavte aplikaci spustit v režimu ladění. To je nutné provést při není aplikace spuštěna.

2.  Spusťte aplikaci. Aplikaci můžete spustit z nabídky Start, kontrakt provádění nebo některé jiné metody.

3.  Připojte ladicí modul k běžící aplikaci.

###  <a name="BKMK_Set_the_app_to_run_in_debug_mode"></a> Nastavte aplikaci spustit v režimu ladění

1.  Nainstalujte na zařízení nainstalovanou aplikaci Visual Studio Remote Tools. Zobrazit [instalace vzdálených nástrojů](http://msdn.microsoft.com/library/windows/apps/hh441469.aspx#BKMK_Installing_the_Remote_Tools).

2.  V nabídce Start, vyhledejte `Debuggable Package Manager` a spusťte jej.

     Zobrazí se okno prostředí PowerShell správně nakonfigurovaný pro rutiny AppxDebug.

3.  Pokud chcete povolit ladění aplikace, je nutné zadat identifikátor Úplnýnázevbalíčku aplikace. Chcete-li zobrazit seznam všech aplikací, které zahrnuje Úplnýnázevbalíčku, zadejte `Get-AppxPackage` řádku Powershellu.

4.  Na příkazovém řádku tento příkaz prostředí PowerShell, zadejte `Enable-AppxDebug` *PackageFullName* kde *PackageFullName* je identifikátor Úplnýnázevbalíčku aplikace.

###  <a name="BKMK_Attach_the_debugger"></a> Připojit ladicí program

> [!TIP]
>  JavaScript aplikace spusťte v instanci procesu wwahost.exe. Pokud jiných aplikací jazyka JavaScript jsou spuštěny po připojení k aplikaci, musíte znát id číselné procesu (PID) wwahost.exe, na kterém aplikace běží v.
>
>  Zavřete všechny ostatní aplikace jazyka JavaScript je nejjednodušší způsob, jak zacházet s touto situací. Předtím, než spustíte aplikaci a poznamenejte si ID procesů wwahost.exe, v opačném případě můžete otevřít Správce úloh Windows. Pokud zadáte proces pro připojení v **procesy k dispozici** dialogovém okně wwahost.exe aplikace bude mít id, které se liší od těch, které jste si poznamenali.

 Připojení ladicího programu:

1. Na **ladění** nabídce zvolte **připojit k procesu**.

    **Připojit k procesu** zobrazí se dialogové okno.

2. Připojit k aplikaci na vzdáleném zařízení, zadejte vzdáleného zařízení **kvalifikátor** pole. Můžeš:

   -   Zadejte název do pole **kvalifikátor** pole.

   -   Zvolte šipku dolů u **kvalifikátor** a vyberte zařízení ze seznamu zařízení, které jste připojili k před.

   -   Zvolte **najít** pro výběr zařízení ze seznamu zařízení v místní podsíti.

3. Zadejte kód, který chcete ladit v **připojit k** pole.

    Zvolte **vyberte** a udělejte jednu z následujících akcí:

   -   Zvolte **automaticky určit typ kódu k ladění**

   -   Zvolte **ladit tyto typy kódu** a ze seznamu vyberte jeden nebo více typů.

4. V **procesy k dispozici** , zvolte odpovídající **wwahost.exe** procesu. Použití **název** sloupec k identifikaci vaší aplikace.

5. Zvolte **připojit**.

   Visual Studio připojí ladicí program k procesu. Provádění pokračuje, dokud není dosaženo zarážky, můžete ručně pozastavení provádění, dojde k neošetřené výjimce nebo ukončení aplikace.

## <a name="see-also"></a>Viz také
 [Řízení spouštění v relaci ladění (JavaScript)](../debugger/control-execution-of-a-store-app-in-a-visual-studio-debug-session-for-windows-store-apps-javascript.md) [rychlý start: ladění kódu HTML a CSS](../debugger/quickstart-debug-html-and-css.md) [aktivační události pozastavení, obnovení a událostí na pozadí pro Windows Store)](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md) [ladění aplikací v Visual Studio](../debugger/debug-store-apps-in-visual-studio.md)
