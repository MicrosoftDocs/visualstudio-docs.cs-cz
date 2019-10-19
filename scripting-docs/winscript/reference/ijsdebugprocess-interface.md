---
title: Rozhraní IJsDebugProcess | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: a7ad5525-55b7-4c68-a4f7-c508f7877712
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9200515b2c975fb1fa5b2acda7c261cb684d85b4
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577344"
---
# <a name="ijsdebugprocess-interface"></a>IJsDebugProcess – rozhraní
Poskytuje rutiny pro kontrolu a řízení cílového procesu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
IJsDebugProcess : public IUnknown;  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Name|Popis|  
|----------|-----------------|  
|[IJsDebugProcess::CreateBreakPoint – metoda](../../winscript/reference/ijsdebugprocess-createbreakpoint-method.md)|Nastaví zarážku na zadané pozici dokumentu.|  
|[IJsDebugProcess::CreateStackWalker – metoda](../../winscript/reference/ijsdebugprocess-createstackwalker-method.md)|Metoda factory pro prohlížeč zásobníku|  
|[IJsDebugProcess::PerformAsyncBreak – metoda](../../winscript/reference/ijsdebugprocess-performasyncbreak-method.md)|Umístí skriptovací stroj do režimu přerušení, což způsobí, že se přeruší na další instrukci skriptu.|  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** Jscript9diag. h  
  
## <a name="see-also"></a>Viz také:  
 [Referenční dokumentace skriptovacích rozhraní systému Windows](../../winscript/reference/windows-script-interfaces-reference.md)