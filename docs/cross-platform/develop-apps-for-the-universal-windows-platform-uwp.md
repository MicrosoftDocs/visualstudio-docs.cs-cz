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
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75587144"
---
# <a name="develop-apps-for-the-universal-windows-platform-uwp"></a>Vývoj aplikací pro Univerzální platformu Windows (UWP)

Pomocí Univerzální platforma Windows a naší sady Windows Core můžete stejnou aplikaci spustit na jakémkoli zařízení s Windows 10, od telefonů po stolní počítače. Vytvářejte tyto univerzální aplikace pro Windows pomocí sady Visual Studio a nástrojů pro vývoj univerzálních aplikací pro Windows.

![Univerzální platforma pro Windows](../cross-platform/media/uwp_coreextensions.png)

Spuštění aplikace na telefonu s Windows 10, Windows 10 desktop a Xbox. Je to stejný balíček aplikace! Zavedení projektového systému Windows 10 jediném, sjednoceném jádře jeden balíček aplikace poběží na všech platformách. Několik platforem má rozšiřující sady SDK, které můžete přidat do své aplikace, abyste mohli využít výhod specifického chování platformy. Například zpracovává sadu SDK rozšíření pro mobilní zařízení se ve Windows phonu stisknutí tlačítka Zpět. Pokud odkazujete na sadu SDK rozšíření v projektu, stačí přidat kontroly za běhu k otestování, jestli je tato sada SDK na této platformě k dispozici. To je to, jak můžete mít stejný balíček aplikace pro každou platformu.

**Co je Windows Core?**

V první době se systém Windows refaktoruje tak, aby měl společný jádro pro všechny platformy Windows 10. Existuje jeden společný zdroj, jeden společný jádro systému Windows, jeden zásobník v/v souborů a jeden model aplikace. Pro uživatelské rozhraní existuje pouze jedno rozhraní XAML UI Framework a jedno rozhraní HTML UI. Můžete se soustředit na vytvoření skvělé aplikace, protože jsme usnadnili, aby vaše aplikace běžela na různých zařízeních s Windows 10.

**Co přesně je Univerzální platforma Windows?**

Univerzální platforma Windows je pouze kolekce kontraktů a verzí. Ty vám umožní zaměřit se na to, kde se vaše aplikace může spouštět. Už necílíte na operační systém. teď cílíte na jednu nebo víc rodin zařízení. Další informace najdete v [úvodu k Univerzální platforma Windows](/windows/uwp/get-started/universal-application-platform-guide).

## <a name="requirements"></a>Požadavky

Nástroje pro vývoj univerzálních aplikací pro Windows přináší emulátory, které můžete použít k zobrazení, jak vaše aplikace vypadá na různých zařízeních. Pokud chcete použít tyto emulátory, musíte tento software nainstalovat na fyzický počítač. Fyzický počítač musí běžet Windows 8.1 (x64) Professional Edition nebo vyšší a musí mít procesor, který podporuje technologii Klient Hyper-V a překlad adres druhé úrovně (SLAT). Emulátory nelze použít, pokud je aplikace Visual Studio nainstalována na virtuálním počítači.

Tady je seznam softwaru, který potřebujete:

::: moniker range="vs-2017"

- [Windows 10](https://support.microsoft.com/help/17777/downloads-for-windows). Visual Studio 2017 podporuje vývoj UWP jenom ve Windows 10. Další podrobnosti najdete v tématu [cílení na platformu](/visualstudio/productinfo/vs2017-compatibility-vs) a [požadavky na systém](/visualstudio/productinfo/vs2017-system-requirements-vs)pro Visual Studio.

- [Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download). Budete také potřebovat volitelnou úlohu vývoje Univerzální platforma Windows.

     ![Úlohy UWP](media/uwp_workload.png)

::: moniker-end

::: moniker range="vs-2019"

- [Windows 10](https://support.microsoft.com/help/17777/downloads-for-windows). Visual Studio 2019 podporuje vývoj UWP jenom ve Windows 10. Další podrobnosti najdete v tématu [cílení na platformu](/visualstudio/releases/2019/compatibility/) a [požadavky na systém](/visualstudio/releases/2019/system-requirements/)pro Visual Studio.

- [Visual Studio](https://visualstudio.microsoft.com/downloads). Budete také potřebovat volitelnou úlohu vývoje Univerzální platforma Windows.

     ![Úlohy UWP](media/uwp_workload.png)

::: moniker-end

Po instalaci tohoto softwaru je potřeba povolit pro vývoj zařízení s Windows 10. Viz [Povolení vývoje zařízení](/windows/uwp/get-started/enable-your-device-for-development). Už nepotřebujete vývojářskou licenci pro každé zařízení s Windows 10.

## <a name="universal-windows-apps"></a>Univerzální aplikace pro Windows

Vyberte preferovaný vývojový jazyk z C#, Visual Basic C++ nebo JavaScript a vytvořte univerzální platforma Windows aplikaci pro zařízení s Windows 10. Přečtěte si téma [Vytvoření první aplikace](/windows/uwp/get-started/your-first-app) nebo sledujte video s [přehledem nástrojů pro Windows 10](https://channel9.msdn.com/Series/ConnectOn-Demand/229) .

Pokud máte existující aplikace pro Windows Store 8,1, Windows Phone 8,1 nebo univerzální aplikace pro Windows vytvořené pomocí sady Visual Studio 2015, budete muset tyto aplikace přenést, aby používaly nejnovější Univerzální platforma Windows. Viz [přesunout z prostředí Windows Runtime 8. x do UWP](/windows/uwp/porting/w8x-to-uwp-root).

Po vytvoření univerzální aplikace pro Windows je nutné zabalit aplikaci, aby ji bylo možné nainstalovat na zařízení s Windows 10, nebo ji odeslat do Windows Storu. Viz vytváření [balíčků aplikací](/windows/uwp/packaging/index).

## <a name="see-also"></a>Viz také:

- [Vývoj mobilních aplikací pro různé platformy v aplikaci Visual Studio](../cross-platform/cross-platform-mobile-development-in-visual-studio.md)
