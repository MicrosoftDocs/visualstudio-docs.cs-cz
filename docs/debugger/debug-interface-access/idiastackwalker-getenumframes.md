---
title: 'IDiaStackWalker:: getEnumFrames | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalker2::getEnumFrames method
ms.assetid: f9f09729-4c34-441c-989c-e0b7339ee32c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 19bd830294d3bf5032bf1a69b51f2ab5824d7494
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85464903"
---
# <a name="idiastackwalkergetenumframes"></a>IDiaStackWalker::getEnumFrames
Načte enumerátor rámce zásobníku pro platformy x86.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT getEnumFrames( 
   IDiaStackWalkHelper*   pHelper,
   IDiaEnumStackFrames**  ppEnum
);
```

#### <a name="parameters"></a>Parametry
 `pHelper`

pro Pomocný objekt [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md) .

 `ppEnum`

mimo Vrátí objekt [IDiaEnumStackFrames](../../debugger/debug-interface-access/idiaenumstackframes.md) , který obsahuje seznam objektů [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md) .

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Chcete-li získat seznam rámců zásobníku na jakékoli jiné platformě, zavolejte metodu [IDiaStackWalker:: getEnumFrames2](../../debugger/debug-interface-access/idiastackwalker-getenumframes2.md) .

## <a name="see-also"></a>Viz také
- [IDiaStackWalker](../../debugger/debug-interface-access/idiastackwalker.md)
- [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)
- [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)
- [IDiaStackWalker::getEnumFrames2](../../debugger/debug-interface-access/idiastackwalker-getenumframes2.md)