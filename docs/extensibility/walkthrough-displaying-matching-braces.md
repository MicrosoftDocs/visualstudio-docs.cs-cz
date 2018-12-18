---
title: 'Návod: Zobrazení odpovídající složené závorky | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - brace matching
ms.assetid: 5af08ac7-1d08-4ccf-997e-01aa6cb3d3d7
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 1f29596c95646db78145725f1f0cead424e1de5e
ms.sourcegitcommit: 1c2ed640512ba613b3bbbc9ce348e28be6ca3e45
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/03/2018
ms.locfileid: "39500433"
---
# <a name="walkthrough-display-matching-braces"></a>Návod: Zobrazení párových složených závorek
Implementuje funkce založený na jazyce, jako je například závorky definováním složené závorky, kterou chcete porovnat a přidání značky značky textu k odpovídající složené závorky po blikající kurzor na jednom z složené závorky. Můžete definovat složené závorky v rámci jazyka, definovat vlastní příponu názvu souboru a typu obsahu a použít jenom značky, které typ nebo použít značky k existujícímu typu obsahu (jako je například "text"). Následující návod ukazuje, jak použít závorky značky "text" typu obsahu.  
  
## <a name="prerequisites"></a>Požadavky  
 Spouští se v sadě Visual Studio 2015, nenainstalujete sadu Visual Studio SDK ze služby Stažení softwaru. Je zahrnutý jako volitelná funkce v instalačním programu sady Visual Studio. VS SDK můžete také nainstalovat později. Další informace najdete v tématu [instalace sady Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="create-a-managed-extensibility-framework-mef-project"></a>Vytvoření projektu Managed Extensibility Framework (MEF)  
  
#### <a name="to-create-a-mef-project"></a>Chcete-li vytvořit projekt rozhraní MEF  
  
1.  Vytvořte projekt klasifikace Editor. Pojmenujte řešení `BraceMatchingTest`.  
  
2.  Přidejte do projektu šablony položky editoru třídění. Další informace najdete v tématu [vytváření rozšíření pomocí šablony položky editoru](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3.  Odstraníte existující soubory tříd.  
  
## <a name="implement-a-brace-matching-tagger"></a>Implementace závorky označovatel  
 Získat složenou závorku zvýraznění efekt, který vypadá podobně jako ten, který se používá v sadě Visual Studio, můžete implementovat označovatel typu <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>. Následující kód ukazuje, jak definovat označovatel párů složenou závorku na libovolné úrovni vnoření. V tomto příkladu dvojice složená závorka [] a {} jsou definovány v konstruktoru označovatel, ale v implementaci úplným jazykovým, relevantní složenou závorku páry by definované ve specifikaci jazyka.  
  
### <a name="to-implement-a-brace-matching-tagger"></a>K implementaci závorky označovatel  
  
1.  Přidejte soubor třídy a pojmenujte ho BraceMatching.  
  
2.  Importujte následující obory názvů.  
  
     [!code-csharp[VSSDKBraceMatchingTest#1](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_1.cs)]
     [!code-vb[VSSDKBraceMatchingTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_1.vb)]  
  
3.  Definovat třídu `BraceMatchingTagger` , která dědí z <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> typu <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>.  
  
     [!code-csharp[VSSDKBraceMatchingTest#2](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_2.cs)]
     [!code-vb[VSSDKBraceMatchingTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_2.vb)]  
  
4.  Přidání vlastností pro zobrazení textu, zdrojové vyrovnávací paměti, aktuálního snímku do konkrétního bodu a také sadu párů závorek.  
  
     [!code-csharp[VSSDKBraceMatchingTest#3](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_3.cs)]
     [!code-vb[VSSDKBraceMatchingTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_3.vb)]  
  
5.  V konstruktoru označovatel, nastavte vlastnosti a přihlášení k odběru událostí změnit zobrazení <xref:Microsoft.VisualStudio.Text.Editor.ITextCaret.PositionChanged> a <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged>. V tomto příkladu pro ilustraci, odpovídající dvojice jsou také definovány v konstruktoru.  
  
     [!code-csharp[VSSDKBraceMatchingTest#4](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_4.cs)]
     [!code-vb[VSSDKBraceMatchingTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_4.vb)]  
  
6.  Jako součást <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> implementaci TagsChanged událost deklarovat.  
  
     [!code-csharp[VSSDKBraceMatchingTest#5](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_5.cs)]
     [!code-vb[VSSDKBraceMatchingTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_5.vb)]  
  
7.  Obslužné rutiny událostí aktualizovat aktuální pozici blikajícího kurzoru `CurrentChar` vlastnost a vyvolat událost TagsChanged.  
  
     [!code-csharp[VSSDKBraceMatchingTest#6](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_6.cs)]
     [!code-vb[VSSDKBraceMatchingTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_6.vb)]  
  
8.  Implementace <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> metodu tak, aby odpovídaly závorek, buď když aktuální znak je levou složenou závorku nebo pokud je předchozí znak je zavřít složené závorky, stejně jako v sadě Visual Studio. Když je nalezena shoda, tato metoda vytvoří dvě značky, jeden pro levou složenou závorku a jeden pro Zavřít složenou závorku.  
  
     [!code-csharp[VSSDKBraceMatchingTest#7](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_7.cs)]
     [!code-vb[VSSDKBraceMatchingTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_7.vb)]  
  
9. Následující privátní metody najít odpovídající závorce na libovolné úrovni vnoření. První metoda vyhledá zavřít znak, který odpovídá znaku otevřít:  
  
     [!code-csharp[VSSDKBraceMatchingTest#8](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_8.cs)]
     [!code-vb[VSSDKBraceMatchingTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_8.vb)]  
  
10. Následující Pomocná metoda vyhledá otevřít znak, který odpovídá znaku Zavřít:  
  
     [!code-csharp[VSSDKBraceMatchingTest#9](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_9.cs)]
     [!code-vb[VSSDKBraceMatchingTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_9.vb)]  
  
## <a name="implement-a-brace-matching-tagger-provider"></a>Implementace poskytovatele označovatel odpovídající závorku  
 Kromě provádění označovatel, musíte také implementovat a exportovat označovatel zprostředkovatele. Typ obsahu zprostředkovatele v tomto případě je "text". Proto závorky se zobrazí ve všech typech textových souborů, ale úplnější implementace se vztahuje jenom na konkrétní typ obsahu párování závorek.  
  
### <a name="to-implement-a-brace-matching-tagger-provider"></a>Pro implementaci zprostředkovatele označovatel odpovídající závorku  
  
1.  Deklarovat označovatel poskytovatele, který dědí z <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider>, pojmenujte ho BraceMatchingTaggerProvider a exportujte ho pomocí <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "text" a <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> z <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>.  
  
     [!code-csharp[VSSDKBraceMatchingTest#10](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_10.cs)]
     [!code-vb[VSSDKBraceMatchingTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_10.vb)]  
  
2.  Implementace <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider.CreateTagger%2A> metoda pro vytvoření instance BraceMatchingTagger.  
  
     [!code-csharp[VSSDKBraceMatchingTest#11](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_11.cs)]
     [!code-vb[VSSDKBraceMatchingTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_11.vb)]  
  
## <a name="build-and-test-the-code"></a>Vytváření a testování kódu  
 K otestování tohoto kódu sestavte řešení BraceMatchingTest a spusťte v experimentální instanci.  
  
#### <a name="to-build-and-test-bracematchingtest-solution"></a>Pro vytváření a testování BraceMatchingTest řešení  
  
1.  Sestavte řešení.  
  
2.  Při spuštění tohoto projektu v ladicím programu se spustí druhé instanci aplikace Visual Studio.  
  
3.  Vytvořte textový soubor a zadejte nějaký text, který obsahuje odpovídající složené závorky.  
  
    ```  
    hello {  
    goodbye}  
  
    {}  
  
    {hello}  
    ```  
  
4.  Když umístíte blikající kurzor před levou složenou závorku, by měl být zvýrazněn této složenou závorku a odpovídající závorce zavřít. Když umístěte kurzor bezprostředně po pravé lomené závorky, by měl být zvýrazněn této složenou závorku a odpovídající levou složenou závorku.  
  
## <a name="see-also"></a>Viz také:  
 [Návod: Propojení typ obsahu, který má příponu názvu souboru](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)