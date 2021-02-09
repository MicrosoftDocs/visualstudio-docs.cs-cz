---
title: 'IEnumDebugPrograms2:: Skip | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugPrograms2::Skip
helpviewer_keywords:
- IEnumDebugPrograms2::Skip
ms.assetid: b283858b-b375-4760-bfec-ab37de89958d
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 60ecbef6ed8644176effb3946bbfe72267526053
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99846605"
---
# <a name="ienumdebugprograms2skip"></a>IEnumDebugPrograms2::Skip
Přeskočí na zadaný počet prvků.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT Skip(
   ULONG celt
);
```

```csharp
int Skip(
   uint celt
);
```

## <a name="parameters"></a>Parametry
`celt`\
pro Počet prvků, které se mají přeskočit

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí `S_OK` . Vrátí, `S_FALSE` Pokud `celt` je větší než počet zbývajících prvků. v opačném případě vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Pokud `celt` Určuje hodnotu větší než počet zbývajících prvků, je výčet nastaven na konec a `S_FALSE` je vrácen.

## <a name="see-also"></a>Viz také
- [IEnumDebugPrograms2](../../../extensibility/debugger/reference/ienumdebugprograms2.md)
