---
title: 'Iremotedebugapplication110 –:: SetDebuggerOptions | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IRemoteDebugApplication110::SetDebuggerOptions
ms.assetid: 58e9fd18-3e0d-47fa-8893-f316146bde84
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e7168a4ef8ec70368c0ff691ba1f721275f9d65d
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577425"
---
# <a name="iremotedebugapplication110setdebuggeroptions"></a>IRemoteDebugApplication110::SetDebuggerOptions
Volá se, aby se aktualizovaly možnosti ladicího programu. Tato metoda by měla být volána po [iremotedebugapplication –:: ConnectDebugger](../../winscript/reference/iremotedebugapplication-connectdebugger.md). Metoda [iremotedebugapplication –::D isconnectdebugger](../../winscript/reference/iremotedebugapplication-disconnectdebugger.md) automaticky obnoví výchozí možnosti. Výchozí možnosti jsou 0 (SDO_NONE).  
  
> [!IMPORTANT]
> [Rozhraní iremotedebugapplication –](../../winscript/reference/iremotedebugapplication-interface.md) je implementováno pomocí PDM v 11.0 a větší. Nachází se v souboru activdbg100.h.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT SetDebuggerOptions(        [in] enum SCRIPT_DEBUGGER_OPTIONS mask,        [in] enum SCRIPT_DEBUGGER_OPTIONS value    );  
```  
  
#### <a name="parameters"></a>Parametry  
 `mask`  
 Maska [výčtu SCRIPT_DEBUGGER_OPTIONS](../../winscript/reference/script-debugger-options-enumeration.md) .  
  
 `value`  
 Hodnota [výčtu SCRIPT_DEBUGGER_OPTIONS](../../winscript/reference/script-debugger-options-enumeration.md) .  
  
## <a name="see-also"></a>Viz také:  
 @No__t_1 [rozhraní iremotedebugapplication –](../../winscript/reference/iremotedebugapplication-interface.md)  
 [IRemoteDebugApplication110 – rozhraní](../../winscript/reference/iremotedebugapplication110-interface.md)