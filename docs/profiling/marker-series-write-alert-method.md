---
title: marker_series::write_alert metoda | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- cvmarkersobj/Concurrency::diagnostic:marker_series::write_alert
helpviewer_keywords:
- Concurrency::diagnostic:marker_series::write_alert method
ms.assetid: 9d5465c7-f862-47a7-b249-4116605075a6
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 635f767f97ea3d237aeff843e99735eccae31efc
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "62831381"
---
# <a name="marker_serieswrite_alert-method"></a>marker_series::write_alert metoda
Zapíše výstrahu do trasovacího souboru vizuále souběžnosti.

## <a name="syntax"></a>Syntaxe

```cpp
void write_alert(
   _In_ LPCTSTR _Format,
   ...
);
```

#### <a name="parameters"></a>Parametry
 `_Format`Složený formátovací řetězec, který obsahuje text smíchaný s nulovými nebo více položkami formátu, které odpovídají objektům v seznamu argumentů.

## <a name="requirements"></a>Požadavky
 **Záhlaví:** *cvmarkersobj.h*

 **Obor názvů:** Souběžnost::diagnostik

## <a name="see-also"></a>Viz také
- [marker_series třída](../profiling/marker-series-class.md)