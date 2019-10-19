---
title: 'Idebugapplicationnodeevents –:: Detach | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplicationNodeEvents.onDetach
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugApplicationNodeEvents::onDetach
ms.assetid: ef0cbe40-8c52-4bc9-bed0-9fc508abec6e
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bb1a33cbec8ef032c1c4fedba28ad4013e676f0d
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574681"
---
# <a name="idebugapplicationnodeeventsondetach"></a>IDebugApplicationNodeEvents::onDetach
Zpracovává událost, která signalizuje, že objekt uzlu ladění aplikace byl odpojen od nadřazeného uzlu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT onDetach();  
```  
  
#### <a name="parameters"></a>Parametry  
 Tato metoda nepřijímá žádné parametry.  
  
## <a name="return-value"></a>Návratová hodnota  
 Metoda vrací `HRESULT`. Možné hodnoty zahrnují hodnoty v následující tabulce, ale nejsou na ně omezeny.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`S_OK`|Metoda byla úspěšná.|  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda zpracovává událost, která signalizuje, že objekt uzlu ladění aplikace byl odpojen od nadřazeného uzlu.  
  
 Implementátori rozhraní `IDebugApplicationNode` vyvolávají tuto událost.  
  
## <a name="see-also"></a>Viz také:  
 @No__t_1 [rozhraní idebugapplicationnodeevents –](../../winscript/reference/idebugapplicationnodeevents-interface.md)  
 [Idebugapplicationnodeevents –:: attach](../../winscript/reference/idebugapplicationnodeevents-onattach.md)    
 [IDebugApplicationNode – rozhraní](../../winscript/reference/idebugapplicationnode-interface.md)