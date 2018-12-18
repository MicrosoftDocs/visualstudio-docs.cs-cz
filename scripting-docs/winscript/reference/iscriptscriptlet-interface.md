---
title: Iscriptscriptlet – rozhraní | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IScriptScriptlet interface
ms.assetid: b9981908-a337-4228-864c-c741f111ab2d
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f3fa3253997d3a09a7170f3795bf8a7bbf8a182c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24796296"
---
# <a name="iscriptscriptlet-interface"></a>IScriptScriptlet – rozhraní
Objekt, který implementuje `IScriptScriptlet` rozhraní představuje skriptu obslužná rutina události.  
  
 Kromě metod zděděno z `IScriptEntry`, `IScriptScriptlet` rozhraní poskytuje následující metody.  
  
## <a name="methods-in-vtable-order"></a>Metody v tabulce Vtable pořadí  
  
|Metoda|Popis|  
|------------|-----------------|  
|[IScriptScriptlet::GetEventName](../../winscript/reference/iscriptscriptlet-geteventname.md)|Vrátí název události, který je přidružen skriptletu.|  
|[Iscriptscriptlet –:: GetSimpleEventName](../../winscript/reference/iscriptscriptlet-getsimpleeventname.md)|Vrací název jednoduchá událost, která souvisí s skriptletu. Toto je název jednoslovného výrazu, který neobsahuje žádné prázdné znaky.|  
|[IScriptScriptlet::GetSubItemName](../../winscript/reference/iscriptscriptlet-getsubitemname.md)|Vrátí poslední identifikátor ve plně kvalifikovaný název hostitele skriptlet objektu.|  
|[IScriptScriptlet::SetEventName](../../winscript/reference/iscriptscriptlet-seteventname.md)|Nastaví název události, která souvisí s skriptletu.|  
|[IScriptScriptlet::SetSimpleEventName](../../winscript/reference/iscriptscriptlet-setsimpleeventname.md)|Nastaví název jednoduchá událost, která souvisí s skriptletu. Toto je název jednoslovného výrazu, který neobsahuje žádné prázdné znaky.|  
|[IScriptScriptlet::SetSubItemName](../../winscript/reference/iscriptscriptlet-setsubitemname.md)|Nastaví identifikátor poslední ve plně kvalifikovaný název hostitele skriptlet objektu.|  
  
## <a name="see-also"></a>Viz také  
 [Rozhraní pro vytváření aktivních skriptů](../../winscript/reference/active-script-authoring-interfaces.md)