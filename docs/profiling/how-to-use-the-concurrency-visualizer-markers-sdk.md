---
title: Použití sady SDK značek Vizualizátor souběžnosti | Microsoft Docs
description: Naučte se používat sady SDK značek Vizualizátor souběžnosti v sadě Visual Studio k vytváření rozsahů a psaní příznaků, zpráv a výstrah.
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 19a45032-f8a7-4137-890e-2ceeec938b8d
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: fab15ce9d3782b2ef7e38d5cca0e2b71d77fbc46
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99920757"
---
# <a name="how-to-use-the-concurrency-visualizer-markers-sdk"></a>Postupy: použití sady značek Vizualizátor souběžnosti
V tomto tématu se dozvíte, jak použít sadu Vizualizátor souběžnosti SDK k vytváření rozsahů a zápisových příznaků, zpráv a výstrah.

### <a name="to-use-c"></a>Použití jazyka C++

1. Přidejte do své aplikace podporu Vizualizátor souběžnosti sady SDK. Další informace najdete v tématu [sada Vizualizátor souběžnosti SDK](../profiling/concurrency-visualizer-sdk.md).

2. Přidejte `include` příkaz a `using` příkaz pro sadu SDK.

    ```cpp
    #include <cvmarkersobj.h>
    using namespace Concurrency::diagnostic;
    ```

3. Přidejte kód pro vytvoření tří rozsahů ve výchozí řadě značek a napište příznak, zprávu a výstrahu, jednu do každého rozpětí. Metody pro zápis příznaků, zpráv a výstrah jsou členy třídy [marker_series](../profiling/marker-series-class.md) . Konstruktor pro třídu [span](../profiling/span-class.md) vyžaduje `marker_series` objekt, aby každý rozsah byl přidružen ke konkrétní řadě značek. `span`Končí, když se odstraní.

    ```cpp
    marker_series series;
    span *flagSpan = new span(series, 1, _T("flag span"));
    series.write_flag(_T("Here is the flag."));
    delete flagSpan;

    span *messageSpan = new span(series, 2, _T("message span"));
    series.write_flag(_T("Here is the message."));
    delete messageSpan;

    span *alertSpan = new span(series, 3, _T("alert span"));
    series.write_flag(_T("Here is the alert."));
    delete alertSpan;
    ```

4. Na panelu nabídek vyberte možnost **analyzovat**, **Vizualizér souběžnosti**, **začněte s aktuálním projektem** a spusťte aplikaci a zobrazte Vizualizér souběžnosti. Následující ilustrace znázorňuje tři rozpětí a tři značky v Vizualizátor souběžnosti.

     ![Vizualizátor souběžnosti se 3 značkami a výstrahami](../profiling/media/cvmarkersnative.png "CvMarkersNative")

5. Přidejte kód pro vytvoření další vlastní řady značek voláním konstruktoru pro `marker_series` , který přebírá název řetězce pro řady značek.

    ```cpp
    marker_series flagSeries(_T("flag series"));
    span *flagSeriesSpan = new span(flagSeries, 1, _T("flag span"));
    flagSeries.write_flag(1, _T("flag"));
    // Sleep to even out the display in the Concurrency Visualizer.
    Sleep(50);
    delete flagSeriesSpan;

    marker_series messageSeries(_T("message series"));
    span *messageSeriesSpan = new span(messageSeries, 1, _T("message span"));
    messageSeries.write_message(1, _T("message"));
    // Sleep to even out the display in the Concurrency Visualizer.
    Sleep(50);
    delete messageSeriesSpan;
    ```

6. Spustí aktuální projekt, aby se zobrazil Vizualizér souběžnosti. Tato dvě série značek se zobrazí v zobrazení vláken v jejich vlastních koridorech. Následující ilustrace znázorňuje dvě nová rozpětí.

     ![Snímek obrazovky s zobrazením vláken v Vizualizátor souběžnosti, který zobrazuje značku, příznak a řadu zpráv s rozsahem příznaků a rozsahem zpráv.](../profiling/media/cvmarkerseriesnative.png "CvMarkerSeriesNative")

### <a name="to-use-visual-basic-or-c"></a>Použití Visual Basic nebo C\#

1. Přidejte do své aplikace podporu Vizualizátor souběžnosti sady SDK. Další informace najdete v tématu [sada Vizualizátor souběžnosti SDK](../profiling/concurrency-visualizer-sdk.md).

2. Přidejte `using` příkaz nebo `Imports` pro sadu SDK.

    ```vb
    Imports Microsoft.ConcurrencyVisualizer.Instrumentation
    ```

    ```csharp
    using Microsoft.ConcurrencyVisualizer.Instrumentation;
    ```

