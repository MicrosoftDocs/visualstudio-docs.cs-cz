---
title: Shromažďují se data interakce vrstev | Microsoft Docs
description: Naučte se shromažďovat informace o profilování vrstev pro vícevrstvé aplikace, které komunikují s databázemi prostřednictvím služeb ADO.NET Services.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
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
ms.openlocfilehash: 768cb173bca578c440e3209fe7b7a1df60fab1be
ms.sourcegitcommit: 7a5c4f60667b5792f876953d55192b49a73f5fe9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/16/2021
ms.locfileid: "98533677"
---
# <a name="collect-tier-interaction-data"></a>Shromažďování dat interakce vrstev

Profilace interakce vrstev poskytuje další informace o době spuštění funkcí vícevrstvých aplikací, které komunikují s databázemi prostřednictvím služby ADO.NET Services. Data jsou shromažďována pouze pro volání synchronních funkcí.

**Edice sady Visual Studio**

Data profilování interakce vrstev je možné shromažďovat pomocí libovolné edice sady Visual Studio. Data profilování interakce vrstev ale můžete zobrazit jenom v Visual Studio Enterprise.

**Windows 8 a Windows Server 2012**

K shromažďování dat interakce vrstev v aplikacích pro stolní počítače se systémem Windows 8 a Windows Server 2012 je nutné použít metodu instrumentace. Nemůžete shromažďovat data interakce vrstev pro aplikace pro UWP. Podívejte [se na nástroje pro sledování výkonu v aplikacích pro Windows 8 a Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md). Data interakce vrstev můžete zahrnout do všech metod profilování v jiné podporované verzi systému Windows.

**Průvodce výkonu**

Z důvodu chyby v průvodci výkonem je nutné přidat možnost shromažďování dat interakce vrstev ke spuštění profilace z Prohlížeč výkonu. Také je nutné přidat projekt, spustitelný soubor nebo web do cílového uzlu Prohlížeč výkonu.

## <a name="to-add-tier-interaction-data-to-a-profiling-run-by-using-the-performance-session-property-pages"></a>Přidání dat interakce vrstev do profilace spouštěné pomocí stránek vlastností relace výkonu

1. V Prohlížeč výkonu v místní nabídce vyberte možnost **vlastnosti** .

2. Vyberte stránku **interakce vrstev** a zaškrtněte políčko **Povolit profilaci interakce vrstev** .

3. V Prohlížeč výkonu vyberte uzel **cíle** a pak určete projekt, spustitelný soubor nebo web, který chcete profilovat.

## <a name="see-also"></a>Viz také:

[Zobrazení interakcí vrstev](../profiling/tier-interactions-view.md)
