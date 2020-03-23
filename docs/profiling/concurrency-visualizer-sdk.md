---
title: Vizualizér souběžnosti SDK | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.sdk.about
ms.assetid: 4b22cdf9-59b1-4c88-a6d8-1644a4a11e08
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cb48733f84dcf484d2c2d7ffb18e838faae07ab0
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "72911198"
---
# <a name="concurrency-visualizer-sdk"></a>SDK Vizualizéru souběžnosti
Můžete instrumentovat zdrojový kód pomocí souběžnosti Vizualizátor SDK zobrazit další informace v souběžnosti Vizualizátor. Další data můžete přidružit k fázím a událostem v kódu. Tyto další vizualizace jsou označovány jako *značky*.  Úvodní návod naleznete v tématu [Introducing the Concurrency Visualizer SDK](https://blogs.msdn.microsoft.com/visualizeparallel/2011/10/17/introducing-the-concurrency-visualizer-sdk/).

## <a name="properties"></a>Vlastnosti
 Příznaky, rozpětí a zprávy mají dvě vlastnosti: kategorie a důležitost. V dialogovém okně [Upřesnit nastavení](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md) můžete tyto vlastnosti použít k filtrování sady zobrazených značek. Kromě toho tyto vlastnosti ovlivňují vizuální znázornění značek. Například velikost příznaků se používá k reprezentaci důležitosti. Kromě toho se barva používá k označení kategorie.

## <a name="basic-usage"></a>Základní použití
 Vizualizér souběžnosti zpřístupňuje výchozího zprostředkovatele, který můžete použít ke generování značek. Zprostředkovatel je již registrována společně s Akcecurrency Visualizer a není třeba dělat nic jiného, aby se značky zobrazí v ui.

### <a name="c-and-visual-basic"></a>C# a Visual Basic
 V jazyce C#, Visual basic a dalším spravovaném kódu použijte výchozího zprostředkovatele voláním metod ve třídě [Markers.](/previous-versions/hh694099(v=vs.140)) Poskytuje čtyři metody pro generování značek: [WriteFlag](/previous-versions/hh694185%28v%3dvs.140%29), [EnterSpan](/previous-versions/hh694205(v=vs.140)), [WriteMessage](/previous-versions/hh694161(v=vs.140))a [WriteAlert](/previous-versions/hh694180(v=vs.140)). Existuje více přetížení pro tyto funkce, v závislosti na tom, zda chcete použít výchozí hodnoty pro vlastnosti.  Nejjednodušší přetížení trvá pouze parametr řetězce, který určuje popis události. Popis se zobrazí v sestavách vizualizéru souběžnosti.

##### <a name="to-add-sdk-support-to-a-c-or-visual-basic-project"></a>Přidání podpory sady SDK do projektu jazyka C# nebo Visual Basic

1. Na řádku nabídek zvolte **Analyzovat**, **Vizualizér souběžnosti**, **Přidat sdk k projektu**.

2. Vyberte projekt, ve kterém chcete získat přístup k sdk, a pak zvolte tlačítko **Přidat sdk do vybraného projektu.**

3. Přidejte importy nebo pomocí příkazu do kódu.

    ```csharp
    using Microsoft.ConcurrencyVisualizer.Instrumentation;
    ```

    ```VB
    Imports Microsoft.ConcurrencyVisualizer.Instrumentation
    ```

### <a name="c"></a>C++
 V jazyce C++ vytvořte objekt [třídy marker_series](../profiling/marker-series-class.md) a použijte jej k volání funkcí.  Třída `marker_series` zpřístupňuje tři funkce pro generování značek, [marker_series::write_flag Metoda](../profiling/marker-series-write-flag-method.md), [marker_series::write_message Metoda](../profiling/marker-series-write-message-method.md)a [marker_series::write_alert Metoda](../profiling/marker-series-write-alert-method.md).

##### <a name="to-add-sdk-support-to-a-c-or-c-project"></a>Přidání podpory sady SDK do projektu jazyka C++ nebo C

1. Na řádku nabídek zvolte **Analyzovat**, **Vizualizér souběžnosti**, **Přidat sdk k projektu**.

2. Vyberte projekt, ve kterém chcete získat přístup k sdk, a pak zvolte tlačítko **Přidat sdk do vybraného projektu.**

3. Pro C++ `cvmarkersobj.h`zahrnout . Pro C, `cvmarkers.h`včetně .

4. Přidejte příkaz using do kódu.

    ```cpp
    using namespace Concurrency::diagnostic;
    ```

5. Vytvořte `marker_series` objekt a předajte jej konstruktoru. `span`

    ```C++

    marker_series mySeries;
    span s(mySeries, _T("Span description"));

    ```

## <a name="custom-usage"></a>Vlastní využití
 Pro pokročilé scénáře souběžnost Vizualizátor SDK zveřejňuje větší kontrolu.  Dva hlavní koncepty jsou spojeny s pokročilejšíscénáře: zprostředkovatelé značek a značky řady. Zprostředkovatelé značek jsou různí poskytovatelé ETW (každý má jiný identifikátor GUID). Marker ové řady jsou sériové kanály událostí, které jsou generovány jedním zprostředkovatelem. Můžete je použít k uspořádání událostí, které jsou generovány poskytovatelem značky.

#### <a name="to-use-a-new-marker-provider-in-a-c-or-visual-basic-project"></a>Použití nového zprostředkovatele značek v projektu jazyka C# nebo Visual Basic

1. Vytvořte objekt [MarkerWriter.](/previous-versions/hh694138(v=vs.140))  Konstruktor má identifikátor GUID.

2. Chcete-li zaregistrovat zprostředkovatele, otevřete dialogové okno Vizualizér [upřesňujících nastavení](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md) souběžnosti.  Vyberte kartu **Značky** a pak zvolte tlačítko **Přidat nového zprostředkovatele.** V dialogovém okně [Upřesnit nastavení](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md) zadejte identifikátor GUID, který byl použit k vytvoření zprostředkovatele, a popis zprostředkovatele.

#### <a name="to-use-a-new-marker-provider-in-a-c-or-c-project"></a>Použití nového zprostředkovatele značek v projektu c++ nebo C

1. Pomocí `CvInitProvider` funkce můžete inicializovat PCV_PROVIDER.  Konstruktor má identifikátor GUID*\*a PCV_PROVIDER .

2. Chcete-li poskytovatele zaregistrovat, otevřete dialogové okno [Upřesnit nastavení.](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md)  Vyberte kartu **Značky** a pak zvolte tlačítko **Přidat nového zprostředkovatele.** V tomto dialogovém okně zadejte identifikátor GUID, který byl použit k vytvoření zprostředkovatele, a popis zprostředkovatele.

#### <a name="to-use-a-marker-series-in-a-c-or-visual-basic-project"></a>Použití řady značek v projektu jazyka C# nebo Visual Basic

1. Chcete-li použít novou [MarkerSeries](/previous-versions/hh694127(v=vs.140)), nejprve ji vytvořte pomocí objektu [MarkerWriter](/previous-versions/hh694138(v=vs.140)) a pak vygenerujte události značky přímo z nové řady.

    ```csharp
    MarkerSeries series1 = myMarkerWriter.CreateMarkerSeries("Series 1");
    series1.WriteFlag("My flag");
    ```

    ```VB
    Dim series1 As New myMarkerWriter.CreateMarkerSeries("Series 1")
    series1.WriteFlag("My flag")
    ```

#### <a name="to-use-a-marker-series-in-a-c-project"></a>Použití řady značek v projektu c++

1. Vytvořte `marker_series` objekt.  Můžete generovat události z této nové řady.

    ```scr
    marker_series series;
    series.write_flag(_T("Hello world!"));
    ```

#### <a name="to-use-a-marker-series-in-a-c-project"></a>Použití řady značek v projektu C

1. Pomocí `CvCreateMarkerSeries` funkce vytvořte PCV_MARKERSERIES.

    ```C++
    PCV_MARKERSERIES series;
    CvCreatemarkerSeries(myProvider, _T("My Series"), &series);
    CvWriteFlag(series, _T("Writing a flag"));
    ```

## <a name="see-also"></a>Viz také

|Nadpis|Popis|
|-----------|-----------------|
|[Odkaz na knihovnu C++](../profiling/cpp-library-reference.md)|Popisuje rozhraní CONCURRENCY Visualizer API pro C++.|
|[Odkaz na knihovnu C](../profiling/c-library-reference.md)|Popisuje rozhraní API vizualizéru souběžnosti pro C.|
|[Instrumentation](/previous-versions/hh694104(v=vs.140))|Popisuje rozhraní CONCURRENCY Visualizer API pro spravovaný kód.|
|[Vizualizér souběžnosti](../profiling/concurrency-visualizer.md)|Referenční informace pro zobrazení a sestavy profilování datových souborů, které jsou generovány pomocí metody souběžnosti a které obsahují data spuštění vlákna.|