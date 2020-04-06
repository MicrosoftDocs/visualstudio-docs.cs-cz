---
title: 'Návod: Vytvoření glyfu okrajů | Dokumenty společnosti Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - margin glyph
ms.assetid: 814185db-24f9-417f-b3b1-7c5aabb42b45
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9588b150dd795fc2bc5e6c55d8f6e2359f609939
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697691"
---
# <a name="walkthrough-create-a-margin-glyph"></a>Návod: Vytvoření symbolu okraje
Vzhled okrajů editoru můžete přizpůsobit pomocí vlastních rozšíření editoru. Tento návod umístí vlastní glyf na okraji ukazatele vždy, když se v komentáři kódu objeví slovo "todo".

## <a name="prerequisites"></a>Požadavky
 Počínaje Visual Studio 2015, nenainstalujete Visual Studio SDK ze služby stažení. Je součástí volitelné funkce v nastavení sady Visual Studio. VS SDK můžete také nainstalovat později. Další informace naleznete [v tématu Instalace sady Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-mef-project"></a>Vytvoření projektu MEF

1. Vytvořte projekt C# VSIX. (V dialogovém okně **Nový projekt** vyberte možnost **Vizuální C# / Rozšiřitelnost**a potom **v six projectu**.) Pojmenujte `TodoGlyphTest`řešení .

2. Přidejte položku projektu klasifikátoru editoru. Další informace naleznete [v tématu Vytvoření rozšíření se šablonou položky editoru](../extensibility/creating-an-extension-with-an-editor-item-template.md).

3. Odstraňte existující soubory tříd.

## <a name="define-the-glyph"></a>Definování glyfu
 Definujte glyf <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactory> spuštěním rozhraní.

### <a name="to-define-the-glyph"></a>Definování glyfu

1. Přidejte soubor třídy `TodoGlyphFactory`a pojmenujte jej .

2. Přidejte následující kód pomocí deklarací.

     [!code-csharp[VSSDKTodoGlyphTest#1](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_1.cs)]
     [!code-vb[VSSDKTodoGlyphTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_1.vb)]

3. Přidejte třídu s názvem, `TodoGlyphFactory` která implementuje <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactory>.

     [!code-csharp[VSSDKTodoGlyphTest#2](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_2.cs)]
     [!code-vb[VSSDKTodoGlyphTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_2.vb)]

4. Přidejte soukromé pole, které definuje rozměry glyfu.

     [!code-csharp[VSSDKTodoGlyphTest#3](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_3.cs)]
     [!code-vb[VSSDKTodoGlyphTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_3.vb)]

5. Implementujte `GenerateGlyph` definováním prvku uživatelského rozhraní glyfu (UI). `TodoTag`je definována dále v tomto návodu.

     [!code-csharp[VSSDKTodoGlyphTest#4](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_4.cs)]
     [!code-vb[VSSDKTodoGlyphTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_4.vb)]

6. Přidejte třídu s názvem, `TodoGlyphFactoryProvider` která implementuje <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactoryProvider>. Exportovat tuto <xref:Microsoft.VisualStudio.Utilities.NameAttribute> třídu s "TodoGlyph", a <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> po <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> VsTextMarker, a <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> "kód" a TodoTag.

     [!code-csharp[VSSDKTodoGlyphTest#5](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_5.cs)]
     [!code-vb[VSSDKTodoGlyphTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_5.vb)]

7. Implementujte <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactoryProvider.GetGlyphFactory%2A> metodu vytvořením `TodoGlyphFactory`instance .

     [!code-csharp[VSSDKTodoGlyphTest#6](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_6.cs)]
     [!code-vb[VSSDKTodoGlyphTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_6.vb)]

## <a name="define-a-todo-tag-and-tagger"></a>Definování značky a taggeru todo
 Definujte vztah mezi prvkem ui, který jste definovali v předchozích krocích, a okrajem ukazatele. Vytvořte typ značky a tagger a exportujte je pomocí poskytovatele taggeru.

### <a name="to-define-a-todo-tag-and-tagger"></a>Definování značky a taggeru todo

1. Přidejte do projektu nový soubor `TodoTagger`třídy a pojmenujte jej .

2. Přidejte následující importy.

     [!code-csharp[VSSDKTodoGlyphTest#7](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_7.cs)]
     [!code-vb[VSSDKTodoGlyphTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_7.vb)]

3. Přidejte třídu s názvem `TodoTag`.

     [!code-csharp[VSSDKTodoGlyphTest#8](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_8.cs)]
     [!code-vb[VSSDKTodoGlyphTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_8.vb)]

4. Upravte třídu s názvem, `TodoTagger` která implementuje <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> typu `TodoTag`.

     [!code-csharp[VSSDKTodoGlyphTest#9](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_9.cs)]
     [!code-vb[VSSDKTodoGlyphTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_9.vb)]

5. Do `TodoTagger` třídy přidejte soukromá pole pro <xref:Microsoft.VisualStudio.Text.Classification.IClassifier> a pro text, který chcete najít v rozsahu klasifikace.

     [!code-csharp[VSSDKTodoGlyphTest#10](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_10.cs)]
     [!code-vb[VSSDKTodoGlyphTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_10.vb)]

6. Přidejte konstruktor, který nastaví třídění.

     [!code-csharp[VSSDKTodoGlyphTest#11](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_11.cs)]
     [!code-vb[VSSDKTodoGlyphTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_11.vb)]

7. Implementujte <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> metodu vyhledáním všech rozsahů klasifikace, jejichž názvy obsahují slovo "komentář" a jejichž text obsahuje hledaný text. Kdykoli je nalezen hledaný text, <xref:Microsoft.VisualStudio.Text.Tagging.TagSpan%601> posuzte nový typ `TodoTag`.

     [!code-csharp[VSSDKTodoGlyphTest#12](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_12.cs)]
     [!code-vb[VSSDKTodoGlyphTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_12.vb)]

8. Deklarujte `TagsChanged` událost.

     [!code-csharp[VSSDKTodoGlyphTest#13](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_13.cs)]
     [!code-vb[VSSDKTodoGlyphTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_13.vb)]

9. Přidejte třídu `TodoTaggerProvider` s <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider>názvem, která <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> implementuje , <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> a exportujte ji s "kód" a TodoTag.

     [!code-csharp[VSSDKTodoGlyphTest#14](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_14.cs)]
     [!code-vb[VSSDKTodoGlyphTest#14](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_14.vb)]

10. Importujte <xref:Microsoft.VisualStudio.Text.Classification.IClassifierAggregatorService>.

     [!code-csharp[VSSDKTodoGlyphTest#15](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_15.cs)]
     [!code-vb[VSSDKTodoGlyphTest#15](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_15.vb)]

11. Implementujte <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider.CreateTagger%2A> metodu vytvořením `TodoTagger`instance .

     [!code-csharp[VSSDKTodoGlyphTest#16](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_16.cs)]
     [!code-vb[VSSDKTodoGlyphTest#16](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_16.vb)]

## <a name="build-and-test-the-code"></a>Sestavení a testování kódu
 Chcete-li otestovat tento kód, vytvořte řešení TodoGlyphTest a spusťte jej v experimentální instanci.

### <a name="to-build-and-test-the-todoglyphtest-solution"></a>Vytvoření a testování řešení TodoGlyphTest

1. Sestavte řešení.

2. Spusťte projekt stisknutím **klávesy F5**. Spustí se druhá instance sady Visual Studio.

3. Ujistěte se, že se zobrazuje ukazatel. (V nabídce **Nástroje** klepněte na **příkaz Možnosti**. Na stránce **Textový editor** zkontrolujte, zda je **vybrána volba okraje indikátoru.)**

4. Otevřete soubor kódu, který má komentáře. Do jedné z částí komentáře přidejte slovo todo.

5. Světle modrý kruh s tmavě modrým obrysem se zobrazí v okraji ukazatele vlevo od okna kódu.
