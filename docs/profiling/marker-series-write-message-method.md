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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 3c5610cc623476fa395fae7bf68c2ffa127c96e2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99927896"
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
 `_Format` Složený řetězec formátu, který obsahuje text vzájemně se smíšenými nulami nebo více formátovacími položkami, které odpovídají objektům v seznamu argumentů.

 `_Importance` Úroveň důležitosti.

 `_Category` Category. důležitost úrovně.

## <a name="requirements"></a>Požadavky
 **Záhlaví:** *cvmarkersobj. h*

 **Obor názvů:** Concurrency::d odeslání diagnostických

## <a name="see-also"></a>Viz také
- [marker_series – třída](../profiling/marker-series-class.md)