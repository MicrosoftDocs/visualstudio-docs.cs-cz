---
title: 'IDebugProperty2:: GetMemoryBytes | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProperty2::GetMemoryBytes
helpviewer_keywords:
- IDebugProperty2::GetMemoryBytes
ms.assetid: b32042ed-7a06-4b4a-99ef-fe03b0aa61cc
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 77b58f247f2a7d12c5d39c4044c37e9c0782c947
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68193522"
---
# <a name="idebugproperty2getmemorybytes"></a>IDebugProperty2::GetMemoryBytes
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Získá bajty paměti, které tvoří hodnotu vlastnosti.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT GetMemoryBytes (   
   IDebugMemoryBytes2** ppMemoryBytes  
);  
```  
  
```csharp  
int GetMemoryBytes (   
   out IDebugMemoryBytes2 ppMemoryBytes  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppMemoryBytes`  
 mimo Vrátí objekt [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md) , který lze použít k načtení paměti, která obsahuje hodnotu vlastnosti.  
  
## <a name="return-value"></a>Návratová hodnota  
 V případě úspěchu vrátí `S_OK` . jinak vrátí kód chyby. Vrátí, `S_GETMEMORYBYTES_NO_MEMORY_BYTES` zda nejsou k dispozici žádné bajty paměti pro načtení.  
  
## <a name="see-also"></a>Viz také  
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)
