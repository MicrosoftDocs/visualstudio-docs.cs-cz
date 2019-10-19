---
title: Výčet SCRIPT_DEBUGGER_OPTIONS | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SCRIPT_DEBUGGER_OPTIONS Enumeration
ms.assetid: aef41ec0-6f65-48e8-a69e-44b4e4fb929f
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c69d419732786442cda275bf85c74ab2b9d3e870
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574562"
---
# <a name="script_debugger_options-enumeration"></a>Výčet SCRIPT_DEBUGGER_OPTIONS
Označuje sadu možností a funkcí, které se vztahují k připojenému ladicímu programu. Použito v [idebugapplicationnode100 –:: GetExcludedDocuments](../../winscript/reference/idebugapplicationnode100-getexcludeddocuments.md) a [Idebugapplicationnode100 –:: SetFilterForEventSink](../../winscript/reference/idebugapplicationnode100-setfilterforeventsink.md)  
  
> [!IMPORTANT]
> Tyto konstanty jsou implementovány pomocí PDM v 10.0 a větší. Nachází se v souboru activdbg100.h.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
typedef SCRIPT_DEBUGGER_OPTIONS  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Hodnota|Popis|  
|------------|-----------|-----------------|  
|SDO_NONE|0x00000000|Nejsou nastavené žádné možnosti.|  
|SDO_ENABLE_FIRST_CHANCE_EXCEPTIONS|0x00000001|Označuje, že modul runtime skriptu má vyvolat události BREAKREASON_ERROR, pokud je vyvolána výjimka. Tuto možnost může nastavit ladicí program nebo nastavit pomocí uživatelského kódu prostřednictvím `Debug.enableFirstChanceExceptions(<true&#124;false>)`.|  
|SDO_ENABLE_WEB_WORKER_SUPPORT|0x00000002|Indikuje, že připojený ladicí program podporuje webové pracovníky.|  
  
## <a name="see-also"></a>Viz také:  
 [Konstanty, výčty a struktury ladicího programu aktivních skriptů](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)