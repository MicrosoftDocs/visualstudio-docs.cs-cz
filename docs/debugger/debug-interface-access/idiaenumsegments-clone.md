---
title: 'IDiaEnumSegments:: Clone | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSegments::Clone method
ms.assetid: 93deaac6-72ab-4408-ba14-66174a618757
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b9d0ff6739487ee34cfb1eb216e6f0509ab19f3f
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/27/2020
ms.locfileid: "85468063"
---
# <a name="idiaenumsegmentsclone"></a>IDiaEnumSegments::Clone
Vytvoří enumerátor, který obsahuje stejný stav výčtu jako aktuální enumerátor.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT Clone ( 
   IDiaEnumSegments** ppenum
);
```

#### <a name="parameters"></a>Parametry
 ppenum

mimo Vrátí objekt [IDiaEnumSegments](../../debugger/debug-interface-access/idiaenumsegments.md) , který obsahuje duplikát objektu Enumerator. Segmenty nejsou duplikovány, pouze enumerátor.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.

## <a name="see-also"></a>Viz také
- [IDiaEnumSegments](../../debugger/debug-interface-access/idiaenumsegments.md)