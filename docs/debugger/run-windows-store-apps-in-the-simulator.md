---
title: Spouštění aplikací pro UWP v simulátoru | Microsoft Docs
description: Pochopte, jak spouštět aplikace Univerzální platforma Windows (UWP) v simulátoru sady Visual Studio, což je aplikace klasické pracovní plochy, která simuluje aplikaci pro UWP.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: 81b69bf8-ec87-4bb6-9ad4-1fa7b7802d16
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- uwp
ms.openlocfilehash: b9a6c2ceeb9a3c384329f167ec158b213f3d15a8
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99887585"
---
# <a name="run-uwp-apps-in-the-simulator"></a>Spouštění aplikací pro UPW na simulátoru

Simulátor sady Visual Studio pro aplikace UWP je desktopová aplikace, která simuluje aplikaci pro UWP. Obvykle budete chtít ladit na místním počítači, připojeném zařízení nebo na vzdáleném počítači. V některých scénářích však můžete chtít použít simulátor sady Visual Studio k emulaci jiné velikosti fyzické obrazovky a rozlišení. Můžete také simulovat běžné události dotykové ovládání a rotace a simulovat vlastnosti síťového připojení.

Simulátor poskytuje prostředí, ve kterém můžete navrhovat, vyvíjet, ladit a testovat aplikace pro UWP. Před publikováním aplikace v Microsoft Store byste však měli aplikaci otestovat na skutečném zařízení.

Simulátor sady Visual Studio pro aplikace pro UWP neběží v izolovaném prostředí na místním počítači. Chyby, ke kterým dochází v simulátoru, jako je například neobnovitelná chyba systému, mohou také ovlivnit celý počítač.

> [!IMPORTANT]
> Simulátor sady Visual Studio 2015 nezahrnuje tlačítko geografického umístění. Důvodem je to, že simulátor Windows 10 neobsahuje simulaci geografického umístění.

## <a name="set-the-simulator-as-the-target"></a><a name="BKMK_Set_the_simulator_as_the_target"></a> Nastavit simulátor jako cíl

Pokud chcete aplikaci UWP spustit v simulátoru, vyberte v rozevíracím seznamu vedle tlačítka **Spustit ladění** na panelu nástrojů **standardní** ladicí program **simulátor** . Tato možnost je dostupná jenom v případě, že je **Minimální verze cílové platformy** vaší aplikace menší než nebo se rovná operačnímu systému na vašem vývojovém počítači.

![Běžící v simulátoru](../debugger/media/vsrun_f5_simulator.png "VSRUN_F5_Simulator")

## <a name="choose-an-interaction-mode"></a><a name="BKMK_Choose_an_interaction_mode"></a> Zvolit režim interakce

Můžete zvolit následující režimy interakce:

- ![Tlačítko režimu myši](../debugger/media/simulator_mousemodebtn.png "SIMULATOR_MouseModeBtn") Režim myši: nastaví režim interakce na gesta myši. Gesta myši zahrnují kliknutí, dvojité kliknutí a přetahování.

- ![Tlačítko spustit emulaci dotykového ovládání](../debugger/media/simulator_starttouchemulationbtn.png "SIMULATOR_StartTouchEmulationBtn") Zahájit emulaci dotykového ovládání: nastaví režim interakce na dotykové gesta jednoho prstu. Události s jedním prstem zahrnují klepnutí, přetahování a přetáhnutí.

   ![Simulátor – jeden cíl Finger](../debugger/media/simulator_onefinger.png "SIMULATOR_OneFinger")
   
   Ikona s jedním cílem indikuje umístění událostí v simulátoru. Ukazatel myši umístěte pomocí myši.

   ![Cíl dotykového ovládání](../debugger/media/simulator_onefingerengaged.png "SIMULATOR_OneFingerEngaged")
   
   Stisknutím levého tlačítka myši aktivujete režim dotykového ovládání. Například klikněte na tlačítko pro simulaci klepnutí nebo stiskněte a držte tlačítko při přetahování myší nebo potažením prstem.

## <a name="pinch-and-zoom"></a>Gesto roztažení prstů a přiblížení

Nastaví režim interakce na gesto roztažení prstů a přiblížení gest dvou prsty.

![Kosimulátor – cíl dvou prstů](../debugger/media/simulator_twofinger.png)

Ikona dvojitého cíle indikuje umístění dvou prsty na obrazovce zařízení.

- Přesunutím myši umístěte ikony nad objekt na obrazovce zařízení.

- Otočením kolečka myši směrem dozadu nebo dopředu můžete změnit simulovanou vzdálenost dvou prsty před tím, než jste gesto roztažení prstů nebo přiblížení.

![Gesto roztažení prstů, přiblížení a rotace cílů](../debugger/media/simulator_twofingerengaged.png)

