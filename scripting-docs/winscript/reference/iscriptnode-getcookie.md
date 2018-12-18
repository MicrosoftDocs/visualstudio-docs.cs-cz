---
title: IScriptNode::GetCookie | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptNode.GetCookie
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptNode::GetCookie
ms.assetid: 007339c6-a73a-4147-b3c0-cc041e467ecd
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fa68f528aeb405ca150cff717ab5e4bebb82027a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24796257"
---
# <a name="iscriptnodegetcookie"></a>IScriptNode::GetCookie
Vrátí hodnotu definované aplikací, který se používá pro přidružení skriptlet objekt hostitele.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetCookie(  
   DWORD              *pdwCookie  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pdwCookie`  
 [out] Pro `IScriptEntry` objektu, vrátí hodnotu souboru cookie definované aplikací.  
  
 Pro `IScriptNode` objekt, který představuje webovou stránku, vrátí hodnotu 0.  
  
## <a name="return-value"></a>Návratová hodnota  
 `HRESULT`. Možné hodnoty zahrnují hodnoty v následující tabulce, ale nejsou na ně omezeny.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`S_OK`|Metoda byla úspěšná.|  
  
## <a name="remarks"></a>Poznámky  
  
## <a name="see-also"></a>Viz také  
 [Iscriptnode – rozhraní](../../winscript/reference/iscriptnode-interface.md)