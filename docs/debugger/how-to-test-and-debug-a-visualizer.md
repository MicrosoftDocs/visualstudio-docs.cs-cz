---
title: Testování a ladění vizualizéru | Microsoft Docs
description: Testovat a ladit vizualizér jeho spuštěním z testovacího ovladače (vývojový hostitel vizualizéru) nebo instalací v Visual Studio a jeho voláním z okna ladicího programu.
ms.custom: SEO-VS-2020
ms.date: 07/02/2021
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: fa97453d08650b78a02eda873a01afe9e376caec
ms.sourcegitcommit: 4cd3eb514e9fa48e586279e38fe7c2e111ebb304
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/06/2021
ms.locfileid: "113298241"
---
# <a name="how-to-test-and-debug-a-visualizer"></a>Postupy: Testování a ladění vizualizéru
Po napsání vizualizéru ho musíte ladit a testovat.

Jedním ze způsob, jak testovat vizualizér, je jeho Visual Studio a voláním z okna ladicího programu. (Viz [Postupy: Instalace vizualizéru](../debugger/how-to-install-a-visualizer.md).) Pokud to chcete udělat, budete muset použít druhou instanci Visual Studio k připojení a ladění vizualizéru, který je spuštěný v první instanci ladicího programu.

Jednodušším způsobem ladění vizualizéru je spuštění vizualizéru z testovacího ovladače. Rozhraní API vizualizéru usnadňuje vytvoření takového ovladače, který se nazývá *vývojový hostitel vizualizéru.*

>[!NOTE]
> V současné době je testovací ovladač podporován pouze při volání vizualizéru z .NET Framework aplikace.

### <a name="to-create-a-visualizer-development-host"></a>Vytvoření vývojového hostitele vizualizéru

1. Do třídy na straně ladicího programu zahrpište statickou metodu, která vytvoří objekt a <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerDevelopmentHost> zavolá jeho metodu show:

    ```csharp
    public static void TestShowVisualizer(object objectToVisualize)
    {
        VisualizerDevelopmentHost myHost = new VisualizerDevelopmentHost(objectToVisualize, typeof(DebuggerSide));
        myHost.ShowVisualizer();
    }
    ```

    Parametry použité k vytvoření hostitele jsou datový objekt, který se zobrazí ve vizualizéru ( ) a typ třídy na `objectToVisualize` straně ladicího programu.

2. Přidejte následující příkaz pro volání `TestShowVisualizer` . Pokud jste vizualizér vytvořili v knihovně tříd, musíte vytvořit spustitelný soubor pro volání knihovny tříd a umístit tento příkaz do spustitelného souboru:

    ```csharp
    DebuggerSide.TestShowVisualizer(myString);
    ```

    Úplnější příklad najdete v tématu [Návod: Zápis vizualizéru v jazyce C#.](../debugger/walkthrough-writing-a-visualizer-in-csharp.md)

## <a name="see-also"></a>Viz také
- [Návod: Zápis vizualizéru v jazyce C#](../debugger/walkthrough-writing-a-visualizer-in-csharp.md)
- [Postupy: Instalace vizualizéru](../debugger/how-to-install-a-visualizer.md)
- [Vytváření vlastních vizualizérů](../debugger/create-custom-visualizers-of-data.md)
