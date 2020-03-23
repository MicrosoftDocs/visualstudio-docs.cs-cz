---
title: 'Postup: Shromažďování dat sledování událostí pro windows (ETW) | Dokumenty společnosti Microsoft'
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779022"
---
# <a name="how-to-collect-event-tracing-for-windows-etw-data"></a>Postup: Shromažďování dat sledování událostí pro Windows (ETW)

Trasování událostí pro Windows (ETW) je efektivní zařízení pro trasování na úrovni jádra, které umožňuje jádro protokolu profileru nebo události definované aplikací. Data, která jsou shromažďována od poskytovatele událostí lze zobrazit pouze pomocí /**Summary:ETW** možnost nástroje příkazového řádku [VSPerfReport.](../profiling/vsperfreport.md) Tuto sestavu můžete použít k určení, kde dochází k problémům s výkonem v aplikaci.

> [!NOTE]
> Rozšířené funkce zabezpečení v systémech Windows 8 a Windows Server 2012 vyžadovaly významné změny ve způsobu, jakým profiler sady Visual Studio shromažďuje data na těchto platformách. Aplikace UPW také vyžadují nové techniky kolekce. Viz [Nástroje pro výkon v aplikacích pro Windows 8 a Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

## <a name="to-enable-event-trace-providers"></a>Povolení zprostředkovatelů trasování událostí

1. V **Průzkumníku výkonu**klepněte pravým tlačítkem myši na relaci výkonu a potom klepněte na příkaz **Vlastnosti**.

2. Na **stránkách vlastností**klepněte na vlastnosti **Událostí systému Windows.**

3. V **seznamu Vybrat zprostředkovatele trasování událostí pro shromažďování dat ze** seznamu vyberte zprostředkovatele událostí, které chcete použít k profilování aplikace.

## <a name="see-also"></a>Viz také

[Konfigurace výkonnostních relací](../profiling/configuring-performance-sessions.md)
