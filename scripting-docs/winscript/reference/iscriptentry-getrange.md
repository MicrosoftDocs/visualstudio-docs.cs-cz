---
title: IScriptEntry::GetRange | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 0ae0ee34298e03fdd2e9c6bc841d9fbe90967e8f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24794865"
---
# <a name="iscriptentrygetrange"></a>IScriptEntry::GetRange
Vrátí počáteční pozice a délka záznamu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetRange(  
   ULONG              *pichMin  
   ULONG              *pcch  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pichMin`  
 [out] Pro `IScriptEntry` objekty, které určují blok skriptu, vrátí hodnotu 0.  
  
 Pro `IScriptEntry` objekty, které určují objekt funkce, vrátí počáteční pozici funkce v aktuálním bloku skriptu.  
  
 Pro `IScriptScriptlet` objekty, vrátí hodnotu 0.  
  
 `pcch`  
 [out] Pro `IScriptEntry` objekty, které určují blok skriptu, vrátí délku textu.  
  
 Pro `IScriptEntry` objekty, které určují objekt funkce, vrátí délku v definici funkce.  
  
 Pro `IScriptScriptlet` objekty, vrátí délku položky.  
  
## <a name="return-value"></a>Návratová hodnota  
 `HRESULT`. Možné hodnoty zahrnují hodnoty v následující tabulce, ale nejsou na ně omezeny.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`S_OK`|Metoda byla úspěšná.|  
  
## <a name="remarks"></a>Poznámky  
  
## <a name="see-also"></a>Viz také  
 [Iscriptentry – rozhraní](../../winscript/reference/iscriptentry-interface.md)