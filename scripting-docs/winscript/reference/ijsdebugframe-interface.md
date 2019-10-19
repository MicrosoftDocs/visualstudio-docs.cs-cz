---
title: Rozhraní IJsDebugFrame | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 5af46b18-9d25-4a23-b8d1-fa23bea3efcf
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 91fe8cdf91b0c2121f4a1a7f111794b0fbe36669
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575108"
---
# <a name="ijsdebugframe-interface"></a>IJsDebugFrame – metoda
Představuje rámec zásobníku.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
IJsDebugFrame : public IUnknown;  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Name|Popis|  
|----------|-----------------|  
|[IJsDebugFrame::Evaluate – metoda](../../winscript/reference/ijsdebugframe-evaluate-method.md)|Vyhodnotit výraz v kontextu tohoto rámce zásobníku.|  
|[IJsDebugFrame::GetDebugProperty – metoda](../../winscript/reference/ijsdebugframe-getdebugproperty-method.md)|Vrátí prohlížeč vlastností pro tento rámec zásobníku.|  
|[IJsDebugFrame::GetDocumentPositionWithId – metoda](../../winscript/reference/ijsdebugframe-getdocumentpositionwithid-method.md)|Vrátí aktuální pozici tohoto rámce zásobníku v dokumentu na úrovni uživatele.|  
|[IJsDebugFrame::GetDocumentPositionWithName – metoda](../../winscript/reference/ijsdebugframe-getdocumentpositionwithname-method.md)|Vrátí aktuální pozici tohoto rámce zásobníku v dokumentu na úrovni uživatele.|  
|[IJsDebugFrame::GetName – metoda](../../winscript/reference/ijsdebugframe-getname-method.md)|Získá uživatelsky přívětivý název rámce zásobníku.|  
|[IJsDebugFrame::GetReturnAddress – metoda](../../winscript/reference/ijsdebugframe-getreturnaddress-method.md)|Získá návratovou adresu vloženou na ' Start ' (viz Getstackrange –) snímku.|  
|[IJsDebugFrame::GetStackRange – metoda](../../winscript/reference/ijsdebugframe-getstackrange-method.md)|Vrátí absolutní rozsah adres rámce logického zásobníku JavaScriptu.|  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** Jscript9diag. h  
  
## <a name="see-also"></a>Viz také:  
 [Referenční dokumentace skriptovacích rozhraní systému Windows](../../winscript/reference/windows-script-interfaces-reference.md)