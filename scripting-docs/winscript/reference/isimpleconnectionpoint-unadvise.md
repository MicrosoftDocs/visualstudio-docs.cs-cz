---
title: 'Isimpleconnectionpoint –:: Unadvise | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- ISimpleConnectionPoint.Unadvise
apilocation:
- pdm.dll
helpviewer_keywords:
- ISimpleConnectionPoint::Unadvise
ms.assetid: eae06a58-ed42-4839-aad4-14420b15343f
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e00c172fd33eb0ccf27aaf28e0e2f692c1a353ab
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571759"
---
# <a name="isimpleconnectionpointunadvise"></a>ISimpleConnectionPoint::Unadvise
Ukončí poradenské připojení, které bylo dříve vytvořeno prostřednictvím `ISimpleConnectionPoint::Advise`.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT Unadvise(  
   DWORD  dwCookie  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `dwCookie`  
 pro Token připojení, které se má ukončit, jak bylo vráceno z `ISimpleConnectionPoint::Advise`.  
  
## <a name="return-value"></a>Návratová hodnota  
 Metoda vrací `HRESULT`. Možné hodnoty zahrnují hodnoty v následující tabulce, ale nejsou na ně omezeny.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`S_OK`|Metoda byla úspěšná.|  
  
## <a name="remarks"></a>Poznámky  
 Při ukončení poradenského připojení volá spojovací bod metodu `Release` na ukazatel, který byl uložen pro připojení během metody `ISimpleConnectionPoint::Advise`. Toto volání obrátí `AddRef`, který byl proveden během `ISimpleConnectionPoint::Advise`, pokud spojovací bod volá `QueryInterface` informační jímky.  
  
## <a name="see-also"></a>Viz také:  
 [ISimpleConnectionPoint – rozhraní](../../winscript/reference/isimpleconnectionpoint-interface.md)