---
title: Isimpleconnectionpoint –::D escribeEvents | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- ISimpleConnectionPoint.DescribeEvents
apilocation:
- pdm.dll
helpviewer_keywords:
- ISimpleConnectionPoint::DescribeEvents
ms.assetid: 659ea05f-d41e-424a-bb38-df7672b2d135
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b5000689d588fe3f63ec5408893187bba8d13d63
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571817"
---
# <a name="isimpleconnectionpointdescribeevents"></a>ISimpleConnectionPoint::DescribeEvents
Vrátí DISPID a název každé události v zadaném rozsahu událostí.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT DescribeEvents(  
   ULONG    iEvent,  
   ULONG    cEvents,  
   DISPID*  prgid,  
   BSTR*    prgbstr,  
   ULONG*   pcEventsFetched  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `iEvent`  
 pro Index první události, která se má načíst  
  
 `cEvents`  
 pro Počet událostí, které mají být načteny.  
  
 `prgid`  
 mimo Pole hodnot DISPID události  
  
 `prgbstr`  
 mimo Pole názvů událostí.  
  
 `pcEventsFetched`  
 mimo Skutečný počet načtených událostí.  
  
## <a name="return-value"></a>Návratová hodnota  
 Metoda vrací `HRESULT`. Možné hodnoty zahrnují hodnoty v následující tabulce, ale nejsou na ně omezeny.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`S_OK`|Metoda byla úspěšná.|  
|`S_FALSE`|Bylo požadováno více událostí, než bylo k dispozici. Nedostupné události jsou reprezentovány s DISPID_NULL a s hodnotou BSTR.|  
|`E_INVALIDARG`|Nemohly být načteny žádné prvky.|  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda vrací identifikátor DISPID a název každé události v zadaném rozsahu událostí.  
  
## <a name="see-also"></a>Viz také:  
 [ISimpleConnectionPoint – rozhraní](../../winscript/reference/isimpleconnectionpoint-interface.md)