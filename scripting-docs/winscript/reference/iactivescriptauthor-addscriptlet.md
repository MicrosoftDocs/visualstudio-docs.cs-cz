---
title: 'Iactivescriptauthor –:: AddScriptlet | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 3a349a848f282e6b3a228c7b17009e0261801be5
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577977"
---
# <a name="iactivescriptauthoraddscriptlet"></a>IActiveScriptAuthor::AddScriptlet
Přidá kód skriptletu jako podřízený objekt `IScriptNode` kořenové úrovně. V hostiteli může plně kvalifikovaný název skriptletu mít jenom dvě úrovně.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
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
 pro Adresa výchozího názvu, který se má přidružit k skriptletu.  
  
 `pszCode`  
 pro Adresa skriptletu textu  
  
 `pszItemName`  
 pro Adresa vyrovnávací paměti identifikátoru nejvyšší úrovně plně kvalifikovaného názvu skriptletu na hostiteli.  
  
 `pszSubItemName`  
 pro Adresa vyrovnávací paměti identifikátoru druhé úrovně pro plně kvalifikovaný název skriptletu v hostiteli. Nastavte na hodnotu NULL, pokud má název jenom jednu úroveň.  
  
 `pszEventName`  
 pro Adresa vyrovnávací paměti, která obsahuje název události, pro kterou je skriptletu obslužná rutina události.  
  
 `pszDelimiter`  
 pro Adresa oddělovače bloku koncových skriptů. Pokud je `pszCode` analyzována z datového proudu, hostitel obvykle používá oddělovač (například dvě jednoduché uvozovky) k detekci konce bloku skriptu. Nastavte tento parametr na hodnotu NULL, pokud oddělovač neoznačí konec bloku skriptu.  
  
 `dwCookie`  
 pro Hodnota definovaná aplikací, která se používá k přidružení skriptletu k objektu hostitele.  
  
 `dwFlags`  
 pro Nepoužívá se.  
  
## <a name="return-value"></a>Návratová hodnota  
 @No__t_0. Možné hodnoty zahrnují hodnoty v následující tabulce, ale nejsou na ně omezeny.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`S_OK`|Metoda byla úspěšná.|  
  
## <a name="remarks"></a>Poznámky  
  
## <a name="see-also"></a>Viz také:  
 [IActiveScriptAuthor – rozhraní](../../winscript/reference/iactivescriptauthor-interface.md)