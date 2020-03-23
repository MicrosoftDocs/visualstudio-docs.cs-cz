---
title: 'DA0003: Mnoho vzorků jádra | Dokumenty společnosti Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.rules.DA0003
- vs.performance.DA0003
- vs.performance.3
- vs.performance.rules.DAManyKernelSamples
ms.assetid: c1f46f77-eb95-42e5-b340-d86bc9de41b4
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 69cd81943641e4e0585a67127c70d35a601a5396
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74777735"
---
# <a name="da0003-many-kernel-samples"></a>DA0003: Vysoký počet ukázek jádra

|||
|-|-|
|Id pravidla|DA0003 řekl:|
|Kategorie|Využití nástrojů profilování|
|Metody profilování|Vzorkování|
|Zpráva|Máte vysoký podíl vzorků v režimu jádra. To může znamenat vysoký objem vstupně-va aktivity nebo vysokou míru přepínání kontextu. Zvažte profilování aplikace znovu pomocí režimu instrumentace.|
|Typ pravidla|Informace|

## <a name="cause"></a>Příčina
 Významná část ukázek zásobníku volání, které byly shromážděny pro aplikaci byly spuštěny v režimu jádra. Zvažte profilování aplikace pomocí jiné metody profilování.

## <a name="rule-description"></a>Popis pravidla
 V systému Windows může být kód spuštěn v režimu jádra nebo v uživatelském režimu. (Režim jádra se také nazývá privilegovaný režim.) V režimu jádra se spouští pouze systémový kód nižší úrovně, například ovladač zařízení. Aplikace v uživatelském režimu může přejít do režimu jádra k provádění vstupně-vaoperací, čekat na základní prvky synchronizace vláken nebo procesů nebo provádět systémová volání.

 Vzorkování je nejúčinnější, pokud profilujete aplikace, které tráví většinu svého času prací v uživatelském režimu. Počet vzorků, které byly shromážděny při provádění aplikace v režimu jádra, může indikovat časté vstupně-vanové operace nebo může znamenat, že dochází k přepnutí kontextu. Ani jedna z těchto operací nemůže být zkoumána metodou odběru vzorků. Pokud je odebráno příliš mnoho vzorků režimu jádra, vzorkovací data nemusí obsahovat dostatek vzorků uživatelského režimu, aby byla statisticky významná.

## <a name="how-to-fix-violations"></a>Jak opravit porušení
 Zvažte profilování aplikace znovu pomocí jedné z následujících možností:

- profilem pomocí metody instrumentace.

- Zvyšte vzorkovací frekvenci a pokuste se shromáždit více vzorků v uživatelském režimu.
