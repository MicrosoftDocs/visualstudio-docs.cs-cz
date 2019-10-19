---
title: Rozhraní Idebugapplicationnodeevents – | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: a2f72290e331a51f1b33746b22a6526c9bfbac7b
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574721"
---
# <a name="idebugapplicationnodeevents-interface"></a>IDebugApplicationNodeEvents – rozhraní
Poskytuje rozhraní události pro rozhraní `IDebugApplicationNode`.  
  
 Kromě metod zděděných z `IUnknown` rozhraní `IDebugApplicationNodeEvents` zpřístupňuje následující metody.  
  
## <a name="methods-in-vtable-order"></a>Metody v pořadí vtable  
  
|Metoda|Popis|  
|------------|-----------------|  
|[IDebugApplicationNodeEvents::onAddChild](../../winscript/reference/idebugapplicationnodeevents-onaddchild.md)|Zpracovává událost při přidání podřízeného uzlu do objektu uzlu ladění aplikace.|  
|[IDebugApplicationNodeEvents::onRemoveChild](../../winscript/reference/idebugapplicationnodeevents-onremovechild.md)|Zpracovává událost při odebrání podřízeného uzlu z objektu uzlu ladění aplikace.|  
|[IDebugApplicationNodeEvents::onDetach](../../winscript/reference/idebugapplicationnodeevents-ondetach.md)|Zpracovává událost, která signalizuje, že objekt uzlu ladění aplikace byl odpojen od nadřazeného uzlu.|  
|[IDebugApplicationNodeEvents::onAttach](../../winscript/reference/idebugapplicationnodeevents-onattach.md)|Zpracovává událost, která označuje, že objekt uzlu ladění aplikace byl připojen k nadřazenému uzlu.|  
  
## <a name="see-also"></a>Viz také:  
 [IDebugApplicationNode – rozhraní](../../winscript/reference/idebugapplicationnode-interface.md)