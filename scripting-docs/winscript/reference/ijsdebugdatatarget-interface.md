---
title: Ijsdebugdatatarget – rozhraní | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: a9b784d6-958f-4d55-b3f6-c2d6b260a16b
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 94e158ced0da6d59bfcadeb87bf206c94a6099ad
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24794937"
---
# <a name="ijsdebugdatatarget-interface"></a>IJsDebugDataTarget – rozhraní
Implementované ladicí program nabízí funkce pro přístup k a změní stav tento cílový proces ladicího programu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IJsDebugDataTarget : public IUnknown;  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[Ijsdebugdatatarget::allocatevirtualmemory – metoda](../../winscript/reference/ijsdebugdatatarget-allocatevirtualmemory-method.md)|Rezerv nebo potvrdí oblasti paměti ve virtuálním adresním prostoru tento cílový proces.|  
|[Ijsdebugdatatarget::createstackframeenumerator – metoda](../../winscript/reference/ijsdebugdatatarget-createstackframeenumerator-method.md)|Vytvoří enumerátor pro rámce zásobníku.|  
|[Ijsdebugdatatarget::FreeVirtualMemory – metoda](../../winscript/reference/ijsdebugdatatarget-freevirtualmemory-method.md)|Uvolní nebo decommits oblasti paměti ve virtuálním adresním prostoru tento cílový proces.|  
|[Ijsdebugdatatarget::getthreadcontext – metoda](../../winscript/reference/ijsdebugdatatarget-getthreadcontext-method.md)|Načte kontext pro danou přístup z více vláken.|  
|[Ijsdebugdatatarget::gettlsvalue – metoda](../../winscript/reference/ijsdebugdatatarget-gettlsvalue-method.md)|Pro vlákno laděné načte hodnotu ve slotu přístup z více vláken místní úložiště (TLS) pro zadaný index TLS.|  
|[Ijsdebugdatatarget::readbstr – metoda](../../winscript/reference/ijsdebugdatatarget-readbstr-method.md)|Čte BSTR z cíl ladění.|  
|[Ijsdebugdatatarget::readmemory – metoda](../../winscript/reference/ijsdebugdatatarget-readmemory-method.md)|Přečte paměť tento cílový proces.|  
|[Ijsdebugdatatarget::readnullterminatedstring – metoda](../../winscript/reference/ijsdebugdatatarget-readnullterminatedstring-method.md)|Přečte zadaný počet znaků z cíle.|  
|[Ijsdebugdatatarget::writememory – metoda](../../winscript/reference/ijsdebugdatatarget-writememory-method.md)|Přečte paměť tento cílový proces.|  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** jscript9diag.h  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace skriptovacích rozhraní systému Windows](../../winscript/reference/windows-script-interfaces-reference.md)