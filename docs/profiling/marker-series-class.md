---
title: marker_series třída | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- cvmarkersobj/Concurrency::diagnostic::marker_series
helpviewer_keywords:
- Concurrency::diagnostic::marker_series class
ms.assetid: b8445ed0-c512-4f92-b6b4-3d05c044f939
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 155d47f6764e754a1093cbcf884368c80d709a2a
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "62575914"
---
# <a name="marker_series-class"></a>marker_series třída
Představuje sériový kanál událostí generovaných jednoho zprostředkovatele.

## <a name="syntax"></a>Syntaxe

```cpp
class marker_series;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejní konstruktéři

|Name (Název)|Popis|
|----------|-----------------|
|[marker_series::marker_series konstruktor](../profiling/marker-series-marker-series-constructor.md)|Inicializuje novou instanci třídy. `marker_series`|
|[marker_series::~marker_series destruktor](../profiling/marker-series-tilde-marker-series-destructor.md)|Zničí marker_series objekt a uvolní všechny přidělené prostředky.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[marker_series::is_enabled metoda](../profiling/marker-series-is-enabled-method.md)|Určuje, zda zprostředkovatele povolila některá relace.|
|[marker_series::write_alert metoda](../profiling/marker-series-write-alert-method.md)|Zapíše výstrahu do trasovacího souboru vizuále souběžnosti.|
|[marker_series::write_flag metoda](../profiling/marker-series-write-flag-method.md)|Zapíše příznak do trasovacího souboru vizualizéru souběžnosti.|
|[marker_series::write_message metoda](../profiling/marker-series-write-message-method.md)|Zapíše zprávu do trasovacího souboru vizuále souběžnosti.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti
 `marker_series`

## <a name="requirements"></a>Požadavky
 **Záhlaví:** *cvmarkersobj.h*

 **Obor názvů:** Souběžnost::diagnostik

## <a name="see-also"></a>Viz také
- [diagnostický obor názvů](../profiling/diagnostic-namespace.md)