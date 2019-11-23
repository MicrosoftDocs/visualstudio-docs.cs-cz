---
title: 'IActiveScript:: SetScriptState | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScript.SetScriptState
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_SetScriptState
ms.assetid: f2b2700c-0c8d-40db-ad84-dc751c5d9bc2
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ea947e00ffd5a3498261f4a3a8acd4791e8ace60
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577994"
---
# <a name="iactivescriptsetscriptstate"></a>IActiveScript::SetScriptState
Vloží skriptovací stroj do daného stavu. Tuto metodu lze volat z nezákladních vláken, aniž by došlo k nezákladnímu popisku pro hostování objektů nebo rozhraní [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) .  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT SetScriptState(  
    SCRIPTSTATE ss  // identifier of new state  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ss`  
 pro Nastaví skriptovací stroj do daného stavu. Může se jednat o jednu z hodnot definovaných ve výčtu [výčtu scriptstate –](../../winscript/reference/scriptstate-enumeration.md) .  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí jednu z následujících hodnot:  
  
|Návratová hodnota|Význam|  
|------------------|-------------|  
|`S_OK`|Nástup.|  
|`E_FAIL`|Skriptovací stroj nepodporuje přechod zpět do inicializovaného stavu. Hostitel musí tento skriptovací stroj zahodit a vytvořit, inicializovat a načíst nový skriptovací stroj, aby dosáhl stejného efektu.|  
|`E_UNEXPECTED`|Volání nebylo očekáváno (například skriptovací stroj ještě nebyl načten nebo inicializován), a proto selhal.|  
|`OLESCRIPT_S_PENDING`|Metoda byla úspěšně zařazena do fronty, ale stav ještě nebyl změněn. V případě změny stavu bude lokalita volána zpět pomocí metody [IActiveScriptSite:: OnStateChange](../../winscript/reference/iactivescriptsite-onstatechange.md) .|  
|`S_FALSE`|Metoda byla úspěšná, ale skript už je v daném stavu.|  
  
## <a name="remarks"></a>Poznámky  
 Další informace o stavech skriptovacího stroje najdete v části stavy skriptovacího stroje skriptovacích [strojů Windows](../../winscript/windows-script-engines.md) .  
  
## <a name="see-also"></a>Viz také:  
 [IActiveScript:: Clone](../../winscript/reference/iactivescript-clone.md)   
 [IActiveScript:: GetScriptDispatch](../../winscript/reference/iactivescript-getscriptdispatch.md)   
 [IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md)   
 [IActiveScriptParse::ParseScriptText](../../winscript/reference/iactivescriptparse-parsescripttext.md)   
 [IActiveScriptSite::GetItemInfo](../../winscript/reference/iactivescriptsite-getiteminfo.md)