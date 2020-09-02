---
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d67a1806034d55147379626b6eb4f868532e4d77
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85330736"
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