---
title: Spuštění relace ladění aplikací pro Store (JavaScript) | Dokumenty společnosti Microsoft
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
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/13/2020
ms.locfileid: "79302481"
---
# <a name="start-a-debugging-session-for-store-apps-in-visual-studio-javascript"></a>Spuštění ladicí relace pro aplikace pro Store v sadě Visual Studio (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Platí pro Windows a Windows Phone](.. /Obrázek/windows_and_phone_content.png "windows_and_phone_content")

 Toto téma popisuje, jak spustit relaci ladění aplikací pro Windows Store napsaných v Jazyce JavaScript a HTML5. Můžete začít ladění s jedním úhozem, nebo můžete nakonfigurovat relaci ladění pro konkrétní scénáře a pak zvolit způsob spuštění aplikace.

> [!NOTE]
> Pro aplikace napsané v XAML a Visual C#, Visual C++ nebo Visual Basic, najdete v [tématu Spuštění relace ladění (VB, C#, C++ a XAML)](../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md)

## <a name="in-this-topic"></a><a name="BKMK_In_this_topic"></a>V tomto tématu
 [V tomto tématu](#BKMK_In_this_topic)

 [Snadný způsob, jak začít ladit](#BKMK_The_easy_way_to_start_debugging)

 [Konfigurace relace ladění](#BKMK_Configure_the_debugging_session)

- [Otevření stránky vlastností ladění pro projekt](#BKMK_Open_the_debugging_property_page_for_the_project)

- [Výběr možností konfigurace sestavení](#BKMK_Choose_the_build_configuration_options)

- [Výběr cíle nasazení](#BKMK_Choose_the_deployment_target)

- [Vyberte ladicí program, který chcete použít.](#BKMK_Choose_the_debugger_to_use)

- [(Nepovinné) Zpoždění spuštění aplikace v relaci ladění](#BKMK__Optional__Delay_starting_app_in_the_debug_session)

- [(Nepovinné) Zakázání síťových zpěticích smyček](#BKMK__Optional__Disable_network_loopbacks)

  [Spuštění relace ladění](#BKMK_Start_the_debugging_session)

- [Zahájení ladění (F5)](#BKMK_Start_debugging__F5_)

- [Spuštění ladění (F5), ale zpoždění spuštění aplikace](#BKMK_Start_debugging__F5__but_delay_the_app_start)

  [Spuštění nainstalované aplikace v ladicím programu](#BKMK_Start_an_installed_app_in_the_debugger)

  [Připojení ladicího programu ke spuštěné aplikaci](#BKMK_Attach_the_debugger_to_a_running_app_)

- [Nastavení spuštění aplikace v režimu ladění](#BKMK_Set_the_app_to_run_in_debug_mode)

- [Připojit ladicí program](#BKMK_Attach_the_debugger)

## <a name="the-easy-way-to-start-debugging"></a><a name="BKMK_The_easy_way_to_start_debugging"></a>Snadný způsob, jak začít ladit
 ![Platí pouze pro Windows](../debugger/media/windows-only-content.png "windows_only_content")

1. Otevřete řešení aplikace v Sadě Visual Studio.

2. Pokud řešení obsahuje projekty pro aplikace pro Windows Store i Windows Store Phone, ujistěte se, že projekt, který chcete ladit, je počáteční projekt. V části Solution Explore vyberte projekt a pak z kontextové nabídky zvolte **Nastavit jako projekt spuštění.**

3. Stiskněte klávesu F5.

   ![Platí pouze pro Windows Phone.](../debugger/media/phone-only-content.png "phone_only_content")

   Visual Studio vytvoří a spustí aplikaci s připojeným ladicím programem. Spuštění pokračuje, dokud je dosaženo zarážky, ručně pozastavit provádění, dojde k neošetřené výjimce nebo ukončení aplikace. Další informace naleznete [v tématu Úvodní příručka: Ladění jazyka HTML a CSS](../debugger/quickstart-debug-html-and-css.md).

## <a name="configure-the-debugging-session"></a><a name="BKMK_Configure_the_debugging_session"></a>Konfigurace relace ladění
 Vzhledem k tomu, že skript není kompilován, konfigurace sestavení a nastavení platformy neplatí. Pokud ladíte c++ nebo spravovanou komponentu, nastavte **konfiguraci** na **ladění** a zvolte cílovou platformu z dialogového okna **Konfigurace.**

### <a name="open-the-debugging-property-page-for-the-project"></a><a name="BKMK_Open_the_debugging_property_page_for_the_project"></a>Otevření stránky vlastností ladění pro projekt

1. V Průzkumníku řešení vyberte projekt. V místní nabídce zvolte **Vlastnosti**.

2. Rozbalte uzel **Vlastnosti konfigurace** a pak zvolte **Ladění**

### <a name="choose-the-build-configuration-options"></a><a name="BKMK_Choose_the_build_configuration_options"></a>Výběr možností konfigurace sestavení

1. V seznamu **Konfigurace** zvolte **Ladění** nebo **(Aktivní) Ladění**.

2. Ze seznamu **Platforma** vyberte cílovou platformu, pro kterou chcete vytvořit. Ve většině případů, **Jakýkoli procesor** je nejlepší volbou.

### <a name="choose-the-deployment-target"></a><a name="BKMK_Choose_the_deployment_target"></a>Výběr cíle nasazení
 Aplikaci můžete nasadit a ladit v počítači sady Visual Studio, v simulátoru sady Visual Studio v místním počítači nebo ve vzdáleném počítači. Cíl můžete vybrat z **ladicího programu, který má být spuštěn** na stránce **vlastnosti Ladění** pro projekt.

 ![Platí pouze pro Windows](../debugger/media/windows-only-content.png "windows_only_content")

 Pro aplikaci pro Windows Store zvolte jednu z těchto možností ze seznamu **Cílové zařízení:**

|||
|-|-|
|**Místní počítač**|Ladění aplikace v aktuální relaci v místním počítači. Viz [Spuštění aplikací pro Windows Store na místním počítači](../debugger/run-windows-store-apps-on-the-local-machine.md).|
|**Simulátor**|Ladění aplikace v simulátoru Visual [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] Studio pro aplikace. Simulátor je okno plochy, které umožňuje ladit funkce zařízení , které nejsou k dispozici v místním počítači. Viz [Spuštění aplikací pro Windows Store v simulátoru](../debugger/run-windows-store-apps-in-the-simulator.md).|
|**Vzdálený stroj**|Ladění aplikace na zařízení, které je připojeno k místnímu počítači přes intranet nebo přímo připojené pomocí ethernetového kabelu. Chcete-li ladit vzdáleně, vzdálené nástroje sady Visual Studio musí být nainstalovány a spuštěny na vzdáleném zařízení. Viz [Spouštění aplikací pro Windows Store na vzdáleném počítači](../debugger/run-windows-store-apps-on-a-remote-machine.md).|

 Pokud zvolíte **vzdálený počítač**, zadejte název nebo IP adresu vzdáleného počítače jedním z těchto způsobů:

- Do pole **Název počítače** zadejte název nebo ADRESU IP vzdáleného počítače.

- V poli Název **počítače** zvolte ** \<Vyhledat... >**. Pak zvolte vzdálený počítač z dialogového okna **Vybrat vzdálené připojení ladicího programu.**

   ![Vybrat vzdálené připojení ladicího programu](../debugger/media/vsrun-pro-selectremotedebuggerdlg.png "VSRUN_PRO_SelectRemoteDebuggerDlg")

  > [!NOTE]
  > Dialogové okno Vybrat vzdálené připojení ladicího programu zobrazuje počítače, které jsou v místní podsíti, a počítače, které jsou přímo připojeny k počítači Visual Studio pomocí ethernetového kabelu. Chcete-li zadat jiný počítač, zadejte název do pole **Název počítače.**

  ![Platí pouze pro Windows Phone.](../debugger/media/phone-only-content.png "phone_only_content")

  Pro aplikaci pro Windows Store pro Telefon zvolte **Zařízení** nebo jeden z emulátorů ze seznamu **Cílové zařízení.**

### <a name="choose-the-debugger-to-use"></a><a name="BKMK_Choose_the_debugger_to_use"></a>Vyberte ladicí program, který chcete použít.
 Ve výchozím nastavení se ladicí program připojí ke kódu JavaScriptu ve vaší aplikaci. Můžete se rozhodnout ladit nativní C++ a spravovaný kód součástí vaší aplikace namísto kódu JavaScript. Kód pro ladění zadáte v seznamu **Typ ladicího programu** na stránce **vlastností ladění** projektu aplikace.

 Vyberte jeden z těchto ladicích programů ze seznamu **Typ ladicího programu:**

|||
|-|-|
|**Pouze skript**|Ladění kódu JavaScript ve vaší aplikaci. Spravovaný kód a nativní kód jsou ignorovány.|
|**Pouze nativní**|Ladění nativního kódu C/C++ ve vaší aplikaci. Spravovaný kód a kód JavaScript jsou ignorovány.|
|**Nativní se skriptem**|Ladění nativního kódu C++ a javascriptového kódu ve vaší aplikaci.|
|**Pouze spravované**|Ladění spravovaného kódu ve vaší aplikaci. Kód JavaScripta a nativní kód C/C++ jsou ignorovány.|
|**Smíšené (spravované a nativní)**|Ladění nativního kódu C/C++ a spravovaného kódu ve vaší aplikaci. Kód JavaScriptu je ignorován.|

### <a name="optional-delay-starting-the-app-in-the-debug-session"></a><a name="BKMK__Optional__Delay_starting_app_in_the_debug_session"></a>(Nepovinné) Zpoždění spuštění aplikace v relaci ladění
 Ve výchozím nastavení Visual Studio okamžitě spustí aplikaci při spuštění ladění. Můžete také spustit relaci ladění, ale zpozdit spuštění aplikace. Aplikace se spustí v ladicím programu, když je spuštěna z nabídky Start nebo aktivační smlouvy, nebo když je spuštěna jiným procesem nebo metodou. Můžete také použít zpožděný start k ladění událostí na pozadí ve vaší aplikaci, které chcete nastat, když aplikace není spuštěná.

 Můžete určit, zda chcete odložit spuštění aplikace v seznamu **Spustit aplikaci** na stránce **vlastností ladění** projektu aplikace. Zvolte jednu z těchto možností:

- Zvolte **Ne,** chcete-li odložit spuštění aplikace.

- Chcete-li aplikaci spustit okamžitě, zvolte **Ano.**

### <a name="optional-disable-network-loopbacks"></a><a name="BKMK__Optional__Disable_network_loopbacks"></a>(Nepovinné) Zakázání síťových zpěticích smyček
 ![Platí pouze pro Windows](../debugger/media/windows-only-content.png "windows_only_content")

 Z bezpečnostních důvodů není aplikace pro Windows Store, která je nainstalována standardním způsobem, povolena pro volání do sítě zařízení, na které je nainstalovaná. Ve výchozím nastavení nasazení visual studia vytvoří výjimku z tohoto pravidla pro nasazenou aplikaci. Tato výjimka umožňuje testovat komunikační postupy na jednom počítači. Než aplikaci odešlete do Windows Storu, měli byste ji otestovat bez výjimky.

 Chcete-li odebrat výjimku zpětné smyčky sítě, zvolte **Ne** ze seznamu **Povolit síťovou zpětnou vazbu** na stránce **vlastností Ladění.**

## <a name="start-the-debugging-session"></a><a name="BKMK_Start_the_debugging_session"></a>Spuštění relace ladění

### <a name="start-debugging-f5"></a><a name="BKMK_Start_debugging__F5_"></a>Zahájení ladění (F5)
 Když v nabídce **Ladění** (Klávesnice: F5) zvolíte **Spustit ladění,** Visual Studio spustí aplikaci s připojeným ladicím programem. Spuštění pokračuje, dokud je dosaženo zarážky, ručně pozastavit provádění, dojde k neošetřené výjimce nebo ukončení aplikace.

### <a name="start-debugging-f5-but-delay-the-app-start"></a><a name="BKMK_Start_debugging__F5__but_delay_the_app_start"></a>Spuštění ladění (F5), ale zpoždění spuštění aplikace
 Můžete nastavit aplikaci spustit v režimu ladění, ale nechat ji spustit metodou jinou než ladicí program. Můžete například chtít ladit spuštění aplikace z nabídky Start nebo ladit proces na pozadí v aplikaci bez spuštění aplikace. Chcete-li odložit spuštění aplikace, udělejte toto:

1. Na stránce **Ladění** vlastností projektu aplikace zvolte **Ne** ze seznamu **Spustit aplikaci.**

2. V nabídce **Ladění** zvolte **Spustit ladění** (Klávesnice: F5).

3. Spusťte aplikaci z nabídky Start, smlouvy o provedení nebo jiným postupem.

   Aplikace se spustí v režimu ladění. Spuštění pokračuje, dokud je dosaženo zarážky, ručně pozastavit provádění, dojde k neošetřené výjimce nebo ukončení aplikace.

   . Další informace o ladění úloh na pozadí najdete [v tématu Trigger suspend, resume a background events for Windows Store).](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md)

## <a name="start-an-installed-app-in-the-debugger"></a><a name="BKMK_Start_an_installed_app_in_the_debugger"></a>Spuštění nainstalované aplikace v ladicím programu
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

## <a name="attach-the-debugger-to-a-running-app"></a><a name="BKMK_Attach_the_debugger_to_a_running_app_"></a>Připojení ladicího programu ke spuštěné aplikaci
 Chcete-li připojit ladicí program k [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] aplikaci, musíte použít Laditelný Správce balíčků k nastavení aplikace pro spuštění v režimu ladění. Správce ladicích balíčků je nainstalován pomocí vzdálených nástrojů sady Visual Studio.

 Připojení ladicího programu k aplikaci je užitečné, když potřebujete ladit již nainstalovanou aplikaci, jako je například aplikace, která byla nainstalovaná z Windows Storu. Připojení je vyžadováno, pokud máte zdrojové soubory pro aplikaci, ale nemáte projekt Sady Visual Studio pro aplikaci. Můžete mít například vlastní systém sestavení, který nepoužívá projekty nebo řešení sady Visual Studio.

 Připojení k aplikaci:

1. Nastavte aplikaci tak, aby běžela v režimu ladění. To musí být provedeno, když aplikace není spuštěna.

2. Spusťte aplikaci. Aplikaci můžete spustit z nabídky Start, smlouvy o provedení nebo jiné metody.

3. Připojte ladicí program ke spuštěné aplikaci.

### <a name="set-the-app-to-run-in-debug-mode"></a><a name="BKMK_Set_the_app_to_run_in_debug_mode"></a>Nastavení spuštění aplikace v režimu ladění

1. Nainstalujte vzdálené nástroje Visual Studia do zařízení, kde je aplikace nainstalovaná. Viz [Instalace vzdálených nástrojů](https://msdn.microsoft.com/library/windows/apps/hh441469.aspx#BKMK_Installing_the_Remote_Tools).

2. V nabídce Start `Debuggable Package Manager` vyhledejte a spusťte ji.

     Zobrazí se okno Prostředí PowerShell správně nakonfigurované pro rutinu AppxDebug.

3. Chcete-li povolit ladění aplikace, musíte zadat identifikátor PackageFullName aplikace. Chcete-li zobrazit seznam všech aplikací, které `Get-AppxPackage` obsahují PackageFullName, zadejte na výzvu PowerShell.

4. Na výzvu Prostředí `Enable-AppxDebug` PowerShell zadejte *PackageFullName,* kde *PackageFullName* je identifikátor PackageFullName aplikace.

### <a name="attach-the-debugger"></a><a name="BKMK_Attach_the_debugger"></a>Připojení ladicího programu

> [!TIP]
> Aplikace JavaScript uběhnou v instanci procesu wwahost.exe. Pokud jsou při připojení k aplikaci spuštěny jiné aplikace JavaScriptu, budete potřebovat znát id číselného procesu (PID) souboru wwahost.exe, ve kterém je aplikace spuštěna.
>
> Nejjednodušší způsob, jak se s touto situací vypořádat, je zavřít všechny ostatní aplikace JavaScriptu. V opačném případě můžete před spuštěním aplikace otevřít Správce úloh systému Windows a zaznamenat id procesů wwahost.exe. Když zadáte proces, ke kterému se má připojit v dialogovém okně **Dostupné procesy,** bude mít wwahost.exe aplikace id, které se liší od toho, které jste zaznamenali.

 Připojení ladicího programu:

1. V nabídce **Ladění** zvolte **Připojit ke zpracování**.

    Zobrazí se dialogové okno **Připojit k procesu.**

2. Chcete-li se připojit k aplikaci na vzdáleném zařízení, zadejte vzdálené zařízení do pole **Kvalifikátor.** Můžete:

   - Zadejte název do pole **Kvalifikátor.**

   - V poli **Kvalifikátor** zvolte šipku dolů a vyberte zařízení ze seznamu zařízení, ke kterým jste se připojili dříve.

   - Zvolte **Najít,** chcete-li vybrat zařízení ze seznamu zařízení v místní podsíti.

3. Zadejte typ kódu, který chcete ladit v poli **Připojit k.**

    Zvolte **Vybrat** a proveďte jednu z následujících akcí:

   - Zvolte **Automaticky určit typ kódu, který chcete ladit.**

   - Zvolte **Ladit tyto typy kódu** a pak zvolte jeden nebo více typů ze seznamu.

4. V seznamu **Dostupné procesy** zvolte příslušný proces **wwahost.exe.** K identifikaci aplikace použijte sloupec **Název.**

5. Zvolte **Připojit**.

   Visual Studio připojí ladicí program k procesu. Spuštění pokračuje, dokud je dosaženo zarážky, ručně pozastavit provádění, dojde k neošetřené výjimce nebo ukončení aplikace.

## <a name="see-also"></a>Viz také
 [Řízení provádění v relaci ladění (JavaScript)](../debugger/control-execution-of-a-store-app-in-a-visual-studio-debug-session-for-windows-store-apps-javascript.md) [Úvodní příručka: Ladění HTML a CSS](../debugger/quickstart-debug-html-and-css.md) [Trigger pozastavit, obnovit a události na pozadí pro Windows Store)](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md) [Ladění aplikace v sadě Visual Studio](../debugger/debug-store-apps-in-visual-studio.md)
