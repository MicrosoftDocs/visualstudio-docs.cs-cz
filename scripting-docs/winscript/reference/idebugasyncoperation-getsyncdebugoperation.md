---
title: IDebugAsyncOperation::GetSyncDebugOperation | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugAsyncOperation.GetSyncDebugOperation
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugAsyncOperation::GetSyncDebugOperation
ms.assetid: ff89a3bc-57d7-4cb9-9818-8d73ed71af73
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ae53dde2b7e48a4bf67cbd7aa5d70904c57d90f2
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24793815"
---
# <a name="idebugasyncoperationgetsyncdebugoperation"></a>IDebugAsyncOperation::GetSyncDebugOperation
Vrátí synchronní ladění operaci přidružené k tomuto objektu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetSyncDebugOperation(  
   IDebugSyncOperation**  ppsdo  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppsdo`  
 [out] Operace synchronní ladění přidružené k tomuto objektu.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí metodu `HRESULT`. Možné hodnoty zahrnují hodnoty v následující tabulce, ale nejsou na ně omezeny.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`S_OK`|Metoda byla úspěšná.|  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda vrátí synchronní ladění operaci přidružené k tomuto objektu.  
  
## <a name="see-also"></a>Viz také  
 [Idebugasyncoperation – rozhraní](../../winscript/reference/idebugasyncoperation-interface.md)