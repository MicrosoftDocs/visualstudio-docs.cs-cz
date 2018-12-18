---
title: IEnumDebugApplicationNodes::Clone | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IEnumDebugApplicationNodes.Clone
apilocation:
- pdm.dll
helpviewer_keywords:
- IEnumDebugApplicationNodes::Clone
ms.assetid: 7190954d-e2da-4a84-8e37-81d4d27886a8
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dab58a36110c0f0321bbf490a105bff9cddad009
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24794211"
---
# <a name="ienumdebugapplicationnodesclone"></a>IEnumDebugApplicationNodes::Clone
Vytvoří enumerátor, který obsahuje stejného stavu jako aktuální enumerátor.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT Clone(  
   IEnumDebugApplicationNodes**  pperddp  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pperddp`  
 [out] Vrátí `IEnumDebugApplicationNodes` rozhraní klonu enumerátor.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí metodu `HRESULT`. Možné hodnoty zahrnují hodnoty v následující tabulce, ale nejsou na ně omezeny.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`S_OK`|Metoda byla úspěšná.|  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda vytvoří enumerátor, který obsahuje stejného stavu jako aktuální enumerátor.  
  
## <a name="see-also"></a>Viz také  
 [Ienumdebugapplicationnodes – rozhraní](../../winscript/reference/ienumdebugapplicationnodes-interface.md)