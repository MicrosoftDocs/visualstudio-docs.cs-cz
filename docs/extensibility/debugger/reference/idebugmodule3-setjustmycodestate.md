---
title: IDebugModule3::SetJustMyCodeState | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugModule3::SetJustMyCodeState
helpviewer_keywords:
- IDebugModule3::SetJustMyCodeState
ms.assetid: 68f8166d-ef64-49ae-ad5e-79604f43bbd4
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 7b029c1c5209e752776e1cdf8a97fecdcc5bea10
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49888590"
---
# <a name="idebugmodule3setjustmycodestate"></a>IDebugModule3::SetJustMyCodeState
Označí modulu jako uživatelský kód, nebo ne.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT SetJustMyCodeState(  
   BOOL fIsUserCode  
);  
```  
  
```csharp  
int SetJustMyCodeState(  
   int fIsUserCode  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `fIsUserCode`  
 [in] Nenulová (`TRUE`), pokud modul by měl být uživatelský kód, hodnotu (`FALSE`) Pokud by neměla.  
  
## <a name="return-value"></a>Návratová hodnota  
 Pokud je úspěšná, vrátí `S_OK`; v opačném případě vrátí kód chyby.  
  
## <a name="see-also"></a>Viz také  
 [IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)