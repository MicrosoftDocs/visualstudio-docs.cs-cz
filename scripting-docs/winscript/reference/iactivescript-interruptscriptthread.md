---
title: IActiveScript::InterruptScriptThread | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: ad717ee950dda4f0f0d7a14292f0f5f150ab4973
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24792081"
---
# <a name="iactivescriptinterruptscriptthread"></a>IActiveScript::InterruptScriptThread
Přerušuje provádění spuštěných vláken skriptu (jímky událostí, okamžité spuštění nebo volání makro). Tato metoda slouží k ukončení skript, který je zablokované (například v nekonečné smyčce). Může být volána z vláken není základní bez výsledkem není základní popisku na objekty hostitele nebo na [iactivescriptsite –](../../winscript/reference/iactivescriptsite.md) metoda.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT InterruptScriptThread(  
    SCRIPTTHREADID   stidThread,  // identifier of thread  
    const EXCEPINFO *pexcepinfo,  // receives error information  
    DWORD dwFlags  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `stidThread`  
 [v] Identifikátor vlákna na přerušení, nebo jeden z následujících hodnot identifikátoru speciální vláken:  
  
|Hodnota|Význam|  
|-----------|-------------|  
|SCRIPTTHREADID_ALL|Všechna vlákna. Přerušení, které se použijí na všechny metody skriptu právě probíhá. Všimněte si, že pokud volající vyžaduje odpojení skript, další skriptované událost způsobí, že kód skriptu znovu spustit při volání [IActiveScript::SetScriptState](../../winscript/reference/iactivescript-setscriptstate.md) metoda s SCRIPTSTATE_DISCONNECTED nebo Nastaven příznak SCRIPTSTATE_INITIALIZED.|  
|SCRIPTTHREADID_BASE|Základní podprocesu. To znamená, že byla vytvořena instance vláken, ve kterém skriptování modul.|  
|SCRIPTTHREADID_CURRENT|Aktuálně prováděné vlákno.|  
  
 `pexcepinfo`  
 [v] Adresa `EXCEPINFO` struktura obsahující informace o chybě, která by měla být oznámeny přerušených skriptu.  
  
 `dwFlags`  
 [v] Možnost příznaky, které jsou přidružené k přerušení. Může být jedna z těchto hodnot:  
  
|Hodnota|Význam|  
|-----------|-------------|  
|SCRIPTINTERRUPT_DEBUG|Pokud podporován, zadejte skriptovací stroj ladicí program k aktuálnímu bodu provádění skriptu.|  
|SCRIPTINTERRUPT_RAISEEXCEPTION|Pokud podporovaná jazyk skriptovací stroje, umožní skript ošetření výjimky. Jinak metoda skript byl přerušen a kód chyby je vrácen volajícímu; To znamená, události zdroje nebo makro původce.|  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí jednu z následujících hodnot:  
  
|Návratová hodnota|Význam|  
|------------------|-------------|  
|`S_OK`|Úspěch.|  
|`E_INVALIDARG`|Argument byl neplatný.|  
|`E_POINTER`|Byl zadán neplatný ukazatel.|  
|`E_UNEXPECTED`|Nebyl očekáván volání (například skriptovací stroj ještě byla načtena nebo inicializovat).|  
  
## <a name="see-also"></a>Viz také  
 [IActiveScript –](../../winscript/reference/iactivescript.md)