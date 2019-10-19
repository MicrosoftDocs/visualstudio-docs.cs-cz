---
title: 'Idebugapplicationnodeevents –:: Attach | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplicationNodeEvents.onAttach
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugApplicationNodeEvents::onAttach
ms.assetid: b610c7e4-1c96-47ee-958e-3a1f5f621af3
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e45af6b931dad28a41f8f4453db9fab96405df3b
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574693"
---
# <a name="idebugapplicationnodeeventsonattach"></a>IDebugApplicationNodeEvents::onAttach
Zpracovává událost, která označuje, že objekt uzlu ladění aplikace byl připojen k nadřazenému uzlu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT onAttach(  
   IDebugApplicationNode*  prddpParent  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `prddpParent`  
 pro Uzel aplikace ladění, který je nadřazeným uzlem tohoto uzlu.  
  
## <a name="return-value"></a>Návratová hodnota  
 Metoda vrací `HRESULT`. Možné hodnoty zahrnují hodnoty v následující tabulce, ale nejsou na ně omezeny.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`S_OK`|Metoda byla úspěšná.|  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda zpracovává událost, která signalizuje, že objekt uzlu ladění aplikace byl připojen k nadřazenému uzlu.  
  
 Implementátori rozhraní `IDebugApplicationNode` vyvolávají tuto událost.  
  
## <a name="see-also"></a>Viz také:  
 @No__t_1 [rozhraní idebugapplicationnodeevents –](../../winscript/reference/idebugapplicationnodeevents-interface.md)  
 [Idebugapplicationnodeevents –:: detach](../../winscript/reference/idebugapplicationnodeevents-ondetach.md)    
 [IDebugApplicationNode – rozhraní](../../winscript/reference/idebugapplicationnode-interface.md)