---
title: 'Návod: vytvoření glyfu marže | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - margin glyph
ms.assetid: 814185db-24f9-417f-b3b1-7c5aabb42b45
caps.latest.revision: 30
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: aa18b900ca44fbb52c646bfdf021beed6e77f504
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68148849"
---
# <a name="walkthrough-creating-a-margin-glyph"></a>Návod: Vytvoření okrajového piktogramu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vzhled okrajů editoru lze přizpůsobit pomocí rozšíření vlastních editorů. Tento návod vloží vlastní glyf na okraj indikátoru vždy, když se v komentáři k kódu zobrazí slovo todo.  
  
## <a name="prerequisites"></a>Předpoklady  
 Od sady Visual Studio 2015 nenainstalujete sadu Visual Studio SDK z webu Stažení softwaru. V instalačním programu sady Visual Studio je zahrnutý jako volitelná funkce. Sadu VS SDK můžete také nainstalovat později. Další informace najdete v tématu [instalace sady Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-mef-project"></a>Vytvoření projektu MEF  
  
1. Vytvoří projekt VSIX v jazyce C#. (V dialogovém okně **Nový projekt** vyberte **Visual C#/rozšiřitelnost**a potom **projekt VSIX**.) Pojmenujte řešení `TodoGlyphTest` .  
  
2. Přidejte položku projektu klasifikátoru editoru. Další informace naleznete v tématu [Vytvoření rozšíření pomocí šablony položky editoru](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3. Odstraňte existující soubory třídy.  
  
## <a name="defining-the-glyph"></a>Definování glyfu  
 Definujte glyf implementující <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactory> rozhraní.  
  
#### <a name="to-define-the-glyph"></a>Chcete-li definovat glyf  
  
1. Přidejte soubor třídy a pojmenujte ho `TodoGlyphFactory` .  
  
2. Přidejte následující deklarace pomocí deklarací.  
  
     [!code-csharp[VSSDKTodoGlyphTest#1](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todoglyphfactory.cs#1)]
     [!code-vb[VSSDKTodoGlyphTest#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todoglyphfactory.vb#1)]  
  
3. Přidejte třídu s názvem `TodoGlyphFactory` , která implementuje <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactory> .  
  
     [!code-csharp[VSSDKTodoGlyphTest#2](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todoglyphfactory.cs#2)]
     [!code-vb[VSSDKTodoGlyphTest#2](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todoglyphfactory.vb#2)]  
  
4. Přidejte soukromé pole definující rozměry glyfu.  
  
     [!code-csharp[VSSDKTodoGlyphTest#3](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todoglyphfactory.cs#3)]
     [!code-vb[VSSDKTodoGlyphTest#3](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todoglyphfactory.vb#3)]  
  
5. Implementujte `GenerateGlyph` definováním elementu uživatelského rozhraní glyfu. `TodoTag` je definováno dále v tomto návodu.  
  
     [!code-csharp[VSSDKTodoGlyphTest#4](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todoglyphfactory.cs#4)]
     [!code-vb[VSSDKTodoGlyphTest#4](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todoglyphfactory.vb#4)]  
  
6. Přidejte třídu s názvem `TodoGlyphFactoryProvider` , která implementuje <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactoryProvider> . Exportujte tuto třídu s <xref:Microsoft.VisualStudio.Utilities.NameAttribute> "TodoGlyph", a <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> za VsTextMarker, a z <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "Code" a a <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> of TodoTag.  
  
     [!code-csharp[VSSDKTodoGlyphTest#5](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todoglyphfactory.cs#5)]
     [!code-vb[VSSDKTodoGlyphTest#5](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todoglyphfactory.vb#5)]  
  
7. Implementujte <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactoryProvider.GetGlyphFactory%2A> metodu vytvořením instance `TodoGlyphFactory` .  
  
     [!code-csharp[VSSDKTodoGlyphTest#6](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todoglyphfactory.cs#6)]
     [!code-vb[VSSDKTodoGlyphTest#6](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todoglyphfactory.vb#6)]  
  
## <a name="defining-a-todo-tag-and-tagger"></a>Definování značky TODO a autor značky  
 Definujte vztah mezi prvkem uživatelského rozhraní, který jste definovali v předchozích krocích, a okrajem indikátoru tak, že vytvoříte typ značky a autor značky a exportujete je pomocí poskytovatele autor značky.  
  
#### <a name="to-define-a-todo-tag-and-tagger"></a>Definování značky TODO a autor značky  
  
1. Přidejte do projektu nový soubor třídy a pojmenujte ho `TodoTagger` .  
  
2. Přidejte následující importy.  
  
     [!code-csharp[VSSDKTodoGlyphTest#7](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs#7)]
     [!code-vb[VSSDKTodoGlyphTest#7](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb#7)]  
  
3. Přidejte třídu s názvem `TodoTag` .  
  
     [!code-csharp[VSSDKTodoGlyphTest#8](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs#8)]
     [!code-vb[VSSDKTodoGlyphTest#8](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb#8)]  
  
4. Upravte třídu s názvem `TodoTagger` , která implementuje <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> typ `TodoTag` .  
  
     [!code-csharp[VSSDKTodoGlyphTest#9](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs#9)]
     [!code-vb[VSSDKTodoGlyphTest#9](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb#9)]  
  
5. Do `TodoTagger` třídy přidejte soukromá pole pro <xref:Microsoft.VisualStudio.Text.Classification.IClassifier> a pro text, který se má najít v rozpětí klasifikace.  
  
     [!code-csharp[VSSDKTodoGlyphTest#10](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs#10)]
     [!code-vb[VSSDKTodoGlyphTest#10](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb#10)]  
  
6. Přidejte konstruktor, který nastaví klasifikátor.  
  
     [!code-csharp[VSSDKTodoGlyphTest#11](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs#11)]
     [!code-vb[VSSDKTodoGlyphTest#11](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb#11)]  
  
7. Implementujte <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> metodu tak, že vyhledáte všechny rozsahy klasifikace, jejichž názvy obsahují slovo "comment" a text, jehož text obsahuje hledaný text. Pokaždé, když se hledaný text najde, vrátí nový <xref:Microsoft.VisualStudio.Text.Tagging.TagSpan%601> typ `TodoTag` .  
  
     [!code-csharp[VSSDKTodoGlyphTest#12](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs#12)]
     [!code-vb[VSSDKTodoGlyphTest#12](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb#12)]  
  
8. Deklaruje `TagsChanged` událost.  
  
     [!code-csharp[VSSDKTodoGlyphTest#13](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs#13)]
     [!code-vb[VSSDKTodoGlyphTest#13](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb#13)]  
  
9. Přidejte třídu s názvem `TodoTaggerProvider` , která implementuje <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider> , a exportujte ji pomocí typu <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "Code" a <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> třídy TodoTag.  
  
     [!code-csharp[VSSDKTodoGlyphTest#14](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs#14)]
     [!code-vb[VSSDKTodoGlyphTest#14](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb#14)]  
  
10. Importujte <xref:Microsoft.VisualStudio.Text.Classification.IClassifierAggregatorService> .  
  
     [!code-csharp[VSSDKTodoGlyphTest#15](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs#15)]
     [!code-vb[VSSDKTodoGlyphTest#15](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb#15)]  
  
11. Implementujte <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider.CreateTagger%2A> metodu vytvořením instance `TodoTagger` .  
  
     [!code-csharp[VSSDKTodoGlyphTest#16](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs#16)]
     [!code-vb[VSSDKTodoGlyphTest#16](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb#16)]  
  
## <a name="building-and-testing-the-code"></a>Sestavování a testování kódu  
 Chcete-li otestovat tento kód, sestavte řešení TodoGlyphTest a spusťte ho v experimentální instanci.  
  
#### <a name="to-build-and-test-the-todoglyphtest-solution"></a>Sestavení a testování řešení TodoGlyphTest  
  
1. Sestavte řešení.  
  
2. Spusťte projekt stisknutím klávesy F5. Vytvoří se druhá instance sady Visual Studio.  
  
3. Ujistěte se, že se zobrazuje okraj indikátoru. (V nabídce **nástroje** klikněte na příkaz **Možnosti**. Na stránce **textový editor** se ujistěte, že je vybrána možnost **okraj indikátoru** .)  
  
4. Otevřete soubor kódu, který obsahuje komentáře. Přidejte slovo TODO do jednoho z oddílů komentářů.  
  
5. V okraji indikátoru nalevo od okna Code by se měla zobrazit světle modrý kroužek, který má tmavě modrý obrys.
