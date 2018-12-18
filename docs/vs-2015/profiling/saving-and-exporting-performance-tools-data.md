---
title: Ukládání a export výkonu nástroje Data | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- performance tools, saving and exporting reports
ms.assetid: 2e9b28fe-3ed2-4e1d-b9cb-0a5e384380b0
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a9b96ae54c91e80fe34c817f710cb400e61f9876
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51768510"
---
# <a name="saving-and-exporting-performance-tools-data"></a>Ukládání a export výkonu nástrojů pro Data
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Toto téma popisuje, jak uložit a exportovat datových souborů výkonu.  
  
##  <a name="BKMK_Save_Profiler_Data_Files_As_Analyzed_Report_Files"></a> Postupy: uložit analyzovanou sestavu do souborů datových souborů výkonu  
 Můžete uložit zobrazení filtrované nebo nefiltrované profilování (.vsp) datové soubory jako soubory analyzované sestav (.vsps). Soubor analyzovanou sestavu lze zobrazit v okně zobrazení sestava a je výrazně menší než původní soubor .vsp. Filtr však nelze použít pro data souboru .vsps. Můžete vytvořit soubor analyzovanou sestavu z prohlížeče výkonu bez nutnosti otevřít soubor v integrovaném vývojovém prostředí (IDE), nebo můžete otevřít a filtrovat souboru .vsp a uložte výsledky.  
  
#### <a name="to-save-an-analyzed-performance-report-from-the-performance-explorer"></a>Chcete-li uložit zprávu o analýze výkonu z prohlížeč výkonu  
  
1.  V části **sestavy**, klikněte pravým tlačítkem na soubor dat profilování, který chcete analyzovat a pak klikněte na tlačítko **uložit analyzovat**.  
  
2.  V **uložit Data analyzovat** dialogové okno pole, zadejte adresář a pak zadejte název souboru.  
  
3.  Klikněte na tlačítko **uložit.**  
  
#### <a name="to-save-an-analyzed-performance-report-from-the-report-view-window"></a>Chcete-li uložit zprávu o analýze výkonu z okna zobrazení sestavy  
  
1.  V okně zobrazit sestavu otevřete souboru dat profilování (.vsp).  
  
2.  (Volitelné) Použijte filtr na data. Další informace najdete v tématu [filtr zobrazení sestav výkonu](../profiling/performance-report-view-filter.md).  
  
3.  Klikněte na tlačítko **uložit analyzovat** na panelu nástrojů okna zobrazení sestavy.  
  
4.  V **uložit Data analyzovat** dialogové okno pole, zadejte adresář a pak zadejte název souboru.  
  
5.  Klikněte na tlačítko **uložit.**  
  
## <a name="how-to-export-profiling-tools-reports-to-an-xml-or-csv-file"></a>Postupy: nástrojů pro profilaci Export sestavy do. XML nebo. Soubor CSV  
 Jedno nebo více zobrazení sestavy můžete exportovat ze souboru .vsp nebo .vsps datového souboru profilování jako buď čárkami oddělený nebo soubor XML. Můžete filtrovat data v okně zobrazení sestava před exportem nebo mohou exportovat sestavy zobrazení celého datového souboru z **prohlížeč výkonu** okna.  
  
> [!NOTE]
>  Můžete také zkopírovat a vložit vybrané řádky z okna zobrazení sestav jako hodnoty oddělené tabulátorem.  
  
#### <a name="to-export-performance-reports-from-the-performance-explorer-window"></a>Export sestavy o výkonu z okna prohlížeče výkonu  
  
1.  V **prohlížeč výkonu**, vyberte sestavu a klikněte pravým tlačítkem a vyberte **exportovat**.  
  
     **Export sestavy** zobrazí se dialogové okno.  
  
2.  Vyberte zobrazení sestav, který chcete exportovat.  
  
3.  V části **předpona sestavy**, zadejte předponu, kterou chcete přidat k názvu sestavy.  
  
4.  V části **umístění exportované sestavy**, zadejte adresář.  
  
5.  V části **formát exportované sestavy**, vyberte (oddělený čárkami) (*.csv) nebo XML Data (\*.xml).  
  
6.  Klikněte na tlačítko **exportovat**.  
  
     Každé zobrazení sestavy se uloží do samostatného souboru, který je pojmenován \<předpony > _\<název zobrazení sestavy >.\< sdílený svazek clusteru&#124;xml >  
  
#### <a name="to-export-performance-reports-from-the-report-view-window"></a>Export sestavy o výkonu z okna zobrazení sestavy  
  
1.  Otevřete soubor .vsp v okně zobrazení sestavy.  
  
2.  (Volitelné) Použijte filtr na data. Další informace najdete v tématu [filtr zobrazení sestav výkonu](../profiling/performance-report-view-filter.md).  
  
3.  Klikněte na tlačítko **Export sestavy** na panelu nástrojů okna zobrazení sestavy.  
  
4.  Vyberte zobrazení sestav, který chcete exportovat.  
  
5.  V části **předpona sestavy**, zadejte předponu, kterou chcete přidat k názvu sestavy.  
  
6.  V části **umístění exportované sestavy**, zadejte adresář.  
  
7.  V části **formát exportované sestavy**, vyberte (oddělený čárkami) (*.csv) nebo XML Data (\*.xml).  
  
8.  Klikněte na tlačítko **exportovat**.  
  
     Každé zobrazení sestavy se uloží do samostatného souboru, který je pojmenován \<předpony > _\<název zobrazení sestavy >.\< sdílený svazek clusteru&#124;xml >  
  
## <a name="see-also"></a>Viz také  
 [Prohlížeč výkonu](../profiling/performance-explorer.md)   
 [Analýza výkonu nástrojů pro Data](../profiling/analyzing-performance-tools-data.md)   
 [Porovnání datových souborů výkonu](../profiling/comparing-performance-data-files.md)   
 [VSPerfReport](../profiling/vsperfreport.md)



