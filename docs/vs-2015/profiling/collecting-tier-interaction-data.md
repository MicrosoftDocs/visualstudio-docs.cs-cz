---
title: Shromažďování dat interakce vrstev | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.performance.property.tierinteraction
helpviewer_keywords:
- Profiling Tools,ADO.NET profiling
- tier interaction profiling method
- Profiling Tools,tier-interaction method
- ADO.NET performance profiling
ms.assetid: 47a944c2-3098-497c-8fc7-e1f43d750bbc
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 31e2d46992b48b987966bac7d7dc68787f4016c2
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51761180"
---
# <a name="collecting-tier-interaction-data"></a>Shromažďování dat interakce vrstev
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Profilování interakce vrstev poskytuje další informace o spuštění s úspěšností funkce víceúrovňových aplikací, které komunikují s databázemi prostřednictvím služeb ADO.NET. Data se shromažďují pouze pro synchronní volání.  
  
 **Edice sady Visual Studio**  
  
 Dat profilace interakce vrstev lze shromažďovat pomocí Visual Studio Ultimate, Visual Studio Premium nebo Visual Studio Professional. Nicméně data profilace interakce vrstev lze zobrazit pouze ve VS Ultimate a VS Premium.  
  
 **Windows 8 a Windows Server 2012**  
  
 Ke shromažďování dat interakce vrstev v aplikacích klasické pracovní plochy systému Windows 8 a Windows Server 2012 aplikace, musíte použít metody instrumentace. Nelze shromažďování dat interakce vrstev pro aplikace Windows Store. Zobrazit [nástroje pro výkon v aplikacích Windows 8 a Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md). Dat interakce vrstev můžete zahrnout všechny metody profilování na ostatní podporované verze systému Windows.  
  
 **Průvodce výkonu**  
  
 Z důvodu chyby v Průvodci výkonu je nutné přidat možnost kolekce dat interakce vrstvy do běhu profilování z prohlížeče výkonu. Musíte také přidat projekt, spustitelný soubor nebo web na cílový uzel prohlížeč výkonu.  
  
### <a name="to-add-tier-interaction-data-to-a-profiling-run-by-using-the-performance-session-property-pages"></a>Přidání dat interakce vrstev pro profilování pomocí stránky vlastností relace výkonu  
  
1.  V Průzkumníku výkonu, zvolte **vlastnosti** v místní nabídce.  
  
2.  Vyberte **interakce vrstev** stránce a potom zkontrolujte **povolit profilaci interakce vrstev** zaškrtávací políčko.  
  
3.  V prohlížeči výkonu, vyberte **cíle** uzel a pak zadejte projekt, spustitelný soubor nebo web, který chcete Profilovat.  
  
## <a name="see-also"></a>Viz také  
 [Zobrazení interakcí vrstev](../profiling/tier-interactions-view.md)



