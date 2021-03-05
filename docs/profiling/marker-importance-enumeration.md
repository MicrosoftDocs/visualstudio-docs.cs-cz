---
description: Představuje úroveň důležitosti značky Vizualizátor souběžnosti.
title: Výčet marker_importance | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- cvmarkersobj/Concurrency, diagnostic::marker_importance
helpviewer_keywords:
- Concurrency, diagnostic::marker_importance enumeration
ms.assetid: d5524ea0-0227-4d8e-9122-332291042df5
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 2c2e7560c91882afe1ee2608bb2ae2fc105738dc
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102223937"
---
# <a name="marker_importance-enumeration"></a>výčet marker_importance
Představuje úroveň důležitosti značky Vizualizátor souběžnosti.

## <a name="syntax"></a>Syntax

```cpp
enum marker_importance;
```

## <a name="members"></a>Členové

### <a name="values"></a>Hodnoty

|Název|Popis|
|----------|-----------------|
|`critical_importance`|Určuje, že značka má kritickou důležitost.|
|`high_importance`|Určuje, že značka má velkou důležitost.|
|`low_importance`|Určuje, že značka má nízkou důležitost.|
|`normal_importance`|Určuje, že má značka normální důležitost.|

## <a name="requirements"></a>Požadavky
 **Záhlaví:** *cvmarkersobj. h*

 **Obor názvů:** Concurrency::d odeslání diagnostických

## <a name="see-also"></a>Viz také
- [obor názvů diagnostiky](../profiling/diagnostic-namespace.md)
