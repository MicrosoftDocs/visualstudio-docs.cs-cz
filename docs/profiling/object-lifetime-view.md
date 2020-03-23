---
title: Zobrazení životnosti objektu | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.view.objectlifetime
helpviewer_keywords:
- lifetime, objects
- Objects Lifetime view
- profiling tools reports, Lifetime view
- performance reports, objects lifetime view
- profiling tools, Lifetime view
ms.assetid: d0501fdd-4b3a-4e74-b6ac-51d950a2e15b
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: d4ea486930d0ea9f266b4ee57b69a50f7c570651
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74772621"
---
# <a name="object-lifetime-view"></a>Zobrazení doby života objektu
Zobrazení Životnost objektu je k dispozici, pokud je na stránkách vlastností **relace výkonu** zaškrtnuto také shromažďování **dat životnosti objektu .NET.**

 Systém uvolňování paměti rozhraní .NET Framework spravuje přidělení a uvolnění paměti pro vaši aplikaci. Chcete-li optimalizovat výkon systému uvolňování paměti, je spravovaná halda rozdělena do tří generací: 0, 1 a 2. Uvolňování systému runtime ukládá nové objekty v generaci 0. Objekty, které přežijí kolekce jsou povýšen a uloženy v generacích 1 a 2.

 Systém uvolňování paměti uvolňuje paměť zrušením přidělení celé generace objektů. U objektů, které byly vytvořeny profilovanou aplikací, zobrazí zobrazení Životnost objektu počet a velikost objektů a generování, ve kterém jsou regenerované.

## <a name="general"></a>Obecné

|Sloupec|Popis|
|------------|-----------------|
|**Název třídy**|Název třídy přiděleného typu.|
|**ID procesu**|ID procesu profilování spustit.|
|**Název procesu**|Název procesu|
|**Název modulu**|Název modulu, který obsahuje funkci.|
|**Cesta modulu**|Cesta modulu, který obsahuje funkci.|

## <a name="instance-data"></a>Data instance
 Data instance označuje počet objektů typu, které byly vytvořeny v profilování spustit a generování, ve kterém byly uvolněny objekty systémem uvolňování paměti.

|Sloupec|Popis|
|------------|-----------------|
|**Instance**|Počet přidělení objektů tohoto typu.|
|**Celkový počet instancí %**|Procento z celkového počtu přidělení, které byly provedeny v profilování spustit.|
|**Gen 0 Instance Shromážděné**|Počet instancí typu, které byly uvolněny v generaci 0 algoritmu uvolňování paměti.|
|**Gen 1 Instance Shromážděné**|Počet instancí typu, které byly uvolněny v generaci 1 algoritmu uvolňování paměti.|
|**Gen 2 Instance Shromážděné**|Počet instancí typu, které byly uvolněny v generaci 2 algoritmu uvolňování paměti.|
|**Instance Alive na konci**|Počet instancí typu, které nebyly deallocated až do konce profilování spustit.|

## <a name="size-byte-data"></a>Data o velikosti (bajtu)
 Velikost (bajt) data označuje velikost objektů typu, které byly vytvořeny v profilování spustit a množství paměti, která byla vyvolána v každé generaci, ve kterém byly objekty přiděleny.

|Sloupec|Popis|
|------------|-----------------|
|**Celkový počet přidělených bajtů**|Celkový počet bajtů pro všechny instance typu.|
|**Celkový počet bajtů %**|Procento z celkového počtu přidělených bajtů v profilování spustit, které byly přiděleny pro instance tohoto typu.|
|**Gen 0 bajtů shromážděných**|Velikost instancí typu, které byly uvolněny v generaci 0 algoritmu uvolňování paměti.|
|**Gen 1 Bajty Shromážděné**|Velikost instancí typu, které byly uvolněny v generaci 1 algoritmu uvolňování paměti.|
|**Gen 2 bajty sebrané**|Velikost instancí typu, které byly uvolněny v generaci 2 algoritmu uvolňování paměti.|

## <a name="large-object-heap-data"></a>Data haldy velkých objektů
 Alokátor paměti .NET spravuje velmi velké objekty v umístění, které je oddělené od standardní spravované haldy. Data haldy velkých objektů označují počet a velikost objektů typu, které byly spravovány v tomto umístění.

|Sloupec|Popis|
|------------|-----------------|
|**Instance hald velkých objektů se branži**|Počet instancí tohoto typu, které byly umístěny v haldě velkého objektu a které byly shromážděny v profilování spustit.|
|**Počet sebraných hald velkých objektů**|Velikost v bajtů instancí tohoto typu, které byly umístěny v haldě velkého objektu a které byly shromážděny v profilování spustit.|

## <a name="see-also"></a>Viz také
- [Zobrazení dat paměti .NET](../profiling/dotnet-memory-data-views.md)
