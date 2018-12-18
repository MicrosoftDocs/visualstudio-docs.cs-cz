---
title: Isimpleconnectionpoint – rozhraní | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: de40f66a9e5721b8dacac634c6fb77982017c155
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24796326"
---
# <a name="isimpleconnectionpoint-interface"></a>ISimpleConnectionPoint – rozhraní
Poskytuje jednoduchý způsob pro popisující a výčet události aktivováno u konkrétní spojovacího bodu. Toto rozhraní také umožňuje snadno spojit `IDispatch` objekt, který chcete tyto události. Toto rozhraní je implementováno ve v procesu ladění Manager (PDM) a spotřebovávají skriptovacích strojů ukládaných.  
  
 Toto rozhraní je k dispozici z `IDebugHelper::CreateSimpleConnectionPoint`.  
  
 Kromě metod zděděno z `IUnknown`, `ISimpleConnectionPoint` rozhraní poskytuje následující metody.  
  
## <a name="methods-in-vtable-order"></a>Metody v tabulce Vtable pořadí  
  
|Metoda|Popis|  
|------------|-----------------|  
|[ISimpleConnectionPoint::Advise](../../winscript/reference/isimpleconnectionpoint-advise.md)|Naváže připojení mezi objektu bodu jednoduché připojení a jímka klienta.|  
|[ISimpleConnectionPoint::DescribeEvents](../../winscript/reference/isimpleconnectionpoint-describeevents.md)|Vrátí DISPID a název pro všechny události v zadaném rozsahu událostí.|  
|[ISimpleConnectionPoint::GetEventCount](../../winscript/reference/isimpleconnectionpoint-geteventcount.md)|Vrátí počet událostí, které jsou zveřejněné na tomto rozhraní.|  
|[ISimpleConnectionPoint::Unadvise](../../winscript/reference/isimpleconnectionpoint-unadvise.md)|Ukončí připojení k poradní dříve vytvořeno prostřednictvím `ISimpleConnectionPoint::Advise`.|  
  
## <a name="see-also"></a>Viz také  
 [Idebugproperty – rozhraní](../../winscript/reference/idebugproperty-interface.md)