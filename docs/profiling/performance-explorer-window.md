---
title: Okno Prohlížeč výkonu | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performanceexplorer
- vs.performance.explorer
helpviewer_keywords:
- performance tools, Performance Explorer
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f27d1436aaeb0ec75876edf9119dff93f7539483
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/19/2018
ms.locfileid: "31582108"
---
# <a name="performance-explorer-window"></a>Okno Prohlížeč výkonu

**Prohlížeč výkonu** okna v prostředí Visual Studio IDE umožňuje nakonfigurovat a spustit výkonnostních relací s použitím sady Visual Studio profilace Tools.

## <a name="performance-explorer-toolbar"></a>Panel nástrojů výkonu aplikace Explorer

Tyto možnosti jsou dostupné na **prohlížeč výkonu** nástrojů:

- **Spustí Průvodce výkonu** -zobrazí výkonu průvodce a přidejte novou relaci výkonu do okna Prohlížeč výkonu.

- **Novou relaci výkonu** -přidá relaci prázdný výkonu okno Prohlížeč výkonu.

- **Spusťte** – **spusťte** příkaz seznam umožňuje spustit cílové aplikace, která profilace okamžitě povolené (**spouštění profilace**) nebo s pozastavenou (profilace **Spuštění s profilace pozastavena**).

- **Metoda** -Určuje, zda je relace profilování metoda vzorkování nebo instrumentace.

- **Zastavit** -okamžitě ukončí cílová aplikace a profileru.

- **Attach/Detach** -zobrazí **připojit profileru proces** dialogové okno Vybrat spuštěných procesů, ke kterému chcete připojit profileru.

## <a name="performance-explorer-window"></a>Okno Prohlížeč výkonu

**Prohlížeč výkonu** okno obsahuje ovládací prvek stromu, která zobrazuje binární soubory a data souborů sestav z jednoho nebo více výkonnostních relací.

- **Název relace** -kořenovém ovládací prvek stromu obsahuje název relace. Klikněte pravým tlačítkem na název relace nastavit vlastnosti relace nebo spusťte cílová aplikace a profileru.

- **Cíle** -zobrazuje názvy binární soubory, které mají být profilovaným v relaci. Klikněte pravým tlačítkem na **cíle** přidat nebo odebrat binární, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] projektu nebo webu. Klikněte pravým tlačítkem na název cílového nastavení vlastností pro jednotlivé binárního souboru.

- **Sestavy** -zobrazuje názvy datových souborů profileru, které jsou generovány pro relaci. Klikněte pravým tlačítkem na **sestavy** přidat existující sestavu nebo porovnat dva datových souborů profileru. Klikněte pravým tlačítkem na název sestavy můžete otevřít, odebrat nebo exportovat soubor dat profileru.

## <a name="see-also"></a>Viz také

[Přehledy](../profiling/overviews-performance-tools.md)  
[Konfigurace výkonnostních relací](../profiling/configuring-performance-sessions.md)  
[Řízení shromažďování dat](../profiling/controlling-data-collection.md)