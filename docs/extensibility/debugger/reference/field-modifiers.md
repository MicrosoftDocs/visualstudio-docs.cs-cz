---
title: FIELD_MODIFIERS | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- FIELD_MODIFIERS
helpviewer_keywords:
- FIELD_MODIFIERS enumeration
ms.assetid: 1e44681c-1f03-41a9-9c04-b79f231b0822
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f7a24345174854462a2118df626223a8a299cd7f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736852"
---
# <a name="field_modifiers"></a>FIELD_MODIFIERS
Určuje modifikátory pro typ pole.

## <a name="syntax"></a>Syntaxe

```cpp
enum enum_FIELD_MODIFIERS {
    FIELD_MOD_NONE             = 0x00000000,

    // Modifier of the field
    FIELD_MOD_ACCESS_NONE      = 0x00000001,
    FIELD_MOD_ACCESS_PUBLIC    = 0x00000002,
    FIELD_MOD_ACCESS_PROTECTED = 0x00000004,
    FIELD_MOD_ACCESS_PRIVATE   = 0x00000008,

    // Storage modifier of the field
    FIELD_MOD_NOMODIFIERS      = 0x00000010,
    FIELD_MOD_STATIC           = 0x00000020,
    FIELD_MOD_CONSTANT         = 0x00000040,
    FIELD_MOD_TRANSIENT        = 0x00000080,
    FIELD_MOD_VOLATILE         = 0x00000100,
    FIELD_MOD_ABSTRACT         = 0x00000200,
    FIELD_MOD_NATIVE           = 0x00000400,
    FIELD_MOD_SYNCHRONIZED     = 0x00000800,
    FIELD_MOD_VIRTUAL          = 0x00001000,
    FIELD_MOD_INTERFACE        = 0x00002000,
    FIELD_MOD_FINAL            = 0x00004000,
    FIELD_MOD_SENTINEL         = 0x00008000,
    FIELD_MOD_INNERCLASS       = 0x00010000,
    FIELD_TYPE_OPTIONAL        = 0x00020000,
    FIELD_MOD_BYREF            = 0x00040000,
    FIELD_MOD_HIDDEN           = 0x00080000,
    FIELD_MOD_MARSHALASOBJECT  = 0x00100000,
    FIELD_MOD_SPECIAL_NAME     = 0x00200000,
    FIELD_MOD_HIDEBYSIG        = 0x00400000,

    FIELD_MOD_WRITEONLY        = 0x80000000,
    FIELD_MOD_ACCESS_MASK      = 0x000000ff,
    FIELD_MOD_MASK             = 0xffffff00,
    FIELD_MOD_ALL              = 0x7fffffff
};
typedef DWORD FIELD_MODIFIERS;
```

```csharp
public enum enum_FIELD_MODIFIERS {
    FIELD_MOD_NONE             = 0x00000000,

    // Modifier of the field
    FIELD_MOD_ACCESS_NONE      = 0x00000001,
    FIELD_MOD_ACCESS_PUBLIC    = 0x00000002,
    FIELD_MOD_ACCESS_PROTECTED = 0x00000004,
    FIELD_MOD_ACCESS_PRIVATE   = 0x00000008,

    // Storage modifier of the field
    FIELD_MOD_NOMODIFIERS      = 0x00000010,
    FIELD_MOD_STATIC           = 0x00000020,
    FIELD_MOD_CONSTANT         = 0x00000040,
    FIELD_MOD_TRANSIENT        = 0x00000080,
    FIELD_MOD_VOLATILE         = 0x00000100,
    FIELD_MOD_ABSTRACT         = 0x00000200,
    FIELD_MOD_NATIVE           = 0x00000400,
    FIELD_MOD_SYNCHRONIZED     = 0x00000800,
    FIELD_MOD_VIRTUAL          = 0x00001000,
    FIELD_MOD_INTERFACE        = 0x00002000,
    FIELD_MOD_FINAL            = 0x00004000,
    FIELD_MOD_SENTINEL         = 0x00008000,
    FIELD_MOD_INNERCLASS       = 0x00010000,
    FIELD_TYPE_OPTIONAL        = 0x00020000,
    FIELD_MOD_BYREF            = 0x00040000,
    FIELD_MOD_HIDDEN           = 0x00080000,
    FIELD_MOD_MARSHALASOBJECT  = 0x00100000,
    FIELD_MOD_SPECIAL_NAME     = 0x00200000,
    FIELD_MOD_HIDEBYSIG        = 0x00400000,

    FIELD_MOD_WRITEONLY        = 0x80000000,
    FIELD_MOD_ACCESS_MASK      = 0x000000ff,
    FIELD_MOD_MASK             = 0xffffff00,
    FIELD_MOD_ALL              = 0x7fffffff
};
```

