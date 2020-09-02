---
title: Spouštění aplikací pro Windows Store v simulátoru | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 81b69bf8-ec87-4bb6-9ad4-1fa7b7802d16
caps.latest.revision: 45
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d072f54dfe351d54e3e115dca7a91bec77fbb9e6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "75844920"
---
# <a name="run-windows-store-apps-in-the-simulator"></a>Spouštění aplikací pro Windows Store v simulátoru
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Simulátor sady Visual Studio pro aplikace pro Windows Store je desktopová aplikace, která simuluje aplikaci pro Windows Store. Můžete spouštět aplikace a simulovat běžné události dotykového a rotačního vývojového počítače. Můžete také zvolit velikost fyzické obrazovky a rozlišení, které chcete emulovat a simulovat vlastnosti síťového připojení.  
  
 Simulátor poskytuje prostředí, ve kterém můžete navrhovat, vyvíjet, ladit a testovat aplikace pro Windows Store. Před publikováním aplikace do Windows Storu ale můžete aplikaci otestovat na skutečném zařízení.  
  
 Simulátor sady Visual Studio pro aplikace pro Windows Store neběží v izolovaném prostředí na místním počítači. Chyby, ke kterým dochází v simulátoru, jako je například neobnovitelná chyba systému, mohou také ovlivnit celý počítač.  
  
 Informace o Windows Phone najdete [v tématu spuštění aplikací Windows Phone v emulátoru](../debugger/run-windows-phone-apps-in-the-emulator.md) .  
  
> [!IMPORTANT]
> Simulátor sady Visual Studio 2015 nezahrnuje tlačítko geografického umístění. Důvodem je to, že simulátor Windows 10 neobsahuje simulaci geografického umístění. Pokud potřebujete tento druh simulace, můžete použít simulátor Visual Studio 2013 v Windows 8.1 nebo starších operačních systémech.  
  
## <a name="set-the-simulator-as-the-target"></a><a name="BKMK_Set_the_simulator_as_the_target"></a> Nastavit simulátor jako cíl  
 Pokud chcete spustit aplikaci pro Windows Store v simulátoru, vyberte v rozevíracím seznamu vedle tlačítka **Spustit ladění** na panelu nástrojů **standardní** ladicí program **simulátor** .  
  
 ![Běžící v simulátoru](../debugger/media/vsrun-f5-simulator.png "VSRUN_F5_Simulator")  
  
## <a name="choose-an-interaction-mode"></a><a name="BKMK_Choose_an_interaction_mode"></a> Zvolit režim interakce  
 Můžete zvolit následující režimy interakce.  
  
- ![Tlačítko režimu myši](../debugger/media/simulator-mousemodebtn.png "SIMULATOR_MouseModeBtn") Režim myši: nastaví režim interakce na gesta myši. Gesta myši zahrnují kliknutí, dvojité kliknutí a přetahování.  
  
- ![Tlačítko spustit emulaci dotykového ovládání](../debugger/media/simulator-starttouchemulationbtn.png "SIMULATOR_StartTouchEmulationBtn") Zahájit emulaci dotykového ovládání: nastaví režim interakce na dotykové gesta jednoho prstu. Události s jedním prstem zahrnují klepnutí, přetahování a přetáhnutí.  
  
     ![Simulátor – jeden cíl Finger](../debugger/media/simulator-onefinger.png "SIMULATOR_OneFinger") Ikona s jedním cílem indikuje umístění událostí v simulátoru. Ukazatel myši umístěte pomocí myši.  
  
     ![Cíl dotykového ovládání](../debugger/media/simulator-onefingerengaged.png "SIMULATOR_OneFingerEngaged") Stisknutím levého tlačítka myši aktivujete režim dotykového ovládání. Například klikněte na tlačítko pro simulaci klepnutí nebo stiskněte a držte tlačítko při přetahování myší nebo potažením prstem.  
  
## <a name="pinch-and-zoom"></a>Gesto roztažení prstů a přiblížení  
 Nastaví režim interakce na gesto roztažení prstů a přiblížení gest dvou prsty.  
  
- ![Kosimulátor – cíl dvou prstů](../debugger/media/simulator-twofinger.png "SIMULATOR_TwoFinger")  

  - Ikona dvojitého cíle indikuje umístění dvou prsty na obrazovce zařízení.  

  - Přesunutím myši umístěte ikony nad objekt na obrazovce zařízení.  

  - Otočením kolečka myši směrem dozadu nebo dopředu můžete změnit simulovanou vzdálenost dvou prsty před tím, než jste gesto roztažení prstů nebo přiblížení.  

- ![Gesto roztažení prstů, přiblížení a rotace cílů](../debugger/media/simulator-twofingerengaged.png "SIMULATOR_TwoFingerEngaged")  

  - Stiskněte levé tlačítko a otáčejte kolečkem (směrem dozadu) k přiblížení (gesto roztažení prstů).  

  - Stiskněte levé tlačítko a otáčejte kolečkem myši (od sebe), které chcete oddálit (přiblížení).  
  
