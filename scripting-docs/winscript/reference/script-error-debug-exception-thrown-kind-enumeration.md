---
title: Výčet SCRIPT_ERROR_DEBUG_EXCEPTION_THROWN_KIND | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: b3aa4966-e110-4b30-b368-1281a9740dbd
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8eb089efbf608b488465809f997ffc82fc2c2e3c
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574400"
---
# <a name="script_error_debug_exception_thrown_kind-enumeration"></a>Výčet SCRIPT_ERROR_DEBUG_EXCEPTION_THROWN_KIND
Označuje druh vyvolané výjimky. Tento výčet používá metoda [IActiveScriptErrorDebug110:: GetExceptionThrownKind](../../winscript/reference/iactivescripterrordebug110-getexceptionthrownkind.md) .  
  
> [!IMPORTANT]
> Tyto konstanty jsou implementovány modulem PDM verze 11.0 nebo novější. Nachází se v souboru activdbg100.h.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
typedef SCRIPT_ERROR_DEBUG_EXCEPTION_THROWN_KIND  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Hodnota|Popis|  
|------------|-----------|-----------------|  
|ETK_FIRST_CHANCE|0x00000000|Tato výjimka je výjimka první příležitosti.|  
|ETK_USER_UNHANDLED|0x00000001|Tato výjimka není ošetřena v uživatelském kódu.|  
|ETK_UNHANDLED|0x00000002|Tato výjimka není ošetřena v kódu.|  
  
## <a name="see-also"></a>Viz také:  
 [IActiveScriptErrorDebug110 – rozhraní](../../winscript/reference/iactivescripterrordebug110-interface.md)