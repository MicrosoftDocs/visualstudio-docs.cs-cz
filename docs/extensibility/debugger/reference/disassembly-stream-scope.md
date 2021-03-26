---
description: Určuje rozsah zpětného streamu zpětného překladu.
title: DISASSEMBLY_STREAM_SCOPE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DISASSEMBLY_STREAM_SCOPE
helpviewer_keywords:
- DISASSEMBLY_STREAM_SCOPE enumeration
ms.assetid: 43e2b364-cbbe-4755-a7e6-a03f3054c965
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 828d6b9afc659a09a4f1091c741e6246512de025
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105096171"
---
# <a name="disassembly_stream_scope"></a>DISASSEMBLY_STREAM_SCOPE
Určuje rozsah zpětného streamu zpětného překladu.

## <a name="syntax"></a>Syntax

```cpp
enum enum_DISASSEMBLY_STREAM_SCOPE {
    DSS_HUGE     = 0x10000000,
    DSS_FUNCTION = 0x0001,
    DSS_MODULE   = (DSS_HUGE) | 0x0002,
    DSS_ALL      = (DSS_HUGE) | 0x0003
};
typedef DWORD DISASSEMBLY_STREAM_SCOPE;
```

```csharp
public enum enum_DISASSEMBLY_STREAM_SCOPE {
    DSS_HUGE     = 0x10000000,
    DSS_FUNCTION = 0x0001,
    DSS_MODULE   = (DSS_HUGE) | 0x0002,
    DSS_ALL      = (DSS_HUGE) | 0x0003
};
```

## <a name="fields"></a>Pole
`DSS_HUGE`\
Určuje, že při rozkládání kontextu kódu by se vygenerovalo více výstupů, než by klient obvykle chtěl načíst v jednom volání.

`DSS_FUNCTION`\
Určuje, že funkce obsažená v kontextu kódu by měla být zpětně přeložena. Určuje, že zpětný proud zpětného překladu představuje funkci, která je vrácena metodou [GetScope](../../../extensibility/debugger/reference/idebugdisassemblystream2-getscope.md) .

`DSS_MODULE`\
Když je metoda vrácena `IDebugDisassemblyStream2::GetScope` metodou, určuje, že datový proud zpětného překladu představuje modul.

`DSS_ALL`\
Určuje zpětný překlad pro celý adresní prostor.

## <a name="remarks"></a>Poznámky
Předán jako argument metody [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md) a vrácený metodou [GetScope](../../../extensibility/debugger/reference/idebugdisassemblystream2-getscope.md) .

Tyto hodnoty mohou být kombinovány s bitovým operátorem `OR` .

## <a name="requirements"></a>Požadavky
Záhlaví: msdbg. h

Obor názvů: Microsoft. VisualStudio. Debugger. Interop

Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Výčty](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)
- [GetScope](../../../extensibility/debugger/reference/idebugdisassemblystream2-getscope.md)
