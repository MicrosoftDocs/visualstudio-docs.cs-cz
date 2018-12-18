---
title: ISimpleConnectionPoint::DescribeEvents | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 42dab9558d46eae0fbb640c60264a79877708321
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24796359"
---
# <a name="isimpleconnectionpointdescribeevents"></a>ISimpleConnectionPoint::DescribeEvents
Vrátí DISPID a název pro všechny události v zadaném rozsahu událostí.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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
 [v] Index první událost pro načtení.  
  
 `cEvents`  
 [v] Počet události k načtení.  
  
 `prgid`  
 [out] Pole hodnot DISPID událostí.  
  
 `prgbstr`  
 [out] Pole názvy událostí.  
  
 `pcEventsFetched`  
 [out] Skutečný počet načtených události.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí metodu `HRESULT`. Možné hodnoty zahrnují hodnoty v následující tabulce, ale nejsou na ně omezeny.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`S_OK`|Metoda byla úspěšná.|  
|`S_FALSE`|Další události se požadovaly než nebyly k dispozici. Není k dispozici události jsou reprezentované pomocí DISPID_NULL a null BSTR.|  
|`E_INVALIDARG`|Může být načteny žádné elementy.|  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda vrátí DISPID a název pro všechny události v zadaném rozsahu událostí.  
  
## <a name="see-also"></a>Viz také  
 [Isimpleconnectionpoint – rozhraní](../../winscript/reference/isimpleconnectionpoint-interface.md)