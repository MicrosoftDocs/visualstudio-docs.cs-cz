---
description: Načte zdrojový soubor a číslo řádku, které označují, kde je definován zadaný uživatelsky definovaný typ.
title: 'IDiaSymbol:: getSrcLineOnTypeDefn | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
ms.assetid: ad554d18-9988-4b64-ad71-e7594c266e94
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 5d6288df169db6d0b5e0a0c31c674f398510f77c
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102161723"
---
# <a name="idiasymbolgetsrclineontypedefn"></a>IDiaSymbol::getSrcLineOnTypeDefn
Načte zdrojový soubor a číslo řádku, které označují, kde je definován zadaný uživatelsky definovaný typ.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT getSrcLineOnTypeDefn(
   IDiaLineNumber **ppResult);
```

#### <a name="parameters"></a>Parametry
 `ppResult`

mimo `IDiaLineNumber` Objekt, který obsahuje zdrojový soubor a číslo řádku, kde je definován uživatelem.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí, `S_OK` jinak vrátí `S_FALSE` nebo kód chyby.

## <a name="see-also"></a>Viz také
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)
