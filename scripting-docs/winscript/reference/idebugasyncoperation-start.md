---
title: 'Idebugasyncoperation –:: Start | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugAsyncOperation.Start
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugAsyncOperation::Start
ms.assetid: a7272364-28e0-48ae-8405-b8bce8a6b9fd
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 485eb34ebe200e7f7898d9338effed37cbf2aa10
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573246"
---
# <a name="idebugasyncoperationstart"></a>IDebugAsyncOperation::Start
Způsobí zahájení asynchronní operace.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT Start(  
   IDebugAsyncOperationCallBack*  padocb  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `padocb`  
 Rozhraní zpětného volání, které přijímá události stavu z této operace.  
  
## <a name="return-value"></a>Návratová hodnota  
 Metoda vrací `HRESULT`. Možné hodnoty zahrnují hodnoty v následující tabulce, ale nejsou na ně omezeny.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`S_OK`|Metoda byla úspěšná.|  
|`E_UNEXPECTED`|Operace již probíhá.|  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda způsobí, že `IDebugSyncOperation::Execute` být asynchronně volána ve vlákně získaném z `IDebugSyncOperation::GetTargetThread`. Tato metoda by měla být volána pouze v rámci vlákna ladicího programu; v opačném případě nebude vrácena, dokud nebude operace dokončena.  
  
## <a name="see-also"></a>Viz také:  
 [Idebugasyncoperation –:: Abort](../../winscript/reference/idebugasyncoperation-abort.md)   
   [rozhraní idebugasyncoperation –](../../winscript/reference/idebugasyncoperation-interface.md)  
 [IDebugSyncOperation –:: Execute](../../winscript/reference/idebugsyncoperation-execute.md)   
 [IDebugSyncOperation::GetTargetThread](../../winscript/reference/idebugsyncoperation-gettargetthread.md)