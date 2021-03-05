---
description: Načte celou řadu uživatelsky definovaného typu (UDT).
title: 'IDiaSymbol:: get_udtKind | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_udtKind method
ms.assetid: 4002f887-aea6-4475-b302-67c57079fe0a
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 6c49fc5b27a9af2a986b0cde1dc41b3a07df7150
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102155577"
---
# <a name="idiasymbolget_udtkind"></a>IDiaSymbol::get_udtKind
Načte celou řadu uživatelsky definovaného typu (UDT).

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_udtKind ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parametry
 `pRetVal`

mimo Vrací hodnotu z výčtu [výčtu udtkind –](../../debugger/debug-interface-access/udtkind.md) , který určuje druh typu UDT: struktura, třída nebo sjednocení.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí, `S_OK` jinak vrátí `S_FALSE` nebo kód chyby.

> [!NOTE]
> Návratová hodnota `S_FALSE` znamená, že vlastnost není k dispozici pro symbol.

## <a name="see-also"></a>Viz také
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [UdtKind – výčet](../../debugger/debug-interface-access/udtkind.md)
