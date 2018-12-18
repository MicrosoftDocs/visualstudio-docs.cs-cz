---
title: Idiaaddressmap::set_addressmap – | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap::set_addressMap method
ms.assetid: 81e82073-089b-43d5-af39-49d7a4907c7a
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1d097ccbe5c893c603aaa2a018f8fcd422f15ac2
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49834516"
---
# <a name="idiaaddressmapsetaddressmap"></a>IDiaAddressMap::set_addressMap
Poskytuje mapování adres pro podporu překlady rozvržení obrázku.  
  
## <a name="syntax"></a>Syntaxe  
  
```C++  
HRESULT set_addressMap (   
   DWORD                     cbData,  
   struct DiaAddressMapEntry data[],  
   BOOL                      imagetoSymbols  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `cbData`  
 [in] Počet prvků v `data` parametru.  
  
 `data[]`  
 [in] Pole [diaaddressmapentry – struktura](../../debugger/debug-interface-access/diaaddressmapentry.md) struktury, které definují mapování překladu.  
  
 `imagetoSymbols`  
 [in] `TRUE` Pokud `data` parametr definuje mapování z nové rozložení obrázku do původního rozložení (jak je popsáno ve symboly ladění). `FALSE` Pokud `data` je mapu, která bude nové rozložení obrázku z původního rozložení.  
  
## <a name="return-value"></a>Návratová hodnota  
 Pokud je úspěšná, vrátí `S_OK`; v opačném případě vrátí kód chyby.  
  
## <a name="remarks"></a>Poznámky  
 Obvykle DIA načte mapování překladu adres ze souboru databáze (PDB) programu. Pokud chybí, jsou tyto hodnoty [idiaaddressmap::set_imageheaders –](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md) metoda je volána dvakrát, jednou s `imagetoSymbols` parametr nastaven na `TRUE` a jednou pro `imagetoSymbols` parametr nastaven na `FALSE`. Překlady adres mapy nelze povolit pomocí [idiaaddressmap::put_addressmapenabled –](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md) metoda Pokud jsou k dispozici obou mapách překladu.  
  
## <a name="see-also"></a>Viz také  
 [Diaaddressmapentry – struktura](../../debugger/debug-interface-access/diaaddressmapentry.md)   
 [Idiaaddressmap –](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [Idiaaddressmap::put_addressmapenabled –](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md)   
 [IDiaAddressMap::set_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md)