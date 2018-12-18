---
title: IScriptNode::GetChild | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptNode.GetChild
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptNode::GetChild
ms.assetid: 8cb3f8b0-958b-40bb-a91a-49a788661861
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d127b1b8a8db0c6d272e50d33b523fbe182a9e21
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24796419"
---
# <a name="iscriptnodegetchild"></a>IScriptNode::GetChild
Vrací podřízeného, který je v zadaném indexu v uzlu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetChild(  
   ULONG              isn,  
   IScriptNode        **ppsn  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `isn`  
 [v] Index podřízené v nadřazené.  
  
 `ppsn`  
 [out] Proměnné, která přijímá ukazatel na adresu `IScriptNode` rozhraní podřízené instance.  
  
 Pro `IScriptNode` objekty, které představují na webové stránce, tento parametr vrátí objekt, který obsahuje blok skriptu.  
  
 Pro `IScriptEntry` objekty, které určují blok skriptu, tento parametr vrátí objekt, který určuje funkci.  
  
## <a name="return-value"></a>Návratová hodnota  
 `HRESULT`. Možné hodnoty zahrnují hodnoty v následující tabulce, ale nejsou na ně omezeny.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`S_OK`|Metoda byla úspěšná.|  
  
## <a name="remarks"></a>Poznámky  
 Pro `IScriptEntry` objekty, které určují objekt funkce a `IScriptScriptlet` objekty, tato metoda selže, protože nejsou k dispozici žádné podřízené položky.  
  
## <a name="see-also"></a>Viz také  
 [Iscriptnode – rozhraní](../../winscript/reference/iscriptnode-interface.md)