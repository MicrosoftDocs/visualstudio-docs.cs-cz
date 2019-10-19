---
title: 'Idebugasyncoperation –:: GetResult | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugAsyncOperation.GetResult
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugAsyncOperation::GetResult
ms.assetid: 56d43365-6b12-4213-a97c-953c40d7b7f6
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 55c51649a5bc3094dd306166e013a892ce67e236
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573281"
---
# <a name="idebugasyncoperationgetresult"></a>IDebugAsyncOperation::GetResult
Poskytuje návratovou hodnotu a návratový parametr objektu z operace synchronního ladění.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetResult(  
   HRESULT*    phrResult,  
   IUnknown**  ppunkResult  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `phrResult`  
 mimo Pokud je operace dokončena, `phrResult` je návratovou hodnotou `IDebugSyncOperation::Execute`.  
  
 `ppunkResult`  
 mimo Pokud je operace dokončena, `ppunkResult` je parametr objektu vrácený operací.  
  
## <a name="return-value"></a>Návratová hodnota  
 Metoda vrací `HRESULT`. Možné hodnoty zahrnují hodnoty v následující tabulce, ale nejsou na ně omezeny.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`S_OK`|Metoda byla úspěšná.|  
|`E_PENDING`|Operace nebyla dokončena.|  
  
## <a name="remarks"></a>Poznámky  
 Pokud byla operace dokončena, vrátí tato metoda `HRESULT` a parametr objektu z `IDebugSyncOperation::Execute`.  
  
## <a name="see-also"></a>Viz také:  
 @No__t_1 [rozhraní idebugasyncoperation –](../../winscript/reference/idebugasyncoperation-interface.md)  
 [IDebugSyncOperation::Execute](../../winscript/reference/idebugsyncoperation-execute.md)