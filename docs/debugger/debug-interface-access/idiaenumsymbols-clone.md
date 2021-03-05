---
description: Vytvoří enumerátor, který obsahuje stejný stav výčtu jako aktuální enumerátor symbolů.
title: 'IDiaEnumSymbols:: Clone | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSymbols::Clone method
ms.assetid: 5c542025-98cf-4307-901f-b9430f780cf0
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 3c6af6aa1aa912c4a1f568bb11318803deb87939
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102148722"
---
# <a name="idiaenumsymbolsclone"></a>IDiaEnumSymbols::Clone
Vytvoří enumerátor, který obsahuje stejný stav výčtu jako aktuální enumerátor.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT Clone ( 
   IDiaEnumSymbols** ppenum
);
```

#### <a name="parameters"></a>Parametry
 ppenum

mimo Vrátí objekt [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md) , který obsahuje duplikát objektu Enumerator. Symboly nejsou duplikovány, pouze enumerátor.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.

## <a name="see-also"></a>Viz také
- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)
