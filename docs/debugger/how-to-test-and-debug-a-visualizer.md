---
title: Jak testovat a ladit Vizualizér | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- visualizers, testing
- visualizers, debugging
- debugging [Visual Studio], visualizers
ms.assetid: 5cc12ce8-c819-48e4-b487-98d403001b28
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1a81a8d094999585620ab6ab412c3b0610caf517
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85348896"
---
# <a name="how-to-test-and-debug-a-visualizer"></a>Postupy: Testování a ladění vizualizéru
Jakmile napíšete vizualizér, budete ho muset ladit a testovat.

Jedním ze způsobů, jak testovat vizualizér, je jeho instalace v aplikaci Visual Studio a jeho volání z okna ladicího programu. (Viz [Postup: instalace Vizualizátoru](../debugger/how-to-install-a-visualizer.md).) Pokud to uděláte, budete muset použít druhou instanci sady Visual Studio k připojení a ladění vizualizér, který je spuštěn v první instanci ladicího programu.

Jednodušší způsob, jak ladit vizualizér, je spustit Vizualizér z testovacího ovladače. Rozhraní API pro Vizualizér usnadňují tvorbu takového ovladače, který se nazývá *vývojový hostitel pro Vizualizér*.

### <a name="to-create-a-visualizer-development-host"></a>Vytvoření hostitelského vývojového prostředí Vizualizér

1. Do třídy na straně ladicího programu zahrňte statickou metodu, která vytvoří <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerDevelopmentHost> objekt a zavolá jeho metodu show:

    ```csharp
    public static void TestShowVisualizer(object objectToVisualize)
    {
        VisualizerDevelopmentHost myHost = new VisualizerDevelopmentHost(objectToVisualize, typeof(DebuggerSide));
        myHost.ShowVisualizer();
    }
    ```

    Parametry použité k sestavení hostitele jsou datový objekt, který bude zobrazen v Vizualizér ( `objectToVisualize` ) a typu třídy na straně ladicího programu.

2. Přidejte následující příkaz pro volání `TestShowVisualizer` . Pokud jste vytvořili Vizualizér v knihovně tříd, je nutné vytvořit spustitelný soubor pro volání knihovny tříd a umístit tento příkaz do spustitelného souboru:

    ```csharp
    DebuggerSide.TestShowVisualizer(myString);
    ```

    Úplnější příklad najdete v tématu [Návod: zápis Vizualizér v jazyce C#](../debugger/walkthrough-writing-a-visualizer-in-csharp.md).

## <a name="see-also"></a>Viz také
- [Návod: Zápis vizualizéru v jazyce C#](../debugger/walkthrough-writing-a-visualizer-in-csharp.md)
- [Postupy: instalace Vizualizátoru](../debugger/how-to-install-a-visualizer.md)
- [Vytváření vlastních vizualizérů](../debugger/create-custom-visualizers-of-data.md)
