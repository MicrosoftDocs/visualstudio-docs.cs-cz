---
title: Shromažďují se data interakce vrstev | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
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
manager: jillfra
ms.openlocfilehash: a20266c870316be9b6be67e661d13eb4e6fdbaee
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "62568044"
---
# <a name="collecting-tier-interaction-data"></a>Shromažďování dat interakce vrstev
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Profilace interakce vrstev poskytuje další informace o době spuštění funkcí vícevrstvých aplikací, které komunikují s databázemi prostřednictvím služby ADO.NET Services. Data jsou shromažďována pouze pro volání synchronních funkcí.  
  
 **Edice sady Visual Studio**  
  
 Data profilování interakce vrstev je možné shromažďovat pomocí Visual Studio Ultimate, Visual Studio Premium nebo Visual Studio Professional. Data profilování interakce vrstev ale můžete zobrazit jenom v sadě VS Ultimate a VS Premium.  
  
 **Windows 8 a Windows Server 2012**  
  
 K shromažďování dat interakce vrstev v aplikacích pro stolní počítače se systémem Windows 8 a Windows Server 2012 je nutné použít metodu instrumentace. Nemůžete shromažďovat data interakce vrstev pro aplikace pro Windows Store. Podívejte [se na nástroje pro sledování výkonu v aplikacích pro Windows 8 a Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md). Data interakce vrstev můžete zahrnout do všech metod profilování v jiné podporované verzi systému Windows.  
  
 **Průvodce výkonu**  
  
 Z důvodu chyby v průvodci výkonem je nutné přidat možnost shromažďování dat interakce vrstev ke spuštění profilace z Prohlížeč výkonu. Také je nutné přidat projekt, spustitelný soubor nebo web do cílového uzlu Prohlížeč výkonu.  
  
### <a name="to-add-tier-interaction-data-to-a-profiling-run-by-using-the-performance-session-property-pages"></a>Přidání dat interakce vrstev do profilace spouštěné pomocí stránek vlastností relace výkonu  
  
1. V Prohlížeč výkonu v místní nabídce vyberte možnost **vlastnosti** .  
  
2. Vyberte stránku **interakce vrstev** a zaškrtněte políčko **Povolit profilaci interakce vrstev** .  
  
3. V Prohlížeč výkonu vyberte uzel **cíle** a pak určete projekt, spustitelný soubor nebo web, který chcete profilovat.  
  
## <a name="see-also"></a>Viz také  
 [Zobrazení interakcí vrstev](../profiling/tier-interactions-view.md)
