---
title: Filtrování zobrazení sestav | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- profiling tools, configuring
ms.assetid: 820cf192-7fd6-4bee-9a51-aa69154aca85
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bf8e172f6693b4efcff1cfff3eb8c79178bb9f90
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49919166"
---
# <a name="filter-report-views"></a>Filtrování zobrazení sestav
Filtry můžete použít profilování datové soubory pro omezení, která se zobrazí v zobrazení sestav výkonu a exportovat soubory sestav modulu dat profilování. Můžete omezit sestavu pro data mezi hodnot časového razítka a můžete omezit data, která mají konkrétní procesy a vlákna. Můžete uložit filtry do souboru a pak vytvořit filtr na jiný soubor dat profilování importováním uložený filtr.  
  
 Sestavy do časového úseku lze také omezit pomocí grafického časové osy na souhrnné zobrazení. Zobrazit [postupy: filtrování zobrazení sestav ze souhrnné časové osy](../profiling/how-to-filter-report-views-from-the-summary-timeline.md).  
  
 Vyloučení systému a kód třetích stran ze sestavy, naleznete v tématu [postupy: filtrování profilování nástroje zobrazení sestav k zobrazení pouze můj kód](../profiling/how-to-filter-profiling-tools-report-views-to-display-just-my-code.md)  
  
## <a name="procedures"></a>Procedury  
  
#### <a name="to-create-a-profiler-report-filter"></a>Chcete-li vytvořit filtr sestavy profileru  
  
1.  Pokud se nezobrazí okno Filtr zobrazení sestav výkonu, klikněte na tlačítko **zobrazit filtr** na panelu nástrojů zobrazení sestav výkonu.  
  
     Filtr zobrazení sestav výkonu je tabulka. Každý řádek v tabulce představuje klauzuli filtru. Můžete přidat tolik klauzule filtru.  
  
2.  Pro každou klauzuli, která chcete přidat filtr vyberte nebo zadejte hodnoty do následujících polí řádku.  
  
    |Pole|Popis|  
    |-----------|-----------------|  
    |**A/nebo**|Zvolte **a** Pokud tuto klauzuli i další klauzule musí být hodnota true pro odpovídat výsledek. Zvolte **nebo** Pokud tuto klauzuli nebo další klauzule může být hodnota true pro odpovídat výsledek.|  
    |**Pole**|Vyberte pole sestavy použít v klauzuli filtru ze zobrazeného seznamu datových polí.|  
    |**– Operátor**|Vyberte operátor, který určuje vztah, který chcete v klauzuli mezi pole a hodnotu.<br /><br /> = Rovná se<br /><br /> <> Nerovná se<br /><br /> < Menší než<br /><br /> > Větší než<br /><br /> < = menší než nebo rovno<br /><br /> > = je větší než nebo rovno|  
    |**Hodnota**|Vyberte nebo zadejte hledaná hodnota. Některá pole jsou uvedeny dostupné hodnoty pro pole.|  
  
  
#### <a name="to-create-a-profiler-report-filter-from-the-marks-report-view"></a>Chcete-li vytvořit filtr sestavy profileru v zobrazení sestavy značky  
  
1. Vyberte **značky** z **aktuální zobrazení** seznamu na panelu nástrojů zobrazení sestav výkonu.  
  
    Zobrazí se sestavy profileru značky.  
  
2. Vyberte trasování událostí pro Windows nebo vzorkování, i, kterou chcete použít jako výchozí bod sestavě.  
  
3. Stiskněte a podržte klávesu CTRL a klikněte na událost, kterou chcete použít jako koncový bod sestavy.  
  
4. Klikněte pravým tlačítkem a pak klikněte na jednu z následujících možností:  
  
   - **Přidat filtr na značky** vytvoří klauzulí filtru, které používají sloupec označit jako pole filtru.  
  
   - **Přidat filtr na časová razítka** vytvoří klauzulí filtru, které používají sloupec časového razítka v milisekundách jako pole filtru.  
  
     Tyto dvě možnosti filtrovat aktuální soubor dat na stejný počáteční a koncový bod. Možnost může být lepší, když exportujete filtru pro použití v jiných sestavách.  
  
#### <a name="to-load-an-existing-filter-from-a-file"></a>Načíst existující filtr ze souboru  
  
1.  V zobrazení sestav výkonu nástrojů, klikněte na **filtru importu**.  
  
     **Načíst filtr** se zobrazí dialogové okno.  
  
2.  Zadejte umístění a název souboru filtru (.vspf) pro načtení.  
  
#### <a name="to-execute-a-filter"></a>Chcete-li spustit filtr  
  
-   V zobrazení sestav výkonu nástrojů, klikněte na **spustit filtr**.  
  
#### <a name="to-stop-a-filter-that-is-taking-too-long-to-execute"></a>Chcete-li zastavit filtr, který trvá příliš dlouho  
  
-   V zobrazení sestav výkonu nástrojů, klikněte na **zastavit filtr**.  
  
#### <a name="to-remove-a-filter-on-a-report-view"></a>Chcete-li odebrat filtr na zobrazení sestavy  
  
1.  Odstraňte řádky ustanovení filtr zobrazení sestav výkonu.  
  
2.  V zobrazení sestav výkonu nástrojů, klikněte na **spustit filtr**.  
  
#### <a name="to-save-a-filter-to-a-file"></a>Do souboru uložit filtr  
  
1.  V zobrazení sestav výkonu nástrojů, klikněte na **Exportovat filtr**.  
  
     **Uložit filtr** se zobrazí dialogové okno.  
  
2.  Zadejte umístění a název souboru filtru (.vspf) Chcete-li uložit.  
  
## <a name="see-also"></a>Viz také:  
 [Přizpůsobení zobrazení sestav nástrojů pro měření výkonu](../profiling/customizing-performance-tools-report-views.md)