---
title: IDebugExpressionEvaluator2::P reloadModules | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugExpressionEvaluator2::PreloadModules
- PreloadModules
ms.assetid: bcf9b968-ee14-4a92-88ad-926268a44e03
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d6d7236f19032fa0767a050ac84afe4b4e1585f0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "62540235"
---
# <a name="idebugexpressionevaluator2preloadmodules"></a>IDebugExpressionEvaluator2::PreloadModules
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Předvede moduly určené zadaným poskytovatelem symbolů.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT PreloadModules (  
   IDebugSymbolProvider* pSym  
);  
```  
  
```csharp  
int PreloadModules (  
   IDebugSymbolProvider pSym  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pSym`  
 pro Zprostředkovatel symbolů, pro který budou moduly předem načteny.  
  
## <a name="return-value"></a>Návratová hodnota  
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.  
  
## <a name="remarks"></a>Poznámky  
 Tato volitelná metoda se používá při připojení k hostitelskému procesu. Udává možnost zahřívání v rámci připojení v EE.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak implementovat tuto metodu pro objekt **ExpressionEvaluatorPackage** , který zpřístupňuje rozhraní [IDebugExpressionEvaluator2](../../../extensibility/debugger/reference/idebugexpressionevaluator2.md) .  
  
```cpp#  
STDMETHODIMP ExpressionEvaluatorPackage::PreloadModules  
(  
    IDebugSymbolProvider *pSym  
)  
{  
    HRESULT hr = NOERROR;  
    RuntimeMemberDescriptor  * prtMemberDesc;  
    RuntimeClassDescriptor *prtClassDesc;  
    CComPtr<IDebugClassField> pClassField;  
    IfFalseGo(pSym,E_INVALIDARG);  
  
    prtMemberDesc = &(g_rgRTLangMembers[StandardModuleAttributeCtor]);  
    prtClassDesc = &(g_rgRTLangClasses[prtMemberDesc->rtParent]);  
    pSym->GetClassTypeByName(prtClassDesc->wszClassName, nmCaseSensitive, &pClassField);  
  
    pClassField = NULL;  
    prtMemberDesc = &(g_rgRTLangMembers[LoadAssembly]);  
    prtClassDesc = &(g_rgRTLangClasses[prtMemberDesc->rtParent]);  
    pSym->GetClassTypeByName(prtClassDesc->wszClassName, nmCaseSensitive, &pClassField);  
  
Error:  
    return hr;  
}  
```  
  
## <a name="see-also"></a>Viz také  
 [IDebugExpressionEvaluator2](../../../extensibility/debugger/reference/idebugexpressionevaluator2.md)
