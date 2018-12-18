---
title: IObjectIdentity::IsEqualObject | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 52e386055e458568f8d4076a37489b7b2397f399
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24794733"
---
# <a name="iobjectidentityisequalobject"></a>IObjectIdentity::IsEqualObject
Určuje, zda objekt rovná aktuálnímu objektu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT IsEqualObject(  
  IUnknown*punk  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `punk`  
 [v] Adresa objekt k porovnání s aktuálním objektem.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí metodu `HRESULT`. Možné hodnoty zahrnují hodnoty v následující tabulce, ale nejsou na ně omezeny.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`S_OK`|Objekty jsou stejné.|  
|`S_FALSE`|Objekty nejsou stejné.|  
  
## <a name="remarks"></a>Poznámky  
 Implementace `IsEqualObject` metoda by měla vrátit `S_OK` pouze v případě, že objekty jsou identické.  
  
## <a name="see-also"></a>Viz také  
 [Iobjectidentity – rozhraní](../../winscript/reference/iobjectidentity-interface.md)