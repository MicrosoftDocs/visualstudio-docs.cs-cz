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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fe609d53571e6ffcd8e18919f0351e29c0329b46
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85465361"
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