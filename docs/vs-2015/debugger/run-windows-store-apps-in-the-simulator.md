---
title: Aplikace Windows Store spustit v simulátoru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 81b69bf8-ec87-4bb6-9ad4-1fa7b7802d16
caps.latest.revision: 45
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 504a63d0f99a1a96d1192a1666d45dafde037253
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51775105"
---
# <a name="run-windows-store-apps-in-the-simulator"></a>Spouštění v simulátoru Windows Store apps
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Simulátor aplikace Visual Studio pro aplikace Windows Store je aplikace klasické pracovní plochy, který simuluje aplikace Windows Store. Můžete spouštět aplikace a simulace událostí otočení a běžné touch na vašem vývojovém počítači. Můžete také velikost fyzické obrazovky a rozlišení, které chcete emulovat a simulovat vlastnosti připojení k síti.  
  
 Simulátor poskytuje prostředí, ve kterém můžete návrh, vývoj, ladění a testování aplikací pro Windows Store. Ale předtím, než můžete publikovat aplikaci pro Windows Store, měli byste otestovat aplikace skutečný zařízení.  
  
 Simulátor aplikace Visual Studio pro aplikace Windows Store nelze spustit v izolovaném prostředí v místním počítači. Proto se chyby, ke kterým dochází v simulátoru, jako je neobnovitelná systémová chyba, může také ovlivnit celý počítač.  
  
 Zobrazit [aplikace spustit na Windows Phone v emulátoru](../debugger/run-windows-phone-apps-in-the-emulator.md) informace Windows Phone.  
  
> [!IMPORTANT]
>  Simulátor aplikace Visual Studio 2015 neobsahuje informace o zeměpisné poloze tlačítko. Je to proto, že simulátor systému Windows 10 neobsahuje informace o zeměpisné poloze simulace. Pokud potřebujete udělat tento druh simulace, můžete použít simulátor aplikace Visual Studio 2013 na Windows 8.1 nebo starší operační systémy.  
  
##  <a name="BKMK_Set_the_simulator_as_the_target"></a> Nastavit jako cíl simulátoru  
 Ke spuštění vaší aplikace Windows Store v simulátoru, vyberte **simulátor** z rozevíracího seznamu vedle položky **spustit ladění** tlačítko na ladicí program **standardní** nástrojů.  
  
 ![Běžících v simulátoru](../debugger/media/vsrun-f5-simulator.png "VSRUN_F5_Simulator")  
  
##  <a name="BKMK_Choose_an_interaction_mode"></a> Volba režimu interakce  
 Můžete použít následující režimy interakce  
  
-   ![Tlačítko myši režimu](../debugger/media/simulator-mousemodebtn.png "SIMULATOR_MouseModeBtn") režim myši: Nastaví režim interakce na gesta myší. Zahrnout kliknutí, gesta myší dvakrát klikne a drags.  
  
-   ![Spouštěcí tlačítko emulace dotykového ovládání](../debugger/media/simulator-starttouchemulationbtn.png "SIMULATOR_StartTouchEmulationBtn") spuštění emulace dotykového ovládání: Nastaví režim interakce na dotyk gesta jeden prstem. Jedním prstem události obsahují klepnete, přetahování a potažení prstem.  
  
     ![Cíl simulátoru jedním prstem](../debugger/media/simulator-onefinger.png "SIMULATOR_OneFinger") ikonu jediný cíl označuje umístění událostí v simulátoru. Umístěte ukazatel pomocí myši.  
  
     ![Cíl touch jedním prstem](../debugger/media/simulator-onefingerengaged.png "SIMULATOR_OneFingerEngaged") stiskněte levým tlačítkem myši na aktivovat režim dotykového ovládání. Například klikněte na tlačítko k simulaci tap, nebo stiskněte a podržte tlačítko a přetáhněte nebo potažením prstem přejděte.  
  
