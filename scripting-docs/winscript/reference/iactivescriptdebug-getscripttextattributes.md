---
title: 'Iactivescriptdebug –:: GetScriptTextAttributes | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptDebug.GetScriptTextAttributes
apilocation:
- jscript.dll
helpviewer_keywords:
- IActiveScriptDebug::GetScriptTextAttributes
ms.assetid: 2e8bda34-db0c-4b2e-a17f-82c4e0dbbc8c
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 57bd466965f6431a1418df1aa56cf6a7bbbc78cc
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576922"
---
# <a name="iactivescriptdebuggetscripttextattributes"></a>IActiveScriptDebug::GetScriptTextAttributes
Vrátí atributy textu pro libovolný blok textu skriptu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetScriptTextAttributes(  
   LPCOLESTR          pstrCode,  
   ULONG              uNumCodeChars,  
   LPCOLESTR          pstrDelimiter,  
   DWORD              dwFlags,  
   SOURCE_TEXT_ATTR*  pattr  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pstrCode`  
 pro Text bloku skriptu Tento řetězec nemusí být ukončený hodnotou null.  
  
 `uNumCodeChars`  
 pro Počet znaků v textu bloku skriptu.  
  
 `pstrDelimiter`  
 pro Adresa oddělovače bloku koncových skriptů. Pokud je `pstrCode` analyzována z datového proudu, hostitel obvykle používá oddělovač, jako je například dvě jednoduché uvozovky (' ') k detekci konce bloku skriptu. Tento parametr určuje oddělovač, který hostitel použil, a umožňuje skriptovacímu stroji poskytovat nějaký podmíněný primitivní předzpracování (například nahrazení jednoduché uvozovky ['] dvěma jednoduchými uvozovkami pro použití jako oddělovače). Jak (a pokud) skriptovací stroj tyto informace používá, závisí na skriptovacím stroji. Nastavte tento parametr na hodnotu NULL, pokud hostitel nepoužil oddělovač k označení konce bloku skriptu.  
  
 `dwFlags`  
 pro Příznaky přidružené k bloku skriptu. Může být kombinací těchto hodnot:  
  
|Konstanta|Hodnota|Popis|  
|--------------|-----------|-----------------|  
|GETATTRTYPE_DEPSCAN|0x0001|Označuje, že identifikátory a operátory tečka by měly být identifikovány pomocí příznaků SOURCETEXT_ATTR_IDENTIFIER a SOURCETEXT_ATTR_MEMBERLOOKUP, v uvedeném pořadí.|  
|GETATTRFLAG_THIS|0x0100|Označuje, že identifikátor pro aktuální objekt by měl být identifikován pomocí příznaku SOURCETEXT_ATTR_THIS.|  
|GETATTRFLAG_HUMANTEXT|0x8000|Označuje, že se má označovat obsah řetězce a text komentáře pomocí příznaku SOURCETEXT_ATTR_HUMANTEXT.|  
  
 `pattr`  
 [in, out] Vyrovnávací paměť obsahující vracené atributy  
  
## <a name="return-value"></a>Návratová hodnota  
 Metoda vrací `HRESULT`. Možné hodnoty zahrnují hodnoty v následující tabulce, ale nejsou na ně omezeny.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`S_OK`|Metoda byla úspěšná.|  
  
## <a name="remarks"></a>Poznámky  
 Inteligentní hostitel, který implementuje rozhraní `IDebugDocumentText`, může tuto metodu použít k delegování volání metody `IDebugDocumentText::GetText`.  
  
 Tato metoda pro bloky skriptu; Metoda `GetScriptletTextAttributes` je určena pro skriptlety.  
  
## <a name="see-also"></a>Viz také:  
 @No__t_1 [rozhraní iactivescriptdebug –](../../winscript/reference/iactivescriptdebug-interface.md)  
 [Iactivescriptdebug –:: GetScriptletTextAttributes](../../winscript/reference/iactivescriptdebug-getscriptlettextattributes.md)    
 @No__t_1 [rozhraní IDebugDocumentText –](../../winscript/reference/idebugdocumenttext-interface.md)  
 [IDebugDocumentText –:: GetText](../../winscript/reference/idebugdocumenttext-gettext.md)    
 [SOURCE_TEXT_ATTR – výčet](../../winscript/reference/source-text-attr-enumeration.md)