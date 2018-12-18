---
title: Idiaaddressmap::get_imagealign – | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap::get_imageAlign method
ms.assetid: f1ba8071-669c-4cf7-9ac0-02f26d99f366
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 409b33953d6674066eff9570288de2e3912bdab3
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49908831"
---
# <a name="idiaaddressmapgetimagealign"></a>IDiaAddressMap::get_imageAlign
Načte aktuální zarovnání obrázku.  
  
## <a name="syntax"></a>Syntaxe  
  
```C++  
HRESULT get_imageAlign (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pRetVal`  
 [out] Vrátí hodnotu zarovnání obrázku ze spustitelného souboru.  
  
## <a name="return-value"></a>Návratová hodnota  
 Pokud je úspěšná, vrátí `S_OK`; v opačném případě vrátí kód chyby.  
  
## <a name="remarks"></a>Poznámky  
 Image je zarovnán konkrétní paměti hranice v závislosti, jak byl obrázek načten a vytvořili. Zarovnání je obvykle na hranicích 1, 2, 4, 8, 16, 32 nebo 64 bajtů. Zarovnání obrázku můžete nastavit pomocí volání [idiaaddressmap::put_imagealign –](../../debugger/debug-interface-access/idiaaddressmap-put-imagealign.md) metody.  
  
## <a name="see-also"></a>Viz také  
 [Idiaaddressmap –](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [IDiaAddressMap::put_imageAlign](../../debugger/debug-interface-access/idiaaddressmap-put-imagealign.md)