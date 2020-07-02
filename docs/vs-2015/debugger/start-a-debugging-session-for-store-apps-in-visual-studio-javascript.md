---
title: Spuštění ladicí relace pro aplikace pro Store (JavaScript) | Microsoft Docs
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
ms.openlocfilehash: 634051d47b3462e2462c5592448b20f70d09ae71
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/30/2020
ms.locfileid: "85531934"
---
# <a name="start-a-debugging-session-for-store-apps-in-visual-studio-javascript"></a>Spuštění ladicí relace pro aplikace pro Store v sadě Visual Studio (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Platí pro Windows a Windows Phone] (.. /Image/windows_and_phone_content.png "windows_and_phone_content")

 Toto téma popisuje, jak spustit relaci ladění pro aplikace pro Windows Store napsané v jazyce JavaScript a HTML5. Ladění můžete spustit jediným stisknutím klávesy nebo můžete nakonfigurovat relaci ladění pro konkrétní scénáře a pak zvolit způsob, jak aplikaci spustit.

> [!NOTE]
> Pro aplikace napsané v jazyce XAML a v jazyce Visual C#, Visual C++ nebo Visual Basic, přečtěte si téma [spuštění ladicí relace (VB, C#, C++ a XAML)](../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md) .

## <a name="in-this-topic"></a><a name="BKMK_In_this_topic"></a>V tomto tématu
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

## <a name="the-easy-way-to-start-debugging"></a><a name="BKMK_The_easy_way_to_start_debugging"></a>Snadný způsob, jak spustit ladění
 ![Platí jenom pro Windows.](../debugger/media/windows-only-content.png "windows_only_content")

1. Otevřete řešení aplikace v aplikaci Visual Studio.

2. Pokud řešení obsahuje projekty pro Windows Store a aplikace pro Windows Store Phone, ujistěte se, že projekt, který chcete ladit, je spouštěcí projekt. V Průzkumníku řešení vyberte projekt a v místní nabídce zvolte **nastavit jako projekt po spuštění** .

3. Stiskněte klávesu F5.

   ![Platí jenom pro Windows Phone](../debugger/media/phone-only-content.png "phone_only_content")

   Visual Studio vytvoří a spustí aplikaci pomocí připojeného ladicího programu. Spuštění pokračuje, dokud není dosaženo zarážky, ručním zastavením spuštění, neošetřené výjimky nebo ukončení aplikace. Další informace najdete v tématu [rychlý Start: ladění HTML a CSS](../debugger/quickstart-debug-html-and-css.md).

## <a name="configure-the-debugging-session"></a><a name="BKMK_Configure_the_debugging_session"></a>Konfigurace relace ladění
 Protože skript není zkompilován, konfigurace sestavení a nastavení platformy se nepoužijí. Pokud ladíte C++ nebo spravovanou komponentu, nastavte **konfiguraci** pro **ladění** a v dialogovém okně **Konfigurace** vyberte cílovou platformu.

### <a name="open-the-debugging-property-page-for-the-project"></a><a name="BKMK_Open_the_debugging_property_page_for_the_project"></a>Otevřete stránku vlastností ladění pro projekt.

1. V Průzkumník řešení vyberte projekt. V místní nabídce vyberte možnost **vlastnosti**.

2. Rozbalte uzel **Vlastnosti konfigurace** a pak zvolte **ladění** .

### <a name="choose-the-build-configuration-options"></a><a name="BKMK_Choose_the_build_configuration_options"></a>Zvolit možnosti konfigurace sestavení

1. V seznamu **Konfigurace** vyberte **ladění** nebo **(aktivní) ladění**.

2. V seznamu **platforma** vyberte cílovou platformu, pro kterou chcete vytvořit. Ve většině případů je nejlepší volbou **Libovolný procesor** .

### <a name="choose-the-deployment-target"></a><a name="BKMK_Choose_the_deployment_target"></a>Zvolit cíl nasazení
 Můžete nasadit a ladit aplikaci na počítači aplikace Visual Studio, v simulátoru sady Visual Studio v místním počítači nebo ve vzdáleném počítači. Vyberte cíl ze seznamu **ladicího programu ke spuštění** na stránce vlastností **ladění** projektu.

 ![Platí jenom pro Windows.](../debugger/media/windows-only-content.png "windows_only_content")

 V případě aplikace pro Windows Store vyberte ze seznamu **cílové zařízení** jednu z těchto možností:

