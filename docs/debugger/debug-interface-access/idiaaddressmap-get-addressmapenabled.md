---
title: Idiaaddressmap::get_addressmapenabled – | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap::get_addressMapEnabled method
ms.assetid: 6183dc5e-befa-4e5a-ae5a-f4aa24f3ed9e
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 47d0b3ac64724881ab72cb9d9d873bc02f3bec9b
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49938835"
---
# <a name="idiaaddressmapgetaddressmapenabled"></a>IDiaAddressMap::get_addressMapEnabled
Označuje, zda mapování adres se vytvořilo pro konkrétní relace.  
  
## <a name="syntax"></a>Syntaxe  
  
```C++  
HRESULT get_addressMapEnabled (   
   BOOL* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 pRetVal  
 [out] Vrátí `TRUE` Pokud mapování adresy je povolené.  
  
## <a name="return-value"></a>Návratová hodnota  
 Pokud je úspěšná, vrátí `S_OK`; v opačném případě vrátí kód chyby.  
  
## <a name="remarks"></a>Poznámky  
 Spustitelný soubor po procesory někdy aktualizovat spustitelný soubor. DIA obsahuje mechanismus pro podporu překladu symboly do nového rozložení.  
  
 Klientské aplikace můžete nastavit mapa adres pro konkrétní relace tím, že získáme [idiaaddressmap –](../../debugger/debug-interface-access/idiaaddressmap.md) rozhraní z [idiasession –](../../debugger/debug-interface-access/idiasession.md) rozhraní a volání [IDiaAddressMap::set_ addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md) metoda za nímž následuje volání [idiaaddressmap::put_addressmapenabled –](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md) metody. `get_addressMapEnabled` Metoda vrátí výsledky volání `put_addressMapEnabled` metody.  
  
## <a name="see-also"></a>Viz také  
 [Idiaaddressmap –](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [Idiasession –](../../debugger/debug-interface-access/idiasession.md)   
 [Idiaaddressmap::set_addressmap –](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)   
 [IDiaAddressMap::put_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md)