---
title: Rozhraní IJsDebugBreakPoint | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 791c8488-21e7-46be-b1b4-fe74117cf200
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e6bb4e12f0e08baf1842d251347f35265425b999
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577682"
---
# <a name="ijsdebugbreakpoint-interface"></a>IJsDebugBreakPoint – rozhraní
Představuje zarážku.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
IJsDebugBreakPoint : public IUnknown;  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Name|Popis|  
|----------|-----------------|  
|[IJsDebugBreakPoint::Delete – metoda](../../winscript/reference/ijsdebugbreakpoint-delete-method.md)|Odstraní zarážku.|  
|[IJsDebugBreakPoint::Disable – metoda](../../winscript/reference/ijsdebugbreakpoint-disable-method.md)|Zakáže zarážku.|  
|[IJsDebugBreakPoint::Enable – metoda](../../winscript/reference/ijsdebugbreakpoint-enable-method.md)|Povoluje zarážku.|  
|[IJsDebugBreakPoint::GetDocumentPosition – metoda](../../winscript/reference/ijsdebugbreakpoint-getdocumentposition-method.md)|Vrátí pozici příkazu, kde byla zarážka svázána.|  
|[IJsDebugBreakPoint::IsEnabled – metoda](../../winscript/reference/ijsdebugbreakpoint-isenabled-method.md)|Určuje, zda je povolena zarážka.|  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** Jscript9diag. h  
  
## <a name="see-also"></a>Viz také:  
 [Referenční dokumentace skriptovacích rozhraní systému Windows](../../winscript/reference/windows-script-interfaces-reference.md)