---
title: 'Imachinedebugmanagercookie –:: EnumApplications | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IMachineDebugManagerCookie.EnumApplications
apilocation:
- scrobj.dll
helpviewer_keywords:
- IMachineDebugManagerCookie::EnumApplications
ms.assetid: 03f863cf-fa7f-4ec4-b1a1-1ae0ad296c39
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e01af108e2e417976a61038d7ed3952cb33742c6
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573892"
---
# <a name="imachinedebugmanagercookieenumapplications"></a>IMachineDebugManagerCookie::EnumApplications
Vrátí enumerátor pro aktuální seznam spuštěných aplikací.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT EnumApplications(  
   IEnumRemoteDebugApplications**  ppeda  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppeda`  
 mimo Enumerátor obsahující aktuální seznam spuštěných aplikací.  
  
## <a name="return-value"></a>Návratová hodnota  
 Metoda vrací `HRESULT`. Možné hodnoty zahrnují hodnoty v následující tabulce, ale nejsou na ně omezeny.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`S_OK`|Metoda byla úspěšná.|  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda vrací enumerátor pro aktuální seznam spuštěných aplikací. Rozhraní IDE ladicího programu používá tuto metodu k zobrazení a připojení aplikací pro účely ladění.  
  
## <a name="see-also"></a>Viz také:  
 [IMachineDebugManagerCookie – rozhraní](../../winscript/reference/imachinedebugmanagercookie-interface.md)