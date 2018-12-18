---
title: IDebugGenericParamField::GetFlags | Dokumentace Microsoftu
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
- GetFlags
- IDebugGenericParamField::GetFlags
ms.assetid: adcbbca1-8960-4c88-86b0-8b9467056c97
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 76ae283854bd8326f506ae4880af157ca95fbdbe
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51740701"
---
# <a name="idebuggenericparamfieldgetflags"></a>IDebugGenericParamField::GetFlags
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Získá příznaky pro tento obecný parametr.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT GetFlags(  
   DWORD* pdwFlags  
);  
```  
  
```csharp  
int GetFlags(  
   ref uint pdwFlags  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pdwFlags`  
 [out] Vrátí příznaky pro tento obecný parametr.  
  
## <a name="return-value"></a>Návratová hodnota  
 Pokud je úspěšná, vrátí `S_OK`; v opačném případě vrátí kód chyby.  
  
## <a name="remarks"></a>Poznámky  
 Tyto příznaky obsahují informace o různých zvláštní omezení.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak pro tuto metodu implementovat **CDebugGenericParamFieldType** objekt, který zveřejňuje [IDebugGenericParamField](../../../extensibility/debugger/reference/idebuggenericparamfield.md) rozhraní.  
  
```cpp#  
HRESULT CDebugGenericParamFieldType::GetFlags(DWORD *pdwFlags)  
{  
    HRESULT hr = S_OK;  
  
    METHOD_ENTRY( CDebugGenericParamFieldType::GetFlags );  
  
    IfFalseGo( pdwFlags, E_INVALIDARG );  
    IfFailGo( this->LoadProps() );  
    *pdwFlags = m_dwFlags;  
  
Error:  
  
    METHOD_EXIT( CDebugGenericParamFieldType::GetFlags, hr );  
    return hr;  
}  
```  
  
## <a name="see-also"></a>Viz také  
 [IDebugGenericParamField](../../../extensibility/debugger/reference/idebuggenericparamfield.md)

