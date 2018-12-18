---
title: IDebugExpression2::Abort | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugExpression2::Abort
helpviewer_keywords:
- IDebugExpression2::Abort
ms.assetid: 4fcb712e-1bdb-4b75-a440-35cc79ee147e
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: fb0fccd72b787a3f7376c8f8a1257d314c2d905a
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51748239"
---
# <a name="idebugexpression2abort"></a>IDebugExpression2::Abort
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Tato metoda zruší asynchronní výraz vyhodnocení jako tím, že volání [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) metody.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT Abort(  
   void  
);  
```  
  
```csharp  
int Abort();  
```  
  
## <a name="return-value"></a>Návratová hodnota  
 Pokud je úspěšná, vrátí `S_OK`; v opačném případě vrátí kód chyby.  
  
## <a name="remarks"></a>Poznámky  
 Při vyhodnocení výrazu asynchronní zrušení, nebyla odeslána [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) události pro událost zpětného volání předána [připojit](../../../extensibility/debugger/reference/idebugprogram2-attach.md) nebo [připojit](../../../extensibility/debugger/reference/idebugengine2-attach.md) metody.  
  
## <a name="see-also"></a>Viz také  
 [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)   
 [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)   
 [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)

