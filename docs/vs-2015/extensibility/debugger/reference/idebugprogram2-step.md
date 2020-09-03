---
title: 'IDebugProgram2:: Step | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProgram2::Step
helpviewer_keywords:
- IDebugProgram2::Step
ms.assetid: e4c2ffce-9810-4088-8162-eac9ef04f2a9
caps.latest.revision: 17
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: dd9d314865eb2051b67d7c127a6c5cc2395b1863
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "86387223"
---
# <a name="idebugprogram2step"></a>IDebugProgram2::Step
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Provede krok.  
  
> [!NOTE]
> Tato metoda je zastaralá. Místo toho použijte metodu [Step](../../../extensibility/debugger/reference/idebugprocess3-step.md) .  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT Step(   
   IDebugThread2*  pThread,  
   STEPKIND        sk,  
   STEPUNIT        step  
);  
```  
  
```csharp  
int Step(   
   IDebugThread2  pThread,  
   enum_STEPKIND  sk,  
   enum_STEPUNIT  step  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pThread`  
 pro Objekt [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) , který představuje nejladěné vlákno.  
  
 `sk`  
 pro Hodnota z výčtu [STEPKIND](../../../extensibility/debugger/reference/stepkind.md) , která určuje druh kroku.  
  
 `step`  
 pro Hodnota z výčtu [STEPUNIT](../../../extensibility/debugger/reference/stepunit.md) , která určuje jednotku kroku (například podle příkazu nebo instrukce).  
  
## <a name="return-value"></a>Návratová hodnota  
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.  
  
## <a name="remarks"></a>Poznámky  
 V případě, že dojde ke synchronizaci vlákna nebo komunikaci mezi vlákny, by se měly spouštět další vlákna v programu při krokování určitého vlákna.  
  
> [!WARNING]
> Neodesílat událost zastavení nebo okamžitou (synchronní) událost k [události](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) během zpracování tohoto volání; v opačném případě může ladicí program přestat reagovat.  
  
## <a name="see-also"></a>Viz také  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)   
 [Událost](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
