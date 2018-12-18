---
title: Ijsdebugprocess – rozhraní | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: a7ad5525-55b7-4c68-a4f7-c508f7877712
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f2a81104f51ca1a66c493779146b7eaa102ea300
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24794724"
---
# <a name="ijsdebugprocess-interface"></a>IJsDebugProcess – rozhraní
Poskytuje rutiny pro kontroly a řízení tento cílový proces.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IJsDebugProcess : public IUnknown;  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[Ijsdebugprocess::createbreakpoint – metoda](../../winscript/reference/ijsdebugprocess-createbreakpoint-method.md)|Nastaví zarážce na pozici zadaný dokument.|  
|[Ijsdebugprocess::createstackwalker – metoda](../../winscript/reference/ijsdebugprocess-createstackwalker-method.md)|Metoda Factory pro walkera zásobníku.|  
|[Ijsdebugprocess::performasyncbreak – metoda](../../winscript/reference/ijsdebugprocess-performasyncbreak-method.md)|Skriptovací stroj převádí v režimu pozastavení způsobuje ho na přerušení na další skript instrukcí.|  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** jscript9diag.h  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace skriptovacích rozhraní systému Windows](../../winscript/reference/windows-script-interfaces-reference.md)