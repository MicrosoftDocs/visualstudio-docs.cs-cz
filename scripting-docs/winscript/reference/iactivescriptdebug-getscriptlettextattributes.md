---
title: 'Iactivescriptdebug –:: GetScriptletTextAttributes | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptDebug.GetScriptletTextAttributes
apilocation:
- jscript.dll
helpviewer_keywords:
- IActiveScriptDebug::GetScriptletTextAttributes
ms.assetid: b3990d86-5fdf-4c9f-9678-3f4b808c7ca8
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6a5dd9e219e51b001659225636396fe45ac815b9
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572808"
---
# <a name="iactivescriptdebuggetscriptlettextattributes"></a>IActiveScriptDebug::GetScriptletTextAttributes
Vrátí atributy textu pro libovolný skriptletu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetScriptletTextAttributes(  
   LPCOLESTR          pstrCode,  
   ULONG              uNumCodeChars,  
   LPCOLESTR          pstrDelimiter,  
   DWORD              dwFlags,  
   SOURCE_TEXT_ATTR*  pattr  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pstrCode`  
 pro Text skriptletu Tento řetězec nemusí být ukončený hodnotou null.  
  
 `uNumCodeChars`  
 pro Počet znaků v textu skriptletu  
  
 `pstrDelimiter`  
 pro Adresa oddělovače end-skriptletu. Pokud je `pstrCode` analyzována z datového proudu, hostitel obvykle používá oddělovač, jako je například dvě jednoduché uvozovky (' ') k detekci konce skriptletu. Tento parametr určuje oddělovač, který hostitel použil, a umožňuje skriptovacímu stroji poskytovat nějaký podmíněný primitivní předzpracování (například nahrazení jednoduché uvozovky ['] dvěma jednoduchými uvozovkami pro použití jako oddělovače). Jak (a pokud) skriptovací stroj tyto informace používá, závisí na skriptovacím stroji. Nastavte tento parametr na hodnotu NULL, pokud hostitel nepoužil oddělovač k označení konce skriptletu.  
  
 `dwFlags`  
 pro Příznaky přidružené k skriptletu. Může být kombinací těchto hodnot:  
  
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
  
 Toto volání je k dispozici, protože skriptlety by měl být výrazy a může mít jinou syntaxi než blok skriptu. Pokud mají stejnou syntaxi, implementace této metody bude shodná s implementací metody `GetScriptTextAttributes`.  
  
## <a name="see-also"></a>Viz také:  
 @No__t_1 [rozhraní iactivescriptdebug –](../../winscript/reference/iactivescriptdebug-interface.md)  
 [Iactivescriptdebug –:: GetScriptTextAttributes](../../winscript/reference/iactivescriptdebug-getscripttextattributes.md)    
 @No__t_1 [rozhraní IDebugDocumentText –](../../winscript/reference/idebugdocumenttext-interface.md)  
 [IDebugDocumentText –:: GetText](../../winscript/reference/idebugdocumenttext-gettext.md)    
 [SOURCE_TEXT_ATTR – výčet](../../winscript/reference/source-text-attr-enumeration.md)