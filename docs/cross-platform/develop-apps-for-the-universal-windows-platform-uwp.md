---
title: Vyvíjejte aplikace pro Universal Windows Platform (UWP) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 10/24/2017
ms.technology:
- tgt-pltfrm-cross-plat
ms.topic: conceptual
ms.assetid: eac59cb6-f12e-4a77-9953-6d62b164a643
author: stevehoag
ms.author: shoag
manager: douge
ms.workload:
- uwp
ms.openlocfilehash: de4306b2fa56bf00fd51a741441395b90ed314e5
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2018
ms.locfileid: "44280802"
---
# <a name="develop-apps-for-the-universal-windows-platform-uwp"></a>Vývoj aplikací pro Univerzální platformu Windows (UWP)
Univerzální platformu Windows a naše jednoho jádra Windows můžete stejnou aplikaci spustit na jakékoli zařízení s Windows 10 z telefonů pro stolní počítače. Vytvořte tyto Universal Windows apps pomocí sady Visual Studio a nástroje pro vývoj univerzálních aplikací pro Windows.

 ![Universal Windows Platform](../cross-platform/media/uwp_coreextensions.png "UWP_CoreExtensions")

 Spuštění aplikace na telefonu s Windows 10, Windows 10 desktop a Xbox. Jedná se o stejné balíček aplikace! Zavedení projektového systému Windows 10 jediném, sjednoceném jádře jeden balíček aplikace poběží na všech platformách. Několik platforem mají rozšíření sady SDK, které můžete přidat do své aplikace a využijte výhod chování pro konkrétní platformu. Například zpracovává sadu SDK rozšíření pro mobilní zařízení se ve Windows phonu stisknutí tlačítka Zpět. Pokud ve vašem projektu odkazovat na sadu SDK rozšíření a pak stačí přidat elementy kontroly za běhu, který testuje, jestli je k dispozici na této platformě této sady SDK. To je, jak můžete použít balíček aplikace pro každou platformu!

 **Co je jádro Windows?**

 Poprvé byla refaktorována Windows, aby běžné jádra na všech platformách systému Windows 10. Existuje jeden společný zdroj, jeden společný jádra Windows, jeden zásobníku vstupně-výstupní operace souboru a jeden model aplikace. Pro uživatelské rozhraní je pouze jeden architekturu uživatelského rozhraní XAML a jedno rozhraní HTML uživatelského rozhraní. Protože jsme usnadnili k vaší aplikaci spouštět na různých zařízeních s Windows 10 můžete soustředit na vytváření skvělých aplikací.

 **Co přesně je univerzální platformu Windows?**

Univerzální platforma Windows je jednoduše soubor smluv a verze. Tyto rutiny umožňují vám do cíle, kde lze spustit vaši aplikaci. Nebudou cíleny operačního systému; Nyní můžete cílit na jeden nebo více rodin zařízení. Přečtěte si a zjistěte další podrobnosti [Úvod k univerzální platformě Windows](/windows/uwp/get-started/universal-application-platform-guide).

## <a name="requirements"></a>Požadavky
 Nástroje pro vývoj univerzálních aplikací pro Windows jsou dostupné emulátorů, které vám umožní zjistit, jak vaše aplikace funguje na různých zařízeních. Pokud chcete použít tyto emulátory, budete muset instalovat tento software na fyzickém počítači. Fyzický počítač musí spustit (x64) Windows 8.1 edice Professional nebo vyšší a procesor, který podporuje technologii klient Hyper-V a překlad adres druhé úrovně (SLAT). Emulátory nelze použít, když je na virtuálním počítači nainstalované sady Visual Studio.

 Tady je seznam softwaru, které potřebujete:

-   [Windows 10](http://windows.microsoft.com/windows/downloads). Visual Studio 2017 podporuje vývoj pro UPW pouze ve Windows 10. Další podrobnosti najdete v tématu Visual Studio [cílení na platformy](/visualstudio/productinfo/vs2017-compatibility-vs) a [požadavky na systém](/visualstudio/productinfo/vs2017-system-requirements-vs).

-   [Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017). Musíte také volitelné úlohu vývoje univerzální platformy Windows.

     ![Úlohy UPW](media/uwp_workload.png)

Po instalaci tohoto softwaru, je potřeba povolit zařízení s Windows 10 pro vývoj. Zobrazit [aktivovat zařízení pro vývoj](/windows/uwp/get-started/enable-your-device-for-development). Už nepotřebujete licenci vývojáře pro každé zařízení s Windows 10.

## <a name="universal-windows-apps"></a>Univerzální aplikace pro Windows
Zvolte si jazyk oblíbeným vývojovým z jazyka C#, Visual Basic, C++ nebo JavaScript k vytvoření aplikace pro univerzální platformu Windows pro zařízení s Windows 10. Čtení [vytvořit svoji první aplikaci](/windows/uwp/get-started/your-first-app) nebo si pusťte video [přehled nástrojů pro Windows 10](https://channel9.msdn.com/Series/ConnectOn-Demand/229) videa.

Pokud máte existující aplikace Windows Store 8.1, aplikace pro Windows Phone 8.1 nebo Universal Windows apps, které byly vytvořeny pomocí sady Visual Studio 2015, bude nutné přenést tyto aplikace, které používají nejnovější univerzální platformu Windows. Zobrazit [přesunout z modulu Windows Runtime 8.x na UPW](/windows/uwp/porting/w8x-to-uwp-root).

Po vytvoření aplikace pro Universal Windows, musíte sestavit balíček aplikace nainstalovat na zařízení s Windows 10 nebo odeslání do Windows Store. Zobrazit [balení aplikací](/windows/uwp/packaging/index).

## <a name="see-also"></a>Viz také:
[Vývoj multiplatformních mobilních řešení v sadě Visual Studio](../cross-platform/cross-platform-mobile-development-in-visual-studio.md)
