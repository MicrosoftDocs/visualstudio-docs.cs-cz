---
title: 'Idisperror –:: GetNext | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDispError.GetNext
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDispError::GetNext
ms.assetid: 3e5267f8-ba62-41c3-bd3e-eced2ad85e8e
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 81186e6eba7983a1210e5de5bca5d83dd77089da
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573102"
---
# <a name="idisperrorgetnext"></a>IDispError::GetNext
Načte další objekt `IDispError`.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetNext(  
   IDispError**  ppde  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppde`  
 mimo Určuje další objekt `IDispError`.  
  
## <a name="return-value"></a>Návratová hodnota  
 Metoda vrací `HRESULT`. Možné hodnoty zahrnují hodnoty v následující tabulce, ale nejsou na ně omezeny.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`S_OK`|Metoda byla úspěšná.|  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda načte další objekt `IDispError`. Pokud se jedná o poslední `IDispError` objekt, vrátí tato metoda hodnotu NULL.  
  
> [!NOTE]
> Tato metoda není implementována.  
  
## <a name="see-also"></a>Viz také:  
 [IDispError – rozhraní](../../winscript/reference/idisperror-interface.md)