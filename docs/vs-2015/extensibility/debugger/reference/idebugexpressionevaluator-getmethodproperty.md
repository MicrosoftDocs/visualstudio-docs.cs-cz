---
title: 'IDebugExpressionEvaluator:: GetMethodProperty | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugExpressionEvaluator::GetMethodProperty
helpviewer_keywords:
- IDebugExpressionEvaluator::GetMethodProperty method
ms.assetid: c394fe4d-eeb6-4feb-828c-098d84a6f1ba
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b84ac959241a8f68f4d9516879660b6414708731
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68155354"
---
# <a name="idebugexpressionevaluatorgetmethodproperty"></a>IDebugExpressionEvaluator::GetMethodProperty
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Tato metoda získá objekt vlastnosti, který obsahuje lokální hodnoty, argumenty a další vlastnosti metody.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT GetMethodProperty(   
   IDebugSymbolProvider* pSymbolProvider,  
   IDebugAddress*        pAddress,  
   IDebugBinder*         pBinder,  
   BOOL                  fIncludeHiddenLocals,  
   IDebugProperty2**     ppProperty  
);  
```  
  
```csharp  
int GetMethodProperty(  
   IDebugSymbolProvider pSymbolProvider,   
   IDebugAddress        pAddress,   
   IDebugBinder         pBinder,   
   int                  fIncludeHiddenLocals,   
   out IDebugProperty2  ppProperty  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pSymbolProvider`  
 pro Poskytovatele symbolů, který se má použít, vyjádřený jako objekt [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md) .  
  
 `pAddress`  
 pro Adresa v kódu vyjádřená jako objekt [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) , který by měl být přeložen na nejbližší obsahující funkci.  
  
 `pBinder`  
 pro Pořadač, který se má použít, vyjádřený jako objekt [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) .  
  
 `fIncludeHiddenLocals`  
 pro Nenulová ( `TRUE` ) znamená, že se mají zahrnout skrytá národní prostředí; nula ( `FALSE` ) znamená odnechat skrytá národní prostředí.  
  
 `ppProperty`  
 mimo Vrátí objekt [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) , který představuje metodu.  
  
## <a name="return-value"></a>Návratová hodnota  
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.  
  
## <a name="remarks"></a>Poznámky  
 Skryté lokální hodnoty jsou obvykle proměnné, které jsou generovány kompilátorem.  
  
## <a name="see-also"></a>Viz také  
 [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)   
 [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)   
 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
