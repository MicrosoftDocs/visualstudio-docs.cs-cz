---
title: 'IDispatchEx –:: GetMemberProperties | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDispatchEx.GetMemberProperties
apilocation:
- scrobj.dll
helpviewer_keywords:
- GetMemberProperties method
ms.assetid: 20d43209-12e2-472a-9bf3-81eced137b71
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 488f8790ec25532fb611f18e8b24e7e7dba2e2f4
ms.sourcegitcommit: d281d2a04a5bc302650eebf369946d8f101e59dd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/12/2020
ms.locfileid: "88144544"
---
# <a name="idispatchexgetmemberproperties"></a>IDispatchEx::GetMemberProperties
Načte vlastnosti člena.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetMemberProperties(  
   DISPID id,  
   DWORD grfdexFetch,  
   DWORD *pgrfdex  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `id`  
 Identifikuje člena. Pomocí `GetDispID` nebo `GetNextDispID` Získá identifikátor odeslání.  
  
 `grfdexFetch`  
 Určuje, které vlastnosti se mají načíst. Může se jednat o kombinaci hodnot uvedených v části `pgrfdex` a/nebo kombinaci následujících hodnot:  
  
|Hodnota|Význam|  
|-----------|-------------|  
|grfdexPropCanAll|Kombinuje fdexPropCanGet, fdexPropCanPut, fdexPropCanPutRef, fdexPropCanCall, fdexPropCanConstruct a fdexPropCanSourceEvents.|  
|grfdexPropCannotAll|Kombinuje fdexPropCannotGet, fdexPropCannotPut, fdexPropCannotPutRef, fdexPropCannotCall, fdexPropCannotConstruct a fdexPropCannotSourceEvents.|  
|grfdexPropExtraAll|Kombinuje fdexPropNoSideEffects a fdexPropDynamicType.|  
|grfdexPropAll|Kombinuje grfdexPropCanAll, grfdexPropCannotAll a grfdexPropExtraAll.|  
  
 `pgrfdex`  
 Adresa `DWORD` , která přijímá požadované vlastnosti. Může se jednat o kombinaci následujících hodnot:  
  
|Hodnota|Význam|  
|-----------|-------------|  
|fdexPropCanGet|Člen lze získat pomocí DISPATCH_PROPERTYGET.|  
|fdexPropCannotGet|Člen nelze získat pomocí DISPATCH_PROPERTYGET.|  
|fdexPropCanPut|Člen lze nastavit pomocí DISPATCH_PROPERTYPUT.|  
|fdexPropCannotPut|Člen nelze nastavit pomocí DISPATCH_PROPERTYPUT.|  
|fdexPropCanPutRef|Člen lze nastavit pomocí DISPATCH_PROPERTYPUTREF.|  
|fdexPropCannotPutRef|Člen nelze nastavit pomocí DISPATCH_PROPERTYPUTREF.|  
|fdexPropNoSideEffects|Člen nemá žádné vedlejší účinky. Ladicí program může například bezpečně získat nebo nastavit nebo zavolat tento člen beze změny stavu laděného skriptu.|  
|fdexPropDynamicType|Člen je dynamický a může se změnit během životnosti objektu.|  
|fdexPropCanCall|Člen může být volán jako metoda pomocí DISPATCH_METHOD.|  
|fdexPropCannotCall|Člen nelze volat jako metodu pomocí DISPATCH_METHOD.|  
|fdexPropCanConstruct|Člen může být volán jako konstruktor pomocí DISPATCH_CONSTRUCT.|  
|fdexPropCannotConstruct|Člen nelze volat jako konstruktor pomocí DISPATCH_CONSTRUCT.|  
|fdexPropCanSourceEvents|Člen může aktivovat události.|  
|fdexPropCannotSourceEvents|Člen nemůže vyvolat události.|  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí jednu z následujících hodnot:  
  
|Hodnota|Význam|
|-|-|  
|`S_OK`|Úspěch.|  
|`DISP_E_UNKNOWNNAME`|Název nebyl znám.|  
  
## <a name="example"></a>Příklad  
  
```cpp
BSTR bstrName;  
   DISPID dispid;  
   IDispatchEx *pdex;   
   DWORD dwProps;  
  
   // Assign to pdex and bstrName  
   if (SUCCEEDED(pdex->GetDispID(bstrName, fdexNameCaseSensitive, &dispid)) &&  
      SUCCEEDED(pdex->GetMemberProperties(dispid, grfdexPropAll, &dwProps)) &&  
         (dwProps & fdexPropCanPut))  
   {  
      // Assign to member  
   }  
```  
  
## <a name="see-also"></a>Viz také  
 [Rozhraní IDispatchEx –](../../winscript/reference/idispatchex-interface.md)   
 [IDispatchEx –:: GetDispID](../../winscript/reference/idispatchex-getdispid.md)   
 [IDispatchEx::GetNextDispID](../../winscript/reference/idispatchex-getnextdispid.md)