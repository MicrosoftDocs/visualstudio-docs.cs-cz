---
title: 'IActiveScript:: GetScriptState | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScript.GetScriptState
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_GetScriptState
ms.assetid: 59837f7c-755d-45c4-8194-bd57638fe2e1
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d266e713879aafe1c5ca271d46b3030f3275460f
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575725"
---
# <a name="iactivescriptgetscriptstate"></a>IActiveScript::GetScriptState
Načte aktuální stav skriptovacího stroje. Tuto metodu lze volat z nezákladních vláken, aniž by došlo k nezákladnímu popisku pro hostování objektů nebo rozhraní [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) .  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetScriptState(  
    SCRIPTSTATE *pss  // address of structure for state information  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pss`  
 mimo Adresa proměnné, která přijímá hodnotu definovanou ve výčtu [výčtu scriptstate –](../../winscript/reference/scriptstate-enumeration.md) . Hodnota označuje aktuální stav skriptovacího modulu přidruženého k volajícímu vláknu.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí `S_OK`, pokud bylo úspěšné, nebo `E_POINTER`, pokud byl zadán neplatný ukazatel.  
  
## <a name="see-also"></a>Viz také:  
 [IActiveScript](../../winscript/reference/iactivescript.md)