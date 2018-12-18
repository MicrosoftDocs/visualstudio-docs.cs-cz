---
title: IScriptNode::GetParent | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptNode.GetParent
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptNode::GetParent
ms.assetid: 0fb813f6-ab94-46b2-b0cf-ef5d1cd38ae4
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1da2f68de40a66b98b97ab7c7eb1d63748f1e07a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24796245"
---
# <a name="iscriptnodegetparent"></a>IScriptNode::GetParent
Vrátí `IScriptNode` objekt, který je nadřazeného objektu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetParent(  
   IScriptNode       **ppsnParent  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppsnParent`  
 [out] Proměnné, která přijímá ukazatel na adresu `IScriptNode` rozhraní nadřazená instance.  
  
 Pokud třída implementuje `IScriptEntry` nebo `IScriptScriptlet`, `IScriptNode` se vrátí objekt.  
  
 Pokud třída implementuje `IScriptNode` (představující webovou stránku), vrátí se hodnota NULL.  
  
## <a name="return-value"></a>Návratová hodnota  
 `HRESULT`. Možné hodnoty zahrnují hodnoty v následující tabulce, ale nejsou na ně omezeny.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`S_OK`|Metoda byla úspěšná.|  
  
## <a name="remarks"></a>Poznámky  
  
## <a name="see-also"></a>Viz také  
 [Iscriptnode – rozhraní](../../winscript/reference/iscriptnode-interface.md)