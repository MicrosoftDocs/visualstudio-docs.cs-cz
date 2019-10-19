---
title: 'Iperpropertybrowsing2 –:: GetPredefinedStrings | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IPerPropertyBrowsing2.GetPredefinedStrings
apilocation:
- scrobj.dll
helpviewer_keywords:
- IPerPropertyBrowsing2::GetPredefinedStrings
ms.assetid: d2fa30f7-a566-4dbd-8b47-ffdc00419771
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 55ade724dd9ee5d59feb9d04c5b525ca839a9cec
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576777"
---
# <a name="iperpropertybrowsing2getpredefinedstrings"></a>IPerPropertyBrowsing2::GetPredefinedStrings
Umožňuje volajícímu vyplnit seznam se počítaným polem ukazatelů na řetězec, který představuje potenciální hodnoty pro tuto vlastnost.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetPredefinedStrings(  
   DISPID  dispid,  
   CALPOLESTR*  pCaStrings,  
   CADWORD*  pCaCookies  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `dispid`  
 pro Identifikátor odeslání vlastnosti, pro kterou volající požaduje seznam řetězců  
  
 `pCaStrings`  
 mimo Ukazatel na vypočtenou strukturu pole přidělenou volajícímu, která obsahuje počet prvků a adresu pole ukazatelů řetězce, které jsou přiděleny metodě. Pokud se metoda nezdařila, není přidělena žádná paměť a obsah struktury není definován.  
  
 `pCaCookies`  
 mimo Ukazatel na vypočtenou strukturu pole přidělenou volajícímu, která obsahuje počet prvků a adresu pole hodnot typu DWORD přidělených metodou. Pokud se metoda nezdařila, není přidělena žádná paměť a obsah struktury není definován.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrací platný `HRESULT`, obvykle `S_OK`.  
  
## <a name="see-also"></a>Viz také:  
 [IPerPropertyBrowsing2 – rozhraní 1](../../winscript/reference/iperpropertybrowsing2-interface-1.md)