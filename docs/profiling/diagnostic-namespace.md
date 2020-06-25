---
title: Obor názvů diagnostiky | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- cvmarkersobj/Concurrency, diagnostic
helpviewer_keywords:
- Concurrency, diagnostic namespace
ms.assetid: ad786b19-7c4c-46ee-bfb6-c4752b373a09
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 680d304a8e4d21365d82f654265ae2f34582b636
ms.sourcegitcommit: 57d96de120e0574e506dfd80bb7adfbac73f96be
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/24/2020
ms.locfileid: "85330261"
---
# <a name="diagnostic-namespace"></a>obor názvů diagnostiky
`diagnostics`Obor názvů poskytuje funkce pro generování značek Vizualizátor souběžnosti.

## <a name="syntax"></a>Syntax

```cpp
namespace diagnostic;
```

## <a name="members"></a>Členové

### <a name="classes"></a>Třídy

|Název|Popis|
|----------|-----------------|
|[marker_series – třída](../profiling/marker-series-class.md)|Představuje sériový kanál událostí generovaných jedním zprostředkovatelem.|
|[span – třída](../profiling/span-class.md)|Definuje fázi aplikace.|

### <a name="enumerations"></a>Výčty

|Název|Popis|
|----------|-----------------|
|[marker_importance – výčet](../profiling/marker-importance-enumeration.md)|Představuje úroveň důležitosti značky Vizualizátor souběžnosti.|

## <a name="requirements"></a>Požadavky
 **Záhlaví:** *cvmarkersobj. h*

 **Obor názvů:** Concurrency

## <a name="see-also"></a>Viz také
- [Concurrency – obor názvů (Vizualizátor souběžnosti)](../profiling/concurrency-namespace-concurrency-visualizer.md)