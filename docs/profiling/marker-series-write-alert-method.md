---
title: 'marker_series:: write_alert metoda | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- cvmarkersobj/Concurrency, diagnostic:marker_series::write_alert
helpviewer_keywords:
- Concurrency, diagnostic:marker_series::write_alert method
ms.assetid: 9d5465c7-f862-47a7-b249-4116605075a6
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 786569f52d4d3d2fcaa7dfbc759759080ebf02d7
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99876937"
---
# <a name="marker_serieswrite_alert-method"></a>marker_series:: write_alert – metoda
Zapíše výstrahu do trasovacího souboru Vizualizátor souběžnosti.

## <a name="syntax"></a>Syntaxe

```cpp
void write_alert(
   _In_ LPCTSTR _Format,
   ...
);
```

#### <a name="parameters"></a>Parametry
 `_Format` Složený řetězec formátu, který obsahuje text vzájemně se smíšenými nulami nebo více formátovacími položkami, které odpovídají objektům v seznamu argumentů.

## <a name="requirements"></a>Požadavky
 **Záhlaví:** *cvmarkersobj. h*

 **Obor názvů:** Concurrency::d odeslání diagnostických

## <a name="see-also"></a>Viz také
- [marker_series – třída](../profiling/marker-series-class.md)