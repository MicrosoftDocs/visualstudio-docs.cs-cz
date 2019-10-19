---
title: 'IDebugApplicationNode –:: Attach | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplicationNode.Attach
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplicationNode::Attach
ms.assetid: f4aad4ae-5bb0-4b5e-8f70-912a677f8f7a
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 30d4e189ec878def1cfd88517654955cd2d1aa12
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574776"
---
# <a name="idebugapplicationnodeattach"></a>IDebugApplicationNode::Attach
Přidá tento uzel aplikace do zadaného stromu projektu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT Attach(  
   IDebugApplicationNode*  pdanParent  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pdanParent`  
 pro Strom projektu, do kterého má být přidán tento uzel aplikace  
  
## <a name="return-value"></a>Návratová hodnota  
 Metoda vrací `HRESULT`. Možné hodnoty zahrnují hodnoty v následující tabulce, ale nejsou na ně omezeny.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`S_OK`|Metoda byla úspěšná.|  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda přidá tento uzel aplikace do stromu projektu pomocí `pdanParent` jako nadřazeného objektu. Pokud je `pdanParent` `NULL`, bude tento uzel aplikace uzlem nejvyšší úrovně.  
  
## <a name="see-also"></a>Viz také:  
 [IDebugApplicationNode –::D etach](../../winscript/reference/idebugapplicationnode-detach.md)    
 [IDebugApplicationNode – rozhraní](../../winscript/reference/idebugapplicationnode-interface.md)