---
title: 'Postup: Shromažďování dat čítače systému Windows | Dokumenty společnosti Microsoft'
ms.date: 11/04/2016
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
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: c85187fd54d61fdf40956c8aee3c0a222d95a313
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74776316"
---
# <a name="how-to-collect-windows-counter-data"></a>Postup: Shromažďování dat čítačů systému Windows

Čítače systému Windows jsou čítače výkonu systému, které lze shromažďovat v nastavených intervalech během profilování. V zobrazení Značky v sestavě Nástroje profilování je řádek označen jako **automatické značky** pro každý interval kolekce. Řádek obsahuje sloupce, které popisují hodnoty čítače výkonu v tomto intervalu. Chcete-li omezit analýzu na časové období mezi dvěma konkrétními značkami, vyberte značky, klepněte pravým tlačítkem myši a v místní nabídce vyberte možnost **Filtrovat podle** > **značek.**

> [!NOTE]
> Rozšířené funkce zabezpečení v systémech Windows 8 a Windows Server 2012 vyžadovaly významné změny ve způsobu, jakým profiler sady Visual Studio shromažďuje data na těchto platformách. Aplikace UPW také vyžadují nové techniky kolekce. Viz [Nástroje pro výkon v aplikacích pro Windows 8 a Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

## <a name="to-collect-windows-counter-data"></a>Shromažďování dat čítačů systému Windows

1. V Průzkumníku výkonu klepněte pravým tlačítkem myši na relaci, pro kterou chcete konfigurovat čítače systému Windows, a vyberte příkaz **Vlastnosti**.

2. Na **stránkách vlastností**klepněte na **položku Čítače systému Windows**.

3. Zaškrtněte políčko **Shromáždit čítače systému Windows.**

4. Do textového pole **Interval kolekce (msecs)** zadejte časový interval.

5. Vyberte kategorii z rozevíracího seznamu **Kategorie čítačů.**

6. Vyberte instanci z rozevíracího seznamu **Instance.**

7. Vyberte čítače, které chcete použít při profilování aplikace.

8. Klikněte na **Použít.**

## <a name="see-also"></a>Viz také

[Konfigurace výkonových relací](../profiling/configuring-performance-sessions.md)
[Vlastnosti výkonu](../profiling/performance-session-properties.md)
[Čítače procesoru a Windows](../profiling/cpu-and-windows-counters.md)
