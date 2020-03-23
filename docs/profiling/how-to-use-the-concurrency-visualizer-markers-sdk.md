---
title: 'Postup: Použití značek vizualizéru souběžnosti SDK | Dokumenty společnosti Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 19a45032-f8a7-4137-890e-2ceeec938b8d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2d97ea90963f70d3a06c669f08473bab27fa08bd
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "68870335"
---
# <a name="how-to-use-the-concurrency-visualizer-markers-sdk"></a>Postup: Použití značek vizualizéru souběžnosti SDK
Toto téma ukazuje, jak pomocí souběžnoměnové visualizer SDK vytvořit rozsahy a psát příznaky, zprávy a výstrahy.

### <a name="to-use-c"></a>Použití jazyka C++

1. Přidejte podporu souběžnosti Visualizer SDK do vaší aplikace. Další informace naleznete v [tématu Souběžnost Visualizer SDK](../profiling/concurrency-visualizer-sdk.md).

2. Přidejte `include` příkaz `using` a příkaz pro sdk.

    ```cpp
    #include <cvmarkersobj.h>
    using namespace Concurrency::diagnostic;
    ```

3. Přidejte kód, který vytvoří tři rozpětí ve výchozí řadě značek a napíše příznak, zprávu a výstrahu, jeden do každého rozsahu. Metody pro zápis příznaků, zpráv a výstrah jsou členy [třídy marker_series.](../profiling/marker-series-class.md) Konstruktor pro třídu [span](../profiling/span-class.md) vyžaduje `marker_series` objekt, takže každý rozsah je přidružen k určité řadě značek. A `span` končí, když je odstraněn.

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

4. Na řádku nabídek zvolte **Analyzovat**, **Vizualizér souběžnosti**, **Začít s aktuálním projektem,** chcete-li aplikaci spustit a zobrazit vizualizér souběžnosti. Následující obrázek znázorňuje tři rozsahy a tři značky v vizualizéru souběžnosti.

     ![Vizualizér souběžnosti se 3 značkami a výstrahami](../profiling/media/cvmarkersnative.png "CvMarkersNativní")

5. Přidejte kód pro vytvoření další, vlastní značky řady voláním konstruktoru, `marker_series` který má název řetězce pro značku řady.

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

6. Spusťte aktuální projekt pro zobrazení vizualizátoru souběžnosti. Dvě řady značek se zobrazí ve vlastních jízdních pruzích v zobrazení vláken. Následující obrázek znázorňuje dva nové rozsahy.

     ![Vizualizér souběžnosti se 3 vlastními značkami](../profiling/media/cvmarkerseriesnative.png "CvMarkerSeriesNative")

### <a name="to-use-visual-basic-or-c"></a>Použití jazyka Visual Basic nebo C\#

1. Přidejte podporu souběžnosti Visualizer SDK do vaší aplikace. Další informace naleznete v [tématu Souběžnost Visualizer SDK](../profiling/concurrency-visualizer-sdk.md).

2. Přidejte `using` `Imports` příkaz nebo pro sdk.

    ```vb
    Imports Microsoft.ConcurrencyVisualizer.Instrumentation
    ```

    ```csharp
    using Microsoft.ConcurrencyVisualizer.Instrumentation;
    ```

3. Přidejte kód, který vytvoří tři rozpětí na výchozí řadě značek a napíše příznak, zprávu a výstrahu, jeden do každého rozsahu. Objekt [Span](/previous-versions/hh694189(v=vs.140)) vytvoříte voláním `EnterSpan` statické metody. Chcete-li zapsat do výchozí řady, použijte statické metody zápisu [třídy Markers.](/previous-versions/hh694099(v=vs.140))

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

4. Na řádku nabídek zvolte **Analyzovat**, **Vizualizér souběžnosti**, **Začít s aktuálním projektem,** chcete-li aplikaci spustit a zobrazit vizualizér souběžnosti. Následující obrázek znázorňuje tři rozsahy a tři značky v zobrazení vláken vizualizéru souběžnosti.

     ![Vizualizér souběžnosti se značkami a výstrahami](../profiling/media/cvmarkersmanaged.png "CvMarkersManaged")

5. Přidejte kód pro vytvoření řady značek zákazníka pomocí statické metody [CreateMarkerSeries.](/previous-versions/hh694171(v=vs.140)) Třída [MarkerSeries](/previous-versions/hh694127(v=vs.140)) obsahuje metody pro vytváření rozsahů a zápisu příznaků, zpráv a výstrah.

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

6. Spusťte aktuální projekt pro zobrazení vizualizátoru souběžnosti. Tři řady značek se zobrazí ve vlastních jízdních pruzích v zobrazení vláken. Následující obrázek znázorňuje tři nové rozsahy.

     ![Vizualizér souběžnosti se 3 vlastními značkami](../profiling/media/cvmarkerseriesmanaged.png "CvMarkerSeriesManaged")

## <a name="see-also"></a>Viz také
- [SDK Vizualizéru souběžnosti](../profiling/concurrency-visualizer-sdk.md)
