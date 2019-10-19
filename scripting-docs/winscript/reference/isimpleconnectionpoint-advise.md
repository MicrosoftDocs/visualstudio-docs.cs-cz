---
title: 'Isimpleconnectionpoint –:: Advise | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- ISimpleConnectionPoint.Advise
apilocation:
- pdm.dll
helpviewer_keywords:
- ISimpleConnectionPoint::Advise
ms.assetid: 59ded60d-b938-4110-aca3-e69ba234ca9a
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d7d08d4774dffbfd840c674b15abe82bedb37e5f
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571837"
---
# <a name="isimpleconnectionpointadvise"></a>ISimpleConnectionPoint::Advise
Naváže spojení mezi jednoduchým objektem spojovacího bodu a jímkou klienta.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT Advise(  
   IDispatch*  pdisp,  
   DWORD*      pdwCookie  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pdisp`  
 pro Ukazatel na rozhraní `IDispatch` v jímky klienta v pokynech. Jímka klienta přijímá odchozí volání z jednoduchého spojovacího bodu.  
  
 `pdwCookie`  
 mimo Ukazatel na vrácený token, který jedinečně identifikuje toto připojení. Volající používá tento token později k odstranění připojení předáním do metody `ISimpleConnectionPoint::Unadvise`. Pokud připojení nebylo úspěšně navázáno, je tato hodnota nulová.  
  
## <a name="return-value"></a>Návratová hodnota  
 Metoda vrací `HRESULT`. Možné hodnoty zahrnují hodnoty v následující tabulce, ale nejsou na ně omezeny.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`S_OK`|Metoda byla úspěšná.|  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda vytváří spojení mezi jednoduchým objektem spojovacího bodu a jímkou klienta.  
  
## <a name="see-also"></a>Viz také:  
 @No__t_1 [rozhraní isimpleconnectionpoint –](../../winscript/reference/isimpleconnectionpoint-interface.md)  
 [ISimpleConnectionPoint::Unadvise](../../winscript/reference/isimpleconnectionpoint-unadvise.md)