---
title: BeginCapture – | Microsoft Docs
description: Pomocí metody BeginCapture třídy VsgDbg zahajte interval zachytávání, který končí na EndCapture.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 9edbb52d-ee0b-4cc4-a382-972bcee067d3
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: c9fc81bdd058d3a8c1dbe26bbe944bcb0e354ac7
ms.sourcegitcommit: aeed3eb503d0b282537b073ebae8c028c4fef750
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/15/2021
ms.locfileid: "114232731"
---
# <a name="begincapture"></a>BeginCapture
Začíná interval zachycení, který bude končovat `EndCapture` na .

## <a name="syntax"></a>Syntax

```C++
void BeginCapture();
```

## <a name="remarks"></a>Poznámky
 Interval zachycení obvykle zahrnuje podmnožinu jednoho snímku, například když chcete zachytit informace grafiky pouze o určitém druhu volání kreslení. Pokud interval zachycení zasáhuje volání do současnosti, jsou zachyceny dva snímky informací grafiky. První snímek zahrnuje interval mezi voláním metody a voláním, které se má prezentovat; druhý snímek zahrnuje interval mezi první událostí Direct3D po volání metody , která se prezentuje, a `BeginCapture` voláním `EndCapture` metody .

 Pokud chcete zachytit interval, je nutné připravit aplikaci k zaznamenání a zaznamenání informací grafiky – to znamená, že jste před voláním nebo museli volat [init](init.md) prostřednictvím instance `VsgDbg` třídy `BeginCapture` `EndCapture` .

## <a name="see-also"></a>Viz také
- [EndCapture](endcapture.md)
- [CaptureCurrentFrame](capturecurrentframe.md)