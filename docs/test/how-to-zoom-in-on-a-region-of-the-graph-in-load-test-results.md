---
title: Přiblížení grafů výsledků zátěžových testů
ms.date: 10/19/2016
ms.topic: conceptual
f1_keywords:
- vs.test.load.monitor.graphzoom
helpviewer_keywords:
- graphs, analyzing load tests
- load tests, zooming with graphs
ms.assetid: 729b4c30-4bc3-4698-91b3-17a676897443
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a22f1a9b6aa772224b217b5de4136687df1462a1
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75594354"
---
# <a name="how-to-zoom-in-on-a-region-of-the-graph-in-load-test-results"></a>Postup: Přiblížení oblasti grafu ve výsledcích zátěžového testu

Po dokončení zátěžového testu můžete pomocí pruhů přiblížení přiblížit a posunout se do oblasti grafu. Přiblížením můžete zkontrolovat data, která byla generována během spuštění zátěžového testu v jemnějších detailech.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Přiblížení je k dispozici pouze v případě, že analyzujete výsledek dokončeného zátěžového testu, nikoli při sledování výsledků průběžného testu.

Ovládací prvek lupy je viditelný pouze v **analyzátoru zátěžového testu,** když zobrazíte výsledek zátěžového testu v režimu přiblížení. Režim přiblížení je vytvořen v zobrazení grafu, když byl dokončen zátěžový test nebo je načten zátěžový test, který byl dříve spuštěn. Ovládací prvky lupy v grafech můžete zobrazit nebo skrýt pomocí funkce **Zobrazit ovládací prvky lupy** na panelu nástrojů.

**Horizontální přiblížení osy x** lze upravit tak, aby analyzovalo konkrétní časová období během zátěžového testu. **Svislé zvětšení osy y** lze upravit tak, aby analyzovalo rozsahy určitých hodnot pro čítače, které jsou zahrnuty v grafu.

Pomocí myši lze upravit **jak vodorovnou časovou osu,** tak ovládací prvky zvětšení **rozsahu svislých hodnot.** **Horizontální ovládací prvek časové osy** lze také upravit pomocí kláves se šipkami vlevo a vpravo. Pomocí kláves se šipkami můžete upravit rozsah přiblížení o 1 interval vzorkování najednou. Pomocí kláves **Shift** a se šipkami provádíte úpravy 10 intervalů vzorkování.

Chcete-li upravit ovládání přiblížení pomocí klávesy se šipkou, nejprve nastavte zaostření na ovládací prvek lupy pomocí klávesy **Tabulátor.** Když má levý jezdec fokus, klávesy se šipkami posunou počáteční hranici okna lupy o 1 interval doleva nebo doprava. Když je fokus na středovém posuvníku, můžete pomocí kláves se šipkami posouvat interval vzorkování okna lupy vlevo nebo vpravo 1 bez změny velikosti okna lupy. A konečně, pravé straně jezdce se pohybuje, rozšíření nebo snížení rozsahu konce okna zoom o 1 interval vzorkování.

Chcete-li vrátit ovládací prvky vodorovného a svislého přiblížení, abyste zobrazili úplné časové osy a rozsahy hodnot, můžete použít volbu **Oddálit vodorovnou** oblast, volbu **Oddálit svisle** nebo **volbu Oddálit obě** v rozbalovací nabídce v grafu.

> [!TIP]
> Pomocí **ovládacích prvků synchronizovat vodorovné zvětšení** na panelu nástrojů můžete zapnout nebo vypnout automatickou synchronizaci vodorovného přiblížení. Při zapnuté synchronizaci se jakékoli přiblížení, které aplikujete na graf, použije také na všechny ostatní grafy v zobrazení Grafy.

![Ovládací prvek zvětšení zobrazení grafu](../test/media/ltest_zoomcontrol.png)

Na předchozím obrázku byl zobrazen graf Systém u **testu,** aby se zjistily problémy s prahovou hodnotou. Porušení prahové hodnoty bylo povoleno pomocí zobrazení **porušení prahové hodnoty v grafu** z rozevíracího seznamu **Možnosti grafu** v panelu nástrojů.

