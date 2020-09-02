---
title: 'IDebugStackFrame3:: GetUnwindCodeContext | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugStackFrame3::GetUnwindCodeContext
helpviewer_keywords:
- IDebugStackFrame3::GetUnwindCodeContext method
ms.assetid: b25f7e7d-2b24-48e4-93b3-829e61d73ebf
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c5a3fdaf9ca21841a43041f0ad5c1dc7b1507085
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "62546886"
---
# <a name="idebugstackframe3getunwindcodecontext"></a>IDebugStackFrame3::GetUnwindCodeContext
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Vrátí kontext kódu představující umístění v případě, že došlo k operaci unwind zásobníku.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT GetUnwindCodeContext(  
   IDebugCodeContext2 **ppCodeContext  
);  
```  
  
```csharp  
int GetUnwindCodeContext(  
   out IDebugCodeContext2 ppCodeContext  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppCodeContext`  
 mimo Vrátí objekt [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) , který představuje umístění kontextu kódu v případě, že došlo k odvíjení zásobníku.  
  
## <a name="return-value"></a>Návratová hodnota  
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.  
  
## <a name="remarks"></a>Poznámky  
 I když tato metoda může vracet kontext kódu pro umístění po unwind zásobníku, nemusí to nutně znamenat, že unwind zásobníku může být skutečně v aktuálním bloku zásobníku.  
  
## <a name="see-also"></a>Viz také  
 [IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
