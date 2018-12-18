---
title: IActiveScriptAuthor::ParseScriptText | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptAuthor.ParseScriptText
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptAuthor::ParseScriptText
ms.assetid: ebe212e8-6789-423d-ad22-92be984dc7ad
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 13e81d96ae817b2117f12cb56fd59759f4c2b849
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24793245"
---
# <a name="iactivescriptauthorparsescripttext"></a>IActiveScriptAuthor::ParseScriptText
Analyzuje text skriptu, přidá text skriptu vytváření modul a vytvoří `IScriptEntry` objekt, který odpovídá blok skriptu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT ParseScriptText(  
   LPCOLESTR pszCode,  
   LPCOLESTR pszItemName,  
   LPCOLESTR pszDelimiter,  
   DWORD dwCookie,  
   DWORD dwFlags  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pszCode`  
 [v] Text skriptu analyzovat.  
  
 `pszItemName`  
 [v] Adresa vyrovnávací paměti, který obsahuje název položky přidružené k bloku skriptu.  
  
 `pszDelimiter`  
 [v] Adresa koncového ze skriptu bloku oddělovač. Když `pszCode` je analyzována z datového proudu textu, hostitele se většinou používá oddělovač (například dvě jednoduchých uvozovek), na zjištění konce bloku skriptu. Tento parametr nastavte na hodnotu NULL, pokud neexistuje žádný oddělovač pro identifikaci konec bloku skriptu.  
  
 `dwCookie`  
 [v] Hodnota definované aplikací, která souvisí s novým `IScriptEntry` objektu.  
  
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