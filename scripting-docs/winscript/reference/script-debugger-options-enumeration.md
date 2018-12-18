---
title: Výčet Script_debugger_options | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 54b910562670104f0fb5679f2b09780afcd17751
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24796380"
---
# <a name="scriptdebuggeroptions-enumeration"></a>Výčet SCRIPT_DEBUGGER_OPTIONS
Určuje sadu možností nebo funkcí, které platí pro připojené ladicí program. Použít v [IDebugApplicationNode100::GetExcludedDocuments](../../winscript/reference/idebugapplicationnode100-getexcludeddocuments.md) a [IDebugApplicationNode100::SetFilterForEventSink](../../winscript/reference/idebugapplicationnode100-setfilterforeventsink.md)  
  
> [!IMPORTANT]
>  Tyto konstanty se implementují PDM v10.0 a větší. Nachází se v souboru activdbg100.h.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef SCRIPT_DEBUGGER_OPTIONS  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Hodnota|Popis|  
|------------|-----------|-----------------|  
|SDO_NONE|0x00000000|Nejsou nastaveny žádné možnosti.|  
|SDO_ENABLE_FIRST_CHANCE_EXCEPTIONS|0x00000001|Označuje, že spuštění skriptu by měla vyvolat BREAKREASON_ERROR událostí, když je vyvolána výjimka. Tato možnost může nastavit pomocí ladicího programu, nebo nastavte pomocí uživatelského kódu prostřednictvím `Debug.enableFirstChanceExceptions(<true&#124;false>)`.|  
|SDO_ENABLE_WEB_WORKER_SUPPORT|0x00000002|Označuje, že připojené ladicí program podporuje webové pracovních procesů.|  
  
## <a name="see-also"></a>Viz také  
 [Konstanty ladicího programu aktivních skriptů, výčty a struktury](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)