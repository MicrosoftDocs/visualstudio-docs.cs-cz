---
title: Spuštění ladicí relace pro aplikace pro Store (JavaScript) | Dokumentace Microsoftu
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
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
manager: jillfra
ms.openlocfilehash: 4b4e861c8985ee37a8c2d9b7f9286d6284bb4f91
ms.sourcegitcommit: 3154387056160bf4c36ac8717a7fdc0cd9faf3f9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2020
ms.locfileid: "78406338"
---
# <a name="start-a-debugging-session-for-store-apps-in-visual-studio-javascript"></a>Spuštění ladicí relace pro aplikace pro Store v sadě Visual Studio (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Platí pro Windows a Windows Phone] (.. /Image/windows_and_phone_content.png "windows_and_phone_content")

 Toto téma popisuje způsob spuštění ladicí relace pro aplikace Windows Store v JavaScriptu a HTML5. Ladění jednoho jedním stisknutím tlačítka lze spustit, nebo můžete nakonfigurovat ladicí relace pro konkrétní scénáře a pak zvolte způsob, jak spustit aplikaci.

> [!NOTE]
> V případě aplikací napsaných v C#jazyce XAML C++a vizuálů, vizuálů nebo Visual Basic, přečtěte si téma [spuštění C#ladicí C++ relace (VB, a XAML)](../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md) .

