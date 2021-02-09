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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 46f3e4ce7f155679bc3c701af90ff51e0fb20239
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99907282"
---
# <a name="gpu-activity-graph"></a>Graf aktivity GPU
Graf aktivity GPU v Vizualizér souběžnosti zobrazuje úroveň aktivity rozhraní DirectX v systému podle počtu používaných modulů rozhraní DirectX v čase.  Graf nezobrazuje, které konkrétní stroje byly použity.  Modul se považuje za používaný, pokud zpracovává veškerou práci GPU.

## <a name="gpu-activity-graph-colors"></a>Barvy grafu aktivity GPU
 Zelená označuje, že se v rámci aktuálního procesu spotřebují moduly DirectX.

 Světlá šedá znamená, že se v systému využije modul DirectX pro jiné procesy. Chcete-li snížit spotřebu rozhraní DirectX pomocí jiných procesů, snižte počet dalších procesů spuštěných v systému.

 Bílá označuje dostupnost nepoužívaných modulů DirectX v systému. Tyto moduly jsou k dispozici pro váš proces, pokud můžete najít více příležitostí k jejich zneužití. Některé moduly lze použít pouze pro konkrétní druhy úkolů.

## <a name="see-also"></a>Viz také
- [Zobrazení využití](../profiling/utilization-view.md)