---
title: IDispatchEx::GetNextDispID | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDispatchEx.GetNextDispID
apilocation:
- scrobj.dll
helpviewer_keywords:
- GetNextDispID method
ms.assetid: 8263d441-85ee-47f4-bdba-fbf2ad07e85f
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ece7bde3230da370c8434cef7f780a92604df34c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24794709"
---
# <a name="idispatchexgetnextdispid"></a>IDispatchEx::GetNextDispID
Vytvoří výčet členů objektu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetNextDispID(  
   DWORD grfdex,  
   DISPID id,  
   DISPID *pid  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `grfdex`  
 Určuje, které sadu položek vytvořit její výčet. To může být kombinací následujícího:  
  
|Hodnota|Význam|  
|-----------|-------------|  
|fdexEnumDefault|Požadavky, že objekt vytvoří výčet výchozí prvky. Objekt je dovoleno vytvořit výčet všech sadu elementů.|  
|fdexEnumAll|Požadavky na objekt zobrazí všechny elementy. Objekt je dovoleno vytvořit výčet všech sadu elementů.|  
  
 `id`  
 Určuje aktuálního člena. Getnextdispid – načte položku ve výčtu po touto. Používá getdispid – nebo předchozí volání getnextdispid – k získání tohoto identifikátoru. Používá hodnotu DISPID_STARTENUM získat první identifikátor první položka.  
  
 `pid`  
 Adresa DISPID proměnné, která přijímá identifikátor další položky ve výčtu.  
  
 Pokud je člen odstraní `DeleteMemberByName` nebo `DeleteMemberByDispID`, `DISPID` musí jsou dál platné pro `GetNextDispID`.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí jednu z následujících hodnot:  
  
|||  
|-|-|  
|`S_OK`|Úspěch.|  
|`S_FALSE`|Výčet provádí.|  
  
## <a name="example"></a>Příklad  
  
```  
HRESULT hr;  
   BSTR bstrName;  
   DISPID dispid;  
   IDispatchEx *pdex;  
  
   // Assign to pdex  
   hr = pdex->GetNextDispID(fdexEnumAll, DISPID_STARTENUM, &dispid);  
   while (hr == NOERROR)  
   {  
      hr = pdex->GetMemberName(dispid, &bstrName);  
      if (!wcscmp(bstrName, OLESTR("Bar")))  
      {  
         SysFreeString(bstrName);  
         return TRUE;  
      }  
      SysFreeString(bstrName);  
      hr = pdex->GetNextDispID(fdexEnumAll, dispid, &dispid);  
   }  
```  
  
## <a name="see-also"></a>Viz také  
 [IDispatchEx – rozhraní](../../winscript/reference/idispatchex-interface.md)   
 [IDispatchEx::GetDispID](../../winscript/reference/idispatchex-getdispid.md)   
 [IDispatchEx::GetNextDispID](#lrfidispatchexgetnextdispid)   
 [IDispatchEx::DeleteMemberByName](../../winscript/reference/idispatchex-deletememberbyname.md)   
 [IDispatchEx::DeleteMemberByDispID](../../winscript/reference/idispatchex-deletememberbydispid.md)