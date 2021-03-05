---
description: Načte enumerátor rámce zásobníku pro konkrétní typ platformy.
title: 'IDiaStackWalker:: getEnumFrames2 | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalker2::getEnumFrames2 method
ms.assetid: 73196d3f-112c-4b3a-997b-7c6b815d4afc
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 71af6f8c78f6f4ac0f6008db8a9ecd4ba72df07e
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102147343"
---
# <a name="idiastackwalkergetenumframes2"></a>IDiaStackWalker::getEnumFrames2
Načte enumerátor rámce zásobníku pro konkrétní typ platformy.

## <a name="syntax"></a>Syntaxe

```C++

      HRESULT getEnumFrames2( 
   enum  CV_CPU_TYPE_e    cpuid,
   IDiaStackWalkHelper*   pHelper,
   IDiaEnumStackFrames**  ppEnum
);
```

#### <a name="parameters"></a>Parametry
 `cpuid`

pro Hodnota z výčtu [výčtu CV_CPU_TYPE_e](../../debugger/debug-interface-access/cv-cpu-type-e.md) , která určuje typ platformy.

 `pHelper`

pro Pomocný objekt [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md) .

 `ppEnum`

mimo Vrátí objekt [IDiaEnumStackFrames](../../debugger/debug-interface-access/idiaenumstackframes.md) obsahující seznam objektů [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md) .

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Chcete-li získat seznam rámců zásobníku jenom pro platformu x86, zavolejte metodu [IDiaStackWalker:: getEnumFrames](../../debugger/debug-interface-access/idiastackwalker-getenumframes.md) .

## <a name="see-also"></a>Viz také
- [IDiaStackWalker](../../debugger/debug-interface-access/idiastackwalker.md)
- [CV_CPU_TYPE_e – výčet](../../debugger/debug-interface-access/cv-cpu-type-e.md)
- [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)
- [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)
- [IDiaStackWalker::getEnumFrames](../../debugger/debug-interface-access/idiastackwalker-getenumframes.md)
