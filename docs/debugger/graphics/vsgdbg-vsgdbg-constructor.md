---
description: Vytvoří instanci třídy VsgDbg s nebo bez přípravy komponenty v aplikaci diagnostiky grafiky pro aktivní zachycení a zaznamenání informací o grafice na základě zadaného logického parametru.
title: 'VsgDbg:: VsgDbg (konstruktor) | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 670651e6-5e79-4845-b0c2-671beb7055a8
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: e3693301aef27e01f2d12fa954f94fcc55fb8dea
ms.sourcegitcommit: aeed3eb503d0b282537b073ebae8c028c4fef750
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/15/2021
ms.locfileid: "114232424"
---
# <a name="vsgdbgvsgdbg-constructor"></a>VsgDbg::VsgDbg (konstruktor)
Vytvoří instanci `VsgDbg` třídy s nebo bez přípravy komponenty v aplikaci diagnostiky grafiky pro aktivní zachycení a zaznamenání informací o grafice na základě zadaného logického parametru.

## <a name="syntax"></a>Syntaxe

```C++
VsgDbg(
  bDefaultInit
);
```

#### <a name="parameters"></a>Parametry
 `bDefaultInit``true`Chcete-li určit, že komponenta v aplikaci diagnostiky grafiky je připravena k aktivnímu zachycení a zaznamenání informací o grafice; `false` Chcete-li určit, že aplikace by neměla být připravena k aktivnímu zachytávání a záznamu grafiky v tuto chvíli.

## <a name="remarks"></a>Poznámky
 Při volání konstruktoru s `bDefaultInit` nastavením na je `true` název souboru protokolu grafiky určen tak, jak `DONT_SAVE_VSGLOG_TO_TEMP` `VSG_DEFAULT_RUN_FILENAME` jsou definovány symboly preprocesoru a před tím, než `vsgcapture.h` je součástí vaší aplikace.

 Při volání konstruktoru s `bDefaultInit` nastavením na je `false` možné připravit komponentu v aplikaci diagnostiky grafiky na aktivní zachycování a zaznamenávání informací grafiky na pozdější dobu voláním `Init` funkce.

## <a name="see-also"></a>Viz také
- [VsgDbg::~VsgDbg (destruktor)](vsgdbg-tilde-vsgdbg-destructor.md)
- [For](init.md)
- [DONT_SAVE_VSGLOG_TO_TEMP](dont-save-vsglog-to-temp.md)
- [VSG_DEFAULT_RUN_FILENAME](vsg-default-run-filename.md)
