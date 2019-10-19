---
title: 'Iactivescriptauthor –:: GetScriptTextAttributes | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptAuthor.GetScriptTextAttributes
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptAuthor::GetScriptTextAttributes
ms.assetid: a53451de-cc5c-4b53-8e5f-81e196364caf
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f89c7b654cc2ac7248598ee6498a3a290d17e2ef
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72563147"
---
# <a name="iactivescriptauthorgetscripttextattributes"></a>IActiveScriptAuthor::GetScriptTextAttributes
Vrátí atributy textu pro blok skriptu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetScriptTextAttributes(  
    LPCOLESTR        pszCode,  
    ULONG            cch,  
    LPCOLESTR        pszDelimiter,  
    DWORD            dwFlags,  
    SOURCE_TEXT_ATTR *pattr);  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pszCode`  
 [in, size_is (`cch`)] Text bloku skriptu Tento řetězec nemusí být ukončen znakem null.  
  
 `cch`  
 pro Velikost použitá pro parametry `pszCode` a `pattr`  
  
 `pszDelimiter`  
 pro Adresa oddělovače koncového skriptu. Pokud je `pszCode` analyzována z datového proudu, hostitel obvykle používá oddělovač (například dvě jednoduché uvozovky) k detekci konce skriptletu. Nastavte tento parametr na hodnotu NULL, pokud neexistuje oddělovač k identifikaci konce bloku skriptu.  
  
 `dwFlags`  
 pro Příznaky, které jsou spojeny s atributy textu bloku skriptu. Může být kombinací následujících hodnot:  
  
|Konstanta|Hodnota|Popis|  
|--------------|-----------|-----------------|  
|GETATTRTYPE_DEPSCAN|0x0001|Identifikujte identifikátory, které mají atribut SOURCETEXT_ATTR_IDENTIFIER, a Identifikujte operátory tečka, které mají atribut SOURCETEXT_ATTR_MEMBERLOOKUP.|  
|GETATTRFLAG_THIS|0x0100|Identifikujte aktuální objekt, který má atribut SOURCETEXT_ATTR_THIS.|  
|GETATTRFLAG_HUMANTEXT|0x8000|Identifikujte obsah řetězce a text komentáře s atributem SOURCETEXT_ATTR_HUMANTEXT.|  
  
 `pattr`  
 [in, out, size_is (`cch`)] Informace o barvách pro kód bloku skriptu.  
  
## <a name="return-value"></a>Návratová hodnota  
 @No__t_0. Možné hodnoty zahrnují hodnoty v následující tabulce, ale nejsou na ně omezeny.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`S_OK`|Metoda byla úspěšná.|  
  
## <a name="remarks"></a>Poznámky  
  
## <a name="see-also"></a>Viz také:  
 @No__t_1 [rozhraní iactivescriptauthor –](../../winscript/reference/iactivescriptauthor-interface.md)  
 [SOURCE_TEXT_ATTR – výčet](../../winscript/reference/source-text-attr-enumeration.md)