---
title: 'Idebugproperty –:: SetValueAsString | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugProperty.SetValueAsString
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugProperty::SetValueAsString
ms.assetid: cad8d7b2-19a5-4a29-9000-cafdecdc238b
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 67e12652056442d9ac162be7af3a0d9e2b61b82c
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574939"
---
# <a name="idebugpropertysetvalueasstring"></a>IDebugProperty::SetValueAsString
Nastaví hodnotu vlastnosti z daného řetězce.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT SetValueAsString (  
   LPCOLESTR pszValue,  
   UINTnRadix,  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pszValue`  
 pro Hodnota, která má být nastavena.  
  
 `nRadix`  
 pro Číselná soustava, která se má použít při interpretaci libovolných číselných informací.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrací platný `HRESULT`, obvykle `S_OK`.  
  
## <a name="see-also"></a>Viz také:  
 [IDebugProperty – rozhraní](../../winscript/reference/idebugproperty-interface.md)