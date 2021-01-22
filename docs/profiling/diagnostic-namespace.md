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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 20b25e2974f4b0e4a6bbf6cf02c411fde3f3de1a
ms.sourcegitcommit: d13f7050c873b6284911d1f4acf07cfd29360183
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/22/2021
ms.locfileid: "98686542"
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