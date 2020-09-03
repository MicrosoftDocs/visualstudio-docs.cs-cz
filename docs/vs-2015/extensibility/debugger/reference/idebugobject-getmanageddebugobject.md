---
title: 'IDebugObject:: GetManagedDebugObject | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugObject::GetManagedDebugObject
helpviewer_keywords:
- IDebugObject::GetManagedDebugObject method
ms.assetid: cb89692e-7657-47ff-846d-311943521951
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4f2917135f5e25648cf08cd9030e3fdf31aedb52
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68162477"
---
# <a name="idebugobjectgetmanageddebugobject"></a>IDebugObject::GetManagedDebugObject
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Vytvoří kopii spravovaného objektu v adresním prostoru ladicího stroje.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT GetManagedDebugObject(   
   IDebugManagedObject** ppObject  
);  
```  
  
```csharp  
int GetManagedDebugObject(  
   out IDebugManagedObject ppObject  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppObject`  
 mimo Vrátí objekt [IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md) představující nově vytvořený spravovaný objekt.  
  
## <a name="return-value"></a>Návratová hodnota  
 V případě úspěchu vrátí S_OK; v opačném případě vrátí kód chyby. Vrátí E_FAIL, pokud tento [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) nepředstavuje instanci třídy spravované hodnoty.  
  
## <a name="remarks"></a>Poznámky  
 Tento objekt [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) musí představovat instanci třídy spravované hodnoty, jako je například `System.Decimal` instance. Když máte místní kopii, režie [vyhodnocování](../../../extensibility/debugger/reference/idebugfunctionobject-evaluate.md) volání se eliminuje.  
  
## <a name="see-also"></a>Viz také  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)   
 [IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md)
