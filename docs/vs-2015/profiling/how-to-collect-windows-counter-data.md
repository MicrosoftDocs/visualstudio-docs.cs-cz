---
title: 'Postupy: shromažďování dat čítače Windows | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.property.syscounter
- vs.performance.property.wincounter
helpviewer_keywords:
- windows counters
- performance tools, using windows counters
- profiling tools, using windows counters
ms.assetid: db4fbac2-bea5-4558-aa8b-160fcccf4b33
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9743fa7defbbf3321636d2ba4799454713a647db
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "64836778"
---
# <a name="how-to-collect-windows-counter-data"></a>Postupy: Shromažďování dat čítačů Windows
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Čítače systému Windows jsou čítače výkonu systému, které lze shromažďovat v nastavených intervalech během profilace. V zobrazení značek Nástroje pro profilaci sestavy je řádek pro každý interval kolekce označen jako automatického **označení** . Řádek obsahuje sloupce, které popisují hodnoty čítače výkonu v tomto intervalu. Chcete-li omezit analýzu na určitou dobu mezi dvěma konkrétními značkami, vyberte značky, klikněte pravým tlačítkem myši a vyberte možnost **filtrovat podle**  ->   **značky** z místní nabídky.  
  
 **Požadavky**  
  
- [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
> [!NOTE]
> Rozšířené funkce zabezpečení ve Windows 8 a Windows Serveru 2012 vyžadují významné změny ve způsobu, jakým Profiler sady Visual Studio shromažďuje data na těchto platformách. Aplikace pro Windows Store vyžadují také nové techniky shromažďování. Podívejte [se na nástroje pro sledování výkonu v aplikacích pro Windows 8 a Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
### <a name="to-collect-windows-counter-data"></a>Shromažďování dat čítače Windows  
  
1. V Prohlížeč výkonu klikněte pravým tlačítkem na relaci, pro kterou chcete nakonfigurovat čítače Windows, a vyberte **vlastnosti**.  
  
2. Na **stránkách vlastností**klikněte na **čítače systému Windows**.  
  
3. Zaškrtněte políčko **shromáždit čítače systému Windows** .  
  
4. Do textového pole **interval shromažďování (MS)** zadejte časový interval.  
  
5. V rozevíracím seznamu **kategorie čítače** vyberte kategorii.  
  
6. V rozevíracím seznamu **instance** vyberte instanci.  
  
7. Vyberte čítače, které chcete použít při profilování aplikace.  
  
8. Klikněte na **použít.**  
  
## <a name="see-also"></a>Viz také  
 [Konfigurace relací výkonu](../profiling/configuring-performance-sessions.md)   
 [Vlastnosti výkonnostní relace](../profiling/performance-session-properties.md)   
 [Čítače procesoru a systému Windows](../profiling/cpu-and-windows-counters.md)
