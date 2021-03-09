---
title: DA0003 – mnoho ukázek jádra | Microsoft Docs
description: Významný podíl ukázek zásobníku volání, které byly shromážděny pro aplikaci, byly spuštěny v režimu jádra.
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.performance.rules.DA0003
- vs.performance.DA0003
- vs.performance.3
- vs.performance.rules.DAManyKernelSamples
ms.assetid: c1f46f77-eb95-42e5-b340-d86bc9de41b4
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 1b93bbbcb2026ad6f7ef0d25dc359eb211a6c85f
ms.sourcegitcommit: 8590cf6b3351e82827fd21159beefef0c02bf162
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/08/2021
ms.locfileid: "102469946"
---
# <a name="da0003-many-kernel-samples"></a>DA0003: Velký počet vzorků jádra

|Položka|Hodnota|
|-|-|
|ID pravidla|DA0003|
|Kategorie|Využití Nástroje pro profilaci|
|Metody profilace|Vzorkování|
|Zpráva|V režimu jádra máte vysokou část ukázek. To může znamenat velký objem vstupně-výstupních aktivit nebo vysoké míry přepínání kontextu. Zvažte možnost profilování aplikace znovu pomocí režimu instrumentace.|
|Typ pravidla|Informace|

## <a name="cause"></a>Příčina
 Významný podíl ukázek zásobníku volání, které byly shromážděny pro aplikaci, byly spuštěny v režimu jádra. Zvažte profilaci aplikace pomocí jiné metody profilace.

## <a name="rule-description"></a>Popis pravidla
 V systému Windows lze kód spustit buď v režimu jádra, nebo v uživatelském režimu. (Režim jádra se označuje taky jako privilegovaný režim.) V režimu jádra je spuštěn pouze systémový kód nižší úrovně, jako je například ovladač zařízení. Aplikace v uživatelském režimu se může převést do režimu jádra, aby prováděla vstupně-výstupní operace, aby se čekalo na prvky synchronizace vlákna nebo procesu, nebo do systémových volání.

 Vzorkování je nejúčinnější při profilování aplikací, které tráví většinu času při práci v uživatelském režimu. Počet vzorků, které byly shromážděny při spuštění aplikace v režimu jádra, může označovat časté vstupně-výstupní operace nebo může indikovat, že dojde k přepnutí kontextu. Ani jednu z těchto operací nelze prozkoumat pomocí metody vzorkování. Pokud jsou odebírány příliš mnoho vzorků režimu jádra, data vzorkování nemusí obsahovat dostatek vzorků uživatelského režimu, aby byly statisticky důležité.

## <a name="how-to-fix-violations"></a>Jak opravit porušení
 Zvažte možnost profilování aplikace znovu pomocí jedné z následujících možností:

- Profilujte pomocí metody instrumentace.

- Zvyšte vzorkovací frekvenci a pokuste se shromáždit další ukázky v uživatelském režimu.
