---
title: Rozhraní Idebugextendedproperty – | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugExtendedProperty interface
ms.assetid: e92ea064-0d92-44cf-bb9f-abda783d84be
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 24a93cb3bd230e2489b58d78f6d414ba1df006ed
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572490"
---
# <a name="idebugextendedproperty-interface"></a>IDebugExtendedProperty – rozhraní
Rozšiřuje `IDebugProperty` rozhraní.  
  
## <a name="methods-in-vtable-order"></a>Metody v pořadí vtable  
 Kromě metod zděděných z `IDebugProperty` toto rozhraní zpřístupňuje následující metody.  
  
|Metoda|Popis|  
|------------|-----------------|  
|[IDebugExtendedProperty::GetExtendedPropertyInfo](../../winscript/reference/idebugextendedproperty-getextendedpropertyinfo.md)|Získá `ExtendedDebugPropertyInfo`, který popisuje tento `IDebugExtendedProperty``.`|  
|[IDebugExtendedProperty::EnumExtendedMembers](../../winscript/reference/idebugextendedproperty-enumextendedmembers.md)|Vytvoří výčet členů rozšířené vlastnosti.|  
  
## <a name="requirements"></a>Požadavky  
 Záhlaví: dbgprop. h  
  
## <a name="see-also"></a>Viz také:  
 [IDebugProperty – rozhraní](../../winscript/reference/idebugproperty-interface.md)