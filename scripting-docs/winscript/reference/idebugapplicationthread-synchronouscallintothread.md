---
title: IDebugApplicationThread::SynchronousCallIntoThread | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplicationThread.SynchronousCallIntoThread
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplicationThread::SynchronousCallIntoThread
ms.assetid: 8a91157f-dade-418a-ad02-5607ce12c95c
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fdeb57380975f19424f8b7da783846b5aae976ed
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24794091"
---
# <a name="idebugapplicationthreadsynchronouscallintothread"></a>IDebugApplicationThread::SynchronousCallIntoThread
Poskytuje mechanismus pro volajícího, aby spuštění kódu v aplikaci vlákno.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT SynchronousCallIntoThread(  
   IDebugThreadCall*  pstcb,  
   DWORD_PTR          dwParam1,  
   DWORD_PTR          dwParam2,  
   DWORD_PTR          dwParam3  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pstcb`  
 [v] Objekt, který se má volat.  
  
 `dwParam1`  
 [v] První parametr předat `IDebugThreadCall::ThreadCallHandler` metoda.  
  
 `dwParam2`  
 [v] Druhý parametr předat `IDebugThreadCall::ThreadCallHandler` metoda.  
  
 `dwParam3`  
 [v] Třetí parametr předat `IDebugThreadCall::ThreadCallHandler` metoda.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí metodu `HRESULT`. Možné hodnoty zahrnují hodnoty v následující tabulce, ale nejsou na ně omezeny.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`S_OK`|Metoda byla úspěšná.|  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda poskytuje mechanismus pro volajícího, aby spuštění kódu v vlákno ladicí program. Moduly jazyka a hostitelů obvykle použít tuto metodu implementovat podprocesy objekty nad jejich jednoho zařazování implementace.  
  
## <a name="see-also"></a>Viz také  
 [Idebugapplicationthread – rozhraní](../../winscript/reference/idebugapplicationthread-interface.md)   
 [Idebugthreadcall – rozhraní](../../winscript/reference/idebugthreadcall-interface.md)