---
title: 'IActiveScript:: GetCurrentScriptThreadID | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScript.GetCurrentScriptThreadID
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_GetCurrentScriptThreadID
ms.assetid: b09e8b48-4209-480e-8b71-e99ee9ae2e17
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dedb16e0c007ed05370fb54835f84f00784c1ae4
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575768"
---
# <a name="iactivescriptgetcurrentscriptthreadid"></a>IActiveScript::GetCurrentScriptThreadID
Načte identifikátor definovaný skriptovacím modulem pro aktuálně spuštěné vlákno. Identifikátor lze použít v následných voláních ke skriptům pro provádění řídicích vláken, jako je například metoda [IActiveScript:: InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md) .  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetCurrentScriptThreadID(  
    SCRIPTTHREADID *pstidThread  // receives scripting thread identifier  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pstidThread`  
 mimo Adresa proměnné, která přijímá identifikátor vlákna skriptu přidružený k aktuálnímu vláknu. Výklad tohoto identifikátoru je ponechán na skriptovacím stroji, ale může to být pouze kopie identifikátoru vlákna systému Windows. Pokud je vlákno Win32 ukončeno, bude tento identifikátor nepřiřazen a následně lze následně přiřadit jinému vláknu.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí `S_OK`, pokud bylo úspěšné, nebo `E_POINTER`, pokud byl zadán neplatný ukazatel.  
  
## <a name="remarks"></a>Poznámky  
 Tuto metodu lze volat z nezákladních vláken, aniž by došlo k nezákladnímu popisku pro hostování objektů nebo rozhraní [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) .  
  
## <a name="see-also"></a>Viz také:  
 [IActiveScript](../../winscript/reference/iactivescript.md)