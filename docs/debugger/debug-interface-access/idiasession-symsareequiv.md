---
title: 'IDiaSession:: symsAreEquiv | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::symsAreEquiv method
ms.assetid: 9941d520-e203-46c0-83c3-b3a967f4fc59
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 10aa5f1b086856793fe32512867834848b6f7162
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99855016"
---
# <a name="idiasessionsymsareequiv"></a>IDiaSession::symsAreEquiv
Kontroluje, zda jsou dva symboly ekvivalentní.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT symsAreEquiv ( 
   IDiaSymbol* symbolA,
   IDiaSymbol* symbolB
);
```

#### <a name="parameters"></a>Parametry
 `symbolA`

pro První objekt [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) použitý v porovnání

 `symbolB`

pro Druhý `IDiaSymbol` objekt použitý v porovnání.

## <a name="return-value"></a>Návratová hodnota
 Pokud jsou symboly ekvivalentní, vrátí, `S_OK` jinak vrátí `S_FALSE` , symboly nejsou ekvivalentní. V opačném případě vrátí kód chyby.

## <a name="see-also"></a>Viz také
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)