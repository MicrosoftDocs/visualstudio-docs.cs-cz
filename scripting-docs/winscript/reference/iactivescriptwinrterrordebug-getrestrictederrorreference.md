---
title: 'Iactivescriptwinrterrordebug –:: GetRestrictedErrorReference | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptWinRTErrorDebug::GetRestrictedErrorReference
ms.assetid: fcf60971-9518-4b24-a3a6-1e2e30a02cea
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4665071fe26ed3dadbaadbcbaa79217562d311c6
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577919"
---
# <a name="iactivescriptwinrterrordebuggetrestrictederrorreference"></a>IActiveScriptWinRTErrorDebug::GetRestrictedErrorReference
Vrátí chybu omezeného odkazu prostředí Windows Runtime, je-li k dispozici.  
  
> [!IMPORTANT]
> [Rozhraní iactivescriptwinrterrordebug –](../../winscript/reference/iactivescriptwinrterrordebug-interface.md) je implementováno pomocí PDM v 11.0 a větší. Nachází se v souboru activdbg100.h.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetRestrictedErrorReference([out] BSTR * referenceString);  
```  
  
#### <a name="parameters"></a>Parametry  
 `referenceString`  
 mimo Řetězec referenční chyby  
  
## <a name="see-also"></a>Viz také:  
 [IActiveScriptWinRTErrorDebug – rozhraní](../../winscript/reference/iactivescriptwinrterrordebug-interface.md)