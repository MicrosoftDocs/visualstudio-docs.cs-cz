---
title: 'IDiaSymbol:: get_thisAdjust | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_thisAdjust method
ms.assetid: 56b9a147-e8c0-4d4b-a42a-398214dd5f86
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2475ccf14d892a7f7d1b130c63dbea458038dd41
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/27/2020
ms.locfileid: "85461799"
---
# <a name="idiasymbolget_thisadjust"></a>IDiaSymbol::get_thisAdjust
Načte logický `this` seřizovací modul pro metodu.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_thisAdjust ( 
   LONG* pRetVal
);
```

#### <a name="parameters"></a>Parametry
 `pRetVal`

mimo Vrátí logický `this` seřizovací metodu pro metodu.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí, `S_OK` jinak vrátí `S_FALSE` nebo kód chyby.

> [!NOTE]
> Návratová hodnota `S_FALSE` znamená, že vlastnost není k dispozici pro symbol.

## <a name="remarks"></a>Poznámky
 V některých případech vícenásobné dědičnosti může metoda sám vypočítat hodnotu true přidáním `this` posunu k `this` .

## <a name="see-also"></a>Viz také
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)