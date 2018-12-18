---
title: Ijsdebugframe – metoda | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 5af46b18-9d25-4a23-b8d1-fa23bea3efcf
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f09a147375661fb52b88f531aff981897138adff
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24795036"
---
# <a name="ijsdebugframe-interface"></a>IJsDebugFrame – metoda
Představuje rámec zásobníku.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IJsDebugFrame : public IUnknown;  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[Ijsdebugframe::evaluate – metoda](../../winscript/reference/ijsdebugframe-evaluate-method.md)|Vyhodnotí výraz v kontextu této rámce zásobníku.|  
|[Ijsdebugframe::getdebugproperty – metoda](../../winscript/reference/ijsdebugframe-getdebugproperty-method.md)|Vrátí prohlížeči vlastnost pro tento rámce zásobníku.|  
|[Ijsdebugframe::getdocumentpositionwithid – metoda](../../winscript/reference/ijsdebugframe-getdocumentpositionwithid-method.md)|Vrátí aktuální pozici tento rámce zásobníku v tomto dokumentu úrovni uživatele.|  
|[Ijsdebugframe::getdocumentpositionwithname – metoda](../../winscript/reference/ijsdebugframe-getdocumentpositionwithname-method.md)|Vrátí aktuální pozici tento rámce zásobníku v tomto dokumentu úrovni uživatele.|  
|[Ijsdebugframe::getName – metoda](../../winscript/reference/ijsdebugframe-getname-method.md)|Získá popisný název rámce zásobníku.|  
|[Ijsdebugframe::getreturnaddress – metoda](../../winscript/reference/ijsdebugframe-getreturnaddress-method.md)|Získá návratový adresu nabídnutých na straně 'start' (viz getstackrange –) rámečku.|  
|[Ijsdebugframe::getstackrange – metoda](../../winscript/reference/ijsdebugframe-getstackrange-method.md)|Vrátí absolutní adresu rozsahu logické rámce zásobníku JavaScript.|  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** jscript9diag.h  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace skriptovacích rozhraní systému Windows](../../winscript/reference/windows-script-interfaces-reference.md)