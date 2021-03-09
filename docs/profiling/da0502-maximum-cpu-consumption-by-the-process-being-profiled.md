---
title: DA0502 – maximální využití procesoru procesem profilování | Microsoft Docs
description: Tato zpráva oznamuje maximální procento času, po který procesor zaneprázdněn prováděním pokynů z aplikace.
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.performance.rules.DA0502
- vs.performance.DA0502
- vs.performance.502
ms.assetid: 1ee53df5-b0dc-4265-9d4f-527830d08725
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 45071fb94b00be721e8c76c69dc5135a59f3a9b1
ms.sourcegitcommit: 8590cf6b3351e82827fd21159beefef0c02bf162
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/08/2021
ms.locfileid: "102465774"
---
# <a name="da0502-maximum-cpu-consumption-by-the-process-being-profiled"></a>DA0502: maximální spotřeba procesoru procesem profilace

|Položka|Hodnota|
|-|-|
|ID pravidla|DA0502|
|Kategorie|Monitorování prostředků|
|Metoda profilace|Vše|
|Zpráva|Toto pravidlo je pouze pro informace. Čítač procesu () \\ % času procesoru měří spotřebu procesoru procesu, který vytváříte profilování. Hodnota hlášené je maximální pozorována ve všech intervalech měření.|
|Typ pravidla|Informační|

 Když použijete profilování pomocí vzorkování, paměti .NET nebo způsobů kolizí prostředků, musíte pro aktivaci tohoto pravidla shromáždit aspoň 10 vzorků.

## <a name="rule-description"></a>Popis pravidla
 Tato zpráva oznamuje maximální procento času, po který procesor zaneprázdněn prováděním pokynů z aplikace. Vykazovaná hodnota je maximální hodnota hlášená mezi všemi měřicími intervaly, ve kterých je proces profilace aktivní. Procentuální hodnota může být větší než 100% na počítači s více než jedním procesorem.

## <a name="how-to-use-the-rule-data"></a>Jak používat data pravidla
 Použijte hodnotu pravidla pro porovnání výkonu různých verzí nebo sestavení programu nebo pro pochopení výkonu aplikace v rámci různých scénářů profilace.
