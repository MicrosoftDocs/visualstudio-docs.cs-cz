---
title: EndCapture | Microsoft Docs
description: Použijte metodu EndCapture třídy VsgDbg k ukončení intervalu zachycení, který byl spuštěn s BeginCapture.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 06084c3b-e065-49b6-968e-d578762fb871
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6bbdc8f2dc4fa3ad25be8674b9a46bf02179aa1d
ms.sourcegitcommit: fcfd0fc7702a47c81832ea97cf721cca5173e930
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2020
ms.locfileid: "97727828"
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