---
title: 'DA0502: Maximální spotřeba procesoru v profilu procesu | Dokumenty společnosti Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.rules.DA0502
- vs.performance.DA0502
- vs.performance.502
ms.assetid: 1ee53df5-b0dc-4265-9d4f-527830d08725
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 5c3cb5169d078ba1242bf898ba93e31a7a488bb8
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779334"
---
# <a name="da0502-maximum-cpu-consumption-by-the-process-being-profiled"></a>DA0502: Maximální spotřeba procesoru v profilu procesu

|||
|-|-|
|Id pravidla|DA0502|
|Kategorie|Monitorování zdrojů|
|Metoda profilování|Všechny|
|Zpráva|Toto pravidlo je pouze pro informaci. Čítač\\Času procesoru (Proces() % měří spotřebu procesoru procesu, který profilujete. Uvedená hodnota je maximální pozorovaná ve všech intervalech měření.|
|Typ pravidla|Informační|

 Při profilování pomocí vzorkování, .NET paměti nebo prostředků konfliktmetody, je nutné shromáždit alespoň 10 vzorků k aktivaci tohoto pravidla.

## <a name="rule-description"></a>Popis pravidla
 Tato zpráva hlásí maximální procento času, po které byl procesor zaneprázdněn prováděním pokynů z aplikace. Vykázaná hodnota je maximální hodnota vykázaná mezi všemi intervaly měření, ve kterých byl profilovaný proces aktivní. Procento může být větší než 100 % v počítači s více než jedním procesorem.

## <a name="how-to-use-the-rule-data"></a>Jak používat data pravidla
 Pomocí hodnoty pravidla můžete porovnat výkon různých verzí nebo sestavení programu nebo porozumět výkonu aplikace v různých scénářích profilování.
