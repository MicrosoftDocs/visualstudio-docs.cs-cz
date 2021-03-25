---
description: Popisuje výjimku nebo chybu za běhu vyvolanou laděným programem.
title: EXCEPTION_INFO | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- EXCEPTION_INFO
helpviewer_keywords:
- EXCEPTION_INFO structure
ms.assetid: d046957a-b97d-420b-b46b-c67cbaef709e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1ec97b56cc7fca8c2185d7180a8d34e87b084b11
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105059467"
---
# <a name="exception_info"></a>EXCEPTION_INFO
Popisuje výjimku nebo chybu za běhu vyvolanou laděným programem.

## <a name="syntax"></a>Syntax

```cpp
typedef struct tagEXCEPTION_INFO {
    IDebugProgram2* pProgram;
    BSTR            bstrProgramName;
    BSTR            bstrExceptionName;
    DWORD           dwCode;
    EXCEPTION_STATE dwState;
    GUID            guidType;
} EXCEPTION_INFO;
```

```csharp
public struct EXCEPTION_INFO {
    public IDebugProgram2 pProgram;
    public string         bstrProgramName;
    public string         bstrExceptionName;
    public uint           dwCode;
    public uint           dwState;
    public Guid           guidType;
};
```

## <a name="members"></a>Členové
`pProgram`\
Objekt [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) , který představuje program, ve kterém došlo k výjimce.

`bstrProgramName`\
Název programu, ve kterém došlo k výjimce.

`bstrExceptionName`\
Název výjimky.

`dwCode`\
Identifikační kód pro výjimku nebo chybu za běhu.

`dwState`\
Hodnota z výčtu [EXCEPTION_STATE](../../../extensibility/debugger/reference/exception-state.md) definující stav výjimky.

`guidType`\
Identifikátor jazyka GUID, buď `guidLang` nebo `guidEng` .

## <a name="remarks"></a>Poznámky
Tato struktura je předána jako parametr [SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md) a metodám [RemoveSetException](../../../extensibility/debugger/reference/idebugengine2-removesetexception.md) . Tato struktura je také předána metodě [Getexcept](../../../extensibility/debugger/reference/idebugexceptionevent2-getexception.md) , která má být vyplněna.

## <a name="requirements"></a>Požadavky
Záhlaví: msdbg. h

Obor názvů: Microsoft. VisualStudio. Debugger. Interop

Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Struktury a sjednocení](../../../extensibility/debugger/reference/structures-and-unions.md)
- [EXCEPTION_STATE](../../../extensibility/debugger/reference/exception-state.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md)
- [RemoveSetException](../../../extensibility/debugger/reference/idebugengine2-removesetexception.md)
- [GetException](../../../extensibility/debugger/reference/idebugexceptionevent2-getexception.md)
