---
title: IDebugApplicationNode::Close | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 6d50d1e9a22c3d64d65847922090dfab0c33ab32
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24793800"
---
# <a name="idebugapplicationnodeclose"></a>IDebugApplicationNode::Close
Způsobí, že tuto aplikaci chcete uvolnit všechny odkazy a zadejte neaktivním stavu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT Close();  
```  
  
#### <a name="parameters"></a>Parametry  
 Tato metoda nepřijímá žádné parametry.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí metodu `HRESULT`. Možné hodnoty zahrnují hodnoty v následující tabulce, ale nejsou na ně omezeny.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`S_OK`|Metoda byla úspěšná.|  
  
## <a name="remarks"></a>Poznámky  
 Vlastník aplikace obvykle volá tuto metodu při ukončení aplikace.  
  
## <a name="see-also"></a>Viz také  
 [Idebugapplicationnode – rozhraní](../../winscript/reference/idebugapplicationnode-interface.md)