---
title: Idebugexpressioncontext –::P arseLanguageText | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugExpressionContext.ParseLanguageText
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugExpressionContext::ParseLanguageText
ms.assetid: 650cb016-7d80-4011-b264-780f871a3466
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0493adde76e029088b637be3c6aaf02c55caaace
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573163"
---
# <a name="idebugexpressioncontextparselanguagetext"></a>IDebugExpressionContext::ParseLanguageText
Vytvoří výraz ladění pro zadaný text.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT ParseLanguageText(  
   LPCOLESTR           pstrCode,  
   UINT                nRadix,  
   LPCOLESTR           pstrDelimiter,  
   DWORD               dwFlags,  
   IDebugExpression**  ppe  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pstrCode`  
 pro Poskytuje text výrazu nebo příkazu (y).  
  
 `nRadix`  
 pro Číselná soustava, která se má použít.  
  
 `pstrDelimiter`  
 pro Oddělovač bloků na konci skriptu. Pokud je `pstrCode` analyzována z datového proudu, hostitel obvykle používá oddělovač, jako je například dvě jednoduché uvozovky (' ') k detekci konce bloku skriptu. Tento parametr určuje oddělovač, který hostitel použil, a umožňuje skriptovacímu stroji poskytovat nějaký podmíněný primitivní předzpracování (například nahrazení jednoduché uvozovky ['] dvěma jednoduchými uvozovkami pro použití jako oddělovače). Jak (a pokud) skriptovací stroj tyto informace používá, závisí na skriptovacím stroji. Nastavte tento parametr na `NULL`, pokud hostitel nepoužil oddělovač k označení konce bloku skriptu.  
  
 `dwFlags`  
 pro Kombinace následujících příznaků ladicího textu:  
  
|Konstanta|Hodnota|Popis|  
|--------------|-----------|-----------------|  
|DEBUG_TEXT_ISEXPRESSION|0x00000001|Označuje, že text je výraz na rozdíl od příkazu. Tento příznak může mít vliv na způsob, jakým je text analyzován některými jazyky.|  
|DEBUG_TEXT_RETURNVALUE|0x00000002|Pokud je vrácená hodnota k dispozici, bude ji volající používat.|  
|DEBUG_TEXT_NOSIDEEFFECTS|0x00000004|Nepovolit vedlejší účinky. Pokud je tento příznak nastaven, vyhodnocení výrazu by neměl změnit žádný běhový stav.|  
|DEBUG_TEXT_ALLOWBREAKPOINTS|0x00000008|Povoluje zarážky během vyhodnocování textu. Pokud tento příznak není nastaven, zarážky se při vyhodnocování textu ignorují.|  
|DEBUG_TEXT_ALLOWERRORREPORT|0x00000010|Umožňuje zprávy o chybách během vyhodnocování textu. Není-li tento příznak nastaven, chyby nebudou při vyhodnocování hlášeny hostiteli.|  
|DEBUG_TEXT_EVALUATETOCODECONTEXT|0x00000020|Určuje, že se má výraz vyhodnotit do kontextu kódu místo spuštění výrazu samotného.|  
  
 `ppe`  
 mimo Vrátí výraz Debug pro zadaný text.  
  
## <a name="return-value"></a>Návratová hodnota  
 Metoda vrací `HRESULT`. Možné hodnoty zahrnují hodnoty v následující tabulce, ale nejsou na ně omezeny.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`S_OK`|Metoda byla úspěšná.|  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda vytvoří výraz ladění pro zadaný text.  
  
## <a name="see-also"></a>Viz také:  
 [IDebugExpressionContext – rozhraní](../../winscript/reference/idebugexpressioncontext-interface.md)