|Možnost|Popis|
|-|-|
|**Místní počítač**|Ladit aplikaci v aktuální relaci na místním počítači. Viz [spuštění aplikací pro Windows Store na místním počítači](../debugger/run-windows-store-apps-on-the-local-machine.md).|
|**Simulátor**|Ladit aplikaci v simulátoru sady Visual Studio pro [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] aplikace. Simulátor je okno plochy, které umožňuje ladění funkcí zařízení, jako jsou dotyková gesta a rotace zařízení, které nejsou k dispozici na místním počítači. Viz [spuštění aplikací pro Windows Store v simulátoru](../debugger/run-windows-store-apps-in-the-simulator.md).|
|**Vzdálený počítač**|Ladit aplikaci na zařízení, které je připojené k místnímu počítači přes intranet nebo přímo připojené pomocí kabelu Ethernet. Chcete-li provést ladění vzdáleně, musí být na vzdáleném zařízení nainstalovány a spuštěny nástroje Visual Studio Remote Tools. Viz [spuštění aplikací pro Windows Store ve vzdáleném počítači](../debugger/run-windows-store-apps-on-a-remote-machine.md).|

 Pokud zvolíte možnost **vzdálený počítač**, zadejte název nebo IP adresu vzdáleného počítače jedním z následujících způsobů:

- Do pole **název počítače** zadejte název nebo IP adresu vzdáleného počítače.

- V poli **název počítače** vyberte šipku dolů a vyberte **\<Locate...>** . Pak zvolte dialogové okno vzdálený počítač ze seznamu **Vybrat připojení vzdáleného ladicího programu** .

   ![Vybrat připojení vzdáleného ladicího programu](../debugger/media/vsrun-pro-selectremotedebuggerdlg.png "VSRUN_PRO_SelectRemoteDebuggerDlg")

  > [!NOTE]
  > V dialogovém okně vybrat připojení vzdáleného ladicího programu se zobrazí počítače, které jsou v místní podsíti a počítače, které jsou přímo připojené k počítači sady Visual Studio pomocí kabelu Ethernet. Pokud chcete zadat jiný počítač, zadejte název do pole **název počítače** .

  ![Platí jenom pro Windows Phone](../debugger/media/phone-only-content.png "phone_only_content")

  V případě aplikace pro Windows Store Phone vyberte v seznamu **cílové zařízení** položku **zařízení** nebo jeden z emulátorů.

### <a name="choose-the-debugger-to-use"></a><a name="BKMK_Choose_the_debugger_to_use"></a>Vyberte ladicí program, který se má použít.
 Ve výchozím nastavení se ladicí program připojí k kódu JavaScriptu ve vaší aplikaci. Můžete se rozhodnout ladit nativní C++ a spravovaný kód komponent vaší aplikace namísto kódu JavaScriptu. Kód, který chcete ladit, určíte v seznamu **Typ ladicího programu** na stránce vlastností **ladění** projektu aplikace.

 Vyberte jeden z těchto ladicích programů ze seznamu **Typ ladicího programu** :

|Typ|Popis|
|-|-|
|**Pouze skript**|Ladění kódu JavaScriptu ve vaší aplikaci. Spravovaný kód a nativní kód jsou ignorovány.|
|**Pouze nativní**|Ladění nativního kódu C/C++ ve vaší aplikaci. Spravovaný kód a kód jazyka JavaScript jsou ignorovány.|
|**Nativní se skriptem**|Ladění nativního kódu C++ a kódu JavaScriptu ve vaší aplikaci.|
|**Jenom spravovaná**|Ladění spravovaného kódu ve vaší aplikaci. Kód JavaScriptu a nativní kód jazyka C/C++ jsou ignorovány.|
|**Smíšený (spravovaný a nativní)**|Ladění nativního kódu C/C++ a spravovaného kódu ve vaší aplikaci. JavaScriptový kód se ignoruje.|

