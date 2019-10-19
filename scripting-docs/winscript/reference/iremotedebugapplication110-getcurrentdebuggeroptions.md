---
title: 'Iremotedebugapplication110 –:: GetCurrentDebuggerOptions | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IRemoteDebugApplication110::GetCurrentDebuggerOptions
ms.assetid: a6e9cae1-e8f3-4d62-b133-52e9ca12ba7a
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b6ae042a5d4d1c1ee350b328fdc5a9b7420d9928
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577435"
---
# <a name="iremotedebugapplication110getcurrentdebuggeroptions"></a>IRemoteDebugApplication110::GetCurrentDebuggerOptions
Vrátí sadu aktuálně povolených možností.  
  
> [!IMPORTANT]
> [Rozhraní iremotedebugapplication –](../../winscript/reference/iremotedebugapplication-interface.md) je implementováno pomocí PDM v 11.0 a větší. Nachází se v souboru activdbg100.h.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetCurrentDebuggerOptions([out] enum SCRIPT_DEBUGGER_OPTIONS* pCurrentOptions);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pCurrentOptions`  
 mimo Aktuální možnosti.  
  
## <a name="see-also"></a>Viz také:  
 @No__t_1 [rozhraní iremotedebugapplication –](../../winscript/reference/iremotedebugapplication-interface.md)  
 [IRemoteDebugApplication110 – rozhraní](../../winscript/reference/iremotedebugapplication110-interface.md)