---
title: IDebugComPlusSymbolProvider2::GetTypeFromToken | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IDebugComPlusSymbolProvider2::GetTypeFromToken
- GetTypeFromToken
ms.assetid: 4452bc5d-0225-40e0-a467-c472a5c7c4ee
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 14047f18979f45bf777274c640a90c54f26c27ca
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51791524"
---
# <a name="idebugcomplussymbolprovider2gettypefromtoken"></a>IDebugComPlusSymbolProvider2::GetTypeFromToken
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Získá typ zadané svůj token.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT GetTypeFromToken(  
   ULONG32       appDomain,  
   GUID          guidModule,  
   DWORD         tdToken,  
   IDebugField** ppField  
);  
```  
  
```csharp  
int GetTypeFromToken(  
   uint            appDomain,  
   Guid            guidModule,  
   uint            tdToken,  
   out IDebugField ppField  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `appDomain`  
 [in] Identifikátor domény aplikace.  
  
 `guidModule`  
 [in] Jedinečný identifikátor modulu.  
  
 `tdToken`  
 [in] Token typu, který se má načíst.  
  
 `ppField`  
 [out] Vrátí typ, který je reprezentován [IDebugField](../../../extensibility/debugger/reference/idebugfield.md).  
  
## <a name="return-value"></a>Návratová hodnota  
 Pokud je úspěšná, vrátí `S_OK`; v opačném případě vrátí kód chyby.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak pro tuto metodu implementovat **CDebugSymbolProvider** objekt, který zveřejňuje [IDebugComPlusSymbolProvider2](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2.md) rozhraní.  
  
```cpp#  
HRESULT CDebugSymbolProvider::GetTypeFromToken(  
    ULONG32 ulAppDomainID,  
    GUID guidModule,  
    DWORD tdToken,  
    IDebugField **ppField)  
{  
    HRESULT hr = E_FAIL;  
  
    METHOD_ENTRY( CDebugDynamicFieldSymbol::GetTypeFromToken );  
  
    ASSERT(IsValidObjectPtr(this, CDebugSymbolProvider));  
    ASSERT(IsValidWritePtr(ppField, IDebugField*));  
  
    Module_ID idModule(ulAppDomainID, guidModule);  
  
    IfFailGo( this->CreateClassType(idModule, tdToken, ppField) );  
  
Error:  
  
    METHOD_EXIT( CDebugDynamicFieldSymbol::GetTypeFromToken, hr );  
  
    return hr;  
}  
```  
  
## <a name="see-also"></a>Viz také  
 [IDebugComPlusSymbolProvider2](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2.md)

