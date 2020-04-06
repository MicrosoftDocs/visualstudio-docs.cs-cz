---
title: BP_PASSCOUNT_STYLE | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_PASSCOUNT_STYLE
helpviewer_keywords:
- BP_PASSCOUNT_STYLE structure
ms.assetid: 0a647047-e2d5-4724-a0b8-68108425ecad
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1633c5e9aa6ff251fedce83a0243664cd9e0e0a7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737917"
---
# <a name="bp_passcount_style"></a>BP_PASSCOUNT_STYLE
Určuje podmínku přidruženou k počtu průchodů zarážky, která způsobí, že se zarážka zapálí.

## <a name="syntax"></a>Syntaxe

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

## <a name="fields"></a>Fields (Pole)
`BP_PASSCOUNT_NONE`\
Určuje žádný styl počtu průchodů zarážky.

`BP_PASSCOUNT_EQUAL`\
Nastaví styl počtu průchodů zarážky na stejný. Zarážka se aktivuje, když počet, kolikrát je zarážka přístupů rovná počet průchodů.

`BP_PASSCOUNT_EQUAL_OR_GREATER`\
Nastaví styl počtu průchodů zarážky na stejný nebo větší. Zarážka je aktivována, když počet, kolikrát je zarážka přístupů je rovna nebo větší než počet průchodů.

`BP_PASSCOUNT_MOD`\
Určuje počet modulo passů. Například pokud počet průchodů je `BP_PASSCOUNT_MOD` typu a hodnota počtu průchodů je 4, zarážka aktivuje pokaždé, když počet přístupů je násobek 4.

## <a name="remarks"></a>Poznámky
Používá se `stylePassCount` pro člen [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md) struktury, která je zase členem [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) a [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) struktury.

## <a name="requirements"></a>Požadavky
Záhlaví: msdbg.h

Obor názvů: Microsoft.VisualStudio.Debugger.Interop

Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Výčty](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md)
- [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)
- [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)
