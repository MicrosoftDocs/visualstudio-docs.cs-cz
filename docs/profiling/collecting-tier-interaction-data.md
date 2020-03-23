---
title: Shromažďování údajů o interakci s úrovní | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.property.tierinteraction
helpviewer_keywords:
- Profiling Tools,ADO.NET profiling
- tier interaction profiling method
- Profiling Tools,tier-interaction method
- ADO.NET performance profiling
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: e01259fdd23e60a1408addc10a6af3a12479c9f2
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74772815"
---
# <a name="collect-tier-interaction-data"></a>Shromažďování dat interakce vrstev

Profilování interakce vrstvy poskytuje další informace o době provádění funkcí vícevrstvých aplikací, které komunikují s databázemi prostřednictvím ADO.NET služeb. Data jsou shromažďována pouze pro synchronní volání funkcí.

**Edice Visual Studia**

Data profilování interakce úrovně lze shromažďovat pomocí libovolné edice sady Visual Studio. Data profilování interakce vrstvy však lze zobrazit pouze v sadě Visual Studio Enterprise.

**Windows 8 a Windows Server 2012**

Chcete-li shromažďovat data interakce vrstvy v aplikacích pro stolní počítače pro Windows 8 a v aplikacích pro Windows Server 2012, musíte použít metodu instrumentace. Pro aplikace UPW nelze shromažďovat data interakce vrstvy. Viz [Nástroje pro výkon v aplikacích pro Windows 8 a Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md). Data interakce vrstvy můžete zahrnout do všech metod profilování v jiné podporované verzi systému Windows.

**Průvodce výkonu**

Z důvodu chyby v Průvodci výkonem je nutné přidat možnost shromažďování dat interakce vrstvy do profilování z Průzkumníka výkonu. Je také nutné přidat projekt, spustitelný soubor nebo web do cílového uzlu Průzkumníka výkonu.

## <a name="to-add-tier-interaction-data-to-a-profiling-run-by-using-the-performance-session-property-pages"></a>Přidání dat interakce vrstvy do profilování spustit pomocí stránek vlastností relace výkonu

1. V Průzkumníku výkonu zvolte **Vlastnosti** z kontextové nabídky.

2. Vyberte **stránku Interakce vrstvy** a zaškrtněte políčko **Povolit profilování interakce vrstvy.**

3. V Průzkumníku výkonu vyberte uzel **Cíle** a zadejte projekt, spustitelný soubor nebo web, který chcete profilovat.

## <a name="see-also"></a>Viz také

[Zobrazení interakce úrovně](../profiling/tier-interactions-view.md)
