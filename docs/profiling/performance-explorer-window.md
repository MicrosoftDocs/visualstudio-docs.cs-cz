---
title: Prohlížeč výkonu okno | Microsoft Docs
description: Přečtěte si, jak Prohlížeč výkonu okno v integrovaném vývojovém prostředí sady Visual Studio umožňuje konfigurovat relace výkonu pomocí Nástroje pro profilaci sady Visual Studio.
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
ms.openlocfilehash: 06d2b7e2ad5d5df4022dc78aa06315545d56c0ee
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2021
ms.locfileid: "98722812"
---
# <a name="performance-explorer-window"></a>Okno Prohlížeč výkonu

Okno **prohlížeč výkonu** v integrovaném vývojovém prostředí sady Visual Studio umožňuje konfigurovat a spouštět relace výkonu pomocí nástroje pro profilaci sady Visual Studio. Pokud potřebujete okno otevřít, postupujte podle pokynů v [příručce pro začátečníky a profilování výkonu](../profiling/beginners-guide-to-cpu-sampling.md).

## <a name="performance-explorer-toolbar"></a>Panel nástrojů Prohlížeč výkonu

Na panelu nástrojů **prohlížeč výkonu** jsou k dispozici následující možnosti:

- **Spustit Průvodce výkonem** – zobrazí Průvodce výkonem, který přidá novou relaci výkonu do okna Prohlížeč výkonu.

- **Nová výkonnostní relace** – přidá do okna Prohlížeč výkonu prázdnou relaci výkonu.

- **Spustit** – seznam **spouštěcích** tlačítek umožňuje spustit cílovou aplikaci, která má okamžitě povolené profilování (**Spustit s profilací**), nebo s pozastaveným profilací (**Spustit s pozastaveným profilací**).

- **Metoda** – určuje, jestli je metoda profilování relace vzorkování nebo instrumentace.

- **Zastavit** – okamžitě ukončí cílovou aplikaci a Profiler.

- **Připojit nebo odpojit** – zobrazí dialogové okno **Připojit profiler k procesu** pro výběr běžícího procesu, ke kterému se má připojit Profiler.

## <a name="performance-explorer-window"></a>Okno Prohlížeč výkonu

Okno **prohlížeč výkonu** obsahuje ovládací prvek stromové struktury, který zobrazuje binární soubory a soubory sestav s daty jedné nebo více relací výkonu.

- **Název relace** – kořen ovládacího prvku stromu obsahuje název relace. Klikněte pravým tlačítkem myši na název relace a nastavte vlastnosti relace nebo spusťte cílovou aplikaci a Profiler.

- **Cíle** – zobrazí názvy binárních souborů, které se mají profilovat v relaci. Kliknutím pravým tlačítkem myši na možnost **cíle** můžete přidat nebo odebrat binární, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] projekt nebo Web. Klikněte pravým tlačítkem myši na název cíle a nastavte vlastnosti pro jednotlivé binární soubory.

- **Sestavy** – zobrazí názvy datových souborů profileru, které jsou generovány pro relaci. Kliknutím pravým tlačítkem myši na **sestavy** můžete přidat existující sestavu nebo porovnat dva datové soubory profileru. Kliknutím pravým tlačítkem myši na název sestavy otevřete, odeberete nebo vyexportujete datový soubor profileru.

## <a name="see-also"></a>Viz také

[Přehledy](../profiling/overviews-performance-tools.md) 
 [Konfigurace relací výkonu](../profiling/configuring-performance-sessions.md) 
 [Řízení shromažďování dat](../profiling/controlling-data-collection.md)
