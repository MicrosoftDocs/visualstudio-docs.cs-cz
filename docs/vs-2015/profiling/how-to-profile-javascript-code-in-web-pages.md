---
title: 'Postupy: profilování kódu JavaScript ve webových stránkách | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- JavaScript performance profiling
- Profiling Tools,JavaScript
- web site performance profiling
ms.assetid: 37d02aad-ca4d-4eb0-bf66-ca3ecef31fbe
caps.latest.revision: 32
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8f9def923e0cc012a37c02d24b67e807668ae976
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51792109"
---
# <a name="how-to-profile-javascript-code-in-web-pages"></a>Postupy: profilování kódu JavaScript ve webových stránkách
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Nástroje pro profilaci můžete shromažďovat údaje o výkonu pro kód jazyka JavaScript, který se spustí v [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] webové aplikace, libovolný webové stránky nebo aplikace JavaScript s využitím metoda profilace instrumentace.  
  
 **Požadavky**  
  
-   [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
-   Internet Explorer 8 nebo novější.  
  
> [!WARNING]
>  Chcete-li Profilovat jazyk JavaScript v aplikacích pro Windows Store, naleznete v následujících tématech:  
> 
> - [Časování funkcí jazyka JavaScript](http://msdn.microsoft.com/library/b2bf49fc-aea7-4d9c-8fcf-cff8b8dd0c03) [časování funkcí jazyka JavaScript na vzdáleném zařízení](http://msdn.microsoft.com/library/d78812b6-a97e-46dc-8d99-e724d1d725d8)  
>   -   [Analýza dat časování funkcí jazyka JavaScript](http://msdn.microsoft.com/library/b5aea8d8-36df-47ba-a7ca-95406700ca9b)  
>   -  
  
 Průvodce Profilováním můžete použít k vytvoření relace výkonu. Určete metody instrumentace a potom určete možnost na stránce instrumentace dialogové okno Vlastnosti relace výkonu profilace jazyka JavaScript.  
  
 Když zadáte profilace JavaScriptu, kód jazyka JavaScript, který se spustí v prohlížeči a [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] kód, který se spustí na serveru jsou profilovány.  
  
-   Pro [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] webovou aplikaci, jak kód jazyka JavaScript, který se spustí v prohlížeči a [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] kód, který se spustí na serveru jsou profilovány.  
  
-   Pro libovolnou webovou stránku je profilována kód jazyka JavaScript, který se spustí v prohlížeči.  
  
### <a name="to-profile-javascript-in-an-aspnet-web-application-project"></a>Chcete-li Profilovat jazyk JavaScript v projektu aplikace ASP.NET  
  
1.  V [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], otevřete [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] webový projekt.  
  
2.  Na **analyzovat** nabídky, klikněte na tlačítko **spustit Průvodce výkonem**.  
  
3.  Na první stránce Průvodce výkonem, zadejte **instrumentace** metoda profilace a potom klikněte na **Další**.  
  
4.  Na druhé stránce průvodce, ujistěte se, že je aktuální projekt vybraný v seznamu cílů a potom klikněte na tlačítko **Další.**  
  
5.  Na třetí stránce průvodce vyberte **Profilovat jazyk JavaScript** zaškrtněte políčko a potom klikněte na tlačítko **Další**.  
  
6.  Na čtvrté stránce průvodce, klikněte na tlačítko **Dokončit** spusťte webovou aplikaci v prohlížeči.  
  
7.  Vykonává funkce, které chcete profil.  
  
8.  Chcete-li ukončit relaci profilování, ukončete prohlížeč.  
  
### <a name="to-profile-javascript-in-individual-web-pages-or-a-javascript-applications"></a>Chcete-li Profilovat jazyk JavaScript v jednotlivých webových stránek nebo aplikací jazyka JavaScript  
  
1.  Otevřít [!INCLUDE[vsPreShort](../includes/vspreshort-md.md)].  
  
2.  Na **analyzovat** nabídky, klikněte na tlačítko **spustit Průvodce výkonem**.  
  
3.  Na první stránce Průvodce výkonem, zadejte **instrumentace** metoda profilace a potom klikněte na **Další**.  
  
4.  Na druhé stránce průvodce, klikněte na aplikace ASP.NET nebo JavaScript a potom klikněte na tlačítko **Další.**  
  
5.  Na třetí stránce průvodce:  
  
    1.  Zadejte adresu URL stránky v **jaká adresa URL nebo cesta se spustí aplikace** pole.  
  
    2.  Vyberte **Profilovat jazyk JavaScript** zaškrtněte políčko a potom klikněte na tlačítko **Další**.  
  
6.  Na čtvrté stránce průvodce, klikněte na tlačítko **Dokončit** spuštění webové stránky v prohlížeči.  
  
7.  Vykonává funkce, které chcete profil.  
  
8.  Chcete-li ukončit relaci profilování, ukončete prohlížeč.



