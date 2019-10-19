---
title: Rozhraní Iscriptentry – | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 868322358908a32c8f14b56846cf3237f8531b4c
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575397"
---
# <a name="iscriptentry-interface"></a>IScriptEntry – rozhraní
Objekt, který implementuje rozhraní `IScriptEntry`, představuje buď blok skriptu, nebo objekt funkce.  
  
 Kromě metod zděděných z `IScriptNode` rozhraní `IScriptEntry` zpřístupňuje následující metody.  
  
## <a name="methods-in-vtable-order"></a>Metody v pořadí vtable  
  
|Metoda|Popis|  
|------------|-----------------|  
|[IScriptEntry::GetBody](../../winscript/reference/iscriptentry-getbody.md)|Vrátí text, který odpovídá textu `IScriptEntry` bloku skriptu, bloku funkce nebo skriptletu.|  
|[IScriptEntry::GetItemName](../../winscript/reference/iscriptentry-getitemname.md)|Vrátí název položky, která identifikuje objekt `IScriptEntry`.|  
|[IScriptEntry::GetName](../../winscript/reference/iscriptentry-getname.md)|Pro položky, které reprezentují jeden objekt (například funkce), vrátí název objektu.|  
|[IScriptEntry::GetRange](../../winscript/reference/iscriptentry-getrange.md)|Vrátí počáteční pozici a délku položky.|  
|[IScriptEntry::GetSignature](../../winscript/reference/iscriptentry-getsignature.md)|Vrátí informace o typu objektu `IScriptEntry` funkce.|  
|[IScriptEntry::GetText](../../winscript/reference/iscriptentry-gettext.md)|Vrátí text, který odpovídá bloku skriptu `IScriptEntry`, nebo zdrojový kód, který je obsažen v obslužné rutině události `IScriptScriptlet`.|  
|[IScriptEntry::SetBody](../../winscript/reference/iscriptentry-setbody.md)|Nastaví text, který se nachází v těle `IScriptEntry` bloku skriptu nebo `IScriptScriptlet` skriptletu.|  
|[IScriptEntry::SetItemName](../../winscript/reference/iscriptentry-setitemname.md)|Nastaví název položky, která identifikuje objekt `IScriptEntry`.|  
|[IScriptEntry::SetName](../../winscript/reference/iscriptentry-setname.md)|Pro položky, které reprezentují jeden objekt (například funkce), nastaví název objektu.|  
|[IScriptEntry::SetSignature](../../winscript/reference/iscriptentry-setsignature.md)|Nastaví informace o typu `IScriptEntry` objektu funkce.|  
|[IScriptEntry::SetText](../../winscript/reference/iscriptentry-settext.md)|Nastaví text, který odpovídá bloku skriptu `IScriptEntry`, nebo zdrojový kód, který je obsažen v obslužné rutině události `IScriptScriptlet`.|  
  
## <a name="see-also"></a>Viz také:  
 [Rozhraní pro vytváření aktivních skriptů](../../winscript/reference/active-script-authoring-interfaces.md)