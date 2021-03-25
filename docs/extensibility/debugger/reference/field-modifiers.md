---
description: Určuje modifikátory pro typ pole.
title: FIELD_MODIFIERS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- FIELD_MODIFIERS
helpviewer_keywords:
- FIELD_MODIFIERS enumeration
ms.assetid: 1e44681c-1f03-41a9-9c04-b79f231b0822
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 55f493280808f0b68089a9d72c4184585d386b18
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105059376"
---
# <a name="field_modifiers"></a>FIELD_MODIFIERS
Určuje modifikátory pro typ pole.

## <a name="syntax"></a>Syntax

```cpp
enum enum_FIELD_MODIFIERS {
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

## <a name="fields"></a>Pole
`FIELD_MOD_ACCESS_TYPE`\
Indikuje, že k poli nelze přicházet.

`FIELD_MOD_ACCESS_PUBLIC`\
Indikuje, že pole má veřejný přístup.

`FIELD_MOD_ACCESS_PROTECTED`\
Indikuje, že pole má chráněný přístup.

`FIELD_MOD_ACCESS_PRIVATE`\
Označuje, že pole má privátní přístup.

`FIELD_MOD_NOMODIFIERS`\
Indikuje, že pole nemá žádné modifikátory.

`FIELD_MOD_STATIC`\
Označuje, že pole je statické.

`FIELD_MOD_CONSTANT`\
Označuje, že pole je konstanta.

`FIELD_MOD_TRANSIENT`\
Indikuje, že je pole přechodné.

`FIELD_MOD_VOLATILE`\
Označuje, že pole je volatile.

`FIELD_MOD_ABSTRACT`\
Označuje, že pole je abstraktní.

`FIELD_MOD_NATIVE`\
Označuje, že pole je nativní.

`FIELD_MOD_SYNCHRONIZED`\
Indikuje, že se pole synchronizuje.

`FIELD_MOD_VIRTUAL`\
Indikuje, že pole je virtuální.

`FIELD_MOD_INTERFACE`\
Označuje, že pole je rozhraní.

`FIELD_MOD_FINAL`\
Indikuje, že pole je finální.

`FIELD_MOD_SENTINEL`\
Označuje, že pole je Sentinel.

`FIELD_MOD_INNERCLASS`\
Označuje, že pole je vnitřní třída.

`FIELD_TYPE_OPTIONAL`\
Označuje, že pole je volitelné.

`FIELD_MOD_BYREF`\
Označuje, že pole je argumentem odkazu. To je speciálně pro argumenty metody.

`FIELD_MOD_HIDDEN`\
Indikuje, že pole musí být skryté nebo zobrazené v jiném kontextu. například [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)] statická národní prostředí.

`FIELD_MOD_MARSHALASOBJECT`\
Označuje, že pole představuje objekt s `IUnknown` rozhraním.

`FIELD_MOD_SPECIAL_NAME`\
Označuje, že pole má speciální název, například `.ctor` pro konstruktor ( [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)] pouze).

`FIELD_MOD_HIDEBYSIG`\
Označuje, že pole má `Overloads` použité klíčové slovo ( [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)] pouze).

`FIELD_MOD_WRITEONLY`\
Označuje, že pole je jen pro zápis. Tato hodnota není obsažena v `FIELD_MOD_ALL` , protože jediné použití takových polí pouze pro zápis je pro vyhodnocení funkce. Uživatel musí explicitně požádat o `FIELD_MOD_WRITEONLY` pole.

`FIELD_MOD_ACCESS_MASK`\
Označuje masku pro přístup k poli.

`FIELD_MOD_MASK`\
Označuje masku pro modifikátory polí.

## <a name="remarks"></a>Poznámky
Používá se pro `dwModifiers` člena [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md) struktury.

Tyto hodnoty jsou také předány metodě [enumfields –](../../../extensibility/debugger/reference/idebugcontainerfield-enumfields.md) pro filtrování konkrétních polí.

## <a name="requirements"></a>Požadavky
Záhlaví: SH. h

Obor názvů: Microsoft. VisualStudio. Debugger. Interop

Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Výčty](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md)
- [EnumFields](../../../extensibility/debugger/reference/idebugcontainerfield-enumfields.md)
