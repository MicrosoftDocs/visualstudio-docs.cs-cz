---
title: ToggleHUD | Microsoft Docs
description: Pomocí metody ToggleHUD () VsgDbg můžete přepínat, jestli se při spuštění aplikace zobrazí hlavní zobrazení (HUD) diagnostiky grafiky.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 7261e01d-3c72-46ce-9fb3-5f33b2ddb901
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 809b33fe3339da56507d09fcf15ec51481b751e0
ms.sourcegitcommit: aeed3eb503d0b282537b073ebae8c028c4fef750
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/15/2021
ms.locfileid: "114232489"
---
# <a name="togglehud"></a>ToggleHUD
Zapíná nebo vypíná zobrazení diagnostiky grafiky *HUD* (zobrazení na záhlaví).

## <a name="syntax"></a>Syntax

```C++
void ToggleHUD();
```

## <a name="remarks"></a>Poznámky
 HUD diagnostiky grafiky se zobrazí v levém horním rohu aplikace, která je spuštěná v rámci diagnostiky grafiky. Zobrazuje běhové informace o aplikaci a o zachycení informací o obrázcích a zprávy, které jsou přidány voláním členské funkce [AddMessage](addmessage.md) .

 Chcete-li přepnout HUD, nemusíte aktivně zachytáváníovat grafické informace – to znamená, že je možné je přepínat prostřednictvím instance `VsgDbg` třídy, ale členská funkce [init](init.md) nemusí být volána jako první.