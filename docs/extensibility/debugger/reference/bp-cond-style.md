---
description: Určuje styl podmínky zarážky pro nevyřízené a vázané zarážky.
title: BP_COND_STYLE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_COND_STYLE
helpviewer_keywords:
- BP_COND_STYLE enumeration
ms.assetid: a93b1412-f447-48a1-af9d-38f3dbb3092f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 611df036ff876e10096013070cac097bc51a8986
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105085413"
---
# <a name="bp_cond_style"></a>BP_COND_STYLE
Určuje styl podmínky zarážky pro nevyřízené a vázané zarážky.

## <a name="syntax"></a>Syntax

```cpp
enum enum_BP_COND_STYLE {
    BP_COND_NONE         = 0x0000,
    BP_COND_WHEN_TRUE    = 0x0001,
    BP_COND_WHEN_CHANGED = 0x0002
};
typedef DWORD BP_COND_STYLE;
```

```csharp
public enum enum_BP_COND_STYLE {
    BP_COND_NONE         = 0x0000,
    BP_COND_WHEN_TRUE    = 0x0001,
    BP_COND_WHEN_CHANGED = 0x0002
};
```

## <a name="fields"></a>Pole
`BP_COND_NONE`\
Vyvolá zarážku, když je dosaženo pozice zarážky. Není zadaná žádná podmínka zarážky.

`BP_COND_WHEN_TRUE`\
Aktivuje zarážku pouze v případě, že je podmíněný výraz přidružený ke zarážce vyhodnocen `true` .

`BP_COND_WHEN_CHANGED`\
Vyvolá zarážku pouze v případě, že se hodnota podmíněného výrazu přidruženého ke zarážce změnila z předchozího vyhodnocení.

## <a name="remarks"></a>Poznámky
Používá se pro `styleCondition` člena [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md) struktury.

## <a name="requirements"></a>Požadavky
Záhlaví: msdbg. h

Obor názvů: Microsoft. VisualStudio. Debugger. Interop

Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Výčty](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md)
