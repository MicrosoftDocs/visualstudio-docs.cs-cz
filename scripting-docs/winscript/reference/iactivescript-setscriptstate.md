---
title: IActiveScript::SetScriptState | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 146cd5e4f2b6137fc6fe6e32e8ca153c3aab8fd5
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24793293"
---
# <a name="iactivescriptsetscriptstate"></a>IActiveScript::SetScriptState
Skriptovací stroj umístí do má daný stav. Tuto metodu lze volat z vlákna není základní bez výsledkem není základní popisku na objekty hostitele nebo na [iactivescriptsite –](../../winscript/reference/iactivescriptsite.md) rozhraní.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT SetScriptState(  
    SCRIPTSTATE ss  // identifier of new state  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ss`  
 [v] Nastaví skriptovací stroj má daný stav. Může být jedna z hodnot fronty definovaných v [SCRIPTSTATE – výčet](../../winscript/reference/scriptstate-enumeration.md) výčtu.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí jednu z následujících hodnot:  
  
|Návratová hodnota|Význam|  
|------------------|-------------|  
|`S_OK`|Úspěch.|  
|`E_FAIL`|Skriptovací stroj nepodporuje přechod zpět inicializovaný stav. Hostitele musí zrušit toto skriptovacího stroje a vytvořit, inicializovat a spouštění nového skriptovacího stroje k dosažení stejného efektu.|  
|`E_UNEXPECTED`|Nebyl očekáván volání (například skriptovací stroj ještě byla načtena nebo inicializovat) a proto se nezdařilo.|  
|`OLESCRIPT_S_PENDING`|Metoda byla úspěšně ve frontě, ale nebyla ještě změnil stav. Když změny stavu webu se zpětné volání prostřednictvím [IActiveScriptSite::OnStateChange](../../winscript/reference/iactivescriptsite-onstatechange.md) metoda.|  
|`S_FALSE`|Metoda byla úspěšná, ale skript byl již má daný stav.|  
  
## <a name="remarks"></a>Poznámky  
 Další informace o skriptování modul stavy, najdete v části stavy modulu skriptu z [skriptovací stroje systému Windows](../../winscript/windows-script-engines.md) .  
  
## <a name="see-also"></a>Viz také  
 [IActiveScript::Clone](../../winscript/reference/iactivescript-clone.md)   
 [IActiveScript::GetScriptDispatch](../../winscript/reference/iactivescript-getscriptdispatch.md)   
 [IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md)   
 [IActiveScriptParse::ParseScriptText](../../winscript/reference/iactivescriptparse-parsescripttext.md)   
 [IActiveScriptSite::GetItemInfo](../../winscript/reference/iactivescriptsite-getiteminfo.md)