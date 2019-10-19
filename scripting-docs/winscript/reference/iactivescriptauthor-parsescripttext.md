---
title: Iactivescriptauthor –::P arseScriptText | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 90d5ab0fa700ed29b5fb37b1c48617cedec871b9
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576141"
---
# <a name="iactivescriptauthorparsescripttext"></a>IActiveScriptAuthor::ParseScriptText
Analyzuje text skriptu, přidá text do modulu vytváření skriptů a vytvoří objekt `IScriptEntry`, který odpovídá bloku skriptu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
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
 pro Text skriptu, který se má analyzovat  
  
 `pszItemName`  
 pro Adresa vyrovnávací paměti, která obsahuje název položky přidružené k bloku skriptu.  
  
 `pszDelimiter`  
 pro Adresa oddělovače bloku koncových skriptů. Pokud je `pszCode` analyzována z datového proudu, hostitel obvykle používá oddělovač (například dvě jednoduché uvozovky) k detekci konce bloku skriptu. Nastavte tento parametr na hodnotu NULL, pokud neexistuje oddělovač k identifikaci konce bloku skriptu.  
  
 `dwCookie`  
 pro Hodnota definovaná aplikací, která je přidružená k novému objektu `IScriptEntry`.  
  
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