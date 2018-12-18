---
title: IActiveScriptParse::ParseScriptText | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 70d17807b47468f2238c0254cc39b339df616411
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24793434"
---
# <a name="iactivescriptparseparsescripttext"></a>IActiveScriptParse::ParseScriptText
Analyzuje skriptlet daného kódu, přidávání deklarace do oboru názvů a vyhodnocení kódu podle potřeby.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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
|`pstrCode`|[v] Adresa skriptlet text k vyhodnocení. Výklad tento řetězec závisí na skriptovací jazyk.|  
|`pstrItemName`|[v] Adresa název položky, která poskytuje kontext, ve kterém se má vyhodnotit skriptletu. Pokud tento parametr hodnotu NULL, vyhodnotí se kód v globálním kontextu skriptovacího stroje.|  
|`punkContext`|[v] Adresa objektu kontextu. Tento objekt je vyhrazený pro použití v prostředí ladění, kde může poskytovat takový kontext ladicí program k reprezentaci active kontextu spuštění. Pokud tento parametr hodnotu NULL, použije modul `pstrItemName` k identifikaci kontextu.|  
|`pstrDelimiter`|[v] Adresa koncového skriptlet oddělovač. Když `pstrCode` je analyzována z datového proudu textu, hostitel se většinou používá oddělovač, například dvě jednoduché uvozovky ("), ke zjištění konec skriptletu. Tento parametr určuje oddělovač, který se používá hostitele, která umožňuje skriptovací stroj zajistit některé podmíněného primitivní předběžného zpracování (například nahrazení jednoduché uvozovky ['] dvě jednoduchých uvozovek pro použití jako oddělovač). Přesně jak (a pokud) skriptovací stroj díky použití těchto informací závisí na skriptovacího stroje. Tento parametr nastavte na `NULL` Pokud hostitel nepoužili konec skriptletu oddělovač.|  
|`dwSourceContextCookie`|[v] Soubor cookie používá pro účely ladění.|  
|`ulStartingLineNumber`|[v] Počítaný od nuly hodnota, která určuje, které řádku analýza ve vyrovnaném bude zahájena v.|  
|`dwFlags`|[v] Příznaky přidružené skriptletu. Může být kombinací těchto hodnot:|  
  
|Hodnota|Význam|  
|-----------|-------------|  
|SCRIPTTEXT_ISEXPRESSION|Pokud mezi výpočetní výraz a příkaz rozdíl je důležitý, ale v skriptovací jazyk syntakticky nejednoznačný, tento příznak určuje, že skriptletu se budou interpretovat jako výraz, nikoli jako příkaz nebo seznam příkazů. Ve výchozím nastavení jsou příkazy předpokládá, pokud lze určit nejvhodnější syntaxe skriptlet textu.|  
|SCRIPTTEXT_ISPERSISTENT|Označuje, že pokud skriptovací stroj je uloženo měli uložit kódu přidaném během toto volání (například prostřednictvím volání `IPersist*::Save`), nebo pokud skriptovacího stroje resetován prostřednictvím přechod zpět na inicializovaný stav.|  
|SCRIPTTEXT_ISVISIBLE|Označuje, že by měly jít vidět text skriptu (a tedy volatelné název) jako globální metody v oboru názvů skriptu.|  
  
|||  
|-|-|  
|`pvarResult`|[out] Adresa vyrovnávací paměti, která přijímá výsledky zpracování skriptlet nebo `NULL` Pokud volající očekává žádný výsledek (to znamená, že není nastavena hodnota SCRIPTTEXT_ISEXPRESSION).|  
|`pexcepinfo`|[out] Adresa strukturu, která přijímá informace o výjimce. Pokud je tato struktura naplní `IActiveScriptParse::ParseScriptText` vrátí DISP_E_EXCEPTION.|  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí jednu z následujících hodnot:  
  
|Návratová hodnota|Význam|  
|------------------|-------------|  
|`S_OK`|Úspěch.|  
|`DISP_E_EXCEPTION`|Došlo k výjimce při zpracování skriptletu. `pexcepinfo` Parametr obsahuje informace o výjimce.|  
|`E_INVALIDARG`|Argument byl neplatný.|  
|`E_POINTER`|Byl zadán neplatný ukazatel.|  
|`E_NOTIMPL`|Tato metoda není podporována. Skriptovací stroj nepodporuje spuštění vyhodnocení výrazů nebo příkazy.|  
|`E_UNEXPECTED`|Nebyl očekáván volání (například skriptovací stroj je ve stavu Neinicializovaný nebo zavřená, nebo byl nastaven příznak SCRIPTTEXT_ISEXPRESSION a skriptovací stroj je inicializovaný stav).|  
|`OLESCRIPT_E_SYNTAX`|V skriptletu došlo k chybě neurčené syntaxe.|  
  
## <a name="remarks"></a>Poznámky  
 Pokud je skriptovací stroj inicializovaný stav, žádný kód se ve skutečnosti vyhodnotí během tohoto hovoru; Místo toho je takový kód zařazených do fronty a spustit, když skriptovacího stroje převedena do (nebo přes) spuštěného stavu. Protože provádění není povolená inicializovaný stav, jedná se o chybu mohli volat tuto metodu s příznakem SCRIPTTEXT_ISEXPRESSION v inicializovaný stav.  
  
 Skriptletu může být výraz, seznam příkazů nebo nic povolenou skriptovací jazyk. Například tato metoda se používá při vyhodnocení HTML \<skriptu > značku, která umožňuje příkazy, čímž provést, protože stránky HTML je vytvářen místo jejich kompilace do stavu skriptu.  
  
 Kód předaná této metodě musí být platný a dokončení část kódu. Například v jazyce VBScript není povolen volat tuto metodu jednou pro dílčí Function(x) a potom ještě jednou s `End Sub`. Analyzátor nesmí čekat na dokončení podprogramu druhé volání, ale spíš musíte vygenerovat Chyba analýzy protože deklaraci podprogramu se spustil, ale není dokončeno.  
  
 Další informace o skriptu stavy, najdete v části stavy modulu skriptu z [skriptovací stroje systému Windows](../../winscript/windows-script-engines.md).  
  
## <a name="see-also"></a>Viz také  
 [IActiveScriptParse –](../../winscript/reference/iactivescriptparse.md)