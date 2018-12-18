---
title: Ijsdebugstackwalker – rozhraní | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 3fe30394-49c8-48e9-bde9-ffe5d79b2121
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dbea11bf1188d148818ea8a082bceec76c704c2b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24794718"
---
# <a name="ijsdebugstackwalker-interface"></a>IJsDebugStackWalker – rozhraní
Představuje zásobníku walkera zadaný vlákna.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IJsDebugStackWalker : public IUnknown;  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[Ijsdebugstackwalker::GetNext – metoda](../../winscript/reference/ijsdebugstackwalker-getnext-method.md)|Získá další rámečku.|  
  
## <a name="remarks"></a>Poznámky  
 Zásobník walkers lze vytvořit pouze při cíl se zastaví a jsou neplatné, jakmile tento cílový proces pokračuje znovu.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** jscript9diag.h  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace skriptovacích rozhraní systému Windows](../../winscript/reference/windows-script-interfaces-reference.md)