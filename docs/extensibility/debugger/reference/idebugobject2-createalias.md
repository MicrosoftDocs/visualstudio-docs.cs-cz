---
title: IDebugObject2::CreateAlias | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugObject2::CreateAlias
helpviewer_keywords:
- IDebugObject2::CreateAlias method
ms.assetid: 54a05920-5d13-4f67-962b-d1a7f013dff9
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 9a581b18dc331e1dd361554e1066cdbcb7b802a2
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49908506"
---
# <a name="idebugobject2createalias"></a>IDebugObject2::CreateAlias
Vytvoří jedinečné ID nebo alias pro tento objekt nebo vrátí existující alias.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT CreateAlias(  
   IDebugAlias** ppAlias  
);  
```  
  
```csharp  
int CreateAlias(  
   out IDebugAlias ppAlias  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppAlias`  
 [out] Nový (nebo existující) alias.  
  
## <a name="return-value"></a>Návratová hodnota  
 V případě úspěchu vrátí hodnotu S_OK; v opačném případě vrátí kód chyby.  
  
## <a name="remarks"></a>Poznámky  
 Alias je popisek, který představuje určitý objekt, pokud je objekt v paměti.  
  
## <a name="see-also"></a>Viz také  
 [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)   
 [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)