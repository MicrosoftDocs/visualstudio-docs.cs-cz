---
title: IDebugExpressionEvaluator::GetMethodLocationProperty | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugExpressionEvaluator::GetMethodLocationProperty
helpviewer_keywords:
- IDebugExpressionEvaluator::GetMethodLocationProperty method
ms.assetid: 52c42a2e-f144-476b-8bef-442464c8fe8e
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f8391adf8fab0deda937cb49f5594aa5275a9ff7
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51738501"
---
# <a name="idebugexpressionevaluatorgetmethodlocationproperty"></a>IDebugExpressionEvaluator::GetMethodLocationProperty
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Tato metoda převede metoda umístění a posun na adresu paměti.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT GetMethodLocationProperty(   
   LPCOLESTR             upstrFullyQualifiedMethodPlusOffset,  
   IDebugSymbolProvider* pSymbolProvider,  
   IDebugAddress*        pAddress,  
   IDebugBinder*         pBinder,  
   IDebugProperty2**     ppProperty  
);  
```  
  
```csharp  
int GetMethodLocationProperty(  
   string               upstrFullyQualifiedMethodPlusOffset,   
   IDebugSymbolProvider pSymbolProvider,   
   IDebugAddress        pAddress,   
   IDebugBinder         pBinder,   
   out IDebugProperty2  ppProperty  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `upstrFullyQualifiedMethodPlusOffset`  
 [in] Metoda umístění a posun, vyjádřený jako řetězec.  
  
 `pSymbolProvider`  
 [in] Poskytovatel symbolů vyjádřený jako [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md) objektu.  
  
 `pAddress`  
 [in] Adresy v rámci metody, vyjádřené jako [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) objektu.  
  
 `pBinder`  
 [in] Vazač vyjádřený jako [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) objektu.  
  
 `ppProperty`  
 [out] Vrátí [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) rozhraní, které představuje adresu paměti.  
  
## <a name="return-value"></a>Návratová hodnota  
 Pokud je úspěšná, vrátí `S_OK`; v opačném případě vrátí kód chyby.  
  
## <a name="remarks"></a>Poznámky  
 Vrácené adresu je možné nastavit zarážku, třeba.  
  
 Bez ohledu na název `upstrFullyQualifiedMethodPlusOffset`, tento parametr je možné předat název metody částečně kvalifikované. V takovém případě vybrané metody je ten, který obklopuje `pAddress`. Jak tento parametr je interpretován je až po implementaci vyhodnocovací filtr výrazů a jazyk, který podporuje.  
  
## <a name="see-also"></a>Viz také  
 [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)

