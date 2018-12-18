---
title: Struktura JsDebugPropertyInfo | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- JsDebugPropertyInfo
apilocation:
- jscript9diag.dll
ms.assetid: 3a5463a7-2013-4846-9ab2-8beb675a5a6a
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1e9d2ae0d93729d4c333509e0178f4c4829ebf13
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24796299"
---
# <a name="jsdebugpropertyinfo-structure"></a>Struktura JsDebugPropertyInfo
Označuje informace o vlastnosti.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef struct tagJsDebugPropertyInfo{   BSTR name;   BSTR type;   BSTR value;   BSTR fullName;   JS_PROPERTY_ATTRIBUTES attr;} JsDebugPropertyInfo;  
```  
  
## <a name="members"></a>Členové  
 `name`  
 Název vlastnosti  
  
 `type`  
 Typ vlastnosti.  
  
 `value`  
 Hodnota vlastnosti  
  
 `fullName`  
 Úplný název vlastnosti.  
  
 `attr`  
 Výčet, který představuje vlastnost atributy.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** jscript9diag.h  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace skriptovacích rozhraní systému Windows](../../winscript/reference/windows-script-interfaces-reference.md)