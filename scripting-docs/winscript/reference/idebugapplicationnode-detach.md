---
title: IDebugApplicationNode –::D etach | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplicationNode.Detach
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplicationNode::Detach
ms.assetid: 36bb3e54-a4df-48d5-a6de-3b8d4c0e98a8
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3ffb422bec21bec65f1550368d898608a5f65015
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574810"
---
# <a name="idebugapplicationnodedetach"></a>IDebugApplicationNode::Detach
Odebere tento uzel aplikace ze stromové struktury projektu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT Detach();  
```  
  
#### <a name="parameters"></a>Parametry  
 Tato metoda nepřijímá žádné parametry.  
  
## <a name="return-value"></a>Návratová hodnota  
 Metoda vrací `HRESULT`. Možné hodnoty zahrnují hodnoty v následující tabulce, ale nejsou na ně omezeny.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`S_OK`|Metoda byla úspěšná.|  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda odebere tento uzel aplikace ze stromové struktury projektu.  
  
## <a name="see-also"></a>Viz také:  
 [IDebugApplicationNode –:: Attach](../../winscript/reference/idebugapplicationnode-attach.md)    
 [IDebugApplicationNode – rozhraní](../../winscript/reference/idebugapplicationnode-interface.md)