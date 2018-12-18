---
title: IDispatchEx::DeleteMemberByName | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 5cb9a9dfd979954c42101fde41819d7e12db59e1
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24794592"
---
# <a name="idispatchexdeletememberbyname"></a>IDispatchEx::DeleteMemberByName
Odstraní členem podle názvu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT DeleteMemberByName(  
   BSTR bstrName,  
   DWORD grfdex  
  
```  
  
#### <a name="parameters"></a>Parametry  
 `bstrName`  
 Název člena odstranit.  
  
 `grfdex`  
 Určuje, zda název člena velká a malá písmena. To může být jeden z následujících hodnot:  
  
|Hodnota|Význam|  
|-----------|-------------|  
|fdexNameCaseSensitive|Požadavky, které vyhledání názvu provést způsobem malá a velká písmena. Můžete ignorovat objektem, který nepodporuje vyhledávání malá a velká písmena.|  
|fdexNameCaseInsensitive|Požadavky, které vyhledání názvu provést způsobem velká a malá písmena. Můžete ignorovat objektem, který nepodporuje vyhledávání bez rozlišování velikosti písmen.|  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí jednu z následujících hodnot:  
  
|||  
|-|-|  
|`S_OK`|Úspěch.|  
|`S_FALSE`|Člen existuje, ale nelze odstranit.|  
  
## <a name="remarks"></a>Poznámky  
 Pokud je tento člen bude odstraněn, DISPID musí jsou dál platné pro `GetNextDispID`.  
  
 Pokud se odstraní člena s daným názvem a později se znovu vytvoří člen se stejným názvem, musí být DISPID stejná. (Jestli členů, které se liší pouze v případě jsou "stejné" je závislé na objektu.)  
  
## <a name="example"></a>Příklad  
  
```  
BSTR bstrName;  
IDispatchEx *pdex;  
  
// Assign to pdex and bstrName  
pdex->DeleteMemberByName(bstrName, fdexNameCaseSensitive);  
```  
  
## <a name="see-also"></a>Viz také  
 [IDispatchEx – rozhraní](../../winscript/reference/idispatchex-interface.md)