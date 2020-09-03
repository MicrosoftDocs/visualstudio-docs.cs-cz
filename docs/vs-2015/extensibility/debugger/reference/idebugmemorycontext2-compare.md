---
title: 'IDebugMemoryContext2:: Compare | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugMemoryContext2::Compare
helpviewer_keywords:
- IDebugMemoryContext2::Compare method
- Compare method
ms.assetid: c51b5128-848e-4d8e-b2e9-1161339763c3
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 3eb48c324b5a1a918ab864c5eb4c4ca39eae41ac
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68163434"
---
# <a name="idebugmemorycontext2compare"></a>IDebugMemoryContext2::Compare
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Porovná kontext paměti s každým kontextem v daném poli způsobem uvedeným pomocí porovnání příznaků a vrátí index prvního kontextu, který odpovídá.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT Compare(   
   CONTEXT_COMPARE        compare,  
   IDebugMemoryContext2** rgpMemoryContextSet,  
   DWORD                  dwMemoryContextSetLen,  
   DWORD*                 pdwMemoryContext  
);  
```  
  
```csharp  
int Compare(  
   enum_CONTEXT_COMPARE   compare,   
   IDebugMemoryContext2[] rgpMemoryContextSet,   
   uint                   dwMemoryContextSetLen,   
   out uint               pdwMemoryContext  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `compare`  
 pro Hodnota z výčtu [CONTEXT_COMPARE](../../../extensibility/debugger/reference/context-compare.md) , která určuje typ porovnání.  
  
 `rgpMemoryContextSet`  
 pro Pole odkazů na objekty [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) , které mají být porovnány.  
  
 `dwMemoryContextSetLen`  
 pro Počet kontextů v `rgpMemoryContextSet` poli.  
  
 `pdwMemoryContext`  
 mimo Vrátí index prvního kontextu paměti, který splňuje porovnání.  
  
## <a name="return-value"></a>Návratová hodnota  
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby. Vrátí, `E_COMPARE_CANNOT_COMPARE` zda nelze porovnat dva kontexty.  
  
## <a name="remarks"></a>Poznámky  
 Ladicí stroj (de) nemusí podporovat všechny typy porovnávání, ale musí podporovat aspoň `CONTEXT_EQUAL` , `CONTEXT_LESS_THAN` `CONTEXT_GREATER_THAN` a `CONTEXT_SAME_SCOPE` .  
  
## <a name="see-also"></a>Viz také  
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)   
 [CONTEXT_COMPARE](../../../extensibility/debugger/reference/context-compare.md)
