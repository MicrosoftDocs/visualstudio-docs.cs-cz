---
title: IDebugEngine2::CauseBreak | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugEngine2::CauseBreak
helpviewer_keywords:
- IDebugEngine2::CauseBreak
ms.assetid: 17fe4698-b04e-4798-8412-80e0da60c387
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 08544fb80e1006dbed08e51689c1bb3b01212edb
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49820509"
---
# <a name="idebugengine2causebreak"></a>IDebugEngine2::CauseBreak
Požadavky, že všechny programy právě laděny ve tento ladicí stroj (DE) pro zastavení provádění příště, jeden z jejich vláken pokusí o spuštění.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT CauseBreak(   
   void   
);  
```  
  
```csharp  
int CauseBreak();  
```  
  
## <a name="return-value"></a>Návratová hodnota  
 Pokud je úspěšná, vrátí `S_OK`; v opačném případě vrátí kód chyby.  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda je asynchronní: [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md) události se odešle, když program další pokusy o spuštění po volání této metody.  
  
## <a name="see-also"></a>Viz také  
 [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)   
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)