---
title: Vytvoření vlastních dat vizualizéry | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/07/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.visualizer.troubleshoot
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- debugger, visualizers
- visualizers
ms.assetid: c24c006f-f2ac-429f-89db-677fc0c6e1ea
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4c5f505bfa8032b0f7d59f348835e1e4969b2648
ms.sourcegitcommit: 6a955a2d179cd0e137942389f940d9fcbbe125de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/13/2018
ms.locfileid: "51607819"
---
# <a name="create-custom-data-visualizers"></a>Vytvoření vlastních dat vizualizéry 
 A *vizualizéru* je součástí [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] uživatelské rozhraní ladicího programu, který se zobrazí proměnné nebo objektu způsobem odpovídajícím k jeho datovému typu. Například HTML vizualizér interpretuje řetězec ve formátu HTML a výsledek zobrazí, jak se bude zobrazovat v okně prohlížeče. Rastrový obrázek vizualizéru interpretuje struktura rastrový obrázek a zobrazí obrázek, který představuje. Některé vizualizéry umožňují měnit také zobrazit data.

 [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] Ladicí program obsahuje šest standardní vizualizéry. Text, HTML, XML a JSON vizualizéry pracovat na řetězcových objektů. Vizualizéru stromu WPF zobrazuje vlastnosti objektu WPF vizuálního stromu. Vizualizér datasetu funguje pro objekty datové sady, zobrazení dat a DataTable. 

Další vizualizéry může být k dispozici ke stažení od Microsoftu, třetích stran a komunity. Můžete také napsat vlastní vizualizéry a nainstalovat je do [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] ladicího programu.

V ladicím programu, vizualizéru reprezentované ikonou lupy ![VisualizerIcon](../debugger/media/dbg-tips-visualizer-icon.png "Vizualizéru ikonu"). Můžete vybrat ikonu **datového tipu**, ladicí program **Watch** okno, nebo **QuickWatch** dialogové okno a potom vyberte příslušné vizualizér pro odpovídající objekt.

## <a name="write-custom-visualizers"></a>Zápis vlastních vizualizérech

 > [!NOTE]
 > Pokud chcete vytvořit vlastní vizualizér pro nativní kód, naleznete v tématu [nativní vizualizér SQLite](https://github.com/Microsoft/VSSDK-Extensibility-Samples/tree/master/SqliteVisualizer) vzorku. Vlastní vizualizátory se nepodporují pro aplikace UPW a Windows 8.x.

Můžete napsat vlastní vizualizér pro všechny spravované třídy s výjimkou objektu <xref:System.Object> a <xref:System.Array>.  
  
Architektura vizualizéru ladicí program má dvě části:  
  
- *Ladicího programu na straně* běží v rámci ladicího programu sady Visual Studio a vytvoří a zobrazí vizualizátor uživatelského rozhraní.  
  
- *Na straně laděného procesu* běží v rámci procesu ladění sady Visual Studio ( *laděného procesu*). Datový objekt k vizualizaci (například objekt String) neexistuje v laděném procesu. Na straně laděného procesu odešle objekt straně ladicí program zobrazí v uživatelském rozhraní, které vytvoříte.  

Na straně ladicí program přijímá objekt dat ze *zprostředkovatele objektu* , který implementuje <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider> rozhraní. Na straně laděného procesu odešle objekt prostřednictvím *zdroj objektu*, který je odvozen z <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource>. 

Objekt zprostředkovatele můžete také odesílat data zpět do zdroje objektu, který umožňuje zápis vizualizéru, lze upravovat data. Můžete přepsat zprostředkovatele objektu ke komunikaci s vyhodnocovací filtr výrazů a zdroj objektu.  
  
Straně laděného procesu ladicího programu na straně a komunikují prostřednictvím <xref:System.IO.Stream> metody, které serializaci dat objektů do <xref:System.IO.Stream> a deserializaci <xref:System.IO.Stream> zpět do datového objektu.  

Můžete napsat vizualizéru pro obecný typ pouze v případě, že typ je otevřeného typu. Toto omezení je stejné jako omezení při použití `DebuggerTypeProxy` atribut. Podrobnosti najdete v tématu [používání atributu DebuggerTypeProxy](../debugger/using-debuggertypeproxy-attribute.md).  
  
Důležité informace o zabezpečení může mít vlastní vizualizéry. Zobrazit [hlediska zabezpečení vizualizéru](../debugger/visualizer-security-considerations.md).  
  
Následující kroky poskytnout základní přehled o vytváření vizualizér. Podrobné pokyny najdete v tématu [návod: zápis vizualizéru v C# ](../debugger/walkthrough-writing-a-visualizer-in-csharp.md) nebo [návod: zápis vizualizéru v jazyce Visual Basic](../debugger/walkthrough-writing-a-visualizer-in-visual-basic.md).  
  
### <a name="to-create-the-debugger-side"></a>Chcete-li vytvořit vedlejší ladicího programu  
  
K vytvoření vizualizátor uživatelského rozhraní na straně ladicího programu, můžete vytvořit třídu, která dědí z <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer>a přepsat <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer.Show%2A?displayProperty=fullName> metodu pro zobrazení rozhraní. Můžete použít <xref:Microsoft.VisualStudio.DebuggerVisualizers.IDialogVisualizerService> k zobrazení formuláře Windows, dialogová okna a ovládací prvky ve vaší vizualizátoru.  
  
1.  Použití <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider> metody k získání vizualizovanému objektu na straně ladicího programu.  
  
1.  Vytvořte třídu, která dědí z <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer>.  
  
1.  Přepsat <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer.Show%2A?displayProperty=fullName> metodu pro zobrazení rozhraní. Použití <xref:Microsoft.VisualStudio.DebuggerVisualizers.IDialogVisualizerService> metody k zobrazení formuláře Windows, dialogová okna a ovládací prvky ve vašem rozhraní.  
  
4.  Použít <xref:System.Diagnostics.DebuggerVisualizerAttribute>, předá vizualizér pro zobrazení (<xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer>).  
  
### <a name="to-create-the-debuggee-side"></a>Chcete-li vytvořit na straně laděného procesu  
  
Zadejte kód na straně laděného procesu pomocí <xref:System.Diagnostics.DebuggerVisualizerAttribute>.  
  
1.  Použít <xref:System.Diagnostics.DebuggerVisualizerAttribute>, že mu poskytneme vizualizéru (<xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer>) a objektový zdroj (<xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource>). Vynecháte-li objektový zdroj, použije vizualizéru výchozí zdroj objektu.  
  
1.  Aby mohl vizualizéru upravit stejně jako objekty data zobrazení, přepsání `TransferData` nebo `CreateReplacementObject` metody ze <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource>.   
  
## <a name="see-also"></a>Viz také:
  
 [Návod: Zápis vizualizéru v jazyce C#](../debugger/walkthrough-writing-a-visualizer-in-csharp.md)  

 [Návod: Zápis vizualizéru v jazyce Visual Basic](../debugger/walkthrough-writing-a-visualizer-in-visual-basic.md)  
  
 [Postupy: Instalace vizualizéru](../debugger/how-to-install-a-visualizer.md)  
  
 [Postupy: Testování a ladění vizualizéru](../debugger/how-to-test-and-debug-a-visualizer.md)  
  
 [Referenční dokumentace rozhraní API vizualizéru](../debugger/visualizer-api-reference.md)  
  
 [Zobrazení dat v ladicím programu](../debugger/viewing-data-in-the-debugger.md)