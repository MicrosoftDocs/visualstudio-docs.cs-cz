---
title: Memorytypeenum – | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- MemoryTypeEnum enumeration
ms.assetid: 8778c047-edeb-4495-8f9f-3f8bbb297099
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: a92cc41fd0e6898ad0d108204f5b472000b9b65c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99862309"
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
`MemTypeCode` Přistupuje pouze k paměti kódu.

`MemTypeData` Přistupuje k datům nebo zásobníku paměti.

`MemTypeStack` Přistupuje pouze do zásobníku paměti.

`MemTypeAny` Přistupuje k jakémukoli typu paměti.

## <a name="remarks"></a>Poznámky
Hodnoty v tomto výčtu jsou předány metodě [IDiaStackWalkHelper:: readMemory –](../../debugger/debug-interface-access/idiastackwalkhelper-readmemory.md) pro omezení přístupu k různým typům paměti.

## <a name="requirements"></a>Požadavky
Záhlaví: cvconst. h

## <a name="see-also"></a>Viz také
- [Výčty a struktury](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaStackWalkHelper::readMemory](../../debugger/debug-interface-access/idiastackwalkhelper-readmemory.md)
