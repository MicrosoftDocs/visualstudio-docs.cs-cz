---
description: Načte příznak, který určuje, zda není zarovnaný uživatelsky definovaný datový typ.
title: 'IDiaSymbol:: get_unalignedType | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_unalignedType method
ms.assetid: fdcb38fb-490e-4d15-b4e5-3770043a366c
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b126951bdc178aca4aae36faeb2d41e307bf9ef1
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102155541"
---
# <a name="idiasymbolget_unalignedtype"></a>IDiaSymbol::get_unalignedType
Načte příznak, který určuje, zda není zarovnaný uživatelsky definovaný datový typ.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_unalignedType ( 
   BOOL* pRetVal
);
```

#### <a name="parameters"></a>Parametry
 `pRetVal`

mimo Vrátí hodnotu `TRUE` , pokud uživatelsky definovaný datový typ není zarovnán; jinak vrátí `FALSE` .

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí, `S_OK` jinak vrátí `S_FALSE` nebo kód chyby.

> [!NOTE]
> Návratová hodnota `S_FALSE` znamená, že vlastnost není k dispozici pro symbol.

## <a name="see-also"></a>Viz také
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
