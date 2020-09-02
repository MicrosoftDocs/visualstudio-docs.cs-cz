---
title: 'Postupy: profilování kódu JavaScriptu na webových stránkách | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- JavaScript performance profiling
- Profiling Tools,JavaScript
- web site performance profiling
ms.assetid: 37d02aad-ca4d-4eb0-bf66-ca3ecef31fbe
caps.latest.revision: 32
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: aa504e961ed8e592f5e3df84ff7a688fa2398200
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "65688143"
---
# <a name="how-to-profile-javascript-code-in-web-pages"></a>Postupy: Profilace kódu JavaScript ve webových stránkách
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Nástroje pro profilaci může shromažďovat údaje o výkonu pro kód JavaScriptu, který se spouští v rámci [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] webové aplikace, libovolné webové stránky nebo aplikace JavaScriptu pomocí metody profilace instrumentace.  
  
 **Požadavky**  
  
- [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
- Internet Explorer 8 nebo novější.  
  
> [!WARNING]
> Chcete-li profilovat jazyk JavaScript v aplikacích pro Windows Store, přečtěte si jedno z následujících témat:  
> 
> - Časování funkcí jazyka JavaScript [funkce](https://msdn.microsoft.com/library/b2bf49fc-aea7-4d9c-8fcf-cff8b8dd0c03) [JavaScriptu na vzdáleném zařízení](https://msdn.microsoft.com/library/d78812b6-a97e-46dc-8d99-e724d1d725d8)  
>   - [Analýza dat časování funkcí JavaScriptu](https://msdn.microsoft.com/library/b5aea8d8-36df-47ba-a7ca-95406700ca9b)  
>   - 
  
 Můžete použít Průvodce profilací k vytvoření výkonnostní relace. Zadejte metodu instrumentace a pak určete možnost profilace JavaScriptu na stránce instrumentace v dialogovém okně Vlastnosti pro relaci výkonu.  
  
 Když zadáte profilaci JavaScriptu, kód JavaScriptu, který se spustí v prohlížeči, a [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] kód, který se spouští na serveru, se profiluje.  
  
- V případě [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] webové aplikace se profiluje kód JavaScriptu, který se spouští v prohlížeči, a [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] kód, který se spouští na serveru.  
  
- V případě libovolné webové stránky je kód JavaScriptu, který se spouští v prohlížeči, profilace.  
  
### <a name="to-profile-javascript-in-an-aspnet-web-application-project"></a>Profilace JavaScriptu v projektu webové aplikace ASP.NET  
  
1. V aplikaci [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)] otevřete [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] webový projekt.  
  
2. V nabídce **analyzovat** klikněte na možnost **Spustit Průvodce výkonem**.  
  
3. Na první stránce Průvodce výkonem zadejte metodu profilace **instrumentace** a potom klikněte na tlačítko **Další**.  
  
4. Na druhé stránce průvodce se ujistěte, že je v seznamu cílů vybraný aktuální projekt, a pak klikněte na **Další.**  
  
5. Na třetí stránce průvodce vyberte zaškrtávací políčko **profil JavaScript** a pak klikněte na **Další**.  
  
6. Na čtvrté stránce průvodce kliknutím na tlačítko **Dokončit** spusťte webovou aplikaci v prohlížeči.  
  
7. Využijte funkci, kterou chcete profilovat.  
  
8. Chcete-li ukončit relaci profilování, zavřete prohlížeč.  
  
### <a name="to-profile-javascript-in-individual-web-pages-or-a-javascript-applications"></a>Profilace JavaScriptu na jednotlivých webových stránkách nebo v aplikacích JavaScriptu  
  
1. Otevřete [!INCLUDE[vsPreShort](../includes/vspreshort-md.md)].  
  
2. V nabídce **analyzovat** klikněte na možnost **Spustit Průvodce výkonem**.  
  
3. Na první stránce Průvodce výkonem zadejte metodu profilace **instrumentace** a potom klikněte na tlačítko **Další**.  
  
4. Na druhé stránce průvodce klikněte na aplikaci ASP.NET nebo JavaScript a potom klikněte na tlačítko **Další.**  
  
5. Na třetí stránce průvodce:  
  
    1. Zadejte adresu URL stránky v poli **Jaká adresa URL nebo cesta spustí vaši aplikaci** .  
  
    2. Zaškrtněte políčko **profil JavaScript** a potom klikněte na tlačítko **Další**.  
  
6. Na čtvrté stránce průvodce kliknutím na tlačítko **Dokončit** otevřete webovou stránku v prohlížeči.  
  
7. Využijte funkci, kterou chcete profilovat.  
  
8. Chcete-li ukončit relaci profilování, zavřete prohlížeč.
