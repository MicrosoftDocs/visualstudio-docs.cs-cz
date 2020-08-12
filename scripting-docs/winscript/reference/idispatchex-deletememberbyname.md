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
ms.openlocfilehash: cf62972b192d73bd130d15066d79ea70fe24beb8
ms.sourcegitcommit: d281d2a04a5bc302650eebf369946d8f101e59dd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/12/2020
ms.locfileid: "88144594"
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
  
|Hodnota|Význam|
|-|-|  
|`S_OK`|Úspěch.|  
|`S_FALSE`|Člen existuje, ale nelze jej odstranit.|  
  
## <a name="remarks"></a>Poznámky  
 Pokud je člen odstraněn, musí identifikátor DISPID zůstat platný pro `GetNextDispID` .  
  
 Pokud se člen s daným názvem odstraní a později se znovu vytvoří člen se stejným názvem, identifikátor DISPID by měl být stejný. (Zda jsou členy, které se liší pouze písmeny, jsou "stejné" závislé na objektu.)  
  
## <a name="example"></a>Příklad  
  
```cpp
BSTR bstrName;  
IDispatchEx *pdex;  
  
// Assign to pdex and bstrName  
pdex->DeleteMemberByName(bstrName, fdexNameCaseSensitive);  
```  
  
## <a name="see-also"></a>Viz také  
 [IDispatchEx – rozhraní](../../winscript/reference/idispatchex-interface.md)