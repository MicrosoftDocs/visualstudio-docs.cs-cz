---
title: IDispatchEx –::D eleteMemberByName | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDispatchEx.DeleteMemberByName
apilocation:
- scrobj.dll
helpviewer_keywords:
- DeleteMemberByName method
ms.assetid: a01b4e6a-d989-4b29-bb3f-04554f8c39f7
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2abb562f65885ee1d12f2ec9b2300fcddd3be37b
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576613"
---
# <a name="idispatchexdeletememberbyname"></a>IDispatchEx::DeleteMemberByName
Odstraní člena podle názvu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT DeleteMemberByName(  
   BSTR bstrName,  
   DWORD grfdex  
  
```  
  
#### <a name="parameters"></a>Parametry  
 `bstrName`  
 Název člena, který se má odstranit  
  
 `grfdex`  
 Určuje, zda rozlišující název člena rozlišuje velká a malá písmena. Může to být jedna z následujících hodnot:  
  
|Hodnota|Význam|  
|-----------|-------------|  
|fdexNameCaseSensitive|Požaduje, aby se vyhledávání názvů provádělo způsobem, který rozlišuje velká a malá písmena. Může být ignorováno objektem, který nepodporuje vyhledávání citlivé na velká a malá písmena.|  
|fdexNameCaseInsensitive|Požaduje, aby se vyhledávání názvů provádělo způsobem, který nerozlišuje velká a malá písmena. Může být ignorováno objektem, který nepodporuje vyhledávání bez rozlišování velkých a malých písmen.|  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí jednu z následujících hodnot:  
  
|||  
|-|-|  
|`S_OK`|Nástup.|  
|`S_FALSE`|Člen existuje, ale nelze jej odstranit.|  
  
## <a name="remarks"></a>Poznámky  
 Pokud je člen odstraněn, musí identifikátor DISPID zůstat platný pro `GetNextDispID`.  
  
 Pokud se člen s daným názvem odstraní a později se znovu vytvoří člen se stejným názvem, identifikátor DISPID by měl být stejný. (Zda jsou členy, které se liší pouze písmeny, jsou "stejné" závislé na objektu.)  
  
## <a name="example"></a>Příklad  
  
```cpp
BSTR bstrName;  
IDispatchEx *pdex;  
  
// Assign to pdex and bstrName  
pdex->DeleteMemberByName(bstrName, fdexNameCaseSensitive);  
```  
  
## <a name="see-also"></a>Viz také:  
 [IDispatchEx – rozhraní](../../winscript/reference/idispatchex-interface.md)