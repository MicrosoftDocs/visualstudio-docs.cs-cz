---
title: BeginCapture | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 9edbb52d-ee0b-4cc4-a382-972bcee067d3
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9521288b27b1f9b11a2fdb8cbbd613f1a77f857d
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72736146"
---
# <a name="begincapture"></a>BeginCapture
Zahájí interval zachytávání, který skončí `EndCapture`.

## <a name="syntax"></a>Syntaxe

```C++
void BeginCapture();
```

## <a name="remarks"></a>Poznámky
 Interval zachycení obvykle pokrývá podmnožinu jednoho rámce, například pokud chcete zachytit informace grafiky pouze o určitém typu volání draw. Pokud interval zachycení zahrnuje volání k dispozici, jsou zachyceny dva snímky informací o grafice. První rámec zahrnuje interval mezi voláním `BeginCapture` a voláním, které je k dispozici; druhý rámec zahrnuje interval mezi první událostí Direct3D po volání a volání `EndCapture`.

 Chcete-li zachytit interval, je nutné připravit aplikaci pro zachycení a záznam informací o grafice – to znamená, že je nutné se před voláním `BeginCapture` nebo `EndCapture` volat [inicializaci](init.md) pomocí instance třídy `VsgDbg`.

## <a name="see-also"></a>Viz také:
- [EndCapture](endcapture.md)
- [CaptureCurrentFrame](capturecurrentframe.md)