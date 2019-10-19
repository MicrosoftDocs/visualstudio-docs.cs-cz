---
title: 'IDebugApplication –:: SynchronousCallInDebuggerThread | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplication.SynchronousCallInDebuggerThread
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplication::SynchronousCallInDebuggerThread
ms.assetid: 9daa1722-f25a-4691-aefc-fd28672fb883
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 134717b6ce30c87ccfb4bbb50ffe958717ae757f
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574590"
---
# <a name="idebugapplicationsynchronouscallindebuggerthread"></a>IDebugApplication::SynchronousCallInDebuggerThread
Poskytuje mechanismus pro volajícího pro spuštění kódu ve vlákně ladicího programu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT SynchronousCallInDebuggerThread(  
   IDebugThreadCall*  pptc,  
   DWORD_PTR          dwParam1,  
   DWORD_PTR          dwParam2,  
   DWORD_PTR          dwParam3  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pptc`  
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
 Jazykové moduly a hostitelé obvykle používají tuto metodu k implementaci objektů s volnými vlákny nad svými implementacemi s jedním vláknem.  
  
## <a name="see-also"></a>Viz také:  
 @No__t_1 [rozhraní IDebugApplication –](../../winscript/reference/idebugapplication-interface.md)  
 [IDebugThreadCall – rozhraní](../../winscript/reference/idebugthreadcall-interface.md)