---
description: Načte vložený zdroj prostřednictvím indexu.
title: 'IDiaEnumInjectedSources:: Item | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumInjectedSources::Item method
ms.assetid: 14846955-7270-451d-91d2-9cb34bb65187
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 1d1ab3a9ce19705a4d9ff22f33a1275efc0e8b02
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102148995"
---
# <a name="idiaenuminjectedsourcesitem"></a>IDiaEnumInjectedSources::Item
Načte vložený zdroj prostřednictvím indexu.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT Item ( 
   DWORD                index,
   IDiaInjectedSource** injectedSource
);
```

#### <a name="parameters"></a>Parametry
 index

pro Index objektu [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md) , který se má načíst Index je rozsah 0 až `count` -1, kde `count` je vrácen metodou [IDiaEnumInjectedSources:: get_Count](../../debugger/debug-interface-access/idiaenuminjectedsources-get-count.md) .

 injectedSource

mimo Vrátí objekt [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md) představující vložený zdroj.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.

## <a name="see-also"></a>Viz také
- [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)
- [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)
