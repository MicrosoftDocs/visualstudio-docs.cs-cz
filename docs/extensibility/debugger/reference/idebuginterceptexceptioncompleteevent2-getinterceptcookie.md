---
title: IDebugInterceptExceptionCompleteEvent2::GetInterceptCookie | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugInterceptExceptionCompleteEvent2::GetInterceptCookie
helpviewer_keywords:
- IDebugInterceptExceptionCompleteEvent2::GetInterceptCookie
ms.assetid: 07b20866-e598-4783-9ecc-6aa8625c8804
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 1f6c59c6fbca8b18e93e890264fbdf1ae8d050fd
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49846418"
---
# <a name="idebuginterceptexceptioncompleteevent2getinterceptcookie"></a>IDebugInterceptExceptionCompleteEvent2::GetInterceptCookie
Volá se po dokončení zpracování zachycené výjimky.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetInterceptCookie(  
   UINT64* pqwCookie  
);  
```  
  
```csharp  
int GetInterceptCookie(  
   out ulong pqwCookie  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pqwCookie`  
 [out] Jedinečná hodnota, která souvisí s tím rozdílem, která byla zachycena.  
  
## <a name="return-value"></a>Návratová hodnota  
 Pokud je úspěšná, vrátí `S_OK`; v opačném případě vrátí kód chyby.  
  
## <a name="remarks"></a>Poznámky  
 Po [interceptcurrentexception –](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md) metoda dokončí zpracování zachycené výjimky, pošle [IDebugInterceptExceptionCompleteEvent2](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md) událostí. Obslužnou rutinu můžete použít `GetInterceptCookie` metodu pro načtení jedinečnou hodnotu související s výjimkou (stejnou hodnotu předanou `InterceptCurrentException` metoda).  
  
## <a name="see-also"></a>Viz také  
 [Interceptcurrentexception –](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md)   
 [IDebugInterceptExceptionCompleteEvent2](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md)