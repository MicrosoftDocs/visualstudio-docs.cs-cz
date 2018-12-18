---
title: IActiveScript::Close | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScript.Close
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_Close
ms.assetid: cc7dd63b-1d7e-410a-857b-09ea3aade275
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7c90b5d089ea6665060944e0a6f720a43aa1295a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24791802"
---
# <a name="iactivescriptclose"></a>IActiveScript::Close
Způsobí, že skriptovací stroj abandon všech aktuálně načtených skriptů, dojít ke ztrátě stavu a uvolnit všechny ukazatele rozhraní, které je jiné objekty, proto zadávání uzavřeném stavu. Jímky událostí, okamžitě spustit skript text a makro volání, které jsou již probíhá dokončení před změny stavu (použijte [IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md) zrušit běžící vlákna skriptu). Tato metoda musí být volána pro vytváření hostitele před rozhraní je vydané zabránit problémům cyklický odkaz.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT Close(void);  
```  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí jednu z následujících hodnot:  
  
|Hodnota|Význam|  
|-----------|-------------|  
|`S_OK`|Úspěch.|  
|`E_UNEXPECTED`|Nebyl očekáván volání (například skriptovací stroj již byla v uzavřeném stavu).|  
|`OLESCRIPT_S_PENDING`|Metoda byla úspěšně ve frontě, ale nebyla ještě změnil stav. Pokud změny stavu webu je zpětné volání provedeno [IActiveScriptSite::OnStateChange](../../winscript/reference/iactivescriptsite-onstatechange.md) metoda.|  
|`S_FALSE`|Metoda byla úspěšná, ale skript již byl uzavřen.|  
  
## <a name="see-also"></a>Viz také  
 [IActiveScript –](../../winscript/reference/iactivescript.md)