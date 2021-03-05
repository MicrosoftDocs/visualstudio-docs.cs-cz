---
description: Načte enumerátor rámce zásobníku pro platformy x86.
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f4dc2230bdbbdb626bece7ecec39f2c2c2578ab3
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102147350"
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
