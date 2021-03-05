---
description: Určuje podmínku spojenou s počtem průchodů zarážkou, který způsobuje, že se zarážka aktivuje.
title: BP_PASSCOUNT_STYLE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_PASSCOUNT_STYLE
helpviewer_keywords:
- BP_PASSCOUNT_STYLE structure
ms.assetid: 0a647047-e2d5-4724-a0b8-68108425ecad
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e216b61d6fed41571baa7f68201d96f84532fc3a
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102144166"
---
# <a name="bp_passcount_style"></a>BP_PASSCOUNT_STYLE
Určuje podmínku spojenou s počtem průchodů zarážkou, který způsobuje, že se zarážka aktivuje.

## <a name="syntax"></a>Syntax

```cpp
enum enum_BP_PASSCOUNT_STYLE {
    BP_PASSCOUNT_NONE             = 0x0000,
    BP_PASSCOUNT_EQUAL            = 0x0001,
    BP_PASSCOUNT_EQUAL_OR_GREATER = 0x0002,
    BP_PASSCOUNT_MOD              = 0x0003
};
typedef DWORD BP_PASSCOUNT_STYLE;
```

```csharp
public enum enum_BP_PASSCOUNT_STYLE {
    BP_PASSCOUNT_NONE             = 0x0000,
    BP_PASSCOUNT_EQUAL            = 0x0001,
    BP_PASSCOUNT_EQUAL_OR_GREATER = 0x0002,
    BP_PASSCOUNT_MOD              = 0x0003
};
```

## <a name="fields"></a>Pole
`BP_PASSCOUNT_NONE`\
Určuje styl počtu průchodů zarážek.

`BP_PASSCOUNT_EQUAL`\
Nastaví styl počtu průchodů zarážky na hodnotu EQUAL. Zarážka je aktivována, když je počet volání zarážky stejný jako počet průchodů.

`BP_PASSCOUNT_EQUAL_OR_GREATER`\
Nastaví styl počtu průchodů zarážky na hodnotu EQUAL nebo vyšší. Zarážka je aktivována, když je počet volání zarážky roven nebo větší než počet průchodů.

`BP_PASSCOUNT_MOD`\
Určuje počet průchodů modulo. Například pokud je počet průchodů typu `BP_PASSCOUNT_MOD` a hodnota počtu průchodů je 4, zarážka se aktivuje pokaždé, když je počet volání násobkem 4.

## <a name="remarks"></a>Poznámky
Používá se pro `stylePassCount` členy [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md) struktury, která je členem [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) a [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) struktury.

## <a name="requirements"></a>Požadavky
Záhlaví: msdbg. h

Obor názvů: Microsoft. VisualStudio. Debugger. Interop

Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Výčty](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md)
- [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)
- [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)
