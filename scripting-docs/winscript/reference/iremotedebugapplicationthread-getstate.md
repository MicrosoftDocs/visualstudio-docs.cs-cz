---
title: IRemoteDebugApplicationThread::GetState | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IRemoteDebugApplicationThread.GetState
apilocation:
- pdm.dll
helpviewer_keywords:
- IRemoteDebugApplicationThread::GetState
ms.assetid: 44503a78-efa9-4fbf-98be-a5dcfa329c5a
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ce34fa73f97b92d08193c697e991c9e922ac17ee
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24795087"
---
# <a name="iremotedebugapplicationthreadgetstate"></a>IRemoteDebugApplicationThread::GetState
Získá stav tohoto podprocesu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetState(  
   DWORD*  pState  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pState`  
 [out] Kombinace následující příznaky stavu přístup z více vláken:  
  
|Konstanta|Hodnota|Popis|  
|--------------|-----------|-----------------|  
|THREAD_STATE_RUNNING|0x00000001|Vlákno je spuštěno.|  
|THREAD_STATE_SUSPENDED|0x00000002|Vlákno je pozastaveno.|  
|THREAD_BLOCKED|0x00000004|Vlákno je blokován.|  
|THREAD_OUT_OF_CONTEXT|0x00000008|Vlákno je mimo obsah.|  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí metodu `HRESULT`. Možné hodnoty zahrnují hodnoty v následující tabulce, ale nejsou na ně omezeny.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`S_OK`|Metoda byla úspěšná.|  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda získá stav tohoto podprocesu.  
  
## <a name="see-also"></a>Viz také  
 [Iremotedebugapplicationthread – rozhraní](../../winscript/reference/iremotedebugapplicationthread-interface.md)