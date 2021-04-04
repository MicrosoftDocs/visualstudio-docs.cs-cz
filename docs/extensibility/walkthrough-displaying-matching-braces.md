---
title: 'Návod: zobrazení vyhovujících složených závorek | Microsoft Docs'
description: V tomto návodu se dozvíte, jak definovat složené závorky v kontextu jazyka, s použitím složených závorek s typem obsahu textu.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- editors [Visual Studio SDK], new - brace matching
ms.assetid: 5af08ac7-1d08-4ccf-997e-01aa6cb3d3d7
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e4565e095c6bd8fe26f0bb72bd66d6df935ff16b
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2021
ms.locfileid: "106217265"
---
# <a name="walkthrough-display-matching-braces"></a>Návod: zobrazení vyhovujících složených závorek
Implementujte jazykové funkce, jako je například párování složených závorek, definováním složených závorek, které mají být shodné, a přidáním značky textové značky do odpovídajících složených závorek, pokud je blikající kurzor v jedné z složených závorek. Složené závorky lze definovat v kontextu jazyka, definovat vlastní příponu názvu souboru a typ obsahu a použít značky pouze pro tento typ nebo použít značky pro existující typ obsahu (například "text"). Následující návod ukazuje, jak použít Tagy pro spárování složených závorek s typem obsahu text.

## <a name="prerequisites"></a>Požadavky
 Od sady Visual Studio 2015 nenainstalujete sadu Visual Studio SDK z webu Stažení softwaru. V instalačním programu sady Visual Studio je zahrnutý jako volitelná funkce. Sadu VS SDK můžete také nainstalovat později. Další informace najdete v tématu [instalace sady Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-managed-extensibility-framework-mef-project"></a>Vytvořit projekt Managed Extensibility Framework (MEF)

#### <a name="to-create-a-mef-project"></a>Vytvoření projektu MEF

1. Vytvořte projekt klasifikátoru editoru. Pojmenujte řešení `BraceMatchingTest` .

2. Přidejte do projektu šablonu položky klasifikátoru editoru. Další informace naleznete v tématu [Vytvoření rozšíření pomocí šablony položky editoru](../extensibility/creating-an-extension-with-an-editor-item-template.md).

3. Odstraňte existující soubory třídy.

## <a name="implement-a-brace-matching-tagger"></a>Implementace autor značky odpovídajícího složené závorky
 Chcete-li získat efekt zvýraznění složené závorky, který se podobá použitému v aplikaci Visual Studio, můžete implementovat autor značky typu <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> . Následující kód ukazuje, jak definovat autor značky pro páry složených závorek na libovolné úrovni vnoření. V tomto příkladu jsou páry složených závorek [] a {} definovány v konstruktoru autor značky, ale v plné jazykové implementaci by se měly definovat odpovídající páry složených závorek ve specifikaci jazyka.

### <a name="to-implement-a-brace-matching-tagger"></a>Implementace odpovídajícího autor značky složené závorky

1. Přidejte soubor třídy a pojmenujte ho BraceMatching.

2. Importujte následující obory názvů.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs" id="Snippet1":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb" id="Snippet1":::

3. Definujte třídu `BraceMatchingTagger` , která dědí z <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> typu <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> .

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs" id="Snippet2":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb" id="Snippet2":::

4. Přidejte vlastnosti pro textové zobrazení, zdrojovou vyrovnávací paměť, aktuální bod snímku a také sadu párů složených závorek.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs" id="Snippet3":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb" id="Snippet3":::

5. V konstruktoru autor značky nastavte vlastnosti a přihlaste se k událostem změny zobrazení <xref:Microsoft.VisualStudio.Text.Editor.ITextCaret.PositionChanged> a <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> . V tomto příkladu jsou pro ilustrativní účely také definovány párové páry v konstruktoru.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs" id="Snippet4":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb" id="Snippet4":::

6. V rámci <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> implementace deklarujte událost TagsChanged.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs" id="Snippet5":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb" id="Snippet5":::

7. Obslužné rutiny události aktualizují aktuální pozici blikajícího kurzoru `CurrentChar` vlastnosti a vyvolávají událost TagsChanged.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs" id="Snippet6":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb" id="Snippet6":::

8. Implementujte <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> metodu pro spárování složených závorek buď v případě, že aktuální znak je levou složenou závorkou, nebo pokud je předchozí znak pravá složená závorka, stejně jako v aplikaci Visual Studio. Když je nalezena shoda, tato metoda vytvoří instanci dvou značek, jednu pro levou složenou závorku a jednu pro pravou složenou závorku.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs" id="Snippet7":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb" id="Snippet7":::

9. Následující soukromé metody vyhledají párové závorky na libovolné úrovni vnoření. První metoda najde znak ukončení, který odpovídá znaku otevření:

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs" id="Snippet8":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb" id="Snippet8":::

10. Následující pomocná metoda najde otevřený znak, který odpovídá znaku ukončení:

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs" id="Snippet9":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb" id="Snippet9":::

## <a name="implement-a-brace-matching-tagger-provider"></a>Implementace odpovídajícího poskytovatele autor značky ve složených závorkách
 Kromě implementace autor značky musíte také implementovat a exportovat poskytovatele autor značky. V tomto případě je typ obsahu poskytovatele "text". Spárování složených závorek se zobrazí ve všech typech textových souborů, ale úplná implementace aplikuje spárování složených závorek pouze na konkrétní typ obsahu.

### <a name="to-implement-a-brace-matching-tagger-provider"></a>Implementace odpovídajícího poskytovatele autor značky ve složených závorkách

1. Deklarujte poskytovatele autor značky, který dědí z <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider> , pojmenujte ho BraceMatchingTaggerProvider a exportujte ho pomocí <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "text" a <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> .

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs" id="Snippet10":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb" id="Snippet10":::

2. Implementujte <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider.CreateTagger%2A> metodu pro vytvoření instance BraceMatchingTagger.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs" id="Snippet11":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb" id="Snippet11":::

## <a name="build-and-test-the-code"></a>Sestavení a testování kódu
 Chcete-li otestovat tento kód, sestavte řešení BraceMatchingTest a spusťte ho v experimentální instanci.

#### <a name="to-build-and-test-bracematchingtest-solution"></a>Sestavení a testování řešení BraceMatchingTest

1. Sestavte řešení.

2. Při spuštění tohoto projektu v ladicím programu se spustí druhá instance sady Visual Studio.

3. Vytvořte textový soubor a napište nějaký text, který bude obsahovat odpovídající závorky.

    ```
    hello {
    goodbye}

    {}

    {hello}
    ```

4. Když umístíte blikající kurzor před levou složenou závorku, měla by být zvýrazněna obě složené závorky i odpovídající uzavírací závorky. Když umístíte kurzor hned za pravou složenou závorku, měla by být zvýrazněna obě složené závorky a odpovídající levou složenou závorku.

## <a name="see-also"></a>Viz také
- [Návod: propojení typu obsahu s příponou názvu souboru](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
