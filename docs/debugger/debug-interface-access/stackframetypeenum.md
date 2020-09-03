---
title: Stackframetypeenum – | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- StackFrameTypeEnum enumeration
ms.assetid: 61e40163-eee0-4c1f-af47-cef3771bdc41
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3f83cdb163881366a1a0bede95a07e1dae1fc50a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85461096"
---
# <a name="stackframetypeenum"></a>StackFrameTypeEnum
Určuje typ rámce zásobníku.

## <a name="syntax"></a>Syntax

```C++
enum StackFrameTypeEnum {
    FrameTypeFPO,
    FrameTypeTrap,
    FrameTypeTSS,
    FrameTypeStandard,
    FrameTypeFrameData,
    FrameTypeUnknown = -1
};
```

## <a name="elements"></a>Elementy
`FrameTypeFPO` Vynechaný ukazatel na rámec; K dispozici jsou informace o!.

`FrameTypeTrap` Rámec depeše jádra.

`FrameTypeTSS` Rámec depeše jádra.

`FrameTypeStandard` Standardní rámec zásobníku EBP

`FrameTypeFrameData` Vynechaný ukazatel na rámec; K dispozici jsou informace o snímcích dat.

`FrameTypeUnknown` Rámec, který nemá žádné informace o ladění.

## <a name="remarks"></a>Poznámky
Hodnoty v tomto výčtu jsou vráceny voláním metody [IDiaStackFrame:: get_Type](../../debugger/debug-interface-access/idiastackframe-get-type.md) .

## <a name="requirements"></a>Požadavky
Záhlaví: cvconst. h

## <a name="see-also"></a>Viz také
- [Výčty a struktury](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaStackFrame::get_type](../../debugger/debug-interface-access/idiastackframe-get-type.md)
