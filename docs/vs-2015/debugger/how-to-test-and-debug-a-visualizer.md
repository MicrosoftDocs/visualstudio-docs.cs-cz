---
title: 'Postupy: testování a ladění Vizualizéru | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
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
manager: ghogen
ms.openlocfilehash: 00fb749505f8bfe16c353552aa3afcb9eaaefc2d
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51723281"
---
# <a name="how-to-test-and-debug-a-visualizer"></a>Postupy: Testování a ladění vizualizéru
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Jakmile jste napsali vizualizéru, budete muset ladění a testování.  
  
 Jedním ze způsobů k otestování vizualizéru je z hlediska instalace v sadě Visual Studio a jeho volání z okna ladicího programu. (Viz [postupy: instalace Vizualizéru](../debugger/how-to-install-a-visualizer.md).) Pokud to uděláte, musíte použít druhou instanci aplikace Visual Studio k připojení a ladění vizualizéru, který je spuštěn v první instanci ladicího programu.  
  
 Snadný způsob, jak ladit vizualizéru je spustit vizualizéru z testu ovladače. Rozhraní API vizualizéru usnadňují vytváření tento ovladač, která je volána *vizualizéru vývoj hostitele*.  
  
### <a name="to-create-a-visualizer-development-host"></a>Pokud chcete vytvořit hostitele vývoj vizualizéru  
  
1.  Ve své třídě ladicí program side zahrnují statická metoda, která vytvoří <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerDevelopmentHost> objektu a volá metodu jeho zobrazit:  
  
    ```  
    public static void TestShowVisualizer(object objectToVisualize)  
    {  
       VisualizerDevelopmentHost myHost = new VisualizerDevelopmentHost(objectToVisualize, typeof(DebuggerSide));  
       myHost.ShowVisualizer();  
    }  
    ```  
  
     Parametry použité k vytvoření hostitele je datový objekt, který se zobrazí ve vizualizátoru (`objectToVisualize`) a typ třídy na straně ladicího programu.  
  
2.  Přidejte následující příkaz k volání `TestShowVisualizer`. Pokud jste vytvořili vaší vizualizéru v knihovně tříd, je potřeba vytvořit spustitelný soubor pro volání knihovny tříd a spustitelný soubor umístit tento příkaz:  
  
    ```  
    DebuggerSide.TestShowVisualizer(myString);  
    ```  
  
     Podrobnější příklad naleznete v tématu [návod: zápis Vizualizéru v jazyce C#](../debugger/walkthrough-writing-a-visualizer-in-csharp.md).  
  
## <a name="see-also"></a>Viz také  
 [Návod: Zápis Vizualizéru v jazyce C#](../debugger/walkthrough-writing-a-visualizer-in-csharp.md)   
 [Postupy: instalace Vizualizéru](../debugger/how-to-install-a-visualizer.md)   
 [Vytváření vlastních vizualizérů](../debugger/create-custom-visualizers-of-data.md)



