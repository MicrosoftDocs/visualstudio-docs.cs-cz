---
title: IDebugThread2 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugThread2
helpviewer_keywords:
- IDebugThread2 interface
ms.assetid: 221b4b1b-4a26-466e-bc29-5eff800fab13
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d93744e55a3e516a131e772fd2df09da5ec23168
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2018
ms.locfileid: "31121323"
---
# <a name="idebugthread2"></a>IDebugThread2
Toto rozhraní představuje vlákna spuštěna v programu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDebugThread2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Poznámky pro implementátory  
 Modul ladění (DE) implementuje toto rozhraní představují vlákno při provádění v jednom programu.  
  
## <a name="notes-for-callers"></a>Poznámky pro volající  
 Volání [getthread –](../../../extensibility/debugger/reference/idebugstackframe2-getthread.md) k získání tohoto rozhraní představující aktuálně aktivních vláken.  
  
 Toto rozhraní je také použité při vytváření požadavku zarážek (viz [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)).  
  
 Při rozpoznávání zarážku hranice nebo chyba, vrátí toto rozhraní (viz [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md) a [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)).  
  
## <a name="methods-in-vtable-order"></a>Metody v tabulce Vtable pořadí  
 Následující tabulka uvádí metody `IDebugThread2`.  
  
|Metoda|Popis|  
|------------|-----------------|  
|[EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)|Načte seznam rámce zásobníku pro tento přístup z více vláken.|  
|[GetName –](../../../extensibility/debugger/reference/idebugthread2-getname.md)|Získá název vlákno.|  
|[Setthreadname –](../../../extensibility/debugger/reference/idebugthread2-setthreadname.md)|Nastaví název vlákno.|  
|[GetProgram](../../../extensibility/debugger/reference/idebugthread2-getprogram.md)|Získá program, ve kterém je spuštěna vlákna.|  
|[CanSetNextStatement](../../../extensibility/debugger/reference/idebugthread2-cansetnextstatement.md)|Určuje, zda lze nastavit další příkaz dané zásobníku rámec a kódu v kontextu.|  
|[SetNextStatement](../../../extensibility/debugger/reference/idebugthread2-setnextstatement.md)|Nastaví další příkaz dané zásobníku rámec a kódu v kontextu.|  
|[GetThreadId](../../../extensibility/debugger/reference/idebugthread2-getthreadid.md)|Získá identifikátor systému přístup z více vláken.|  
|[Pozastavit](../../../extensibility/debugger/reference/idebugthread2-suspend.md)|Pozastaví vlákna.|  
|[Obnovení](../../../extensibility/debugger/reference/idebugthread2-resume.md)|Obnoví vlákna.|  
|[GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md)|Získá vlastnosti, které popisují vlákna.|  
|[GetLogicalThread](../../../extensibility/debugger/reference/idebugthread2-getlogicalthread.md)|Získá logickou vlákno přidružené k této fyzické přístup z více vláken.|  
  
## <a name="remarks"></a>Poznámky  
 Protože jedním vláknem a fyzické můžete spustit v několika programy, více než jeden `IDebugThread2` z více než jeden program může představovat stejné fyzické vlákno.  
  
 Když dojde k zarážek nebo výjimky, událost je odeslána voláním [událostí](../../../extensibility/debugger/reference/idebugeventcallback2-event.md). Jeden z argumentů pro tuto metodu je `IDebugThread2` rozhraní představující aktuální vlákno. [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) slouží k získání [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) rozhraní pro aktuální rámec zásobníku.  
  
## <a name="requirements"></a>Požadavky  
 Záhlaví: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Viz také  
 [Základní rozhraní](../../../extensibility/debugger/reference/core-interfaces.md)   
 [Události](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)   
 [Getthread –](../../../extensibility/debugger/reference/idebugstackframe2-getthread.md)   
 [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)   
 [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)   
 [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)