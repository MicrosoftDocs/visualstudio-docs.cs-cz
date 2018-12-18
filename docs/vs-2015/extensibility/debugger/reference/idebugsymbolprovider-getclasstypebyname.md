---
title: IDebugSymbolProvider::GetClassTypeByName | Dokumentace Microsoftu
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
- IDebugSymbolProvider::GetClassTypeByName
helpviewer_keywords:
- IDebugSymbolProvider::GetClassTypeByName method
ms.assetid: 2c748909-51dc-49b7-b193-19f96fca1138
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ffb3f59996389ec093c872e41e828ac88aa702d7
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51789197"
---
# <a name="idebugsymbolprovidergetclasstypebyname"></a>IDebugSymbolProvider::GetClassTypeByName
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Tato metoda načte pole typu třídy, představující plně kvalifikovaný název třídy.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT GetClassTypeByName(   
   LPCOLESTR          pszClassName,  
   NAME_MATCH         nameMatch,  
   IDebugClassField** ppField  
);  
```  
  
```csharp  
int GetClassTypeByName(  
   string               pszClassName,   
   NAME_MATCH           nameMatch,   
   out IDebugClassField ppField  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pszClassName`  
 [in] Název třídy.  
  
 `nameMatch`  
 [in] Vybere typ shody, například velká a malá písmena. Hodnota z [NAME_MATCH](../../../extensibility/debugger/reference/name-match.md) výčtu.  
  
 `ppField`  
 [out] Vrátí typ třídy reprezentovaná [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) rozhraní.  
  
## <a name="return-value"></a>Návratová hodnota  
 Pokud je úspěšná, vrátí `S_OK`; v opačném případě vrátí kód chyby.  
  
## <a name="see-also"></a>Viz také  
 [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [NAME_MATCH](../../../extensibility/debugger/reference/name-match.md)   
 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)

