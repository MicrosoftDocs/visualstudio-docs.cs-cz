---
title: diagnostický obor názvů | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- cvmarkersobj/Concurrency::diagnostic
helpviewer_keywords:
- Concurrency::diagnostic namespace
ms.assetid: ad786b19-7c4c-46ee-bfb6-c4752b373a09
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 03671f314dca3c016f9524bcb246b74e0eb1f837
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "62970080"
---
# <a name="diagnostic-namespace"></a>diagnostický obor názvů
Obor `diagnostics` názvů poskytuje funkce pro vyzařování značek vizualizérů souběžnosti.

## <a name="syntax"></a>Syntaxe

```cpp
namespace diagnostic;
```

## <a name="members"></a>Členové

### <a name="classes"></a>Třídy

|Name (Název)|Popis|
|----------|-----------------|
|[marker_series – třída](../profiling/marker-series-class.md)|Představuje sériový kanál událostí generovaných jednoho zprostředkovatele.|
|[span – třída](../profiling/span-class.md)|Definuje fázi aplikace.|

### <a name="enumerations"></a>Výčty

|Name (Název)|Popis|
|----------|-----------------|
|[marker_importance – výčet](../profiling/marker-importance-enumeration.md)|Představuje úroveň důležitosti značky Vizualizér souběžnosti.|

## <a name="requirements"></a>Požadavky
 **Záhlaví:** *cvmarkersobj.h*

 **Obor názvů:** Souběžnost

## <a name="see-also"></a>Viz také
- [Obor názvů souběžnosti (vizualizér souběžnosti)](../profiling/concurrency-namespace-concurrency-visualizer.md)