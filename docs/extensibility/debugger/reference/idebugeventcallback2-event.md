---
title: IDebugEventCallback2::Event | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugEventCallback2::Event
helpviewer_keywords:
- IDebugEventCallback2::Event
ms.assetid: e5a3345b-d460-4e40-8f5b-3111c56a2ed9
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: dc61f6a8b2a8a069d0fb921e4dbfe631088b2925
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49913316"
---
# <a name="idebugeventcallback2event"></a>IDebugEventCallback2::Event
Odešle oznámení o událostech ladění.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT Event(   
   IDebugEngine2*  pEngine,  
   IDebugProcess2* pProcess,  
   IDebugProgram2* pProgram,  
   IDebugThread2*  pThread,  
   IDebugEvent2*   pEvent,  
   REFIID          riidEvent,  
   DWORD           dwAttrib  
);  
```  
  
```csharp  
int Event(   
   IDebugEngine2  pEngine,  
   IDebugProcess2 pProcess,  
   IDebugProgram2 pProgram,  
   IDebugThread2  pThread,  
   IDebugEvent2   pEvent,  
   ref Guid       riidEvent,  
   uint           dwAttrib  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pEngine`  
 [in] [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) objekt, který reprezentuje ladicího stroje (DE), který odesílá této události. Zavedenými je potřeba vyplnit tento parametr.  
  
 `pProcess`  
 [in] [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) objekt, který představuje proces, ve kterém dojde k události. Tento parametr je vyplněna aplikací správce ladění relace (SDM). Zavedenými vždycky předá pro tento parametr hodnotu null.  
  
 `pProgram`  
 [in] [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) objekt, který reprezentuje program, ve kterém dojde k této události. Pro většinu události, tento parametr není hodnotu null.  
  
 `pThread`  
 [in] [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) objekt, který reprezentuje vláken, ve kterém dojde k této události. Pro události zastavení, tento parametr nemůže mít hodnotu null, rámce zásobníku získaný z tohoto parametru.  
  
 `pEvent`  
 [in] [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) objekt, který představuje událost ladění.  
  
 `riidEvent`  
 [in] Identifikátor GUID, který identifikuje které události rozhraní získat z `pEvent` parametru.  
  
 `dwAttrib`  
 [in] Kombinace příznaků z [EVENTATTRIBUTES](../../../extensibility/debugger/reference/eventattributes.md) výčtu.  
  
## <a name="return-value"></a>Návratová hodnota  
 Pokud je úspěšná, vrátí `S_OK`; v opačném případě vrátí kód chyby.  
  
## <a name="remarks"></a>Poznámky  
 Při volání této metody `dwAttrib` parametru musí odpovídat hodnotě vrácené [GetAttributes –](../../../extensibility/debugger/reference/idebugevent2-getattributes.md) předaný způsob, jak volat u objektu události `pEvent` parametru.  
  
 Všechny výjimky ladění jsou odeslány asynchronně, bez ohledu na to, zda je událost samotné asynchronní nebo ne. Když Zavedenými volá tuto metodu, návratová hodnota neindikuje, zda událost byla zpracována, pouze to, zda byla přijata událost. Ve skutečnosti ve většině situací, události nebyl zpracován po návratu tato metoda.  
  
## <a name="see-also"></a>Viz také  
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [EVENTATTRIBUTES](../../../extensibility/debugger/reference/eventattributes.md)