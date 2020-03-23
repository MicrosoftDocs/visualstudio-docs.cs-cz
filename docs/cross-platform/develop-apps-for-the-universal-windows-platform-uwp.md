---
title: Vývoj aplikací pro Univerzální platformu Windows (UWP)
ms.date: 10/24/2017
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: eac59cb6-f12e-4a77-9953-6d62b164a643
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- uwp
ms.openlocfilehash: 2ef09f58d22e3cb72af5b745f16b2acf8920900e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75587144"
---
# <a name="develop-apps-for-the-universal-windows-platform-uwp"></a>Vývoj aplikací pro Univerzální platformu Windows (UWP)

S univerzální platformou Windows a naším jedním jádrem Windows můžete spustit stejnou aplikaci na jakémkoli zařízení s Windows 10, od telefonů až po stolní počítače. Vytvořte tyto univerzální aplikace pro Windows pomocí Sady Visual Studio a univerzálních nástrojů pro vývoj aplikací pro Windows.

![Univerzální platforma Windows](../cross-platform/media/uwp_coreextensions.png)

Spusťte aplikaci na telefonu s Windows 10, na ploše s Windows 10 nebo na Xboxu. Je to stejný balíček aplikací! Se zavedením jednotného jádra Windows 10 může jeden balíček aplikace běžet na všech platformách. Několik platforem má rozšíření sady SDK, které můžete přidat do aplikace, abyste mohli využívat chování specifické pro platformu. Například rozšíření SDK pro mobilní zvládá tlačítko Zpět stisknuté na telefonu se systémem Windows. Pokud odkazujete na rozšíření SDK v projektu, pak stačí přidat runtime kontroly k testování, pokud tato sada SDK je k dispozici na této platformě. To je, jak můžete mít stejný balíček aplikace pro každou platformu!

**Co je jádro systému Windows?**

Poprvé byl systém Windows refaktorován tak, aby měl společné jádro na všech platformách Windows 10. Existuje jeden společný zdroj, jedno společné jádro systému Windows, jeden zásobník vstupně-va souborů a jeden model aplikace. Pro uživatelské rozhraní existuje pouze jeden rozhraní uživatelského rozhraní XAML a jeden rámec uživatelského rozhraní HTML. Můžete se soustředit na vytvoření skvělé aplikace, protože jsme vám usnadnili spuštění aplikace na různých zařízeních s Windows 10.

**Co přesně je univerzální platforma Windows?**

Univerzální platforma Windows je jednoduše kolekce smluv a verzí. Ty vám umožní cílit, kde může vaše aplikace běžet. Již cílíte na operační systém. nyní cílíte na jednu nebo více rodin zařízení. Další podrobnosti najdete [v úvodním úvodu na univerzální platformu Windows](/windows/uwp/get-started/universal-application-platform-guide).

## <a name="requirements"></a>Požadavky

Univerzální nástroje pro vývoj aplikací pro Windows jsou dodávány s emulátory, které můžete použít k zobrazení vzhledu aplikace na různých zařízeních. Pokud chcete použít tyto emulátory, je třeba nainstalovat tento software na fyzickém počítači. Fyzický počítač musí spustit Windows 8.1 (x64) Professional edition nebo vyšší a mít procesor, který podporuje překlad adres klienta Hyper-V a překlad adresy druhé úrovně (SLAT). Emulátory nelze použít, pokud je visual studio nainstalováno ve virtuálním počítači.

Zde je seznam softwaru, který potřebujete:

::: moniker range="vs-2017"

- [Windows 10](https://support.microsoft.com/help/17777/downloads-for-windows). Visual Studio 2017 podporuje vývoj UPW pouze ve Windows 10. Další podrobnosti naleznete v [tématu Visual](/visualstudio/productinfo/vs2017-compatibility-vs) Studio Platform cílení a [systémové požadavky](/visualstudio/productinfo/vs2017-system-requirements-vs).

- Sadu [Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download). Budete také potřebovat volitelné úlohy vývoje univerzální platformy Windows.

     ![Pracovní vytížení UPW](media/uwp_workload.png)

::: moniker-end

::: moniker range="vs-2019"

- [Windows 10](https://support.microsoft.com/help/17777/downloads-for-windows). Visual Studio 2019 podporuje vývoj UPW pouze ve Windows 10. Další podrobnosti naleznete v [tématu Visual](/visualstudio/releases/2019/compatibility/) Studio Platform cílení a [systémové požadavky](/visualstudio/releases/2019/system-requirements/).

- Sadu [Visual Studio](https://visualstudio.microsoft.com/downloads). Budete také potřebovat volitelné úlohy vývoje univerzální platformy Windows.

     ![Pracovní vytížení UPW](media/uwp_workload.png)

::: moniker-end

Po instalaci tohoto softwaru je třeba povolit vývoj zařízení s Windows 10. Viz [Povolení vývoje zařízení](/windows/uwp/get-started/enable-your-device-for-development). Pro každé zařízení s Windows 10 už nepotřebujete vývojářskou licenci.

## <a name="universal-windows-apps"></a>Univerzální aplikace pro Windows

Vyberte si preferovaný vývojový jazyk z C#, Visual Basic, C++ nebo JavaScriptu a vytvořte aplikaci pro univerzální platformu Windows pro zařízení s Windows 10. Přečtěte si [článek Vytvoření první aplikace](/windows/uwp/get-started/your-first-app) nebo video Přehled nástrojů pro Windows [10.](https://channel9.msdn.com/Series/ConnectOn-Demand/229)

Pokud máte existující aplikace pro Windows Store 8.1, aplikace pro Windows Phone 8.1 nebo univerzální aplikace pro Windows, které byly vytvořeny ve Visual Studiu 2015, budete muset tyto aplikace portovat, abyste mohli používat nejnovější univerzální platformu Windows. Viz [Přesun z prostředí Windows Runtime 8.x do UPW](/windows/uwp/porting/w8x-to-uwp-root).

Po vytvoření univerzální aplikace pro Windows musíte aplikaci zabalit a nainstalovat ji na zařízení s Windows 10 nebo ji odeslat do Windows Storu. Viz [Balení aplikací](/windows/uwp/packaging/index).

## <a name="see-also"></a>Viz také

- [Vývoj mobilních zařízení napříč platformami ve Visual Studiu](../cross-platform/cross-platform-mobile-development-in-visual-studio.md)
