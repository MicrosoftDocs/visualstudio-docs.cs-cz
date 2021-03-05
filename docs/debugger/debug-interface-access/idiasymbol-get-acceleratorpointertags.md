---
description: Vrátí všechny hodnoty značek akcelerátoru, které odpovídají funkci pro zástupné procedury akcelerátoru C++ AMP.
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
ms.openlocfilehash: 99bf6f90cb15484613a6572952a6f8501fa6bf31
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102156599"
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
