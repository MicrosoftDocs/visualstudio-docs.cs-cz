---
title: IActiveScriptParse::AddScriptlet | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptParse.AddScriptlet
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptParse_AddScriptlet
ms.assetid: 824929f4-4dd3-473a-92d9-0b96acea2f14
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e854ac71dc36263d805160f9336e049856076ce5
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24793488"
---
# <a name="iactivescriptparseaddscriptlet"></a>IActiveScriptParse::AddScriptlet
Přidá skriptlet kód skriptu. Tato metoda se používá v prostředích, kde trvalý stav skriptu je vzájemně propojeny s dokumentem hostitele a hostitele je zodpovědná za obnovení skriptu, nikoli pomocí `IPersist*` rozhraní. Primární příkladů skriptovací jazyky HTML, které umožňují skriptlety kód vložený v dokumentu HTML, který má být připojené k vnitřní události (například ONCLICK="button1.text='Exit" ").  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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
 [v] Adresa pro přidružení skriptletu výchozí název. Pokud skriptletu neobsahuje informace o názvech (jako v předchozím příkladu ONCLICK), tento název se použije k identifikaci skriptletu. Pokud tento parametr je `NULL`, skriptovací stroj vyrábí jedinečný název, v případě potřeby.  
  
 `pstrCode`  
 [v] Adresa skriptlet textu k přidání. Výklad tento řetězec závisí na skriptovací jazyk.  
  
 `pstrItemName`  
 [v] Adresa vyrovnávací paměť, která obsahuje název položky přidružené k této skriptlet. Tento parametr, stejně jako `pstrSubItemName`, identifikuje objekt, pro kterou je skriptletu obslužné rutiny události.  
  
 `pstrSubItemName`  
 [v] Adresa vyrovnávací paměť, která obsahuje název `subobject` s názvem položky, které tento skriptlet souvisí; tento název je nutné nalézt ve informací o typu s názvem položky. Tento parametr hodnotu NULL, pokud má být přidružen k položce pojmenované místo skriptletu `subitem`. Tento parametr, stejně jako `pstrItemName`, určuje konkrétní objekt, pro kterou je skriptletu obslužné rutiny události.  
  
 `pstrEventName`  
 [v] Adresa vyrovnávací paměť, která obsahuje název události, pro kterou je skriptletu obslužné rutiny události.  
  
 `pstrDelimiter`  
 [v] Adresa koncového skriptlet oddělovač. Když `pstrCode` parametr je analyzována z datového proudu textu, hostitel se většinou používá oddělovač, například dvě jednoduché uvozovky ("), ke zjištění konec skriptletu. Tento parametr určuje oddělovač, který se používá hostitele, která umožňuje skriptovací stroj zajistit některé podmíněného primitivní předběžného zpracování (například nahrazení jednoduché uvozovky ['] dvě jednoduchých uvozovek pro použití jako oddělovač). Přesně jak (a pokud) skriptovací stroj díky použití těchto informací závisí na skriptovacího stroje. Tento parametr nastavte na hodnotu NULL, pokud hostitel nepoužili konec skriptletu oddělovač.  
  
 `dwSourceContextCookie`  
 [v] Hodnota definované aplikací, který se používá pro účely ladění.  
  
 `ulStartingLineNumber`  
 [v] Počítaný od nuly hodnota, která určuje, které řádku analýza ve vyrovnaném bude zahájena v.  
  
 `dwFlags`  
 [v] Příznaky přidružené skriptletu. Může být kombinací následujícího:  
  
|Návratová hodnota|Význam|  
|------------------|-------------|  
|SCRIPTTEXT_ISVISIBLE|Označuje, že by měly jít vidět text skriptu (a tedy volatelné název) jako globální metody v oboru názvů skriptu.|  
|SCRIPTTEXT_ISPERSISTENT|Označuje, že pokud skriptovací stroj je uloženo měli uložit kódu přidaném během toto volání (například prostřednictvím volání `IPersist*::Save`), nebo pokud skriptovacího stroje resetován prostřednictvím přechod zpět na inicializovaný stav. Další informace o tomto stavu najdete v části stavy modulu skriptu.|  
  
 `pbstrName` ,  
 [out] Použít k identifikaci skriptletu skutečný název. Toto je v pořadí podle priority: název v textu skriptlet explicitně určena, výchozí název uvedené v `pstrDefaultName`, nebo syntetizované skriptovací stroj jedinečný název.  
  
 `pexcepinfo` ,  
 [out] Adresa strukturu obsahující informace o výjimce. Tato struktura je nutné zadat DISP_E_EXCEPTION je vrácen.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí jednu z následujících hodnot:  
  
|Návratová hodnota|Význam|  
|------------------|-------------|  
|`S_OK`|Úspěch.|  
|`DISP_E_EXCEPTION`|Při analýze skriptletu došlo k výjimce. `pexcepinfo` Parametr obsahuje informace o výjimce.|  
|`E_INVALIDARG`|Argument byl neplatný.|  
|`E_NOTIMPL`|Tato metoda není podporovaná; Skriptovací stroj nepodporuje přidávání skriptlety vnořování událostí.|  
|`E_POINTER`|Byl zadán neplatný ukazatel.|  
|`E_UNEXPECTED`|Nebyl očekáván volání (například skriptovací stroj ještě byla načtena nebo inicializovat) a proto se nezdařilo.|  
|`OLESCRIPT_E_INVALIDNAME`|Zadaný výchozí název je neplatný v této skriptovací jazyk.|  
|`OLESCRIPT_E_SYNTAX`|V skriptletu došlo k chybě neurčené syntaxe.|  
  
## <a name="see-also"></a>Viz také  
 [IActiveScriptParse –](../../winscript/reference/iactivescriptparse.md)