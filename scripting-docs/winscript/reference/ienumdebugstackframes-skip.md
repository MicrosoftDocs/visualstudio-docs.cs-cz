---
title: IEnumDebugStackFrames::Skip | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IEnumDebugStackFrames.Skip
apilocation:
- jscript.dll
helpviewer_keywords:
- IEnumDebugStackFrames::Skip
ms.assetid: d893d6e9-e119-4f14-99d0-bf23dbd2d625
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 79267220c7ad3ce19d1901c6371554c7aabacde8
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24794343"
---
# <a name="ienumdebugstackframesskip"></a>IEnumDebugStackFrames::Skip
Přeskočí zadaný počet segmentů v posloupnosti výčtu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT Skip(  
   ULONG  celt  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `celt`  
 [v] Počet segmentů v pořadí výčtu tak, aby přeskočil.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí metodu `HRESULT`. Možné hodnoty zahrnují hodnoty v následující tabulce, ale nejsou na ně omezeny.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`S_OK`|Metoda byla úspěšná.|  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda přeskočí zadaný počet segmentů v posloupnosti výčtu.  
  
## <a name="see-also"></a>Viz také  
 [Ienumdebugstackframes – rozhraní](../../winscript/reference/ienumdebugstackframes-interface.md)