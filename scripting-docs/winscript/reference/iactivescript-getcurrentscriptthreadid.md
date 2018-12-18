---
title: IActiveScript::GetCurrentScriptThreadID | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 5921dc4d0f9a9bf0d505fece0f47354cb16d440c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24791748"
---
# <a name="iactivescriptgetcurrentscriptthreadid"></a>IActiveScript::GetCurrentScriptThreadID
Načte identifikátor skriptovací stroj definované pro aktuálně prováděné vlákno. Identifikátor dá následující volání metody řízení provádění skriptu přístup z více vláken, jako [IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md) metoda.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetCurrentScriptThreadID(  
    SCRIPTTHREADID *pstidThread  // receives scripting thread identifier  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pstidThread`  
 [out] Adresa proměnné, která přijímá identifikátor vlákno skript, který je přidružený aktuální vlákno. Výklad tento identifikátor je zleva skriptovací stroje, ale může být pouze kopie identifikátor systému Windows. Pokud vlákno Win32 ukončí, tento identifikátor se stane nepřiřazené a následně může být přiřazen jiné vlákno.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí `S_OK` v případě úspěchu nebo `E_POINTER` Pokud byl zadán neplatný ukazatel.  
  
## <a name="remarks"></a>Poznámky  
 Tuto metodu lze volat z vlákna není základní bez výsledkem není základní popisku na objekty hostitele nebo na [iactivescriptsite –](../../winscript/reference/iactivescriptsite.md) rozhraní.  
  
## <a name="see-also"></a>Viz také  
 [IActiveScript –](../../winscript/reference/iactivescript.md)