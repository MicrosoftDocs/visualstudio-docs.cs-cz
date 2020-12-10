---
title: ToggleHUD | Microsoft Docs
description: Pomocí metody ToggleHUD () VsgDbg můžete přepínat, jestli se při spuštění aplikace zobrazí hlavní zobrazení (HUD) diagnostiky grafiky.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 7261e01d-3c72-46ce-9fb3-5f33b2ddb901
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 60bee5a89be0fc1503595a36cfc48a692711d40a
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2020
ms.locfileid: "96996068"
---
# <a name="togglehud"></a>ToggleHUD
Zapíná nebo vypíná zobrazení diagnostiky grafiky *HUD* (zobrazení na záhlaví).

## <a name="syntax"></a>Syntaxe

```C++
void ToggleHUD();
```

## <a name="remarks"></a>Poznámky
 HUD diagnostiky grafiky se zobrazí v levém horním rohu aplikace, která je spuštěná v rámci diagnostiky grafiky. Zobrazuje běhové informace o aplikaci a o zachycení informací o obrázcích a zprávy, které jsou přidány voláním členské funkce [AddMessage](addmessage.md) .

 Chcete-li přepnout HUD, nemusíte aktivně zachytáváníovat grafické informace – to znamená, že je možné je přepínat prostřednictvím instance `VsgDbg` třídy, ale členská funkce [init](init.md) nemusí být volána jako první.