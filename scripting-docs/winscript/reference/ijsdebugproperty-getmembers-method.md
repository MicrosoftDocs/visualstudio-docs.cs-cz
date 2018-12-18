---
title: Ijsdebugproperty::GetMembers – metoda | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugProperty.GetMembers
apilocation:
- jscript9diag.dll
ms.assetid: a32b5372-d9cb-4b9a-9bc2-81b5e1df365c
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 066db431f27eca01fab63d10d0396575b3895527
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24794682"
---
# <a name="ijsdebugpropertygetmembers-method"></a>IJsDebugProperty::GetMembers – metoda
Získá členy tohoto objektu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetMembers(  
   JS_PROPERTY_MEMBERS members,  
   IJsEnumDebugProperty **ppEnum  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `members`  
 [v] Příznaky k určení, co je součástí informace o členech.  
  
 `ppEnum`  
 [out] Členové objektu.  
  
## <a name="return-value"></a>Návratová hodnota  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** jscript9diag.h  
  
## <a name="see-also"></a>Viz také  
 [Ijsdebugproperty – rozhraní](../../winscript/reference/ijsdebugproperty-interface.md)