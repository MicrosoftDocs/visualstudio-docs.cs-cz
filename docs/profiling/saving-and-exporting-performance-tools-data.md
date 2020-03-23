---
title: Ukládání a export dat nástrojů výkonu | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- performance tools, saving and exporting reports
ms.assetid: 2e9b28fe-3ed2-4e1d-b9cb-0a5e384380b0
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 729dc2e28446420dd2590e132b7ec8a5444fcb9c
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74773896"
---
# <a name="save-and-export-performance-tools-data"></a>Uložení a export dat nástrojů pro měření výkonu
Tento článek popisuje, jak uložit a exportovat datové soubory výkonu.

## <a name="how-to-save-performance-data-files-as-analyzed-report-files"></a>Postup: Uložení datových souborů výkonu jako analyzovaných souborů sestav
 Můžete uložit filtrovaná nebo nefiltrovaná zobrazení dat profilování (.* vsp*) soubory jako analyzované sestavy (.* vsps*) soubory. Analyzovaný soubor sestavy lze zobrazit v okně zobrazení sestavy a je výrazně menší než původní . *vsp.* Filtr však nelze použít na data aplikace . *vsps.* Analyzovaný soubor sestavy můžete vytvořit z Průzkumníka výkonu bez otevření souboru v integrovaném vývojovém prostředí (IDE), nebo můžete otevřít a filtrovat . *vsp* a výsledky uložte.

#### <a name="to-save-an-analyzed-performance-report-from-the-performance-explorer"></a>Uložení analyzované sestavy výkonu z Průzkumníka výkonu

1. V části **Sestavy**klikněte pravým tlačítkem myši na datový soubor profilování, který chcete analyzovat, a potom klikněte na **uložit analyzovaný**soubor .

2. V dialogovém okně **Uložit analyzovaná data** zadejte adresář a zadejte název souboru.

3. Klikněte na **Uložit.**

#### <a name="to-save-an-analyzed-performance-report-from-the-report-view-window"></a>Uložení analyzované sestavy výkonu z okna zobrazení sestavy

1. Otevřete data profilování (.* vsp*) v okně zobrazení sestavy.

2. (Nepovinné) Použití filtru na data. Další informace naleznete v tématu [Sledování výkonu sestavy filtru](../profiling/performance-report-view-filter.md).

3. Na panelu nástrojů okna zobrazení sestavy klikněte na **Uložit analyzovaný.**

4. V dialogovém okně **Uložit analyzovaná data** zadejte adresář a zadejte název souboru.

5. Klikněte na **Uložit.**

## <a name="how-to-export-profiling-tools-reports-to-an-xml-or-csv-file"></a>Postup: Export sestav profilovacích nástrojů do souboru XML nebo CSV
 Můžete exportovat jedno nebo více zobrazení sestavy z . *vsp* nebo . *vsps* profilování datového souboru jako čárka oddělená nebo soubor XML. Před exportem můžete filtrovat data v okně Zobrazení sestavy nebo můžete exportovat zobrazení sestavy celého datového souboru z okna **Průzkumník výkonu.**

> [!NOTE]
> Vybrané řádky můžete také zkopírovat a vložit z okna Zobrazení sestavy jako hodnoty oddělené tabulátory.

#### <a name="to-export-performance-reports-from-the-performance-explorer-window"></a>Export zpráv o výkonu z okna Průzkumník výkonu

1. V **Průzkumníku výkonu**vyberte sestavu a potom klepněte pravým tlačítkem myši a vyberte **exportovat**.

     Zobrazí se dialogové okno **Exportovat sestavu.**

2. Vyberte zobrazení sestavy, která chcete exportovat.

3. V části **Sestava předpony s ,** zadejte předponu, kterou chcete přidat k názvu sestavy.

4. V části **Exportované umístění sestavy**zadejte adresář.

5. V části **Exportovaný formát sestavy**vyberte možnost\*(Čárka oddělená) ( .csv\)nebo XML Data (\*XML .\)

6. Klikněte na **Exportovat**.

     Každé zobrazení sestavy je uloženo do \<samostatného\<souboru s názvem předpona>_ název zobrazení sestavy>. \<csv&#124;> xml

#### <a name="to-export-performance-reports-from-the-report-view-window"></a>Export zpráv o výkonu z okna zobrazení sestavy

1. Otevřete . *vsp* v okně zobrazení sestavy.

2. (Nepovinné) Použití filtru na data. Další informace naleznete v tématu [Sledování výkonu sestavy filtru](../profiling/performance-report-view-filter.md).

3. Na panelu nástrojů okna zobrazení sestavy klikněte na **Exportovat sestavu.**

4. Vyberte zobrazení sestavy, která chcete exportovat.

5. V části **Sestava předpony s ,** zadejte předponu, kterou chcete přidat k názvu sestavy.

6. V části **Exportované umístění sestavy**zadejte adresář.

7. V části **Exportovaný formát sestavy**vyberte možnost\*(Čárka oddělená) ( .csv) nebo Data XML (\*XML).

8. Klikněte na **Exportovat**.

     Každé zobrazení sestavy je uloženo do \<samostatného\<souboru s názvem předpona>_ název zobrazení sestavy>. \<csv&#124;> xml

## <a name="see-also"></a>Viz také
- [Prohlížeč výkonu](../profiling/performance-explorer.md)
- [Analýza dat nástrojů pro měření výkonu](../profiling/analyzing-performance-tools-data.md)
- [Porovnání datových souborů výkonu](../profiling/comparing-performance-data-files.md)
- [VSPerfReport](../profiling/vsperfreport.md)
