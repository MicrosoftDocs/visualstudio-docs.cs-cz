---
title: IActiveScript::GetScriptState | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 285a09308c7477dbeed68f9f93417b503ca4fe49
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24791562"
---
# <a name="iactivescriptgetscriptstate"></a>IActiveScript::GetScriptState
Načte aktuální stav skriptovacího stroje. Tuto metodu lze volat z vlákna není základní bez výsledkem není základní popisku na objekty hostitele nebo na [iactivescriptsite –](../../winscript/reference/iactivescriptsite.md) rozhraní.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetScriptState(  
    SCRIPTSTATE *pss  // address of structure for state information  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pss`  
 [out] Adresy proměnné, která přijímá hodnota definovaná v [SCRIPTSTATE – výčet](../../winscript/reference/scriptstate-enumeration.md) výčtu. Hodnota označuje aktuální stav skriptovací stroje přidružené volající vlákno.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí `S_OK` v případě úspěchu nebo `E_POINTER` Pokud byl zadán neplatný ukazatel.  
  
## <a name="see-also"></a>Viz také  
 [IActiveScript –](../../winscript/reference/iactivescript.md)