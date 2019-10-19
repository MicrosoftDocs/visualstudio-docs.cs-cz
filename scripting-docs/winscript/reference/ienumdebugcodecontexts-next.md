---
title: 'Ienumdebugcodecontexts –:: Next | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IEnumDebugCodeContexts.Next
apilocation:
- jscript.dll
helpviewer_keywords:
- IEnumDebugCodeContexts::Next
ms.assetid: 844cc353-ae0b-45e1-84a6-32b0bb67f57f
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 289085265f182ec0fafca27a2cc18e8865b98091
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577177"
---
# <a name="ienumdebugcodecontextsnext"></a>IEnumDebugCodeContexts::Next
Načte zadaný počet segmentů v sekvenci výčtu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT Next(  
   ULONG                celt,  
   IDebugCodeContext**  pscc,  
   ULONG*               pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `celt`  
 pro Počet segmentů, které se mají načíst.  
  
 `pscc`  
 mimo Vrátí pole `IDebugCodeContext` rozhraní, které představují segmenty, které jsou načítány.  
  
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
 [IEnumDebugCodeContexts – rozhraní](../../winscript/reference/ienumdebugcodecontexts-interface.md)