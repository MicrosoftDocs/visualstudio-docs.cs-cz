---
title: IDispatchEx –::D eleteMemberByDispID | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDispatchEx.DeleteMemberByDispID
apilocation:
- scrobj.dll
helpviewer_keywords:
- DeleteMemberByDispID method
ms.assetid: f61231e5-ba93-4ac3-bde8-d363548356b3
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0c3dbb040e39fd15b77e42b2eaa9fb2cdda0b1b2
ms.sourcegitcommit: d281d2a04a5bc302650eebf369946d8f101e59dd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/12/2020
ms.locfileid: "88144633"
---
# <a name="idispatchexdeletememberbydispid"></a>IDispatchEx::DeleteMemberByDispID
Odstraní člena podle identifikátoru DISPID.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT DeleteMemberByDispID(  
    DISPID id  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `id`  
 Identifikátor člena. Pomocí `GetDispID` nebo `GetNextDispID` Získá identifikátor odeslání.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí jednu z následujících hodnot:  
  
|Hodnota|Význam|
|-|-|  
|`S_OK`|Úspěch.|  
|`S_FALSE`|Člen existuje, ale nelze jej odstranit.|  
  
## <a name="remarks"></a>Poznámky  
 Pokud je člen odstraněn, musí identifikátor DISPID zůstat platný pro `GetNextDispID` .  
  
 Pokud se člen s daným názvem odstraní a později se znovu vytvoří člen se stejným názvem, identifikátor DISPID by měl být stejný. (Zda se názvy členů, které se liší pouze písmeny, jsou závislé na objektu.)  
  
## <a name="example"></a>Příklad  
  
```cpp
BSTR bstrName;  
DISPID dispid;  
IDispatchEx *pdex;   
  
// Assign to pdex and bstrName  
if (SUCCEEDED(pdex->GetDispID(bstrName, fdexNameCaseSensitive, &dispid)))  
    pdex->DeleteMemberByDispID(dispid);  
```  
  
## <a name="see-also"></a>Viz také  
 [Rozhraní IDispatchEx –](../../winscript/reference/idispatchex-interface.md)   
 [IDispatchEx –:: GetDispID](../../winscript/reference/idispatchex-getdispid.md)   
 [IDispatchEx::GetNextDispID](../../winscript/reference/idispatchex-getnextdispid.md)