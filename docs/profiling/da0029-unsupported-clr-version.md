---
title: 'DA0029: Nepodporovaná verze CLR | Dokumenty společnosti Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.29
- vs.performance.rules.DA0029
helpviewer_keywords:
- vs.performance.29
- vs.performance.DA0029
- vs.performance.rules.DA0029
ms.assetid: 76247259-c6f3-44c4-b3f9-d8dac16b5e0d
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: dbc0bfcdb49557e56711b60dca11977a3504d907
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74777512"
---
# <a name="da0029-unsupported-clr-version"></a>DA0029: Nepodporovaná verze CLR

|||
|-|-|
|Id pravidla|DA0029 řekl:|
|Kategorie|Využití nástrojů profilování|
|Metoda profilování|Profilování z příkazového řádku|
|Zpráva|Během kolekce byla zjištěna nepodporovaná verze CLR. Spravované symboly nemusí vyřešit správně.|
|Typ pravidla|Informace.|

## <a name="cause"></a>Příčina
 Pokoušíte se profilovat aplikaci, [!INCLUDE[net_v11_long](../profiling/includes/net_v11_long_md.md)] která používá to, co není podporováno nástroji profilování.

## <a name="rule-description"></a>Popis pravidla
 K tomuto upozornění dochází, protože profilovací nástroje nebudou moci vyřešit symboly spravovaného kódu spuštěnév aplikaci. Nástroje profilování nelze vyřešit symboly spravovaného [!INCLUDE[net_v11_long](../profiling/includes/net_v11_long_md.md)]kódu pro aplikace, které jsou spuštěny .

## <a name="how-to-fix-violations"></a>Jak opravit porušení
 Žádné.