## <a name="fields"></a>Fields (Pole)
`FIELD_MOD_ACCESS_TYPE`\
Označuje, že pole nelze získat přístup.

`FIELD_MOD_ACCESS_PUBLIC`\
Označuje, že pole má veřejný přístup.

`FIELD_MOD_ACCESS_PROTECTED`\
Označuje, že pole má chráněný přístup.

`FIELD_MOD_ACCESS_PRIVATE`\
Označuje, že pole má soukromý přístup.

`FIELD_MOD_NOMODIFIERS`\
Označuje, že pole nemá žádné modifikátory.

`FIELD_MOD_STATIC`\
Označuje, že pole je statické.

`FIELD_MOD_CONSTANT`\
Označuje, že pole je konstanta.

`FIELD_MOD_TRANSIENT`\
Označuje, že pole je přechodné.

`FIELD_MOD_VOLATILE`\
Označuje, že pole je nestálé.

`FIELD_MOD_ABSTRACT`\
Označuje, že pole je abstraktní.

`FIELD_MOD_NATIVE`\
Označuje, že pole je nativní.

`FIELD_MOD_SYNCHRONIZED`\
Označuje, že pole je synchronizováno.

`FIELD_MOD_VIRTUAL`\
Označuje, že pole je virtuální.

`FIELD_MOD_INTERFACE`\
Označuje, že pole je rozhraní.

`FIELD_MOD_FINAL`\
Označuje, že pole je konečné.

`FIELD_MOD_SENTINEL`\
Označuje, že pole je sentinel.

`FIELD_MOD_INNERCLASS`\
Označuje, že pole je vnitřní třída.

`FIELD_TYPE_OPTIONAL`\
Označuje, že pole je volitelné.

`FIELD_MOD_BYREF`\
Označuje, že pole je referenční mač. Toto je speciálně pro argumenty metody.

`FIELD_MOD_HIDDEN`\
Označuje, že pole musí být skryto nebo prezentováno v jiném kontextu; například [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)] statické místní.

`FIELD_MOD_MARSHALASOBJECT`\
Označuje, že pole představuje `IUnknown` objekt s rozhraním.

`FIELD_MOD_SPECIAL_NAME`\
Označuje, že pole má zvláštní název, `.ctor` například[!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)] pro konstruktor (pouze).

`FIELD_MOD_HIDEBYSIG`\
Označuje, že na `Overloads` pole bylo[!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)] použito klíčové slovo (pouze).

`FIELD_MOD_WRITEONLY`\
Označuje, že pole je jen pro zápis. Tato hodnota není `FIELD_MOD_ALL`zahrnuta v aplikaci , protože pouze použití těchto polí pouze pro zápis je pro vyhodnocení funkce. Uživatel musí explicitně `FIELD_MOD_WRITEONLY` požádat o pole.

`FIELD_MOD_ACCESS_MASK`\
Označuje masku pro přístup k polím.

`FIELD_MOD_MASK`\
Označuje masku pro modifikátory pole.

## <a name="remarks"></a>Poznámky
Používá se `dwModifiers` pro člen [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md) struktury.

Tyto hodnoty jsou také předány [EnumFields](../../../extensibility/debugger/reference/idebugcontainerfield-enumfields.md) metoda filtrovat pro konkrétní pole.

## <a name="requirements"></a>Požadavky
Záhlaví: sh.h

Obor názvů: Microsoft.VisualStudio.Debugger.Interop

Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Výčty](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md)
- [EnumFields](../../../extensibility/debugger/reference/idebugcontainerfield-enumfields.md)
