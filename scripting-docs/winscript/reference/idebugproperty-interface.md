---
title: Idebugproperty – rozhraní | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugProperty interface
ms.assetid: 7e8f5341-23ef-4029-814d-f5c2307b9203
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2888a6d781ecd501128545e483971a47859d9cda
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24794271"
---
# <a name="idebugproperty-interface"></a>IDebugProperty – rozhraní
Používají k popisu hierarchické vlastnost laděné entity, který má název, typ a hodnotu. Nejčastěji `IDebugProperty` se používá k popisu výsledkem vyhodnocení výrazu, vyhodnocení prohlášení nebo vyhodnocení registrace.  
  
## <a name="methods-in-vtable-order"></a>Metody v tabulce Vtable pořadí  
 Následující tabulka uvádí metody `IDebugProperty` rozhraní.  
  
|Metoda|Popis|  
|------------|-----------------|  
|[IDebugProperty::GetPropertyInfo](../../winscript/reference/idebugproperty-getpropertyinfo.md)|Získat `DebugPropertyInfo` , který to popisuje`IDebugProperty``.`|  
|[IDebugProperty::GetExtendedInfo](../../winscript/reference/idebugproperty-getextendedinfo.md)|Získá rozšířené informace o vlastnosti.|  
|[IDebugProperty::SetValueAsString](../../winscript/reference/idebugproperty-setvalueasstring.md)|Nastaví hodnotu vlastnosti z řetězce.|  
|[IDebugProperty::EnumMembers](../../winscript/reference/idebugproperty-enummembers.md)|Vytvoří výčet členů vlastnost.|  
|[IDebugProperty::GetParent](../../winscript/reference/idebugproperty-getparent.md)|Získá nadřazený vlastnosti.|  
  
## <a name="requirements"></a>Požadavky  
 Záhlaví: dbgprop.h