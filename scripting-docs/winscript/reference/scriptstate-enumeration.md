---
title: Výčet SCRIPTSTATE – | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 10dd6366e2d0783ec2e9d6bdadc001e9f999901e
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575680"
---
# <a name="scriptstate-enumeration"></a>SCRIPTSTATE – výčet
Určuje stav skriptovacího modulu. Tento výčet používá metody [IActiveScript:: GetScriptState](../../winscript/reference/iactivescript-getscriptstate.md) , [IActiveScript:: SetScriptState](../../winscript/reference/iactivescript-setscriptstate.md) a [IActiveScriptSite:: OnStateChange](../../winscript/reference/iactivescriptsite-onstatechange.md) .  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
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
|SCRIPTSTATE_UNINITIALIZED|Skript byl právě vytvořen, ale ještě nebyl inicializován pomocí rozhraní `IPersist*` a [IActiveScript:: SetScriptSite](../../winscript/reference/iactivescript-setscriptsite.md) .|  
|SCRIPTSTATE_INITIALIZED|Skript byl inicializován, ale neběží (připojuje se k jiným objektům nebo událostem jímky) nebo spouští jakýkoliv kód. Kód může být dotazován na spuštění voláním metody [IActiveScriptParse::P arsescripttext](../../winscript/reference/iactivescriptparse-parsescripttext.md) .|  
|SCRIPTSTATE_STARTED|Skript může spustit kód, ale ještě nepracuje s událostmi objektů přidaných metodou [IActiveScript:: AddNamedItem](../../winscript/reference/iactivescript-addnameditem.md) .|  
|SCRIPTSTATE_CONNECTED|Skript je načten a připojen pro události jímky.|  
|SCRIPTSTATE_DISCONNECTED|Skript je načten a má běhový stav spuštění, ale je dočasně odpojen od událostí jímky.|  
|SCRIPTSTATE_CLOSED|Skript je uzavřený. Skriptovací stroj už nefunguje a vrací chyby pro většinu metod.|  
  
## <a name="see-also"></a>Viz také:  
 [Konstanty, výčty a kódy chyb aktivních skriptů](../../winscript/reference/active-script-constants-enumerations-and-error-codes.md)