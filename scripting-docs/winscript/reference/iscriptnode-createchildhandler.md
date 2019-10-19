---
title: 'Iscriptnode –:: CreateChildHandler | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptNode.CreateChildHandler
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptNode::CreateChildHandler
ms.assetid: 4ce5eb10-1a3f-43b0-a4b7-599a397ed3a2
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9e024bb7d6a81b35994edddfe9e71666b0ee8df0
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573603"
---
# <a name="iscriptnodecreatechildhandler"></a>IScriptNode::CreateChildHandler
Přidá skriptletu jako podřízenou instanci `IScriptNode`.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT CreateChildHandler(  
   LPCOLESTR          pszDefaultName,  
   LPCOLESTR          *prgpszNames,  
   ULONG              cpszNames,  
   LPCOLESTR          pszEvent,  
   LPCOLESTR          pszDelimiter,  
   ITypeInfo*         ptiSignature,  
   ULONG              iMethodSignature,  
   ULONG              isn,  
   DWORD              dwCookie,  
   IScriptEntry       **ppse  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pszDefaultName`  
 pro Adresa výchozího názvu, který se má přidružit k skriptletu.  
  
 `prgpszNames`  
 [in, size_is (`cpszNames`)] Seznam identifikátorů z plně kvalifikovaného názvu na hostiteli.  
  
 `cpszNames`  
 pro Počet identifikátorů v parametru `prgpszNames`.  
  
 `pszEvent`  
 pro Adresa vyrovnávací paměti, která identifikuje název události přidružené k skriptletu.  
  
 `pszDelimiter`  
 pro Adresa oddělovače bloku koncových skriptů. Pro účely analýzy hostitel obvykle používá oddělovač (například dvě jednoduché uvozovky) k detekci konce bloku skriptu.  
  
 Oddělovač umožňuje předzpracování modulu vytváření skriptů. Modul může například nahradit jednoduché uvozovky dvěma jednoduchými uvozovkami pro použití jako oddělovač. Modul určuje, jak je oddělovač použit.  
  
 Nastavte na hodnotu NULL, pokud není použit žádný oddělovač k identifikaci konce bloku skriptu.  
  
 `ptiSignature`  
 pro Informace o typu pro objekt funkce.  
  
 `iMethodSignature`  
 pro Index funkce v parametru `ITypeInfo``ptiSignature`.  
  
 `isn`  
 pro Index podřízeného objektu v nadřazeném prvku.  
  
 `dwCookie`  
 pro Hodnota definovaná aplikací, která se používá k přidružení položky k objektu hostitele.  
  
 `ppse`  
 mimo Adresa proměnné, která přijímá ukazatel na `IScriptEntry` rozhraní podřízené instance.  
  
## <a name="return-value"></a>Návratová hodnota  
 @No__t_0. Možné hodnoty zahrnují hodnoty v následující tabulce, ale nejsou na ně omezeny.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`S_OK`|Metoda byla úspěšná.|  
  
## <a name="remarks"></a>Poznámky  
 Skriptletu určuje obslužnou rutinu události. Tato metoda vytvoří skriptletu, pokud je volána objektem `IScriptNode`, který představuje webovou stránku. Tato metoda není úspěšná, pokud je volána jinými rozhraními.  
  
## <a name="see-also"></a>Viz také:  
 @No__t_1 [rozhraní iscriptnode –](../../winscript/reference/iscriptnode-interface.md)  
 [IScriptEntry – rozhraní](../../winscript/reference/iscriptentry-interface.md)