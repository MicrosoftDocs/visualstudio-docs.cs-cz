---
title: 'IDiaEnumSymbols:: Skip | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSymbols::Skip method
ms.assetid: e601fbc9-b10b-41c7-8180-959e57efabe8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9252826470decd3cddfabdcc2a00e22037d5de5c
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72743910"
---
# <a name="idiaenumsymbolsskip"></a>IDiaEnumSymbols::Skip
Přeskočí zadaný počet symbolů v sekvenci výčtu.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT Skip ( 
   ULONG celt
);
```

#### <a name="parameters"></a>Parametry
 celt

pro Počet symbolů v sekvenci výčtu k přeskočení.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí `S_OK`; jinak vrátí `S_FALSE`, pokud nejsou k dispozici žádné další symboly, které by bylo možné přeskočit.

## <a name="see-also"></a>Viz také:
- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)