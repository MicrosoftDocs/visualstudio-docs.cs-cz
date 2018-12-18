---
title: Architektura vizualizéru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: 6aad395f-7170-4d9e-b2b8-a5faf453380e
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0e9c9f9012cc2811e0462586abe062e25a5478c5
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49836603"
---
# <a name="visualizer-architecture"></a>Architektura vizualizéru
Architektura vizualizéru ladicí program má dvě části:  
  
- *Ladicího programu na straně* běží v rámci ladicího programu sady Visual Studio. Ladicí program na straně kód vytvoří a zobrazí uživatelské rozhraní pro vaše vizualizér.  
  
- *Na straně laděného procesu* běží v rámci procesu ladění sady Visual Studio ( *laděného procesu*).  
  
  Vizualizéru je komponenta ladicího programu, které umožňují ladicímu programu k zobrazení (*vizualizovat*) obsah datového objektu ve formě smysluplné, srozumitelné. Některé vizualizéry podporují také úpravy datového objektu. Psaním vlastních vizualizérů, můžete rozšířit ladicího programu pro zpracování vlastní vlastní datové typy.  
  
  Datový objekt má být zobrazen se nachází v rámci procesu ladění ( *laděného procesu* proces). Uživatelské rozhraní, které se zobrazí data se vytvoří v rámci procesu ladicího programu sady Visual Studio:  
  
|Procesu ladicího programu|Laděném procesu|  
|----------------------|----------------------|  
|Uživatelské rozhraní (datových tipů, okna kukátka, Rychlé kukátko) ladicího programu|Datový objekt má být zobrazen|  
  
 Pokud chcete vizualizovat datový objekt v rámci rozhraní ladicího programu, musíte kód ke komunikaci mezi dvěma procesy. V důsledku toho tato architektura vizualizéru se skládá ze dvou částí: *ladicího programu na straně* kódu a *na straně laděného procesu* kódu.  
  
 Ladicí program side kód vytvoří vlastní uživatelské rozhraní, který lze vyvolat pomocí rozhraní ladicího programu, jako je například DataTip, okna kukátka nebo Rychlé kukátko. Rozhraní vizualizéru se vytvoří s použitím <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer> třídy a <xref:Microsoft.VisualStudio.DebuggerVisualizers.IDialogVisualizerService> rozhraní. Stejně jako všechna rozhraní API Vizualizéru, DialogDebuggerVisualizer a IDialogVisualizerService se nacházejí v <xref:Microsoft.VisualStudio.DebuggerVisualizers> oboru názvů.  
  
|Na straně ladicího programu|Na straně laděného procesu|  
|-------------------|-------------------|  
|Třída DialogDebuggerVisualizer<br /><br /> IDialogVisualizerService rozhraní|Datový objekt|  
  
 Uživatelské rozhraní načte data, která má být zobrazen od poskytovatele objektu, která existuje na straně ladicího programu:  
  
|Na straně ladicího programu|Na straně laděného procesu|  
|-------------------|-------------------|  
|Třída DialogDebuggerVisualizer<br /><br /> IDialogVisualizerService rozhraní|Datový objekt|  
|Objekt zprostředkovatele (implementuje <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider>)||  
  
 Na straně laděného procesu volat zdroj objektu je odpovídající objekt:  
  
|Na straně ladicího programu|Na straně laděného procesu|  
|-------------------|-------------------|  
|Třída DialogDebuggerVisualizer<br /><br /> IDialogVisualizerService rozhraní|Datový objekt|  
|Objekt zprostředkovatele (implementuje <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider>)|Objekt zdroje (odvozený od <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource>)|  
  
 Objekt zprostředkovatele poskytuje data objektu, která má být zobrazen na vizualizátor uživatelského rozhraní. Objekt zprostředkovatel získá dat objektů ze zdroje objektu. Objekt zprostředkovatele a objekt zdroje poskytují rozhraní API pro komunikaci data objektu mezi straně ladicího programu a na straně laděného objektu.  
  
 Každý vizualizéru musí získejte datový objekt má být zobrazen. V následující tabulce jsou uvedeny odpovídající rozhraní API, že pro tento účel použít objekt zprostředkovatele a objekt zdroje:  
  
