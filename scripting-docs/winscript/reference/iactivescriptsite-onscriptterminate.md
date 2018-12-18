---
title: IActiveScriptSite::OnScriptTerminate | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSite.OnScriptTerminate
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSite_OnScriptTerminate
ms.assetid: 3301ddf4-5929-404c-81d3-1a720e589008
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: eef8bd2a3f2e2a4eb4fd4b5f0e35fcd9acfe5bc9
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24793539"
---
# <a name="iactivescriptsiteonscriptterminate"></a>IActiveScriptSite::OnScriptTerminate
Informuje hostitele, že skript dokončila spuštění.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT OnScriptTerminate(  
    VARIANT *pvarResult,   // address of script results  
    EXCEPINFO *pexcepinfo  // address of structure with exception information  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pvarResult`  
 [v] Adresa proměnné, která obsahuje výsledek skriptu nebo `NULL` Pokud skript vytvořil žádný výsledek.  
  
 `pexcepinfo`  
 [v] Adresa `EXCEPINFO` struktura, která obsahuje informace o výjimce, které jsou generovány, pokud byl ukončen skript, nebo `NULL` Pokud byla vygenerována žádná výjimka.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí `S_OK` v případě úspěchu.  
  
## <a name="remarks"></a>Poznámky  
 Skriptovací stroj volá tuto metodu před volání [IActiveScriptSite::OnStateChange](../../winscript/reference/iactivescriptsite-onstatechange.md) metoda SCRIPTSTATE_INITIALIZED příznak nastaven, je dokončena. Tato metoda slouží k vrátit stav dokončení a výsledky na hostitele. Upozorňujeme ale, že mnoho skriptu jazyky, které jsou založeny na zpracování událostí z hostitele, se životnost, které jsou definovány pro hostitele. V takovém případě může nikdy volat tuto metodu.  
  
## <a name="see-also"></a>Viz také  
 [Iactivescriptsite –](../../winscript/reference/iactivescriptsite.md)