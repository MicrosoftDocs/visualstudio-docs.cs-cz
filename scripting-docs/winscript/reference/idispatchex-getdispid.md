---
title: 'IDispatchEx –:: GetDispID | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDispatchEx.GetDispID
apilocation:
- scrobj.dll
helpviewer_keywords:
- GetDispID method
ms.assetid: a288d63d-b08a-4540-9d9d-0bcd182eff9a
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 81bb33a1e793f38e15dc51b37c4fa062eb54e7fa
ms.sourcegitcommit: d281d2a04a5bc302650eebf369946d8f101e59dd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/12/2020
ms.locfileid: "88144530"
---
# <a name="idispatchexgetdispid"></a>IDispatchEx::GetDispID
Mapuje jeden název členu na jeho odpovídající identifikátor DISPID, který se pak může použít při následných voláních `IDispatchEx::InvokeEx` .  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetDispID(  
   BSTR bstrName,  
   DWORD grfdex,  
   DISPID *pid  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `bstrName`  
 Předaný název, který se má namapovat  
  
 `grfdex`  
 Určuje možnosti získání identifikátoru člena. Může se jednat o kombinaci následujících hodnot:  
  
|Hodnota|Význam|  
|-----------|-------------|  
|fdexNameCaseSensitive|Požaduje, aby se vyhledávání názvů provádělo způsobem, který rozlišuje velká a malá písmena. Může být ignorováno objektem, který nepodporuje vyhledávání citlivé na velká a malá písmena.|  
|fdexNameEnsure|Požaduje, aby byl člen vytvořen, pokud ještě neexistuje. Nový člen by měl být vytvořen s hodnotou `VT_EMPTY` .|  
|fdexNameImplicit|Indikuje, že volající vyhledává objekty pro člena určitého názvu, pokud není explicitně zadaný základní objekt.|  
|fdexNameCaseInsensitive|Požaduje, aby se vyhledávání názvů provádělo způsobem, který nerozlišuje velká a malá písmena. Může být ignorováno objektem, který nepodporuje vyhledávání bez rozlišování velkých a malých písmen.|  
  
 `pid`  
 Ukazatel na umístění přidělené volajícímu pro získání výsledku DISPID. Pokud dojde k chybě, `pid` obsahuje DISPID_UNKNOWN.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí jednu z následujících hodnot:  
  
|Hodnota|Význam|
|-|-|  
|`S_OK`|Úspěch.|  
|`E_OUTOFMEMORY`|Nedostatek paměti|  
|`DISP_E_UNKNOWNNAME`|Název nebyl znám.|  
  
## <a name="remarks"></a>Poznámky  
 `GetDispID`dá se použít místo `GetIDsOfNames` k získání DISPID pro daného člena.  
  
 Vzhledem k tomu `IDispatchEx` , že umožňuje přidání a odstranění členů, sada identifikátorů DISPID nezůstane pro životnost objektu konstantní.  
  
 Nepoužitý `riid` parametr v `IDispatch::GetIDsOfNames` byl odebrán.  
  
## <a name="example"></a>Příklad  
  
```cpp
BSTR bstrName;  
   DISPID dispid;  
   IDispatchEx *pdex;   
  
   // Assign to pdex and bstrName  
   pdex->GetDispID(bstrName, fdexNameCaseSensitive, &dispid);  
   // Use dispid  
```  
  
## <a name="see-also"></a>Viz také  
 [IDispatchEx – rozhraní](../../winscript/reference/idispatchex-interface.md)