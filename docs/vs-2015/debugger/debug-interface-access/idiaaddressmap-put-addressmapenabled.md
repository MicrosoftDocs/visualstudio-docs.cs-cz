---
title: IDiaAddressMap::p ut_addressMapEnabled | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap::put_addressMapEnabled method
ms.assetid: 0f205337-4e59-4383-8059-7b1d207d6dcd
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 4f2f7fc6fd512fa121cf96cb64f4ce4b961772e1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68198674"
---
# <a name="idiaaddressmapput_addressmapenabled"></a>IDiaAddressMap::put_addressMapEnabled
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Určuje, zda se má mapa adres použít k překladu adres symbolů.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT put_addressMapEnabled (   
   BOOL NewVal  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 NewVal  
 pro Nastavte na `TRUE` , chcete-li povolit překlad symbolů nebo `FALSE` zakázat.  
  
## <a name="return-value"></a>Návratová hodnota  
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.  
  
## <a name="remarks"></a>Poznámky  
 Spustitelné procesory někdy aktualizují spustitelný soubor. DIA obsahuje mechanismus pro podporu překladu symbolů na nové rozložení.  
  
 Po načtení souboru PDB je povolena mapa adres uložená v souboru. Existují však situace, kdy může klientská aplikace potřebovat dodat vlastní mapu adresy voláním metody [IDiaAddressMap:: set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md) . Pokud `set_addressMap` je metoda úspěšná, klientská aplikace musí zavolat `put_addressMapEnabled` metodu s `NewVal` parametrem `TRUE` pro povolení použití této mapy adres.  
  
 Aktuální stav povoleného mapování adres lze načíst voláním metody [IDiaAddressMap:: get_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-addressmapenabled.md) .  
  
## <a name="see-also"></a>Viz také  
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [IDiaAddressMap:: set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)   
 [IDiaAddressMap::get_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-addressmapenabled.md)
