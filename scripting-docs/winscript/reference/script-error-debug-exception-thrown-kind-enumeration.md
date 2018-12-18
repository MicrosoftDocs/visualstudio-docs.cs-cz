---
title: Výčet Script_error_debug_exception_thrown_kind | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: b3aa4966-e110-4b30-b368-1281a9740dbd
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6fe5b308ea75956d9e5826b4daadaef3a823141f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24796398"
---
# <a name="scripterrordebugexceptionthrownkind-enumeration"></a>Výčet SCRIPT_ERROR_DEBUG_EXCEPTION_THROWN_KIND
Označuje druh vyvolané výjimky. Tento výčet je používán [IActiveScriptErrorDebug110::GetExceptionThrownKind](../../winscript/reference/iactivescripterrordebug110-getexceptionthrownkind.md) metoda.  
  
> [!IMPORTANT]
>  Tyto konstanty jsou implementovány modulem PDM verze 11.0 nebo novější. Nachází se v souboru activdbg100.h.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef SCRIPT_ERROR_DEBUG_EXCEPTION_THROWN_KIND  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Hodnota|Popis|  
|------------|-----------|-----------------|  
|ETK_FIRST_CHANCE|0x00000000|Tato výjimka je výjimka první příležitosti.|  
|ETK_USER_UNHANDLED|0x00000001|Tato výjimka není ošetřena v uživatelském kódu.|  
|ETK_UNHANDLED|0x00000002|Tato výjimka není ošetřena v kódu.|  
  
## <a name="see-also"></a>Viz také  
 [Iactivescripterrordebug110 – rozhraní](../../winscript/reference/iactivescripterrordebug110-interface.md)