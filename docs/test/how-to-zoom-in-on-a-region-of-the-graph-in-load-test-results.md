---
title: Přiblížit na grafy výsledků testu zatížení
ms.date: 10/19/2016
ms.topic: conceptual
f1_keywords:
- vs.test.load.monitor.graphzoom
helpviewer_keywords:
- graphs, analyzing load tests
- load tests, zooming with graphs
ms.assetid: 729b4c30-4bc3-4698-91b3-17a676897443
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 558d6429c5d92f833e81074fe928436ab6e7f30e
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53064890"
---
# <a name="how-to-zoom-in-on-a-region-of-the-graph-in-load-test-results"></a>Postupy: přiblížení oblasti grafu ve výsledcích zátěžového testu

Po dokončení zátěžového testu můžete přiblížit a přejděte do oblasti grafu pruhy přiblížení. Podle přiblížit, můžete zkoumat data, která byla vygenerována během spuštění jemnější podrobně zátěžového testu.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Přiblížit je k dispozici pouze při analýze výsledku dokončeného zátěžového testu není během pozorujete výsledky spuštění testu.

Ovládací prvek lupy je viditelná pouze v **Analyzéru zátěžového testu** při prohlížení výsledku zátěžového testu v zvětšení a zmenšení režimu. V zobrazení grafu je stanoven režim zvětšení a zmenšení, po dokončení zátěžového testu nebo načíst zátěžového testu, která byla dříve spuštěna. Můžete zobrazit nebo skrýt ovládací prvky zvětšení na grafy pomocí **zobrazit ovládací prvky zvětšení** na panelu nástrojů.

**Vodorovné osy x lupy** k analýze konkrétní časová období, během zátěžového testu lze upravit. **Svislé osy y přiblížení** lze upravit k analýze rozsahy konkrétní hodnotu čítače, které jsou zahrnuty v grafu.

Oba **vodorovné ose** a **rozsah hodnot svislé** ovládací prvky zvětšení lze upravit pomocí myši. **Ovládací prvek vodorovné ose** může být také upravena pomocí kláves šipka doleva a doprava. Pomocí kláves se šipkami upravit ovládací prvek lupy, můžete upravit rozsah windows ve vzorkovací frekvence 1 najednou. Použití **Shift** a klávesy se šipkami provádí úpravy 10 intervalů vzorkování.

Chcete-li upravit ovládací prvek lupy pomocí klávesy šipka, nejprve se zaměřit na ovládací prvek lupy pomocí **kartu** klíč. Pokud Levý posuvník má fokus, klávesy se šipkami se přesunout počáteční hranice okna přiblížení 1 interval doleva nebo doprava. Pokud je fokus nastavený na posuvník System center, můžete použít klávesy se šipkami posouvat přiblížení okno doleva nebo doprava 1 interval vzorkování beze změny velikosti okna přiblížení. A nakonec se posune posuvník na pravé straně, rozšíření nebo snížením rozsahu konec časového období přiblížení o 1 interval vzorkování.

Vrátit ovládací prvky vodorovného a svislého zvětšení zobrazíte úplný časového harmonogramu a rozsahy hodnot, můžete použít **zvětšení limitu vodorovné** možnost, **přiblížení na svislé** možnost, nebo **Oddálit Obě** možnost v rozbalovací nabídce v grafu.

> [!TIP]
> Můžete použít **synchronizovat vodorovné přiblížení ovládací prvky** v panelu nástrojů můžete zapnout nebo vypnout automatické vodorovného zvětšení synchronizace. Synchronizace na jakékoli změna měřítka zobrazení, které použijete do grafu použijí se taky pro jiné grafy pro zobrazení grafů.

![Ovládací prvek lupy grafu zobrazit](../test/media/ltest_zoomcontrol.png)

Na předchozím obrázku **zkoušený systém** graf má přiblížení, a zjistit problémy s prahovou hodnotou. Byly povoleny překročení mezních hodnot s použitím **zobrazit v grafu porušení mezních** z **možnosti grafu** rozevíracího seznamu na panelu nástrojů.

Další informace najdete v tématu [výsledků zátěžového testu analyzovat v zobrazení grafů](../test/analyze-load-test-results-in-the-graphs-view.md).

