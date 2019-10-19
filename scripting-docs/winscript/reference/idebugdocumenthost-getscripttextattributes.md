---
title: 'Idebugdocumenthost –:: GetScriptTextAttributes | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentHost.GetScriptTextAttributes
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugDocumentHost::GetScriptTextAttributes
ms.assetid: fe459d0d-937f-4176-be81-99d5cca121a1
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3b18f4f49fa157b78e4f1fd6c7766e929890a6c6
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72569202"
---
# <a name="idebugdocumenthostgetscripttextattributes"></a>IDebugDocumentHost::GetScriptTextAttributes
Vrátí atributy textu pro blok textu dokumentu.  
  
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
 pro Text bloku skriptu Tento řetězec nemusí být ukončen znakem null.  
  
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
|`E_NOTIMPL`|Hostitel používá pouze výchozí atributy.|  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda vrátí atributy textu pro libovolný blok textu dokumentu. Je přijatelné, aby hostitelé vraceli `E_NOTIMPL`. v takovém případě se použijí výchozí atributy.  
  
## <a name="see-also"></a>Viz také:  
 @No__t_1 [rozhraní idebugdocumenthost –](../../winscript/reference/idebugdocumenthost-interface.md)  
 [SOURCE_TEXT_ATTR – výčet](../../winscript/reference/source-text-attr-enumeration.md)