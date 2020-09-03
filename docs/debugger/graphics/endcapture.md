---
title: EndCapture | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 06084c3b-e065-49b6-968e-d578762fb871
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c54e8b12f4d3b924b363f42cb098a1d528a8108b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72735980"
---
# <a name="endcapture"></a>EndCapture
Ukončí interval zachycení, který byl spuštěn s `BeginCapture` .

## <a name="syntax"></a>Syntax

```C++
void EndCapture();
```

## <a name="remarks"></a>Poznámky
 Interval zachycení obvykle pokrývá podmnožinu jednoho rámce, například pokud chcete zachytit informace grafiky pouze o určitém typu volání draw. Pokud interval zachycení zahrnuje volání k dispozici, jsou zachyceny dva snímky informací o grafice. První rámec zahrnuje interval mezi voláním `BeginCapture` a voláním, které je k dispozici. druhý rámec zahrnuje interval mezi první událostí Direct3D po volání k přítomnosti a volání `EndCapture` .

 Chcete-li zachytit interval, je nutné připravit aplikaci pro zachycení a záznam informací o grafice – to znamená, že je [Init](init.md) nutné se `VsgDbg` před voláním nebo pomocí volání metody init přes instanci třídy `BeginCapture` `EndCapture` .

## <a name="see-also"></a>Viz také
- [BeginCapture](begincapture.md)
- [CaptureCurrentFrame](capturecurrentframe.md)