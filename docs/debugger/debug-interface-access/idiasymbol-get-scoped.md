---
title: 'IDiaSymbol:: get_scoped | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_scoped method
ms.assetid: 588163f7-958e-4072-bf66-db5c5f07d3cb
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8ab42f39535dae2f6eb1e84e0c656dc4ff601f18
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85468719"
---
# <a name="idiasymbolget_scoped"></a>IDiaSymbol::get_scoped
Načte příznak, který určuje, zda se uživatelsky definovaný datový typ zobrazuje v neglobálním lexikálním oboru.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_scoped ( 
   BOOL* pRetVal
);
```

#### <a name="parameters"></a>Parametry
 `pRetVal`

mimo Vrátí, `TRUE` zda je uživatelem definovaný datový typ zobrazen v neglobálním lexikálním oboru; v opačném případě vrátí `FALSE` .

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí, `S_OK` jinak vrátí `S_FALSE` nebo kód chyby.

> [!NOTE]
> Návratová hodnota `S_FALSE` znamená, že vlastnost není k dispozici pro symbol.

## <a name="see-also"></a>Viz také
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)