## <a name="BKMK_In_this_topic"></a>V tomto tématu
 [V tomto tématu](#BKMK_In_this_topic)

 [Snadný způsob, jak spustit ladění](#BKMK_The_easy_way_to_start_debugging)

 [Konfigurace relace ladění](#BKMK_Configure_the_debugging_session)

- [Otevřete stránku vlastností ladění pro projekt.](#BKMK_Open_the_debugging_property_page_for_the_project)

- [Zvolit možnosti konfigurace sestavení](#BKMK_Choose_the_build_configuration_options)

- [Zvolit cíl nasazení](#BKMK_Choose_the_deployment_target)

- [Vyberte ladicí program, který se má použít.](#BKMK_Choose_the_debugger_to_use)

- [Volitelné Zpoždění spuštění aplikace v relaci ladění](#BKMK__Optional__Delay_starting_app_in_the_debug_session)

- [Volitelné Zakázat zpětné smyčky sítě](#BKMK__Optional__Disable_network_loopbacks)

  [Spuštění relace ladění](#BKMK_Start_the_debugging_session)

- [Spustit ladění (F5)](#BKMK_Start_debugging__F5_)

- [Spustit ladění (F5), ale zpozdit začátek aplikace](#BKMK_Start_debugging__F5__but_delay_the_app_start)

  [Spustit nainstalovanou aplikaci v ladicím programu](#BKMK_Start_an_installed_app_in_the_debugger)

  [Připojení ladicího programu ke spuštěné aplikaci](#BKMK_Attach_the_debugger_to_a_running_app_)

- [Nastavení aplikace, která se má spustit v režimu ladění](#BKMK_Set_the_app_to_run_in_debug_mode)

- [Připojit ladicí program](#BKMK_Attach_the_debugger)

## <a name="BKMK_The_easy_way_to_start_debugging"></a>Snadný způsob, jak spustit ladění
 ![Platí jenom pro Windows.](../debugger/media/windows-only-content.png "windows_only_content")

1. Otevřete aplikaci řešení v sadě Visual Studio.

2. Pokud řešení obsahuje projekty pro aplikace pro Windows Store a Windows Store Phone, ujistěte se, že je projekt, který chcete ladit spuštění projektu. V Průzkumníku řešení vyberte projekt a v místní nabídce zvolte **nastavit jako projekt po spuštění** .

3. Stiskněte klávesu F5.

   ![Platí jenom pro Windows Phone](../debugger/media/phone-only-content.png "phone_only_content")

   Visual Studio vytvoří a spustí aplikaci s připojeným ladícím nástrojem. Provádění pokračuje, dokud není dosaženo zarážky, můžete ručně pozastavení provádění, dojde k neošetřené výjimce nebo ukončení aplikace. Další informace najdete v tématu [rychlý Start: ladění HTML a CSS](../debugger/quickstart-debug-html-and-css.md).

## <a name="BKMK_Configure_the_debugging_session"></a>Konfigurace relace ladění
 Protože skriptu není kompilována, nemůžete použít nastavení konfigurace a platforma sestavení. Při C++ ladění nebo spravované součásti nastavte **konfiguraci** pro **ladění** a v dialogovém okně **Konfigurace** vyberte cílovou platformu.

### <a name="BKMK_Open_the_debugging_property_page_for_the_project"></a>Otevřete stránku vlastností ladění pro projekt.

1. V Průzkumníku řešení vyberte projekt. V místní nabídce vyberte možnost **vlastnosti**.

2. Rozbalte uzel **Vlastnosti konfigurace** a pak zvolte **ladění** .

### <a name="BKMK_Choose_the_build_configuration_options"></a>Zvolit možnosti konfigurace sestavení

1. V seznamu **Konfigurace** vyberte **ladění** nebo **(aktivní) ladění**.

2. V seznamu **platforma** vyberte cílovou platformu, pro kterou chcete vytvořit. Ve většině případů je nejlepší volbou **Libovolný procesor** .

### <a name="BKMK_Choose_the_deployment_target"></a>Zvolit cíl nasazení
 Můžete nasadit a ladit aplikaci na počítač s Visual Studio, simulátoru sady Visual Studio na místním počítači nebo ve vzdáleném počítači. Vyberte cíl ze seznamu **ladicího programu ke spuštění** na stránce vlastností **ladění** projektu.

 ![Platí jenom pro Windows.](../debugger/media/windows-only-content.png "windows_only_content")

 V případě aplikace pro Windows Store vyberte ze seznamu **cílové zařízení** jednu z těchto možností:

|||
|-|-|
|**Místní počítač**|Ladění aplikace v aktuální relaci na místním počítači. Viz [spuštění aplikací pro Windows Store na místním počítači](../debugger/run-windows-store-apps-on-the-local-machine.md).|
|**Simulátor**|Ladit aplikaci v simulátoru sady Visual Studio pro aplikace [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)]. Simulátor není okno klasické pracovní plochy, která umožňuje ladit funkce zařízení, jako je například gesta dotykového ovládání a otočení obrazovky –, které nejsou k dispozici v místním počítači. Viz [spuštění aplikací pro Windows Store v simulátoru](../debugger/run-windows-store-apps-in-the-simulator.md).|
|**Vzdálený počítač**|Ladění aplikací na zařízení, který je připojený k místním počítači v síti intranet nebo přímo pomocí kabelu Ethernet. Pro vzdálené ladění, vzdálené nástroje sady Visual Studio musí být nainstalovaná a spuštěná na vzdáleném zařízení. Viz [spuštění aplikací pro Windows Store ve vzdáleném počítači](../debugger/run-windows-store-apps-on-a-remote-machine.md).|

 Pokud zvolíte možnost **vzdálený počítač**, zadejte název nebo IP adresu vzdáleného počítače jedním z následujících způsobů:

- Do pole **název počítače** zadejte název nebo IP adresu vzdáleného počítače.

- V poli **název počítače** vyberte šipku dolů a vyberte **\<najít... >** . Pak zvolte dialogové okno vzdálený počítač ze seznamu **Vybrat připojení vzdáleného ladicího programu** .

   ![Vybrat připojení vzdáleného ladicího programu](../debugger/media/vsrun-pro-selectremotedebuggerdlg.png "VSRUN_PRO_SelectRemoteDebuggerDlg")

  > [!NOTE]
  > V dialogovém okně vyberte připojení vzdáleného ladicího programu zobrazí počítače, které jsou na místní podsíť a počítačů, které jsou připojené přímo k sadě Visual Studio počítači pomocí kabelu Ethernet. Pokud chcete zadat jiný počítač, zadejte název do pole **název počítače** .

  ![Platí jenom pro Windows Phone](../debugger/media/phone-only-content.png "phone_only_content")

  V případě aplikace pro Windows Store Phone vyberte v seznamu **cílové zařízení** položku **zařízení** nebo jeden z emulátorů.

### <a name="BKMK_Choose_the_debugger_to_use"></a>Vyberte ladicí program, který se má použít.
 Ve výchozím nastavení ladicí program připojí do kódu jazyka JavaScript v aplikaci. Můžete ladit nativní kód C++ a spravovaném kódu komponentami vaší aplikace namísto kódu jazyka JavaScript. Kód, který chcete ladit, určíte v seznamu **Typ ladicího programu** na stránce vlastností **ladění** projektu aplikace.

 Vyberte jeden z těchto ladicích programů ze seznamu **Typ ladicího programu** :

|||
|-|-|
|**Pouze skript**|Ladění kódu JavaScript ve vaší aplikaci. Nativní a spravovaný kód jsou ignorovány.|
|**Pouze nativní**|Ladění nativního kódu C/C++ v aplikaci. Spravovaný kód a kód jazyka JavaScript jsou ignorovány.|
|**Nativní se skriptem**|Ladění nativního kódu jazyka C++ a jazyka JavaScript v aplikaci.|
|**Jenom spravovaná**|Ladit spravovaný kód ve vaší aplikaci. Kód jazyka JavaScript a nativního kódu C/C++ jsou ignorovány.|
|**Smíšený (spravovaný a nativní)**|Ladění nativního kódu C/C++ a spravovaném kódu ve vaší aplikaci. Kód jazyka JavaScript se ignoruje.|

### <a name="BKMK__Optional__Delay_starting_app_in_the_debug_session"></a>Volitelné Zpoždění spuštění aplikace v relaci ladění
 Ve výchozím nastavení spustí aplikace Visual Studio okamžitě aplikace při spuštění ladění. Můžete také spustit relaci ladění, ale zpoždění spuštění vaší aplikace. Když se spustí z nabídky Start nebo kontrakt aktivace nebo při spuštění jiným procesem nebo metoda je aplikace spuštěná v ladicím programu. Také vám pomůže zpožděné spuštění ladění události na pozadí ve vaší aplikaci, kterou chcete dojít, když není aplikace spuštěna.

 V seznamu **spuštění aplikace** na stránce vlastností **ladění** projektu aplikace určíte, zda chcete odložit spuštění aplikace. Vyberte jednu z těchto možností:

- Pokud chcete odložit spuštění aplikace, klikněte na **ne** .

- Pokud chcete aplikaci spustit hned, vyberte **Ano** .

### <a name="BKMK__Optional__Disable_network_loopbacks"></a>Volitelné Zakázat zpětné smyčky sítě
 ![Platí jenom pro Windows.](../debugger/media/windows-only-content.png "windows_only_content")

 Z bezpečnostních důvodů aplikace Windows Store, nainstalovaný ve standardním způsobem nepovoluje volat síťových zařízení, ve kterých je nainstalované. Ve výchozím nastavení nasazení sady Visual Studio vytvoří výjimku z tohoto pravidla pro aplikace nasazené. Tato výjimka umožňuje testovat postupy komunikace na jednom počítači. Před odesláním aplikace do Windows Store, měli byste otestovat vaši aplikaci bez výjimky.

 Chcete-li odebrat výjimku zpětné smyčky sítě, vyberte možnost **ne** v seznamu **povolená smyčka sítě** na stránce vlastností **ladění** .

## <a name="BKMK_Start_the_debugging_session"></a>Spuštění relace ladění

### <a name="BKMK_Start_debugging__F5_"></a>Spustit ladění (F5)
 Zvolíte-li možnost **Spustit ladění** v nabídce **ladění** (klávesnice: F5), aplikace Visual Studio spustí aplikaci pomocí připojeného ladicího programu. Provádění pokračuje, dokud není dosaženo zarážky, můžete ručně pozastavení provádění, dojde k neošetřené výjimce nebo ukončení aplikace.

### <a name="BKMK_Start_debugging__F5__but_delay_the_app_start"></a>Spustit ladění (F5), ale zpozdit začátek aplikace
 Můžete nastavit aplikaci spustit v režimu ladění, ale ten spustit pomocí jiné metody než ladicí program. Můžete například, chcete-li ladit spuštění vaší aplikace z nabídky Start nebo chcete-li ladit proces na pozadí v aplikaci bez spuštění aplikace. Chcete-li zpoždění spuštění aplikace, postupujte takto:

1. Na stránce **ladění** vlastností projektu aplikace v seznamu **Spustit aplikaci** vyberte možnost **ne** .

2. V nabídce **ladění** klikněte na příkaz **Spustit ladění** (klávesnice: F5).

3. Aplikaci spusťte z nabídky Start, kontrakt provádění nebo jiný postup.

   Spuštění aplikace v režimu ladění. Provádění pokračuje, dokud není dosaženo zarážky, můžete ručně pozastavení provádění, dojde k neošetřené výjimce nebo ukončení aplikace.

   . Další informace o ladění úloh na pozadí naleznete v tématu [aktivační událost pozastavit, obnovit a události na pozadí pro Windows Store)](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md).

## <a name="BKMK_Start_an_installed_app_in_the_debugger"></a>Spustit nainstalovanou aplikaci v ladicím programu
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

## <a name="BKMK_Attach_the_debugger_to_a_running_app_"></a>Připojení ladicího programu ke spuštěné aplikaci
 Chcete-li připojit ladicí program k aplikaci [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)], je nutné použít Správce balíčků, který lze ladit, a nastavit aplikaci tak, aby běžela v režimu ladění. Laditelný Správce balíčků je nainstalované s Visual Studio Remote Tools.

 Připojování ladicího programu do aplikace je užitečné, když budete potřebovat k ladění aplikace již nainstalována, jako jsou aplikace nainstalované z Windows uložit. Připojení se vyžaduje, pokud mají zdrojové soubory pro aplikaci, ale není nutné projekt sady Visual Studio pro aplikaci. Například může mít vlastní sestavovací systém, který nepoužívá projektů sady Visual Studio nebo řešení.

 Připojit k aplikaci:

1. Nastavte aplikaci spustit v režimu ladění. To je nutné provést při není aplikace spuštěna.

2. Spusťte aplikaci. Aplikaci můžete spustit z nabídky Start, kontrakt provádění nebo některé jiné metody.

3. Připojte ladicí modul k běžící aplikaci.

### <a name="BKMK_Set_the_app_to_run_in_debug_mode"></a>Nastavení aplikace, která se má spustit v režimu ladění

1. Nainstalujte na zařízení nainstalovanou aplikaci Visual Studio Remote Tools. Viz [Instalace nástrojů Remote Tools](https://msdn.microsoft.com/library/windows/apps/hh441469.aspx#BKMK_Installing_the_Remote_Tools).

2. V nabídce Start vyhledejte `Debuggable Package Manager` a pak ho spusťte.

     Zobrazí se okno prostředí PowerShell správně nakonfigurovaný pro rutiny AppxDebug.

3. Pokud chcete povolit ladění aplikace, je nutné zadat identifikátor Úplnýnázevbalíčku aplikace. Pokud chcete zobrazit seznam všech aplikací, které obsahují PackageFullName, zadejte do příkazového řádku PowerShellu `Get-AppxPackage`.

4. Na příkazovém řádku PowerShellu zadejte `Enable-AppxDebug` *PackageFullName* , kde *PackageFullName* je identifikátor PackageFullName aplikace.

### <a name="BKMK_Attach_the_debugger"></a>Připojit ladicí program

> [!TIP]
> JavaScript aplikace spusťte v instanci procesu wwahost.exe. Pokud jiných aplikací jazyka JavaScript jsou spuštěny po připojení k aplikaci, musíte znát id číselné procesu (PID) wwahost.exe, na kterém aplikace běží v.
>
> Zavřete všechny ostatní aplikace jazyka JavaScript je nejjednodušší způsob, jak zacházet s touto situací. Předtím, než spustíte aplikaci a poznamenejte si ID procesů wwahost.exe, v opačném případě můžete otevřít Správce úloh Windows. Když v dialogovém okně **Dostupné procesy** určíte proces, který se má připojit, bude mít wwahost. exe aplikace ID, které se liší od těch, které jste si poznamenali.

 Připojení ladicího programu:

1. V nabídce **ladění** vyberte možnost **připojit k procesu**.

    Zobrazí se dialogové okno **připojit k procesu** .

2. Pokud se chcete připojit k aplikaci na vzdáleném zařízení, zadejte vzdálené zařízení do pole **kvalifikátor** . Můžete:

   - Zadejte název do pole **kvalifikátor** .

   - Vyberte šipku dolů v poli **kvalifikátor** a vyberte zařízení ze seznamu zařízení, ke kterým jste se připojili.

   - Vyberte **Najít** , pokud chcete zařízení vybrat ze seznamu zařízení v místní podsíti.

3. V poli **připojit k** zadejte typ kódu, který chcete ladit.

    Zvolte **Vybrat** a pak proveďte jednu z následujících akcí:

   - Vyberte **automaticky určit typ kódu, který se má ladit** .

   - Zvolte možnost **ladit tyto typy kódu** a pak v seznamu vyberte jeden nebo více typů.

4. V seznamu **procesy k dispozici** vyberte příslušný proces **wwahost. exe** . K identifikaci vaší aplikace použijte sloupec **title** .

5. Klikněte na tlačítko **připojit**.

   Visual Studio připojí ladicí program k procesu. Provádění pokračuje, dokud není dosaženo zarážky, můžete ručně pozastavení provádění, dojde k neošetřené výjimce nebo ukončení aplikace.

## <a name="see-also"></a>Viz také
 [Spuštění řízení v relaci ladění (JavaScript)](../debugger/control-execution-of-a-store-app-in-a-visual-studio-debug-session-for-windows-store-apps-javascript.md) [rychlý Start: ladění aktivačních událostí HTML a CSS](../debugger/quickstart-debug-html-and-css.md) [Aktivace, obnovení a události na pozadí pro Windows Store)](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md) [ladění aplikací v aplikaci Visual Studio](../debugger/debug-store-apps-in-visual-studio.md)
