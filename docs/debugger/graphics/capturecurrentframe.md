---
title: CaptureCurrentFrame | Microsoft Docs
description: Pomocí metody CaptureCurrentFrame třídy VsgDbg Zachyťte zbytek aktuálního rámce do souboru protokolu grafiky.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 4509311d-6fe2-4b65-9b4a-ff0522585d6a
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 17c917c6c23dff41a5692e95588ce757a8d08293
ms.sourcegitcommit: aeed3eb503d0b282537b073ebae8c028c4fef750
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/15/2021
ms.locfileid: "114232724"
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