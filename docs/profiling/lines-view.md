---
title: Zobrazení řádků | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.view.lines
helpviewer_keywords:
- profiling tools reports, Line view
- profiling tools, Line view
- Lines view
ms.assetid: 71ec0781-6031-4e17-af09-f50226018437
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 25dbb0beb600f7f043ae006e09ac48b9b64d613b
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74773978"
---
# <a name="lines-view"></a>Zobrazení řádků
Zobrazení Čáry je k dispozici pouze pro data profileru, která byla shromážděna pomocí metody vzorkování. Zobrazení není k dispozici pro data, která byla shromážděna pomocí instrumentace.

 Pro data profil vzorkování, čáry zobrazení identifikuje příkaz ve funkci, která byla přímo provádění při vzorku byla shromážděna. U dat paměti .NET zobrazení čáry identifikuje příkazy, které přidělují paměť.

 Ve zdrojovém souboru může příkaz zahrnovat více než jeden řádek ve zdrojovém souboru a jeden řádek může obsahovat více než jeden příkaz.

 Prohlášení je označeno:

- Zdrojový soubor, který obsahuje příkaz funkce.

- Funkce, která obsahuje příkaz.

- Zdrojový řádek, na kterém začíná příkaz.

- Znak ve zdrojovém řádku, na kterém začíná příkaz.

- Zdrojový řádek, na kterém končí příkaz.

- Znak ve zdrojovém řádku, na kterém končí příkaz.

## <a name="see-also"></a>Viz také
- [Zobrazení řádků](../profiling/lines-view-sampling-data.md)
- [Zobrazení čar - odběr vzorků](../profiling/lines-view-dotnet-memory-sampling-data.md)
- [Zobrazení řádků](../profiling/lines-view-contention-data.md)