3. Přidejte kód pro vytvoření tří různých rozsahů na výchozí řadě značek a napište příznak, zprávu a výstrahu, jednu do každého rozpětí. Objekt [span](/previous-versions/hh694189(v=vs.140)) vytvoříte voláním statické `EnterSpan` metody. Chcete-li zapisovat do výchozí řady, použijte statické metody zápisu třídy [značek](/previous-versions/hh694099(v=vs.140)) .

    ```vb
    Dim flagSpan As Span = Markers.EnterSpan("flag span")
    Markers.WriteFlag("Here is the flag.")
    flagSpan.Leave()

    Dim messageSpan As Span = Markers.EnterSpan("message span")
    ' Sleep for a millisecond to even out the display in the Concurrency Visualizer.
    System.Threading.Thread.Sleep(1)
    Markers.WriteMessage("Here is a message")
    messageSpan.Leave()

    Dim alertSpan As Span = Markers.EnterSpan("alert span")
    ' Sleep for a millisecond to even out the display in the Concurrency Visualizer.
    System.Threading.Thread.Sleep(1)
    Markers.WriteAlert("Here is an alert")
    alertSpan.Leave()
    ```

    ```csharp
    Span flagSpan = Markers.EnterSpan("flag span");
    Markers.WriteFlag("Here is the flag.");
    flagSpan.Leave();

    Span messageSpan = Markers.EnterSpan("message span");
    // Sleep for a millisecond to even out the display in the Concurrency Visualizer.
    System.Threading.Thread.Sleep(1);
    Markers.WriteMessage("Here is a message");
    messageSpan.Leave();

    Span alertSpan = Markers.EnterSpan("alert span");
    // Sleep for a millisecond to even out the display in the Concurrency Visualizer.
    System.Threading.Thread.Sleep(1);
    Markers.WriteAlert("Here is an alert");
    alertSpan.Leave();
    ```

4. Na panelu nabídek vyberte možnost **analyzovat**, **Vizualizér souběžnosti**, **začněte s aktuálním projektem** a spusťte aplikaci a zobrazte Vizualizér souběžnosti. Následující ilustrace znázorňuje tři rozpětí a tři značky v zobrazení vláken Vizualizátor souběžnosti.

     ![Vizualizátor souběžnosti se značkami a výstrahami](../profiling/media/cvmarkersmanaged.png "CvMarkersManaged")

5. Přidejte kód pro vytvoření řady značek zákazníka pomocí metody static [CreateMarkerSeries](/previous-versions/hh694171(v=vs.140)) . Třída [MarkerSeries](/previous-versions/hh694127(v=vs.140)) obsahuje metody pro vytváření a psaní příznaků, zpráv a upozornění.

    ```VB

    Dim flagSeries As MarkerSeries = Markers.DefaultWriter.CreateMarkerSeries("flag series")
    Dim flagSeriesSpan As Span = flagSeries.EnterSpan("flag span")
    System.Threading.Thread.Sleep(1)
    flagSeries.WriteFlag(1, "flag")
    System.Threading.Thread.Sleep(1)
    flagSeriesSpan.Leave()

    Dim messageSeries As MarkerSeries = Markers.DefaultWriter.CreateMarkerSeries("message series")
    Dim messageSeriesSpan As Span = messageSeries.EnterSpan("message span")
    messageSeries.WriteMessage("message")
    System.Threading.Thread.Sleep(1)
    messageSeriesSpan.Leave()
    ```

    ```csharp

    MarkerSeries flagSeries = Markers.DefaultWriter.CreateMarkerSeries("flag series");
    Span flagSeriesSpan = flagSeries.EnterSpan("flag span");
    System.Threading.Thread.Sleep(1);
    flagSeries.WriteFlag(1, "flag");
    System.Threading.Thread.Sleep(1);
    flagSeriesSpan.Leave();

    MarkerSeries messageSeries = Markers.DefaultWriter.CreateMarkerSeries("message series");
    Span messageSeriesSpan = messageSeries.EnterSpan("message span");
    messageSeries.WriteMessage("message");
    System.Threading.Thread.Sleep(1);
    messageSeriesSpan.Leave();
    ```

6. Spustí aktuální projekt, aby se zobrazil Vizualizér souběžnosti. Tři řady značek se zobrazí v zobrazení vláken v jejich vlastních koridorech. Následující ilustrace znázorňuje tři nové rozsahy.

     ![Snímek obrazovky s zobrazením vláken v Vizualizátor souběžnosti, který zobrazuje značku, příznak a řadu zpráv, se zprávou, výstrahou a rozsahem příznaku.](../profiling/media/cvmarkerseriesmanaged.png "CvMarkerSeriesManaged")

## <a name="see-also"></a>Viz také
- [SDK Vizualizéru souběžnosti](../profiling/concurrency-visualizer-sdk.md)