### <a name="optional-delay-starting-the-app-in-the-debug-session"></a><a name="BKMK__Optional__Delay_starting_app_in_the_debug_session"></a>Volitelné Zpoždění spuštění aplikace v relaci ladění
 Ve výchozím nastavení Visual Studio hned spustí aplikaci při spuštění ladění. Můžete také spustit ladicí relaci, ale zpozdit začátek aplikace. Aplikace se spustí v ladicím programu při spuštění z nabídky Start nebo podle aktivační smlouvy, nebo když ji spustí jiný proces nebo metoda. Můžete také použít zpožděné spuštění k ladění událostí na pozadí v aplikaci, které chcete provést, když aplikace není spuštěná.

 V seznamu **spuštění aplikace** na stránce vlastností **ladění** projektu aplikace určíte, zda chcete odložit spuštění aplikace. Vyberte jednu z těchto možností:

- Pokud chcete odložit spuštění aplikace, klikněte na **ne** .

- Pokud chcete aplikaci spustit hned, vyberte **Ano** .

### <a name="optional-disable-network-loopbacks"></a><a name="BKMK__Optional__Disable_network_loopbacks"></a>Volitelné Zakázat zpětné smyčky sítě
 ![Platí jenom pro Windows.](../debugger/media/windows-only-content.png "windows_only_content")

 Z bezpečnostních důvodů není v aplikaci pro Windows Store, která je nainstalovaná standardním způsobem, povoleno provádět síťová volání do zařízení, na kterém je nainstalovaná. Ve výchozím nastavení vytvoří nasazení sady Visual Studio výjimku z tohoto pravidla pro nasazenou aplikaci. Tato výjimka umožňuje testovat komunikační postupy na jednom počítači. Před odesláním aplikace do Windows Storu byste měli aplikaci testovat bez výjimky.

 Chcete-li odebrat výjimku zpětné smyčky sítě, vyberte možnost **ne** v seznamu **povolená smyčka sítě** na stránce vlastností **ladění** .

## <a name="start-the-debugging-session"></a><a name="BKMK_Start_the_debugging_session"></a>Spuštění relace ladění

### <a name="start-debugging-f5"></a><a name="BKMK_Start_debugging__F5_"></a>Spustit ladění (F5)
 Zvolíte-li možnost **Spustit ladění** v nabídce **ladění** (klávesnice: F5), aplikace Visual Studio spustí aplikaci pomocí připojeného ladicího programu. Spuštění pokračuje, dokud není dosaženo zarážky, ručním zastavením spuštění, neošetřené výjimky nebo ukončení aplikace.

### <a name="start-debugging-f5-but-delay-the-app-start"></a><a name="BKMK_Start_debugging__F5__but_delay_the_app_start"></a>Spustit ladění (F5), ale zpozdit začátek aplikace
 Aplikaci můžete nastavit tak, aby běžela v režimu ladění, ale umožnila ji spustit jinou metodou než ladicí program. Například můžete chtít ladit spuštění aplikace z nabídky Start nebo ladit proces na pozadí v aplikaci bez spuštění aplikace. Při zpoždění spuštění aplikace proveďte tento postup:

1. Na stránce **ladění** vlastností projektu aplikace v seznamu **Spustit aplikaci** vyberte možnost **ne** .

2. V nabídce **ladění** klikněte na příkaz **Spustit ladění** (klávesnice: F5).

3. Spusťte aplikaci z nabídky Start, z prováděcí smlouvy nebo jiného postupu.

   Aplikace se spustí v režimu ladění. Spuštění pokračuje, dokud není dosaženo zarážky, ručním zastavením spuštění, neošetřené výjimky nebo ukončení aplikace.

   . Další informace o ladění úloh na pozadí naleznete v tématu [aktivační událost pozastavit, obnovit a události na pozadí pro Windows Store)](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md).

## <a name="start-an-installed-app-in-the-debugger"></a><a name="BKMK_Start_an_installed_app_in_the_debugger"></a>Spustit nainstalovanou aplikaci v ladicím programu
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

