---
title: Graf aktivity GPU | Microsoft Docs
description: Pochopení grafu aktivity GPU, který se zobrazí v Vizualizér souběžnosti, úroveň aktivity rozhraní DirectX v systému.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.cpu.graph.gpu
ms.assetid: d7c769af-95fb-49a3-b5ab-deafecee46fa
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bccf4869a1197306017b443b00670cc123300a48
ms.sourcegitcommit: 589d96700208bf22c8da9e26a1d2041fbf39b8f9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/26/2021
ms.locfileid: "98801331"
---
# <a name="gpu-activity-graph"></a>Graf aktivity GPU
Graf aktivity GPU v Vizualizér souběžnosti zobrazuje úroveň aktivity rozhraní DirectX v systému podle počtu používaných modulů rozhraní DirectX v čase.  Graf nezobrazuje, které konkrétní stroje byly použity.  Modul se považuje za používaný, pokud zpracovává veškerou práci GPU.

## <a name="gpu-activity-graph-colors"></a>Barvy grafu aktivity GPU
 Zelená označuje, že se v rámci aktuálního procesu spotřebují moduly DirectX.

 Světlá šedá znamená, že se v systému využije modul DirectX pro jiné procesy. Chcete-li snížit spotřebu rozhraní DirectX pomocí jiných procesů, snižte počet dalších procesů spuštěných v systému.

 Bílá označuje dostupnost nepoužívaných modulů DirectX v systému. Tyto moduly jsou k dispozici pro váš proces, pokud můžete najít více příležitostí k jejich zneužití. Některé moduly lze použít pouze pro konkrétní druhy úkolů.

## <a name="see-also"></a>Viz také
- [Zobrazení využití](../profiling/utilization-view.md)