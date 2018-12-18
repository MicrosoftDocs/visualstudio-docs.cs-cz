---
title: Spouštění aplikací pro UWP v simulátoru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: 81b69bf8-ec87-4bb6-9ad4-1fa7b7802d16
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- uwp
ms.openlocfilehash: f8d1ae730947a70cac253866d0257aa4e0216626
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49882766"
---
# <a name="run-uwp-apps-in-the-simulator"></a>Spouštění aplikací pro UPW na simulátoru
Simulátor aplikace Visual Studio pro aplikace pro UPW je desktopová aplikace, která simuluje aplikace pro UPW. Obvykle můžete ladit na místním počítači, připojeného zařízení nebo vzdálený počítač. Ale v některých případech můžete chtít použít simulátor aplikace Visual Studio k emulaci různých fyzických obrazovku a řešení. Můžete také simulovat běžné touch a otočení události a simulovat vlastnosti připojení k síti.
  
 Simulátor poskytuje prostředí, ve kterém můžete návrh, vývoj, ladění a testování aplikací pro UPW. Ale předtím, než můžete publikovat aplikaci pro Microsoft Store, měli byste otestovat aplikace skutečný zařízení.  
  
 Simulátor aplikace Visual Studio pro aplikace pro UPW se nespouští v izolovaném prostředí v místním počítači. Proto se chyby, ke kterým dochází v simulátoru, jako je neobnovitelná systémová chyba, může také ovlivnit celý počítač.  
  
> [!IMPORTANT]
>  Simulátor aplikace Visual Studio 2015 neobsahuje informace o zeměpisné poloze tlačítko. Je to proto, že simulátor systému Windows 10 neobsahuje informace o zeměpisné poloze simulace.
  
##  <a name="BKMK_Set_the_simulator_as_the_target"></a> Nastavit jako cíl simulátoru  
 Ke spuštění vaší aplikace pro UWP v simulátoru, vyberte **simulátor** z rozevíracího seznamu vedle položky **spustit ladění** tlačítko na ladicí program **standardní** nástrojů. Tato možnost je k dispozici, pouze pokud vaše aplikace **Min cílové platformy. Verze** je menší než nebo rovna operačního systému na vývojovém počítači. 
  
 ![Běžících v simulátoru](../debugger/media/vsrun_f5_simulator.png "VSRUN_F5_Simulator")  
  
##  <a name="BKMK_Choose_an_interaction_mode"></a> Volba režimu interakce  
 Můžete použít následující režimy interakce  
  
-   ![Tlačítko myši režimu](../debugger/media/simulator_mousemodebtn.png "SIMULATOR_MouseModeBtn") režim myši: Nastaví režim interakce na gesta myší. Zahrnout kliknutí, gesta myší dvakrát klikne a drags.  
  
-   ![Spouštěcí tlačítko emulace dotykového ovládání](../debugger/media/simulator_starttouchemulationbtn.png "SIMULATOR_StartTouchEmulationBtn") spuštění emulace dotykového ovládání: Nastaví režim interakce na dotyk gesta jeden prstem. Jedním prstem události obsahují klepnete, přetahování a potažení prstem.  
  
     ![Cíl simulátoru jedním prstem](../debugger/media/simulator_onefinger.png "SIMULATOR_OneFinger") ikonu jediný cíl označuje umístění událostí v simulátoru. Umístěte ukazatel pomocí myši.  
  
     ![Cíl touch jedním prstem](../debugger/media/simulator_onefingerengaged.png "SIMULATOR_OneFingerEngaged") stiskněte levým tlačítkem myši na aktivovat režim dotykového ovládání. Například klikněte na tlačítko k simulaci tap, nebo stiskněte a podržte tlačítko a přetáhněte nebo potažením prstem přejděte.  
  
## <a name="pinch-and-zoom"></a>Ovládání stažením prstů a přiblížení  
 Nastaví režim interakce pro ovládání stažením prstů a gesta dvěma prsty přiblížení.  
  
-   ![Cíl prstem Siimulator dvě](../debugger/media/simulator_twofinger.png "SIMULATOR_TwoFinger")  
  
     Dvojité cílovou ikonu označuje umístění dvěma prsty na obrazovce zařízení.  
  
    -   Najeďte myší na pozici ikony na objekt na obrazovce zařízení.  
  
    -   Otočení kolečka myši, chcete-li změnit simulované vzdálenost dvěma prsty před roztažením prstů nebo zvětšení dopředu nebo dozadu.  
  