## <a name="display-graphs"></a>Zobrazení grafů

Před změnou zobrazení grafu přiblížení nebo oddálení nebo posouvání, zobrazení grafů pomocí tohoto postupu.

Chcete-li zobrazit grafy:

1.  Spusťte zátěžový test, dokud se nedokončí.

2.  Na konci zátěžového testu, zvolte **Ano** v dialogovém okně, které žádá o zobrazení výsledků z výsledků zátěžových testů úložiště.

     \- nebo –

     Zobrazte podrobnosti o dříve spuštěném zátěžovém testu. Další informace najdete v tématu [postupy: přístup k analýze výsledků zátěžového testu](../test/how-to-access-load-test-results-for-analysis.md).

3.  Zvolte **grafy** Pokud vaše grafy nejsou zobrazeny.

4.  Pokud se nezobrazují přiblížení pruhy, zvolte **zobrazit ovládací prvky zvětšení**.

     Dva panely přiblížení jsou k dispozici pro každý graf. Panel přiblížení, který řídí vertikální škálování se zobrazí nalevo od grafu. V grafu se zobrazí pruh zvětšení, které řídí horizontálního škálování.

     Každý panel přiblížení má dva popisovače. Popisovač je obdélníkovou oblast na každém konci panelu přiblížení.

## <a name="zoom-and-scroll"></a>Přiblížení a posouvání

Pokud máte více grafů, které se zobrazí, můžete zachovat jejich synchronizaci, aby se zobrazí stejné část zátěžového testu.

### <a name="to-synchronize-zooming-and-scrolling"></a>Synchronizovat přibližování a posouvání

1.  Na **Analyzéru zátěžového testu**, zvolte **synchronizovat vodorovné přiblížení ovládací prvky**.

     Když **synchronizovat vodorovné přiblížení ovládací prvky** vybere tlačítko, přibližování a posouvání časové měřítko grafu jednotlivé také přiblížení a zobrazení se posune časové měřítko další grafy.

2.  Znovu, vyberte **synchronizovat vodorovné přiblížení ovládací prvky**.

     Když **synchronizovat vodorovné přiblížení ovládací prvky** tlačítko není vybrané, přibližování a posouvání časové měřítko grafu jednotlivé ovlivní pouze tohoto grafu.

### <a name="to-zoom-and-scroll-to-a-region-of-the-graph"></a>Přiblížení a přejděte do oblasti grafu

1.  Na panelu přiblížení pod graf přetažením úchytu levé straně na pravé straně.

     To se přiblíží ve druhé části testovacího běhu. Podobně přetažením úchytu na pravé straně vlevo přiblíží v dřívější části testovacího běhu.

2.  Přiblížit na určitou oblast snímků obou popisovače směrem do středu grafu.

     Čím blíž dva popisovače jsou k sobě navzájem, tím více přiblížit zobrazíte kratší, jemnější segmenty zátěžového testu.

     Vyberte centrum části panelu přiblížení a poté ji přetáhněte do přejděte na konkrétní místo v zátěžovém testu.

### <a name="to-zoom-to-a-region-of-the-graph-by-choosing-and-dragging"></a>Přiblížení výběrem a přetažením do oblasti grafu

1. Zvolte na jednom konci přiblížení oblasti grafu.

2. Přetažením ukazatele myši na druhém konci přiblížení oblasti.

3. Uvolněte tlačítko myši.

    Tím se zvětší oblasti, která jste definovali kliknutím a přetažením.

   Následující postup popisuje, jak rychle horizonální oddálení, aniž by bylo nutné upravit konce panelu přiblížení.

### <a name="to-zoom-out"></a>Zmenšíte.

1.  Klikněte pravým tlačítkem na graf přiblížené.

2.  V místní nabídce vyberte **zvětšení limitu vodorovné**.

     To Oddálí zobrazíte spuštění celou dobu trvání zátěžového testu.

## <a name="see-also"></a>Viz také:

- [Analýza výsledků zátěžových testů v zobrazení grafů](../test/analyze-load-test-results-in-the-graphs-view.md)
- [Analýza výsledků zátěžových testů](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
- [Postupy: Přidání a odstranění čítačů pro grafy](../test/how-to-add-and-delete-counters-on-graphs-in-load-test-results.md)