|Objekt zprostředkovatele|Zdroj objektu|  
|---------------------|-------------------|  
|<xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetData%2A><br /><br /> —nebo—<br /><br /> <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetObject%2A>|<xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource.GetData%2A>|  
  
 Všimněte si, že zprostředkovatele objektu můžete použít buď <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetData%2A> nebo <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetObject%2A>. Buď rozhraní API, které jsou výsledkem volání <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource.GetData%2A> na zdroji objektu. Volání <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource.GetData%2A?displayProperty=fullName> vyplní <xref:System.IO.Stream?displayProperty=fullName>, která představuje serializované podoby, která je vizualizovaného objektu.  
  
 <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetObject%2A?displayProperty=fullName> deserializuje data zpět do objektu formulář, který pak můžete zobrazit v uživatelském rozhraní, kterou vytvoříte pomocí <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer>. <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetData%2A?displayProperty=fullName> vyplní jako nezpracovaná data `Stream`, které musí deserializovat sami. <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetObject%2A?displayProperty=fullName> funguje tak, že volání <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetData%2A?displayProperty=fullName> zobrazíte serializovaný `Stream`, potom deserializaci data. Použití <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetData%2A?displayProperty=fullName> když objekt není serializovatelná pomocí .NET a vyžaduje vlastní serializace. V takovém případě je nutné také přepsat <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource.Serialize%2A?displayProperty=fullName> metody.  
  
 Pokud vytváříte jen pro čtení vizualizéru, jednosměrnou komunikaci s <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetData%2A> nebo <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetObject%2A> je dostačující. Pokud vytváříte vizualizéru, který podporuje úpravy datových objektů, musí zvládnout víc. Musíte být také odesílat datový objekt ze zprostředkovatele objektu zpět do zdroje objektu. V následující tabulce jsou uvedeny zprostředkovatele objektu a objekt zdroje API používaná pro tento účel:  
  
|Objekt zprostředkovatele|Zdroj objektu|  
|---------------------|-------------------|  
|<xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.ReplaceData%2A><br /><br /> —nebo—<br /><br /> <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.ReplaceObject%2A>|<xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource.CreateReplacementObject%2A>|  
  
 Všimněte si znovu, že existují dvě rozhraní API, které můžete použít zprostředkovatele objektu. Vždy odeslání dat ze zprostředkovatele objektu do objektu zdroje jako `Stream`, ale <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.ReplaceData%2A> vyžaduje serializaci objektů do `Stream` sami.  
  
 <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.ReplaceObject%2A> serializuje přebírá objekt, který zadáte, ho do `Stream`, pak zavolá <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.ReplaceData%2A> k odeslání `Stream` k <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource.CreateReplacementObject%2A>.  
  
 Pomocí jedné z metod nahradit vytvoří nový objekt dat laděného procesu, který nahrazuje objekt, který je právě vizualizován. Pokud chcete změnit obsah na původní objekt bez jeho nahrazení, použijte jednu z metod přenosu je znázorněno v následující tabulce. Tato rozhraní API přenosu dat v obou směrech ve stejnou dobu bez nutnosti vyměnit objekt, který je vizualizovaného:  
  
|Objekt zprostředkovatele|Zdroj objektu|  
|---------------------|-------------------|  
|<xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.TransferData%2A><br /><br /> —nebo—<br /><br /> <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.TransferObject%2A>|<xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource.TransferData%2A>|  
  
## <a name="see-also"></a>Viz také  
 [Postupy: zápis Vizualizéru](../debugger/how-to-write-a-visualizer.md)   
 [Návod: Zápis Vizualizéru v jazyce C#](../debugger/walkthrough-writing-a-visualizer-in-csharp.md)   
 [Návod: Zápis Vizualizéru v jazyce Visual Basic](../debugger/walkthrough-writing-a-visualizer-in-visual-basic.md)   
 [Návod: Zápis Vizualizéru v jazyce Visual Basic](../debugger/walkthrough-writing-a-visualizer-in-visual-basic.md)   
 [Informace o zabezpečení vizualizéru](../debugger/visualizer-security-considerations.md)