-   -   ![Ovládání stažením prstů, přibližování a otáčení cíle](../debugger/media/simulator_twofingerengaged.png "SIMULATOR_TwoFingerEngaged")  
  
         Stiskněte tlačítko vlevo a otočit kolečko dozadu (směrem k) Chcete-li zvětšit (stažení).  
  
    -   Stiskněte tlačítko vlevo a otáčením kolečko myši dopředu (směrem od) horizonální oddálení (Lupa).  
  
## <a name="object-rotation"></a>Otočení objektu  
 **Emulace dotykového ovládání otočit** tlačítka nastaví režim interakce na gesta otočení pomocí dvěma prsty.  
  
-   -   Najeďte myší na pozici ikony na objekt na obrazovce zařízení.  
  
    -   Otočení kolečka myši, chcete-li změnit simulované orientace dvěma prsty před otočit objekt dopředu nebo dozadu.  
  
-   -   Stiskněte tlačítko vlevo a otáčením kolečka zpětné (směrem k) Otočit proti směru hodinových ručiček objektu. Jak otočení kolečka myši, jednu z ikon dvou cílové otočí kolem druhý k určení relativní velikosti otočení.  
  
    -   Stiskněte tlačítko vlevo a otočení objektu po směru hodinových ručiček otáčením kolečko myši dopředu (směrem od).  
  
##  <a name="BKMK_Enable_or_disable_Always_on_top_mode"></a> Povolení nebo zakázání vždy na začátek režimu  
 Můžete nastavit okno simulátoru vždy být nad ostatními okny. **Nejvrchnější okna přepnout** tlačítko povolí nebo zakáže **vždy navrchu** režimu okno simulátoru.  
  
##  <a name="BKMK_Change_the_device_orientation"></a> Změna orientace zařízení  
 Orientace zařízení mezi na výšku a šířku můžete přepnout otočením v simulátoru 90 stupňů vede libovolným směrem.  
  
