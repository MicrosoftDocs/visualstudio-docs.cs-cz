---
title: Zobrazení řádků | Microsoft Docs
description: Zjistěte, jak je zobrazení řádků dostupné jenom pro data profileru získaná pomocí metody vzorkování.
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
ms.openlocfilehash: ac0d7785071e5f2928e7eabb4a29b1655b42c5ad
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2021
ms.locfileid: "98721291"
---
# <a name="lines-view"></a>Zobrazení řádků
Zobrazení řádků je k dispozici pouze pro data profileru, která byla shromážděna pomocí metody vzorkování. Zobrazení není k dispozici pro data shromážděná pomocí instrumentace.

 V případě vzorkování dat profilu se v zobrazení řádky identifikuje příkaz ve funkci, která byla přímo spuštěna při shromáždění ukázky. V případě dat paměti .NET identifikuje zobrazení řádky příkazy, které přidělují paměť.

 Ve zdrojovém souboru může příkaz pokrývat více než jeden řádek ve zdrojovém souboru a jeden řádek může obsahovat více než jeden výraz.

 Příkaz je identifikován následujícím způsobem:

- Zdrojový soubor, který obsahuje příkaz Function.

- Funkce, která obsahuje příkaz.

- Zdrojový řádek, ve kterém se příkaz spustí.

- Znak ve zdrojovém řádku, ve kterém se příkaz spustí.

- Zdrojový řádek, na kterém končí příkaz.

- Znak ve zdrojovém řádku, na kterém končí příkaz.

## <a name="see-also"></a>Viz také
- [Zobrazení řádků](../profiling/lines-view-sampling-data.md)
- [Zobrazení řádků – vzorkování](../profiling/lines-view-dotnet-memory-sampling-data.md)
- [Zobrazení řádků](../profiling/lines-view-contention-data.md)
