---
title: IActiveScript::GetScriptThreadState | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 1b11b8566857bc70aaeac5bdf8e8e357fa5d9c2e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24791889"
---
# <a name="iactivescriptgetscriptthreadstate"></a>IActiveScript::GetScriptThreadState
Načte aktuální stav vlákna skriptu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetScriptThreadState(  
    SCRIPTTHREADID stidThread,    // identifier of script thread  
    SCRIPTTHREADSTATE *pstsState  // receives state flag  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `stidThread`  
 [v] Identifikátor vlákno, které chcete stav obnovit, nebo jeden z následujících identifikátorů speciální vlákna:  
  
|Hodnota|Význam|  
|-----------|-------------|  
|SCRIPTTHREADID_BASE|Základní podprocesu. To znamená, že byla vytvořena instance vláken, ve kterém skriptování modul.|  
|SCRIPTTHREADID_CURRENT|Aktuálně prováděné vlákno.|  
  
 `pstsState`  
 [out] Adresa proměnné, která obdrží stav uvedené vlákno. Stav je indikován jednu s názvem konstantní hodnoty, které jsou definované [SCRIPTTHREADSTATE – výčet](../../winscript/reference/scriptthreadstate-enumeration.md) výčtu. Pokud tento parametr neidentifikuje aktuální vlákno, může kdykoli změnit stav.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí jednu z následujících hodnot:  
  
|Návratová hodnota|Význam|  
|------------------|-------------|  
|`S_OK`|Úspěch.|  
|`E_POINTER`|Byl zadán neplatný ukazatel.|  
|`E_UNEXPECTED`|Nebyl očekáván volání (například skriptovací stroj ještě byla načtena nebo inicializovat).|  
  
## <a name="remarks"></a>Poznámky  
 Tuto metodu lze volat z vlákna není základní bez výsledkem není základní popisku na objekty hostitele nebo na [iactivescriptsite –](../../winscript/reference/iactivescriptsite.md) rozhraní.  
  
## <a name="see-also"></a>Viz také  
 [IActiveScript –](../../winscript/reference/iactivescript.md)