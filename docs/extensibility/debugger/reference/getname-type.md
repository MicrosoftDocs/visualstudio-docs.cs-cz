---
title: GETNAME_TYPE | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- GETNAME_TYPE
helpviewer_keywords:
- GETNAME_TYPE enumeration
ms.assetid: 2f9f1679-e9e8-4c9c-ac90-aa07bfe69914
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1d0d146ec4ed7340bde36b298df9d455257b35fe
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736672"
---
# <a name="getname_type"></a>GETNAME_TYPE
Určuje typ názvu souborů, které mají být načteny.

## <a name="syntax"></a>Syntaxe

```cpp
enum enum_GETNAME_TYPE {
    GN_NAME         = 0,
    GN_FILENAME     = 1,
    GN_BASENAME     = 2,
    GN_MONIKERNAME  = 3,
    GN_URL          = 4,
    GN_TITLE        = 5,
    GN_STARTPAGEURL = 6
};
typedef DWORD GETNAME_TYPE;
```

```csharp
public enum enum_GETNAME_TYPE {
    GN_NAME         = 0,
    GN_FILENAME     = 1,
    GN_BASENAME     = 2,
    GN_MONIKERNAME  = 3,
    GN_URL          = 4,
    GN_TITLE        = 5,
    GN_STARTPAGEURL = 6
};
```

## <a name="fields"></a>Fields (Pole)
`GN_NAME`\
Určuje popisný název dokumentu nebo kontextu.

`GN_FILENAME`\
Určuje úplnou cestu k dokumentu nebo kontextu.

`GN_BASENAME`\
Určuje název základního souboru namísto úplné cesty k dokumentu nebo kontextu.

`GN_MONIKERNAME`\
Určuje jedinečný název dokumentu nebo kontextu ve formě zástupného názvu.

`GN_URL`\
Určuje název adresy URL dokumentu nebo kontextu.

`GN_TITLE`\
Určuje název dokumentu, pokud existuje.

`GN_STARTPAGEURL`\
Získá adresu URL počáteční stránky pro procesy.

## <a name="remarks"></a>Poznámky
Tyto hodnoty jsou předány jako parametry [GetName](../../../extensibility/debugger/reference/idebugdocument2-getname.md), [GetName](../../../extensibility/debugger/reference/idebugdocumentcontext2-getname.md)a [GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md) metody určit, jaký druh názvu vrátit.

## <a name="requirements"></a>Požadavky
Záhlaví: msdbg.h

Obor názvů: Microsoft.VisualStudio.Debugger.Interop

Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Výčty](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetName](../../../extensibility/debugger/reference/idebugdocument2-getname.md)
- [GetName](../../../extensibility/debugger/reference/idebugdocumentcontext2-getname.md)
- [GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md)
