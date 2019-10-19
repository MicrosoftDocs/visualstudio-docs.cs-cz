---
title: 'IDebugApplication –:: CreateAsyncDebugOperation | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplication.CreateAsyncDebugOperation
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplication::CreateAsyncDebugOperation
ms.assetid: bc32b101-6364-4498-8458-bd5f3ab5ad94
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1feb8207fb7e7a7faf4427be189c4952139ef32c
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575563"
---
# <a name="idebugapplicationcreateasyncdebugoperation"></a>IDebugApplication::CreateAsyncDebugOperation
Poskytuje asynchronní přístup k dané synchronní operaci ladění.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT CreateAsyncDebugOperation(  
   IDebugSyncOperation*    psdo,  
   IDebugAsyncOperation**  ppado  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `psdo`  
 pro Objekt synchronní operace ladění.  
  
 `ppado`  
 mimo Objekt asynchronní operace ladění.  
  
## <a name="return-value"></a>Návratová hodnota  
 Metoda vrací `HRESULT`. Možné hodnoty zahrnují hodnoty v následující tabulce, ale nejsou na ně omezeny.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`S_OK`|Metoda byla úspěšná.|  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda umožňuje, aby jazykové moduly vyhodnotily výrazy asynchronně bez explicitní synchronizace s vláknem ladicího programu. Další informace naleznete v tématu rozhraní [IDebugSyncOperation –](../../winscript/reference/idebugsyncoperation-interface.md) a [rozhraní idebugasyncoperation –](../../winscript/reference/idebugasyncoperation-interface.md).  
  
## <a name="see-also"></a>Viz také:  
 @No__t_1 [rozhraní IDebugApplication –](../../winscript/reference/idebugapplication-interface.md)  
 @No__t_1 [rozhraní IDebugSyncOperation –](../../winscript/reference/idebugsyncoperation-interface.md)  
 [IDebugAsyncOperation – rozhraní](../../winscript/reference/idebugasyncoperation-interface.md)