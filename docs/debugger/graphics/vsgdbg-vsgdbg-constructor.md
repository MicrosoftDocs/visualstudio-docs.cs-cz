---
title: 'VsgDbg:: VsgDbg (konstruktor) | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 670651e6-5e79-4845-b0c2-671beb7055a8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ae94a7cb9572a0975dc1c3717275c384c2e45978
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72734751"
---
# <a name="vsgdbgvsgdbg-constructor"></a>VsgDbg::VsgDbg (konstruktor)
Vytvoří instanci třídy `VsgDbg` s nebo bez přípravy komponenty v aplikaci diagnostiky grafiky pro aktivní zachycení a zaznamenání informací o grafice na základě zadaného logického parametru.

## <a name="syntax"></a>Syntaxe

```C++
VsgDbg(
  bDefaultInit
);
```

#### <a name="parameters"></a>Parametry
 `bDefaultInit` `true` určit, že se komponenta v aplikaci diagnostiky grafiky připravuje na aktivní zachycování a zaznamenávání informací grafiky.  `false` určit, že by se aplikace neměla připravovat k aktivnímu zachytávání a zaznamenání informací o grafice v tuto chvíli.

## <a name="remarks"></a>Poznámky
 Když je konstruktor volán s `bDefaultInit` nastavenou na `true`, název souboru protokolu grafiky je určen tak, jak jsou definovány `DONT_SAVE_VSGLOG_TO_TEMP` a `VSG_DEFAULT_RUN_FILENAME` symboly preprocesoru, než je ve vaší aplikaci obsažena `vsgcapture.h`.

 Když je konstruktor volán s `bDefaultInit` nastavenou na `false`, může být komponenta v aplikaci diagnostiky grafiky připravena k aktivnímu zachycení a zaznamenání informací grafiky na pozdější dobu voláním funkce `Init`.

## <a name="see-also"></a>Viz také:
- [VsgDbg::~VsgDbg (destruktor)](vsgdbg-tilde-vsgdbg-destructor.md)
- [Init](init.md)
- [DONT_SAVE_VSGLOG_TO_TEMP](dont-save-vsglog-to-temp.md)
- [VSG_DEFAULT_RUN_FILENAME](vsg-default-run-filename.md)