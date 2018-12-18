---
title: IActiveScript::GetScriptThreadID | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScript.GetScriptThreadID
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_GetScriptThreadID
ms.assetid: 2595d76e-30b5-429f-88b4-1d026645dd9b
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8850319035b7b5e3a9cbbd4bbe4340e1eefacc96
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24792003"
---
# <a name="iactivescriptgetscriptthreadid"></a>IActiveScript::GetScriptThreadID
Načte identifikátor skriptovací stroj definované pro vlákno přidružené k dané Win32 vlákno.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetScriptThreadID(  
    DWORD dwWin32ThreadID,       // Win32 thread identifier.  
    SCRIPTTHREADID *pstidThread  // Receives scripting thread. identifier  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `dwWin32ThreadID` ,  
 [v] Vlákno identifikátor spuštěné Win32 vlákna v aktuálním procesu. Použití [IActiveScript::GetCurrentScriptThreadID](../../winscript/reference/iactivescript-getcurrentscriptthreadid.md) funkce načíst identifikátor aktuálně prováděné vlákno.  
  
 `pstidThread` ,  
 [out] Adresa proměnné, která přijímá identifikátor skriptu přidružené k dané Win32 vlákno. Výklad tento identifikátor je zleva skriptovací stroje, ale může být pouze kopie identifikátor systému Windows. Upozorňujeme, že pokud vlákno Win32 ukončí, tento identifikátor se stane nepřiřazené a následně může být přiřazen jiné vlákno.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí jednu z následujících hodnot:  
  
|Návratová hodnota|Význam|  
|------------------|-------------|  
|`S_OK`|Úspěch.|  
|`E_POINTER`|Byl zadán neplatný ukazatel.|  
|`E_UNEXPECTED`|Nebyl očekáván volání (například skriptovací stroj ještě byla načtena nebo inicializovat) a proto se nezdařilo.|  
  
## <a name="remarks"></a>Poznámky  
 Načtené identifikátor lze v následných volání metod řízení provádění skriptu přístup z více vláken, jako [IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md) metoda.  
  
 Tuto metodu lze volat z vlákna není základní bez výsledkem není základní popisku na objekty hostitele nebo na [IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md) rozhraní.  
  
## <a name="see-also"></a>Viz také  
 [IActiveScript –](../../winscript/reference/iactivescript.md)