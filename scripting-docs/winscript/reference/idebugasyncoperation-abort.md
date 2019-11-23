---
title: 'Idebugasyncoperation –:: Abort | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugAsyncOperation.Abort
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugAsyncOperation::Abort
ms.assetid: 232541c6-81b8-4eb7-96a7-a8e5fe087b31
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b9ca6c5e1498229c84dc28a13cda2cce77b58a4f
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573297"
---
# <a name="idebugasyncoperationabort"></a>IDebugAsyncOperation::Abort
Zruší operaci.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT Abort();  
```  
  
#### <a name="parameters"></a>Parametry  
 Tato metoda nepřijímá žádné parametry.  
  
## <a name="return-value"></a>Návratová hodnota  
 Metoda vrací `HRESULT`. Možné hodnoty zahrnují hodnoty v následující tabulce, ale nejsou na ně omezeny.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|S_OK|Metoda byla úspěšná.|  
|E_NOTIMPL|Operace se nedají zrušit.|  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda je obvykle volána v rámci vlákna ladicího programu pro zrušení operace, která nereaguje. Tato metoda způsobí, že je volána metoda `InProgressAbort` objektu `IDebugSyncOperation`.  
  
## <a name="see-also"></a>Viz také:  
   [rozhraní idebugasyncoperation –](../../winscript/reference/idebugasyncoperation-interface.md)  
 [Idebugasyncoperation –:: Start](../../winscript/reference/idebugasyncoperation-start.md)   
 [IDebugSyncOperation::InProgressAbort](../../winscript/reference/idebugsyncoperation-inprogressabort.md)