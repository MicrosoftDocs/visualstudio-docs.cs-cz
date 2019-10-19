---
title: 'IDebugSyncOperation –:: Execute | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugSyncOperation.Execute
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugSyncOperation::Execute
ms.assetid: a45b8c7d-c51a-4098-877f-fbec2f1f6947
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 25da02e6736cc2f8ac27c82f922bd515e791bef1
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576698"
---
# <a name="idebugsyncoperationexecute"></a>IDebugSyncOperation::Execute
Synchronně provede operaci a vrátí.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT Execute(  
   IUnknown**  ppunkResult  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppunkResult`  
 mimo Parametr objektu vrácený operací.  
  
## <a name="return-value"></a>Návratová hodnota  
 Metoda vrací `HRESULT`. Možné hodnoty zahrnují hodnoty v následující tabulce, ale nejsou na ně omezeny.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`S_OK`|Metoda byla úspěšná.|  
|`E_ABORT`|Operace byla přerušena voláním metody `IDebugSyncOperation::InProgressAbort`.|  
  
## <a name="remarks"></a>Poznámky  
 Správce ladění procesu v cílovém vlákně volá metodu `Execute` synchronně.  
  
## <a name="see-also"></a>Viz také:  
 [IDebugSyncOperation – rozhraní](../../winscript/reference/idebugsyncoperation-interface.md)