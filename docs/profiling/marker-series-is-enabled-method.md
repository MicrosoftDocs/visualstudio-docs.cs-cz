---
title: marker_series::is_enabled metoda | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- cvmarkersobj/Concurrency::diagnostic::marker_series::is_enabled
helpviewer_keywords:
- Concurrency::diagnostic::marker_series::is_enabled method
ms.assetid: 8ce4dd50-ca29-4c72-98d6-582693f7d501
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 22a7baa08a29cd77506e48762179118b3bbb2d1a
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "63002762"
---
# <a name="marker_seriesis_enabled-method"></a>marker_series::is_enabled metoda
Určuje, zda zprostředkovatele povolila některá relace.

## <a name="syntax"></a>Syntaxe

```cpp
bool is_enabled();
bool is_enabled(
   marker_importance _Importance,
   int _Category
);
```

#### <a name="parameters"></a>Parametry
 `_Importance`Úroveň důležitosti.

 `_Category`Kategorie.

## <a name="return-value"></a>Návratová hodnota

## <a name="requirements"></a>Požadavky
 **Záhlaví:** *cvmarkersobj.h*

 **Obor názvů:** Souběžnost::diagnostik

## <a name="see-also"></a>Viz také
- [marker_series třída](../profiling/marker-series-class.md)