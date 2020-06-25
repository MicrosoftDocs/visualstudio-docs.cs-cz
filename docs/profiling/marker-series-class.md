---
title: marker_series třídy | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- cvmarkersobj/Concurrency, diagnostic::marker_series
helpviewer_keywords:
- Concurrency, diagnostic::marker_series class
ms.assetid: b8445ed0-c512-4f92-b6b4-3d05c044f939
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8f7df74624ea602b5c996d5523a45826137119f5
ms.sourcegitcommit: 57d96de120e0574e506dfd80bb7adfbac73f96be
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/24/2020
ms.locfileid: "85330706"
---
# <a name="marker_series-class"></a>marker_series – třída
Představuje sériový kanál událostí generovaných jedním zprostředkovatelem.

## <a name="syntax"></a>Syntax

```cpp
class marker_series;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[marker_series:: marker_series – konstruktor](../profiling/marker-series-marker-series-constructor.md)|Inicializuje novou instanci `marker_series` třídy.|
|[marker_series:: ~ marker_series destruktor](../profiling/marker-series-tilde-marker-series-destructor.md)|Zničí marker_series objekt a uvolní všechny přidělené prostředky.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[marker_series:: is_enabled – metoda](../profiling/marker-series-is-enabled-method.md)|Určuje, zda má kterákoli relace povoleného poskytovatele.|
|[marker_series:: write_alert – metoda](../profiling/marker-series-write-alert-method.md)|Zapíše výstrahu do trasovacího souboru Vizualizátor souběžnosti.|
|[marker_series:: write_flag – metoda](../profiling/marker-series-write-flag-method.md)|Zapíše příznak do trasovacího souboru Vizualizátor souběžnosti.|
|[marker_series:: write_message – metoda](../profiling/marker-series-write-message-method.md)|Zapíše zprávu do trasovacího souboru Vizualizátor souběžnosti.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti
 `marker_series`

## <a name="requirements"></a>Požadavky
 **Záhlaví:** *cvmarkersobj. h*

 **Obor názvů:** Concurrency::d odeslání diagnostických

## <a name="see-also"></a>Viz také
- [obor názvů diagnostiky](../profiling/diagnostic-namespace.md)