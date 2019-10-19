---
title: 'IDebugApplication –:: StepOutComplete | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplication.StepOutComplete
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplication::StepOutComplete
ms.assetid: 9675b214-7be5-4cf7-a63f-7865f3c54371
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f50d7e8a8936e52f4177450e7d163c4cfeaa55df
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571034"
---
# <a name="idebugapplicationstepoutcomplete"></a>IDebugApplication::StepOutComplete
Upozorní správce ladění procesu, že jazykový modul v režimu jednoho kroku se bude vracet ke svému volajícímu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT StepOutComplete();  
```  
  
#### <a name="parameters"></a>Parametry  
 Tato metoda nepřijímá žádné parametry.  
  
## <a name="return-value"></a>Návratová hodnota  
 Metoda vrací `HRESULT`. Možné hodnoty zahrnují hodnoty v následující tabulce, ale nejsou na ně omezeny.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`S_OK`|Metoda byla úspěšná.|  
  
## <a name="remarks"></a>Poznámky  
 Jazykové moduly volají tuto metodu v režimu jednoduchých kroků těsně předtím, než se vrátí volajícímu. Správce procesu ladění používá tuto příležitost k oznamování všech dalších skriptovacích strojů, které by měly být při první příležitosti přerušeny. Tímto postupem je implementace režimů kroků mezi jazyky.  
  
## <a name="see-also"></a>Viz také:  
 [IDebugApplication – rozhraní](../../winscript/reference/idebugapplication-interface.md)