---
title: DA0004 – vysoké využití procesoru | Microsoft Docs
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
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: e0ac8d8558ee73903898e920ed8174c73ea66c4d
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/30/2020
ms.locfileid: "85548171"
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
