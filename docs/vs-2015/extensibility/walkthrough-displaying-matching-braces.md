---
title: 'Návod: zobrazení vyhovujících složených závorek | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - brace matching
ms.assetid: 5af08ac7-1d08-4ccf-997e-01aa6cb3d3d7
caps.latest.revision: 28
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: caaafd0143d3b09a51518ee5f54a02b06dbf10aa
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68165780"
---
# <a name="walkthrough-displaying-matching-braces"></a>Návod: Zobrazení párových složených závorek
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Můžete implementovat základní funkce, jako je například párování složených závorek, definování složených závorek a následnou přidáním značky textu do odpovídajících závorek, pokud je stříška v jedné z složených závorek. Složené závorky lze definovat v kontextu jazyka nebo můžete definovat vlastní příponu názvu souboru a typ obsahu a použít značky pouze pro tento typ, nebo můžete značky použít na existující typ obsahu (například "text"). Následující návod ukazuje, jak použít Tagy pro spárování složených závorek s typem obsahu text.  
  
## <a name="prerequisites"></a>Předpoklady  
 Od sady Visual Studio 2015 nenainstalujete sadu Visual Studio SDK z webu Stažení softwaru. V instalačním programu sady Visual Studio je zahrnutý jako volitelná funkce. Sadu VS SDK můžete také nainstalovat později. Další informace najdete v tématu [instalace sady Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-managed-extensibility-framework-mef-project"></a>Vytvoření projektu Managed Extensibility Framework (MEF)  
  
#### <a name="to-create-a-mef-project"></a>Vytvoření projektu MEF  
  
1. Vytvořte projekt klasifikátoru editoru. Pojmenujte řešení `BraceMatchingTest` .  
  
2. Přidejte do projektu šablonu položky klasifikátoru editoru. Další informace naleznete v tématu [Vytvoření rozšíření pomocí šablony položky editoru](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3. Odstraňte existující soubory třídy.  
  
## <a name="implementing-a-brace-matching-tagger"></a>Implementace odpovídajícího autor značky složené závorky  
 Chcete-li získat efekt zvýraznění složené závorky, který se podobá použitému v aplikaci Visual Studio, můžete implementovat autor značky typu <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> . Následující kód ukazuje, jak definovat autor značky pro páry složených závorek na libovolné úrovni vnoření. V tomto příkladu páry složených závorek []. [] a {} jsou definovány v konstruktoru autor značky, ale v plné jazykové implementaci by se měly definovat příslušné páry složených závorek ve specifikaci jazyka.  
  
#### <a name="to-implement-a-brace-matching-tagger"></a>Implementace odpovídajícího autor značky složené závorky  
  
1. Přidejte soubor třídy a pojmenujte ho BraceMatching.  
  
2. Importujte následující obory názvů.  
  
     [!code-csharp[VSSDKBraceMatchingTest#1](../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs#1)]
     [!code-vb[VSSDKBraceMatchingTest#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb#1)]  
  
3. Definujte třídu `BraceMatchingTagger` , která dědí z <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> typu <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> .  
  
     [!code-csharp[VSSDKBraceMatchingTest#2](../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs#2)]
     [!code-vb[VSSDKBraceMatchingTest#2](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb#2)]  
  
4. Přidejte vlastnosti pro textové zobrazení, zdrojovou vyrovnávací paměť a aktuální bod snímku a také sadu párů složených závorek.  
  
     [!code-csharp[VSSDKBraceMatchingTest#3](../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs#3)]
     [!code-vb[VSSDKBraceMatchingTest#3](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb#3)]  
  
5. V konstruktoru autor značky nastavte vlastnosti a přihlaste se k událostem změny zobrazení <xref:Microsoft.VisualStudio.Text.Editor.ITextCaret.PositionChanged> a <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> . V tomto příkladu jsou pro ilustrativní účely také definovány párové páry v konstruktoru.  
  
     [!code-csharp[VSSDKBraceMatchingTest#4](../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs#4)]
     [!code-vb[VSSDKBraceMatchingTest#4](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb#4)]  
  
6. V rámci <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> implementace deklarujte událost TagsChanged.  
  
     [!code-csharp[VSSDKBraceMatchingTest#5](../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs#5)]
     [!code-vb[VSSDKBraceMatchingTest#5](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb#5)]  
  
7. Obslužné rutiny události aktualizují aktuální pozici blikajícího kurzoru `CurrentChar` vlastnosti a vyvolávají událost TagsChanged.  
  
     [!code-csharp[VSSDKBraceMatchingTest#6](../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs#6)]
     [!code-vb[VSSDKBraceMatchingTest#6](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb#6)]  
  
8. Implementujte <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> metodu pro spárování složených závorek buď v případě, že aktuální znak je levou složenou závorkou, nebo pokud je předchozí znak pravá složená závorka, stejně jako v aplikaci Visual Studio. Když je nalezena shoda, tato metoda vytvoří instanci dvou značek, jednu pro levou složenou závorku a jednu pro pravou složenou závorku.  
  
     [!code-csharp[VSSDKBraceMatchingTest#7](../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs#7)]
     [!code-vb[VSSDKBraceMatchingTest#7](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb#7)]  
  
9. Následující soukromé metody vyhledají párové závorky na libovolné úrovni vnoření. První metoda najde znak ukončení, který odpovídá znaku otevření:  
  
     [!code-csharp[VSSDKBraceMatchingTest#8](../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs#8)]
     [!code-vb[VSSDKBraceMatchingTest#8](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb#8)]  
  
10. Následující pomocná metoda najde otevřený znak, který odpovídá znaku ukončení:  
  
     [!code-csharp[VSSDKBraceMatchingTest#9](../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs#9)]
     [!code-vb[VSSDKBraceMatchingTest#9](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb#9)]  
  
## <a name="implementing-a-brace-matching-tagger-provider"></a>Implementace odpovídajícího poskytovatele autor značky ve složených závorkách  
 Kromě implementace autor značky musíte také implementovat a exportovat poskytovatele autor značky. V tomto případě je typ obsahu poskytovatele "text". To znamená, že spárování složených závorek se zobrazí ve všech typech textových souborů, ale plná implementace by použila spárování složených závorek pouze s konkrétním typem obsahu.  
  
#### <a name="to-implement-a-brace-matching-tagger-provider"></a>Implementace odpovídajícího poskytovatele autor značky ve složených závorkách  
  
1. Deklarujte poskytovatele autor značky, který dědí z <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider> , pojmenujte ho BraceMatchingTaggerProvider a exportujte ho pomocí <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "text" a <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> .  
  
     [!code-csharp[VSSDKBraceMatchingTest#10](../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs#10)]
     [!code-vb[VSSDKBraceMatchingTest#10](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb#10)]  
  
2. Implementujte <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider.CreateTagger%2A> metodu pro vytvoření instance BraceMatchingTagger.  
  
     [!code-csharp[VSSDKBraceMatchingTest#11](../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs#11)]
     [!code-vb[VSSDKBraceMatchingTest#11](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb#11)]  
  
## <a name="building-and-testing-the-code"></a>Sestavování a testování kódu  
 Chcete-li otestovat tento kód, sestavte řešení BraceMatchingTest a spusťte ho v experimentální instanci.  
  
#### <a name="to-build-and-test-bracematchingtest-solution"></a>Sestavení a testování řešení BraceMatchingTest  
  
1. Sestavte řešení.  
  
2. Při spuštění tohoto projektu v ladicím programu je vytvořena instance druhé instance aplikace Visual Studio.  
  
3. Vytvořte textový soubor a napište nějaký text, který bude obsahovat odpovídající závorky.  
  
    ```  
    hello {  
    goodbye}  
  
    {}  
  
    {hello}  
    ```  
  
4. Když umístíte blikající kurzor před levou složenou závorku, měla by být zvýrazněna obě složené závorky i odpovídající uzavírací závorky. Když umístíte kurzor hned za pravou složenou závorku, měla by být zvýrazněna obě složené závorky a odpovídající levou složenou závorku.  
  
## <a name="see-also"></a>Viz také  
 [Návod: Propojení typu obsahu s příponou názvu souboru](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
