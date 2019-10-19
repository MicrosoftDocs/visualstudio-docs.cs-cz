---
title: 'Iscriptnode –:: getpodřízená | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 27ddde527be1ea4148e4166581ab2cb1a71d15f7
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573556"
---
# <a name="iscriptnodegetchild"></a>IScriptNode::GetChild
Vrátí podřízenou položku, která se nachází na zadaném indexu v uzlu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetChild(  
   ULONG              isn,  
   IScriptNode        **ppsn  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `isn`  
 pro Index podřízeného objektu v nadřazeném prvku.  
  
 `ppsn`  
 mimo Adresa proměnné, která přijímá ukazatel na `IScriptNode` rozhraní podřízené instance.  
  
 U `IScriptNode` objektů, které reprezentují webovou stránku, vrátí tento parametr objekt, který obsahuje blok skriptu.  
  
 Pro `IScriptEntry` objekty, které určují blok skriptu, tento parametr vrátí objekt, který určuje funkci.  
  
## <a name="return-value"></a>Návratová hodnota  
 @No__t_0. Možné hodnoty zahrnují hodnoty v následující tabulce, ale nejsou na ně omezeny.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`S_OK`|Metoda byla úspěšná.|  
  
## <a name="remarks"></a>Poznámky  
 Pro `IScriptEntry` objekty, které určují objekt funkce a pro `IScriptScriptlet` objekty, tato metoda se nezdařila, protože neexistují žádné podřízené položky.  
  
## <a name="see-also"></a>Viz také:  
 [IScriptNode – rozhraní](../../winscript/reference/iscriptnode-interface.md)