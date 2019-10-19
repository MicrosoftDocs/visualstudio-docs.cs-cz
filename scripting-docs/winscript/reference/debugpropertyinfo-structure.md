---
title: Struktura Debugpropertyinfo – | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- DebugPropertyInfo
apilocation:
- scrobj.dll
helpviewer_keywords:
- DebugPropertyInfo structure
ms.assetid: 3246efbc-c212-4024-8f07-6414c2f85e75
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 793c83b467460f0744abffe3f161f7510f56257a
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575072"
---
# <a name="debugpropertyinfo-structure"></a>DebugPropertyInfo – struktura
Popisuje objekt hierarchického charakteru, který má název, typ a hodnotu. Slouží k popisu ladicích vlastností místních proměnných, parametrů, sledovacích proměnných a výrazů a registrů.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
typedef struct DebugPropertyInfo{  
   DBGPROP_INFO_FLAGS  dwValidFields;  
   BSTR  bstrName;  
   BSTR  bstrType;  
   BSTR  bstrValue;  
   BSTR  bstrFullName;  
   DBGPROP_ATTRIB_FLAGS  dwAttrib;  
   IDebugProperty*  pDebugProp;  
};  
```  
  
## <a name="members"></a>Členové  
 dwValidFields  
 Výčtový datový typ použitý k určení, která pole jsou inicializována.  
  
 BSTR  
 Název vlastnosti v rámci kontextu.  
  
 bstrType  
 Typ vlastnosti, jako formátovaný řetězec.  
  
 bstrValue  
 Hodnota vlastnosti jako formátovaný řetězec.  
  
 bstrFullName  
 Úplný název vlastnosti.  
  
 dwAttrib  
 Výčet, který určuje příznaky pro atributy vlastností ladění.  
  
 pDebugProp  
 @No__t_0 popisují informace v této `DebugPropertyInfo` struktuře.  
  
## <a name="see-also"></a>Viz také:  
 @No__t_1 [rozhraní idebugproperty –](../../winscript/reference/idebugproperty-interface.md)  
 [DBGPROP_ATTRIB_FLAGS](../../winscript/reference/dbgprop-attrib-flags.md)    
 [DBGPROP_INFO_FLAGS](../../winscript/reference/dbgprop-info-flags.md)