---
title: Idebugapplicationnodeevents – rozhraní | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugApplicationNodeEvents interface
ms.assetid: 02e0bb17-84ce-458b-bae6-608a9899e535
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 20d0fac68bb7cdb3d7f5cb6aac6b0ab67e373c84
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24794124"
---
# <a name="idebugapplicationnodeevents-interface"></a>IDebugApplicationNodeEvents – rozhraní
Poskytuje rozhraní pro události `IDebugApplicationNode` rozhraní.  
  
 Kromě metod zděděno z `IUnknown`, `IDebugApplicationNodeEvents` rozhraní poskytuje následující metody.  
  
## <a name="methods-in-vtable-order"></a>Metody v tabulce Vtable pořadí  
  
|Metoda|Popis|  
|------------|-----------------|  
|[IDebugApplicationNodeEvents::onAddChild](../../winscript/reference/idebugapplicationnodeevents-onaddchild.md)|Zpracovává událost, když podřízený uzel je přidán do objektu ladění aplikace uzlu.|  
|[IDebugApplicationNodeEvents::onRemoveChild](../../winscript/reference/idebugapplicationnodeevents-onremovechild.md)|Zpracovává událost, pokud podřízený uzel je odebrán z objektu uzlu ladění aplikace.|  
|[IDebugApplicationNodeEvents::onDetach](../../winscript/reference/idebugapplicationnodeevents-ondetach.md)|Zpracovává událost, což svědčí o tom, že objekt ladění aplikace uzlu byla odpojena od nadřazeného uzlu.|  
|[IDebugApplicationNodeEvents::onAttach](../../winscript/reference/idebugapplicationnodeevents-onattach.md)|Zpracovává událost, což svědčí o tom, že objekt ladění aplikace uzlu se připojil k nadřazeného uzlu.|  
  
## <a name="see-also"></a>Viz také  
 [Idebugapplicationnode – rozhraní](../../winscript/reference/idebugapplicationnode-interface.md)