---
title: 'IDiaSymbol:: get_acceleratorPointerTags | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
ms.assetid: 30e13cee-e511-49ec-affd-99b0097071b2
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 1f45c212502a6f8cb065be536e5ecbb7e6b61d7b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99854617"
---
# <a name="idiasymbolget_acceleratorpointertags"></a>IDiaSymbol::get_acceleratorPointerTags
Vrátí všechny hodnoty značek akcelerátoru, které odpovídají funkci pro zástupné procedury akcelerátoru C++ AMP.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_acceleratorPointerTags(
   DWORD          cnt,
   DWORD*         pcnt,
   DWORD*         pPointerTags);
```

#### <a name="parameters"></a>Parametry
 `cnt`

pro Velikost výstupního pole `pPointerTags` .

 `pcnt`

mimo Počet značek akcelerátoru v zástupné funkci akcelerátoru C++ AMP.

 `pPointerTags`

mimo `DWORD` Ukazatel na pole, který je vyplněn hodnotami značky akcelerátoru v zástupné funkci akcelerátoru C++ amp.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí, `S_OK` jinak vrátí `S_FALSE` nebo kód chyby.

## <a name="remarks"></a>Poznámky
 Tato metoda se volá na `IDiaSymbol` rozhraní, které odpovídá funkci pro zástupné procedury akcelerátoru C++ amp.

## <a name="see-also"></a>Viz také
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)