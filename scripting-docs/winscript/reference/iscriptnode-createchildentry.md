---
title: 'Iscriptnode –:: CreateChildEntry | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptNode. CreateChildEntry
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptNode::CreateChildEntry
ms.assetid: b9682505-4457-40e9-8691-235843637506
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8fcc010efe8fcf30a8f467dd94befff54bc5fac5
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24795060"
---
# <a name="iscriptnode-createchildentry"></a>IScriptNode:: CreateChildEntry
Přidá podřízený instanci `IScriptEntry`.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT CreateChildEntry(  
   ULONG              isn,  
   DWORD              dwCookie,  
   LPCOLESTR          pszDelimiter,  
   IScriptEntry       **ppse  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `isn`  
 [v] Index podřízené v nadřazené.  
  
 `dwCookie`  
 [v] Definované aplikací hodnotou použité pro přidružení ke objekt hostitele podřízené položky.  
  
 `pszDelimiter`  
 [v] Adresa koncového ze skriptu bloku oddělovač. Pro analýzu, hostitele většinou používá oddělovač (například dvě jednoduchých uvozovek), na zjištění konce bloku skriptu.  
  
 Oddělovač, který umožňuje vytváření modul zajistit předzpracování skript. Modul může například nahraďte jednoduché uvozovky dvě jednoduchých uvozovek pro použití jako oddělovač. Modul určuje, jak se používá jako oddělovač.  
  
 Pokud oddělovač neoznačí konec bloku skriptu nastavena na hodnotu NULL.  
  
 `ppse`  
 [out] Proměnné, která přijímá ukazatel na adresu `IScriptEntry` rozhraní podřízené instance.  
  
 Pro `IScriptNode` objekty, které představují na webové stránce, tento parametr vrátí `IScriptEntry` instanci, která určuje blok skriptu.  
  
 Pro `IScriptEntry` objekty, které představují blok skriptu, vrátí tento parametr `IScriptEntry` instance, který určuje objekt funkce.  
  
 Pro `IScriptEntry` objektu objekty, které představují funkci, tato metoda selže.  
  
 Pro `IScriptScriptlet` objekty, tato metoda selže.  
  
## <a name="return-value"></a>Návratová hodnota  
 `HRESULT`. Možné hodnoty zahrnují hodnoty v následující tabulce, ale nejsou na ně omezeny.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`S_OK`|Metoda byla úspěšná.|  
  
## <a name="remarks"></a>Poznámky  
 `IScriptNode` Rozhraní představuje webovou stránku nebo jeho prvky. `IScriptEntry` Rozhraní (který je odvozen z `IScriptNode`) představuje blok skriptu nebo objekt funkce. `IScriptScriptlet` Rozhraní (který je odvozen z `IScriptEntry`) představuje obslužnou rutinu události.  
  
## <a name="see-also"></a>Viz také  
 [Iscriptnode – rozhraní](../../winscript/reference/iscriptnode-interface.md)   
 [Iscriptentry – rozhraní](../../winscript/reference/iscriptentry-interface.md)