---
title: METADATA_TYPE | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- METADATA_TYPE
helpviewer_keywords:
- METADATA_TYPE structure
ms.assetid: 2d8b78f6-0aef-4d79-809a-cff9b2c24659
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: afe5ea128775c7be0e48035ab4c7e7d370c9d233
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80714292"
---
# <a name="metadata_type"></a>METADATA_TYPE
Tato struktura určuje informace o typu pole převzatém z metadat.

## <a name="syntax"></a>Syntaxe

```cpp
typedef struct _tagTYPE_METADATA {
   ULONG32  ulAppDomainID;
   GUID     guidModule;
   _mdToken tokClass;
} METADATA_TYPE;
```

```csharp
public struct METADATA_TYPE {
   public uint ulAppDomainID;
   public Guid guidModule;
   public int  tokClass;
};
```

## <a name="parameters"></a>Parametry
 `ulAppDomainID`\
 ID aplikace, ze které symbol pochází. Používá se k jednoznačné identifikaci instance aplikace.

 `guidModule`\
 Identifikátor GUID modulu, který obsahuje toto pole.

 `tokClass`\
 ID tokenu metadat tohoto typu.

 [C++] `_mdToken` je `typedef` pro 32bitový `int`.

## <a name="remarks"></a>Poznámky
 Tato struktura se zobrazí jako součást unie ve [struktuře TYPE_INFO,](../../../extensibility/debugger/reference/type-info.md) `dwKind` když je pole `TYPE_INFO` struktury nastaveno na `TYPE_KIND_METADATA` (hodnota z [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md) výčtu).

 Hodnota `tokClass` je token metadat, který jednoznačně identifikuje typ. Podrobnosti o tom, jak interpretovat horní bity ID `CorTokenType` tokenu metadat, naleznete ve výčtu v souboru corhdr.h v sdk rozhraní .NET Framework.

## <a name="requirements"></a>Požadavky
 Záhlaví: sh.h

 Obor názvů: Microsoft.VisualStudio.Debugger.Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Struktury a sjednocení](../../../extensibility/debugger/reference/structures-and-unions.md)
- [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)
- [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)
