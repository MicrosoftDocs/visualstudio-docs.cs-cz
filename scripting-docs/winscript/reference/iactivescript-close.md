---
title: 'IActiveScript:: Close | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: f858de42ef2948d218aac6c3194cc6af544da5e9
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575784"
---
# <a name="iactivescriptclose"></a>IActiveScript::Close
Způsobí, že skriptovací modul opustí libovolný aktuálně načtený skript, ztratí jeho stav a uvolní všechny ukazatele rozhraní, které má, a to tak, aby vstoupily do zavřeného stavu. Jímka událostí, ihned spouštěný text skriptu a vyvolání makra, která již probíhá, jsou dokončeny před změnou stavu (pomocí [IActiveScript:: InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md) zrušení spuštěného vlákna skriptu). Tuto metodu musí volat vytvořením hostitele předtím, než se uvolní rozhraní, aby se předešlo problémům s cyklickými odkazy.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT Close(void);  
```  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí jednu z následujících hodnot:  
  
|Hodnota|Význam|  
|-----------|-------------|  
|`S_OK`|Nástup.|  
|`E_UNEXPECTED`|Volání nebylo očekáváno (například skriptovací stroj byl již v zavřeném stavu).|  
|`OLESCRIPT_S_PENDING`|Metoda byla úspěšně zařazena do fronty, ale stav ještě nebyl změněn. V případě změny stavu bude lokalita volána zpět v metodě [IActiveScriptSite:: OnStateChange](../../winscript/reference/iactivescriptsite-onstatechange.md) .|  
|`S_FALSE`|Metoda byla úspěšná, ale skript už je uzavřený.|  
  
## <a name="see-also"></a>Viz také:  
 [IActiveScript](../../winscript/reference/iactivescript.md)