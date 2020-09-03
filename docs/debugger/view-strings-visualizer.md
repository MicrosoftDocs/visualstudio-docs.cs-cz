---
title: Zobrazení řetězců v Vizualizér řetězců | Microsoft Docs
ms.date: 04/08/2019
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JavaScript
helpviewer_keywords:
- string visualizer
- visualizers, string
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 33e1cbd4b1c754498d7e2bd6c354e874ae8cdad5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72450396"
---
# <a name="view-strings-in-a-string-visualizer-in-visual-studio"></a>Zobrazení řetězců v Vizualizér řetězců v aplikaci Visual Studio

Při ladění v aplikaci Visual Studio můžete zobrazit řetězce s integrovaným vizualizérm řetězců. Vizualizér řetězců zobrazuje řetězce, které jsou příliš dlouhé pro datový Tip nebo okno ladicího programu. Může vám také usnadnit identifikaci chybných řetězců.

Vestavěný Vizualizér řetězců obsahuje možnosti pro prostý text, XML, HTML a JSON. Můžete také otevřít předdefinované vizualizace pro několik dalších typů, například [datovou sadu, DataTable a objekty DataView](../debugger/dataset-visualizer-dialog-box.md) , z okna **Automatické** hodnoty nebo jiného ladicího programu.

> [!NOTE]
> Pokud potřebujete zkontrolovat prvky uživatelského rozhraní XAML nebo WPF v vizualizér, přečtěte si nebo [Zkontrolujte vlastnosti XAML během ladění](../xaml-tools/inspect-xaml-properties-while-debugging.md) nebo [použijte Vizualizér stromu WPF](../debugger/how-to-use-the-wpf-tree-visualizer.md).

## <a name="open-a-string-visualizer"></a>Otevřete Vizualizér řetězců

Chcete-li otevřít Vizualizér řetězců, je nutné pozastavit během ladění. Najeďte myší na proměnnou, která má hodnotu řetězce prostého textu, XML, HTML nebo JSON, a vyberte ikonu lupy ![VisualizerIcon](../debugger/media/dbg-tips-visualizer-icon.png "Ikona Vizualizátoru").

![Otevřete Vizualizér řetězců](../debugger/media/dbg-tips-string-visualizers.png "Otevřít Vizualizér řetězců")

## <a name="view-string-visualizer-data"></a>Zobrazit data Vizualizér řetězců

V okně Vizualizér řetězců se v poli **výraz** zobrazuje proměnná nebo výraz, na který přejedete, a pole **hodnota** zobrazuje hodnotu řetězce.

Prázdná **hodnota** znamená, že zvolený Vizualizér nemůže rozpoznat řetězec. Například **Vizualizér XML** zobrazuje prázdnou **hodnotu** pro textový řetězec bez značek XML nebo řetězec JSON.

Pokud chcete zobrazit řetězce, které vybraný Vizualizér nemůže rozpoznat, vyberte **Vizualizér textu**. **Vizualizér textu** zobrazuje prostý text.

### <a name="view-json-string-data"></a>Zobrazit data řetězce JSON

Ve správném formátu se zdá, že v Vizualizér JSON vypadá podobně jako na následujícím obrázku. Poškozený kód JSON může zobrazit ikonu chyby (nebo prázdné, pokud není rozpoznán). Chcete-li identifikovat chybu JSON, zkopírujte a vložte řetězec do nástroje JSON linting, jako je například [JSLint](https://www.jslint.com/).

![Vizualizér řetězců JSON](../debugger/media/dbg-tips-string-visualizer-json.png "Vizualizér řetězců JSON")

### <a name="view-xml-string-data"></a>Zobrazit data řetězce XML

Ve správném formátu se řetězec XML podobá následující ilustraci v Vizualizér XML. Nesprávně vytvořený kód XML může být zobrazen bez značek XML nebo prázdný, pokud nebyl rozpoznán.

![Vizualizér řetězců XML](../debugger/media/dbg-string-visualizers-xml.png "Vizualizér řetězců XML")

### <a name="view-html-string-data"></a>Zobrazit data řetězce HTML

Dobře vytvořený řetězec HTML se zobrazí, jako kdyby byl vykreslen v prohlížeči, jak je znázorněno na následujícím obrázku. Nesprávně vytvořený kód HTML se může zobrazit jako prostý text.

![Vizualizér řetězců HTML](../debugger/media/dbg-string-visualizers-html.png "Vizualizér řetězců HTML")

## <a name="see-also"></a>Viz také

- [Vytváření vlastních vizualizací (C#, Visual Basic)](../debugger/create-custom-visualizers-of-data.md)
- [Vizualizace dat v Visual Studio pro Mac](/visualstudio/mac/data-visualizations)