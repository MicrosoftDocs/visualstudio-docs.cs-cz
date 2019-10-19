---
title: Rozhraní Ienumdebugextendedpropertyinfo – | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IEnumDebugExtendedPropertyInfo
apilocation:
- scrobj.dll
helpviewer_keywords:
- IEnumDebugExtendedPropertyInfo interface
ms.assetid: 316d5aa7-c949-48fc-89c1-239f00566cae
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8ceae13f2a785a0920598fa79b237a9c8ae1da1c
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72568938"
---
# <a name="ienumdebugextendedpropertyinfo-interface"></a>IEnumDebugExtendedPropertyInfo – rozhraní
Vytvoří výčet `ExtendedDebugPropertyInfo` struktur.  
  
## <a name="methods-in-vtable-order"></a>Metody v pořadí vtable  
 Následující tabulka ukazuje metody `IEnumDebugExtendedPropertyInfo`.  
  
|Metoda|Popis|  
|------------|-----------------|  
|[IEnumDebugExtendedPropertyInfo::Clone](../../winscript/reference/ienumdebugextendedpropertyinfo-clone.md)|Vytvoří enumerátor, který obsahuje stejný stav výčtu jako aktuální enumerátor.|  
|[IEnumDebugExtendedPropertyInfo::GetCount](../../winscript/reference/ienumdebugextendedpropertyinfo-getcount.md)|Získá počet `ExtendedDebugPropertyInfo` struktur v enumerátoru.|  
|[IEnumDebugExtendedPropertyInfo::Next](../../winscript/reference/ienumdebugextendedpropertyinfo-next.md)|Načte zadaný počet `ExtendedDebugPropertyInfo` struktur v sekvenci výčtu.|  
|[IEnumDebugExtendedPropertyInfo::Skip](../../winscript/reference/ienumdebugextendedpropertyinfo-skip.md)|Přeskočí zadaný počet `ExtendedDebugPropertyInfo` struktur v sekvenci výčtu.|  
|[IEnumDebugExtendedPropertyInfo::Reset](../../winscript/reference/ienumdebugextendedpropertyinfo-reset.md)|Obnoví posloupnost výčtu na začátek.|  
  
## <a name="requirements"></a>Požadavky  
 Záhlaví: dbgprop. h  
  
## <a name="see-also"></a>Viz také:  
 [ExtendedDebugPropertyInfo – struktura](../../winscript/reference/extendeddebugpropertyinfo-structure.md)