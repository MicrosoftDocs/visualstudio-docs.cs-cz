---
title: 'IDebugObject:: IsReadOnly | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugObject::IsReadOnly
helpviewer_keywords:
- IDebugObject::IsReadOnly method
ms.assetid: c460f772-d08a-4b36-81f3-dff6a51a93fd
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 74b55895e440f900e59cd3b517e22dd8a0191414
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68159090"
---
# <a name="idebugobjectisreadonly"></a>IDebugObject::IsReadOnly
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Určuje, zda je tento objekt určen jen pro čtení.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT IsReadOnly(   
   BOOL* pfIsReadOnly  
);  
```  
  
```csharp  
int IsReadOnly(  
   out int pfIsReadOnly  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pfIsReadOnly`  
 mimo Vrátí nenulovou hodnotu ( `TRUE` ), pokud je tento objekt jen pro čtení; v opačném případě vrátí hodnotu nula ( `FALSE` ).  
  
## <a name="return-value"></a>Návratová hodnota  
 V případě úspěchu vrátí S_OK; v opačném případě vrátí kód chyby.  
  
## <a name="remarks"></a>Poznámky  
 Po vytvoření objektu jen pro čtení nemůže být jeho hodnota změněna.  
  
## <a name="see-also"></a>Viz také  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
