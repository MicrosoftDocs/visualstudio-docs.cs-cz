---
title: 'IActiveScript:: GetScriptThreadState | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScript.GetScriptThreadState
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_GetScriptThreadState
ms.assetid: 7cac94d0-436e-4c29-895b-0c4afa0b3ccc
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 38f6ef4b0acdf6e3b746316bef8abe9a3f0f8225
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72578012"
---
# <a name="iactivescriptgetscriptthreadstate"></a>IActiveScript::GetScriptThreadState
Načte aktuální stav vlákna skriptu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetScriptThreadState(  
    SCRIPTTHREADID stidThread,    // identifier of script thread  
    SCRIPTTHREADSTATE *pstsState  // receives state flag  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `stidThread`  
 pro Identifikátor vlákna, pro které je stav požadován, nebo jeden z následujících speciálních identifikátorů vláken:  
  
|Hodnota|Význam|  
|-----------|-------------|  
|SCRIPTTHREADID_BASE|Základní vlákno; To znamená vlákno, ve kterém se vytvořila instance skriptovacího stroje.|  
|SCRIPTTHREADID_CURRENT|Aktuálně prováděné vlákno.|  
  
 `pstsState`  
 mimo Adresa proměnné, která přijímá stav určeného vlákna. Stav je označen jednou z pojmenovaných konstantních hodnot definovaných výčtem [výčtu scriptthreadstate –](../../winscript/reference/scriptthreadstate-enumeration.md) . Pokud tento parametr neidentifikuje aktuální vlákno, stav se může kdykoli změnit.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí jednu z následujících hodnot:  
  
|Návratová hodnota|Význam|  
|------------------|-------------|  
|`S_OK`|Nástup.|  
|`E_POINTER`|Byl zadán neplatný ukazatel.|  
|`E_UNEXPECTED`|Volání nebylo očekáváno (například skriptovací stroj ještě nebyl načten nebo inicializován).|  
  
## <a name="remarks"></a>Poznámky  
 Tuto metodu lze volat z nezákladních vláken, aniž by došlo k nezákladnímu popisku pro hostování objektů nebo rozhraní [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) .  
  
## <a name="see-also"></a>Viz také:  
 [IActiveScript](../../winscript/reference/iactivescript.md)