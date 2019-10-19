---
title: Rozhraní Isimpleconnectionpoint – | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- ISimpleConnectionPoint interface
ms.assetid: f632a82f-942d-4291-963e-e9fa2b162493
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 549d7f38b01937f992b240cb6f1d651bc848236c
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571786"
---
# <a name="isimpleconnectionpoint-interface"></a>ISimpleConnectionPoint – rozhraní
Poskytuje jednoduchý způsob, jak popsat a vytvořit výčet událostí vyvolaných v určitém bodu připojení. Toto rozhraní také usnadňuje zapojování objektů `IDispatch` k těmto událostem. Toto rozhraní je implementováno pomocí Správce ladění procesu (PDM) a využívané skriptovacími moduly.  
  
 Toto rozhraní je dostupné z `IDebugHelper::CreateSimpleConnectionPoint`.  
  
 Kromě metod zděděných z `IUnknown` rozhraní `ISimpleConnectionPoint` zpřístupňuje následující metody.  
  
## <a name="methods-in-vtable-order"></a>Metody v pořadí vtable  
  
|Metoda|Popis|  
|------------|-----------------|  
|[ISimpleConnectionPoint::Advise](../../winscript/reference/isimpleconnectionpoint-advise.md)|Naváže spojení mezi jednoduchým objektem spojovacího bodu a jímkou klienta.|  
|[ISimpleConnectionPoint::DescribeEvents](../../winscript/reference/isimpleconnectionpoint-describeevents.md)|Vrátí DISPID a název každé události v zadaném rozsahu událostí.|  
|[ISimpleConnectionPoint::GetEventCount](../../winscript/reference/isimpleconnectionpoint-geteventcount.md)|Vrátí počet událostí vystavených v tomto rozhraní.|  
|[ISimpleConnectionPoint::Unadvise](../../winscript/reference/isimpleconnectionpoint-unadvise.md)|Ukončí poradenské připojení, které bylo dříve vytvořeno prostřednictvím `ISimpleConnectionPoint::Advise`.|  
  
## <a name="see-also"></a>Viz také:  
 [IDebugProperty – rozhraní](../../winscript/reference/idebugproperty-interface.md)