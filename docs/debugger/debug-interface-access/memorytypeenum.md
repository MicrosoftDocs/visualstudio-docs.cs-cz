---
title: Memorytypeenum – | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MemoryTypeEnum enumeration
ms.assetid: 8778c047-edeb-4495-8f9f-3f8bbb297099
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e0710ec5cdfcfcb59407d18b43b885603f017fdb
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72738635"
---
# <a name="memorytypeenum"></a>MemoryTypeEnum
Určuje typ paměti, pro který má být přístup.

## <a name="syntax"></a>Syntaxe

```C++
enum MemoryTypeEnum {
    MemTypeCode,
    MemTypeData,
    MemTypeStack,
    MemTypeAny = -1
};
```

#### <a name="parameters"></a>Parametry
`MemTypeCode` přistupuje pouze k paměti kódu.

`MemTypeData` přistupuje k datům nebo zásobníku paměti.

`MemTypeStack` přistupuje pouze k paměti zásobníku.

`MemTypeAny` přistupuje k jakémukoli typu paměti.

## <a name="remarks"></a>Poznámky
Hodnoty v tomto výčtu jsou předány metodě [IDiaStackWalkHelper:: readMemory –](../../debugger/debug-interface-access/idiastackwalkhelper-readmemory.md) pro omezení přístupu k různým typům paměti.

## <a name="requirements"></a>Požadavky
Záhlaví: cvconst. h

## <a name="see-also"></a>Viz také:
- [Výčty a struktury](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaStackWalkHelper::readMemory](../../debugger/debug-interface-access/idiastackwalkhelper-readmemory.md)
