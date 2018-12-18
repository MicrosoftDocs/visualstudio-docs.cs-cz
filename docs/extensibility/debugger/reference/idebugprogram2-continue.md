---
title: IDebugProgram2::Continue | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProgram2::Continue
helpviewer_keywords:
- IDebugProgram2::Continue
ms.assetid: e5a6e02a-d21b-4a03-a034-e8de1f71ce2e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8e776c91e68e4689c1cc6c54f17397eca495b493
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49832652"
---
# <a name="idebugprogram2continue"></a>IDebugProgram2::Continue
Dál spuštěním tohoto programu v zastaveném stavu. Všechny předchozí stav spuštění (například krok) se zachová, a program začne provádět znovu.  
  
> [!NOTE]
>  Tato metoda je zastaralá. Použití [pokračovat](../../../extensibility/debugger/reference/idebugprocess3-continue.md) metoda místo.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT Continue(   
   IDebugThread2* pThread  
);  
```  
  
```csharp  
int Continue(   
   IDebugThread2 pThread  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pThread`  
 [in] [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) objekt, který reprezentuje vlákna.  
  
## <a name="return-value"></a>Návratová hodnota  
 Pokud je úspěšná, vrátí `S_OK`; v opačném případě vrátí kód chyby.  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda je volána na tomto programu bez ohledu na to, kolik programy jsou právě laděny nebo program, který vygeneruje událostí ukončení. Implementaci musí zachovat předchozí stav provádění (například krok) a pokračovat v provádění, jako by měl nikdy zastavila před dokončením předchozích spuštění. To znamená pokud vlákno v tomto programu dělal překročení operace a byla zastavena, protože některé program zastaví a pak tato metoda se volala, program musí dokončit původní překročení.  
  
> [!WARNING]
>  Neodesílat událostí ukončení nebo okamžité (synchronní) události, která [události](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) při zpracování tohoto volání; v opačném případě ladicí program může přestat reagovat.  
  
## <a name="see-also"></a>Viz také  
 [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)   
 [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)