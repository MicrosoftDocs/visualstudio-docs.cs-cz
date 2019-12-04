---
title: 'DA0029: Nepodporovaná verze CLR | Microsoft Docs'
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
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74777512"
---
# <a name="da0029-unsupported-clr-version"></a>DA0029: Nepodporovaná verze CLR

|||
|-|-|
|Id pravidla|DA0029|
|Kategorie|Využití Nástroje pro profilaci|
|Metoda profilace|Profilace z příkazového řádku|
|Zpráva|Během shromažďování byla zjištěna nepodporovaná verze CLR. Spravované symboly se nemusí správně přeložit.|
|Typ pravidla|Informace.|

## <a name="cause"></a>příčina
 Pokoušíte se profilovat aplikaci, která používá [!INCLUDE[net_v11_long](../profiling/includes/net_v11_long_md.md)], kterou Nástroje pro profilaci nepodporuje.

## <a name="rule-description"></a>Popis pravidla
 K tomuto upozornění dochází, protože nástroje pro profilaci nebudou moci přeložit symboly pro spravovaný kód spuštěný v aplikaci. Nástroje pro profilaci nemůžou přeložit spravované symboly kódu pro aplikace, na kterých běží [!INCLUDE[net_v11_long](../profiling/includes/net_v11_long_md.md)].

## <a name="how-to-fix-violations"></a>Jak opravit porušení
 Žádné
