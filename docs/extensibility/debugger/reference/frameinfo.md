---
title: FRAMEINFO | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- FRAMEINFO
helpviewer_keywords:
- FRAMEINFO structure
ms.assetid: 95001b89-dddb-45bb-889d-8327994e38a5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c40361a9739bf468de2038df4325fa1ac98337c1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80736794"
---
# <a name="frameinfo"></a>FRAMEINFO
Popisuje rámec zásobníku.

## <a name="syntax"></a>Syntax

```cpp
typedef struct tagFRAMEINFO {
    FRAMEINFO_FLAGS    m_dwValidFields;
    BSTR               m_bstrFuncName;
    BSTR               m_bstrReturnType;
    BSTR               m_bstrArgs;
    BSTR               m_bstrLanguage;
    BSTR               m_bstrModule;
    UINT64             m_addrMin;
    UINT64             m_addrMax;
    IDebugStackFrame2* m_pFrame;
    IDebugModule2*     m_pModule;
    BOOL               m_fHasDebugInfo;
    BOOL               m_fStaleCode;
    BOOL               m_fAnnotatedFrame;
} FRAMEINFO;
```

```csharp
public struct FRAMEINFO {
    public uint              m_dwValidFields;
    public string            m_bstrFuncName;
    public string            m_bstrReturnType;
    public string            m_bstrArgs;
    public string            m_bstrLanguage;
    public string            m_bstrModule;
    public ulong             m_addrMin;
    public ulong             m_addrMax;
    public IDebugStackFrame2 m_pFrame;
    public IDebugModule2     m_pModule;
    public int               m_fHasDebugInfo;
    public int               m_fStaleCode;
    public int               m_fAnnotatedFrame;
} FRAMEINFO;
```

## <a name="members"></a>Členové
`m_dwValidFields`\
Kombinace příznaků z výčtu [FRAMEINFO_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md) , který určuje, která pole jsou vyplněna.

`m_bstrFuncName`\
Název funkce spojený s rámcem zásobníku.

`m_bstrReturnType`\
Návratový typ spojený s rámcem zásobníku.

`m_bstrArgs`\
Argumenty funkce spojené s rámcem zásobníku.

`m_bstrLanguage`\
Jazyk, ve kterém je funkce implementována.

`m_bstrModule`\
Název modulu spojený s rámcem zásobníku.

`m_addrMin`\
Minimální adresa fyzického zásobníku.

`m_addrMAX`\
Maximální adresa fyzického zásobníku.

`m_pFrame`\
Objekt [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) , který představuje tento rámec zásobníku.

`m_pModule`\
Objekt [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md) , který představuje modul, který obsahuje tento rámec zásobníku.

`m_fHasDebugInfo`\
Non-Zero ( `TRUE` ), pokud informace o ladění existují v daném snímku.

`m_fStaleCode`\
Non-Zero ( `TRUE` ), pokud je rámec zásobníku přidružen k kódu, který již není platný.

`m_fAnnotatedFrame`\
Nenulová ( `TRUE` ), pokud je bloku zásobníku opatřeno poznámkou v rámci Správce ladění relace (SDM).

## <a name="remarks"></a>Poznámky
Tato struktura je předána metodě [GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md) , která bude vyplněna. Tato struktura je také obsažena v seznamu, který je obsažen v rozhraní [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md) , které je zase vráceno voláním metody [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) .

## <a name="requirements"></a>Požadavky
Záhlaví: msdbg. h

Obor názvů: Microsoft. VisualStudio. Debugger. Interop

Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Struktury a sjednocení](../../../extensibility/debugger/reference/structures-and-unions.md)
- [FRAMEINFO_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md)
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
- [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md)
- [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md)
- [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)
