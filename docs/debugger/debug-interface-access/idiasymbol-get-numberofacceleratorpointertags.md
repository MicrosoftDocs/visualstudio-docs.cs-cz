---
description: Vrátí počet značek akcelerátoru v C++ AMP funkci zástupné procedury.
title: 'IDiaSymbol:: get_numberOfAcceleratorPointerTags | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
ms.assetid: 1886e3ec-b227-4187-8d93-c5144b4b77ae
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d428ea0a4837d8a1ddf79e6749d852279bb1c115
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102155927"
---
# <a name="idiasymbolget_numberofacceleratorpointertags"></a>IDiaSymbol::get_numberOfAcceleratorPointerTags
Vrátí počet značek akcelerátoru v C++ AMP funkci zástupné procedury.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_numberOfAcceleratorPointerTags(
   DWORD* count);
```

#### <a name="parameters"></a>Parametry
 `count`

mimo Ukazatel na `DWORD` , který obsahuje počet značek akcelerátoru v C++ amp funkci zástupné procedury.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí, `S_OK` jinak vrátí `S_FALSE` nebo kód chyby.

## <a name="remarks"></a>Poznámky
 Tato metoda se volá na `IDiaSymbol` rozhraní, které odpovídá funkci pro zástupné procedury akcelerátoru C++ amp.

## <a name="see-also"></a>Viz také
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
