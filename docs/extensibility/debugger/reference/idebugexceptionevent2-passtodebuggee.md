---
title: IDebugExceptionEvent2::PassToDebuggee | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugExceptionEvent2::PassToDebuggee
helpviewer_keywords:
- IDebugExceptionEvent2::PassToDebuggee
ms.assetid: a20d0f0b-2ca0-4437-bd22-9213c81d2738
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3b1fb575299000e4b9ab894a4700fdf314d17d6c
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49832703"
---
# <a name="idebugexceptionevent2passtodebuggee"></a>IDebugExceptionEvent2::PassToDebuggee
Určuje, zda výjimky by měly být předány program laděn při provádění pokračuje, nebo pokud by měl být zahozeny výjimku.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT PassToDebuggee(  
   BOOL fPass  
);  
```  
  
```csharp  
int PassToDebuggee(  
   int fPass  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `fPass`  
 [in] Nenulová (`TRUE`) Pokud výjimky by měly být předány program laděn při provádění pokračuje nebo nula (`FALSE`) Pokud výjimky by měl být zahozeny.  
  
## <a name="return-value"></a>Návratová hodnota  
 Pokud je úspěšná, vrátí `S_OK`; v opačném případě vrátí kód chyby.  
  
## <a name="remarks"></a>Poznámky  
 Voláním této metody nezpůsobí skutečně jakýkoli kód, který se spustí v programu, který se právě ladí. Volání je pouze se nastavit stav pro další spuštění kódu. Například volání [CanPassToDebuggee](../../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md) metoda může vrátit `S_OK` s [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md).`dwState` pole nastaveno `EXCEPTION_STOP_SECOND_CHANCE`.  
  
 Rozhraní IDE se může zobrazit [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md) událostí a volání [pokračovat](../../../extensibility/debugger/reference/idebugprogram2-continue.md) metody. Ladicí stroj (DE) by měly mít výchozí chování pro zpracování v případě, pokud `PassToDebuggee` metoda není volána.  
  
## <a name="see-also"></a>Viz také  
 [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md)   
 [CanPassToDebuggee](../../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md)   
 [Continue](../../../extensibility/debugger/reference/idebugprogram2-continue.md)