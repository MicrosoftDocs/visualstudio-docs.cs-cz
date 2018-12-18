---
title: 'Návod: Zobrazení odpovídající složené závorky | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], new - brace matching
ms.assetid: 5af08ac7-1d08-4ccf-997e-01aa6cb3d3d7
caps.latest.revision: 28
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9795cd3c40eeff714d55f4bb95f78cf1f7f8aea9
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51745888"
---
# <a name="walkthrough-displaying-matching-braces"></a>Návod: Zobrazení párových složených závorek
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Budete moct implementovat založený na jazyce funkce, jako je například závorky definováním složené závorky, kterou chcete porovnat, a následným přidáním značky text značky do odpovídající složené závorky po blikající kurzor na jednom z složené závorky. Složené závorky můžete definovat v rámci jazyka, nebo můžete definovat vlastní název souboru příponu a obsah zadejte a použít značky jenom typu nebo můžete použít značky k existujícímu typu obsahu (jako je například "text"). Následující návod ukazuje, jak použít závorky značky "text" typu obsahu.  
  
## <a name="prerequisites"></a>Požadavky  
 Spouští se v sadě Visual Studio 2015, nenainstalujete sadu Visual Studio SDK ze služby Stažení softwaru. Je zahrnut jako volitelná funkce v instalačním programu sady Visual Studio. VS SDK můžete také nainstalovat později. Další informace najdete v tématu [instalace sady Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-managed-extensibility-framework-mef-project"></a>Vytvoření projektu Managed Extensibility Framework (MEF)  
  
#### <a name="to-create-a-mef-project"></a>Chcete-li vytvořit projekt rozhraní MEF  
  
1.  Vytvořte projekt klasifikace Editor. Pojmenujte řešení `BraceMatchingTest`.  
  
2.  Přidejte do projektu šablony položky editoru třídění. Další informace najdete v tématu [vytváření rozšíření pomocí šablony položky editoru](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3.  Odstraníte existující soubory tříd.  
  
## <a name="implementing-a-brace-matching-tagger"></a>Implementace závorky Označovatel  
 Získat složenou závorku zvýraznění efekt, který vypadá podobně jako ten, který se používá v sadě Visual Studio, můžete implementovat označovatel typu <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>. Následující kód ukazuje, jak definovat označovatel párů složenou závorku na libovolné úrovni vnoření. V tomto příkladu [] dvojice závorek. [], a {} jsou definovány v konstruktoru označovatel, ale v implementaci úplným jazykovým páry odpovídající závorku by definované ve specifikaci jazyka.  
  
#### <a name="to-implement-a-brace-matching-tagger"></a>K implementaci závorky označovatel  
  
1.  Přidejte soubor třídy a pojmenujte ho BraceMatching.  
  
2.  Importujte následující obory názvů.  
  
     [!code-csharp[VSSDKBraceMatchingTest#1](../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs#1)]
     [!code-vb[VSSDKBraceMatchingTest#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb#1)]  
  
3.  Definovat třídu `BraceMatchingTagger` , která dědí z <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> typu <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>.  
  
     [!code-csharp[VSSDKBraceMatchingTest#2](../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs#2)]
     [!code-vb[VSSDKBraceMatchingTest#2](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb#2)]  
  
4.  Přidání vlastností zobrazení textu, zdrojová vyrovnávací paměť aktuálního snímku do konkrétního bodu a také sadu párů závorek.  
  
     [!code-csharp[VSSDKBraceMatchingTest#3](../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs#3)]
     [!code-vb[VSSDKBraceMatchingTest#3](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb#3)]  
  
5.  V konstruktoru označovatel, nastavte vlastnosti a přihlášení k odběru událostí změnit zobrazení <xref:Microsoft.VisualStudio.Text.Editor.ITextCaret.PositionChanged> a <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged>. V tomto příkladu pro ilustraci, odpovídající dvojice jsou také definovány v konstruktoru.  
  
     [!code-csharp[VSSDKBraceMatchingTest#4](../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs#4)]
     [!code-vb[VSSDKBraceMatchingTest#4](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb#4)]  
  
6.  Jako součást <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> implementaci TagsChanged událost deklarovat.  
  
     [!code-csharp[VSSDKBraceMatchingTest#5](../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs#5)]
     [!code-vb[VSSDKBraceMatchingTest#5](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb#5)]  
  
7.  Obslužné rutiny událostí aktualizovat aktuální pozici blikajícího kurzoru `CurrentChar` vlastnost a vyvolat událost TagsChanged.  
  
     [!code-csharp[VSSDKBraceMatchingTest#6](../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs#6)]
     [!code-vb[VSSDKBraceMatchingTest#6](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb#6)]  
  
8.  Implementace <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> metodu tak, aby odpovídaly závorek, buď když aktuální znak je levou složenou závorku nebo pokud je předchozí znak je zavřít složené závorky, stejně jako v sadě Visual Studio. Když je nalezena shoda, tato metoda vytvoří dvě značky, jeden pro levou složenou závorku a jeden pro Zavřít složenou závorku.  
  
     [!code-csharp[VSSDKBraceMatchingTest#7](../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs#7)]
     [!code-vb[VSSDKBraceMatchingTest#7](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb#7)]  
  
9. Následující privátní metody najít odpovídající závorce na libovolné úrovni vnoření. První metoda vyhledá zavřít znak, který odpovídá znaku otevřít:  
  
     [!code-csharp[VSSDKBraceMatchingTest#8](../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs#8)]
     [!code-vb[VSSDKBraceMatchingTest#8](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb#8)]  
  
10. Následující Pomocná metoda vyhledá otevřít znak, který odpovídá znaku Zavřít:  
  
     [!code-csharp[VSSDKBraceMatchingTest#9](../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs#9)]
     [!code-vb[VSSDKBraceMatchingTest#9](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb#9)]  
  
## <a name="implementing-a-brace-matching-tagger-provider"></a>Implementace závorky Označovatel zprostředkovatele  
 Kromě provádění označovatel, musíte také implementovat a exportovat označovatel zprostředkovatele. Typ obsahu zprostředkovatele v tomto případě je "text". To znamená, že závorky se zobrazí ve všech typech textových souborů, ale úplnější implementace se vztahují jenom na konkrétní typ obsahu párování závorek.  
  
#### <a name="to-implement-a-brace-matching-tagger-provider"></a>Pro implementaci zprostředkovatele označovatel odpovídající závorku  
  
1.  Deklarovat označovatel poskytovatele, který dědí z <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider>, pojmenujte ho BraceMatchingTaggerProvider a exportujte ho pomocí <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "text" a <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> z <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>.  
  
     [!code-csharp[VSSDKBraceMatchingTest#10](../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs#10)]
     [!code-vb[VSSDKBraceMatchingTest#10](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb#10)]  
  
2.  Implementace <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider.CreateTagger%2A> metoda pro vytvoření instance BraceMatchingTagger.  
  
     [!code-csharp[VSSDKBraceMatchingTest#11](../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs#11)]
     [!code-vb[VSSDKBraceMatchingTest#11](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb#11)]  
  
## <a name="building-and-testing-the-code"></a>Vytváření a testování kódu  
 K otestování tohoto kódu sestavte řešení BraceMatchingTest a spusťte v experimentální instanci.  
  
#### <a name="to-build-and-test-bracematchingtest-solution"></a>Pro vytváření a testování BraceMatchingTest řešení  
  
1.  Sestavte řešení.  
  
2.  Při spuštění tohoto projektu v ladicím programu, je vytvořena instance druhou instanci aplikace Visual Studio.  
  
3.  Vytvořte textový soubor a zadejte nějaký text, který obsahuje odpovídající složené závorky.  
  
    ```  
    hello {  
    goodbye}  
  
    {}  
  
    {hello}  
    ```  
  
4.  Když umístíte blikající kurzor před levou složenou závorku, by měl být zvýrazněn této složenou závorku a odpovídající závorce zavřít. Když umístěte kurzor bezprostředně po pravé lomené závorky, by měl být zvýrazněn této složenou závorku a odpovídající levou složenou závorku.  
  
## <a name="see-also"></a>Viz také  
 [Návod: Propojení typu obsahu s příponou názvu souboru](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)

