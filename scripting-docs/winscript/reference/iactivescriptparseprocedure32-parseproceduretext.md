---
title: IActiveScriptParseProcedure32::P arseProcedureText | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: ede37171-2f1e-4467-a358-17bd4a4f1869
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: 52333d13731b5c31329ee812be403c09cf43d63b
ms.sourcegitcommit: 9a9c61ca115c22d33bb902153eb0853789c7be4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/02/2020
ms.locfileid: "85835729"
---
# <a name="iactivescriptparseprocedure32parseproceduretext"></a>IActiveScriptParseProcedure32::ParseProcedureText
Analyzuje daný postup kódu a přidá proceduru do oboru názvů.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT ParseProcedureText(  
    LPCOLESTR pstrCode,              // address of procedure text  
    LPCOLESTR pstrFormalParams,      // address of formal parameter names  
    LPCOLESTR pstrProcedureName,     // address of procedure name  
    LPCOLESTR pstrItemName,          // address of item name  
    IUnknown *punkContext,           // address of debugging context  
    LPCOLESTR pstrDelimiter,         // address of end-of-procedure delimiter  
    DWORD_PTR dwSourceContextCookie, // application-defined value for debugging  
    ULONG ulStartingLineNumber,      // starting line of the script  
    DWORD dwFlags,                   // procedure flags  
    IDispatch **ppdisp               // receives IDispatch pointer  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pstrCode`  
 pro Adresa textu procedury, kterou chcete vyhodnotit. Výklad tohoto řetězce závisí na skriptovacím jazyce.  
  
 `pstrFormalParams`  
 pro Adresa formálních názvů parametrů pro proceduru. Názvy parametrů musí být odděleny odpovídajícími oddělovači pro skriptovací modul. Názvy by neměly být uzavřeny v závorkách.  
  
 `pstrProcedureName`  
 pro Adresa názvu procedury, která se má analyzovat  
  
 `pstrItemName`  
 pro Adresa názvu položky, která poskytuje kontext, ve kterém má být procedura vyhodnocena. Pokud je tento parametr `NULL` , kód se vyhodnocuje v globálním kontextu skriptovacího modulu.  
  
 `punkContext`  
 pro Adresa objektu kontextu. Tento objekt je vyhrazen pro použití v ladicím prostředí, kde takový kontext může být poskytnut ladicím programem, který představuje aktivní kontext běhu. Pokud je tento parametr `NULL` , modul používá `pstrItemName` k identifikaci kontextu.  
  
 `pstrDelimiter`  
 pro Adresa oddělovače koncových procedur. Když `pstrCode` je analyzována z datového proudu, hostitel obvykle používá oddělovač, například dvě jednoduché uvozovky ('), ke zjištění konce procedury. Tento parametr určuje oddělovač, který hostitel použil, a umožňuje skriptovacímu stroji poskytovat nějaký podmíněný primitivní předzpracování (například nahrazení jednoduché uvozovky ['] dvěma jednoduchými uvozovkami pro použití jako oddělovače). Stejně tak, jak (a pokud) skriptovací stroj používá tyto informace, závisí na skriptovacím stroji. Nastavte tento parametr na, `NULL` Pokud hostitel nepoužil oddělovač k označení konce procedury.  
  
 `dwSourceContextCookie`  
 pro Hodnota definovaná aplikací, která se používá pro účely ladění.  
  
 `ulStartingLineNumber`  
 pro Hodnota založená na nule, která určuje, na který řádek bude analýza začínat.  
  
 `dwFlags`  
 pro Příznaky přidružené k proceduře Může být kombinací těchto hodnot:  
  
|Hodnota|Význam|  
|-----------|-------------|  
|SCRIPTPROC_ISEXPRESSION|Označuje, že kód v `pstrCode` je výraz, který představuje vrácenou hodnotu procedury. Ve výchozím nastavení může kód obsahovat výraz, seznam příkazů nebo cokoli jiného, co je povoleno v proceduře pomocí skriptovacího jazyka.|  
|SCRIPTPROC_IMPLICIT_THIS|Indikuje, že `this` je ukazatel zahrnutý v rozsahu procedury.|  
|SCRIPTPROC_IMPLICIT_PARENTS|Označuje, že rodiče `this` ukazatele jsou zahrnuti v rozsahu procedury.|  
  
 `ppdisp`  
 mimo Adresa ukazatele pro objekt obsahující globální metody a vlastnosti skriptu. Pokud skriptovací stroj takový objekt nepodporuje, `NULL` je vrácen.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí jednu z následujících hodnot:  
  
|Návratová hodnota|Význam|  
|------------------|-------------|  
|`S_OK`|Úspěch.|  
|`E_INVALIDARG`|Argument byl neplatný.|  
|`E_POINTER`|Byl zadán neplatný ukazatel.|  
|`E_NOTIMPL`|Tato metoda není podporována. Skriptovací stroj nepodporuje přidávání procedur do oboru názvů za běhu.|  
|`E_UNEXPECTED`|Volání nebylo očekáváno (například skriptovací stroj je v neinicializovaném nebo zavřeném stavu).|  
|`OLESCRIPT_E_SYNTAX`|V proceduře se stala Nespecifikovaná chyba syntaxe.|  
|`S_FALSE`|Skriptovací stroj nepodporuje objekt Dispatch; `ppdisp`parametr je nastaven na hodnotu `NULL` .|  
  
## <a name="remarks"></a>Poznámky  
 Během tohoto volání není vyhodnocen žádný kód skriptu; místo toho je procedura zkompilována do stavu skriptu, kde může být skript volán později.  
  
## <a name="see-also"></a>Viz také  
 [IActiveScriptParseProcedure32](../../winscript/reference/iactivescriptparseprocedure32.md)