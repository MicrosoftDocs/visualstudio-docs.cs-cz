---
title: 'Iscriptentry –:: SetBody | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptEntry.SetBody
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptEntry::SetBody
ms.assetid: 719062e4-98e4-4a7b-946d-6e5dbbcc5225
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1af865c8366481204ee413377a083b09d8c97383
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575383"
---
# <a name="iscriptentrysetbody"></a>IScriptEntry::SetBody
Nastaví text, který se nachází v těle `IScriptEntry` bloku skriptu nebo `IScriptScriptlet` skriptletu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT SetBody(  
   LPCOLESTR          psz  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `psz`  
 pro Pro `IScriptEntry` blok skriptu `psz` je text uzavřený ve značkách skriptu.  
  
 Pro blok `IScriptEntry` funkce je `psz` tělo funkce.  
  
 V případě objektu `IScriptScriptlet` (který je odvozen z `IScriptEntry`) je `psz` text skriptu pro skriptletu.  
  
## <a name="return-value"></a>Návratová hodnota  
 @No__t_0. Možné hodnoty zahrnují hodnoty v následující tabulce, ale nejsou na ně omezeny.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`S_OK`|Metoda byla úspěšná.|  
  
## <a name="remarks"></a>Poznámky  
  
## <a name="see-also"></a>Viz také:  
 @No__t_1 [rozhraní iscriptentry –](../../winscript/reference/iscriptentry-interface.md)  
 [IScriptEntry::GetBody](../../winscript/reference/iscriptentry-getbody.md)