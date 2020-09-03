---
title: Zobrazení modulů | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.view.modules
helpviewer_keywords:
- Modules view
- profiling tools reports, Modules view
- profiling tools, Modules view
ms.assetid: 4314a404-2120-425b-be42-180cd4bac840
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 89d9146b3f724b4883f21a43689a495eef252777
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "74778515"
---
# <a name="modules-view"></a>Zobrazení modulů
V zobrazení modulů jsou uvedeny moduly dat profilování. Každý modul je kořenovým uzlem hierarchického stromu. Profilované funkce modulu jsou uvedeny pod uzlem modulu. Pokud byla data profilace shromážděna pomocí metody vzorkování, jsou informace o řádku uvedeny pod uzlem funkce a data ukazatele instrukcí jsou uvedena pod uzlem line.

 Rozbalte nebo sbalte název modulu pro zobrazení nebo zavření zobrazení dat výkonu modulu.

 Chcete-li přidat nebo odebrat sloupce, klikněte pravým tlačítkem myši v okně sestavy a vyberte možnost **Přidat nebo odebrat sloupce**. Data můžete seřadit kliknutím na název sloupce. Další informace najdete v tématu [Postup: přizpůsobení sloupců zobrazení sestavy](../profiling/how-to-customize-report-view-columns.md).

 Sloupce, které jsou k dispozici v zobrazení modulů, závisí na metodě profilace (vzorkování nebo instrumentace), která byla použita ke shromažďování dat a zda byla data paměti .NET shromažďována při spuštění profilace.

## <a name="see-also"></a>Viz také
- [Zobrazení modulů](../profiling/modules-view-sampling-data.md)
- [Zobrazení modulů](../profiling/modules-view-instrumentation-data.md)
- [Zobrazení modulů – instrumentace](../profiling/modules-view-dotnet-memory-instrumentation-data.md)
- [Zobrazení modulů – vzorkování](../profiling/modules-view-dotnet-memory-sampling-data.md)
- [Zobrazení modulů](../profiling/modules-view-contention-data.md)
