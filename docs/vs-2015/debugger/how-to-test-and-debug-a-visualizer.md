---
title: 'Postupy: testování a ladění Vizualizér | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- visualizers, testing
- visualizers, debugging
- debugging [Visual Studio], visualizers
ms.assetid: 5cc12ce8-c819-48e4-b487-98d403001b28
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 18261d9e8c6c7d3f65dea7c72439b29f4e2e0df3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68176493"
---
# <a name="how-to-test-and-debug-a-visualizer"></a>Postupy: Testování a ladění vizualizéru
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Jakmile napíšete vizualizér, budete ho muset ladit a testovat.  
  
 Jedním ze způsobů, jak testovat vizualizér, je jeho instalace v aplikaci Visual Studio a jeho volání z okna ladicího programu. (Viz [Postup: instalace Vizualizátoru](../debugger/how-to-install-a-visualizer.md).) Pokud to uděláte, budete muset použít druhou instanci sady Visual Studio k připojení a ladění vizualizér, který je spuštěn v první instanci ladicího programu.  
  
 Jednodušší způsob, jak ladit vizualizér, je spustit Vizualizér z testovacího ovladače. Rozhraní API pro Vizualizér usnadňují tvorbu takového ovladače, který se nazývá *vývojový hostitel pro Vizualizér*.  
  
### <a name="to-create-a-visualizer-development-host"></a>Vytvoření hostitelského vývojového prostředí Vizualizér  
  
1. Do třídy na straně ladicího programu zahrňte statickou metodu, která vytvoří <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerDevelopmentHost> objekt a zavolá jeho metodu show:  
  
    ```  
    public static void TestShowVisualizer(object objectToVisualize)  
    {  
       VisualizerDevelopmentHost myHost = new VisualizerDevelopmentHost(objectToVisualize, typeof(DebuggerSide));  
       myHost.ShowVisualizer();  
    }  
    ```  
  
     Parametry použité k sestavení hostitele jsou datový objekt, který bude zobrazen v Vizualizér ( `objectToVisualize` ) a typu třídy na straně ladicího programu.  
  
2. Přidejte následující příkaz pro volání `TestShowVisualizer` . Pokud jste vytvořili Vizualizér v knihovně tříd, je nutné vytvořit spustitelný soubor pro volání knihovny tříd a umístit tento příkaz do spustitelného souboru:  
  
    ```  
    DebuggerSide.TestShowVisualizer(myString);  
    ```  
  
     Úplnější příklad najdete v tématu [Návod: zápis Vizualizér v jazyce C#](../debugger/walkthrough-writing-a-visualizer-in-csharp.md).  
  
## <a name="see-also"></a>Viz také  
 [Návod: zápis Vizualizér v jazyce C #](../debugger/walkthrough-writing-a-visualizer-in-csharp.md)   
 [Postupy: instalace Vizualizátoru](../debugger/how-to-install-a-visualizer.md)   
 [Vytváření vlastních vizualizérů](../debugger/create-custom-visualizers-of-data.md)
