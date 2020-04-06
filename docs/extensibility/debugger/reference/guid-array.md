---
title: GUID_ARRAY | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- GUID_ARRAY structure
ms.assetid: 9e12500c-2c1c-49b1-a0ba-e08366c97eb8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e163674b5622146ef1a270920dc7458dce2e3993
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736639"
---
# <a name="guid_array"></a>GUID_ARRAY
Popisuje pole jedinečných identifikátorů pro dostupné ladicí moduly.

## <a name="syntax"></a>Syntaxe

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
Počet jedinečných identifikátorů v poli.

`Members`\
Pole, které obsahuje jedinečné identifikátory.

## <a name="remarks"></a>Poznámky
Tato struktura je vrácena [metodou GetEngineFilter.](../../../extensibility/debugger/reference/idebugprocess3-getenginefilter.md)

## <a name="requirements"></a>Požadavky
Záhlaví: Msdbg.h

Obor názvů: Microsoft.VisualStudio.Debugger.Interop

Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Struktury a sjednocení](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetEngineFilter](../../../extensibility/debugger/reference/idebugprocess3-getenginefilter.md)
