---
title: TYPE_INFO | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- TYPE_INFO
helpviewer_keywords:
- TYPE_INFO structure
ms.assetid: d725cb68-a565-49d1-a16f-ff0445c587a0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 82796c1d82dc3ca77151abcec3e1dd6ce13ac59d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713317"
---
# <a name="type_info"></a>TYPE_INFO
Tato struktura určuje různé druhy informací o typu pole.

## <a name="syntax"></a>Syntaxe

```cpp
struct _tagTYPE_INFO_UNION {
   dwTYPE_KIND dwKind;
   union {
      METADATA_TYPE typeMeta;
      PDB_TYPE      typePdb;
      BUILT_TYPE    typeBuilt;
      DWORD         unused;
   } type;
} TYPE_INFO;
```

```csharp
public struct TYPE_INFO {
   public uint   dwKind;
   public IntPtr unionmember;
};
```

## <a name="members"></a>Členové
 `dwKind`\
 Hodnota z [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md) výčtu, který určuje, jak interpretovat unie.

 `type.typeMeta`\
 [Pouze C++] Obsahuje [METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md) strukturu, pokud `dwKind` je `TYPE_KIND_METADATA`.

 `type.typePdb`\
 [Pouze C++] Obsahuje [PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md) strukturu, pokud `dwKind` je `TYPE_KIND_PDB`.

 `type.typeBuilt`\
 [Pouze C++] Obsahuje [BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md) strukturu, pokud `dwKind` je `TYPE_KIND_BUILT`.

 `type.unused`\
 Nepoužité polstrování.

 `type`\
 Název odborů.

 `unionmember`\
 [Pouze C#] Zařazujte to na `dwKind`příslušný typ struktury na základě .

## <a name="remarks"></a>Poznámky
 Tato struktura je předána [GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md) metoda, kde je vyplněna. Způsob interpretace obsahu struktury je založen `dwKind` na poli.

> [!NOTE]
> [Pouze C++] Pokud `dwKind` se `TYPE_KIND_BUILT`rovná , pak je nutné uvolnit základní [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) objekt při `TYPE_INFO` zničení struktury. To se provádí `typeInfo.type.typeBuilt.pUnderlyingField->Release()`voláním .

 [Pouze C#] Následující tabulka ukazuje, jak `unionmember` interpretovat člen pro každý druh typu. Příklad ukazuje, jak se to provádí pro jeden druh typu.

|`dwKind`|`unionmember`interpretována jako|
|--------------|----------------------------------|
|`TYPE_KIND_METADATA`|[METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md)|
|`TYPE_KIND_PDB`|[PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md)|
|`TYPE_KIND_BUILT`|[BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md)|

## <a name="example"></a>Příklad
 Tento příklad ukazuje, `unionmember` jak interpretovat člen `TYPE_INFO` struktury v C#. Tento příklad ukazuje interpretaci`TYPE_KIND_METADATA`pouze jednoho typu ( ), ale ostatní jsou interpretovány přesně stejným způsobem.

```csharp
using System;
using System.Runtime.Interop.Services;
using Microsoft.VisualStudio.Debugger.Interop;

namespace MyPackage
{
    public class MyClass
    {
        public void Interpret(TYPE_INFO ti)
        {
            if (ti.dwKind == (uint)enum_dwTypeKind.TYPE_KIND_METADATA)
            {
                 METADATA_TYPE dataType = (METADATA_TYPE)Marshal.PtrToStructure(ti.unionmember,
                                               typeof(METADATA_TYPE));
            }
        }
    }
}
```

## <a name="requirements"></a>Požadavky
 Záhlaví: sh.h

 Obor názvů: Microsoft.VisualStudio.Debugger.Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Struktury a sjednocení](../../../extensibility/debugger/reference/structures-and-unions.md)
- [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)
- [GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md)
- [METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md)
- [PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md)
- [BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md)
