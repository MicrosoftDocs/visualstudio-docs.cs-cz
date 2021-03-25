---
description: Popisuje pole jedinečných identifikátorů pro dostupné moduly ladění.
title: GUID_ARRAY | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- GUID_ARRAY structure
ms.assetid: 9e12500c-2c1c-49b1-a0ba-e08366c97eb8
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 504c917d9fb2b1e2cd15ac8154faf70eaf98beec
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105054579"
---
# <a name="guid_array"></a>GUID_ARRAY
Popisuje pole jedinečných identifikátorů pro dostupné moduly ladění.

## <a name="syntax"></a>Syntax

```cpp
typedef struct tagGUID_ARRAY
{
    DWORD dwCount;
    GUID *Members;
} GUID_ARRAY;
```

```csharp
public struct GUID_ARRAY
{
    public uint dwCount;
    public Guid Members;
}
```

## <a name="members"></a>Členové
`dwCount`\
Počet jedinečných identifikátorů v poli

`Members`\
Pole, které obsahuje jedinečné identifikátory.

## <a name="remarks"></a>Poznámky
Tato struktura je vrácena metodou [GetEngineFilter](../../../extensibility/debugger/reference/idebugprocess3-getenginefilter.md) .

## <a name="requirements"></a>Požadavky
Záhlaví: msdbg. h

Obor názvů: Microsoft. VisualStudio. Debugger. Interop

Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Struktury a sjednocení](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetEngineFilter](../../../extensibility/debugger/reference/idebugprocess3-getenginefilter.md)
