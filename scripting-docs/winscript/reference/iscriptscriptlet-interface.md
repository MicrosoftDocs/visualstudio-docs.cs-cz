---
title: Rozhraní Iscriptscriptlet – | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 7b7973aee209695592f022d0e05a770caa1e694c
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571882"
---
# <a name="iscriptscriptlet-interface"></a>IScriptScriptlet – rozhraní
Objekt, který implementuje rozhraní `IScriptScriptlet`, představuje skript obslužné rutiny události.  
  
 Kromě metod zděděných z `IScriptEntry` rozhraní `IScriptScriptlet` zpřístupňuje následující metody.  
  
## <a name="methods-in-vtable-order"></a>Metody v pořadí vtable  
  
|Metoda|Popis|  
|------------|-----------------|  
|[IScriptScriptlet::GetEventName](../../winscript/reference/iscriptscriptlet-geteventname.md)|Vrátí název události, která je přidružena k skriptletu.|  
|[IScriptScriptlet:: GetSimpleEventName](../../winscript/reference/iscriptscriptlet-getsimpleeventname.md)|Vrátí jednoduchý název události, který je přidružen k skriptletu. Jedná se o název jednoho slova, který neobsahuje žádné prázdné znaky.|  
|[IScriptScriptlet::GetSubItemName](../../winscript/reference/iscriptscriptlet-getsubitemname.md)|Vrátí poslední identifikátor v plně kvalifikovaném názvu skriptletu hostitele objektu.|  
|[IScriptScriptlet::SetEventName](../../winscript/reference/iscriptscriptlet-seteventname.md)|Nastaví název události, která je přidružená k skriptletu.|  
|[IScriptScriptlet::SetSimpleEventName](../../winscript/reference/iscriptscriptlet-setsimpleeventname.md)|Nastaví jednoduchý název události, který je přidružen k skriptletu. Jedná se o název jednoho slova, který neobsahuje žádné prázdné znaky.|  
|[IScriptScriptlet::SetSubItemName](../../winscript/reference/iscriptscriptlet-setsubitemname.md)|Nastaví poslední identifikátor v plně kvalifikovaném názvu skriptletu hostitele objektu.|  
  
## <a name="see-also"></a>Viz také:  
 [Rozhraní pro vytváření aktivních skriptů](../../winscript/reference/active-script-authoring-interfaces.md)