---
title: Struktura Extendeddebugpropertyinfo – | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- ExtendedDebugPropertyInfo
apilocation:
- scrobj.dll
helpviewer_keywords:
- ExtendedDebugPropertyInfo structure
ms.assetid: f2cf6477-454b-4d13-95da-ae4c90daa175
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 09f3c5a219fca9ec9b881e2ae8363aae4d48e03f
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575839"
---
# <a name="extendeddebugpropertyinfo-structure"></a>ExtendedDebugPropertyInfo – struktura
Rozšiřuje strukturu `DebugPropertyInfo` o další členy pro charakterizaci rozšířené vlastnosti.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
typedef struct ExtendedDebugPropertyInfo{  
   DBGPROP_INFO_FLAGS  dwValidFields;  
   LPOLESTR  bstrName;  
   LPOLESTR  bstrType;  
   LPOLESTR  bstrValue;  
   LPOLESTR  bstrFullName;  
   DBGPROP_ATTRIB_FLAGS  dwAttrib;  
   IDebugProperty*  pDebugProp;  
   DWORD  nDISPID;  
   DWORD  nType;  
   VARIANT  varValue;  
   ILockBytes*  plbValue;  
   IDebugExtendedProperty*  pDebugExtProp;  
};  
```  
  
## <a name="members"></a>Členové  
 `dwValidFields`  
 Výčtový datový typ použitý k určení, která pole jsou inicializována.  
  
 `bstrName`  
 Název vlastnosti v rámci kontextu.  
  
 `bstrType`  
 Typ vlastnosti jako formátovaný řetězec.  
  
 `bstrValue`  
 Hodnota vlastnosti jako formátovaný řetězec.  
  
 `bstrFullName`  
 Úplný název vlastnosti.  
  
 `dwAttrib`  
 Výčet, který určuje příznaky pro atributy vlastností ladění.  
  
 `pDebugProp`  
 `IDebugProperty` objekt odpovídající tomuto `ExtendedDebugPropertyInfo`.  
  
 `nDISPID`  
 ID odeslání.  
  
 `nType`  
 Rozšířený typ vlastnosti.  
  
 `varValue`  
 Hodnota rozšířené vlastnosti, pokud se může vejít do varianty.  
  
 `plbValue`  
 Skutečné datové bajty hodnoty vlastnosti.  
  
 `pDebugExtProp`  
 `IDebugExtendedProperty` objekt odpovídající tomuto `ExtendedDebugPropertyInfo`.  
  
## <a name="see-also"></a>Viz také:  
   [struktury debugpropertyinfo –](../../winscript/reference/debugpropertyinfo-structure.md)  
   [rozhraní idebugproperty –](../../winscript/reference/idebugproperty-interface.md)  
   [rozhraní idebugextendedproperty –](../../winscript/reference/idebugextendedproperty-interface.md)  
 [DBGPROP_ATTRIB_FLAGS](../../winscript/reference/dbgprop-attrib-flags.md)   
 [DBGPROP_INFO_FLAGS](../../winscript/reference/dbgprop-info-flags.md)