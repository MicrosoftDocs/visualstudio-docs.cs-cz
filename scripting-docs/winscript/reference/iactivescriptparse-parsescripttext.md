---
title: IActiveScriptParse::P arseScriptText | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptParse.ParseScriptText
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptParse_ParseScriptText
ms.assetid: 2d237d6c-cc65-415b-8808-72791304a136
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b4f35b398a7348f4e2bdbaaa9ab3e322bf69ddb6
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72561618"
---
# <a name="iactivescriptparseparsescripttext"></a>IActiveScriptParse::ParseScriptText
Analyzuje daný kód skriptletu, přidává deklarace do oboru názvů a podle potřeby vyhodnocuje kód.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT ParseScriptText(  
    LPCOLESTR pstrCode,              // address of scriptlet text  
    LPCOLESTR pstrItemName,          // address of item name  
    IUnknown *punkContext,           // address of debugging context  
    LPCOLESTR pstrDelimiter,         // address of end-of-scriptlet delimiter  
    DWORD_PTR dwSourceContextCookie, // cookie for debugging  
    ULONG ulStartingLineNumber,      // starting line of the script  
    DWORD dwFlags,                   // scriptlet flags  
    VARIANT *pvarResult,             // address of buffer for results  
    EXCEPINFO *pexcepinfo            // address of buffer for error data  
);  
```  
  
#### <a name="parameters"></a>Parametry  
  
|||  
|-|-|  
|`pstrCode`|pro Adresa skriptletu textu, který se má vyhodnotit Výklad tohoto řetězce závisí na skriptovacím jazyce.|  
|`pstrItemName`|pro Adresa názvu položky, která poskytuje kontext, ve kterém má být skriptletu vyhodnocena. Pokud má tento parametr hodnotu NULL, kód se vyhodnotí v globálním kontextu skriptovacího modulu.|  
|`punkContext`|pro Adresa objektu kontextu. Tento objekt je vyhrazen pro použití v ladicím prostředí, kde takový kontext může být poskytnut ladicím programem, který představuje aktivní kontext běhu. Pokud má tento parametr hodnotu NULL, modul používá `pstrItemName` k identifikaci kontextu.|  
|`pstrDelimiter`|pro Adresa oddělovače end-skriptletu. Pokud je `pstrCode` analyzována z datového proudu, hostitel obvykle používá oddělovač, jako je například dvě jednoduché uvozovky (' ') k detekci konce skriptletu. Tento parametr určuje oddělovač, který hostitel použil, a umožňuje skriptovacímu stroji poskytovat nějaký podmíněný primitivní předzpracování (například nahrazení jednoduché uvozovky ['] dvěma jednoduchými uvozovkami pro použití jako oddělovače). Stejně tak, jak (a pokud) skriptovací stroj používá tyto informace, závisí na skriptovacím stroji. Nastavte tento parametr na `NULL`, pokud hostitel nepoužil oddělovač k označení konce skriptletu.|  
|`dwSourceContextCookie`|pro Soubor cookie, který se používá pro účely ladění.|  
|`ulStartingLineNumber`|pro Hodnota založená na nule, která určuje, na který řádek bude analýza začínat.|  
|`dwFlags`|pro Příznaky přidružené k skriptletu. Může být kombinací těchto hodnot:|  
  
|Hodnota|Význam|  
|-----------|-------------|  
|SCRIPTTEXT_ISEXPRESSION|Je-li rozdíl mezi výpočetním výrazem a příkazem, který je důležitý, ale syntakticky dvojznačný ve skriptovacím jazyce, tento příznak určuje, že skriptletu má být interpretován jako výraz, nikoli jako příkaz nebo seznam příkazů. Ve výchozím nastavení se předpokládají příkazy, pokud nelze určit správnou volbu z syntaxe skriptletu textu.|  
|SCRIPTTEXT_ISPERSISTENT|Označuje, že kód přidaný během tohoto volání by měl být uložen, pokud je uložen skriptovací stroj (například prostřednictvím volání `IPersist*::Save`), nebo pokud je skriptovací modul resetován pomocí přechodu zpět do inicializovaného stavu.|  
|SCRIPTTEXT_ISVISIBLE|Indikuje, že by měl být text skriptu viditelný (a proto se dá volat pomocí názvu) jako globální metoda v názvovém prostoru skriptu.|  
  
|||  
|-|-|  
|`pvarResult`|mimo Adresa vyrovnávací paměti, která přijímá výsledky zpracování skriptletu, nebo `NULL`, pokud volající neočekává žádný výsledek (to znamená, že hodnota SCRIPTTEXT_ISEXPRESSION není nastavená).|  
|`pexcepinfo`|mimo Adresa struktury, která obdrží informace o výjimce. Tato struktura je vyplněna, pokud `IActiveScriptParse::ParseScriptText` vrátí DISP_E_EXCEPTION.|  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí jednu z následujících hodnot:  
  
|Návratová hodnota|Význam|  
|------------------|-------------|  
|`S_OK`|Nástup.|  
|`DISP_E_EXCEPTION`|Při zpracování skriptletu došlo k výjimce. Parametr `pexcepinfo` obsahuje informace o výjimce.|  
|`E_INVALIDARG`|Argument byl neplatný.|  
|`E_POINTER`|Byl zadán neplatný ukazatel.|  
|`E_NOTIMPL`|Tato metoda není podporována. Skriptovací stroj nepodporuje vyhodnocení za běhu výrazů nebo příkazů.|  
|`E_UNEXPECTED`|Volání nebylo očekáváno (například skriptovací stroj je v neinicializovaném nebo zavřeném stavu, nebo byl nastaven příznak SCRIPTTEXT_ISEXPRESSION a skriptovací stroj je v inicializovaném stavu).|  
|`OLESCRIPT_E_SYNTAX`|V skriptletu došlo k nespecifikované chybě syntaxe.|  
  
## <a name="remarks"></a>Poznámky  
 Pokud je skriptovací modul v inicializovaném stavu, nebude během tohoto volání vyhodnocen žádný kód. místo toho je tento kód zařazen do fronty a proveden při přechodu skriptovacího modulu do (nebo prostřednictvím) počátečního stavu. Vzhledem k tomu, že provádění není povoleno v inicializovaném stavu, jedná se o chybu při volání této metody s příznakem SCRIPTTEXT_ISEXPRESSION, pokud je v inicializovaném stavu.  
  
 Skriptletu může být výraz, seznam příkazů nebo cokoli, co povoluje skriptovací jazyk. Například tato metoda se používá při vyhodnocování značky HTML \<SCRIPT >, která umožňuje příkazy, které mají být provedeny při sestavování stránky HTML, nikoli pouze kompilování do stavu skriptu.  
  
 Kód předaný této metodě musí být platná kompletní část kódu. Například v jazyce VBScript není povoleno volat tuto metodu jednou pomocí dílčí funkce (x) a potom s `End Sub` podruhé. Analyzátor nesmí čekat na druhé volání k dokončení podrutiny, ale je nutné vygenerovat chybu analýzy, protože byla spuštěna deklarace subrutiny, ale nebyla dokončena.  
  
 Další informace o stavu skriptu najdete v části stavy skriptovacího stroje skriptovacích [strojů Windows](../../winscript/windows-script-engines.md).  
  
## <a name="see-also"></a>Viz také:  
 [IActiveScriptParse](../../winscript/reference/iactivescriptparse.md)