---
title: IPerPropertyBrowsing2::GetPredefinedStrings | Dokumentace Microsoftu
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: a60225e69a04399a3ff0160291b84e9f3fda513c
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49915958"
---
# <a name="iperpropertybrowsing2getpredefinedstrings"></a>IPerPropertyBrowsing2::GetPredefinedStrings
Umožňuje volajícímu naplnit pole se seznamem spočítaný počet pole ukazatelů na řetězec, které představují potenciální hodnoty této vlastnosti.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetPredefinedStrings(  
   DISPID  dispid,  
   CALPOLESTR*  pCaStrings,  
   CADWORD*  pCaCookies  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `dispid`  
 [in] Identifikátor odeslání vlastnost, pro kterou volající požaduje seznam řetězců.  
  
 `pCaStrings`  
 [out] Ukazatel na strukturu pole přidělené volajícímu, spočítaný počet, který obsahuje počet prvků a adresa přidělena metoda pole ukazatelů na řetězec. Jestliže metoda selže, žádná paměť je přidělena a obsah struktury nejsou definovány.  
  
 `pCaCookies`  
 [out] Ukazatel na strukturu pole přidělené volajícímu, spočítaný počet, který obsahuje počet prvků a adresa přidělena metoda pole typu DWORD. Jestliže metoda selže, žádná paměť je přidělena a obsah struktury nejsou definovány.  
  
## <a name="return-value"></a>Návratová hodnota  
 Bude vracet platnou `HRESULT`, obvykle `S_OK`.  
  
## <a name="see-also"></a>Viz také  
 [IPerPropertyBrowsing2 – rozhraní 1](../../winscript/reference/iperpropertybrowsing2-interface-1.md)