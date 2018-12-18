---
title: Iperpropertybrowsing2 – rozhraní 1 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IPerPropertyBrowsing2
apilocation:
- scrobj.dll
helpviewer_keywords:
- IPerPropertyBrowsing2 interface
ms.assetid: 1e50b3f7-cc1c-495a-93c7-3ee03aea0b8a
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 75a0a7ef30bca2205789a63ea577808c11582791
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24794670"
---
# <a name="iperpropertybrowsing2-interface-1"></a>Iperpropertybrowsing2 – rozhraní 1
Přístupy nabízí informace na stránkách vlastností objektu.  
  
## <a name="methods-in-vtable-order"></a>Metody v tabulce Vtable pořadí  
  
|Metoda|Popis|  
|------------|-----------------|  
|`GetDisplayString`|Vrátí textový řetězec popisující zadanou vlastnost.|  
|`MapPropertyToPage`|Vrátí CLSID vlastností stránky, která umožňuje zpracování zadanou vlastnost.|  
|`GetPredefinedStrings`|Vrátí spočítané pole řetězců (`LPOLESTR` ukazatele) výpis popisy povolených hodnot, které může přijmout zadanou vlastnost.|  
|`SetPredefinedValue`|Nastaví hodnotu vlastnosti na hodnotu předdefinované identifikovaný tokenu`dwCookie.`|  
  
## <a name="requirements"></a>Požadavky  
 Záhlaví: dbgprop.h