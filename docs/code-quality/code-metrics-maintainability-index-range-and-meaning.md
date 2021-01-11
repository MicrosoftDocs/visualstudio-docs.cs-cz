---
title: Metriky kódu – rozsah indexů údržby a význam
ms.date: 1/8/2021
description: Přečtěte si o metrikě rozsahu indexu udržovatelnosti pro metriky kódu v aplikaci Visual Studio.
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 14bee6dcb522b7c1dd0475ca309b829a09c0d4ec
ms.sourcegitcommit: b1f7e7d7a0550d5c6f46adff3bddd44bc1d6ee1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/11/2021
ms.locfileid: "98069598"
---
# <a name="code-metrics---maintainability-index-range-and-meaning"></a>Metriky kódu – rozsah indexů údržby a význam

Otázka: index udržovatelnosti byl resetován tak, aby byl mezi 0 a 100. Jak a proč to bylo hotové?

Tato metrika se původně vypočítala takto: `Maintainability Index = 171 - 5.2 * ln(Halstead Volume) - 0.23 * (Cyclomatic Complexity) - 16.2 * ln(Lines of Code)`

Použití tohoto vzorce je určeno pro rozsah od 171 do neohraničeného záporného čísla.  Jako kód, který je v rozsahu 0, bylo jasně obtížné zachovat kód a rozdíl mezi kódem na 0 a nějakou zápornou hodnotou nebyl užitečný.  V důsledku snížení užitečnosti záporných čísel a přání, aby byla metrika co možná nejasná, jsme se rozhodli považovat za 0 nebo méně indexů jako 0 a pak zmenšit rozsah 171 nebo méně, než je 0 až 100. Z tohoto důvodu používáme následující vzorec:

   `Maintainability Index = MAX(0,(171 - 5.2 * ln(Halstead Volume) - 0.23 * (Cyclomatic Complexity) - 16.2 * ln(Lines of Code))*100 / 171)`

Kromě toho jsme se rozhodli mít konzervativní prahové hodnoty.  Je potřeba, aby v případě, že se index zobrazil červeně, říkáme s vysokou mírou jistoty, že došlo k potížím s kódem.  To nám poskytlo následující prahové hodnoty:

V případě prahových hodnot jsme se rozhodli tento 0-100 rozsah 80-20, aby úroveň hluku zůstala nízká a kód, který byl podezřelý, byl jenom podezřelý. Používali jsme následující prahové hodnoty:

- 0-9 = červená
- 10-19 = žlutá
- 20-100 = zelená
