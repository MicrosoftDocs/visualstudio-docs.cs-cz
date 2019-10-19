---
title: 'Ienumremotedebugapplicationthreads –:: Next | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IEnumRemoteDebugApplicationThreads.Next
apilocation:
- pdm.dll
helpviewer_keywords:
- IEnumRemoteDebugApplicationThreads::Next
ms.assetid: d8d10d7e-3468-49be-acf9-d842db9940e7
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 36d24ffaca05b64c05815124358024d3b88b0d74
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575177"
---
# <a name="ienumremotedebugapplicationthreadsnext"></a>IEnumRemoteDebugApplicationThreads::Next
Metoda `Next` načte zadaný počet segmentů v sekvenci výčtu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT Next(  
   ULONG                            celt,  
   IRemoteDebugApplicationThread**  pprdat,  
   ULONG*                           pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `celt`  
 pro Počet segmentů, které se mají načíst.  
  
 `pprdat`  
 mimo Vrátí pole `IRemoteDebugApplicationThread` rozhraní, které představují segmenty, které jsou načítány.  
  
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
 [IEnumRemoteDebugApplicationThreads – rozhraní](../../winscript/reference/ienumremotedebugapplicationthreads-interface.md)