## <a name="attach-the-debugger-to-a-running-app"></a><a name="BKMK_Attach_the_debugger_to_a_running_app_"></a>Připojení ladicího programu ke spuštěné aplikaci
 Chcete-li připojit ladicí program k [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] aplikaci, je nutné použít Správce balíčků, který lze ladit, a nastavit aplikaci tak, aby běžela v režimu ladění. Laděný správce balíčků se instaluje s nástroji Visual Studio Remote Tools.

 Připojení ladicího programu k aplikaci je užitečné v případě, že potřebujete ladit už nainstalovanou aplikaci, například aplikaci, která byla nainstalovaná z Windows Storu. Připojení se vyžaduje v případě, že máte zdrojové soubory aplikace, ale nemáte k dispozici projekt sady Visual Studio pro aplikaci. Můžete mít například vlastní systém sestavení, který nepoužívá projekty nebo řešení sady Visual Studio.

 Připojení k aplikaci:

1. Nastavte aplikaci tak, aby běžela v režimu ladění. To je potřeba udělat, když aplikace není spuštěná.

2. Spusťte aplikaci. Aplikaci můžete spustit z nabídky Start, z prováděcí smlouvy nebo jiné metody.

3. Připojte ladicí program ke spuštěné aplikaci.

### <a name="set-the-app-to-run-in-debug-mode"></a><a name="BKMK_Set_the_app_to_run_in_debug_mode"></a>Nastavení aplikace, která se má spustit v režimu ladění

1. Na zařízení, ve kterém je aplikace nainstalovaná, nainstalujte nástroje Visual Studio Remote Tools. Viz [Instalace nástrojů Remote Tools](https://msdn.microsoft.com/library/windows/apps/hh441469.aspx#BKMK_Installing_the_Remote_Tools).

2. V nabídce Start vyhledejte `Debuggable Package Manager` a spusťte ji.

     Zobrazí se okno PowerShellu správně nakonfigurované pro rutinu AppxDebug.

3. Pokud chcete povolit ladění aplikace, musíte zadat PackageFullName identifikátor aplikace. Pokud chcete zobrazit seznam všech aplikací, které obsahují PackageFullName, zadejte `Get-AppxPackage` na příkazovém řádku PowerShellu.

4. Na příkazovém řádku PowerShellu zadejte `Enable-AppxDebug` *PackageFullName* , kde *PackageFullName* je identifikátor PackageFullName aplikace.

### <a name="attach-the-debugger"></a><a name="BKMK_Attach_the_debugger"></a>Připojit ladicí program

> [!TIP]
> Aplikace JavaScriptu běží v instanci procesu wwahost.exe. Pokud se při připojení k aplikaci spustí jiné aplikace JavaScriptu, budete potřebovat znát číslo ID procesu (PID) wwahost.exe, ve kterém aplikace běží.
>
> Nejjednodušší způsob, jak řešit tuto situaci, je zavřít všechny ostatní aplikace JavaScriptu. V opačném případě můžete před spuštěním aplikace otevřít Správce úloh systému Windows a poznamenat si ID wwahost.exech procesů. Když v dialogovém okně **Dostupné procesy** určíte proces, který se má připojit, bude mít wwahost.exe aplikace ID, které se liší od těch, které jste si poznamenali.

 Postup připojení ladicího programu:

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

4. V seznamu **procesy k dispozici** vyberte příslušný proces **wwahost.exe** . K identifikaci vaší aplikace použijte sloupec **title** .

5. Klikněte na tlačítko **připojit**.

   Visual Studio připojí ladicí program k procesu. Spuštění pokračuje, dokud není dosaženo zarážky, ručním zastavením spuštění, neošetřené výjimky nebo ukončení aplikace.

## <a name="see-also"></a>Viz také
 [Spuštění řízení v relaci ladění (JavaScript)](../debugger/control-execution-of-a-store-app-in-a-visual-studio-debug-session-for-windows-store-apps-javascript.md) [rychlý Start: ladění aktivačních událostí HTML a CSS](../debugger/quickstart-debug-html-and-css.md) [Aktivace, obnovení a události na pozadí pro Windows Store)](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md) [ladění aplikací v aplikaci Visual Studio](../debugger/debug-store-apps-in-visual-studio.md)
