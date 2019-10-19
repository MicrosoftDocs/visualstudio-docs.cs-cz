---
title: Rozhraní IJsDebugDataTarget | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: a9b784d6-958f-4d55-b3f6-c2d6b260a16b
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 85c77209230abfe261c9ec0b884ad0a677cfbf07
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572461"
---
# <a name="ijsdebugdatatarget-interface"></a>IJsDebugDataTarget – rozhraní
Implementováno ladicím programem pro poskytování funkcí pro přístup a změnu stavu cílového procesu ladicího programu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
IJsDebugDataTarget : public IUnknown;  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Name|Popis|  
|----------|-----------------|  
|[IJsDebugDataTarget::AllocateVirtualMemory – metoda](../../winscript/reference/ijsdebugdatatarget-allocatevirtualmemory-method.md)|Rezervuje nebo potvrdí oblast paměti v rámci virtuálního adresového prostoru cílového procesu.|  
|[IJsDebugDataTarget::CreateStackFrameEnumerator – metoda](../../winscript/reference/ijsdebugdatatarget-createstackframeenumerator-method.md)|Vytvoří enumerátor pro rámce zásobníku.|  
|[IJsDebugDataTarget::FreeVirtualMemory – metoda](../../winscript/reference/ijsdebugdatatarget-freevirtualmemory-method.md)|Vydává nebo odváže oblast paměti v rámci virtuálního adresového prostoru cílového procesu.|  
|[IJsDebugDataTarget::GetThreadContext – metoda](../../winscript/reference/ijsdebugdatatarget-getthreadcontext-method.md)|Načte kontext pro dané vlákno.|  
|[IJsDebugDataTarget::GetTlsValue – metoda](../../winscript/reference/ijsdebugdatatarget-gettlsvalue-method.md)|Pro vlákno, které je laděno, načte hodnotu z slotu thread local Storage (TLS) pro zadaný index TLS.|  
|[IJsDebugDataTarget::ReadBSTR – metoda](../../winscript/reference/ijsdebugdatatarget-readbstr-method.md)|Přečte BSTR z cíle ladění.|  
|[IJsDebugDataTarget::ReadMemory – metoda](../../winscript/reference/ijsdebugdatatarget-readmemory-method.md)|Přečte paměť cílového procesu.|  
|[IJsDebugDataTarget::ReadNullTerminatedString – metoda](../../winscript/reference/ijsdebugdatatarget-readnullterminatedstring-method.md)|Přečte zadaný počet znaků z cíle.|  
|[IJsDebugDataTarget::WriteMemory – metoda](../../winscript/reference/ijsdebugdatatarget-writememory-method.md)|Přečte paměť cílového procesu.|  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** Jscript9diag. h  
  
## <a name="see-also"></a>Viz také:  
 [Referenční dokumentace skriptovacích rozhraní systému Windows](../../winscript/reference/windows-script-interfaces-reference.md)