---
title: Vývoj aplikací pro Univerzální platforma Windows (UWP) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: tgt-pltfrm-cross-plat
ms.topic: conceptual
ms.assetid: eac59cb6-f12e-4a77-9953-6d62b164a643
caps.latest.revision: 50
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: ac6ce00002e40c6d8bd1d5db65b8c7bb5e6bc7cd
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2019
ms.locfileid: "74299839"
---
# <a name="develop-apps-for-the-universal-windows-platform-uwp"></a>Vývoj aplikací pro Univerzální platformu Windows (UWP)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Univerzální platforma Windows a naše jednoho jádra Windows můžete spustit stejné aplikace na všechna zařízení s Windows 10 z telefonů stolní počítače. Vytvořte tyto Universal Windows apps pomocí sady Visual Studio 2015 a nástroje pro vývoj univerzálních aplikací pro Windows.

 ![Univerzální platforma Windows](../cross-platform/media/uwp-coreextensions.png "UWP_CoreExtensions")

 Spuštění aplikace na telefonu s Windows 10, Windows 10 desktop a Xbox. Jedná se o stejné balíček aplikace! Zavedení projektového systému Windows 10 jediném, sjednoceném jádře jeden balíček aplikace poběží na všech platformách. Několik platforem mají rozšíření SDK, která můžete přidat do své aplikace a využít výhod chování pro konkrétní platformu. Například zpracovává sadu SDK rozšíření pro mobilní zařízení se ve Windows phonu stisknutí tlačítka Zpět. Pokud ve vašem projektu odkazovat na rozšíření SDK, stačí přidat elementy kontroly za běhu, který testuje, jestli je k dispozici na této platformě této sady SDK. To je, jak můžete použít balíček aplikace pro každou platformu!

 **Co je Windows Core?**

 V první době se systém Windows refaktoruje tak, aby měl společný jádro pro všechny platformy Windows 10. Existuje jeden společný zdroj, jeden společný jádro systému Windows, jeden zásobník v/v souborů a jeden model aplikace. Pro uživatelské rozhraní existuje pouze jedno rozhraní XAML UI Framework a jedno rozhraní HTML UI. Takže se můžete soustředit na vytvoření skvělé aplikace, protože jsme usnadnili, aby vaše aplikace běžela na různých zařízeních s Windows 10.

 **Co přesně je Univerzální platforma Windows?**

 Je to jednoduše kolekce kontraktů a verzí. Ty vám umožní zaměřit se na to, kde se vaše aplikace může spouštět. Už necílíte na operační systém. Nyní aplikaci zacílíte na jednu nebo více rodiny zařízení. Další podrobnosti najdete v této [příručce k platformě](https://msdn.microsoft.com/library/windows/apps/dn894631.aspx).

## <a name="requirements"></a>Požadavky
 Nástroje pro vývoj univerzálních aplikací pro Windows přináší emulátory, které můžete použít k zobrazení, jak vaše aplikace vypadá na různých zařízeních. Pokud chcete použít tyto emulátory, musíte tento software nainstalovat na fyzický počítač. Fyzický počítač musí běžet Windows 8.1 (x64) Professional Edition nebo vyšší a musí mít procesor, který podporuje technologii Klient Hyper-V a překlad adres druhé úrovně (SLAT). Emulátory nelze použít, pokud je aplikace Visual Studio nainstalována na virtuálním počítači.

 Tady je seznam softwaru, který potřebujete:

- [Windows 10](https://windows.microsoft.com/windows/downloads)

- [Visual Studio 2015](https://go.microsoft.com/fwlink/p/?LinkId=526725). Ujistěte se, že jsou vybrané nástroje pro vývoj univerzálních aplikací pro Windows ze seznamu volitelných funkcí. Bez těchto nástrojů nebudete moct vytvářet své univerzální aplikace.

  Po instalaci tohoto softwaru je potřeba povolit pro vývoj [zařízení s Windows 10](https://msdn.microsoft.com/library/windows/apps/xaml/dn706236.aspx) . (Pro každé zařízení s Windows 10 už nebudete potřebovat vývojářskou licenci.)

  **Podpora Windows 8.1 a Windows 7**

  Pokud se rozhodnete pro vývoj univerzálních aplikací pro Windows pomocí sady Visual Studio 2015 na jiné platformě než Windows 10, jedná se o tato omezení:

- Windows 8.1: aplikaci nemůžete spouštět místně (jenom na vzdáleném zařízení s Windows 10). Můžete použít emulátory v aplikaci Visual Studio, ale ne simulátor.

- Windows 7: aplikaci nemůžete spouštět místně (jenom na vzdáleném zařízení s Windows 10). Nemůžete použít emulátory ani simulátor v aplikaci Visual Studio ani jeden z nich.

  Návrhář XAML můžete použít pouze v případě, že vaše vývojová platforma používá systém Windows 10.

## <a name="universal-windows-apps"></a>Univerzální aplikace pro Windows
 Vyberte preferovaný vývojový jazyk z C#, Visual Basic C++ nebo JavaScript pro [Vytvoření univerzální aplikace pro Windows pro zařízení s Windows 10](https://msdn.microsoft.com/library/windows/apps/xaml/dn609832.aspx#target_win10). Nebo si přehrajte [Toto úvodní video](https://channel9.msdn.com/Series/ConnectOn-Demand/229).

 Pokud máte stávající aplikace pro Windows Store 8,1, Windows Phone 8,1 nebo univerzální aplikace pro Windows vytvořené pomocí sady Visual Studio 2015 RC, [přeportů těchto stávajících aplikací](https://msdn.microsoft.com/library/windows/apps/xaml/mt238321.aspx) na používání nejnovější Univerzální platforma Windows.

 Po vytvoření univerzální aplikace pro Windows je nutné [zabalit aplikaci](https://msdn.microsoft.com/library/windows/apps/hh454036.aspx) , aby ji bylo možné nainstalovat na zařízení s Windows 10, nebo ji odeslat do Windows Storu.
