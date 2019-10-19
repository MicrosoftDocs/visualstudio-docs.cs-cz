---
title: Iactivescriptparseprocedureold –::P arseProcedureText | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptParseProcedureOld.ParseProcedureText
apilocation:
- jscript.dll
helpviewer_keywords:
- IActiveScriptParseProcedureOld::ParseProcedureText
ms.assetid: 21a21313-35ce-432d-b9a6-7999065f19ac
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 116cbc7fac0d53b55c9766945d56ecebd27b6785
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577452"
---
# <a name="iactivescriptparseprocedureoldparseproceduretext"></a>IActiveScriptParseProcedureOld::ParseProcedureText
Analyzuje daný postup kódu a přidá anonymní proceduru do oboru názvů.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT ParseProcedureText(  
   LPCOLESTR    pstrCode,  
   LPCOLESTR    pstrFormalParams,  
   LPCOLESTR    pstrItemName,  
   IUnknown*    punkContext,  
   LPCOLESTR    pstrDelimiter,  
   DWORD_PTR    dwSourceContextCookie,  
   ULONG        ulStartingLineNumber,  
   DWORD        dwFlags,  
   IDispatch**  ppdisp  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pstrCode`  
 pro Text procedury k vyhodnocení. Výklad tohoto řetězce závisí na skriptovacím jazyce.  
  
 `pstrFormalParams`  
 pro Formální názvy parametrů pro proceduru. Názvy parametrů musí být odděleny odpovídajícími oddělovači pro skriptovací modul. Názvy by neměly být uzavřeny v závorkách.  
  
 `pstrItemName`  
 pro Název pojmenované položky, která poskytuje kontext, ve kterém má být procedura vyhodnocena. Pokud je tento parametr `NULL`, je kód vyhodnocen v globálním kontextu skriptovacího modulu.  
  
 `punkContext`  
 pro Objekt kontextu. Tento objekt je vyhrazen pro použití v ladicím prostředí, kde takový kontext může být poskytnut ladicím programem, který představuje aktivní kontext běhu. Pokud je tento parametr `NULL`, modul používá `pstrItemName` k identifikaci kontextu.  
  
 `pstrDelimiter`  
 pro Oddělovač koncových postupů. Pokud je `pstrCode` analyzována z datového proudu, hostitel obvykle používá oddělovač, jako je například dvě jednoduché uvozovky (' ') k detekci konce procedury. Tento parametr určuje oddělovač, který hostitel použil, a umožňuje skriptovacímu stroji poskytovat nějaký podmíněný, primitivní předzpracování (například nahrazení jednoduché uvozovky ['] dvěma jednoduchými uvozovkami pro použití jako oddělovač). Jak (a pokud) skriptovací stroj tyto informace používá, závisí na skriptovacím stroji. Nastavte tento parametr na `NULL`, pokud hostitel nepoužil oddělovač k označení konce procedury.  
  
 `dwSourceContextCookie`  
 pro Hodnota definovaná aplikací, která se používá pro účely ladění.  
  
 `ulStartingLineNumber`  
 pro Hodnota založená na nule, která určuje, na jakém řádku bude analýza zahájena.  
  
 `dwFlags`  
 pro Příznaky přidružené k proceduře Může být kombinací těchto hodnot.  
  
|Konstanta|Hodnota|Význam|  
|--------------|-----------|-------------|  
|SCRIPTPROC_ISEXPRESSION|0x00000020|Označuje, že kód v `pstrCode` je výraz, který představuje vrácenou hodnotu procedury.|  
|SCRIPTPROC_IMPLICIT_THIS|0x00000100|Označuje, že ukazatel `this` je zahrnut v rozsahu procedury.|  
|SCRIPTPROC_IMPLICIT_PARENTS|0x00000200|Označuje, že rodiče ukazatele `this` jsou součástí rozsahu procedury.|  
  
 `ppdisp`  
 mimo Vrátí obálku Dispatch, kde výchozí metoda je procedura analyzovaná touto metodou.  
  
## <a name="return-value"></a>Návratová hodnota  
 Metoda vrací `HRESULT`. Možné hodnoty zahrnují hodnoty v následující tabulce, ale nejsou na ně omezeny.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`S_OK`|Metoda byla úspěšná.|  
|`E_INVALIDARG`|Argument byl neplatný.|  
|`E_POINTER`|Byl zadán neplatný ukazatel.|  
|`E_NOTIMPL`|Tato metoda není podporována. Skriptovací stroj nepodporuje přidávání procedur do oboru názvů za běhu.|  
|`E_UNEXPECTED`|Volání nebylo očekáváno (například skriptovací stroj je v neinicializovaném nebo zavřeném stavu).|  
|`OLESCRIPT_E_SYNTAX`|V proceduře se stala Nespecifikovaná chyba syntaxe.|  
|`S_FALSE`|Skriptovací stroj nepodporuje objekt Dispatch; `ppdisp`parameter je nastavená na `NULL`.|  
  
## <a name="remarks"></a>Poznámky  
 Během tohoto volání není vyhodnocen žádný kód skriptu; místo toho je procedura zkompilována do metody na `ppdisp`, kde ji lze zavolat skriptem později.  
  
 Toto rozhraní je zastaralé namísto rozhraní `IActiveScriptParseProcedure`. Metoda `IActiveScriptParseProcedure::ParseProcedureText` je podobná této metodě, ale umožňuje zadání názvu procedury. Za všech okolností by se měla použít `IActiveScriptParseProcedure::ParseProcedureText`.  
  
## <a name="see-also"></a>Viz také:  
 @No__t_1 [rozhraní iactivescriptparseprocedureold –](../../winscript/reference/iactivescriptparseprocedureold-interface.md)  
 [IActiveScriptParseProcedure::ParseProcedureText](../../winscript/reference/iactivescriptparseprocedure-parseproceduretext.md)