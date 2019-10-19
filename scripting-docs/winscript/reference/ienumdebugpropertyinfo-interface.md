---
title: Rozhraní Ienumdebugpropertyinfo – | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IEnumDebugPropertyInfo interface
ms.assetid: c5eea4da-8414-408a-a8f6-6a9ca8745868
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0ce4f5a114629a473df99b583c77ae7747bcd339
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574185"
---
# <a name="ienumdebugpropertyinfo-interface"></a>IEnumDebugPropertyInfo – rozhraní
Vytvoří výčet `DebugPropertyInfo` struktur.  
  
## <a name="methods-in-vtable-order"></a>Metody v pořadí vtable  
 Následující tabulka ukazuje metody `IEnumDebugPropertyInfo`.  
  
|Metoda|Popis|  
|------------|-----------------|  
|[IEnumDebugPropertyInfo::Next](../../winscript/reference/ienumdebugpropertyinfo-next.md)|Načte zadaný počet `DebugPropertyInfo` struktur v sekvenci výčtu.|  
|[IEnumDebugPropertyInfo::Skip](../../winscript/reference/ienumdebugpropertyinfo-skip.md)|Přeskočí zadaný počet `DebugPropertyInfo` struktur v sekvenci výčtu.|  
|[IEnumDebugPropertyInfo::Reset](../../winscript/reference/ienumdebugpropertyinfo-reset.md)|Obnoví posloupnost výčtu na začátek.|  
|[IEnumDebugPropertyInfo::Clone](../../winscript/reference/ienumdebugpropertyinfo-clone.md)|Vytvoří enumerátor, který obsahuje stejný stav výčtu jako aktuální enumerátor.|  
|[IEnumDebugPropertyInfo::GetCount](../../winscript/reference/ienumdebugpropertyinfo-getcount.md)|Získá počet `DebugPropertyInfo` struktur v enumerátoru.|  
  
## <a name="requirements"></a>Požadavky  
 Záhlaví: dbgprop. h  
  
## <a name="see-also"></a>Viz také:  
 [DebugPropertyInfo – struktura](../../winscript/reference/debugpropertyinfo-structure.md)