---
title: IDebugMethodField::EnumStaticLocals | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugMethodField::EnumStaticLocals
helpviewer_keywords:
- IDebugMethodField::EnumStaticLocals method
ms.assetid: e0c522c4-f759-4c32-ae87-7abcb573e77d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 35474156ec43fb9e1e44117e44430b27a6e1b383
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49905087"
---
# <a name="idebugmethodfieldenumstaticlocals"></a>IDebugMethodField::EnumStaticLocals
Vytvoří čítač pro statické lokální proměnné metody.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT EnumStaticLocals(   
   IEnumDebugFields** ppLocals  
);  
```  
  
```csharp  
int EnumStaticLocals(  
   out IEnumDebugFields ppLocals  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppLocals`  
 [out] Vrátí [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) objekt představující seznam statické lokální proměnné. Vrátí hodnotu null, pokud neexistují žádné statické lokální proměnné.  
  
## <a name="return-value"></a>Návratová hodnota  
 V případě úspěchu vrátí hodnotu S_OK nebo vrátí S_FALSE v případě, že neexistují žádné statické lokální proměnné. V opačném případě vrátí kód chyby.  
  
## <a name="remarks"></a>Poznámky  
 Každý prvek je [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) objektu, který představuje různé druhy statické lokální proměnné. Volání [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) metoda na každém objektu k určení přesně jaký druh statické místní objekt představuje.  
  
## <a name="see-also"></a>Viz také  
 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)