## <a name="pinch-and-zoom"></a>Ovládání stažením prstů a přiblížení  
 Nastaví režim interakce pro ovládání stažením prstů a gesta dvěma prsty přiblížení.  
  
-   ![Cíl prstem Siimulator dvě](../debugger/media/simulator-twofinger.png "SIMULATOR_TwoFinger")  
  
     Dvojité cílovou ikonu označuje umístění dvěma prsty na obrazovce zařízení.  
  
    -   Najeďte myší na pozici ikony na objekt na obrazovce zařízení.  
  
    -   Otočení kolečka myši, chcete-li změnit simulované vzdálenost dvěma prsty před roztažením prstů nebo zvětšení dopředu nebo dozadu.  
  
-   -   ![Ovládání stažením prstů, přibližování a otáčení cíle](../debugger/media/simulator-twofingerengaged.png "SIMULATOR_TwoFingerEngaged")  
  
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
>  Škálovaná verze bitmapové obrázky můžete uložit ve vaší aplikaci a Windows se načte správné bitové kopie pro aktuální měřítko. Další informace najdete v tématu [Responzivní návrh 101](https://msdn.microsoft.com/library/windows/apps/dn958435.aspx). Ale pokud změníte na simulátoru řešení tak, že Windows vybere jinou image podle rozlišení, budete muset zastavte a restartujte relaci ladění zobrazíte novou bitovou kopii.  
  
##  <a name="BKMK_Capture_a_screenshot_of_your_app_for_submission_to_the_Microsoft_Store"></a> Zachytit snímek obrazovky aplikace k odeslání do Windows Store  
 Při odeslání aplikace do app storu Windows, musíte zahrnout snímky obrazovky aplikace.  
  
> [!NOTE]
>  Na snímku obrazovky je uložen na aktuální řešení simulátoru. Chcete-li změnit na řešení, zvolte **změnit rozlišení** tlačítko.  
  
-   Chcete-li vytvořit snímky obrazovek pro vaši aplikaci v simulátoru, zvolte **zachytit snímek obrazovky do schránky** tlačítko.  
  
-   Chcete-li nastavit umístění, kde se nachází snímky obrazovky, zvolte **nastavení snímku obrazovky** tlačítko a vyberte umístění v místní nabídce.  
  
     ![Snímek obrazovky nastavení místní nabídka](../debugger/media/simulator-screenshotsettingscntxmnu.png "SIMULATOR_ScreenShotSettingsCntxMnu")  
  
##  <a name="BKMK_Simulate_network_connection_properties"></a> Simulovat vlastnosti připojení k síti  
 Můžete uživatelům vaší aplikace, spravovat náklady na měřeném připojení k síti zachování povědomí o síťové připojení zdarma nebo dat plánu změny stavu a povolením aplikaci pomocí těchto informací zabránit bez dalších nákladů pro roaming nebo vyšší než pomoci omezení přenosu zadaná data. [Windows.Networking.Connectivity](https://msdn.microsoft.com/library/windows/apps/windows.networking.connectivity.aspx) rozhraní API umožňuje reagovat na [NetworkStatusChanged](https://msdn.microsoft.com/library/windows/apps/windows.networking.connectivity.networkinformation.networkstatuschanged.aspx) a [TriggerType](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.background.systemtrigger.triggertype.aspx) události, které se přihlaste. Zobrazit [rychlý start: Správa sítí s měřením dat nákladů omezení](http://msdn.microsoft.com/library/windows/apps/Hh750310.aspx).  
  
 K ladění a testování kódu s ohledem na náklady na síť, můžete simulátoru napodobují vlastnosti sítě, které jsou vystaveny prostřednictvím [ConnectionProfile](https://msdn.microsoft.com/library/windows/apps/windows.networking.connectivity.connectionprofile.aspx) vrácený [GetInternetConnectionProfile](https://msdn.microsoft.com/library/windows/apps/windows.networking.connectivity.networkinformation.getinternetconnectionprofile.aspx)...  
  
 Pro simulaci sítě-vlastnosti:  
  
1. Na panelu nástrojů themeroller simulátor **změnit vlastnosti sítě** tlačítko.  
  
2. Na **nastavit vlastnosti sítě** dialogu **použití simulované sítě-vlastnosti**.  
  
    Zrušte zaškrtnutí políčka odebrat simulace a vraťte se do vlastností síťového rozhraní aktuálně připojené.  
  
3. Zadejte **název profilu** pro simulované síti. Doporučujeme použít jedinečný název, který můžete použít k identifikaci simulace v [ProfileName](https://msdn.microsoft.com/library/windows/apps/windows.networking.connectivity.connectionprofile.profilename.aspx) vlastnost [ConnectionProfile](https://msdn.microsoft.com/library/windows/apps/windows.networking.connectivity.connectionprofile.aspx) objektu.  
  
4. Vyberte [NetworkCostType](https://msdn.microsoft.com/library/windows/apps/windows.networking.connectivity.networkcosttype.aspx) hodnotu z profilu **typ náklady na síť** seznamu.  
  
5. Z **příznak stavu limitu dat** seznamu, můžete nastavit [ApproachingDataLimit](https://msdn.microsoft.com/library/windows/apps/windows.networking.connectivity.connectioncost.approachingdatalimit.aspx) vlastnost nebo [OverDataLimit](https://msdn.microsoft.com/library/windows/apps/windows.networking.connectivity.connectioncost.overdatalimit.aspx)vlastnost na hodnotu true, nebo můžete zvolit  **V části omezení dat** nastavení obě hodnoty na hodnotu false.  
  
6. Z **Roaming stavu** seznam, nastavte [Roaming](https://msdn.microsoft.com/library/windows/apps/windows.networking.connectivity.connectioncost.roaming.aspx) vlastnost.  
  
7. Zvolte **nastavit vlastnosti** simulovat vlastnosti sítě aktivací popředí [NetworkStatusChanged](https://msdn.microsoft.com/library/windows/apps/windows.networking.connectivity.networkinformation.networkstatuschanged.aspx) událostí a na pozadí [SystemTrigger](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.background.systemtrigger.aspx) typu  **NetworkStateChange**.  
  
   **Další informace o správě připojení k síti**  
  
   [Rychlý start: Správa měří omezení náklady na síť](http://msdn.microsoft.com/library/windows/apps/Hh750310.aspx)  
  
   [Ukázka informace o síti](http://code.msdn.microsoft.com/windowsapps/Network-Information-Sample-63aaa201)  
  
   [Analýza spotřeby energie](../profiling/analyze-energy-use-in-store-apps.md)  
  
   [Windows.Networking.Connectivity](https://msdn.microsoft.com/library/windows/apps/windows.networking.connectivity.aspx)  
  
   [Jak reagovat na události systému s úlohami na pozadí](http://msdn.microsoft.com/en-us/f7c86e86-a7ae-4abb-a923-76b03337a80a)  
  
   [Jak aktivovat pozastavení, obnovení a události na pozadí v aplikacích Windows Store](http://msdn.microsoft.com/library/windows/apps/hh974425.aspx)  
  
##  <a name="BKMK_Navigate_the_simulator_with_the_keyboard"></a> Přejděte simulátoru pomocí klávesnice  
 Simulátor nástrojů můžete přejít stisknutím klávesy **CTRL + ALT + Šipka nahoru** k přepnutí okno simulátoru na panel nástrojů simulátoru. Použití **šipka nahoru** a **šipka dolů** přesouvat mezi tlačítka na panelu nástrojů.  
  
 Simulátor můžete ukončit stisknutím kombinace kláves **CTRL + ALT + F4**.  
  
## <a name="see-also"></a>Viz také  
 [Spouštění aplikací ze sady Visual Studio](../debugger/run-store-apps-from-visual-studio.md)