- Stiskněte levé tlačítko a otáčejte kolečkem (směrem dozadu) k přiblížení (gesto roztažení prstů).

- Stiskněte levé tlačítko a otáčejte kolečkem myši (od sebe), které chcete oddálit (přiblížení).

## <a name="object-rotation"></a>Otočení objektu

Tlačítko pro **otočení dotykového ovládání** nastaví režim interakce k otočení gesty pomocí dvou prsty.

- Přesunutím myši umístěte ikony nad objekt na obrazovce zařízení. Otočením kolečka myši směrem dozadu nebo dopředu změňte simulovanou orientaci dvou prsty před otočením objektu.

- Stiskněte levé tlačítko a otáčejte kolečkem (směrem dozadu), abyste přetočili objekt proti směru hodinových ručiček. Při otočení kolečka myši se jedna ze dvou cílových ikon otočí kolem druhé, aby označovala relativní velikost otočení.

- Stiskněte levé tlačítko a otočte kolečkem myši (od sebe), aby se objekt otáčí po směru hodinových ručiček.

## <a name="enable-or-disable-always-on-top-mode"></a><a name="BKMK_Enable_or_disable_Always_on_top_mode"></a> Povolit nebo zakázat režim Always On Top
 Okno simulátoru můžete nastavit tak, aby se vždy nacházet na dalších oknech. Tlačítko **Přepnout nad oknem okna** povolí nebo zakáže **horní** režim okna simulátoru.

## <a name="change-the-device-orientation"></a><a name="BKMK_Change_the_device_orientation"></a> Změna orientace zařízení
 Orientaci zařízení mezi úrovněmi na výšku a na šířku můžete přepínat otočením simulátoru 90 stupňů v libovolném směru.

> [!NOTE]
> Simulátor nerespektuje vlastnost [DisplayProperties. AutoRotationPreferences](/uwp/api/windows.graphics.display.displayproperties.autorotationpreferences) projektu. Například pokud váš projekt nastaví orientaci na `Landscape` , a pak dojde k otočení simulátoru na orientaci na výšku, zobrazí se také obrázek simulátoru, který se změní na výšku. Otestujte tato nastavení na skutečném zařízení.

> [!NOTE]
> Pokud otočíte simulátor tak, že je jeden okraj simulátoru větší než obrazovka, na které je zobrazený, simulátor se automaticky přizpůsobí velikosti obrazovky. Při opětovném otočení se simulátor nemění na původní velikost.

## <a name="change-the-simulated-screen-size-and-resolution"></a><a name="BKMK_Change_the_simulated_screen_size_and_resolution"></a> Změna velikosti simulované obrazovky a jejich rozlišení
 Chcete-li změnit simulovanou velikost a rozlišení obrazovky, vyberte v paletě tlačítko **rozlišení změn** a v seznamu vyberte novou velikost a rozlišení.

 Velikost obrazovky a rozlišení jsou uvedeny jako *Šířka obrazovky, Šířka pixelů X pixelů*. Všimněte si, že velikost obrazovky i rozlišení jsou simulované. Souřadnice umístění simulátoru jsou přeloženy na zvolené velikosti a rozlišení zařízení.

> [!NOTE]
> V aplikaci můžete ukládat verze rastrových obrázků s horizontálním škálováním a systém Windows načte správnou image pro aktuální měřítko. Další informace najdete v tématu [Návrh a úvodní uživatelské rozhraní](/windows/uwp/layout/design-and-ui-intro). Pokud však změníte rozlišení simulátoru, takže systém Windows vybere jiný obrázek, aby odpovídal rozlišení, je nutné zastavit a znovu spustit ladicí relaci, aby zobrazila nový obrázek.

## <a name="capture-a-screenshot-of-your-app-for-submission-to-microsoft-store"></a><a name="BKMK_Capture_a_screenshot_of_your_app_for_submission_to_the_Microsoft_Store"></a> Zachytit snímek obrazovky vaší aplikace pro odeslání do Microsoft Store
 Když odešlete aplikaci do Microsoft Store, musíte zahrnout snímky obrazovky aplikace.

> [!NOTE]
> Snímek obrazovky je uložený v aktuálním rozlišení simulátoru. Chcete-li změnit rozlišení, klikněte na tlačítko **změnit rozlišení** .

- Chcete-li vytvořit snímky obrazovky vaší aplikace z simulátoru, klikněte na tlačítko **zachytit snímek obrazovky se schránkou** .

- Chcete-li nastavit umístění, kde jsou umístěny snímky obrazovky, klikněte na tlačítko **nastavení snímku obrazovky** a z místní nabídky vyberte umístění.

   ![Místní nabídka nastavení snímků obrazovky](../debugger/media/simulator_screenshotsettingscntxmnu.png)

