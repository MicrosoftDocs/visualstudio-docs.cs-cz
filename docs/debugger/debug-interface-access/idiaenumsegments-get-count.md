---
title: 'IDiaEnumSegments:: get_Count | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSegments::get_Count method
ms.assetid: c62a0fda-17b8-4cf6-b321-6014ce581096
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 74597d8e5deab9fc572500bef0b4175fd5722d96
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/27/2020
ms.locfileid: "85468056"
---
# <a name="idiaenumsegmentsget_count"></a>IDiaEnumSegments::get_Count
Načte počet segmentů.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_Count ( 
   LONG* pRetVal
);
```

#### <a name="parameters"></a>Parametry
 pRetVal
- [out, retval] Vrátí počet segmentů.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.

## <a name="see-also"></a>Viz také
- [IDiaEnumSegments](../../debugger/debug-interface-access/idiaenumsegments.md)
- [IDiaEnumSegments::Item](../../debugger/debug-interface-access/idiaenumsegments-item.md)