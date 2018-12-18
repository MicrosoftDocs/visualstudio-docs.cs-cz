---
title: 'Postupy: shromažďování dat čítačů Windows | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.property.syscounter
- vs.performance.property.wincounter
helpviewer_keywords:
- windows counters
- performance tools, using windows counters
- profiling tools, using windows counters
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4ea074024e605d2dcc91500fb00fe0d7b6781692
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "35676059"
---
# <a name="how-to-collect-windows-counter-data"></a>Postupy: shromažďování dat čítačů Windows

Čítače Windows jsou systémové čítače výkonu, které mohou být shromážděných během profilace v nastavených intervalech. V zobrazení sestav nástrojů pro profilaci sady značek je označen řádek **AutoMark** pro každý interval shromažďování. Tento řádek obsahuje sloupce, které popisují hodnoty čítače výkonu v tomto intervalu. Chcete-li omezit analýzu na určitou dobu mezi dvěma konkrétními značkami, vyberte značky, klikněte pravým tlačítkem a pak vyberte **filtrovat podle** > **značky** z místní nabídky.

> [!NOTE]
> Rozšířené funkce zabezpečení v systému Windows 8 a Windows Server 2012 vyžadují významné změny ve způsobu, jakým profiler systému Visual Studio na těchto platformách shromažďuje data. U aplikací pro UPW také vyžadují nové techniky kolekce. Zobrazit [nástroje pro výkon v aplikacích Windows 8 a Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

## <a name="to-collect-windows-counter-data"></a>Ke shromažďování dat čítačů Windows

1. V prohlížeči výkonu, klikněte pravým tlačítkem na relaci, pro kterou chcete konfigurovat čítače Windows a vyberte **vlastnosti**.

2. V **stránky vlastností**, klikněte na tlačítko **čítače Windows**.

3. Vyberte **shromáždit čítače Windows** zaškrtávací políčko.

4. V **intervalem sběru hodnot (MS)** textové pole, zadejte časový interval.

5. Vybrat kategorii z **kategorie čítače** rozevíracího seznamu.

6. Vyberte instanci, ze **Instance** rozevíracího seznamu.

7. Vyberte čítače, které chcete použít při profilování aplikace.

8. Klikněte na tlačítko **použít.**

## <a name="see-also"></a>Viz také:

[Konfigurace výkonnostních relací](../profiling/configuring-performance-sessions.md)  
[Vlastnosti výkonnostní relace](../profiling/performance-session-properties.md)  
[Čítače procesoru a systému Windows](../profiling/cpu-and-windows-counters.md)