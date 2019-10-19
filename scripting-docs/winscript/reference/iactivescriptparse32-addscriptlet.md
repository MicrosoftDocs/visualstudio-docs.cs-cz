---
title: 'IActiveScriptParse32:: AddScriptlet | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fcf11eb2-8e71-4cca-afda-a91791c243ff
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: b48d89ce2c49bd971fe298d2b4773aad8b65e8c3
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72561693"
---
# <a name="iactivescriptparse32addscriptlet"></a>IActiveScriptParse32::AddScriptlet
Přidá do skriptu kód skriptletu. Tato metoda se používá v prostředích, kde je trvalý stav skriptu propojen s hostitelským dokumentem a hostitel je zodpovědný za obnovení skriptu, nikoli prostřednictvím rozhraní `IPersist*`. Hlavní příklady jsou skriptovací jazyky HTML, které umožňují připojení skriptlety kódu vloženého do dokumentu HTML k vnitřním událostem (například při kliknutí = "Button1. text =" Exit ").  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT AddScriptlet(  
    LPCOLESTR pstrDefaultName,       // address of default name of scriptlet  
    LPCOLESTR pstrCode,              // address of scriptlet text  
    LPCOLESTR pstrItemName,          // address of item name  
    LPCOLESTR pstrSubItemName,       // address of subitem name  
    LPCOLESTR pstrEventName,         // address of event name  
    LPCOLESTR pstrDelimiter,         // address of end-of-scriptlet delimiter  
    DWORD_PTR dwSourceContextCookie, // application-defined value for debugging  
    ULONG ulStartingLineNumber,      // starting line of the script  
    DWORD dwFlags,                   // scriptlet flags  
    BSTR *pbstrName,                 // address of actual name of scriptlet  
    EXCEPINFO *pexcepinfo            // address of exception information  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pstrDefaultName`  
 pro Adresa výchozího názvu, který se má přidružit k skriptletu. Pokud skriptletu neobsahuje informace o pojmenování (jako v předchozím příkladu klikněte výše), tento název se použije k identifikaci skriptletu. Pokud je tento parametr `NULL`, skriptovací stroj vytvoří jedinečný název, pokud je to nutné.  
  
 `pstrCode`  
 pro Adresa skriptletu textu, který se má přidat Výklad tohoto řetězce závisí na skriptovacím jazyce.  
  
 `pstrItemName`  
 pro Adresa vyrovnávací paměti, která obsahuje název položky přidružené k tomuto skriptletu. Tento parametr, kromě `pstrSubItemName`, identifikuje objekt, pro který je skriptletu obslužná rutina události.  
  
 `pstrSubItemName`  
 pro Adresa vyrovnávací paměti obsahující název `subobject` pojmenované položky, ke které je přidružen tento skriptletu; Tento název musí být nalezen v informacích o typu pojmenované položky. Tento parametr má hodnotu NULL, pokud má být skriptletu přidružen k pojmenované položce namísto `subitem`. Tento parametr, kromě `pstrItemName`, identifikuje konkrétní objekt, pro který je skriptletu obslužná rutina události.  
  
 `pstrEventName`  
 pro Adresa vyrovnávací paměti obsahující název události, pro kterou je skriptletu obslužná rutina události.  
  
 `pstrDelimiter`  
 pro Adresa oddělovače end-skriptletu. Pokud je parametr `pstrCode` analyzován z datového proudu, hostitel obvykle používá oddělovač, například dvě jednoduché uvozovky (' ') k detekci konce skriptletu. Tento parametr určuje oddělovač, který hostitel použil, a umožňuje skriptovacímu stroji poskytovat nějaký podmíněný primitivní předzpracování (například nahrazení jednoduché uvozovky ['] dvěma jednoduchými uvozovkami pro použití jako oddělovače). Stejně tak, jak (a pokud) skriptovací stroj používá tyto informace, závisí na skriptovacím stroji. Nastavte tento parametr na hodnotu NULL, pokud hostitel nepoužil oddělovač k označení konce skriptletu.  
  
 `dwSourceContextCookie`  
 pro Hodnota definovaná aplikací, která se používá pro účely ladění.  
  
 `ulStartingLineNumber`  
 pro Hodnota založená na nule, která určuje, na který řádek bude analýza začínat.  
  
 `dwFlags`  
 pro Příznaky přidružené k skriptletu. Může být kombinací následujících hodnot:  
  
|Návratová hodnota|Význam|  
|------------------|-------------|  
|SCRIPTTEXT_ISVISIBLE|Indikuje, že by měl být text skriptu viditelný (a proto se dá volat pomocí názvu) jako globální metoda v názvovém prostoru skriptu.|  
|SCRIPTTEXT_ISPERSISTENT|Označuje, že kód přidaný během tohoto volání by měl být uložen, pokud je uložen skriptovací stroj (například prostřednictvím volání `IPersist*::Save`), nebo pokud je skriptovací modul resetován pomocí přechodu zpět do inicializovaného stavu. Další informace o tomto stavu najdete v tématu stavy skriptovacího stroje.|  
  
 `pbstrName`,  
 mimo Skutečný název, který slouží k identifikaci skriptletu. To má být v pořadí podle priority: název explicitně zadaný v skriptletu textu, výchozí název zadaný v `pstrDefaultName` nebo jedinečný název, který je vysyntetizuje skriptovací stroj.  
  
 `pexcepinfo`,  
 mimo Adresa struktury obsahující informace o výjimce. Tato struktura by měla být vyplněna, pokud je vráceno DISP_E_EXCEPTION.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí jednu z následujících hodnot:  
  
|Návratová hodnota|Význam|  
|------------------|-------------|  
|`S_OK`|Nástup.|  
|`DISP_E_EXCEPTION`|Při analýze skriptletu došlo k výjimce. Parametr `pexcepinfo` obsahuje informace o výjimce.|  
|`E_INVALIDARG`|Argument byl neplatný.|  
|`E_NOTIMPL`|Tato metoda není podporována; skriptovací stroj nepodporuje přidávání skriptletyování událostí.|  
|`E_POINTER`|Byl zadán neplatný ukazatel.|  
|`E_UNEXPECTED`|Volání nebylo očekáváno (například skriptovací stroj ještě nebyl načten nebo inicializován), a proto selhal.|  
|`OLESCRIPT_E_INVALIDNAME`|Zadaný výchozí název není v tomto skriptovacím jazyce platný.|  
|`OLESCRIPT_E_SYNTAX`|V skriptletu došlo k nespecifikované chybě syntaxe.|  
  
## <a name="see-also"></a>Viz také:  
 [IActiveScriptParse32](../../winscript/reference/iactivescriptparse32.md)