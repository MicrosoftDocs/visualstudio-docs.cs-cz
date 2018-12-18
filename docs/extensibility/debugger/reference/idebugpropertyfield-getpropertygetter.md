---
title: IDebugPropertyField::GetPropertyGetter | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugPropertyField::GetPropertyGetter
helpviewer_keywords:
- IDebugPropertyField::GetPropertyGetter method
ms.assetid: ab9f861a-42ad-4a82-9ae6-2606176f755a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6411be501847648eed1dfdfa28e8a77a250855b8
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49888422"
---
# <a name="idebugpropertyfieldgetpropertygetter"></a>IDebugPropertyField::GetPropertyGetter
Získá metody, která získá vlastnost.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetPropertyGetter(   
   IDebugMethodField** ppField  
);  
```  
  
```cpp  
int GetPropertyGetter(  
   out IDebugMethodField ppField  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppField`  
 [out] Vrátí [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md) objekt reprezentující metodu, která získá vlastnost.  
  
## <a name="return-value"></a>Návratová hodnota  
 V případě úspěchu vrátí hodnotu S_OK; v opačném případě vrátí kód chyby.  
  
## <a name="remarks"></a>Poznámky  
 Chcete-li získat metodu, která nastaví vlastnost [GetPropertySetter](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertysetter.md) volání metody.  
  
## <a name="see-also"></a>Viz také  
 [IDebugPropertyField](../../../extensibility/debugger/reference/idebugpropertyfield.md)   
 [GetPropertySetter](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertysetter.md)   
 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)