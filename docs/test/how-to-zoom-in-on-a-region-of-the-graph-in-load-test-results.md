---
title: Přiblížit grafy výsledků zátěžového testu
description: Naučte se, jak kontrolovat data generovaná během zátěžového testu podrobnějším způsobem pomocí pruhů přiblížení k přiblížení a posouvání oblasti grafu.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
f1_keywords:
- vs.test.load.monitor.graphzoom
helpviewer_keywords:
- graphs, analyzing load tests
- load tests, zooming with graphs
ms.assetid: 729b4c30-4bc3-4698-91b3-17a676897443
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 172b777111027b4492420185b53086f55ee4084b
ms.sourcegitcommit: 9ce13a961719afbb389fa033fbb1a93bea814aae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/30/2020
ms.locfileid: "96328662"
---
# <a name="how-to-zoom-in-on-a-region-of-the-graph-in-load-test-results"></a>Postupy: přiblížení oblasti grafu do výsledků zátěžového testu

Po dokončení zátěžového testu můžete použít pruhy přiblížení k přiblížení a posouvání oblasti grafu. Přiblížením můžete zkontrolovat data, která byla vygenerována během zátěžového testu, v podrobnějších podrobnostech.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Přiblížení je k dispozici pouze v případě, že analyzujete výsledek dokončeného zátěžového testu, nikoli při pozorování výsledků spuštěného testu.

Ovládací prvek přiblížení je viditelný pouze v **analyzátoru zátěžového testu** při zobrazení výsledku zátěžového testu v režimu přiblížení. Režim přiblížení je vytvořen v zobrazení grafu, když je dokončen buď zátěžový test, nebo je načten zátěžový test, který byl dříve spuštěn. Můžete zobrazit nebo skrýt ovládací prvky přiblížení v grafech pomocí tlačítka **Zobrazit ovládací prvky zvětšení** na panelu nástrojů.

**Vodorovný přiblížení osy x** lze upravit tak, aby během zátěžového testu mohla analyzovat konkrétní časová období. **Svislé přiblížení osy y** se dá upravit tak, aby se pro čítače zahrnuté v grafu analyzovaly konkrétní rozsahy hodnot.

**Vodorovnou časovou osu** i svislé ovládací prvky přiblížení **rozsahu hodnot** lze upravit pomocí myši. **Vodorovný ovládací prvek časové osy** lze také upravit pomocí kláves Šipka vlevo a vpravo. Když použijete klávesy se šipkami k úpravě ovládacího prvku Lupa, můžete upravit rozsah oken Windows podle 1 intervalu vzorkování po dobu 1. Pomocí kláves **SHIFT** a šipky lze upravit 10 vzorkovacích intervalů.

Chcete-li upravit ovládací prvek přiblížení pomocí klávesy šipka, nejprve nastavte fokus na ovládací prvek zvětšení pomocí klávesy **TAB** . Když má Levý posuvník fokus, klávesy se šipkami přesunou počáteční hranici okna Lupa o 1 interval doleva nebo doprava. Když je fokus na středovém posuvníku, můžete pomocí kláves se šipkami posunout interval přiblížení doleva nebo doprava 1, aniž by se změnila velikost okna lupy. A nakonec posuvník na pravé straně přesouvá, rozšiřuje nebo zmenšuje rozsah konce okna lupy o 1 interval vzorkování.

Chcete-li vrátit vodorovné a svislé ovládací prvky přiblížení k zobrazení celé časové osy a rozsahů hodnot, můžete použít možnost **Rozblížit horizontální** , **svislou možnost přiblížení** nebo **oddálení obou** možností v místní nabídce grafu.

> [!TIP]
> Pomocí funkce **Synchronizovat vodorovné ovládací prvky přiblížení** na panelu nástrojů můžete zapnout nebo vypnout automatickou synchronizaci horizontálního přiblížení. Při synchronizaci se u všech ostatních grafů v zobrazení grafů použije i jakékoli přiblížení, které použijete u grafu.

![Ovládací prvek zvětšení zobrazení grafu](../test/media/ltest_zoomcontrol.png)

V předchozím obrázku byl systém v **testovacím** grafu přizpůsobený, aby bylo možné prozkoumat problémy s prahovou hodnotou. Překročení prahových hodnot bylo povoleno pomocí možnosti **Zobrazit překročení prahové hodnoty v grafu** z rozevíracího seznamu **Možnosti grafu** na panelu nástrojů.

