---
title: Shromažďovat data trasování událostí pro Windows (ETW) | Microsoft Docs
description: Naučte se používat trasování událostí pro Windows (ETW) k určení, kde dochází k problémům s výkonem v aplikaci. Data se zobrazují pomocí VSPerfReport.exe.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.performance.property.events
helpviewer_keywords:
- event trace providers, performance tools
- profiling tools, event trace providers
- performance tools, enabling event trace providers
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 77ddd22450786091c5240f26213633a7935c03dd
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99886285"
---
# <a name="how-to-collect-event-tracing-for-windows-etw-data"></a>Postupy: shromažďování dat trasování událostí pro Windows (ETW)

Trasování událostí pro Windows (ETW) je výkonné zařízení pro trasování na úrovni jádra, které umožňuje události v jádru protokolu profileru nebo aplikace definované aplikací. Data shromážděná od zprostředkovatele událostí lze zobrazit pouze pomocí možnosti/**summary: ETW** nástroje příkazového řádku [VSPerfReport](../profiling/vsperfreport.md) . Pomocí této sestavy můžete určit, kde dochází k problémům s výkonem v aplikaci.

> [!NOTE]
> Rozšířené funkce zabezpečení ve Windows 8 a Windows Serveru 2012 vyžadují významné změny ve způsobu, jakým Profiler sady Visual Studio shromažďuje data na těchto platformách. Aplikace pro UWP také vyžadují nové techniky shromažďování. Podívejte [se na nástroje pro sledování výkonu v aplikacích pro Windows 8 a Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

## <a name="to-enable-event-trace-providers"></a>Povolení zprostředkovatelů trasování událostí

1. V **prohlížeč výkonu** klikněte pravým tlačítkem na relaci výkonu a pak klikněte na **vlastnosti**.

2. Na **stránkách vlastností** klikněte na vlastnosti **událostí systému Windows** .

3. V seznamu **Vyberte poskytovatele trasování událostí pro shromáždění dat** vyberte poskytovatele událostí, které chcete použít k profilování aplikace.

## <a name="see-also"></a>Viz také

[Konfigurace výkonnostních relací](../profiling/configuring-performance-sessions.md)
