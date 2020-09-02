---
title: Visual Studio a Xamarin | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: tgt-pltfrm-cross-plat
ms.topic: conceptual
ms.assetid: 1da4064f-af69-472c-8f31-98484be5f790
caps.latest.revision: 14
ms.author: crdun
manager: crdun
ms.openlocfilehash: 098d94a1aed9020271db5010e278a4aa8fc68330
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "64828374"
---
# <a name="visual-studio-and-xamarin"></a>Visual Studio a Xamarin
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Xamarin je platforma pro vývoj mobilních aplikací pro vytváření nativních aplikací pro iOS, Android a Windows ze společného základu kódu v jazyce C#/.NET, což dosahuje 75% pro téměř 100% opětovného využití kódu mezi platformami. Aplikace napsané v prostředích Xamarin a C# mají úplný přístup k základním rozhraním API platformy a možnost vytvářet nativní uživatelská rozhraní a kompilovat na balíčky specifické pro platformu, takže má malý dopad na výkon modulu runtime. (Poznámka: Xamarin také podporuje F #, ale tato dokumentace se soustředí jenom na C#. Visual Basic se v tuto chvíli nepodporuje.)  
  
 Lepší je, že vývojáři, kteří znají C#, .NET a Visual Studio, budou mít při práci se službou Xamarin pro mobilní aplikace stejný výkon a produktivitu, včetně vzdáleného ladění na zařízeních s Androidem, iOS a Windows, aniž by se museli učit jazyky nativního kódování, jako je například cíl-C nebo Java. Je to málo neočekávaně, takže mnoho vysoce výkonných aplikací s působivými uživatelskými rozhraními, jako jsou NASCAR, Aviva a MixRadio, se vytvořilo pomocí Xamarin.  
  
 Tato dokumentace vám pomůže vyhodnotit všechny možnosti sady **Visual Studio pomocí Xamarin** pro sestavování těchto prostředí.  
  
- Začněte s [instalačním programem a nainstalujte](../cross-platform/setup-and-install.md), což je proces, který nějakou dobu trvá (obvykle 2-4 hodin v závislosti na rychlosti připojení k Internetu, co jste už nainstalovali a vybrané možnosti).  
  
- I když jsou instalační programy spuštěné, můžete [se seznámit s vývojem pro mobilní zařízení pomocí Xamarin](../cross-platform/learn-about-mobile-development-with-xamarin.md) , který vám bude informovat o povaze Xamarin, porovnání Xamarin. Forms až k NATIVNÍmu uživatelskému rozhraní a další.  
  
- Po dokončení instalace [Ověřte své prostředí Xamarin](../cross-platform/verify-your-xamarin-environment.md).  
  
- Projděte si kurz a [Naučte se základy vytváření aplikací pomocí Xamarin. Forms v aplikaci Visual Studio](../cross-platform/learn-app-building-basics-with-xamarin-forms-in-visual-studio.md).  
  
  Můžete pracovat se všemi funkcemi Xamarin prostřednictvím [libovolné edice sady Visual Studio 2015](https://www.visualstudio.com/vs-2015-product-editions) (Community, Professional a Enterprise). Poznámka: od března 31 2016 je Xamarin součástí všech edic sady Visual Studio 2015 a již nevyžaduje samostatnou licenci. Pro Visual Studio 2013 můžete Xamarin nainstalovat samostatně, jak popisuje téma [instalace a instalace](../cross-platform/setup-and-install.md) .  
  
> [!NOTE]
> Tyto pokyny popisují nejjednodušší a nejpřímější konfiguraci počítače pro ty, které mají pozadí Windows a Visual Studio. V této konfiguraci je celkové vývojové prostředí zjednodušené, protože k používání simulátoru iOS a připojeného zařízení potřebujete pracovat jenom s počítačem Mac. Pokud místo toho přejdete na pozadí Mac, doporučujeme, abyste spustili aplikaci Visual Studio v paralelním prostředí/VMWare nebo pomocí Xamarin Studio komunity. Pokyny najdete v tématu [instalace, instalace a ověření pro uživatele Mac](../cross-platform/setup-install-and-verifications-for-mac-users.md) .  
  
> [!NOTE]
> Pokud hledáte vývojové řešení pro různé platformy na základě HTML a CSS, Projděte si Visual Studio Tools pro Apache Cordova, jak je popsáno v tématu [vývoj pro různé platformy v aplikaci Visual Studio](../cross-platform/cross-platform-mobile-development-in-visual-studio.md#HTML).