> [!NOTE]
>  Simulátor nerespektuje [DisplayProperties.AutoRotationPreferences](http://go.microsoft.com/fwlink/?LinkId=249460) vlastnost projektu. Například, pokud váš projekt nastaví orientaci `Landscape`a potom otočit simulator pro orientaci na výšku, obraz simulátor také se otočí a se změněnou velikostí. Vyzkoušejte nastavení na příslušném zařízení.  
  
> [!NOTE]
>  Pokud otočíte simulátoru tak, aby jednomu z okrajů simulátoru je větší, než se zobrazí na obrazovce, simulátor je automaticky přizpůsobí na obrazovce. Simulátor nezmění původní velikost, pokud znovu otočit.  
  
##  <a name="BKMK_Change_the_simulated_screen_size_and_resolution"></a> Změna velikosti obrazovky s Simulovaná a řešení  
 Chcete-li změnit velikost simulované obrazovky a rozlišení, zvolte **změnit rozlišení** tlačítko na paletě a v seznamu vyberte novou velikost a řešení.  
  
 Velikost obrazovky a rozlišení, které jsou uvedené jako *palce šířka obrazovky, pixel šířka a výška pixel*. Mějte na paměti, že se simulované velikosti obrazovky a rozlišení. Souřadnice umístění na simulátoru jsou přeloženy na souřadnice velikost vybraného zařízení a řešení.  
  
> [!NOTE]
>  Škálovaná verze bitmapové obrázky můžete uložit ve vaší aplikaci a Windows se načte správné bitové kopie pro aktuální měřítko. Další informace najdete v tématu [návrhu a uživatelského rozhraní ÚVOD](/windows/uwp/layout/design-and-ui-intro). Ale pokud změníte na simulátoru řešení tak, že Windows vybere jinou image podle rozlišení, budete muset zastavte a restartujte relaci ladění zobrazíte novou bitovou kopii.  
  
##  <a name="BKMK_Capture_a_screenshot_of_your_app_for_submission_to_the_Microsoft_Store"></a> Zachytit snímek obrazovky aplikace k odeslání do Microsoft Store  
 Při odesílání aplikace pro Microsoft Store, musíte zahrnout snímky obrazovky aplikace.  
  
> [!NOTE]
>  Na snímku obrazovky je uložen na aktuální řešení simulátoru. Chcete-li změnit na řešení, zvolte **změnit rozlišení** tlačítko.  
  
-   Chcete-li vytvořit snímky obrazovek pro vaši aplikaci v simulátoru, zvolte **zachytit snímek obrazovky do schránky** tlačítko.  
  
-   Chcete-li nastavit umístění, kde se nachází snímky obrazovky, zvolte **nastavení snímku obrazovky** tlačítko a vyberte umístění v místní nabídce.  
  
     ![Snímek obrazovky nastavení místní nabídka](../debugger/media/simulator_screenshotsettingscntxmnu.png "SIMULATOR_ScreenShotSettingsCntxMnu")  
  
##  <a name="BKMK_Simulate_network_connection_properties"></a> Simulovat vlastnosti připojení k síti  
 Můžete uživatelům vaší aplikace, spravovat náklady na měřeném připojení k síti zachování povědomí o síťové připojení zdarma nebo dat plánu změny stavu a povolením aplikaci pomocí těchto informací zabránit bez dalších nákladů pro roaming nebo vyšší než pomoci omezení přenosu zadaná data. [Windows.Networking.Connectivity](/uwp/api/windows.networking.connectivity) rozhraní API umožňuje reagovat na [NetworkStatusChanged](/uwp/api/windows.networking.connectivity.networkinformation) a [TriggerType](/uwp/api/windows.applicationmodel.background.systemtrigger) události, které se přihlaste. Zobrazit [rychlý start: Správa sítí s měřením dat nákladů omezení](https://msdn.microsoft.com/library/windows/apps/Hh750310.aspx).  
  
 K ladění a testování kódu s ohledem na náklady na síť, můžete simulátoru napodobují vlastnosti sítě, které jsou vystaveny prostřednictvím [ConnectionProfile](/uwp/api/windows.networking.connectivity.connectionprofile) vrácený [GetInternetConnectionProfile](/uwp/api/windows.networking.connectivity.networkinformation).
  
 Pro simulaci sítě-vlastnosti:  
  
1. Na panelu nástrojů themeroller simulátor **změnit vlastnosti sítě** tlačítko.  
  
2. Na **nastavit vlastnosti sítě** dialogu **použití simulované sítě-vlastnosti**.  
  
    Zrušte zaškrtnutí políčka odebrat simulace a vraťte se do vlastností síťového rozhraní aktuálně připojené.  
  
3. Zadejte **název profilu** pro simulované síti. Doporučujeme použít jedinečný název, který můžete použít k identifikaci simulace v [ProfileName](/uwp/api/windows.networking.connectivity.connectionprofile) vlastnost [ConnectionProfile](/uwp/api/windows.networking.connectivity.connectionprofile) objektu.  
  
4. Vyberte [NetworkCostType](/uwp/api/windows.networking.connectivity.networkcosttype) hodnotu z profilu **typ náklady na síť** seznamu.  
  
5. Z **příznak stavu limitu dat** seznamu, můžete nastavit [ApproachingDataLimit](/uwp/api/windows.networking.connectivity.connectioncost) vlastnost nebo [OverDataLimit](/uwp/api/windows.networking.connectivity.connectioncost) vlastnost na hodnotu true, nebo můžete zvolit  **V části omezení dat** nastavení obě hodnoty na hodnotu false.  
  
6. Z **Roaming stavu** seznam, nastavte [Roaming](/uwp/api/windows.networking.connectivity.connectioncost) vlastnost.  
  
7. Zvolte **nastavit vlastnosti** simulovat vlastnosti sítě aktivací popředí [NetworkStatusChanged](/uwp/api/windows.networking.connectivity.networkinformation) událostí a na pozadí [SystemTrigger](/uwp/api/windows.applicationmodel.background.systemtrigger) typu  **NetworkStateChange**.  
  
   **Další informace o správě připojení k síti**  
  
   [Rychlý start: Správa měří omezení náklady na síť](https://msdn.microsoft.com/library/windows/apps/Hh750310.aspx)  
  
   [Ukázka informace o síti](https://code.msdn.microsoft.com/windowsapps/Network-Information-Sample-63aaa201)  
  
   [Analýza spotřeby energie](../profiling/analyze-energy-use-in-store-apps.md)  
  
   [Windows.Networking.Connectivity](/uwp/api/windows.networking.connectivity)  
  
   [Jak reagovat na události systému s úlohami na pozadí](/previous-versions/windows/apps/hh977058(v=win.10))  
  
   [Jak aktivovat pozastavení, obnovení a události na pozadí v aplikacích pro UWP](/visualstudio/debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio)  
  
##  <a name="BKMK_Navigate_the_simulator_with_the_keyboard"></a> Přejděte simulátoru pomocí klávesnice  
 Simulátor nástrojů můžete přejít stisknutím klávesy **CTRL + ALT + Šipka nahoru** k přepnutí okno simulátoru na panel nástrojů simulátoru. Použití **šipka nahoru** a **šipka dolů** přesouvat mezi tlačítka na panelu nástrojů.  
  
 Simulátor můžete ukončit stisknutím kombinace kláves **CTRL + ALT + F4**.  
  
## <a name="see-also"></a>Viz také  
 [Spouštění aplikací ze sady Visual Studio](../debugger/run-store-apps-from-visual-studio.md)