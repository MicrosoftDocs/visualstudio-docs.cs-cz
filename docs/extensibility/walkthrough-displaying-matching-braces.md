---
title: 'Návod: Zobrazení odpovídajících závorek | Dokumenty společnosti Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - brace matching
ms.assetid: 5af08ac7-1d08-4ccf-997e-01aa6cb3d3d7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 107610733ab9b5c8085b3f987fa999250b453d63
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697455"
---
# <a name="walkthrough-display-matching-braces"></a>Návod: Zobrazení odpovídajících závorek
Implementujte funkce založené na jazyce, jako je například porovnávání složených závorek, které chcete spárovat, a přidáním značky textové značky do odpovídajících závorek, když je stříška na jedné ze složených závorek. Můžete definovat složená závorky v kontextu jazyka, definovat vlastní příponu názvu souboru a typ obsahu a použít značky pouze na tento typ nebo použít značky na existující typ obsahu (například "text"). Následující návod ukazuje, jak aplikovat značky složených závorek na typ obsahu "text".

## <a name="prerequisites"></a>Požadavky
 Počínaje Visual Studio 2015, nenainstalujete Visual Studio SDK ze služby stažení. Je součástí volitelné funkce v nastavení sady Visual Studio. VS SDK můžete také nainstalovat později. Další informace naleznete [v tématu Instalace sady Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-managed-extensibility-framework-mef-project"></a>Vytvoření projektu spravovaného rámce rozšiřitelnosti (MEF)

#### <a name="to-create-a-mef-project"></a>Vytvoření projektu MEF

1. Vytvořte projekt klasifikátoru editoru. Pojmenujte `BraceMatchingTest`řešení .

2. Přidejte do projektu šablonu položky třídění editoru. Další informace naleznete [v tématu Vytvoření rozšíření se šablonou položky editoru](../extensibility/creating-an-extension-with-an-editor-item-template.md).

3. Odstraňte existující soubory tříd.

## <a name="implement-a-brace-matching-tagger"></a>Implementace taggeru složených závorek
 Chcete-li získat efekt zvýraznění závorky, který se podobá efektu používanému <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>v sadě Visual Studio, můžete implementovat tagger typu . Následující kód ukazuje, jak definovat tagger pro páry složených závorek na libovolné úrovni vnoření. V tomto příkladu dvojice závorek [] a {} jsou definovány v konstruktoru tagger, ale v implementaci plného jazyka by příslušné dvojice složených závorek byly definovány ve specifikaci jazyka.

### <a name="to-implement-a-brace-matching-tagger"></a>Chcete-li implementovat tagger odpovídající složená závorka

1. Přidejte soubor třídy a pojmenujte jej BraceMatching.

2. Importujte následující obory názvů.

     [!code-csharp[VSSDKBraceMatchingTest#1](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_1.cs)]
     [!code-vb[VSSDKBraceMatchingTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_1.vb)]

3. Definujte `BraceMatchingTagger` třídu, <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> která <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>dědí z typu .

     [!code-csharp[VSSDKBraceMatchingTest#2](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_2.cs)]
     [!code-vb[VSSDKBraceMatchingTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_2.vb)]

4. Přidejte vlastnosti pro zobrazení textu, zdrojovou vyrovnávací paměť, aktuální bod snímku a také sadu párů složených závorek.

     [!code-csharp[VSSDKBraceMatchingTest#3](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_3.cs)]
     [!code-vb[VSSDKBraceMatchingTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_3.vb)]

5. V konstruktoru tagger nastavte vlastnosti a přihlaste se k odběru událostí <xref:Microsoft.VisualStudio.Text.Editor.ITextCaret.PositionChanged> změn zobrazení a <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged>. V tomto příkladu pro ilustrativní účely jsou odpovídající dvojice také definovány v konstruktoru.

     [!code-csharp[VSSDKBraceMatchingTest#4](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_4.cs)]
     [!code-vb[VSSDKBraceMatchingTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_4.vb)]

6. Jako součást <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> implementace deklarujte událost TagsChanged.

     [!code-csharp[VSSDKBraceMatchingTest#5](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_5.cs)]
     [!code-vb[VSSDKBraceMatchingTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_5.vb)]

7. Obslužné rutiny události aktualizovat `CurrentChar` aktuální pozici stříšky vlastnosti a zvýšit TagsChanged události.

     [!code-csharp[VSSDKBraceMatchingTest#6](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_6.cs)]
     [!code-vb[VSSDKBraceMatchingTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_6.vb)]

8. Implementujte <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> metodu tak, aby odpovídala závorkám, pokud je aktuální znak otevřená závorka nebo pokud je předchozí znak blízkým složená zvorka, jako v sadě Visual Studio. Když je nalezena shoda, tato metoda inkoniátuje dvě značky, jeden pro otevřenou závorku a jeden pro úzkou závorku.

     [!code-csharp[VSSDKBraceMatchingTest#7](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_7.cs)]
     [!code-vb[VSSDKBraceMatchingTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_7.vb)]

9. Následující soukromé metody najít odpovídající složená závorka na libovolné úrovni vnoření. První metoda vyhledá znak zavření, který odpovídá otevřenému znaku:

     [!code-csharp[VSSDKBraceMatchingTest#8](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_8.cs)]
     [!code-vb[VSSDKBraceMatchingTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_8.vb)]

10. Následující pomocná metoda vyhledá otevřený znak, který odpovídá znaku blízkého:

     [!code-csharp[VSSDKBraceMatchingTest#9](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_9.cs)]
     [!code-vb[VSSDKBraceMatchingTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_9.vb)]

## <a name="implement-a-brace-matching-tagger-provider"></a>Implementace zprostředkovatele tagger odpovídající složená závorka
 Kromě implementace tagger, musíte také implementovat a exportovat zprostředkovatele tagger. V tomto případě je typ obsahu poskytovatele "text". Takže srovnávač odpovídající se zobrazí ve všech typech textových souborů, ale plnější implementace platí složená závorka odpovídající pouze pro určitý typ obsahu.

### <a name="to-implement-a-brace-matching-tagger-provider"></a>Implementace zprostředkovatele tagger odpovídající složená závorka

1. <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider>Deklarujte zprostředkovatele tagger, který dědí z , pojmenujte braceMatchingTaggerProvider a exportujte jej s <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "text" a a <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> . <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>

     [!code-csharp[VSSDKBraceMatchingTest#10](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_10.cs)]
     [!code-vb[VSSDKBraceMatchingTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_10.vb)]

2. Implementujte <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider.CreateTagger%2A> metodu k vytvoření instance BraceMatchingTagger.

     [!code-csharp[VSSDKBraceMatchingTest#11](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_11.cs)]
     [!code-vb[VSSDKBraceMatchingTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_11.vb)]

## <a name="build-and-test-the-code"></a>Sestavení a testování kódu
 Chcete-li otestovat tento kód, vytvořte řešení BraceMatchingTest a spusťte jej v experimentální instanci.

#### <a name="to-build-and-test-bracematchingtest-solution"></a>Vytvoření a testování řešení BraceMatchingTest

1. Sestavte řešení.

2. Při spuštění tohoto projektu v ladicím programu je spuštěna druhá instance sady Visual Studio.

3. Vytvořte textový soubor a zadejte text, který obsahuje odpovídající závorky.

    ```
    hello {
    goodbye}

    {}

    {hello}
    ```

4. Při umístění stříšky před otevřenou složenou závorku by měla být zvýrazněna jak tato ortéza, tak odpovídající závorka. Při umístění kurzoru těsně za zavřít ortézu, jak tuto ortézu a odpovídající otevřenou složenou závorku by měla být zvýrazněna.

## <a name="see-also"></a>Viz také
- [Návod: Propojení typu obsahu s příponou názvu souboru](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
