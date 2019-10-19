---
title: 'IActiveScriptSite:: OnScriptTerminate | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSite.OnScriptTerminate
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSite_OnScriptTerminate
ms.assetid: 3301ddf4-5929-404c-81d3-1a720e589008
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a715b39b07df4183d4ec542a1dd82b4229d1f41e
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72570204"
---
# <a name="iactivescriptsiteonscriptterminate"></a>IActiveScriptSite::OnScriptTerminate
Informuje hostitele, že se dokončilo provádění skriptu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT OnScriptTerminate(  
    VARIANT *pvarResult,   // address of script results  
    EXCEPINFO *pexcepinfo  // address of structure with exception information  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pvarResult`  
 pro Adresa proměnné, která obsahuje výsledek skriptu, nebo `NULL`, pokud skript nevytvořil žádný výsledek.  
  
 `pexcepinfo`  
 pro Adresa `EXCEPINFO` struktury, která obsahuje informace o výjimce vygenerované při ukončení skriptu, nebo `NULL`, pokud nebyla vygenerována žádná výjimka.  
  
## <a name="return-value"></a>Návratová hodnota  
 Pokud je úspěšná, vrátí `S_OK`.  
  
## <a name="remarks"></a>Poznámky  
 Skriptovací modul volá tuto metodu před voláním metody [IActiveScriptSite:: OnStateChange](../../winscript/reference/iactivescriptsite-onstatechange.md) , se sadou příznaků SCRIPTSTATE_INITIALIZED je dokončena. Tato metoda se dá použít k vrácení stavu dokončení a výsledků do hostitele. Všimněte si, že mnoho skriptovacích jazyků, které jsou založeny na událostech jímky z hostitele, mají životní rozsahy, které jsou definovány hostitelem. V takovém případě nemusí být tato metoda nikdy volána.  
  
## <a name="see-also"></a>Viz také:  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)