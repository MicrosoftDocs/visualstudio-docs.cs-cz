---
title: SDK Vizualizéru souběžnosti | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.cv.sdk.about
ms.assetid: 4b22cdf9-59b1-4c88-a6d8-1644a4a11e08
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d98a5383a330242110bef860b9dc19a2fb6bef87
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51754834"
---
# <a name="concurrency-visualizer-sdk"></a>SDK Vizualizéru souběžnosti
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Můžete použít zdrojový kód pomocí sada Vizualizátor souběžnosti SDK k zobrazení dalších informací ve vizualizátoru souběžnosti. Doplňující data můžete přidružit fází a události ve vašem kódu. Tyto další vizualizace, jsou označovány jako *značky*.  Úvodní prohlídka, naleznete v tématu [Představujeme sada Vizualizátor souběžnosti SDK](http://go.microsoft.com/fwlink/?LinkId=235405).  
  
## <a name="properties"></a>Vlastnosti  
 Příznaky, rozsahy a zprávy mají dvě vlastnosti: kategorie a důležitosti. V [Upřesnit nastavení](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md) dialogové okno, tyto vlastnosti můžete použít k filtrování sady značek, které jsou zobrazeny. Kromě toho tyto vlastnosti ovlivňují vizuální reprezentaci značky. Například velikost příznaky se používá k reprezentování význam. Kromě toho barva se používá k označení kategorie.  
  
## <a name="basic-usage"></a>Základní informace o využití  
 Vizualizátor souběžnosti zpřístupňuje výchozího zprostředkovatele, který můžete použít ke generování značky. Zprostředkovatel je již zaregistrována spolu s Vizualizátorem souběžnosti a nemusíte dělat nic dalšího provádět značky se zobrazí v uživatelském rozhraní.  
  
### <a name="c-and-visual-basic"></a>C# a Visual Basic  
 V C#, Visual basic a dalších spravovaný kód, pomocí výchozího zprostředkovatele voláním <xref:Microsoft.ConcurrencyVisualizer.Instrumentation.Markers>. Poskytuje čtyři funkce pro generování značek: <xref:Microsoft.ConcurrencyVisualizer.Instrumentation.Markers.WriteFlag%2A>, <xref:Microsoft.ConcurrencyVisualizer.Instrumentation.Markers.EnterSpan%2A>, <xref:Microsoft.ConcurrencyVisualizer.Instrumentation.Markers.WriteMessage%2A>, a <xref:Microsoft.ConcurrencyVisualizer.Instrumentation.Markers.WriteAlert%2A>. Existuje více přetížení pro tyto funkce, v závislosti na tom, jestli chcete použít výchozí hodnoty pro vlastnosti.  Nejjednodušší přetížení trvá jenom řetězcový parametr, který určuje popis události. Popis se zobrazí v sestavách Vizualizátor souběžnosti.  
  
##### <a name="to-add-sdk-support-to-a-c-or-visual-basic-project"></a>Chcete-li přidat podporu sady SDK do projektu C# nebo Visual Basic  
  
1.  V panelu nabídky zvolte **analyzovat**, **Vizualizátor souběžnosti**, **přidat sadu SDK do projektu**.  
  
2.  Vyberte projekt, ve kterém chcete pro přístup k sadě SDK a klikněte na tlačítko **přidat sadu SDK do projektu vybrané** tlačítko.  
  
3.  Přidáte imports nebo using příkazu do vašeho kódu.  
  
    ```csharp  
    using Microsoft.ConcurrencyVisualizer.Instrumentation;  
    ```  
  
    ```vb  
    Imports Microsoft.ConcurrencyVisualizer.Instrumentation  
    ```  
  
### <a name="c"></a>C++  
 V jazyce C++, vytvořit [marker_series – třída](../profiling/marker-series-class.md) objektu a použít jej k vyvolání funkce.  `marker_series` Třída zveřejňuje tři funkce pro generování značek, [marker_series::write_flag – metoda](../profiling/marker-series-write-flag-method.md), [marker_series::write_message – metoda](../profiling/marker-series-write-message-method.md)a [marker_ Metoda Series::write_alert](../profiling/marker-series-write-alert-method.md).  
  
##### <a name="to-add-sdk-support-to-a-c-or-c-project"></a>Chcete-li přidat podporu sady SDK do projektu jazyka C++ i c.  
  
1.  V panelu nabídky zvolte **analyzovat**, **Vizualizátor souběžnosti**, **přidat sadu SDK do projektu**.  
  
2.  Vyberte projekt, ve kterém chcete pro přístup k sadě SDK a klikněte na tlačítko **přidat sadu SDK do projektu vybrané** tlačítko.  
  
3.  Pro jazyk C++, zahrnují `cvmarkersobj.h`. Pro jazyk C, zahrnují `cvmarkers.h`.  
  
4.  Přidat sadu pomocí příkazu do vašeho kódu.  
  
    ```  
    using namespace Concurrency::diagnostic;  
    ```  
  
5.  Vytvořit `marker_series` objektu a předejte jej `span` konstruktoru.  
  
    ```cpp  
  
    marker_series mySeries;  
    span s(mySeries, _T("Span description"));  
  
    ```  
  
## <a name="custom-usage"></a>Vlastní využití  
 Pro pokročilé scénáře sada Vizualizátor souběžnosti SDK zpřístupňuje větší kontrolu.  Dva hlavní koncepty, které jsou spojeny s pokročilejší scénáře: kteří poskytovatelé značek a značky řady. Kteří poskytovatelé značek jsou různých zprostředkovatelů trasování událostí pro Windows (každý má jiný identifikátor GUID). Řada značky jsou sériové kanály událostí, které jsou generovány pomocí jednoho poskytovatele. Můžete využít k uspořádání událostí, které jsou generovány pomocí poskytovatele značek.  
  
#### <a name="to-use-a-new-marker-provider-in-a-c-or-visual-basic-project"></a>Použití nového poskytovatele značek v projektu C# nebo Visual Basic  
  
1.  Vytvoření <xref:Microsoft.ConcurrencyVisualizer.Instrumentation.MarkerWriter> objektu.  Konstruktor přijme identifikátor GUID.  
  
2.  Chcete-li registraci poskytovatele, otevřete Vizualizátor souběžnosti [Upřesnit nastavení](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md) dialogové okno.  Vyberte **značky** kartě a klikněte na tlačítko **přidat nového poskytovatele** tlačítko. V [Upřesnit nastavení](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md) dialogového okna zadejte identifikátor GUID, který byl použit k vytvoření poskytovatele a popis poskytovatele.  
  
#### <a name="to-use-a-new-marker-provider-in-a-c-or-c-project"></a>Použití nového poskytovatele značek v projektu jazyka C++ i c.  
  
1.  Použití `CvInitProvider` funkce lze inicializovat PCV_PROVIDER.  Konstruktor přijme identifikátor GUID * a PCV_PROVIDER\*.  
  
2.  Chcete-li registraci poskytovatele, otevřete [Upřesnit nastavení](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md) dialogové okno.  Vyberte **značky** kartě a klikněte na tlačítko **přidat nového poskytovatele** tlačítko. V tomto dialogovém okně zadejte identifikátor GUID, který byl použit k vytvoření poskytovatele a popis poskytovatele.  
  
#### <a name="to-use-a-marker-series-in-a-c-or-visual-basic-project"></a>Použití značek řady v projektu C# nebo Visual Basic  
  
1.  Použití nového <xref:Microsoft.ConcurrencyVisualizer.Instrumentation.MarkerSeries>, nejprve ji vytvořit pomocí <xref:Microsoft.ConcurrencyVisualizer.Instrumentation.MarkerWriter> objekt a potom generovat značky události přímo z nové řady.  
  
    ```csharp  
    MarkerSeries series1 = myMarkerWriter.CreateMarkerSeries(″Series 1″);  
    series1.WriteFlag(″My flag″);  
    ```  
  
    ```vb  
    Dim series1 As New myMarkerWriter.CreateMarkerSeries(″Series 1″)  
    series1.WriteFlag(″My flag″)  
    ```  
  
#### <a name="to-use-a-marker-series-in-a-c-project"></a>Použití značek řady projektu v jazyce C++  
  
1.  Vytvoření `marker_series` objektu.  Generování událostí z této nové řady.  
  
    ```scr  
    marker_series series;  
    series.write_flag(_T("Hello world!"));  
    ```  
  
#### <a name="to-use-a-marker-series-in-a-c-project"></a>Použití značek řady v projektu jazyka C  
  
1.  Použití `CvCreateMarkerSeries` funkci, která vytvoří PCV_MARKERSERIES.  
  
    ```cpp  
    PCV_MARKERSERIES series;  
    CvCreatemarkerSeries(myProvider, _T("My Series"), &series);  
    CvWriteFlag(series, _T("Writing a flag"));  
    ```  
  
## <a name="related-topics"></a>Související témata  
  
|Název|Popis|  
|-----------|-----------------|  
|[Referenční dokumentace knihoven jazyka C++](../profiling/cpp-library-reference.md)|Popisuje rozhraní API Vizualizéru souběžnosti jazyka C++.|  
|[Referenční dokumentace knihoven jazyka C](../profiling/c-library-reference.md)|Popisuje rozhraní API Vizualizéru souběžnosti pro C.|  
|<xref:Microsoft.ConcurrencyVisualizer.Instrumentation>|Popisuje rozhraní API Vizualizéru souběžnosti pro spravovaný kód.|  
|[Vizualizér souběžnosti](../profiling/concurrency-visualizer.md)|Referenční informace o zobrazeních a sestavách profilace datových souborů, které jsou generovány pomocí za použití metody souběžnosti a, které zahrnují data spouštění vlákna.|



