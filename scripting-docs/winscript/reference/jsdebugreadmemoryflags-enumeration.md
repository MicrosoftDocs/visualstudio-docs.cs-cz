---
title: Výčet JsDebugReadMemoryFlags | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- JsDebugReadMemoryFlags
apilocation:
- jscript9diag.dll
ms.assetid: 0d98d154-9cb1-49de-b2df-a2d029d343b7
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a1757678f20a01221ae46e1535d3190cd463d724
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571699"
---
# <a name="jsdebugreadmemoryflags-enumeration"></a>Výčet JsDebugReadMemoryFlags
Příznaky pro určení chování při čtení paměti  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
enum JsDebugReadMemoryFlags{   None = 0,   JsDebugAllowPartialRead= 0x1} JsDebugReadMemoryFlags;  
```  
  
## <a name="members"></a>Členové  
  
### <a name="values"></a>Hodnoty  
  
|Name|Popis|  
|----------|-----------------|  
|`JsDebugAllowPartialRead`|Označuje, že volající chce, aby operace čtení proběhla úspěšně, pokud byla pouze část paměti úspěšně načtena. Pokud je tato možnost nastavena, bude vyvolána chyba E_JsDEBUG_INVALID_MEMORY_ADDRESS pouze v případě, že adresa je neplatná. Pokud je tento příznak nejasný, bude vyvolána chyba E_JsDEBUG_INVALID_MEMORY_ADDRESS, pokud kterákoli část požadované paměti byla nečitelná.|  
|`None`|Označuje, že volající chce výchozí chování pro readMemory –.|  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** Jscript9diag. h  
  
## <a name="see-also"></a>Viz také:  
 [Referenční dokumentace skriptovacích rozhraní systému Windows](../../winscript/reference/windows-script-interfaces-reference.md)