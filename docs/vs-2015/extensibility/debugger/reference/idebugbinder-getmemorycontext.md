---
title: 'IDebugBinder:: GetMemoryContext | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugBinder::GetMemoryContext
helpviewer_keywords:
- IDebugBinder::GetMemoryContext method
ms.assetid: 801c5b60-acff-4822-b23d-e9c7bbca8a0f
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: db8d8d820c43d17194feda0bf228227a279dccc6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "62423410"
---
# <a name="idebugbindergetmemorycontext"></a>IDebugBinder::GetMemoryContext
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Tato metoda převede buď umístění objektu, nebo adresu paměti na kontext paměti.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT GetMemoryContext(   
   IDebugField*           pField,  
   DWORD                  dwConstant,  
   IDebugMemoryContext2** ppMemCxt  
);  
```  
  
```csharp  
int GetMemoryContext(  
   IDebugField              pField,   
   uint                     dwConstant,   
   out IDebugMemoryContext2 ppMemCxt  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pField`  
 pro [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) popisující objekt, který se má najít. IF `NULL` a `dwConstant` místo toho použít.  
  
 `dwConstant`  
 pro Adresa paměti konstanty, například 0x5000.  
  
 `ppMemCxt`  
 mimo Vrátí rozhraní [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) , které představuje adresu objektu, nebo adresu v paměti.  
  
## <a name="return-value"></a>Návratová hodnota  
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.  
  
## <a name="see-also"></a>Viz také  
 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)   
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
