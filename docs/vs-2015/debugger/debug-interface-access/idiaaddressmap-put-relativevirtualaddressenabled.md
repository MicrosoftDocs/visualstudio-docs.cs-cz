---
title: IDiaAddressMap::p ut_relativeVirtualAddressEnabled | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap::put_relativeVirtualAddressEnabled method
ms.assetid: 767c078e-8ad7-4940-9e00-cae7704aadee
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 14c9924346471e098d9ba9f1abb52fda0d3c9969
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68198661"
---
# <a name="idiaaddressmapput_relativevirtualaddressenabled"></a>IDiaAddressMap::put_relativeVirtualAddressEnabled
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Umožňuje klientovi povolit nebo zakázat výpočet a použití relativních virtuálních adres (RVA).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT put_relativeVirtualAddressEnabled (   
   BOOL NewVal  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 NewVal  
 pro Nastavte na `TRUE` Povolit nebo `FALSE` zakázat.  
  
## <a name="return-value"></a>Návratová hodnota  
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.  
  
## <a name="remarks"></a>Poznámky  
 Adresy pro objekty ladění, které jsou popsány rozhraními DIA a relativní vzhledem k základu obrázku spustitelného souboru, lze načíst jako relativní virtuální adresy.  
  
 Použití RVA je povoleno, když jsou segmenty zpočátku načteny ze souboru PDB. Chcete-li získat aktuální stav použití RVA, zavolejte metodu [IDiaAddressMap:: get_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md) .  
  
 `put_relativeVirtualAddress`Metoda musí být volána, aby bylo možné povolit RVA po úspěšném volání metody [IDiaAddressMap:: set_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md) se vytvořila nová záhlaví obrázků.  
  
## <a name="see-also"></a>Viz také  
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [IDiaAddressMap:: get_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md)   
 [IDiaAddressMap::set_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md)
