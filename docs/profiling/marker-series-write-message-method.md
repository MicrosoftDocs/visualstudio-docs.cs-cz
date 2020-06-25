---
title: 'marker_series:: write_message metoda | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- cvmarkersobj/Concurrency, diagnostic::marker_series::write_message
helpviewer_keywords:
- Concurrency, diagnostic::marker_series::write_message method
ms.assetid: 546121bc-67e0-4a5a-a456-12bd78fd6de2
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 14a4cb4a604907908b8f2b35ea0baa583ab1ca57
ms.sourcegitcommit: 57d96de120e0574e506dfd80bb7adfbac73f96be
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/24/2020
ms.locfileid: "85328301"
---
# <a name="marker_serieswrite_message-method"></a>marker_series:: write_message – metoda
Zapíše zprávu do trasovacího souboru Vizualizátor souběžnosti.

## <a name="syntax"></a>Syntaxe

```cpp
void write_message(
   _In_ LPCTSTR _Format,
   ...
);
void write_message(
   marker_importance _Importance,
   _In_ LPCTSTR _Format,
   ...
);
void write_message(
   int _Category,
   _In_ LPCTSTR _Format,
   ...
);
void write_message(
   marker_importance _Importance,
   int _Category,
   _In_ LPCTSTR _Format,
   ...
);
```

#### <a name="parameters"></a>Parametry
 `_Format`Složený řetězec formátu, který obsahuje text vzájemně se smíšenými nulami nebo více formátovacími položkami, které odpovídají objektům v seznamu argumentů.

 `_Importance`Úroveň důležitosti.

 `_Category`Category. důležitost úrovně.

## <a name="requirements"></a>Požadavky
 **Záhlaví:** *cvmarkersobj. h*

 **Obor názvů:** Concurrency::d odeslání diagnostických

## <a name="see-also"></a>Viz také
- [marker_series – třída](../profiling/marker-series-class.md)