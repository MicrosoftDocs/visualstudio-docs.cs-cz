---
title: Obor názvů diagnostiky | Microsoft Docs
description: Použijte obor názvů diagnostiky k vygenerování značek Vizualizátor souběžnosti. Obor názvů diagnostiky je členem souběžného oboru názvů.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- cvmarkersobj/Concurrency, diagnostic
helpviewer_keywords:
- Concurrency, diagnostic namespace
ms.assetid: ad786b19-7c4c-46ee-bfb6-c4752b373a09
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 22224e375c1d1f463f1c07d41ca5a03efa5cabdb
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99923744"
---
# <a name="diagnostic-namespace"></a>obor názvů diagnostiky
`diagnostics`Obor názvů poskytuje funkce pro generování značek Vizualizátor souběžnosti.

## <a name="syntax"></a>Syntax

```cpp
namespace diagnostic;
```

## <a name="members"></a>Členové

### <a name="classes"></a>Třídy

|Název|Description|
|----------|-----------------|
|[marker_series – třída](../profiling/marker-series-class.md)|Představuje sériový kanál událostí generovaných jedním zprostředkovatelem.|
|[span – třída](../profiling/span-class.md)|Definuje fázi aplikace.|

### <a name="enumerations"></a>Výčty

|Název|Description|
|----------|-----------------|
|[marker_importance – výčet](../profiling/marker-importance-enumeration.md)|Představuje úroveň důležitosti značky Vizualizátor souběžnosti.|

## <a name="requirements"></a>Požadavky
 **Záhlaví:** *cvmarkersobj. h*

 **Obor názvů:** Concurrency

## <a name="see-also"></a>Viz také
- [Concurrency – obor názvů (Vizualizátor souběžnosti)](../profiling/concurrency-namespace-concurrency-visualizer.md)