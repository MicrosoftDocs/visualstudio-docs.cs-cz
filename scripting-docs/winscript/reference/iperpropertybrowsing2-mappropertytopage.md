---
title: 'Iperpropertybrowsing2 –:: MapPropertyToPage | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IPerPropertyBrowsing2.MapPropertyToPage
apilocation:
- scrobj.dll
helpviewer_keywords:
- IPerPropertyBrowsing2::MapPropertyToPage
ms.assetid: e6418a8e-500b-42e1-9b5a-52e6f7567f99
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e9e3f821d9e02be567f970d8db1c238ee5cebd29
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577119"
---
# <a name="iperpropertybrowsing2mappropertytopage"></a>IPerPropertyBrowsing2::MapPropertyToPage
Vrátí CLSID stránky vlastností, kterou lze použít k úpravě této vlastnosti.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT MapPropertyToPage(  
   DISPID  dispid,  
   CLSID*  pClsidPropPage  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `dispid`  
 pro Identifikátor odeslání vlastnosti zájmu.  
  
 `pClsidPropPage`  
 mimo Ukazatel na identifikátor CLSID identifikující stránku vlastností přidruženou k vlastnosti. Pokud tato metoda není úspěšná, * `pClsidPropPage` je nastavená na CLSID_NULL.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrací platný `HRESULT`, obvykle `S_OK`.  
  
## <a name="see-also"></a>Viz také:  
 [IPerPropertyBrowsing2 – rozhraní 1](../../winscript/reference/iperpropertybrowsing2-interface-1.md)