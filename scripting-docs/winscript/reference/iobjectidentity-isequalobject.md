---
title: 'Iobjectidentity –:: IsEqualObject | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IObjectIdentity.IsEqualObject
apilocation:
- scrobj.dll
helpviewer_keywords:
- IsEqualObject method
ms.assetid: 78c5c5c2-d299-4036-986c-7c1d87cbe7cd
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 636dfa07b1fc94dfec2273220aa4101f5cd085b1
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571473"
---
# <a name="iobjectidentityisequalobject"></a>IObjectIdentity::IsEqualObject
Určuje, zda je objekt roven aktuálnímu objektu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT IsEqualObject(  
  IUnknown*punk  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `punk`  
 pro Adresa objektu, který se má porovnat s aktuálním objektem.  
  
## <a name="return-value"></a>Návratová hodnota  
 Metoda vrací `HRESULT`. Možné hodnoty zahrnují hodnoty v následující tabulce, ale nejsou na ně omezeny.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`S_OK`|Objekty jsou stejné.|  
|`S_FALSE`|Objekty nejsou stejné.|  
  
## <a name="remarks"></a>Poznámky  
 Implementace metody `IsEqualObject` by měla vracet `S_OK` pouze v případě, že objekty jsou identické.  
  
## <a name="see-also"></a>Viz také:  
 [IObjectIdentity – rozhraní](../../winscript/reference/iobjectidentity-interface.md)