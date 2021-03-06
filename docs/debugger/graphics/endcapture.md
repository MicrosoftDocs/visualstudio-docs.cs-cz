---
title: EndCapture | Microsoft Docs
description: Použijte metodu EndCapture třídy VsgDbg k ukončení intervalu zachycení, který byl spuštěn s BeginCapture.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 06084c3b-e065-49b6-968e-d578762fb871
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 8b0820950980860465e5129211c77e48ff641bdf
ms.sourcegitcommit: aeed3eb503d0b282537b073ebae8c028c4fef750
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/15/2021
ms.locfileid: "114232671"
---
# <a name="endcapture"></a>EndCapture
Ukončí interval zachycení, který byl spuštěn s `BeginCapture` .

## <a name="syntax"></a>Syntax

```C++
void EndCapture();
```

## <a name="remarks"></a>Poznámky
 Interval zachycení obvykle pokrývá podmnožinu jednoho rámce, například pokud chcete zachytit informace grafiky pouze o určitém typu volání draw. Pokud interval zachycení zahrnuje volání k dispozici, jsou zachyceny dva snímky informací o grafice. První rámec zahrnuje interval mezi voláním `BeginCapture` a voláním, které je k dispozici. druhý rámec zahrnuje interval mezi první událostí Direct3D po volání k přítomnosti a volání `EndCapture` .

 Chcete-li zachytit interval, je nutné připravit aplikaci pro zachycení a záznam informací o grafice – to znamená, že je [](init.md) nutné se `VsgDbg` před voláním nebo pomocí volání metody init přes instanci třídy `BeginCapture` `EndCapture` .

## <a name="see-also"></a>Viz také
- [BeginCapture](begincapture.md)
- [CaptureCurrentFrame](capturecurrentframe.md)