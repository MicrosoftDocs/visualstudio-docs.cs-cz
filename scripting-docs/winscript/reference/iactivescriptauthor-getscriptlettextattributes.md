---
title: IActiveScriptAuthor::GetScriptletTextAttributes | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptAuthor.GetScriptletTextAttributes
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptAuthor::GetScriptletTextAttributes
ms.assetid: 082edfce-6c5b-4e5e-b942-31b423a4fa1d
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b01fba7d0e8eb80fed51b1ff0ebd3a8816bacb01
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24793299"
---
# <a name="iactivescriptauthorgetscriptlettextattributes"></a>IActiveScriptAuthor::GetScriptletTextAttributes
Vrátí text atributy skriptletu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetScriptletTextAttributes(  
   LPCOLESTR pszCode,  
   ULONG cch,  
   LPCOLESTR pszDelimiter,  
   DWORD dwFlags,  
   SOURCE_TEXT_ATTR *pattr  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pszCode`  
 [v části size_is – (`cch`)] skriptlet text. Tento řetězec nebude muset mít hodnotu null byla ukončena.  
  
 `cch`  
 [v] Velikost použitá pro `pszCode` a `pattr` parametry.  
  
 `pszDelimiter`  
 [v] Adresa koncového skriptlet oddělovač. Když `pszCode` je analyzována z datového proudu textu, hostitel se většinou používá oddělovač (například dvě jednoduchých uvozovek), ke zjištění konec skriptletu. Tento parametr nastavte na hodnotu NULL, pokud žádný oddělovač slouží k identifikaci konec skriptletu.  
  
 `dwFlags`  
 [v] Příznaky, které jsou spojeny s atributy text skriptletu. Může být kombinací následující hodnoty.  
  
|Konstanta|Hodnota|Popis|  
|--------------|-----------|-----------------|  
|GETATTRTYPE_DEPSCAN|0x0001|Identifikujte identifikátory, které mají atribut SOURCETEXT_ATTR_IDENTIFIER a identifikovat tečkou operátory, které mají atribut SOURCETEXT_ATTR_MEMBERLOOKUP.|  
|GETATTRFLAG_THIS|0x0100|Určete aktuální objekt, který má atribut SOURCETEXT_ATTR_THIS.|  
|GETATTRFLAG_HUMANTEXT|0x8000|Řetězec obsahu a komentář text, který má atribut SOURCETEXT_ATTR_HUMANTEXT Identifikujte.|  
  
 `pattr`  
 [ve out size_is – (`cch`)] barva informace pro kód skriptlet.  
  
## <a name="return-value"></a>Návratová hodnota  
 `HRESULT`. Možné hodnoty zahrnují hodnoty v následující tabulce, ale nejsou na ně omezeny.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`S_OK`|Metoda byla úspěšná.|  
  
## <a name="remarks"></a>Poznámky  
  
## <a name="see-also"></a>Viz také  
 [Iactivescriptauthor – rozhraní](../../winscript/reference/iactivescriptauthor-interface.md)   
 [IActiveScriptAuthor::GetScriptTextAttributes](../../winscript/reference/iactivescriptauthor-getscripttextattributes.md)   
 [SOURCE_TEXT_ATTR – výčet](../../winscript/reference/source-text-attr-enumeration.md)