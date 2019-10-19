---
title: 'Iperpropertybrowsing2 –:: SetPredefinedValue | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IPerPropertyBrowsing2.SetPredefinedValue
apilocation:
- scrobj.dll
helpviewer_keywords:
- IPerPropertyBrowsing2::SetPredefinedValue
ms.assetid: 3aff5300-c5a4-4d9b-9d47-a75b64014ac4
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1a823a04082b7e19b2c1bc475c1070cc501789e8
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576237"
---
# <a name="iperpropertybrowsing2setpredefinedvalue"></a>IPerPropertyBrowsing2::SetPredefinedValue
Nastaví hodnotu vlastnosti určenou parametrem `dispID`. Předdefinovaná hodnota je identifikována tokenem `dwCookie.`  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT SetPredefinedValue(  
   DISPID  dispid,  
   DWORD  dwCookie  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `dispid`  
 pro Identifikátor odeslání vlastnosti, pro kterou je nastavena předdefinovaná hodnota  
  
 `dwCookie`  
 pro Token identifikující hodnotu, která se má nastavit  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrací platný `HRESULT`, obvykle `S_OK`.  
  
## <a name="see-also"></a>Viz také:  
 [IPerPropertyBrowsing2 – rozhraní 1](../../winscript/reference/iperpropertybrowsing2-interface-1.md)