---
title: Idebugstackframe – rozhraní | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugStackFrame interface
ms.assetid: e95c1b4f-17c1-490c-a56b-c25fa45d4822
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 36fa0ba2d1b4049ad41ff0502ed33be0a706d9f6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24794412"
---
# <a name="idebugstackframe-interface"></a>IDebugStackFrame – rozhraní
Představuje logické zásobníku v zásobníku přístup z více vláken. Volání `IDebugStackFrame::QueryInterface` metoda získat `IDebugExpressionContext` rozhraní, což umožňuje výraz vyhodnocování a sledování systému windows.  
  
 Kromě metod zděděno z `IUnknown`, `IDebugStackFrame` rozhraní poskytuje následující metody.  
  
## <a name="methods-in-vtable-order"></a>Metody v tabulce Vtable pořadí  
  
|Metoda|Popis|  
|------------|-----------------|  
|[IDebugStackFrame::GetCodeContext](../../winscript/reference/idebugstackframe-getcodecontext.md)|Vrátí aktuální kontext kód přidružený rámce zásobníku.|  
|[IDebugStackFrame::GetDescriptionString](../../winscript/reference/idebugstackframe-getdescriptionstring.md)|Vrátí kratší nebo dlouho textový popis rámce zásobníku.|  
|[IDebugStackFrame::GetLanguageString](../../winscript/reference/idebugstackframe-getlanguagestring.md)|Vrátí kratší nebo dlouho textový popis jazyka.|  
|[IDebugStackFrame::GetThread](../../winscript/reference/idebugstackframe-getthread.md)|Vrátí vlákno přidružené k této rámce zásobníku.|  
|[IDebugStackFrame::GetDebugProperty](../../winscript/reference/idebugstackframe-getdebugproperty.md)|Vrátí prohlížeči vlastností pro aktuální rámec.|