---
title: DA0029 – Nepodporovaná verze CLR | Microsoft Docs
description: Pokoušíte se profilovat aplikaci, která používá .NET Framework 1,1, kterou Nástroje pro profilaci nepodporuje.
ms.date: 11/04/2016
ms.topic: reference
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
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: b3f5e5129bed479273e141af70121d5a344972e2
ms.sourcegitcommit: 8590cf6b3351e82827fd21159beefef0c02bf162
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/08/2021
ms.locfileid: "102465839"
---
# <a name="da0029-unsupported-clr-version"></a>DA0029: Nepodporovaná verze CLR

|Položka|Hodnota|
|-|-|
|ID pravidla|DA0029|
|Kategorie|Využití Nástroje pro profilaci|
|Metoda profilace|Profilace z příkazového řádku|
|Zpráva|Během shromažďování byla zjištěna nepodporovaná verze CLR. Spravované symboly se nemusí správně přeložit.|
|Typ pravidla|Informace.|

## <a name="cause"></a>Příčina
 Pokoušíte se profilovat aplikaci, která používá rozhraní [!INCLUDE[net_v11_long](../profiling/includes/net_v11_long_md.md)] , které není nástroje pro profilaci podporováno.

## <a name="rule-description"></a>Popis pravidla
 K tomuto upozornění dochází, protože nástroje pro profilaci nebudou moci přeložit symboly pro spravovaný kód spuštěný v aplikaci. Nástroje pro profilaci nemůžou přeložit spravované symboly kódu pro aplikace, na kterých běží [!INCLUDE[net_v11_long](../profiling/includes/net_v11_long_md.md)] .

## <a name="how-to-fix-violations"></a>Jak opravit porušení
 Žádné
