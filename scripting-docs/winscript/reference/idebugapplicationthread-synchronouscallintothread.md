---
title: 'Idebugapplicationthread –:: SynchronousCallIntoThread | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: d545782f8103d10b38f3eb0d2f149c4ef3b9dc95
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574502"
---
# <a name="idebugapplicationthreadsynchronouscallintothread"></a>IDebugApplicationThread::SynchronousCallIntoThread
Poskytuje mechanismus pro volajícího pro spuštění kódu ve vlákně aplikace.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT SynchronousCallIntoThread(  
   IDebugThreadCall*  pstcb,  
   DWORD_PTR          dwParam1,  
   DWORD_PTR          dwParam2,  
   DWORD_PTR          dwParam3  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pstcb`  
 pro Objekt, který má být volán.  
  
 `dwParam1`  
 pro První parametr, který se předá metodě `IDebugThreadCall::ThreadCallHandler`.  
  
 `dwParam2`  
 pro Druhý parametr, který se předá metodě `IDebugThreadCall::ThreadCallHandler`.  
  
 `dwParam3`  
 pro Třetí parametr, který se má předat metodě `IDebugThreadCall::ThreadCallHandler`.  
  
## <a name="return-value"></a>Návratová hodnota  
 Metoda vrací `HRESULT`. Možné hodnoty zahrnují hodnoty v následující tabulce, ale nejsou na ně omezeny.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`S_OK`|Metoda byla úspěšná.|  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda poskytuje mechanismus pro volajícího pro spuštění kódu ve vlákně ladicího programu. Jazykové moduly a hostitelé obvykle používají tuto metodu k implementaci objektů s volnými vlákny nad svými implementacemi s jedním vláknem.  
  
## <a name="see-also"></a>Viz také:  
 @No__t_1 [rozhraní idebugapplicationthread –](../../winscript/reference/idebugapplicationthread-interface.md)  
 [IDebugThreadCall – rozhraní](../../winscript/reference/idebugthreadcall-interface.md)