---
title: Dialogové okno Vizualizér řetězců | Microsoft Docs
ms.date: 10/10/2018
ms.custom: seoapril2019
ms.topic: reference
f1_keywords:
- vs.debug.stringviewer
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JavaScript
helpviewer_keywords:
- string visualizer
- visualizers, string
ms.assetid: 080fd8f1-72b0-461f-8451-3c84d5dc51df
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 10e7e50ffc0cb61bd036bef65c554e8147eecc09
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/16/2019
ms.locfileid: "72430831"
---
# <a name="string-visualizer-dialog-box"></a>Dialogové okno vizualizéru řetězce

Při ladění v aplikaci Visual Studio můžete zobrazit řetězce s integrovaným vizualizérm řetězců. Vizualizér řetězců zobrazuje řetězce, které jsou příliš dlouhé pro datový Tip nebo okno ladicího programu. Může vám také usnadnit identifikaci chybných řetězců.

Vestavěný Vizualizér řetězců obsahuje možnosti pro prostý text, XML, HTML a JSON. Můžete také otevřít předdefinované vizualizace pro několik dalších typů, například [datovou sadu, DataTable a objekty DataView](../debugger/dataset-visualizer-dialog-box.md) , z okna **Automatické** hodnoty nebo jiného ladicího programu.

> [!NOTE]
> Pokud potřebujete zkontrolovat prvky uživatelského rozhraní XAML nebo WPF v vizualizér, přečtěte si nebo [Zkontrolujte vlastnosti XAML během ladění](../xaml-tools/inspect-xaml-properties-while-debugging.md) nebo [použijte Vizualizér stromu WPF](../debugger/how-to-use-the-wpf-tree-visualizer.md).

Chcete-li otevřít Vizualizér řetězců, je nutné pozastavit během ladění. Najeďte myší na proměnnou, která má hodnotu řetězce prostého textu, XML, HTML nebo JSON, a vyberte ikonu lupy ![VisualizerIcon](../debugger/media/dbg-tips-visualizer-icon.png "Ikona Vizualizátoru").

## <a name="uielement-list"></a>UIElement – seznam

V poli **výrazu** se zobrazuje proměnná nebo výraz, na který ukazatel nahráváte.

**Hodnota** pole zobrazuje hodnotu řetězce. Prázdná **hodnota** znamená, že zvolený Vizualizér nemůže rozpoznat řetězec. Například **Vizualizér XML** zobrazuje prázdnou **hodnotu** pro textový řetězec bez značek XML nebo řetězec JSON. Pokud chcete zobrazit řetězce, které vybraný Vizualizér nemůže rozpoznat, vyberte místo toho **Vizualizér textu** . **Vizualizér textu** zobrazuje prostý text.

### <a name="json-string-data"></a>Data řetězce JSON

Ve správném formátu se zdá, že v Vizualizér JSON vypadá podobně jako na následujícím obrázku. Poškozený kód JSON může zobrazit ikonu chyby (nebo prázdné, pokud není rozpoznán). Chcete-li identifikovat chybu JSON, zkopírujte a vložte řetězec do nástroje JSON linting, jako je například [JSLint](https://www.jslint.com/).

![Vizualizér řetězců JSON](../debugger/media/dbg-tips-string-visualizer-json.png "Vizualizér řetězců JSON")

### <a name="xml-string-data"></a>Data řetězce XML

Ve správném formátu se řetězec XML podobá následující ilustraci v Vizualizér XML. Nesprávně vytvořený kód XML může být zobrazen bez značek XML nebo prázdný, pokud nebyl rozpoznán.

![Vizualizér řetězců XML](../debugger/media/dbg-string-visualizers-xml.png "Vizualizér řetězců XML")

### <a name="html-string-data"></a>Data řetězce HTML

Dobře vytvořený řetězec HTML se zobrazí, jako kdyby byl vykreslen v prohlížeči, jak je znázorněno na následujícím obrázku. Nesprávně vytvořený kód HTML se může zobrazit jako prostý text.

![Vizualizér řetězců HTML](../debugger/media/dbg-string-visualizers-html.png "Vizualizér řetězců HTML")

## <a name="see-also"></a>Viz také:

- [Vytvořit vlastní nástroje pro vizualizaci (C#, Visual Basic)](../debugger/create-custom-visualizers-of-data.md)
- [Vizualizace dat v Visual Studio pro Mac](/visualstudio/mac/data-visualizations)