---
title: 'Iremotedebugapplicationevents –:: OnDestroyThread | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IRemoteDebugApplicationEvents.OnDestroyThread
apilocation:
- jscript.dll
helpviewer_keywords:
- IRemoteDebugApplicationEvents::OnDestroyThread
ms.assetid: 7c716ccc-7b82-41b2-9a16-d0366999dee8
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 59f2b599978cfaf993981fa66958fd3acabe4b32
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575607"
---
# <a name="iremotedebugapplicationeventsondestroythread"></a>IRemoteDebugApplicationEvents::OnDestroyThread
Zpracovává událost zničenou vláknem.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT OnDestroyThread(  
   IRemoteDebugApplicationThread*  prdat  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `prdat`  
 pro Vlákno, které bylo zničeno.  
  
## <a name="return-value"></a>Návratová hodnota  
 Metoda vrací `HRESULT`. Možné hodnoty zahrnují hodnoty v následující tabulce, ale nejsou na ně omezeny.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`S_OK`|Metoda byla úspěšná.|  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda zpracovává událost zničenou vláknem.  
  
## <a name="see-also"></a>Viz také:  
 [IRemoteDebugApplicationEvents – rozhraní](../../winscript/reference/iremotedebugapplicationevents-interface.md)