---
title: IDebugProgram2::GetDisassemblyStream | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::GetDisassemblyStream
helpviewer_keywords:
- IDebugProgram2::GetDisassemblyStream
ms.assetid: beda0da5-267e-4bf3-96c4-b659d29e2254
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2160f963ad1f3f37291519ced30b8096e33a6116
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722862"
---
# <a name="idebugprogram2getdisassemblystream"></a>IDebugProgram2::GetDisassemblyStream
Získá datový proud demontáže pro tento program nebo část tohoto programu.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetDisassemblyStream( 
   DISASSEMBLY_STREAM_SCOPE   dwScope,
   IDebugCodeContext2*        pCodeContext,
   IDebugDisassemblyStream2** ppDisassemblyStream
);
```

```csharp
int GetDisassemblyStream( 
   enum_DISASSEMBLY_STREAM_SCOPE  dwScope,
   IDebugCodeContext2             pCodeContext,
   out IDebugDisassemblyStream2   ppDisassemblyStream
);
```

## <a name="parameters"></a>Parametry
`dwScope`\
[v] Určuje hodnotu z [DISASSEMBLY_STREAM_SCOPE](../../../extensibility/debugger/reference/disassembly-stream-scope.md) výčtu, který definuje rozsah datového proudu demontáže.

`pCodeContext`\
[v] [Objekt IDebugCodeContext2,](../../../extensibility/debugger/reference/idebugcodecontext2.md) který představuje pozici, kde spustit datový proud demontáže.

`ppDisassemblyStream`\
[out] Vrátí objekt [IDebugDassemblyStream2,](../../../extensibility/debugger/reference/idebugdisassemblystream2.md) který představuje datový proud demontáže.

## <a name="return-value"></a>Návratová hodnota
 V případě `S_OK`úspěchu vrátí ; v opačném případě vrátí kód chyby. Vrátí, `E_DISASM_NOTSUPPORTED` pokud není pro tuto konkrétní architekturu podporována demontáž.

## <a name="remarks"></a>Poznámky
 Pokud `dwScopes` má parametr `DSS_HUGE` příznak sady výčtu [DISASSEMBLY_STREAM_SCOPE,](../../../extensibility/debugger/reference/disassembly-stream-scope.md) očekává se, že demontáž vrátí velký počet pokynů k demontáži, například pro celý soubor nebo modul. Pokud `DSS_HUGE` příznak není nastaven, očekává se, že demontáž bude omezena na malou oblast, obvykle na jednu funkci.

## <a name="see-also"></a>Viz také
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [DISASSEMBLY_STREAM_SCOPE](../../../extensibility/debugger/reference/disassembly-stream-scope.md)
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
- [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)
