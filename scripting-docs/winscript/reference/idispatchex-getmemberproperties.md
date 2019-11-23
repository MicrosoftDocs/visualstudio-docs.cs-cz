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
ms.openlocfilehash: 8016eef7b6e0da9b9fc88695db845cba7f608ff3
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574089"
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
 Identifikuje člena. K získání identifikátoru odeslání používá `GetDispID` nebo `GetNextDispID`.  
  
 `grfdexFetch`  
 Určuje, které vlastnosti se mají načíst. Může se jednat o kombinaci hodnot uvedených v části `pgrfdex` a/nebo kombinaci následujících hodnot:  
  
|Hodnota|Význam|  
|-----------|-------------|  
|grfdexPropCanAll|Kombinuje fdexPropCanGet, fdexPropCanPut, fdexPropCanPutRef, fdexPropCanCall, fdexPropCanConstruct a fdexPropCanSourceEvents.|  
|grfdexPropCannotAll|Kombinuje fdexPropCannotGet, fdexPropCannotPut, fdexPropCannotPutRef, fdexPropCannotCall, fdexPropCannotConstruct a fdexPropCannotSourceEvents.|  
|grfdexPropExtraAll|Kombinuje fdexPropNoSideEffects a fdexPropDynamicType.|  
|grfdexPropAll|Kombinuje grfdexPropCanAll, grfdexPropCannotAll a grfdexPropExtraAll.|  
  
 `pgrfdex`  
 Adresa `DWORD`, která přijímá požadované vlastnosti. Může se jednat o kombinaci následujících hodnot:  
  
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
  
|||  
|-|-|  
|`S_OK`|Nástup.|  
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
  
## <a name="see-also"></a>Viz také:  
   [rozhraní IDispatchEx –](../../winscript/reference/idispatchex-interface.md)  
 [IDispatchEx –:: GetDispID](../../winscript/reference/idispatchex-getdispid.md)   
 [IDispatchEx::GetNextDispID](../../winscript/reference/idispatchex-getnextdispid.md)