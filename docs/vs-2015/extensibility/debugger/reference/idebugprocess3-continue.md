---
title: 'IDebugProcess3:: Continue | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProcess3::Continue
helpviewer_keywords:
- IDebugProcess3::Continue
ms.assetid: 57506242-5763-4c08-adb9-8a78ce02cebb
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 92a36bb7e89d8afaa6d76f7d7b3772bd1714ffa7
ms.sourcegitcommit: a77158415da04e9bb8b33c332f6cca8f14c08f8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/15/2020
ms.locfileid: "86386235"
---
# <a name="idebugprocess3continue"></a>IDebugProcess3::Continue
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Pokračuje v běhu tohoto procesu ze stavu Zastaveno. Veškerý předchozí stav spuštění (například krok) se zachová a proces se začne znovu spouštět.  
  
> [!NOTE]
> Tato metoda by se měla použít místo [pokračování](../../../extensibility/debugger/reference/idebugprogram2-continue.md).  
  
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
 pro Objekt [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) představující vlákno, které se má pokračovat.  
  
## <a name="return-value"></a>Návratová hodnota  
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda se volá na tomto procesu bez ohledu na to, kolik procesů je právě laděno nebo který proces vygeneroval událost zastavení. Implementace musí uchovávat předchozí stav spuštění (například krok) a pokračovat v provádění, jako by se ještě nezastavila před dokončením předchozího spuštění. To znamená, že pokud vlákno v tomto procesu provádělo operaci převzetí operacemi krok za sebou a zastavilo se, protože se zastavil nějaký jiný proces a potom `Continue` byl volán, zadané vlákno musí dokončit původní operaci převzetí služeb.  
  
 **Upozornění** Neodesílat událost zastavení nebo okamžitou (synchronní) událost k [události](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) během zpracování tohoto volání; v opačném případě může ladicí program přestat reagovat.  
  
## <a name="see-also"></a>Viz také  
 [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [Událost](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