## <a name="simulate-network-connection-properties"></a><a name="BKMK_Simulate_network_connection_properties"></a> Simulovat vlastnosti síťového připojení

Můžete uživatelům vaší aplikace spravovat náklady na měřené síťové připojení tím, že udržují povědomí o nákladech na síťové připojení nebo změnách stavu datového tarifu a umožníte, aby vaše aplikace tyto informace používala k tomu, aby se předešlo dalším nákladům na roaming nebo překročení zadaného limitu přenosu dat. Rozhraní API pro [Windows. Networking. Connectivity](/uwp/api/windows.networking.connectivity) umožňuje reagovat na události [NetworkStatusChanged](/uwp/api/windows.networking.connectivity.networkinformation) a [TriggerType](/uwp/api/windows.applicationmodel.background.systemtrigger) , které se podepisují. Další informace najdete v tématu [rychlý Start: Správa omezení podle objemu nákladů na síť](/previous-versions/windows/apps/hh750310(v=win.10)).

Pro ladění a testování kódu, který zohledňuje náklady na síť, může simulátor napodobovat vlastnosti sítě, které jsou vystaveny prostřednictvím objektu [ConnectionProfile](/uwp/api/windows.networking.connectivity.connectionprofile) , který vrací [GetInternetConnectionProfile](/uwp/api/windows.networking.connectivity.networkinformation).

Simulace vlastností sítě:

1. Na panelu nástrojů simulátor klikněte na tlačítko **změnit vlastnosti sítě** .

2. V dialogovém okně **nastavit vlastnosti sítě** vyberte **použít vlastnosti simulované sítě**.

    Zrušením zaškrtnutí políčka odeberte simulaci a vraťte se do vlastností sítě aktuálně připojeného rozhraní.

3. Zadejte **název profilu** simulované sítě. Doporučujeme použít jedinečný název, který můžete použít k identifikaci simulace [ve vlastnosti](/uwp/api/windows.networking.connectivity.connectionprofile) [proConnectionProfile](/uwp/api/windows.networking.connectivity.connectionprofile) objektu.

4. Vyberte hodnotu [NetworkCostType](/uwp/api/windows.networking.connectivity.networkcosttype) pro profil ze seznamu **Typ nákladů na síť** .

5. V seznamu **příznak stavu limitu dat** můžete nastavit vlastnost [ApproachingDataLimit](/uwp/api/windows.networking.connectivity.connectioncost) nebo vlastnost [OverDataLimit](/uwp/api/windows.networking.connectivity.connectioncost) na hodnotu true, nebo můžete vybrat možnost **v části omezení dat** a nastavit obě hodnoty na hodnotu false.

6. V seznamu **stav roamingu** nastavte vlastnost [roaming](/uwp/api/windows.networking.connectivity.connectioncost) .

7. Vyberte **nastavit vlastnosti** pro simulaci vlastností sítě aktivací události [NetworkStatusChanged](/uwp/api/windows.networking.connectivity.networkinformation) popředí a [SystemTrigger](/uwp/api/windows.applicationmodel.background.systemtrigger) na pozadí typu **NetworkStateChange**.

Další informace o správě síťových připojení najdete v těchto tématech:

[Rychlý Start: Správa omezení pro náklady na měření sítě](/previous-versions/windows/apps/hh750310(v=win.10))

[Ukázka informací o síti](https://code.msdn.microsoft.com/windowsapps/Network-Information-Sample-63aaa201)

::: moniker range="vs-2017"
[Analýza spotřeby energie](../profiling/analyze-energy-use-in-store-apps.md)
::: moniker-end

[Windows. Networking. Connectivity](/uwp/api/windows.networking.connectivity)

[Postup reakce na události systému s úlohami na pozadí](/previous-versions/windows/apps/hh977058(v=win.10))

[Jak aktivovat pozastavení, obnovení a události na pozadí v aplikacích pro UWP](how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md)

## <a name="navigate-the-simulator-with-the-keyboard"></a><a name="BKMK_Navigate_the_simulator_with_the_keyboard"></a> Procházení simulátoru pomocí klávesnice

Panel nástrojů simulátor můžete procházet stisknutím **kombinace kláves CTRL + ALT + šipka nahoru** a přepnout fokus z okna simulátoru na panel nástrojů simulátoru. Pomocí **šipky nahoru** a **dolů** se můžete pohybovat mezi tlačítky na panelu nástrojů.

Simulátor můžete vypnout stisknutím **kombinace kláves CTRL + ALT + F4**.

## <a name="see-also"></a>Viz také

- [Spouštění aplikací ze sady Visual Studio](debugging-windows-store-and-windows-universal-apps.md)