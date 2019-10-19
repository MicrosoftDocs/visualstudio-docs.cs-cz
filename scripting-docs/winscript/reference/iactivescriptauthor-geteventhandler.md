---
title: 'Iactivescriptauthor –:: geteventhandler | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: c69b32f0040ea6d52e0712b8e1813cc5a0b40c58
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576220"
---
# <a name="iactivescriptauthorgeteventhandler"></a>IActiveScriptAuthor::GetEventHandler
Vrátí skriptletu, který má zadané atributy.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
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
 pro Objekt `IDispatch`, který odpovídá `NamedItem`, ke kterému je připojen skriptletu.  
  
 `pszItem`  
 pro Adresa vyrovnávací paměti identifikátoru nejvyšší úrovně plně kvalifikovaného názvu skriptletu na hostiteli.  
  
 `pszSubItem`  
 pro Adresa vyrovnávací paměti identifikátoru druhé úrovně pro plně kvalifikovaný název skriptletu v hostiteli. Nastavte na hodnotu NULL, pokud má název jenom jednu úroveň.  
  
 `pszEvent`  
 pro Adresa vyrovnávací paměti, která obsahuje název události. Skriptletu je obslužná rutina události pro tuto událost.  
  
 `ppse`  
 mimo Adresa proměnné, která přijímá ukazatel na `IScriptEntry` rozhraní skriptletu, které má zadané atributy.  
  
## <a name="return-value"></a>Návratová hodnota  
 @No__t_0. Možné hodnoty zahrnují hodnoty v následující tabulce, ale nejsou na ně omezeny.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`S_OK`|Metoda byla úspěšná.|  
  
## <a name="remarks"></a>Poznámky  
  
## <a name="see-also"></a>Viz také:  
 @No__t_1 [rozhraní iactivescriptauthor –](../../winscript/reference/iactivescriptauthor-interface.md)  
 [IScriptEntry – rozhraní](../../winscript/reference/iscriptentry-interface.md)