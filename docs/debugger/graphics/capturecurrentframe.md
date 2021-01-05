---
title: CaptureCurrentFrame | Microsoft Docs
description: Pomocí metody CaptureCurrentFrame třídy VsgDbg Zachyťte zbytek aktuálního rámce do souboru protokolu grafiky.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 4509311d-6fe2-4b65-9b4a-ff0522585d6a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 793d86ac7d23fa209560222415dce50f4e5ac508
ms.sourcegitcommit: fcfd0fc7702a47c81832ea97cf721cca5173e930
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2020
ms.locfileid: "97727941"
---
# <a name="capturecurrentframe"></a>CaptureCurrentFrame
Zachycuje zbytek aktuálního rámce do souboru protokolu grafiky.

## <a name="syntax"></a>Syntax

```C++
void CaptureCurrentFrame();
```

## <a name="remarks"></a>Poznámky
 Pokud v současné době probíhá jiné zachycení – například zachytávání, který byl spuštěn `BeginCapture` funkcí, pak toto zachycení je dokončeno a zaznamenáno do protokolu grafiky jako samostatný rámec. Ihned poté Diagnostika grafiky zahájí zachycení zbývajícího aktuálního rámce, který je také zaznamenán jako samostatný rámec. Konec aktuálního rámce je označen voláním k dispozici.

 Chcete-li zachytit snímek, je nutné připravit aplikaci pro zachycení a záznam informací o grafice – to znamená, že před voláním je nutné se před voláním volat [init](init.md) pomocí instance `VsgDbg` třídy `CaptureCurrentFrame` .

## <a name="see-also"></a>Viz také
- [For](init.md)
- [BeginCapture](begincapture.md)