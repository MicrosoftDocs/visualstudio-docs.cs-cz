---
title: IDebugSyncOperation::Execute | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 69e07c646bfa176f5e2dc07539f301a8ef5c5273
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24794238"
---
# <a name="idebugsyncoperationexecute"></a>IDebugSyncOperation::Execute
Synchronně provede operaci a vrátí.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT Execute(  
   IUnknown**  ppunkResult  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppunkResult`  
 [out] Parametr objektu vrácená operací.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí metodu `HRESULT`. Možné hodnoty zahrnují hodnoty v následující tabulce, ale nejsou na ně omezeny.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`S_OK`|Metoda byla úspěšná.|  
|`E_ABORT`|Operace byla přerušena při volání `IDebugSyncOperation::InProgressAbort` metoda.|  
  
## <a name="remarks"></a>Poznámky  
 Proces Debug Manager ve voláních vlákno cíl `Execute` metoda synchronně.  
  
## <a name="see-also"></a>Viz také  
 [Idebugsyncoperation – rozhraní](../../winscript/reference/idebugsyncoperation-interface.md)