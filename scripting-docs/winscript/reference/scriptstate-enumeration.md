---
title: SCRIPTSTATE – výčet | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- SCRIPTSTATE
apilocation:
- scrobj.dll
helpviewer_keywords:
- SCRIPTSTATE enum
ms.assetid: 5f5deb05-c4bb-4964-8077-e624c6b2a14e
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 35e062a9c2f3076144063ffb77895c8a03ecc4ac
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24796464"
---
# <a name="scriptstate-enumeration"></a>SCRIPTSTATE – výčet
Určuje stav skriptovací stroje. Tento výčet je používán [IActiveScript::GetScriptState](../../winscript/reference/iactivescript-getscriptstate.md) , [IActiveScript::SetScriptState](../../winscript/reference/iactivescript-setscriptstate.md) , a [IActiveScriptSite::OnStateChange](../../winscript/reference/iactivescriptsite-onstatechange.md) metody.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef enum tagSCRIPTSTATE {  
    SCRIPTSTATE_UNINITIALIZED = 0,  
    SCRIPTSTATE_INITIALIZED   = 5,  
    SCRIPTSTATE_STARTED       = 1,  
    SCRIPTSTATE_CONNECTED     = 2,  
    SCRIPTSTATE_DISCONNECTED  = 3,  
    SCRIPTSTATE_CLOSED        = 4  
} SCRIPTSTATE;  
```  
  
## <a name="enumeration-values"></a>Hodnoty výčtu  
  
|||  
|-|-|  
|SCRIPTSTATE_UNINITIALIZED|Skript byl právě vytvořen, ale ještě nebyla inicializovaná pomocí `IPersist*` rozhraní a [IActiveScript::SetScriptSite](../../winscript/reference/iactivescript-setscriptsite.md) .|  
|SCRIPTSTATE_INITIALIZED|Skript byl inicializován, ale není používat (připojení k jiné objekty nebo zpracování událostí) nebo spuštěním jakéhokoli kódu. Kód může být dotázán na spuštění při volání [IActiveScriptParse::ParseScriptText](../../winscript/reference/iactivescriptparse-parsescripttext.md) metoda.|  
|SCRIPTSTATE_STARTED|Skript může spustit kód, ale ještě není vnořování události objektů přidaných [IActiveScript::AddNamedItem](../../winscript/reference/iactivescript-addnameditem.md) metoda.|  
|SCRIPTSTATE_CONNECTED|Skript je načíst a připojení pro zpracování událostí.|  
|SCRIPTSTATE_DISCONNECTED|Skript je načteno a má stav běhu spuštění, ale je dočasně odpojen od zpracování událostí.|  
|SCRIPTSTATE_CLOSED|Skript byl uzavřen. Skriptovací stroje už funguje a vrátí chyby pro většinu metod.|  
  
## <a name="see-also"></a>Viz také  
 [Aktivních skriptů konstanty, výčty a kódy chyb](../../winscript/reference/active-script-constants-enumerations-and-error-codes.md)