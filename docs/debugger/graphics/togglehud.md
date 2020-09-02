---
title: ToggleHUD | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 7261e01d-3c72-46ce-9fb3-5f33b2ddb901
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cb05bb6a424b5639e0ee98e96c80315c51081ace
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "62848475"
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