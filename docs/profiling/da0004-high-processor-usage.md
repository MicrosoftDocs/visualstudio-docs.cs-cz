---
title: 'DA0004: Vysoká využití procesoru | Dokumenty společnosti Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: b324d26d21920bae9f03f909b2eab0c1ce7ab419
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74777722"
---
# <a name="da0004-high-processor-usage"></a>DA0004: Vysoké využití procesoru

|||
|-|-|
|Id pravidla|DA0004 řekl:|
|Kategorie|Využití nástrojů profilování|
|Metody profilování|Instrumentace<br /><br /> Vzorkování|
|Zpráva|Využití procesoru je trvale vyšší než 75 %. Zvažte použití režimu vzorkování pro aplikace vázané na procesor.|
|Typ pravidla|Informace|

 Při profilování pomocí vzorkování, .NET paměti nebo prostředků konfliktmetody, je nutné shromáždit alespoň 10 vzorků k aktivaci tohoto pravidla.

## <a name="cause"></a>Příčina
 Využití procesoru (CPU) bylo vysoké v profilování dat, která byla shromážděna pomocí metody instrumentace. Zvažte použití metody profilování vzorkování při profilování aplikace vázané na procesor.

## <a name="rule-description"></a>Popis pravidla
 Během tohoto spuštění profilování byl procesor (nebo procesory) konzistentně zaneprázdněn. Vysoké využití procesoru může indikovat aplikaci vázanou na procesor. Instrumentované profily nejsou nejúčinnější způsob, jak prozkoumat scénáře využití procesoru. Vzorkování je efektivnější, když profilování aplikací, které tráví většinu svého času provádění mantinelu na procesoru.

## <a name="how-to-fix-violations"></a>Jak opravit porušení
 Zvažte profilování aplikace znovu pomocí metody vzorkování namísto metody instrumentace, pokud nepožadujete časování funkcí nebo se více nezajímáte o pochopení vstupu a výstupu než kritických míst procesoru.
