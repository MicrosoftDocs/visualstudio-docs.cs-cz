---
title: Ukládání a export výkonu nástroje Data | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- performance tools, saving and exporting reports
ms.assetid: 2e9b28fe-3ed2-4e1d-b9cb-0a5e384380b0
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8136369a09145c46c7989bebe12796642851a7b0
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "35675894"
---
# <a name="save-and-export-performance-tools-data"></a>Uložení a export dat nástrojů pro měření výkonu
Tento článek popisuje, jak uložit a exportovat datových souborů výkonu.  
  
## <a name="how-to-save-performance-data-files-as-analyzed-report-files"></a>Postupy: uložení datových souborů výkonu jako soubory analyzovanou sestavu  
 Můžete uložit filtrovaná nebo nefiltrované zobrazení dat profilování (. *Vsp*) soubory tak, jak analyzovat zprávu (. *vsps*) soubory. Soubor analyzovanou sestavu lze zobrazit v okně zobrazení sestava a je výrazně menší než originál. *vsp* souboru. Však nelze použít filtr na data. *vsps* souboru. Můžete vytvořit soubor analyzovanou sestavu z prohlížeče výkonu bez nutnosti otevřít soubor v integrovaném vývojovém prostředí (IDE), nebo můžete otevřít a filtrovat. *vsp* soubor a uložte výsledky.  
  
#### <a name="to-save-an-analyzed-performance-report-from-the-performance-explorer"></a>Chcete-li uložit zprávu o analýze výkonu z prohlížeč výkonu  
  
1.  V části **sestavy**, klikněte pravým tlačítkem na soubor dat profilování, který chcete analyzovat a pak klikněte na tlačítko **uložit analyzovat**.  
  
2.  V **uložit Data analyzovat** dialogové okno pole, zadejte adresář a pak zadejte název souboru.  
  
3.  Klikněte na tlačítko **uložit.**  
  
#### <a name="to-save-an-analyzed-performance-report-from-the-report-view-window"></a>Chcete-li uložit zprávu o analýze výkonu z okna zobrazení sestavy  
  
1.  Otevření dat profilování (. *Vsp*) soubor v okně zobrazení sestavy.  
  
2.  (Volitelné) Použijte filtr na data. Další informace najdete v tématu [filtr zobrazení sestav výkonu](../profiling/performance-report-view-filter.md).  
  
3.  Klikněte na tlačítko **uložit analyzovat** na panelu nástrojů okna zobrazení sestavy.  
  
4.  V **uložit Data analyzovat** dialogové okno pole, zadejte adresář a pak zadejte název souboru.  
  
5.  Klikněte na tlačítko **uložit.**  
  
## <a name="how-to-export-profiling-tools-reports-to-an-xml-or-csv-file"></a>Postupy: Export nástroje pro profilaci sestavy do souboru .xml nebo .csv  
 Můžete exportovat z jednoho nebo více zobrazení sestav. *vsp* souboru nebo. *vsps* profilace datový soubor jako bude čárkami oddělený nebo soubor XML. Můžete filtrovat data v okně zobrazení sestava před exportem nebo mohou exportovat sestavy zobrazení celého datového souboru z **prohlížeč výkonu** okna.  
  
> [!NOTE]
>  Můžete také zkopírovat a vložit vybrané řádky z okna zobrazení sestav jako hodnoty oddělené tabulátorem.  
  
#### <a name="to-export-performance-reports-from-the-performance-explorer-window"></a>Export sestavy o výkonu z okna prohlížeče výkonu  
  
1.  V **prohlížeč výkonu**, vyberte sestavu a klikněte pravým tlačítkem a vyberte **exportovat**.  
  
     **Export sestavy** zobrazí se dialogové okno.  
  
2.  Vyberte zobrazení sestav, který chcete exportovat.  
  
3.  V části **předpona sestavy**, zadejte předponu, kterou chcete přidat k názvu sestavy.  
  
4.  V části **umístění exportované sestavy**, zadejte adresář.  
  
5.  V části **formát exportované sestavy**, vyberte (oddělený čárkami) (\*CSV\), nebo XML Data (\*.xml\).  
  
6.  Klikněte na tlačítko **exportovat**.  
  
     Každé zobrazení sestavy se uloží do samostatného souboru, který je pojmenován \<předpony > _\<název zobrazení sestavy >.\< sdílený svazek clusteru&#124;xml >  
  
#### <a name="to-export-performance-reports-from-the-report-view-window"></a>Export sestavy o výkonu z okna zobrazení sestavy  
  
1.  Otevřít. *vsp* souborů v okně zobrazení sestavy.  
  
2.  (Volitelné) Použijte filtr na data. Další informace najdete v tématu [filtr zobrazení sestav výkonu](../profiling/performance-report-view-filter.md).  
  
3.  Klikněte na tlačítko **Export sestavy** na panelu nástrojů okna zobrazení sestavy.  
  
4.  Vyberte zobrazení sestav, který chcete exportovat.  
  
5.  V části **předpona sestavy**, zadejte předponu, kterou chcete přidat k názvu sestavy.  
  
6.  V části **umístění exportované sestavy**, zadejte adresář.  
  
7.  V části **formát exportované sestavy**, vyberte (oddělený čárkami) (\*CSV), nebo XML Data (\*.xml).  
  
8.  Klikněte na tlačítko **exportovat**.  
  
     Každé zobrazení sestavy se uloží do samostatného souboru, který je pojmenován \<předpony > _\<název zobrazení sestavy >.\< sdílený svazek clusteru&#124;xml >  
  
## <a name="see-also"></a>Viz také:  
 [Prohlížeč výkonu](../profiling/performance-explorer.md)   
 [Analýza dat nástrojů pro výkon](../profiling/analyzing-performance-tools-data.md)   
 [Porovnání datových souborů výkonu](../profiling/comparing-performance-data-files.md)   
 [VSPerfReport](../profiling/vsperfreport.md)
