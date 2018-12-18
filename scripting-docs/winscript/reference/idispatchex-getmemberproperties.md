---
title: IDispatchEx::GetMemberProperties | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 0d216bb7b21c8895337b9925007637c00d0deb37
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24795051"
---
# <a name="idispatchexgetmemberproperties"></a>IDispatchEx::GetMemberProperties
Načte vlastnosti člena.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetMemberProperties(  
   DISPID id,  
   DWORD grfdexFetch,  
   DWORD *pgrfdex  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `id`  
 Identifikuje člena. Používá `GetDispID` nebo `GetNextDispID` získat identifikátor odesílání.  
  
 `grfdexFetch`  
 Určuje vlastnosti, které chcete načíst. To může být kombinací hodnoty uvedené v `pgrfdex` nebo kombinaci těchto hodnot:  
  
|Hodnota|Význam|  
|-----------|-------------|  
|grfdexPropCanAll|Kombinuje fdexPropCanGet, fdexPropCanPut, fdexPropCanPutRef, fdexPropCanCall, fdexPropCanConstruct a fdexPropCanSourceEvents.|  
|grfdexPropCannotAll|Kombinuje fdexPropCannotGet, fdexPropCannotPut, fdexPropCannotPutRef, fdexPropCannotCall, fdexPropCannotConstruct a fdexPropCannotSourceEvents.|  
|grfdexPropExtraAll|Kombinuje fdexPropNoSideEffects a fdexPropDynamicType.|  
|grfdexPropAll|Kombinuje grfdexPropCanAll, grfdexPropCannotAll a grfdexPropExtraAll.|  
  
 `pgrfdex`  
 Adresa `DWORD` která přijme požadované vlastnosti. To může být kombinací následujícího:  
  
|Hodnota|Význam|  
|-----------|-------------|  
|fdexPropCanGet|Člen je možné získat pomocí DISPATCH_PROPERTYGET.|  
|fdexPropCannotGet|Člena nelze získat pomocí DISPATCH_PROPERTYGET.|  
|fdexPropCanPut|Člen se dá nastavit pomocí DISPATCH_PROPERTYPUT.|  
|fdexPropCannotPut|Člena nelze nastavit pomocí DISPATCH_PROPERTYPUT.|  
|fdexPropCanPutRef|Člen se dá nastavit pomocí DISPATCH_PROPERTYPUTREF.|  
|fdexPropCannotPutRef|Člena nelze nastavit pomocí DISPATCH_PROPERTYPUTREF.|  
|fdexPropNoSideEffects|Člen nemá žádné vedlejší účinky. Například ladicí program může bezpečně get/set nebo volání tento člen beze změny stavu laděné skriptu.|  
|fdexPropDynamicType|Člen je dynamická a můžete změnit v průběhu životnosti objektu.|  
|fdexPropCanCall|Člen je možné volat jako metodu pomocí DISPATCH_METHOD.|  
|fdexPropCannotCall|Člena nelze volat jako metodu pomocí DISPATCH_METHOD.|  
|fdexPropCanConstruct|Člen je možné volat jako konstruktor pomocí DISPATCH_CONSTRUCT.|  
|fdexPropCannotConstruct|Člena nelze volat jako konstruktor pomocí DISPATCH_CONSTRUCT.|  
|fdexPropCanSourceEvents|Člen můžete aktivovat události.|  
|fdexPropCannotSourceEvents|Člena nelze aktivovat události.|  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí jednu z následujících hodnot:  
  
|||  
|-|-|  
|`S_OK`|Úspěch.|  
|`DISP_E_UNKNOWNNAME`|Název nebyl znám.|  
  
## <a name="example"></a>Příklad  
  
```  
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
 [IDispatchEx – rozhraní](../../winscript/reference/idispatchex-interface.md)   
 [IDispatchEx::GetDispID](../../winscript/reference/idispatchex-getdispid.md)   
 [IDispatchEx::GetNextDispID](../../winscript/reference/idispatchex-getnextdispid.md)