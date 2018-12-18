---
title: IActiveScriptAuthor::GetEventHandler | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptAuthor.GetEventHandler
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptAuthor::GetEventHandler
ms.assetid: 87c7a71d-46b9-448c-b34d-394105e20982
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2b09f900162b6dba82696c946b53ab131691530c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24793266"
---
# <a name="iactivescriptauthorgeteventhandler"></a>IActiveScriptAuthor::GetEventHandler
Vrátí skriptlet, který má zadané atributy.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetEventHandler(  
   IDispatch          *pdisp,  
   LPCOLESTR          pszItem,  
   LPCOLESTR          pszSubItem,  
   LPCOLESTR          pszEvent,  
   IScriptEntry       **ppse  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pdisp`  
 [v] `IDispatch` Objekt, který odpovídá `NamedItem` skriptletu je připojen.  
  
 `pszItem`  
 [v] Adresa vyrovnávací paměti nejvyšší úrovně identifikátor skriptlet plně kvalifikovaný název na hostiteli.  
  
 `pszSubItem`  
 [v] Adresa vyrovnávací paměti druhé úrovně identifikátor skriptlet plně kvalifikovaný název na hostiteli. Nastavte na hodnotu NULL, pokud má název pouze jedna úroveň.  
  
 `pszEvent`  
 [v] Adresa vyrovnávací paměť, která obsahuje název události. Skriptletu je obslužné rutiny události pro tuto událost.  
  
 `ppse`  
 [out] Proměnné, která přijímá ukazatel na adresu `IScriptEntry` rozhraní skriptlet, který má zadané atributy.  
  
## <a name="return-value"></a>Návratová hodnota  
 `HRESULT`. Možné hodnoty zahrnují hodnoty v následující tabulce, ale nejsou na ně omezeny.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`S_OK`|Metoda byla úspěšná.|  
  
## <a name="remarks"></a>Poznámky  
  
## <a name="see-also"></a>Viz také  
 [Iactivescriptauthor – rozhraní](../../winscript/reference/iactivescriptauthor-interface.md)   
 [Iscriptentry – rozhraní](../../winscript/reference/iscriptentry-interface.md)