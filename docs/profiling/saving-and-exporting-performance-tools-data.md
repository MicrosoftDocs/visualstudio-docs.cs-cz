---
title: Ukládají se a exportují data nástrojů výkonu | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "74773896"
---
# <a name="save-and-export-performance-tools-data"></a>Uložení a export dat nástrojů pro měření výkonu
Tento článek popisuje, jak uložit a exportovat soubory s daty o výkonu.

## <a name="how-to-save-performance-data-files-as-analyzed-report-files"></a>Postupy: ukládání souborů dat výkonu jako analyzovaných souborů sestav
 Můžete uložit filtrovaná nebo nefiltrovaná zobrazení dat profilace (.* VSP*) soubory jako analyzovaná sestava (.* vsps*) soubory. Analyzovaný soubor sestavy lze zobrazit v okně zobrazení sestavy a je výrazně menší než původní. soubor *VSP* . Nemůžete však použít filtr na data. soubor *vsps* Můžete vytvořit analyzovaný soubor sestavy z Prohlížeč výkonu bez otevření souboru v integrovaném vývojovém prostředí (IDE), nebo můžete otevřít a filtrovat. soubor *VSP* a pak výsledky uložte.

#### <a name="to-save-an-analyzed-performance-report-from-the-performance-explorer"></a>Uložení analyzovaných sestav výkonu z Prohlížeč výkonu

1. V části **sestavy**klikněte pravým tlačítkem na soubor dat profilace, který chcete analyzovat, a pak klikněte na **Uložit analyzované**.

2. V dialogovém okně **Uložit Analyzovaná data** zadejte adresář a potom zadejte název souboru.

3. Klikněte na **Uložit.**

#### <a name="to-save-an-analyzed-performance-report-from-the-report-view-window"></a>Uložení sestavy analýz výkonu z okna zobrazení sestavy

1. Otevřete data profilace (.* VSP*) v okně zobrazení sestavy.

2. Volitelné Použijte filtr na data. Další informace najdete v tématu [Filtr zobrazení sestav výkonu](../profiling/performance-report-view-filter.md).

3. Klikněte na tlačítko **Uložit analyzovat** na panelu nástrojů okna zobrazení sestavy.

4. V dialogovém okně **Uložit Analyzovaná data** zadejte adresář a potom zadejte název souboru.

5. Klikněte na **Uložit.**

## <a name="how-to-export-profiling-tools-reports-to-an-xml-or-csv-file"></a>Postupy: Export sestav nástrojů pro profilaci do souboru. XML nebo. csv
 Jedno nebo více zobrazení sestav můžete exportovat z. soubor *VSP* nebo. soubor dat profilování *vsps* buď jako oddělený čárkou, nebo jako soubor XML. Data můžete filtrovat v okně zobrazení sestavy před exportem nebo můžete exportovat zobrazení sestav celého datového souboru z okna **prohlížeč výkonu** .

> [!NOTE]
> Můžete také zkopírovat a vložit vybrané řádky z okna zobrazení sestavy jako hodnoty oddělené tabulátorem.

#### <a name="to-export-performance-reports-from-the-performance-explorer-window"></a>Export sestav výkonu z okna Prohlížeč výkonu

1. V **prohlížeč výkonu**vyberte sestavu, klikněte pravým tlačítkem a vyberte **exportovat**.

     Zobrazí se dialogové okno **exportovat sestavu** .

2. Vyberte zobrazení sestav, která chcete exportovat.

3. V části **Sestava předpona s**zadejte předponu, kterou chcete přidat do názvu sestavy.

4. V části **umístění exportované sestavy**zadejte adresář.

5. V části **exportovaný formát sestavy**vyberte (textový soubor s oddělovači) ( \* . csv \) nebo data XML ( \* . XML) \) .

6. Klikněte na **Exportovat**.

     Každé zobrazení sestavy je uloženo do samostatného souboru s názvem \<prefix> _ \<report view name> .\<csv&#124;xml>

#### <a name="to-export-performance-reports-from-the-report-view-window"></a>Export sestav výkonu z okna zobrazení sestavy

1. Otevřete. soubor *VSP* v okně zobrazení sestavy.

2. Volitelné Použijte filtr na data. Další informace najdete v tématu [Filtr zobrazení sestav výkonu](../profiling/performance-report-view-filter.md).

3. Na panelu nástrojů okna zobrazení sestav klikněte na **exportovat sestavu** .

4. Vyberte zobrazení sestav, která chcete exportovat.

5. V části **Sestava předpona s**zadejte předponu, kterou chcete přidat do názvu sestavy.

6. V části **umístění exportované sestavy**zadejte adresář.

7. V části **exportovaný formát sestavy**vyberte (textový soubor s oddělovači) ( \* . csv) nebo data XML ( \* . XML).

8. Klikněte na **Exportovat**.

     Každé zobrazení sestavy je uloženo do samostatného souboru s názvem \<prefix> _ \<report view name> .\<csv&#124;xml>

## <a name="see-also"></a>Viz také
- [Prohlížeč výkonu](../profiling/performance-explorer.md)
- [Analýza dat nástrojů pro měření výkonu](../profiling/analyzing-performance-tools-data.md)
- [Porovnání datových souborů výkonu](../profiling/comparing-performance-data-files.md)
- [VSPerfReport](../profiling/vsperfreport.md)
