---
title: dwTYPE_KIND | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- dwTYPE_KIND
helpviewer_keywords:
- dwTYPE_KIND enumeration
ms.assetid: 6ff56b0f-c502-4e6c-9829-bfa05361b783
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a9d790f12d3fc21bbae7373470746af2ebfe6dc9
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737190"
---
# <a name="dwtype_kind"></a>dwTYPE_KIND
Určuje, jak interpretovat typ objektu [IDebugField.](../../../extensibility/debugger/reference/idebugfield.md)

## <a name="syntax"></a>Syntaxe

```cpp
enum enum_dwTYPE_KIND {
    TYPE_KIND_METADATA = 0x0001,
    TYPE_KIND_PDB      = 0x0002,
    TYPE_KIND_BUILT    = 0x0003,
};

typedef DWORD dwTYPE_KIND;
```

```csharp
public enum enum_dwTYPE_KIND {
    TYPE_KIND_METADATA = 0x0001,
    TYPE_KIND_PDB      = 0x0002,
    TYPE_KIND_BUILT    = 0x0003,
};
```

## <a name="fields"></a>Fields (Pole)
`TYPE_KIND_METADATA`\
Svaz [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) by měl být vykládán jako [METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md) struktura.

`TYPE_KIND_PDB`\
Unie `TYPE_INFO` by měla být vykládána jako [PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md) struktura.

`TYPE_KIND_BUILT`\
Unie `TYPE_INFO` by měla být vykládána jako [BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md) struktura.

## <a name="remarks"></a>Poznámky
Hodnoty tohoto výčtu se `dwKind` zobrazí v poli [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) struktury a slouží `type` k určení, jak interpretovat člena unie. Struktura `TYPE_INFO` je vrácena voláním [GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md) metoda.

## <a name="requirements"></a>Požadavky
Záhlaví: sh.h

Obor názvů: Microsoft.VisualStudio.Debugger.Interop

Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Výčty](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)
- [GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md)
- [METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md)
- [PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md)
- [BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md)
