---
title: IDebugApplicationNode::Detach | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 409501172a1ee4b8f00562adaee0d533d517e449
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24793752"
---
# <a name="idebugapplicationnodedetach"></a>IDebugApplicationNode::Detach
Tento uzel aplikace odebere ze stromu projektu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT Detach();  
```  
  
#### <a name="parameters"></a>Parametry  
 Tato metoda nepřijímá žádné parametry.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí metodu `HRESULT`. Možné hodnoty zahrnují hodnoty v následující tabulce, ale nejsou na ně omezeny.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`S_OK`|Metoda byla úspěšná.|  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda odebere tento uzel aplikace ze stromu projektu.  
  
## <a name="see-also"></a>Viz také  
 [IDebugApplicationNode::Attach](../../winscript/reference/idebugapplicationnode-attach.md)   
 [Idebugapplicationnode – rozhraní](../../winscript/reference/idebugapplicationnode-interface.md)