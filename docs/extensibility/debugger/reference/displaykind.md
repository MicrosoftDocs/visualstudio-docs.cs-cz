---
description: Vytvoří výčet platných hodnot, které reprezentují typy informací, které mají být přebírat z objektu IDebugField a zobrazí uživateli.
title: DisplayKind | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- DisplayKind enumeration
ms.assetid: 940968c5-6065-4bda-8ee6-c31597db4d71
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5632c6844a38f1891070311fe3c7c65a0220def5
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102151021"
---
# <a name="displaykind"></a>DisplayKind
Vytvoří výčet platných hodnot, které reprezentují typy informací, které mají být přebírat z objektu [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) a zobrazí uživateli.

## <a name="syntax"></a>Syntax

```cpp
enum enum_DisplayKind
{
    DisplayKind_Value = 0x1,
    DisplayKind_Name = 0x2,
    DisplayKind_Type = 0x3,
};
typedef DWORD DisplayKind;
```

```csharp
public enum enum_DisplayKind
{
    DisplayKind_Value = 0x1,
    DisplayKind_Name = 0x2,
    DisplayKind_Type = 0x3,
};
```

## <a name="fields"></a>Pole
`DisplayKind_Value`\
Hodnota pole

`DisplayKind_Name`\
Název pole

`DisplayKind_Type`\
Typ pole.

## <a name="requirements"></a>Požadavky
Záhlaví: ee. h

Obor názvů: Microsoft. VisualStudio. Debugger. Interop

Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Výčty](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetValueDisplayStringCount](../../../extensibility/debugger/reference/ieevisualizerservice-getvaluedisplaystringcount.md)
