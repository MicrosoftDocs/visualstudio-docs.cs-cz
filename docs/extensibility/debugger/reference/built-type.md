---
title: BUILT_TYPE | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BUILT_TYPE
helpviewer_keywords:
- BUILT_TYPE structure
ms.assetid: cc02c32c-0f65-4210-ad25-a9b1899066e8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 885f17b0841a39672c87be5bc7c947b2e0d9c7e0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737695"
---
# <a name="built_type"></a>BUILT_TYPE
Tato struktura určuje informace o typu pole převzatém z metadat.

## <a name="syntax"></a>Syntaxe

```cpp
typedef struct _tagTYPE_BUILT {
    ULONG32      ulAppDomainID;
    GUID         guidModule;
    IDebugField* pUnderlyingField;
} BUILT_TYPE;
```

```csharp
public struct BUILT_TYPE {
    public uint        ulAppDomainID;
    public Guid        guidModule;
    public IDebugField pUnderlyingField;
};
```

## <a name="members"></a>Členové
`ulAppDomainID`\
ID aplikace, ze které symbol pochází. Používá se k jednoznačné identifikaci instance aplikace.

`guidModule`\
Identifikátor GUID modulu, který obsahuje toto pole.

`pUnderlyingField`\
Objekt [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) identifikující základní pole přidružené k tomuto sestavenému poli.

## <a name="remarks"></a>Poznámky
Tato struktura se zobrazí jako součást unie ve [struktuře TYPE_INFO,](../../../extensibility/debugger/reference/type-info.md) `dwKind` když je pole `TYPE_INFO` struktury nastaveno na `TYPE_KIND_BUILT` (hodnota z [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md) výčtu).

## <a name="requirements"></a>Požadavky
Záhlaví: sh.h

Obor názvů: Microsoft.VisualStudio.Debugger.Interop

Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Struktury a sjednocení](../../../extensibility/debugger/reference/structures-and-unions.md)
- [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)
- [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
