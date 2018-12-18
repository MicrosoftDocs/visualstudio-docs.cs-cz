---
title: SDK Vizualizéru souběžnosti | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.sdk.about
ms.assetid: 4b22cdf9-59b1-4c88-a6d8-1644a4a11e08
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c02959f30f89b8f7c79527026404099a4452a827
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2018
ms.locfileid: "34691183"
---
# <a name="concurrency-visualizer-sdk"></a>SDK Vizualizéru souběžnosti
Pomocí sady SDK Vizualizéru souběžnosti zobrazíte další informace v Concurrency Visualizer můžou instrumentovat vašeho zdrojového kódu. Další data můžete přidružit fáze a události v kódu. Tyto další vizualizace se označují jako *značek*.  Úvodní prohlídka, najdete v části [představení SDK Vizualizéru souběžnosti](http://go.microsoft.com/fwlink/?LinkId=235405).  
  
## <a name="properties"></a>Vlastnosti  
 Příznaky, rozsahy a zprávy, které mají dvě vlastnosti: kategorie a význam. V [Upřesnit nastavení](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md) dialogové okno, tyto vlastnosti můžete použít pro filtrování sady značek, které jsou zobrazeny. Kromě toho tyto vlastnosti ovlivňují vizuální reprezentace značek. Například velikost příznaky se používá k reprezentování význam. Kromě toho je barva slouží k určení kategorie.  
  
## <a name="basic-usage"></a>Základní informace o využití  
 Vizualizér souběžnosti zpřístupní výchozího zprostředkovatele, který můžete použít ke generování značek. Zprostředkovatel je již zaregistrována spolu s vizualizér souběžnosti a nemusíte dělat žádné další kroky, aby se zobrazí v uživatelském rozhraní značek.  
  
### <a name="c-and-visual-basic"></a>C# a Visual Basic  
 V C#, Visual basic a dalších spravovaného kódu, použít výchozího poskytovatele voláním <xref:Microsoft.ConcurrencyVisualizer.Instrumentation.Markers>. Poskytuje čtyři funkce pro generování značek: <xref:Microsoft.ConcurrencyVisualizer.Instrumentation.Markers.WriteFlag%2A>, <xref:Microsoft.ConcurrencyVisualizer.Instrumentation.Markers.EnterSpan%2A>, <xref:Microsoft.ConcurrencyVisualizer.Instrumentation.Markers.WriteMessage%2A>, a <xref:Microsoft.ConcurrencyVisualizer.Instrumentation.Markers.WriteAlert%2A>. Existuje více přetížení pro tyto funkce, v závislosti na tom, jestli chcete použít výchozí hodnoty pro vlastnosti.  Nejjednodušší přetížení trvá pouze parametr řetězec, který určuje popis události. Popis se zobrazí v sestavách vizualizér souběžnosti.  
  
##### <a name="to-add-sdk-support-to-a-c-or-visual-basic-project"></a>Chcete-li přidat podporu SDK do projektu C# nebo Visual Basic  
  
1.  Na řádku nabídek zvolte **analyzovat**, **vizualizér souběžnosti**, **přidat sadu SDK do projektu**.  
  
2.  Vyberte projekt, ve kterém chcete přístup k sadě SDK a potom zvolte **přidat sadu SDK do projektu vybrané** tlačítko.  
  
3.  Přidáte importy nebo pomocí příkazu do vašeho kódu.  
  
    ```csharp  
    using Microsoft.ConcurrencyVisualizer.Instrumentation;  
    ```  
  
    ```VB  
    Imports Microsoft.ConcurrencyVisualizer.Instrumentation  
    ```  
  
### <a name="c"></a>C++  
 V jazyce C++, vytvoření [marker_series – třída](../profiling/marker-series-class.md) objektu a použít ho k volání funkce.  `marker_series` Třída zpřístupňuje tři funkce pro generování značek, [marker_series::write_flag – metoda](../profiling/marker-series-write-flag-method.md), [marker_series::write_message – metoda](../profiling/marker-series-write-message-method.md)a [značka_ Series::write_alert metoda](../profiling/marker-series-write-alert-method.md).  
  
##### <a name="to-add-sdk-support-to-a-c-or-c-project"></a>Chcete-li přidat podporu SDK do projektu C++ nebo C  
  
1.  Na řádku nabídek zvolte **analyzovat**, **vizualizér souběžnosti**, **přidat sadu SDK do projektu**.  
  
2.  Vyberte projekt, ve kterém chcete přístup k sadě SDK a potom zvolte **přidat sadu SDK do projektu vybrané** tlačítko.  
  
3.  Pro jazyk C++, zahrnují `cvmarkersobj.h`. Pro jazyk C zahrnují `cvmarkers.h`.  
  
4.  Přidat pomocí příkazu do vašeho kódu.  
  
    ```cpp  
    using namespace Concurrency::diagnostic;  
    ```  
  
5.  Vytvoření `marker_series` objektu a předejte ji do `span` konstruktor.  
  
    ```C++  
  
    marker_series mySeries;  
    span s(mySeries, _T("Span description"));  
  
    ```  
  
## <a name="custom-usage"></a>Vlastní použití  
 SDK Vizualizéru souběžnosti pro pokročilé scénáře, zpřístupní větší kontrolu.  Dva hlavní koncepty, které jsou přidružené pokročilejší scénáře: zprostředkovatelé značky a značky řady. Zprostředkovatelé značky jsou různé zprostředkovatele trasování událostí pro Windows (každá má jiný identifikátor GUID). Řada značky jsou sériové kanály událostí, které jsou generovány nástrojem jednoho poskytovatele. Můžete je používat k uspořádání události, které se generují poskytovatelem značky.  
  
#### <a name="to-use-a-new-marker-provider-in-a-c-or-visual-basic-project"></a>K použití nového poskytovatele značky v projektu C# nebo Visual Basic  
  
1.  Vytvoření <xref:Microsoft.ConcurrencyVisualizer.Instrumentation.MarkerWriter> objektu.  Konstruktor trvá identifikátor GUID.  
  
2.  K registraci poskytovatele, otevřete vizualizér souběžnosti [Upřesnit nastavení](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md) dialogové okno.  Vyberte **značek** a pak klikněte na příkaz **přidat nového poskytovatele** tlačítko. V [Upřesnit nastavení](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md) dialogovém okně zadejte identifikátor GUID, který byl použit k vytvoření zprostředkovatele a popis zprostředkovatele.  
  
#### <a name="to-use-a-new-marker-provider-in-a-c-or-c-project"></a>K použití nového poskytovatele značky v projektu C++ nebo C  
  
1.  Použití `CvInitProvider` funkce k chybě při inicializaci PCV_PROVIDER.  Konstruktor přijímá GUID * a PCV_PROVIDER\*.  
  
2.  K registraci poskytovatele, otevřete [Upřesnit nastavení](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md) dialogové okno.  Vyberte **značek** a pak klikněte na příkaz **přidat nového poskytovatele** tlačítko. Toto dialogové okno Zadejte identifikátor GUID, který byl použit k vytvoření zprostředkovatele a popis zprostředkovatele.  
  
#### <a name="to-use-a-marker-series-in-a-c-or-visual-basic-project"></a>K použití řadu značky v projektu C# nebo Visual Basic  
  
1.  Použít novou <xref:Microsoft.ConcurrencyVisualizer.Instrumentation.MarkerSeries>, nejprve vytvořit pomocí <xref:Microsoft.ConcurrencyVisualizer.Instrumentation.MarkerWriter> objektu a pak generovat události značky přímo z nové řady.  
  
    ```csharp  
    MarkerSeries series1 = myMarkerWriter.CreateMarkerSeries("Series 1");  
    series1.WriteFlag("My flag");  
    ```  
  
    ```VB  
    Dim series1 As New myMarkerWriter.CreateMarkerSeries("Series 1")  
    series1.WriteFlag("My flag")  
    ```  
  
#### <a name="to-use-a-marker-series-in-a-c-project"></a>Použití řadu značky v projektu jazyka C++  
  
1.  Vytvoření `marker_series` objektu.  Události můžete vygenerovat z této série nové.  
  
    ```scr  
    marker_series series;  
    series.write_flag(_T("Hello world!"));  
    ```  
  
#### <a name="to-use-a-marker-series-in-a-c-project"></a>K použití řadu značky v projektu jazyka C  
  
1.  Použití `CvCreateMarkerSeries` funkce k vytvoření PCV_MARKERSERIES.  
  
    ```C++  
    PCV_MARKERSERIES series;  
    CvCreatemarkerSeries(myProvider, _T("My Series"), &series);  
    CvWriteFlag(series, _T("Writing a flag"));  
    ```  
  
## <a name="see-also"></a>Viz také:  
  
|Název|Popis|  
|-----------|-----------------|  
|[Referenční dokumentace knihoven jazyka C++](../profiling/cpp-library-reference.md)|Popisuje vizualizér souběžnosti rozhraní API jazyka C++.|  
|[Referenční dokumentace knihoven jazyka C](../profiling/c-library-reference.md)|Popisuje vizualizér souběžnosti rozhraní API pro C.|  
|<xref:Microsoft.ConcurrencyVisualizer.Instrumentation>|Popisuje rozhraní API Vizualizéru souběžnosti pro spravovaný kód.|  
|[Vizualizér souběžnosti](../profiling/concurrency-visualizer.md)|Referenční informace pro zobrazení a sestavy profilace datové soubory, které jsou generovány pomocí metoda souběžného zpracování, které obsahují data provádění přístup z více vláken.|