---
title: 'Návod: vytvoření glyfu marže | Microsoft Docs'
description: V tomto návodu se dozvíte, jak přizpůsobit vzhled okrajů editoru pomocí rozšíření vlastních editorů.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- editors [Visual Studio SDK], new - margin glyph
ms.assetid: 814185db-24f9-417f-b3b1-7c5aabb42b45
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 9260b567b65000780ee81226607e0a1c76c5fd46
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105062002"
---
# <a name="walkthrough-create-a-margin-glyph"></a>Návod: vytvoření glyfu marže
Vzhled okrajů editoru lze přizpůsobit pomocí rozšíření vlastních editorů. Tento návod vloží vlastní glyf na okraj indikátoru vždy, když se v komentáři k kódu zobrazí slovo todo.

## <a name="prerequisites"></a>Požadavky
 Od sady Visual Studio 2015 nenainstalujete sadu Visual Studio SDK z webu Stažení softwaru. V instalačním programu sady Visual Studio je zahrnutý jako volitelná funkce. Sadu VS SDK můžete také nainstalovat později. Další informace najdete v tématu [instalace sady Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-mef-project"></a>Vytvořit projekt MEF

1. Vytvoří projekt VSIX v jazyce C#. (V dialogovém okně **Nový projekt** vyberte **Visual C#/rozšiřitelnost** a potom **projekt VSIX**.) Pojmenujte řešení `TodoGlyphTest` .

2. Přidejte položku projektu klasifikátoru editoru. Další informace naleznete v tématu [Vytvoření rozšíření pomocí šablony položky editoru](../extensibility/creating-an-extension-with-an-editor-item-template.md).

3. Odstraňte existující soubory třídy.

## <a name="define-the-glyph"></a>Definovat glyf
 Definujte glyf spuštěním <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactory> rozhraní.

### <a name="to-define-the-glyph"></a>Chcete-li definovat glyf

1. Přidejte soubor třídy a pojmenujte ho `TodoGlyphFactory` .

2. Přidejte následující kód pomocí deklarací.

     [!code-csharp[VSSDKTodoGlyphTest#1](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_1.cs)]
     [!code-vb[VSSDKTodoGlyphTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_1.vb)]

3. Přidejte třídu s názvem `TodoGlyphFactory` , která implementuje <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactory> .

     [!code-csharp[VSSDKTodoGlyphTest#2](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_2.cs)]
     [!code-vb[VSSDKTodoGlyphTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_2.vb)]

4. Přidejte soukromé pole definující rozměry glyfu.

     [!code-csharp[VSSDKTodoGlyphTest#3](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_3.cs)]
     [!code-vb[VSSDKTodoGlyphTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_3.vb)]

5. Implementujte `GenerateGlyph` definováním elementu uživatelského rozhraní glyfu. `TodoTag` je definováno dále v tomto návodu.

     [!code-csharp[VSSDKTodoGlyphTest#4](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_4.cs)]
     [!code-vb[VSSDKTodoGlyphTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_4.vb)]

6. Přidejte třídu s názvem `TodoGlyphFactoryProvider` , která implementuje <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactoryProvider> . Exportujte tuto třídu s <xref:Microsoft.VisualStudio.Utilities.NameAttribute> "TodoGlyph", a <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> za VsTextMarker, a z <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "Code" a a <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> of TodoTag.

     [!code-csharp[VSSDKTodoGlyphTest#5](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_5.cs)]
     [!code-vb[VSSDKTodoGlyphTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_5.vb)]

7. Implementujte <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactoryProvider.GetGlyphFactory%2A> metodu vytvořením instance `TodoGlyphFactory` .

     [!code-csharp[VSSDKTodoGlyphTest#6](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_6.cs)]
     [!code-vb[VSSDKTodoGlyphTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_6.vb)]

## <a name="define-a-todo-tag-and-tagger"></a>Definování značky TODO a autor značky
 Definujte vztah mezi prvkem uživatelského rozhraní, který jste definovali v předchozích krocích a na okraji indikátoru. Vytvořte typ značky a autor značky ho exportujte pomocí poskytovatele autor značky.

### <a name="to-define-a-todo-tag-and-tagger"></a>Definování značky TODO a autor značky

1. Přidejte do projektu nový soubor třídy a pojmenujte ho `TodoTagger` .

2. Přidejte následující importy.

     [!code-csharp[VSSDKTodoGlyphTest#7](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_7.cs)]
     [!code-vb[VSSDKTodoGlyphTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_7.vb)]

3. Přidejte třídu s názvem `TodoTag` .

     [!code-csharp[VSSDKTodoGlyphTest#8](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_8.cs)]
     [!code-vb[VSSDKTodoGlyphTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_8.vb)]

4. Upravte třídu s názvem `TodoTagger` , která implementuje <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> typ `TodoTag` .

     [!code-csharp[VSSDKTodoGlyphTest#9](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_9.cs)]
     [!code-vb[VSSDKTodoGlyphTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_9.vb)]

5. Do `TodoTagger` třídy přidejte soukromá pole pro <xref:Microsoft.VisualStudio.Text.Classification.IClassifier> a pro text, který se má najít v rozpětí klasifikace.

     [!code-csharp[VSSDKTodoGlyphTest#10](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_10.cs)]
     [!code-vb[VSSDKTodoGlyphTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_10.vb)]

6. Přidejte konstruktor, který nastaví klasifikátor.

     [!code-csharp[VSSDKTodoGlyphTest#11](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_11.cs)]
     [!code-vb[VSSDKTodoGlyphTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_11.vb)]

7. Implementujte <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> metodu tak, že vyhledáte všechny rozsahy klasifikace, jejichž názvy obsahují slovo "comment" a text, jehož text obsahuje hledaný text. Pokaždé, když se hledaný text najde, vrátí nový <xref:Microsoft.VisualStudio.Text.Tagging.TagSpan%601> typ `TodoTag` .

     [!code-csharp[VSSDKTodoGlyphTest#12](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_12.cs)]
     [!code-vb[VSSDKTodoGlyphTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_12.vb)]

8. Deklaruje `TagsChanged` událost.

     [!code-csharp[VSSDKTodoGlyphTest#13](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_13.cs)]
     [!code-vb[VSSDKTodoGlyphTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_13.vb)]

9. Přidejte třídu s názvem `TodoTaggerProvider` , která implementuje <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider> , a exportujte ji pomocí typu <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "Code" a <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> třídy TodoTag.

     [!code-csharp[VSSDKTodoGlyphTest#14](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_14.cs)]
     [!code-vb[VSSDKTodoGlyphTest#14](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_14.vb)]

10. Importujte <xref:Microsoft.VisualStudio.Text.Classification.IClassifierAggregatorService> .

     [!code-csharp[VSSDKTodoGlyphTest#15](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_15.cs)]
     [!code-vb[VSSDKTodoGlyphTest#15](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_15.vb)]

11. Implementujte <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider.CreateTagger%2A> metodu vytvořením instance `TodoTagger` .

     [!code-csharp[VSSDKTodoGlyphTest#16](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_16.cs)]
     [!code-vb[VSSDKTodoGlyphTest#16](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_16.vb)]

## <a name="build-and-test-the-code"></a>Sestavení a testování kódu
 Chcete-li otestovat tento kód, sestavte řešení TodoGlyphTest a spusťte ho v experimentální instanci.

### <a name="to-build-and-test-the-todoglyphtest-solution"></a>Sestavení a testování řešení TodoGlyphTest

1. Sestavte řešení.

2. Spusťte projekt stisknutím klávesy **F5**. Spustí se druhá instance sady Visual Studio.

3. Ujistěte se, že se zobrazuje okraj indikátoru. (V nabídce **nástroje** klikněte na příkaz **Možnosti**. Na stránce **textový editor** se ujistěte, že je vybrána možnost **okraj indikátoru** .)

4. Otevřete soubor kódu, který obsahuje komentáře. Přidejte slovo TODO do jednoho z oddílů komentářů.

5. Světle modrý kroužek s tmavě modrým obrysem se zobrazí v okraji indikátoru nalevo od okna Code (kód).
