---
title: IEnumDebugCodeContexts::Next | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 00a3a5765f5b5a62753653d24cf27e4667a5647f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24794700"
---
# <a name="ienumdebugcodecontextsnext"></a>IEnumDebugCodeContexts::Next
Načte zadaný počet segmentů v pořadí výčtu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT Next(  
   ULONG                celt,  
   IDebugCodeContext**  pscc,  
   ULONG*               pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `celt`  
 [v] Počet segmentů k načtení.  
  
 `pscc`  
 [out] Vrátí pole `IDebugCodeContext` rozhraní, která představuje segmenty, dojde k načtení.  
  
 `pceltFetched`  
 [out] Skutečný počet segmentů načtených podle enumerátor.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí metodu `HRESULT`. Možné hodnoty zahrnují hodnoty v následující tabulce, ale nejsou na ně omezeny.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`S_OK`|Metoda byla úspěšná.|  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda načte zadaný počet segmentů v pořadí výčtu.  
  
## <a name="see-also"></a>Viz také  
 [Ienumdebugcodecontexts – rozhraní](../../winscript/reference/ienumdebugcodecontexts-interface.md)