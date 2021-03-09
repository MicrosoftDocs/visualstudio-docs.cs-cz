---
title: DA0501 – Průměrná spotřeba procesoru procesem profilace. | Dokumentace Microsoftu
description: Tato zpráva oznamuje procento času, po který procesor byl zaneprázdněn prováděním pokynů z aplikace.
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.performance.rules.DA0501
- vs.performance.DA0501
- vs.performance.501
ms.assetid: b01946b4-75e3-47d5-a1a1-cebfae66a3af
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 242a3ff10042a53997b17f662af145440df2e95a
ms.sourcegitcommit: 8590cf6b3351e82827fd21159beefef0c02bf162
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/08/2021
ms.locfileid: "102465826"
---
# <a name="da0501-average-cpu-consumption-by-the-process-being-profiled"></a>DA0501: Průměrná spotřeba procesoru procesem profilace.

|Položka|Hodnota|
|-|-|
|ID pravidla|DA501|
|Kategorie|Monitorování prostředků|
|Metoda profilace|Vše|
|Zpráva|Průměrná spotřeba procesoru profilovaným procesem|
|Typ pravidla|Informace|

 Když použijete profilování pomocí vzorkování, paměti .NET nebo způsobů kolizí prostředků, musíte pro aktivaci tohoto pravidla shromáždit aspoň 10 vzorků.

## <a name="rule-description"></a>Popis pravidla
 Tato zpráva oznamuje procento času, po který procesor byl zaneprázdněn prováděním pokynů z aplikace. Vykazovaná hodnota je průměr ve všech intervalech měření, v nichž byl proces profilace aktivní. Hodnota Value může být větší než 100% na počítači s více než jedním procesorem.

## <a name="how-to-use-rule-data"></a>Jak používat data pravidla
 Použijte hodnotu pravidla pro porovnání výkonu různých verzí nebo sestavení programu nebo pro pochopení výkonu aplikace v různých testovacích scénářích.
