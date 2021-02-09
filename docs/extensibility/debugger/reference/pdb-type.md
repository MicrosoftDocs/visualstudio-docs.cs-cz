---
title: PDB_TYPE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PDB_TYPE
helpviewer_keywords:
- PDB_TYPE structure
ms.assetid: 1c1bb772-77d6-4870-90b2-fd9247d0004e
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: df6a41801f4cce272d896776745ac0cc507d0e38
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99890016"
---
# <a name="pdb_type"></a>PDB_TYPE

Tato struktura určuje informace o typu pole pořízených ze symbolu PDB.

## <a name="syntax"></a>Syntax

```cpp
typedef struct _tagTYPE_PDB {
    ULONG32 ulAppDomainID;
    GUID    guidModule;
    DWORD   symid;
} PDB_TYPE;
```

```csharp
public struct PDB_TYPE {
    public uint ulAppDomainID;
    public Guid guidModule;
    public uint symid;
};
```

## <a name="members"></a>Členové

`ulAppDomainID`\
ID aplikace, ze které byl symbol dodán Slouží k jednoznačné identifikaci instance aplikace.

`guidModule`\
Identifikátor GUID modulu, který obsahuje toto pole.

`symid`\
ID symbolu, který odpovídá tomuto poli.

## <a name="remarks"></a>Poznámky

Tato struktura se zobrazí jako součást sjednocení ve struktuře [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) , pokud `dwKind` `TYPE_INFO` je pole struktury nastaveno na `TYPE_KIND_PDB` hodnotu (hodnota z výčtu [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md) ).

## <a name="requirements"></a>Požadavky

Záhlaví: SH. h

Obor názvů: Microsoft. VisualStudio. Debugger. Interop

Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také

- [Struktury a sjednocení](../../../extensibility/debugger/reference/structures-and-unions.md)
- [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)
- [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)
