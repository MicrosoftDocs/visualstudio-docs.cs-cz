---
title: 'Iperpropertybrowsing2 –:: GetDisplayString | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IPerPropertyBrowsing2.GetDisplayString
apilocation:
- scrobj.dll
helpviewer_keywords:
- IPerPropertyBrowsing2::GetDisplayString
ms.assetid: 8f75c6a9-86a9-4e2d-8cb4-74e7b1c0a524
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bc702ad15d1aba04bf991c04b585728afde4fb41
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571451"
---
# <a name="iperpropertybrowsing2getdisplaystring"></a>IPerPropertyBrowsing2::GetDisplayString
Získá řetězec pro zobrazení typů, které nejsou ve své podstatě viditelné, je název popisující vlastnost a může se zobrazit v uživatelském rozhraní volajícího.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetDisplayString(  
   DISPID  dispid,  
   BSTR*  pBstr  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `dispid`  
 pro Identifikátor odeslání vlastnosti, jejíž zobrazovaný název je požadován.  
  
 `pBstr`  
 mimo Ukazatel na `BSTR`, který obsahuje zobrazovaný název pro vlastnost identifikovanou `dispID`.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrací platný `HRESULT`, obvykle `S_OK`.  
  
## <a name="remarks"></a>Poznámky  
 Vrácený řetězec není platnou hodnotou vlastnosti. Je to pouze řetězcové zobrazení vlastnosti.  
  
## <a name="see-also"></a>Viz také:  
 [IPerPropertyBrowsing2 – rozhraní 1](../../winscript/reference/iperpropertybrowsing2-interface-1.md)