---
title: 'DA0501: Průměr Spotřeby procesoru profilovaným Procesem. | Dokumentace Microsoftu'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.rules.DA0501
- vs.performance.DA0501
- vs.performance.501
ms.assetid: b01946b4-75e3-47d5-a1a1-cebfae66a3af
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: d9835ad1965d1fd9a31113117eeb07ed62fd8ec4
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74777460"
---
# <a name="da0501-average-cpu-consumption-by-the-process-being-profiled"></a>DA0501: Průměrná spotřeba procesoru podle procesu, který je profilován.

|||
|-|-|
|Id pravidla|DA501|
|Kategorie|Monitorování zdrojů|
|Metoda profilování|Všechny|
|Zpráva|Průměrná spotřeba procesoru profilovaným procesem|
|Typ pravidla|Informace|

 Při profilování pomocí vzorkování, .NET paměti nebo prostředků konfliktmetody, je nutné shromáždit alespoň 10 vzorků k aktivaci tohoto pravidla.

## <a name="rule-description"></a>Popis pravidla
 Tato zpráva hlásí procento času, po který byl procesor zaneprázdněn prováděním pokynů z aplikace. Vykázaná hodnota je průměr za všechny intervaly měření, ve kterých byl profilovaný proces aktivní. Hodnota může být větší než 100 % v počítači s více než jedním procesorem.

## <a name="how-to-use-rule-data"></a>Použití dat pravidla
 Pomocí hodnoty pravidla můžete porovnat výkon různých verzí nebo sestavení programu nebo porozumět výkonu aplikace v různých testovacích scénářích.
