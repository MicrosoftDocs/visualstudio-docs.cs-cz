---
title: Zobrazit řetězců ve vizualizéru řetězce | Dokumentace Microsoftu
ms.custom: ''
ms.date: 10/10/2018
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.stringviewer
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
- SQL
helpviewer_keywords:
- string visualizer
- visualizers, string
ms.assetid: 080fd8f1-72b0-461f-8451-3c84d5dc51df
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: eb447a29ea669dbea3a68312884760f8984cc2de
ms.sourcegitcommit: dd839de3aa24ed7cd69f676293648c6c59c6560a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/27/2018
ms.locfileid: "52388553"
---
# <a name="view-strings-in-a-string-visualizer-in-visual-studio"></a>Zobrazení řetězců ve vizualizéru řetězce v sadě Visual Studio

Při ladění v sadě Visual Studio, můžete zobrazit řetězce pomocí vizualizéru integrované řetězec. Vizualizér řetězce zobrazí řetězce, které jsou příliš dlouhé pro okno datový tip nebo ladicí program. Může také pomoct identifikovat poškozený řetězce.

Vizualizér integrované řetězec obsahuje prostý text, XML, HTML a JSON možnosti. Vizualizéry pro několik jiných typů, jako je například WPF objektů lze také otevřít z **automatické hodnoty** nebo dalších oknech ladicího programu.

## <a name="open-a-string-visualizer"></a>Otevřete vizualizéru řetězce

Otevřete vizualizéru řetězce, musí být pozastaveno během ladění. Podržte ukazatel myši nad proměnnou, která obsahuje prostý text, XML, HTML nebo JSON řetězcová hodnota a vyberte ikonu lupy ![VisualizerIcon](../debugger/media/dbg-tips-visualizer-icon.png "Vizualizéru ikonu").

![Otevřete vizualizéru řetězce](../debugger/media/dbg-tips-string-visualizers.png "řetězec pro otevření vizualizéru")

## <a name="view-string-visualizer-data"></a>Zobrazení data vizualizéru řetězce

V okně vizualizéru řetězce **výraz** poli se zobrazí proměnné nebo výrazu najedete, a **hodnotu** pole zobrazí hodnotu řetězce.

Prázdnou hodnotu **hodnotu** znamená, že nemůže rozpoznat zvolené vizualizéru řetězce. Například **XML vizualizér** zobrazí prázdnou hodnotu **hodnotu** pro textový řetězec s žádné značky XML nebo řetězec formátu JSON.

K zobrazení řetězce, které nemůže rozpoznat zvolené vizualizéru, zvolte **Vizualizátor textu**. **Vizualizátor textu** zobrazuje prostý text.

### <a name="view-json-string-data"></a>Data řetězce JSON zobrazení

Podobně jako na následujícím obrázku v JSON visualizér se zobrazí řetězec JSON ve správném formátu. Nesprávný formát JSON se může zobrazit ikona chyby (nebo prázdné, pokud nebyl rozpoznán). K identifikaci chyby JSON, zkopírujte a vložte řetězec do nástroje linting JSON, jako [JSLint](https://www.jslint.com/).

![Vizualizér řetězce JSON](../debugger/media/dbg-tips-string-visualizer-json.png "vizualizéru řetězce JSON")

### <a name="view-xml-string-data"></a>Zobrazení dat řetězec XML

Podobně jako na následujícím obrázku ve vizualizátoru XML se zobrazí řetězec XML ve správném formátu. Pokud nebyl rozpoznán se může zobrazit nesprávně vytvořeným kódem XML bez značek XML nebo prázdný.

![XML vizualizér řetězce](../debugger/media/dbg-string-visualizers-xml.png "XML vizualizér řetězce")

### <a name="view-html-string-data"></a>Data řetězce zobrazení HTML

Zobrazí se ve správném formátu řetězec ve formátu HTML jakoby vykreslení v prohlížeči, jak je znázorněno na následujícím obrázku. Poškozená HTML se může zobrazit jako prostý text.

![HTML vizualizér řetězce](../debugger/media/dbg-string-visualizers-html.png "HTML vizualizér řetězce")

## <a name="see-also"></a>Viz také:

- [Vytváření vlastních vizualizérů (C#, Visual Basic)](../debugger/create-custom-visualizers-of-data.md)
- [Vizualizace dat v sadě Visual Studio pro Mac](/visualstudio/mac/data-visualizations)