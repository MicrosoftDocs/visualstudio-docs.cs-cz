---
title: IDebugBinder3::GetTypeArguments | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugBinder3::GetTypeArguments
helpviewer_keywords:
- IDebugBinder3::GetTypeArguments method
ms.assetid: fa0c37a7-327f-463e-9a9d-bb3f534584cb
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6ed4e1863313dae173d6737970765ca3d5f0b0b3
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49879451"
---
# <a name="idebugbinder3gettypearguments"></a>IDebugBinder3::GetTypeArguments
Tato metoda načte seznam typů argumentů, které jsou přidružené k tomuto objektu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetTypeArguments(  
   UINT          skip,  
   UINT          count,  
   IDebugField** ppFields,  
   UINT*         pFetched  
);  
```  
  
```csharp  
int GetTypeArguments(  
   uint          skip,  
   uint          count,  
   IDebugField[] ppFields,  
   out uint      pFetched  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `skip`  
 [in] Počet polí, přejděte před získáním typy argumentů.  
  
 `count`  
 [in] Počet polí argument vrátit (také určuje velikost `ppFields` pole).  
  
 `ppFields`  
 [out v] Pole polí, která bude vyplněno při návratu tato metoda.  
  
 `pFetched`  
 [out] \(volitelné) Počet argumentů typu pole ve skutečnosti vrátí.  
  
## <a name="return-value"></a>Návratová hodnota  
 Pokud je úspěšná, vrátí `S_OK`; v opačném případě vrátí kód chyby.  
  
## <a name="remarks"></a>Poznámky  
 Počet typů argumentů, které lze získat předem s [gettypeargumentcount –](../../../extensibility/debugger/reference/idebugbinder3-gettypeargumentcount.md).  
  
## <a name="see-also"></a>Viz také  
 [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)   
 [GetTypeArgumentCount](../../../extensibility/debugger/reference/idebugbinder3-gettypeargumentcount.md)