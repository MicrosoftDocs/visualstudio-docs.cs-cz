---
title: Iscriptnode –::D dstranit | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptNode.Delete
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptNode::Delete
ms.assetid: 6765ff80-a9a8-40a3-a669-7fcc284c87af
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3c3522e5543d333443de5b1287c994bf29de51c9
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576307"
---
# <a name="iscriptnodedelete"></a>IScriptNode::Delete
Odstraní tento strom objektů.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT Delete();  
```  
  
#### <a name="parameters"></a>Parametry  
 Metoda nepřijímá žádné parametry.  
  
## <a name="return-value"></a>Návratová hodnota  
 @No__t_0. Možné hodnoty zahrnují hodnoty v následující tabulce, ale nejsou na ně omezeny.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`S_OK`|Metoda byla úspěšná.|  
  
## <a name="remarks"></a>Poznámky  
 Po volání metody `Delete` musí metoda [iscriptnode –:: Alive](../../winscript/reference/iscriptnode-alive.md) indikovat, že uzel skriptu není aktivní.  
  
## <a name="see-also"></a>Viz také:  
 [IScriptNode – rozhraní](../../winscript/reference/iscriptnode-interface.md)