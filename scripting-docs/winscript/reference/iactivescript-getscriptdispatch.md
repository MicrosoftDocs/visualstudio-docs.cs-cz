---
title: IActiveScript::GetScriptDispatch | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScript.GetScriptDispatch
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_GetScriptDispatch
ms.assetid: 2092ccd4-1f4c-493a-b5b7-077a70ce95ca
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5b2f09934cf6d2bb28f7dae93d0bf49c8dc7437d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24791949"
---
# <a name="iactivescriptgetscriptdispatch"></a>IActiveScript::GetScriptDispatch
Načte `IDispatch` rozhraní pro metody a vlastnosti související s probíhající skriptu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetScriptDispatch(  
    LPCOLESTR pstrItemName  // address of item name  
    IDispatch **ppdisp      // receives IDispatch pointer  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pstrItemName`  
 [v] Adresa vyrovnávací paměť, která obsahuje název položky, pro niž je volající objekt přidružený odeslání. Pokud tento parametr je `NULL`, obsahuje objekt odeslání jako členy všechny globální metody a vlastnosti definované ve skriptu. Prostřednictvím `IDispatch` rozhraní a přidruženého `ITypeInfo` rozhraní, můžete vyvolání metody skriptu nebo zobrazení a úpravy skriptu proměnných hostitele.  
  
 `ppdisp`  
 [out] Adresa proměnné, která přijímá ukazatel na objekt přidružený ke skriptu globální metody a vlastnosti. Pokud skriptovací stroj nepodporuje takového objektu `NULL` je vrácen.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí jednu z následujících hodnot:  
  
|Návratová hodnota|Význam|  
|------------------|-------------|  
|`S_OK`|Úspěch.|  
|`E_INVALIDARG`|Argument byl neplatný.|  
|`E_POINTER`|Byl zadán neplatný ukazatel.|  
|`E_UNEXPECTED`|Nebyl očekáván volání (například skriptovací stroj ještě byla načtena nebo inicializovat).|  
|`S_FALSE`|Skriptovací stroj nepodporuje objekt odesílání; `ppdisp` parametr je nastaven na hodnotu NULL.|  
  
## <a name="remarks"></a>Poznámky  
 Protože metody a vlastnosti lze přidat při volání [IActiveScriptParse –](../../winscript/reference/iactivescriptparse.md) rozhraní, `IDispatch` rozhraní vrácená touto metodou dynamicky podporují nové metody a vlastnosti. Podobně `IDispatch::GetTypeInfo` metoda by měla vrátit na nové, jedinečné `ITypeInfo` rozhraní po přidání metody a vlastnosti. Upozorňujeme však, že nesmí změnit jazyk modulů `IDispatch` rozhraní v, které není kompatibilní s žádným předchozí `ITypeInfo` rozhraní vrátila. Znamená, například, že hodnoty dispID bude nikdy znovu použita.  
  
## <a name="see-also"></a>Viz také  
 [IActiveScript –](../../winscript/reference/iactivescript.md)