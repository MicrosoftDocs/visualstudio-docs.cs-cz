---
title: Okno Průzkumníka výkonu | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performanceexplorer
- vs.performance.explorer
helpviewer_keywords:
- performance tools, Performance Explorer
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: a365892f606da90c608e43b7ccce73b902ec0e98
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74772436"
---
# <a name="performance-explorer-window"></a>Okno Prohlížeč výkonu

Okno **Průzkumník výkonu** v rozhraní IDE sady Visual Studio umožňuje konfigurovat a spouštět relace výkonu pomocí nástrojů pro profilování sady Visual Studio. Pokud potřebujete otevřít okno, postupujte podle pokynů v [příručce Pro začátečníky k profilování výkonu](../profiling/beginners-guide-to-cpu-sampling.md).

## <a name="performance-explorer-toolbar"></a>Panel nástrojů Průzkumník výkonu

Na panelu nástrojů **Průzkumníka výkonu** jsou k dispozici následující možnosti:

- **Průvodce spuštěním výkonu** – zobrazí Průvodce výkonem a přidá do okna Průzkumníka výkonu novou relaci výkonu.

- **Nová relace výkonu** – přidá prázdnou relaci výkonu do okna Průzkumníkvýkonu.

- **Spustit** - Seznam příkazů **Spustit** umožňuje spustit cílovou aplikaci, která má profilování okamžitě povoleno **(Spuštění s profilováním)** nebo s pozastaveným profilováním **(Spuštění s pozastaveným profilováním).**

- **Metoda** - Určuje, zda je metoda profilování relace vzorkování nebo instrumentace.

- **Stop** - Okamžitě ukončí cílovou aplikaci a profiler.

- **Připojit/odpojit** - Zobrazí dialogové okno **Připojit profiler ke zpracování** a vybrat tak spuštěný proces, ke kterému chcete připojit profiler.

## <a name="performance-explorer-window"></a>Okno Prohlížeč výkonu

Okno **Průzkumník výkonu** obsahuje ovládací prvek stromu, který zobrazuje binární soubory a datové soubory sestavy jedné nebo více relací výkonu.

- **Název relace** - Kořen ovládacího prvku stromu obsahuje název relace. Klepněte pravým tlačítkem myši na název relace a nastavte vlastnosti relace nebo spusťte cílovou aplikaci a profiler.

- **Cíle** – Zobrazí názvy binárních souborů, které mají být profilovány v relaci. Chcete-li přidat nebo odebrat [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] binární soubor, projekt nebo web, klepněte pravým tlačítkem myši na **cíl.** Chcete-li nastavit vlastnosti jednotlivých binárních objektů, klepněte pravým tlačítkem myši na cílový název.

- **Sestavy** – zobrazí názvy datových souborů profileru, které jsou generovány pro relaci. Kliknutím pravým tlačítkem myši na **Sestavy** přidáte existující sestavu nebo porovnáte dva datové soubory profileru. Kliknutím pravým tlačítkem myši na název sestavy otevřete, odeberete nebo exportujete datový soubor profileru.

## <a name="see-also"></a>Viz také

[Přehledy](../profiling/overviews-performance-tools.md)
[Konfigurace relací](../profiling/configuring-performance-sessions.md)
výkonu[ovládajících shromažďování dat](../profiling/controlling-data-collection.md)
