---
title: 'IDebugEngineProgram2:: WatchForExpressionEvaluationOnThread | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugEngineProgram2::WatchForExpressionEvaluationOnThread
helpviewer_keywords:
- IDebugEngineProgram2::WatchForExpressionEvaluationOnThread
ms.assetid: 01d05e77-8cac-4d1b-b19f-25756767ed27
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ebc513ead1ae911147217becd8f541cb11cd5585
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "62431469"
---
# <a name="idebugengineprogram2watchforexpressionevaluationonthread"></a>IDebugEngineProgram2::WatchForExpressionEvaluationOnThread
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Povolí (nebo zakáže) vyhodnocení výrazu v daném vlákně, i když se program zastavil.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT WatchForExpressionEvaluationOnThread(   
   IDebugProgram2*       pOriginatingProgram,  
   DWORD                 dwTid,  
   DWORD                 dwEvalFlags,  
   IDebugEventCallback2* pExprCallback,  
   BOOL                  fWatch  
);  
```  
  
```csharp  
int WatchForExpressionEvaluationOnThread(   
   IDebugProgram2       pOriginatingProgram,  
   uint                  dwTid,  
   uint                  dwEvalFlags,  
   IDebugEventCallback2 pExprCallback,  
   int                   fWatch  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pOriginatingProgram`  
 pro Objekt [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) představující program, který vyhodnocuje výraz.  
  
 `dwTid`  
 pro Určuje identifikátor vlákna.  
  
 `dwEvalFlags`  
 pro Kombinace příznaků z výčtu [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) , která určuje, jak má být provedeno vyhodnocení.  
  
 `pExprCallback`  
 pro Objekt [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) , který se má použít k odeslání událostí ladění, ke kterým dojde při vyhodnocování výrazu.  
  
 `fWatch`  
 pro Pokud je nenulová ( `TRUE` ), umožňuje vyhodnocení výrazu na vlákně identifikovaném `dwTid` . v opačném případě nula ( `FALSE` ) zakáže vyhodnocení výrazu v tomto vlákně.  
  
## <a name="return-value"></a>Návratová hodnota  
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.  
  
## <a name="remarks"></a>Poznámky  
 Když správce ladění relace (SDM) požádá o program označený `pOriginatingProgram` parametrem, aby vyhodnotil výraz, upozorní všechny ostatní připojené programy voláním této metody.  
  
 Vyhodnocení výrazu v jednom programu může způsobit, že se kód spustí v jiném z důvodu vyhodnocení funkce nebo vyhodnocení jakýchkoli `IDispatch` vlastností. Z tohoto důvodu umožňuje tato metoda vyhodnocení výrazu spustit a dokončit, i když je vlákno v tomto programu možné zastavit.  
  
## <a name="see-also"></a>Viz také  
 [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)   
 [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