## <a name="object-rotation"></a>Otočení objektu  
 Tlačítko pro **otočení dotykového ovládání** nastaví režim interakce k otočení gesty pomocí dvou prsty.  
  
- Přesunutím myši umístěte ikony nad objekt na obrazovce zařízení.  
  
  - Otočením kolečka myši směrem dozadu nebo dopředu změňte simulovanou orientaci dvou prsty před otočením objektu.  

- Stiskněte levé tlačítko a otáčejte kolečkem (směrem dozadu), abyste přetočili objekt proti směru hodinových ručiček. Při otočení kolečka myši se jedna ze dvou cílových ikon otočí kolem druhé, aby označovala relativní velikost otočení.  

  - Stiskněte levé tlačítko a otočte kolečkem myši (od sebe), aby se objekt otáčí po směru hodinových ručiček.  

## <a name="enable-or-disable-always-on-top-mode"></a><a name="BKMK_Enable_or_disable_Always_on_top_mode"></a> Povolit nebo zakázat režim Always On Top  
 Okno simulátoru můžete nastavit tak, aby se vždy nacházet na dalších oknech. Tlačítko **Přepnout nad oknem okna** povolí nebo zakáže **horní** režim okna simulátoru.  
  
## <a name="change-the-device-orientation"></a><a name="BKMK_Change_the_device_orientation"></a> Změna orientace zařízení  
 Orientaci zařízení mezi úrovněmi na výšku a na šířku můžete přepínat otočením simulátoru 90 stupňů v libovolném směru.  
  
