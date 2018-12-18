---
title: IDebugThread2::SetThreadName | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugThread2::SetThreadName
helpviewer_keywords:
- IDebugThread2::SetThreadName
ms.assetid: fa934121-3f58-44dc-9c30-d3f752e44c8b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 910f4f0f26295d8e826736aa24585a1e02b41e37
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49866282"
---
# <a name="idebugthread2setthreadname"></a>IDebugThread2::SetThreadName
Nastaví název vlákna.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT SetThreadName (   
   LPCOLESTR pszName  
);  
```  
  
```csharp  
int SetThreadName (   
   string pszName  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pszName`  
 [in] Název vlákna.  
  
## <a name="return-value"></a>Návratová hodnota  
 Pokud je úspěšná, vrátí `S_OK`; v opačném případě vrátí kód chyby.  
  
## <a name="remarks"></a>Poznámky  
 Získejte název vlákna, volání [GetName](../../../extensibility/debugger/reference/idebugthread2-getname.md) metody.  
  
## <a name="see-also"></a>Viz také  
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [GetName](../../../extensibility/debugger/reference/idebugthread2-getname.md)