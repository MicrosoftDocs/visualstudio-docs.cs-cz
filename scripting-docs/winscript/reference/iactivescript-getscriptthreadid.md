---
title: 'IActiveScript:: GetScriptThreadID | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 2a0fb1eebfcb6ed100056289fab6bce662f86a7b
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575708"
---
# <a name="iactivescriptgetscriptthreadid"></a>IActiveScript::GetScriptThreadID
Načte identifikátor definovaný skriptovacím modulem pro vlákno přidružené k danému vláknu Win32.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetScriptThreadID(  
    DWORD dwWin32ThreadID,       // Win32 thread identifier.  
    SCRIPTTHREADID *pstidThread  // Receives scripting thread. identifier  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `dwWin32ThreadID`,  
 pro Identifikátor vlákna běžícího vlákna Win32 v aktuálním procesu. K načtení identifikátoru vlákna aktuálně zpracovávaného vlákna použijte funkci [IActiveScript:: GetCurrentScriptThreadID](../../winscript/reference/iactivescript-getcurrentscriptthreadid.md) .  
  
 `pstidThread`,  
 mimo Adresa proměnné, která přijímá identifikátor vlákna skriptu přidružený k danému vláknu Win32. Výklad tohoto identifikátoru je ponechán na skriptovacím stroji, ale může to být pouze kopie identifikátoru vlákna systému Windows. Všimněte si, že pokud je vlákno Win32 ukončeno, bude tento identifikátor nepřiřazen a následně může být následně přiřazen jinému vláknu.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí jednu z následujících hodnot:  
  
|Návratová hodnota|Význam|  
|------------------|-------------|  
|`S_OK`|Nástup.|  
|`E_POINTER`|Byl zadán neplatný ukazatel.|  
|`E_UNEXPECTED`|Volání nebylo očekáváno (například skriptovací stroj ještě nebyl načten nebo inicializován), a proto selhal.|  
  
## <a name="remarks"></a>Poznámky  
 Načtený identifikátor lze použít v následných voláních metod ovládacího prvku spuštění vlákna skriptu, jako je například metoda [IActiveScript:: InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md) .  
  
 Tuto metodu lze volat z nezákladních vláken, aniž by došlo k nezákladnímu popisku pro hostování objektů nebo rozhraní [IActiveScript:: InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md) .  
  
## <a name="see-also"></a>Viz také:  
 [IActiveScript](../../winscript/reference/iactivescript.md)