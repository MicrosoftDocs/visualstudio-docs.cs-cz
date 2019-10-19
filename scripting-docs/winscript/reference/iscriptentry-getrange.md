---
title: 'Iscriptentry –:: GetRange | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptEntry.GetRange
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptEntry::GetRange
ms.assetid: 3ac18f0a-b470-4f4d-b8f5-2da3fdef74f1
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0a6e1b1600c93aa05bbe9669fb57a23a8c9344a1
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575437"
---
# <a name="iscriptentrygetrange"></a>IScriptEntry::GetRange
Vrátí počáteční pozici a délku položky.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetRange(  
   ULONG              *pichMin  
   ULONG              *pcch  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pichMin`  
 mimo Pro `IScriptEntry` objekty, které určují blok skriptu, vrátí hodnotu 0.  
  
 Pro `IScriptEntry` objekty, které určují objekt funkce, vrátí počáteční pozici funkce v aktuálním bloku skriptu.  
  
 U objektů `IScriptScriptlet` vrátí hodnotu 0.  
  
 `pcch`  
 mimo Pro `IScriptEntry` objekty, které určují blok skriptu, vrátí délku textu.  
  
 Pro `IScriptEntry` objekty, které určují objekt funkce, vrátí délku definice funkce.  
  
 U `IScriptScriptlet` objektů vrátí délku položky.  
  
## <a name="return-value"></a>Návratová hodnota  
 @No__t_0. Možné hodnoty zahrnují hodnoty v následující tabulce, ale nejsou na ně omezeny.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`S_OK`|Metoda byla úspěšná.|  
  
## <a name="remarks"></a>Poznámky  
  
## <a name="see-also"></a>Viz také:  
 [IScriptEntry – rozhraní](../../winscript/reference/iscriptentry-interface.md)