---
title: 'Iremotedebugapplicationevents –:: pro\ce | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IRemoteDebugApplicationEvents.OnSetName
apilocation:
- jscript.dll
helpviewer_keywords:
- IRemoteDebugApplicationEvents::OnSetName
ms.assetid: 524dcff3-fb48-4d8f-8989-73eb539454fb
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cb2d3b301888015c2815725c5d1c7903758e319a
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571930"
---
# <a name="iremotedebugapplicationeventsonsetname"></a>IRemoteDebugApplicationEvents::OnSetName
Zpracovává událost názvu sady.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT OnSetName(  
   LPCOLESTR  pstrName  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pstrName`  
 pro Nový název.  
  
## <a name="return-value"></a>Návratová hodnota  
 Metoda vrací `HRESULT`. Možné hodnoty zahrnují hodnoty v následující tabulce, ale nejsou na ně omezeny.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`S_OK`|Metoda byla úspěšná.|  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda zpracovává událost názvu sady.  
  
## <a name="see-also"></a>Viz také:  
 [IRemoteDebugApplicationEvents – rozhraní](../../winscript/reference/iremotedebugapplicationevents-interface.md)