---
title: IDispatchEx::GetDispID | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 93595cd2d0f88244866ab7363ecd68c6d8073b48
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24794868"
---
# <a name="idispatchexgetdispid"></a>IDispatchEx::GetDispID
Mapuje název jednoho člena na jeho odpovídající DISPID, který lze potom použít v následných volání `IDispatchEx::InvokeEx`.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
 HRESULT GetDispID(  
   BSTR bstrName,  
   DWORD grfdex,  
   DISPID *pid  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `bstrName`  
 Předaný název nejde mapovat.  
  
 `grfdex`  
 Určuje možnosti pro získání identifikátor členu. To může být kombinací následujícího:  
  
|Hodnota|Význam|  
|-----------|-------------|  
|fdexNameCaseSensitive|Požadavky, které vyhledání názvu provést způsobem malá a velká písmena. Může být ignorován objektem, který nepodporuje vyhledávání malá a velká písmena.|  
|fdexNameEnsure|Požadavky, aby člen lze vytvořit, pokud ještě neexistuje. Nový člen by měl být vytvořen s hodnotou `VT_EMPTY`.|  
|fdexNameImplicit|Označuje, že je volající hledání členem konkrétní název vybrané objekty v případě, že není explicitně zadán základní objekt.|  
|fdexNameCaseInsensitive|Požadavky, které vyhledání názvu provést způsobem velká a malá písmena. Může být ignorován objektem, který nepodporuje vyhledávání bez rozlišování velikosti písmen.|  
  
 `pid`  
 Ukazatel na přidělené volající umístění pro příjem DISPID výsledek. Pokud dojde k chybě, `pid` obsahuje DISPID_UNKNOWN.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí jednu z následujících hodnot:  
  
|||  
|-|-|  
|`S_OK`|Úspěch.|  
|`E_OUTOFMEMORY`|Nedostatek paměti.|  
|`DISP_E_UNKNOWNNAME`|Název nebyl znám.|  
  
## <a name="remarks"></a>Poznámky  
 `GetDispID`můžete použít místo `GetIDsOfNames` získat DISPID je daný člen.  
  
 Protože `IDispatchEx` umožňuje přidání a odstranění členů sadu hodnoty dispID nezůstávat konstantní po dobu jeho existence objektu.  
  
 Nepoužívané `riid` parametr v `IDispatch::GetIDsOfNames` byla odebrána.  
  
## <a name="example"></a>Příklad  
  
```  
BSTR bstrName;  
   DISPID dispid;  
   IDispatchEx *pdex;   
  
   // Assign to pdex and bstrName  
   pdex->GetDispID(bstrName, fdexNameCaseSensitive, &dispid);  
   // Use dispid  
```  
  
## <a name="see-also"></a>Viz také  
 [IDispatchEx – rozhraní](../../winscript/reference/idispatchex-interface.md)