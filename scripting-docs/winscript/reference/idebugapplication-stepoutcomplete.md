---
title: IDebugApplication::StepOutComplete | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 4c344f0316bda6ed5ef895c1b88ae7b1a6465e73
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24793845"
---
# <a name="idebugapplicationstepoutcomplete"></a>IDebugApplication::StepOutComplete
Oznámí správci ladění procesu, že modul jazyka v režimu krokování se vrátit do jeho volajícího.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT StepOutComplete();  
```  
  
#### <a name="parameters"></a>Parametry  
 Tato metoda nepřijímá žádné parametry.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí metodu `HRESULT`. Možné hodnoty zahrnují hodnoty v následující tabulce, ale nejsou na ně omezeny.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`S_OK`|Metoda byla úspěšná.|  
  
## <a name="remarks"></a>Poznámky  
 Moduly jazyka volat tuto metodu v režimu krokování těsně před vracejí jejich volajícího. Správce ladění proces používá tuto příležitost upozornit všechny ostatní skriptovacích strojů, které by mělo dojít při první příležitosti. Tento postup je krok jak mezi jazyky jsou implementované režimy.  
  
## <a name="see-also"></a>Viz také  
 [Idebugapplication – rozhraní](../../winscript/reference/idebugapplication-interface.md)