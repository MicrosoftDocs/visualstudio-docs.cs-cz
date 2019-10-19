---
title: 'IActiveScript:: InterruptScriptThread | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScript.InterruptScriptThread
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_InterruptScriptThread
ms.assetid: 2304d035-6d39-4811-acd3-8a9640fdbef6
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a436f973df05b945c0939f3a593640f567774277
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577269"
---
# <a name="iactivescriptinterruptscriptthread"></a>IActiveScript::InterruptScriptThread
Přeruší provádění spuštěného vlákna skriptu (jímka události, okamžité provedení nebo vyvolání makra). Tato metoda se dá použít k ukončení skriptu, který se zablokuje (například v nekonečné smyčce). Dá se volat z nezákladních vláken, aniž by to mělo za následek nezákladní bublinový popisek pro hostování objektů nebo [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) metody.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT InterruptScriptThread(  
    SCRIPTTHREADID   stidThread,  // identifier of thread  
    const EXCEPINFO *pexcepinfo,  // receives error information  
    DWORD dwFlags  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `stidThread`  
 pro Identifikátor vlákna, které chcete přerušit, nebo jednu z následujících hodnot identifikátoru speciálního vlákna:  
  
|Hodnota|Význam|  
|-----------|-------------|  
|SCRIPTTHREADID_ALL|Všechna vlákna. Přerušení se aplikuje na všechny aktuálně probíhající metody skriptu. Všimněte si, že pokud volající nepožaduje, aby byl skript odpojený, další skriptovaná událost způsobí, že se kód skriptu znovu spustí voláním metody [IActiveScript:: SetScriptState](../../winscript/reference/iactivescript-setscriptstate.md) s příznakem SCRIPTSTATE_DISCONNECTED nebo SCRIPTSTATE_INITIALIZED. stanovenými.|  
|SCRIPTTHREADID_BASE|Základní vlákno; To znamená vlákno, ve kterém se vytvořila instance skriptovacího stroje.|  
|SCRIPTTHREADID_CURRENT|Aktuálně prováděné vlákno.|  
  
 `pexcepinfo`  
 pro Adresa `EXCEPINFO` struktury obsahující informace o chybě, které by měly být hlášeny na přerušený skript.  
  
 `dwFlags`  
 pro Příznaky možností přidružené k přerušení. Může to být jedna z těchto hodnot:  
  
|Hodnota|Význam|  
|-----------|-------------|  
|SCRIPTINTERRUPT_DEBUG|Pokud je tato podpora podporovaná, zadejte ladicí program skriptovacího stroje v aktuálním bodě spuštění skriptu.|  
|SCRIPTINTERRUPT_RAISEEXCEPTION|V případě, že jazyk skriptovacího stroje podporuje, skript vynechá výjimku. V opačném případě je metoda skriptu přerušena a kód chyby je vrácen volajícímu; To znamená, že zdroj události nebo makro původce.|  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí jednu z následujících hodnot:  
  
|Návratová hodnota|Význam|  
|------------------|-------------|  
|`S_OK`|Nástup.|  
|`E_INVALIDARG`|Argument byl neplatný.|  
|`E_POINTER`|Byl zadán neplatný ukazatel.|  
|`E_UNEXPECTED`|Volání nebylo očekáváno (například skriptovací stroj ještě nebyl načten nebo inicializován).|  
  
## <a name="see-also"></a>Viz také:  
 [IActiveScript](../../winscript/reference/iactivescript.md)