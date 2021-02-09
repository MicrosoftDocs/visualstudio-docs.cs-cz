---
title: Shromáždit data čítače Windows | Microsoft Docs
description: Čítače systému Windows se používají při profilaci instrumentace. Naučte se shromažďovat data čítače Windows a omezovat analýzu do jednoho intervalu shromažďování.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.performance.property.syscounter
- vs.performance.property.wincounter
helpviewer_keywords:
- windows counters
- performance tools, using windows counters
- profiling tools, using windows counters
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: b3f1e8f38ee9cb63dfe5a79f0b410e957b4cefaf
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99886207"
---
# <a name="how-to-collect-windows-counter-data"></a>Postupy: shromažďování dat čítače Windows

Čítače systému Windows jsou čítače výkonu systému, které lze shromažďovat v nastavených intervalech během profilace. V zobrazení značek Nástroje pro profilaci sestavy je řádek pro každý interval kolekce označen jako automatického **označení** . Řádek obsahuje sloupce, které popisují hodnoty čítače výkonu v tomto intervalu. Chcete-li omezit analýzu na určitou dobu mezi dvěma konkrétními značkami, vyberte značky, klikněte pravým tlačítkem myši a vyberte možnost **filtrovat podle**  >  **značky** z místní nabídky.

> [!NOTE]
> Rozšířené funkce zabezpečení ve Windows 8 a Windows Serveru 2012 vyžadují významné změny ve způsobu, jakým Profiler sady Visual Studio shromažďuje data na těchto platformách. Aplikace pro UWP také vyžadují nové techniky shromažďování. Podívejte [se na nástroje pro sledování výkonu v aplikacích pro Windows 8 a Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

## <a name="to-collect-windows-counter-data"></a>Shromažďování dat čítače Windows

1. V Prohlížeč výkonu klikněte pravým tlačítkem na relaci, pro kterou chcete nakonfigurovat čítače Windows, a vyberte **vlastnosti**.

2. Na **stránkách vlastností** klikněte na **čítače systému Windows**.

3. Zaškrtněte políčko **shromáždit čítače systému Windows** .

4. Do textového pole **interval shromažďování (MS)** zadejte časový interval.

5. V rozevíracím seznamu **kategorie čítače** vyberte kategorii.

6. V rozevíracím seznamu **instance** vyberte instanci.

7. Vyberte čítače, které chcete použít při profilování aplikace.

8. Klikněte na **použít.**

## <a name="see-also"></a>Viz také

[Konfigurace relací výkonu](../profiling/configuring-performance-sessions.md) 
 [Vlastnosti](../profiling/performance-session-properties.md) 
 výkonnostní relace [Čítače procesoru a systému Windows](../profiling/cpu-and-windows-counters.md)
