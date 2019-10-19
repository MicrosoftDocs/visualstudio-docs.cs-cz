---
title: 'IEnumDebugStackFrames –:: Next | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IEnumDebugStackFrames.Next
apilocation:
- jscript.dll
helpviewer_keywords:
- IEnumDebugStackFrames::Next
ms.assetid: ade3f5b0-8ff3-48a0-9433-270789e6d53e
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 17261f8ba9b2957d33ed7019c16f2e1423b6b42e
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575553"
---
# <a name="ienumdebugstackframesnext"></a>IEnumDebugStackFrames::Next
Načte zadaný počet segmentů v sekvenci výčtu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT Next(  
   ULONG                       celt,  
   DebugStackFrameDescriptor*  prgdsfd,  
   ULONG*                      pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `celt`  
 pro Počet segmentů, které se mají načíst.  
  
 `prgdsfd`  
 mimo Vrátí pole `DebugStackFrameDescriptor` rozhraní, které představují segmenty, které jsou načítány.  
  
 `pceltFetched`  
 mimo Skutečný počet segmentů načtených enumerátorem.  
  
## <a name="return-value"></a>Návratová hodnota  
 Metoda vrací `HRESULT`. Možné hodnoty zahrnují hodnoty v následující tabulce, ale nejsou na ně omezeny.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`S_OK`|Metoda byla úspěšná.|  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda načte zadaný počet segmentů v sekvenci výčtu.  
  
## <a name="see-also"></a>Viz také:  
 @No__t_1 [rozhraní IEnumDebugStackFrames –](../../winscript/reference/ienumdebugstackframes-interface.md)  
 [DebugStackFrameDescriptor – struktura](../../winscript/reference/debugstackframedescriptor-structure.md)