---
title: 'IDebugApplicationNode –:: Close | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplicationNode.Close
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplicationNode::Close
ms.assetid: ea8db480-2344-4c7b-960c-4fa97fa6c1b7
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 928dc94a5d700b2cad6a7acfb59a409240be7dc3
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574831"
---
# <a name="idebugapplicationnodeclose"></a>IDebugApplicationNode::Close
Způsobí, že tato aplikace uvolní všechny odkazy a vstoupí do neaktivního stavu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT Close();  
```  
  
#### <a name="parameters"></a>Parametry  
 Tato metoda nepřijímá žádné parametry.  
  
## <a name="return-value"></a>Návratová hodnota  
 Metoda vrací `HRESULT`. Možné hodnoty zahrnují hodnoty v následující tabulce, ale nejsou na ně omezeny.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`S_OK`|Metoda byla úspěšná.|  
  
## <a name="remarks"></a>Poznámky  
 Obvykle vlastník aplikace volá tuto metodu, když dojde k ukončení aplikace.  
  
## <a name="see-also"></a>Viz také:  
 [IDebugApplicationNode – rozhraní](../../winscript/reference/idebugapplicationnode-interface.md)