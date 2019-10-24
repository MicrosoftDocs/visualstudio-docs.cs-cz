---
title: 'IDiaImageData:: get_imageBase | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaImageData::get_imageBase method
ms.assetid: 4ba3d9e4-b205-4ee6-a41d-6996972f1f85
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7887fea30b04f4ebb6605169c58551122eccf73d
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72743441"
---
# <a name="idiaimagedataget_imagebase"></a>IDiaImageData::get_imageBase
Načte umístění paměti, kde má být obrázek založen.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_imageBase ( 
   ULONGLONG* pRetVal
);
```

#### <a name="parameters"></a>Parametry
 `pRetVal`

mimo Vrátí navrhovanou základní hodnotu obrázku.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí `S_OK`; v opačném případě vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Vzhledem k tomu, že jsou v konfliktu s obrázkem, může se při načtení image automaticky znovu zakládat do nevyužitého místa v paměti. Tato metoda vrátí základní pomocný parametr (navrhované umístění v paměti), který byl uložen v modulu v době kompilace.

## <a name="see-also"></a>Viz také:
- [IDiaImageData](../../debugger/debug-interface-access/idiaimagedata.md)