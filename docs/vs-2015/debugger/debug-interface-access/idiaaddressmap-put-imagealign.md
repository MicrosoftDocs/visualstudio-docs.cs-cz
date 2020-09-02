---
title: IDiaAddressMap::p ut_imageAlign | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap::put_imageAlign method
ms.assetid: f9ce875d-c263-43e5-a534-f34c37f9866f
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5e0fa57c38c8451bde84d96ab32bc7980c5e2d8b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "64799980"
---
# <a name="idiaaddressmapput_imagealign"></a>IDiaAddressMap::put_imageAlign
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Nastaví zarovnání obrázku.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT put_imageAlign (   
   DWORD NewVal  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 NewVal  
 pro Nová hodnota zarovnání obrázku pro spustitelný soubor.  
  
## <a name="return-value"></a>Návratová hodnota  
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.  
  
## <a name="remarks"></a>Poznámky  
 Image (načtené spustitelné soubory) jsou zarovnané na zadané hranice paměti. Toto zarovnání může být ovlivněno aktuální architekturou systému a možnostmi kompilovat a propojit čas. Zarovnání obrázku je vždy na hranicích bajtů. Následující hodnoty zarovnání obrázku jsou platné: 1, 2, 4, 8, 16, 16, 32 a 64 bajtových hranic.  
  
 Aktuální zarovnání obrázku lze načíst voláním metody [IDiaAddressMap:: get_imageAlign](../../debugger/debug-interface-access/idiaaddressmap-get-imagealign.md) .  
  
> [!NOTE]
> Bitová kopie je již načtena v době, kdy lze tuto metodu volat. `put_imageAlign`Metoda se obvykle používá, když se obrázek přesunul nebo změnil a vyžaduje se nové zarovnání.  
  
## <a name="see-also"></a>Viz také  
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [IDiaAddressMap::get_imageAlign](../../debugger/debug-interface-access/idiaaddressmap-get-imagealign.md)
