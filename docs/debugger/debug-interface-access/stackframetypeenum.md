---
description: Určuje typ rámce zásobníku.
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b84ad19ec31cd1fae65913827b8ee381711f6534
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102155304"
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
