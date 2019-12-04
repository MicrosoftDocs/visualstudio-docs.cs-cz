---
title: 'Postupy: shromažďování dat trasování událostí pro Windows (ETW) | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.property.events
helpviewer_keywords:
- event trace providers, performance tools
- profiling tools, event trace providers
- performance tools, enabling event trace providers
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 2fa0547682351d1a7ba4efe4ce3b4350b906462c
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74779022"
---
# <a name="how-to-collect-event-tracing-for-windows-etw-data"></a>Postupy: shromažďování dat trasování událostí pro Windows (ETW)

Trasování událostí pro Windows (ETW) je výkonné zařízení pro trasování na úrovni jádra, které umožňuje události v jádru protokolu profileru nebo aplikace definované aplikací. Data shromážděná od zprostředkovatele událostí lze zobrazit pouze pomocí možnosti/**summary: ETW** nástroje příkazového řádku [VSPerfReport](../profiling/vsperfreport.md) . Pomocí této sestavy můžete určit, kde dochází k problémům s výkonem v aplikaci.

> [!NOTE]
> Rozšířené funkce zabezpečení ve Windows 8 a Windows Serveru 2012 vyžadují významné změny ve způsobu, jakým Profiler sady Visual Studio shromažďuje data na těchto platformách. Aplikace pro UWP také vyžadují nové techniky shromažďování. Podívejte [se na nástroje pro sledování výkonu v aplikacích pro Windows 8 a Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

## <a name="to-enable-event-trace-providers"></a>Povolení zprostředkovatelů trasování událostí

1. V **prohlížeč výkonu**klikněte pravým tlačítkem na relaci výkonu a pak klikněte na **vlastnosti**.

2. Na **stránkách vlastností**klikněte na vlastnosti **událostí systému Windows** .

3. V seznamu **Vyberte poskytovatele trasování událostí pro shromáždění dat** vyberte poskytovatele událostí, které chcete použít k profilování aplikace.

## <a name="see-also"></a>Viz také:

[Konfigurace výkonnostních relací](../profiling/configuring-performance-sessions.md)
