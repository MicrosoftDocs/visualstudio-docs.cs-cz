---
title: marker_importance Výčet | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- cvmarkersobj/Concurrency::diagnostic::marker_importance
helpviewer_keywords:
- Concurrency::diagnostic::marker_importance enumeration
ms.assetid: d5524ea0-0227-4d8e-9122-332291042df5
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b3f5cfb583ec4fceb9fb7428b08c00f6ca8e26b6
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "62999964"
---
# <a name="marker_importance-enumeration"></a>marker_importance výčet
Představuje úroveň důležitosti značky Vizualizér souběžnosti.

## <a name="syntax"></a>Syntaxe

```cpp
enum marker_importance;
```

## <a name="members"></a>Členové

### <a name="values"></a>Hodnoty

|Name (Název)|Popis|
|----------|-----------------|
|`critical_importance`|Určuje, že značka má kritický význam.|
|`high_importance`|Určuje, že značka má vysokou důležitost.|
|`low_importance`|Určuje, že značka má nízkou důležitost.|
|`normal_importance`|Určuje, že značka má normální význam.|

## <a name="requirements"></a>Požadavky
 **Záhlaví:** *cvmarkersobj.h*

 **Obor názvů:** Souběžnost::diagnostik

## <a name="see-also"></a>Viz také
- [diagnostický obor názvů](../profiling/diagnostic-namespace.md)