Další informace naleznete v tématu [Analýza výsledků zátěžových testů v zobrazení grafů](../test/analyze-load-test-results-in-the-graphs-view.md).

## <a name="display-graphs"></a>Zobrazit grafy

Než změníte zobrazení grafu zvětšením nebo zmenšením nebo posouváním, použijte tento postup k zobrazení grafů.

Zobrazení grafů:

1. Spusťte zátěžový test, dokud se nedokončí.

2. Na konci běhu zátěžového testu v dialogovém okně, které se zeptá o zobrazení výsledků z úložiště výsledků zátěžového testu, vyberte **Ano** .

     \- ani

     Zobrazte podrobnosti o dříve spuštěném zátěžovém testu. Další informace najdete v tématu [Postup: přístup k výsledkům zátěžového testu pro analýzu](../test/how-to-access-load-test-results-for-analysis.md).

3. Pokud nejsou grafy zobrazeny, vyberte možnost **grafy** .

4. Pokud se nezobrazují čáry přiblížení, vyberte **Zobrazit ovládací prvky zvětšení**.

     Pro každý graf jsou k dispozici dva pruhy přiblížení. Panel přiblížení, který ovládá svislé měřítko, se zobrazí nalevo od grafu. V grafu se zobrazí panel přiblížení, který ovládá horizontální měřítko.

     Každý panel přiblížení má dva popisovače. Popisovač je obdélníková oblast na každém konci panelu přiblížení.

## <a name="zoom-and-scroll"></a>Lupa a posouvání

Pokud máte zobrazeno více grafů, můžete je udržovat synchronizované, aby zobrazovaly stejnou část běhu zátěžového testu.

### <a name="to-synchronize-zooming-and-scrolling"></a>Synchronizace lupy a posouvání

1. V **analyzátoru zátěžového testu** vyberte možnost **Synchronizovat vodorovné ovládací prvky lupy**.

     Když je vybraná možnost **synchronizovat horizontální ovládací prvky přiblížení** , přiblíží se a posune se časové měřítko jednotlivého grafu a posune se i časové měřítko ostatních grafů.

2. Znovu vyberte možnost **synchronizovat horizontální ovládací prvky lupy**.

     Pokud není vybráno tlačítko **synchronizovat horizontální ovládací prvky přiblížení** , přibližování a posouvání časového měřítka jednotlivého grafu ovlivní pouze tento graf.

### <a name="to-zoom-and-scroll-to-a-region-of-the-graph"></a>Přiblížení a posouvání do oblasti grafu

1. Na panelu přiblížení v grafu přetáhněte levý úchyt na pravé straně.

     Tím se přiblíží k druhé části testovacího běhu. Podobně přetáhněte úchyt na pravé straně k levému přiblížení v předchozích částech testovacího běhu.

2. Chcete-li přiblížit určitou oblast, posuňte oba úchyty do středu grafu.

     Spolu tyto dva popisovače jsou navzájem, další přiblížení se zobrazí kratší a jemnější segmenty zátěžového testu.

     Zvolte prostřední část panelu přiblížení a pak ji přetáhněte na konkrétní bod v zátěžovém testu.

### <a name="to-zoom-to-a-region-of-the-graph-by-choosing-and-dragging"></a>Přiblížení oblasti grafu výběrem a přetažením

1. Vyberte graf na jednom konci oblasti přiblížení.

2. Přetáhněte ukazatel myši na druhý konec oblasti přiblížení.

3. Uvolněte tlačítko myši.

    Tím se zvětší oblast, kterou jste definovali volbou a přetažením.

   Následující postup popisuje, jak rychle oddálení zmenšit, aniž byste museli upravovat konce panelu přiblížení.

### <a name="to-zoom-out"></a>Oddálení

1. Klikněte pravým tlačítkem na graf přiblížit.

2. V místní nabídce vyberte možnost **oddálení vodorovně**.

     Tímto přiblížením zobrazíte celou dobu trvání běhu zátěžového testu.

## <a name="see-also"></a>Viz také

- [Analýza výsledků zátěžových testů v zobrazení grafů](../test/analyze-load-test-results-in-the-graphs-view.md)
- [Analyzovat výsledky zátěžového testu](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
- [Postupy: přidávání a odstraňování čítačů v grafech](../test/how-to-add-and-delete-counters-on-graphs-in-load-test-results.md)
