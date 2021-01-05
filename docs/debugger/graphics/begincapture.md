---
title: BeginCapture | Microsoft Docs
description: Použijte metodu BeginCapture třídy VsgDbg k zahájení intervalu zachycení, který skončí EndCapture.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 9edbb52d-ee0b-4cc4-a382-972bcee067d3
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 931e7ab05442a429c0b9e6468d42aadca942c1ee
ms.sourcegitcommit: fcfd0fc7702a47c81832ea97cf721cca5173e930
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2020
ms.locfileid: "97727962"
---
# <a name="begincapture"></a>BeginCapture
Zahájí interval zachycení, který skončí `EndCapture` .

## <a name="syntax"></a>Syntax

```C++
void BeginCapture();
```

## <a name="remarks"></a>Poznámky
 Interval zachycení obvykle pokrývá podmnožinu jednoho rámce, například pokud chcete zachytit informace grafiky pouze o určitém typu volání draw. Pokud interval zachycení zahrnuje volání k dispozici, jsou zachyceny dva snímky informací o grafice. První rámec zahrnuje interval mezi voláním `BeginCapture` a voláním, které je k dispozici. druhý rámec zahrnuje interval mezi první událostí Direct3D po volání k přítomnosti a volání `EndCapture` .

 Chcete-li zachytit interval, je nutné připravit aplikaci pro zachycení a záznam informací o grafice – to znamená, že je [](init.md) nutné se `VsgDbg` před voláním nebo pomocí volání metody init přes instanci třídy `BeginCapture` `EndCapture` .

## <a name="see-also"></a>Viz také
- [EndCapture](endcapture.md)
- [CaptureCurrentFrame](capturecurrentframe.md)