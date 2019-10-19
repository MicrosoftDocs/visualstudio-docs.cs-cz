---
title: 'Iscriptnode –:: CreateChildEntry | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: c58ff83c43a1418e6fb7bd8945afa181af60c68a
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573607"
---
# <a name="iscriptnode-createchildentry"></a>IScriptNode:: CreateChildEntry
Přidá podřízenou instanci `IScriptEntry`.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT CreateChildEntry(  
   ULONG              isn,  
   DWORD              dwCookie,  
   LPCOLESTR          pszDelimiter,  
   IScriptEntry       **ppse  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `isn`  
 pro Index podřízeného objektu v nadřazeném prvku.  
  
 `dwCookie`  
 pro Hodnota definovaná aplikací, která slouží k přidružení podřízené položky k objektu hostitele.  
  
 `pszDelimiter`  
 pro Adresa oddělovače bloku koncových skriptů. Pro účely analýzy hostitel obvykle používá oddělovač (například dvě jednoduché uvozovky) k detekci konce bloku skriptu.  
  
 Oddělovač umožňuje modulu vytváření skriptů poskytnout předzpracování. Modul může například nahradit jednoduché uvozovky dvěma jednoduchými uvozovkami pro použití jako oddělovač. Modul určuje, jak je oddělovač použit.  
  
 Nastavte na NULL, pokud oddělovač neoznačí konec bloku skriptu.  
  
 `ppse`  
 mimo Adresa proměnné, která přijímá ukazatel na `IScriptEntry` rozhraní podřízené instance.  
  
 U `IScriptNode` objektů, které reprezentují webovou stránku, vrátí tento parametr instanci `IScriptEntry`, která určuje blok skriptu.  
  
 U `IScriptEntry` objektů, které reprezentují blok skriptu, vrátí tento parametr instanci `IScriptEntry`, která určuje objekt funkce.  
  
 Pro `IScriptEntry` objekty, které reprezentují objekt funkce, tato metoda se nezdařila.  
  
 U `IScriptScriptlet` objektů Tato metoda selhává.  
  
## <a name="return-value"></a>Návratová hodnota  
 @No__t_0. Možné hodnoty zahrnují hodnoty v následující tabulce, ale nejsou na ně omezeny.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`S_OK`|Metoda byla úspěšná.|  
  
## <a name="remarks"></a>Poznámky  
 Rozhraní `IScriptNode` představuje webovou stránku nebo její prvky. Rozhraní `IScriptEntry` (které je odvozeno z `IScriptNode`) představuje buď blok skriptu, nebo objekt funkce. Rozhraní `IScriptScriptlet` (které je odvozeno z `IScriptEntry`) představuje obslužnou rutinu události.  
  
## <a name="see-also"></a>Viz také:  
 @No__t_1 [rozhraní iscriptnode –](../../winscript/reference/iscriptnode-interface.md)  
 [IScriptEntry – rozhraní](../../winscript/reference/iscriptentry-interface.md)