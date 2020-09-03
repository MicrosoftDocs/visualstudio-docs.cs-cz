---
title: 'IDebugProgram2:: GetDisassemblyStream | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProgram2::GetDisassemblyStream
helpviewer_keywords:
- IDebugProgram2::GetDisassemblyStream
ms.assetid: beda0da5-267e-4bf3-96c4-b659d29e2254
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6f918b9895975554534ef1702334d7a006112f77
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68202734"
---
# <a name="idebugprogram2getdisassemblystream"></a>IDebugProgram2::GetDisassemblyStream
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Získá datový proud zpětného překladu pro tento program nebo část tohoto programu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
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
  
#### <a name="parameters"></a>Parametry  
 `dwScope`  
 pro Určuje hodnotu z výčtu [DISASSEMBLY_STREAM_SCOPE](../../../extensibility/debugger/reference/disassembly-stream-scope.md) , který definuje obor zpětného streamu zpětného překladu.  
  
 `pCodeContext`  
 pro Objekt [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) , který představuje pozici, kde se má spustit zpětný proud zpětného překladu.  
  
 `ppDisassemblyStream`  
 mimo Vrátí objekt [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md) , který představuje Stream zpětného překladu.  
  
## <a name="return-value"></a>Návratová hodnota  
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby. Vrátí `E_DISASM_NOTSUPPORTED` , zda zpětný překlad není pro tuto konkrétní architekturu podporován.  
  
## <a name="remarks"></a>Poznámky  
 Pokud `dwScopes` má parametr příznak pro `DSS_HUGE` [DISASSEMBLY_STREAM_SCOPE](../../../extensibility/debugger/reference/disassembly-stream-scope.md) sadu výčtu, pak se očekává, že zpětné sestavení vrátí velký počet pokynů pro zpětný překlad, například pro celý soubor nebo modul. Pokud `DSS_HUGE` příznak není nastaven, očekává se, že zpětný překlad bude omezen na malou oblast, obvykle pro jednu funkci.  
  
## <a name="see-also"></a>Viz také  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [DISASSEMBLY_STREAM_SCOPE](../../../extensibility/debugger/reference/disassembly-stream-scope.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)   
 [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)
