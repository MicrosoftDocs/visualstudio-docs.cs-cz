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
ms.openlocfilehash: ec5eecef40220c2cf2d4e3f1ece8eb5eb763bdeb
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2021
ms.locfileid: "106217408"
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

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todoglyphfactory.cs" id="Snippet1":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todoglyphfactory.vb" id="Snippet1":::

3. Přidejte třídu s názvem `TodoGlyphFactory` , která implementuje <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactory> .

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todoglyphfactory.cs" id="Snippet2":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todoglyphfactory.vb" id="Snippet2":::

4. Přidejte soukromé pole definující rozměry glyfu.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todoglyphfactory.cs" id="Snippet3":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todoglyphfactory.vb" id="Snippet3":::

5. Implementujte `GenerateGlyph` definováním elementu uživatelského rozhraní glyfu. `TodoTag` je definováno dále v tomto návodu.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todoglyphfactory.cs" id="Snippet4":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todoglyphfactory.vb" id="Snippet4":::

6. Přidejte třídu s názvem `TodoGlyphFactoryProvider` , která implementuje <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactoryProvider> . Exportujte tuto třídu s <xref:Microsoft.VisualStudio.Utilities.NameAttribute> "TodoGlyph", a <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> za VsTextMarker, a z <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "Code" a a <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> of TodoTag.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todoglyphfactory.cs" id="Snippet5":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todoglyphfactory.vb" id="Snippet5":::

7. Implementujte <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactoryProvider.GetGlyphFactory%2A> metodu vytvořením instance `TodoGlyphFactory` .

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todoglyphfactory.cs" id="Snippet6":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todoglyphfactory.vb" id="Snippet6":::

## <a name="define-a-todo-tag-and-tagger"></a>Definování značky TODO a autor značky
 Definujte vztah mezi prvkem uživatelského rozhraní, který jste definovali v předchozích krocích a na okraji indikátoru. Vytvořte typ značky a autor značky ho exportujte pomocí poskytovatele autor značky.

### <a name="to-define-a-todo-tag-and-tagger"></a>Definování značky TODO a autor značky

1. Přidejte do projektu nový soubor třídy a pojmenujte ho `TodoTagger` .

2. Přidejte následující importy.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs" id="Snippet7":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb" id="Snippet7":::

3. Přidejte třídu s názvem `TodoTag` .

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs" id="Snippet8":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb" id="Snippet8":::

4. Upravte třídu s názvem `TodoTagger` , která implementuje <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> typ `TodoTag` .

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs" id="Snippet9":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb" id="Snippet9":::

5. Do `TodoTagger` třídy přidejte soukromá pole pro <xref:Microsoft.VisualStudio.Text.Classification.IClassifier> a pro text, který se má najít v rozpětí klasifikace.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs" id="Snippet10":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb" id="Snippet10":::

6. Přidejte konstruktor, který nastaví klasifikátor.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs" id="Snippet11":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb" id="Snippet11":::

7. Implementujte <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> metodu tak, že vyhledáte všechny rozsahy klasifikace, jejichž názvy obsahují slovo "comment" a text, jehož text obsahuje hledaný text. Pokaždé, když se hledaný text najde, vrátí nový <xref:Microsoft.VisualStudio.Text.Tagging.TagSpan%601> typ `TodoTag` .

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs" id="Snippet12":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb" id="Snippet12":::

8. Deklaruje `TagsChanged` událost.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs" id="Snippet13":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb" id="Snippet13":::

9. Přidejte třídu s názvem `TodoTaggerProvider` , která implementuje <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider> , a exportujte ji pomocí typu <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "Code" a <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> třídy TodoTag.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs" id="Snippet14":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb" id="Snippet14":::

10. Importujte <xref:Microsoft.VisualStudio.Text.Classification.IClassifierAggregatorService> .

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs" id="Snippet15":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb" id="Snippet15":::

11. Implementujte <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider.CreateTagger%2A> metodu vytvořením instance `TodoTagger` .

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs" id="Snippet16":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb" id="Snippet16":::

## <a name="build-and-test-the-code"></a>Sestavení a testování kódu
 Chcete-li otestovat tento kód, sestavte řešení TodoGlyphTest a spusťte ho v experimentální instanci.

### <a name="to-build-and-test-the-todoglyphtest-solution"></a>Sestavení a testování řešení TodoGlyphTest

1. Sestavte řešení.

2. Spusťte projekt stisknutím klávesy **F5**. Spustí se druhá instance sady Visual Studio.

3. Ujistěte se, že se zobrazuje okraj indikátoru. (V nabídce **nástroje** klikněte na příkaz **Možnosti**. Na stránce **textový editor** se ujistěte, že je vybrána možnost **okraj indikátoru** .)

4. Otevřete soubor kódu, který obsahuje komentáře. Přidejte slovo TODO do jednoho z oddílů komentářů.

5. Světle modrý kroužek s tmavě modrým obrysem se zobrazí v okraji indikátoru nalevo od okna Code (kód).
