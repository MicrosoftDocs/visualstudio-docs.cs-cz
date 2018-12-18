---
title: IDebugExpressionContext::ParseLanguageText | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: e455768b7d38096c64ab61f2b36aeba871ddf0bc
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24794925"
---
# <a name="idebugexpressioncontextparselanguagetext"></a>IDebugExpressionContext::ParseLanguageText
Vytvoří výraz ladění pro zadaný text.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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
 [v] Poskytuje text výraz nebo příkazy.  
  
 `nRadix`  
 [v] Základ – používat.  
  
 `pstrDelimiter`  
 [v] Oddělovač koncový z skriptu blok. Když `pstrCode` je analyzována z datového proudu textu, hostitel se většinou používá oddělovač, například dvě jednoduché uvozovky ("), na zjištění konce bloku skriptu. Tento parametr určuje oddělovač, který se používá hostitele, která umožňuje skriptovací stroj zajistit některé podmíněného primitivní předběžného zpracování (například nahrazení jednoduché uvozovky ['] dvě jednoduchých uvozovek pro použití jako oddělovač). Přesně jak (a pokud) skriptovací stroj používá tyto informace závisí na skriptovacího stroje. Tento parametr nastavte na `NULL` Pokud hostitel nepoužili oddělovač konec bloku skriptu.  
  
 `dwFlags`  
 [v] Kombinace následující příznaky text ladění:  
  
|Konstanta|Hodnota|Popis|  
|--------------|-----------|-----------------|  
|DEBUG_TEXT_ISEXPRESSION|0x00000001|Označuje, že je text výrazu oproti příkaz. Tento příznak může mít vliv na způsob, ve kterém je analyzována text v některých jazycích.|  
|DEBUG_TEXT_RETURNVALUE|0x00000002|Pokud je k dispozici návratovou hodnotu, použije se volajícího.|  
|DEBUG_TEXT_NOSIDEEFFECTS|0x00000004|Nepovolit vedlejší účinky. Pokud je nastavený tento příznak, vyhodnocování výrazu by měl změnit žádné stav modulu runtime.|  
|DEBUG_TEXT_ALLOWBREAKPOINTS|0x00000008|Umožňuje zarážky během vyhodnocení textu. Pokud není nastavený tento příznak se ignorují zarážky během vyhodnocení textu.|  
|DEBUG_TEXT_ALLOWERRORREPORT|0x00000010|Umožňuje zprávy o chybách během vyhodnocení textu. Pokud není nastavený tento příznak pak chyby nejsou hlášeny hostitele během vyhodnocování.|  
|DEBUG_TEXT_EVALUATETOCODECONTEXT|0x00000020|Označuje výraz se má vyhodnotit pro kontext kódu než systémem samotného výrazu.|  
  
 `ppe`  
 [out] Vrací výraz ladění pro zadaný text.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí metodu `HRESULT`. Možné hodnoty zahrnují hodnoty v následující tabulce, ale nejsou na ně omezeny.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`S_OK`|Metoda byla úspěšná.|  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda vytvoří výraz ladění pro zadaný text.  
  
## <a name="see-also"></a>Viz také  
 [Idebugexpressioncontext – rozhraní](../../winscript/reference/idebugexpressioncontext-interface.md)