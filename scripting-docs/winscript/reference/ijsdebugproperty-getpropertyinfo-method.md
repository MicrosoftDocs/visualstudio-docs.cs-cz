---
title: Ijsdebugproperty::GetPropertyInfo – metoda | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugProperty.GetPropertyInfo
apilocation:
- jscript9diag.dll
ms.assetid: ab9d6e0b-0448-4f21-b0b0-1738867587d2
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a98f0ec3c4b0cdde1432402fce16c7383947e309
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24794721"
---
# <a name="ijsdebugpropertygetpropertyinfo-method"></a>IJsDebugProperty::GetPropertyInfo – metoda
Získá informace pro tento objekt.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetPropertyInfo(  
   UINT nRadix,  
   JsDebugPropertyInfo *pPropertyInfo  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `nRadix`  
 [v] Základ – používat.  
  
 `pPropertyInfo`  
 [out] Informace o objektu.  
  
## <a name="return-value"></a>Návratová hodnota  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** jscript9diag.h  
  
## <a name="see-also"></a>Viz také  
 [Ijsdebugproperty – rozhraní](../../winscript/reference/ijsdebugproperty-interface.md)