Další informace naleznete [v tématu Analýza výsledků zátěžových testů v zobrazení Grafy](../test/analyze-load-test-results-in-the-graphs-view.md).

## <a name="display-graphs"></a>Zobrazit grafy

Před změnou zobrazení grafu přiblížením nebo oddálením nebo posouváním zobrazte grafy následujícím postupem.

Zobrazení grafů:

1. Spusťte zátěžový test, dokud se nedokončí.

2. Na konci spuštění zátěžového testu zvolte **Ano** v dialogovém okně, které se ptá na zobrazení výsledků z úložiště výsledků zátěžového testu.

     \-nebo -

     Zobrazte podrobnosti o dříve spuštěném zátěžovém testu. Další informace naleznete v [tématu How to: Access load test results for analysis](../test/how-to-access-load-test-results-for-analysis.md).

3. Pokud se grafy nezobrazují, zvolte **Grafy.**

4. Pokud se pruhy přiblížení nezobrazují, zvolte **Zobrazit ovládací prvky přiblížení**.

     Pro každý graf jsou k dispozici dva pruhy přiblížení. Pruh lupy, který řídí svislé měřítko, se zobrazí vlevo od grafu. Pod grafem se zobrazí pruh lupy, který řídí vodorovné měřítko.

     Každý pruh lupy má dva úchyty. Úchyt je obdélníková oblast na každém konci pruhu lupy.

## <a name="zoom-and-scroll"></a>Přiblížení a posouvání

Pokud máte zobrazeno více grafů, můžete je zachovat synchronizované tak, aby zobrazovaly stejnou část spuštění zátěžového testu.

### <a name="to-synchronize-zooming-and-scrolling"></a>Synchronizace přiblížení a posouvání

1. V **analyzátoru zátěžového testu**zvolte **Synchronizovat ovládací prvky vodorovného přiblížení**.

     Když je vybráno tlačítko **Synchronizovat ovládací prvky vodorovného přiblížení,** přiblížení a posouvání časového měřítka jednotlivého grafu také zvětšuje a posouvá časové měřítko ostatních grafů.

2. Znovu zvolte **Synchronizovat ovládací prvky vodorovného přiblížení**.

     Pokud není vybráno tlačítko **Synchronizovat ovládací prvky vodorovného přiblížení,** zvětšování a posouvání časového měřítka jednotlivého grafu ovlivní pouze tento graf.

### <a name="to-zoom-and-scroll-to-a-region-of-the-graph"></a>Zvětšení a posunutí do oblasti grafu

1. Na lupě pod grafem přetáhněte levé táhlo doprava.

     To přiblíží druhou část testovacího běhu. Podobně přetažením pravého úchytu doleva přiblížíte dřívější části testovacího běhu.

2. Chcete-li přiblížit určitou oblast, posuňte obě táhla směrem ke středu grafu.

     Čím blíže jsou dva úchyty k sobě, tím více přiblížíte, abyste zobrazili kratší, jemnější segmenty zátěžového testu.

     Zvolte středovou část pruhu lupy a přetažením se posunete k určitému bodu zátěžového testu.

### <a name="to-zoom-to-a-region-of-the-graph-by-choosing-and-dragging"></a>Přiblížení oblasti grafu výběrem a přetažením

1. Zvolte graf na jednom konci oblasti lupy.

2. Přetáhněte ukazatel myši na druhý konec oblasti lupy.

3. Uvolněte tlačítko myši.

    Tím se zvětší oblast, kterou jste definovali výběrem a přetažením.

   Následující postup popisuje, jak rychle oddálit bez nutnosti upravovat konce lupy.

### <a name="to-zoom-out"></a>Oddálení

1. Klikněte pravým tlačítkem myši na zvětšený graf.

2. V místní nabídce vyberte **Oddálit vodorovné .**

     Tím se oddálí, aby se zobrazila celá doba trvání zátěžového testu.

## <a name="see-also"></a>Viz také

- [Analýza výsledků zátěžových testů v zobrazení Grafy](../test/analyze-load-test-results-in-the-graphs-view.md)
- [Analýza výsledků zátěžových testů](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
- [Postup: Přidání a odstranění čítačů v grafech](../test/how-to-add-and-delete-counters-on-graphs-in-load-test-results.md)
