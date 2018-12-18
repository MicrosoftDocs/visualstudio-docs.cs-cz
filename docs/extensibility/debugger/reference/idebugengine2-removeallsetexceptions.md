---
title: IDebugEngine2::RemoveAllSetExceptions | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugEngine2::RemoveAllSetExceptions
helpviewer_keywords:
- IDebugEngine2::RemoveAllSetExceptions
ms.assetid: 165fbe89-802d-4d99-85ca-c10fd6cccc09
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 5d569362de2e71a462bcfe90bd5c7180256f981b
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49921038"
---
# <a name="idebugengine2removeallsetexceptions"></a>IDebugEngine2::RemoveAllSetExceptions
Odebere seznam výjimek, integrovaném vývojovém prostředí má nastavit pro konkrétní architekturu za běhu nebo jazyk.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT RemoveAllSetExceptions(   
   REFGUID guidType  
);  
```  
  
```csharp  
int RemoveAllSetExceptions(   
   ref Guid guidType  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `guidType`  
 [in] Identifikátor GUID pro jazyk nebo identifikátor GUID pro ladicí stroj, který je specifický pro architekturu za běhu.  
  
## <a name="return-value"></a>Návratová hodnota  
 Pokud je úspěšná, vrátí `S_OK`; v opačném případě vrátí kód chyby.  
  
## <a name="remarks"></a>Poznámky  
 Výjimky odebrat touto metodou byly nastavené zásadami předchozích volání [SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md) metody.  
  
 Chcete-li odebrat určité výjimky, zavolejte [RemoveSetException](../../../extensibility/debugger/reference/idebugengine2-removesetexception.md) metody.  
  
## <a name="see-also"></a>Viz také  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)   
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)   
 [RemoveSetException](../../../extensibility/debugger/reference/idebugengine2-removesetexception.md)