> [!NOTE]
> Simulátor nerespektuje vlastnost [DisplayProperties. AutoRotationPreferences](https://msdn.microsoft.com/library/windows/apps/windows.graphics.display.displayproperties.autorotationpreferences.aspx) projektu. Například pokud váš projekt nastaví orientaci na `Landscape` , a pak dojde k otočení simulátoru na orientaci na výšku, zobrazí se také obrázek simulátoru, který se změní na výšku. Otestujte tato nastavení na skutečném zařízení.  
  
> [!NOTE]
> Pokud otočíte simulátor tak, že je jeden okraj simulátoru větší než obrazovka, na které je zobrazený, simulátor se automaticky přizpůsobí velikosti obrazovky. Při opětovném otočení se simulátor nemění na původní velikost.  
  
## <a name="change-the-simulated-screen-size-and-resolution"></a><a name="BKMK_Change_the_simulated_screen_size_and_resolution"></a> Změna velikosti simulované obrazovky a jejich rozlišení  
 Chcete-li změnit simulovanou velikost a rozlišení obrazovky, vyberte v paletě tlačítko **rozlišení změn** a v seznamu vyberte novou velikost a rozlišení.  
  
 Velikost obrazovky a rozlišení jsou uvedeny jako *Šířka obrazovky, Šířka pixelů X pixelů*. Všimněte si, že velikost obrazovky i rozlišení jsou simulované. Poloha souřadnice na simulátoru se převede na souřadnice vybrané velikosti a rozlišení zařízení.  
  
> [!NOTE]
> V aplikaci můžete ukládat verze rastrových obrázků s horizontálním škálováním a systém Windows načte správnou image pro aktuální měřítko. Další informace najdete v článku s [odezvou na návrh 101](https://msdn.microsoft.com/library/windows/apps/dn958435.aspx). Pokud však změníte rozlišení simulátoru, takže systém Windows vybere jiný obrázek, aby odpovídal rozlišení, je nutné zastavit a znovu spustit ladicí relaci, aby zobrazila nový obrázek.  
  
## <a name="capture-a-screenshot-of-your-app-for-submission-to-the-windows-store"></a><a name="BKMK_Capture_a_screenshot_of_your_app_for_submission_to_the_Microsoft_Store"></a> Zachytit snímek obrazovky vaší aplikace pro odeslání do Windows Storu  
 Když odešlete aplikaci do Windows App Storu, musíte zahrnout snímky obrazovky aplikace.  
  
> [!NOTE]
> Snímek obrazovky je uložený v aktuálním rozlišení simulátoru. Chcete-li změnit rozlišení, klikněte na tlačítko **změnit rozlišení** .  
  
- Chcete-li vytvořit snímky obrazovky vaší aplikace z simulátoru, klikněte na tlačítko **zachytit snímek obrazovky se schránkou** .  
  
- Chcete-li nastavit umístění, kde jsou umístěny snímky obrazovky, klikněte na tlačítko **nastavení snímku obrazovky** a z místní nabídky vyberte umístění.  
  
     ![Místní nabídka nastavení snímků obrazovky](../debugger/media/simulator-screenshotsettingscntxmnu.png "SIMULATOR_ScreenShotSettingsCntxMnu")  
  
## <a name="simulate-network-connection-properties"></a><a name="BKMK_Simulate_network_connection_properties"></a> Simulovat vlastnosti síťového připojení  
 Můžete uživatelům vaší aplikace spravovat náklady na měřené síťové připojení tím, že udržují povědomí o nákladech na síťové připojení nebo změnách stavu datového tarifu a umožníte, aby vaše aplikace tyto informace používala k tomu, aby se předešlo dalším nákladům na roaming nebo překročení zadaného limitu přenosu dat. Rozhraní API pro [Windows. Networking. Connectivity](https://msdn.microsoft.com/library/windows/apps/windows.networking.connectivity.aspx) umožňuje reagovat na události [NetworkStatusChanged](https://msdn.microsoft.com/library/windows/apps/windows.networking.connectivity.networkinformation.networkstatuschanged.aspx) a [TriggerType](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.background.systemtrigger.triggertype.aspx) , které se podepisují. Další informace najdete v tématu [rychlý Start: Správa omezení podle objemu nákladů na síť](https://msdn.microsoft.com/library/windows/apps/Hh750310.aspx).  
  
 Pro ladění a testování kódu, který zohledňuje náklady na síť, může simulátor napodobovat vlastnosti sítě, které jsou vystaveny prostřednictvím objektu [ConnectionProfile](https://msdn.microsoft.com/library/windows/apps/windows.networking.connectivity.connectionprofile.aspx) , který vrátila [GetInternetConnectionProfile](https://msdn.microsoft.com/library/windows/apps/windows.networking.connectivity.networkinformation.getinternetconnectionprofile.aspx)..  
  
 Simulace vlastností sítě:  
  
1. Na panelu nástrojů simulátor klikněte na tlačítko **změnit vlastnosti sítě** .  
  
2. V dialogovém okně **nastavit vlastnosti sítě** vyberte **použít vlastnosti simulované sítě**.  
  
    Zrušením zaškrtnutí políčka odeberte simulaci a vraťte se do vlastností sítě aktuálně připojeného rozhraní.  
  
3. Zadejte **název profilu** simulované sítě. Doporučujeme použít jedinečný název, který můžete použít k identifikaci simulace [ve vlastnosti](https://msdn.microsoft.com/library/windows/apps/windows.networking.connectivity.connectionprofile.profilename.aspx) [proConnectionProfile](https://msdn.microsoft.com/library/windows/apps/windows.networking.connectivity.connectionprofile.aspx) objektu.  
  
4. Vyberte hodnotu [NetworkCostType](https://msdn.microsoft.com/library/windows/apps/windows.networking.connectivity.networkcosttype.aspx) pro profil ze seznamu **Typ nákladů na síť** .  
  
5. V seznamu **příznak stavu limitu dat** můžete nastavit vlastnost [ApproachingDataLimit](https://msdn.microsoft.com/library/windows/apps/windows.networking.connectivity.connectioncost.approachingdatalimit.aspx) nebo vlastnost [OverDataLimit](https://msdn.microsoft.com/library/windows/apps/windows.networking.connectivity.connectioncost.overdatalimit.aspx)na hodnotu true, nebo můžete vybrat možnost **v části omezení dat** a nastavit obě hodnoty na hodnotu false.  
  
6. V seznamu **stav roamingu** nastavte vlastnost [roaming](https://msdn.microsoft.com/library/windows/apps/windows.networking.connectivity.connectioncost.roaming.aspx) .  
  
7. Vyberte **nastavit vlastnosti** pro simulaci vlastností sítě aktivací události [NetworkStatusChanged](https://msdn.microsoft.com/library/windows/apps/windows.networking.connectivity.networkinformation.networkstatuschanged.aspx) popředí a [SystemTrigger](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.background.systemtrigger.aspx) na pozadí typu **NetworkStateChange**.  
  
   **Další informace o správě síťových připojení**  
  
   [Rychlý Start: Správa omezení pro náklady na měření sítě](https://msdn.microsoft.com/library/windows/apps/Hh750310.aspx)  
  
   [Ukázka informací o síti](https://code.msdn.microsoft.com/windowsapps/Network-Information-Sample-63aaa201)  
  
   [Analýza spotřeby energie](../profiling/analyze-energy-use-in-store-apps.md)  
    
   [Windows. Networking. Connectivity](https://msdn.microsoft.com/library/windows/apps/windows.networking.connectivity.aspx)  
  
   [Postup reakce na události systému s úlohami na pozadí](https://msdn.microsoft.com/f7c86e86-a7ae-4abb-a923-76b03337a80a)  
  
   [Jak aktivovat události pozastavení, obnovení a na pozadí v aplikacích pro Windows Store](https://msdn.microsoft.com/library/windows/apps/hh974425.aspx)  
  
## <a name="navigate-the-simulator-with-the-keyboard"></a><a name="BKMK_Navigate_the_simulator_with_the_keyboard"></a> Procházení simulátoru pomocí klávesnice  
 Panel nástrojů simulátor můžete procházet stisknutím **kombinace kláves CTRL + ALT + šipka nahoru** a přepnout fokus z okna simulátoru na panel nástrojů simulátoru. Pomocí **šipky nahoru** a **dolů** se můžete pohybovat mezi tlačítky na panelu nástrojů.  
  
 Simulátor můžete vypnout stisknutím **kombinace kláves CTRL + ALT + F4**.  
  
## <a name="see-also"></a>Viz také  
 [Spouštění aplikací ze sady Visual Studio](../debugger/run-store-apps-from-visual-studio.md)
