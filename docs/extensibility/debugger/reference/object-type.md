---
title: OBJECT_TYPE | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- OBJECT_TYPE
helpviewer_keywords:
- OBJECT_TYPE enumeration
ms.assetid: c4d246f9-8a98-44ec-b2bb-ff5c684f668e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4ffb85a14e42dd57c345481285eb1f776b3866d3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80714132"
---
# <a name="object_type"></a>OBJECT_TYPE
Určuje typ objektu z vyhodnocení výrazu.

## <a name="syntax"></a>Syntaxe

```cpp
enum enum_OBJECT_TYPE { 
   OBJECT_TYPE_BOOLEAN = 0x0,
   OBJECT_TYPE_CHAR    = 0x1,
   OBJECT_TYPE_I1      = 0x2,
   OBJECT_TYPE_U1      = 0x3,
   OBJECT_TYPE_I2      = 0x4,
   OBJECT_TYPE_U2      = 0x5,
   OBJECT_TYPE_I4      = 0x6,
   OBJECT_TYPE_U4      = 0x7,
   OBJECT_TYPE_I8      = 0x8,
   OBJECT_TYPE_U8      = 0x9,
   OBJECT_TYPE_R4      = 0xa,
   OBJECT_TYPE_R8      = 0xb,
   OBJECT_TYPE_OBJECT  = 0xc,
   OBJECT_TYPE_NULL    = 0xd,
   OBJECT_TYPE_CLASS   = 0xe
};
typedef DWORD OBJECT_TYPE;
```

```csharp
public enum enum_OBJECT_TYPE { 
   OBJECT_TYPE_BOOLEAN = 0x0,
   OBJECT_TYPE_CHAR    = 0x1,
   OBJECT_TYPE_I1      = 0x2,
   OBJECT_TYPE_U1      = 0x3,
   OBJECT_TYPE_I2      = 0x4,
   OBJECT_TYPE_U2      = 0x5,
   OBJECT_TYPE_I4      = 0x6,
   OBJECT_TYPE_U4      = 0x7,
   OBJECT_TYPE_I8      = 0x8,
   OBJECT_TYPE_U8      = 0x9,
   OBJECT_TYPE_R4      = 0xa,
   OBJECT_TYPE_R8      = 0xb,
   OBJECT_TYPE_OBJECT  = 0xc,
   OBJECT_TYPE_NULL    = 0xd,
   OBJECT_TYPE_CLASS   = 0xe
};
```

## <a name="fields"></a>Fields (Pole)
 `OBJECT_TYPE_BOOLEAN`\
 Označuje, že objekt je logická hodnota.

 `OBJECT_TYPE_CHAR`\
 Označuje, že objekt je znak.

 `OBJECT_TYPE_I1`\
 Označuje, že objekt je jednobajtové podepsané celé číslo.

 `OBJECT_TYPE_U1`\
 Označuje, že objekt je jednobajtové nepodepsané celé číslo.

 `OBJECT_TYPE_I2`\
 Označuje, že objekt je dvoubajtové podezla.

 `OBJECT_TYPE_U2`\
 Označuje, že objekt je dvoubajtové nepodepsané celé číslo.

 `OBJECT_TYPE_I4`\
 Označuje, že objekt je čtyřbajtové podezla.

 `OBJECT_TYPE_U4`\
 Označuje, že objekt je čtyřbajtové nepodepsané celé číslo.

 `OBJECT_TYPE_I8`\
 Označuje, že objekt je podezírné osmibajtové číslo.

 `OBJECT_TYPE_U8`\
 Označuje, že objekt je osmibajtové nepodepsané celé číslo.

 `OBJECT_TYPE_R4`\
 Označuje, že objekt je čtyřbajtové číslo s plovoucí desetinnou desetinnou tácem.

 `OBJECT_TYPE_R8`\
 Označuje, že objekt je osmibajtové číslo s plovoucí desetinnou desetinnou tácem.

 `OBJECT_TYPE_OBJECT`\
 Označuje, že objekt je objekt.

 `OBJECT_TYPE_NULL`\
 Označuje, že objekt je NULL.

 `OBJECT_TYPE_CLASS`\
 Označuje, že objekt je třída.

## <a name="remarks"></a>Poznámky
 Předáno jako argument metodám [CreatePrimitiveObject](../../../extensibility/debugger/reference/idebugfunctionobject-createprimitiveobject.md) a [CreateArrayObject.](../../../extensibility/debugger/reference/idebugfunctionobject-createarrayobject.md)

## <a name="requirements"></a>Požadavky
 Záhlaví: ee.h

 Obor názvů: Microsoft.VisualStudio.Debugger.Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Výčty](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [CreatePrimitiveObject](../../../extensibility/debugger/reference/idebugfunctionobject-createprimitiveobject.md)
- [CreateArrayObject](../../../extensibility/debugger/reference/idebugfunctionobject-createarrayobject.md)
