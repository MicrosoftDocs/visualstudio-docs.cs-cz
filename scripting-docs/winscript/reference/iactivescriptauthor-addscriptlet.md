---
title: IActiveScriptAuthor::AddScriptlet | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptAuthor.AddScriptlet
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptAuthor::AddScriptlet
ms.assetid: 879a6651-f187-4934-b130-c1247549900b
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b21f906a73a313bf775683ba63738adb25af0007
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24793290"
---
# <a name="iactivescriptauthoraddscriptlet"></a>IActiveScriptAuthor::AddScriptlet
Přidá skriptlet kód jako podřízená kořenové úrovni `IScriptNode` objektu. Na hostiteli plně kvalifikovaný název skriptletu může mít pouze dvě úrovně.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT AddScriptlet(  
   LPCOLESTR pszDefaultName,  
   LPCOLESTR pszCode,  
   LPCOLESTR pszItemName,  
   LPCOLESTR pszSubItemName,  
   LPCOLESTR pszEventName,  
   LPCOLESTR pszDelimiter,  
   DWORD dwCookie,  
   DWORD dwFlags  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pszDefaultName`  
 [v] Adresa pro přidružení skriptletu výchozí název.  
  
 `pszCode`  
 [v] Adresa skriptlet text.  
  
 `pszItemName`  
 [v] Adresa vyrovnávací paměti nejvyšší úrovně identifikátor skriptlet plně kvalifikovaný název na hostiteli.  
  
 `pszSubItemName`  
 [v] Adresa vyrovnávací paměti druhé úrovně identifikátor skriptlet plně kvalifikovaný název na hostiteli. Nastavte na hodnotu NULL, pokud má název pouze jedna úroveň.  
  
 `pszEventName`  
 [v] Adresa vyrovnávací paměť, která obsahuje název události, pro kterou je skriptletu obslužné rutiny události.  
  
 `pszDelimiter`  
 [v] Adresa koncového ze skriptu bloku oddělovač. Když `pszCode` je analyzována z datového proudu textu, hostitele se většinou používá oddělovač (například dvě jednoduchých uvozovek), na zjištění konce bloku skriptu. Tento parametr nastavte na hodnotu NULL, pokud oddělovač neoznačí konec bloku skriptu.  
  
 `dwCookie`  
 [v] Definované aplikací hodnota, která se používá k přidružení skriptletu objekt hostitele.  
  
 `dwFlags`  
 [v] Nepoužívá se.  
  
## <a name="return-value"></a>Návratová hodnota  
 `HRESULT`. Možné hodnoty zahrnují hodnoty v následující tabulce, ale nejsou na ně omezeny.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`S_OK`|Metoda byla úspěšná.|  
  
## <a name="remarks"></a>Poznámky  
  
## <a name="see-also"></a>Viz také  
 [Iactivescriptauthor – rozhraní](../../winscript/reference/iactivescriptauthor-interface.md)