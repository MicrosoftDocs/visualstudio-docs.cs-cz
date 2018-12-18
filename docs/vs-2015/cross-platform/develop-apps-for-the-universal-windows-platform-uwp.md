---
title: Vyvíjejte aplikace pro Universal Windows Platform (UWP) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- tgt-pltfrm-cross-plat
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: eac59cb6-f12e-4a77-9953-6d62b164a643
caps.latest.revision: 50
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 24dfca5d4ac8432cbe659bb42ca54d0398c47c04
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51766476"
---
# <a name="develop-apps-for-the-universal-windows-platform-uwp"></a>Vývoj aplikací pro Univerzální platformu Windows (UWP)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Univerzální platforma Windows a naše jednoho jádra Windows můžete spustit stejné aplikace na všechna zařízení s Windows 10 z telefonů stolní počítače. Vytvořte tyto Universal Windows apps pomocí sady Visual Studio 2015 a nástroje pro vývoj univerzálních aplikací pro Windows.  
  
 ![Universal Windows Platform](../cross-platform/media/uwp-coreextensions.png "UWP_CoreExtensions")  
  
 Spuštění aplikace na telefonu s Windows 10, Windows 10 desktop a Xbox. Jedná se o stejné balíček aplikace! Zavedení projektového systému Windows 10 jediném, sjednoceném jádře jeden balíček aplikace poběží na všech platformách. Několik platforem mají rozšíření SDK, která můžete přidat do své aplikace a využít výhod chování pro konkrétní platformu. Například zpracovává sadu SDK rozšíření pro mobilní zařízení se ve Windows phonu stisknutí tlačítka Zpět. Pokud ve vašem projektu odkazovat na rozšíření SDK, stačí přidat elementy kontroly za běhu, který testuje, jestli je k dispozici na této platformě této sady SDK. To je, jak můžete použít balíček aplikace pro každou platformu!  
  
 **Co je jádro Windows?**  
  
 Poprvé byla refaktorována Windows, aby běžné jádra na všech platformách systému Windows 10. Existuje jeden společný zdroj, jeden společný jádra Windows, jeden zásobníku vstupně-výstupní operace souboru a jeden model aplikace. Pro uživatelské rozhraní je pouze jeden architekturu uživatelského rozhraní XAML a jedno rozhraní HTML uživatelského rozhraní. Tak můžete soustředit na vytváření skvělých aplikací, protože jsme usnadnili k vaší aplikaci spouštět na různých zařízeních s Windows 10.  
  
 **Co přesně je univerzální platformu Windows?**  
  
 Je jednoduše kolekce smluv a verze. Tyto rutiny umožňují vám do cíle, kde lze spustit vaši aplikaci. Nebudou cíleny operačního systému. Nyní můžete cílit své aplikace na jeden nebo více rodin zařízení. Přečtěte si další informace z tohoto [Průvodce platformou](http://msdn.microsoft.com/library/windows/apps/dn894631.aspx).  
  
## <a name="requirements"></a>Požadavky  
 Nástroje pro vývoj univerzálních aplikací pro Windows jsou dostupné emulátorů, které vám umožní zjistit, jak vaše aplikace funguje na různých zařízeních. Pokud chcete použít tyto emulátory, budete muset instalovat tento software na fyzickém počítači. Fyzický počítač musí spustit (x64) Windows 8.1 edice Professional nebo vyšší a procesor, který podporuje technologii klient Hyper-V a překlad adres druhé úrovně (SLAT). Emulátory nelze použít, když je na virtuálním počítači nainstalované sady Visual Studio.  
  
 Tady je seznam softwaru, které potřebujete:  
  
- [Windows 10](http://windows.microsoft.com/windows/downloads)  
  
- [Visual Studio 2015](http://go.microsoft.com/fwlink/p/?LinkId=526725). Ujistěte se, že jsou v seznamu volitelných funkcí nástroje vývoj univerzálních aplikací Windows. Bez těchto nástrojů nebudete moct vytvářet univerzální aplikace.  
  
  Po instalaci tohoto softwaru, je nutné [povolit zařízení s Windows 10](https://msdn.microsoft.com/library/windows/apps/xaml/dn706236.aspx) pro vývoj. (Už nepotřebujete licenci vývojáře pro každé zařízení s Windows 10.)  
  
  **Podpora Windows 8.1 a Windows 7**  
  
  Pokud vyberete možnost vyvíjet aplikace pro Universal Windows pomocí sady Visual Studio 2015 na platformě jiné než Windows 10, jsou omezení:  
  
- Windows 8.1: Nelze spustit aplikaci místně (pouze na vzdáleném zařízení Windows 10). Můžete použít emulátory v sadě Visual Studio, ale ne simulátor.  
  
- Windows 7: Nelze spustit aplikaci místně (pouze na vzdáleném zařízení Windows 10). V sadě Visual Studio nelze buď použít emulátory ani simulátor.  
  
  Návrhář XAML můžete použít pouze pokud je Vývojová platforma Windows 10.  
  
## <a name="universal-windows-apps"></a>Univerzální aplikace pro Windows  
 Zvolte si jazyk oblíbeným vývojovým v jazycích C#, Visual Basic, C++ nebo JavaScript, který chcete [vytvoření aplikace pro Universal Windows pro zařízení s Windows 10](http://msdn.microsoft.com/library/windows/apps/xaml/dn609832.aspx#target_win10). Nebo si pusťte video [Toto úvodní video](http://channel9.msdn.com/Series/ConnectOn-Demand/229).  
  
 Pokud máte existující aplikace Windows Store 8.1, aplikace pro Windows Phone 8.1 nebo Windows Universal aplikací vytvořených pomocí sady Visual Studio 2015 RC, [portu tyto existující aplikace](http://msdn.microsoft.com/library/windows/apps/xaml/mt238321.aspx) použít nejnovější univerzální platformu Windows.  
  
 Po vytvoření aplikace pro Universal Windows, je nutné [zabalení aplikace](https://msdn.microsoft.com/library/windows/apps/hh454036.aspx) ho nainstalovat na zařízení s Windows 10 nebo odeslání do Windows Store.

