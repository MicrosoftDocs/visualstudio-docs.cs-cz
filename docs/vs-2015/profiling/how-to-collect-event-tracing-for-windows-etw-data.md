---
title: 'Postupy: shromažďování dat trasování událostí pro Windows (ETW) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.property.events
helpviewer_keywords:
- event trace providers, performance tools
- profiling tools, event trace providers
- performance tools, enabling event trace providers
ms.assetid: aa2261fe-d5f5-49fc-a171-d18842e1dc7d
caps.latest.revision: 31
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9d113a32622c40c68a030fdbc670ec19c6038de2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "64810203"
---
# <a name="how-to-collect-event-tracing-for-windows-etw-data"></a>Postupy: Shromažďování dat Trasování událostí pro Windows
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Trasování událostí pro Windows (ETW) je výkonné zařízení pro trasování na úrovni jádra, které umožňuje události v jádru protokolu profileru nebo aplikace definované aplikací. Data shromážděná od zprostředkovatele událostí lze zobrazit pouze pomocí možnosti/**summary: ETW** nástroje příkazového řádku [VSPerfReport](../profiling/vsperfreport.md) . Pomocí této sestavy můžete určit, kde dochází k problémům s výkonem v aplikaci.  
  
 **Požadavky**  
  
- [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
> [!NOTE]
> Rozšířené funkce zabezpečení ve Windows 8 a Windows Serveru 2012 vyžadují významné změny ve způsobu, jakým Profiler sady Visual Studio shromažďuje data na těchto platformách. Aplikace pro Windows Store vyžadují také nové techniky shromažďování. Podívejte [se na nástroje pro sledování výkonu v aplikacích pro Windows 8 a Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
### <a name="to-enable-event-trace-providers"></a>Povolení zprostředkovatelů trasování událostí  
  
1. V **prohlížeč výkonu**klikněte pravým tlačítkem na relaci výkonu a pak klikněte na **vlastnosti**.  
  
2. Na **stránkách vlastností**klikněte na vlastnosti **událostí systému Windows** .  
  
3. V seznamu **Vyberte poskytovatele trasování událostí pro shromáždění dat** vyberte poskytovatele událostí, které chcete použít k profilování aplikace.  
  
## <a name="see-also"></a>Viz také  
 [Konfigurace výkonnostních relací](../profiling/configuring-performance-sessions.md)
