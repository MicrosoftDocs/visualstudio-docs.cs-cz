---
title: Výčet Jsdebugreadmemoryflags | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 7efb5170bf0314e95b1acded39a897c2236a29ff
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24796266"
---
# <a name="jsdebugreadmemoryflags-enumeration"></a>Výčet JsDebugReadMemoryFlags
Příznaky pro určení chování při čtení paměti  
  
## <a name="syntax"></a>Syntaxe  
  
```  
enum JsDebugReadMemoryFlags{   None = 0,   JsDebugAllowPartialRead= 0x1} JsDebugReadMemoryFlags;  
```  
  
## <a name="members"></a>Členové  
  
### <a name="values"></a>Hodnoty  
  
|Název|Popis|  
|----------|-----------------|  
|`JsDebugAllowPartialRead`|Označuje, že volající chce operace čtení úspěšné, pouze pokud část paměti číst úspěšně. Pokud je toto nastaveno, bude vyvolána chybu E_JsDEBUG_INVALID_MEMORY_ADDRESS pouze pokud 'Adresa' je neplatný. Pokud tento příznak není zaškrtnuto, je-li jakékoli její části velikost paměti požadované nečitelná bude vyvolána chyba E_JsDEBUG_INVALID_MEMORY_ADDRESS.|  
|`None`|Označuje, že volající chce pro readmemory – použije se výchozí chování.|  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** jscript9diag.h  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace skriptovacích rozhraní systému Windows](../../winscript/reference/windows-script-interfaces-reference.md)