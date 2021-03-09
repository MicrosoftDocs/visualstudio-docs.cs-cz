---
title: DA0004 – vysoké využití procesoru | Microsoft Docs
description: Využití procesoru (CPU) bylo vysoké v datech profilace, která byla shromážděna pomocí metody instrumentace.
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.performance.rules.DAHighProcessorUsage
- vs.performance.rules.DA0004
- vs.performance.DA0004
- vs.performance.4
ms.assetid: 2c4fb569-929e-4f1d-8c50-b590ee371351
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: e80f9161e435a3b2b615aed700714a0c3cd0efa4
ms.sourcegitcommit: 8590cf6b3351e82827fd21159beefef0c02bf162
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/08/2021
ms.locfileid: "102469972"
---
# <a name="da0004-high-processor-usage"></a>DA0004: Vysoké využití procesoru

|Položka|Hodnota|
|-|-|
|ID pravidla|DA0004|
|Kategorie|Využití Nástroje pro profilaci|
|Metody profilace|Instrumentace<br /><br /> Vzorkování|
|Zpráva|Využití procesoru je konzistentně vyšší než 75%. Zvažte použití režimu vzorkování pro aplikace vázané na procesor.|
|Typ pravidla|Informace|

 Když použijete profilování pomocí vzorkování, paměti .NET nebo způsobů kolizí prostředků, musíte pro aktivaci tohoto pravidla shromáždit aspoň 10 vzorků.

## <a name="cause"></a>Příčina
 Využití procesoru (CPU) bylo vysoké v datech profilace, která byla shromážděna pomocí metody instrumentace. Při profilování aplikace vázané na procesor zvažte použití metody profilace vzorkování.

## <a name="rule-description"></a>Popis pravidla
 Během tohoto spuštění profilace byl procesor (nebo procesory) konzistentně zaneprázdněný. Vysoké využití procesoru může označovat aplikaci vázanou na procesor. Instrumentované profily nejsou nejúčinnějším způsobem, jak prozkoumat scénáře využití procesoru. Vzorkování je efektivnější, pokud vytváříte aplikace pro profilaci, které stráví spoustu času prováděním instrukcí v procesoru.

## <a name="how-to-fix-violations"></a>Jak opravit porušení
 Zvažte možnost profilování aplikace znovu pomocí metody vzorkování namísto metody instrumentace, pokud nepožadujete časování funkcí nebo máte větší zájem o porozumění vstupu/výstupu, než je problémová místa pro procesor.
