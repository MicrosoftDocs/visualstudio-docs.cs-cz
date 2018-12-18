---
title: Iscriptentry – rozhraní | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IScriptEntry interface
ms.assetid: 86da3bc1-58b7-4d73-87ab-bc3ce34e3f41
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a785be8777cf3400f7723c24f1022bad6e22e330
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24795096"
---
# <a name="iscriptentry-interface"></a>IScriptEntry – rozhraní
Objekt, který implementuje `IScriptEntry` rozhraní představuje blok skriptu nebo objekt funkce.  
  
 Kromě metod zděděno z `IScriptNode`, `IScriptEntry` rozhraní poskytuje následující metody.  
  
## <a name="methods-in-vtable-order"></a>Metody v tabulce Vtable pořadí  
  
|Metoda|Popis|  
|------------|-----------------|  
|[IScriptEntry::GetBody](../../winscript/reference/iscriptentry-getbody.md)|Vrátí text, který odpovídá k tělu `IScriptEntry` blok skriptu, funkce bloku nebo skriptlet.|  
|[IScriptEntry::GetItemName](../../winscript/reference/iscriptentry-getitemname.md)|Vrátí název položky, které identifikují `IScriptEntry` objektu.|  
|[IScriptEntry::GetName](../../winscript/reference/iscriptentry-getname.md)|Pro položky, které představují jeden objekt (například funkce) vrátí název objektu.|  
|[IScriptEntry::GetRange](../../winscript/reference/iscriptentry-getrange.md)|Vrátí počáteční pozice a délka záznamu.|  
|[IScriptEntry::GetSignature](../../winscript/reference/iscriptentry-getsignature.md)|Vrací typ informace pro `IScriptEntry` objekt funkce.|  
|[IScriptEntry::GetText](../../winscript/reference/iscriptentry-gettext.md)|Vrátí text, který odpovídá `IScriptEntry` bloku skriptu nebo zdrojový kód, který je součástí `IScriptScriptlet` obslužné rutiny události.|  
|[IScriptEntry::SetBody](../../winscript/reference/iscriptentry-setbody.md)|Nastaví text, který je v textu `IScriptEntry` bloku skriptu nebo `IScriptScriptlet` skriptlet.|  
|[IScriptEntry::SetItemName](../../winscript/reference/iscriptentry-setitemname.md)|Nastaví název položky, které identifikují `IScriptEntry` objektu.|  
|[IScriptEntry::SetName](../../winscript/reference/iscriptentry-setname.md)|Pro položky, které představují jeden objekt (například funkce) nastaví název objektu.|  
|[IScriptEntry::SetSignature](../../winscript/reference/iscriptentry-setsignature.md)|Nastaví typ informace pro `IScriptEntry` objekt funkce.|  
|[IScriptEntry::SetText](../../winscript/reference/iscriptentry-settext.md)|Nastaví text, který odpovídá `IScriptEntry` bloku skriptu nebo zdrojový kód, který je součástí `IScriptScriptlet` obslužné rutiny události.|  
  
## <a name="see-also"></a>Viz také  
 [Rozhraní pro vytváření aktivních skriptů](../../winscript/reference/active-script-authoring-interfaces.md)