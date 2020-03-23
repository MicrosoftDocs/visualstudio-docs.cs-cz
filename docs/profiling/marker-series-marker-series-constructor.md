---
title: marker_series::marker_series konstruktor | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- cvmarkersobj/Concurrency::diagnostic::marker_series::marker_series
helpviewer_keywords:
- Concurrency::diagnostic::marker_series constructor
ms.assetid: 042c7d23-f1d8-4e09-9e76-a21c30243790
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5178b2cebdfa4246256aef6334e026ef091fa553
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "62831410"
---
# <a name="marker_seriesmarker_series-constructor"></a>marker_series::marker_series konstruktor
Inicializuje novou instanci třídy. `marker_series`

## <a name="syntax"></a>Syntaxe

```cpp
marker_series();
marker_series(
   _In_ LPCTSTR _SeriesName
);
marker_series(
   _In_ const GUID* _ProviderGuid
);
marker_series(
   _In_ const GUID* _ProviderGuid,
   _In_ LPCTSTR _SeriesName
);
```

#### <a name="parameters"></a>Parametry
 `_SeriesName`Název řady, kterou chcete vytvořit.

 `_ProviderGuid`Identifikátor GUID zprostředkovatele řady.

## <a name="requirements"></a>Požadavky
 **Záhlaví:** *cvmarkersobj.h*

 **Obor názvů:** Souběžnost::diagnostik

## <a name="see-also"></a>Viz také
- [marker_series třída](../profiling/marker-series-class.md)