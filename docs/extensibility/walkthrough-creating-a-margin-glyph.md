---
title: 'Návod: Vytvoření okrajového piktogramu | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - margin glyph
ms.assetid: 814185db-24f9-417f-b3b1-7c5aabb42b45
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 1ac8d70c401d543afe73ac14d6f8617e5f375482
ms.sourcegitcommit: 1c2ed640512ba613b3bbbc9ce348e28be6ca3e45
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/03/2018
ms.locfileid: "39497814"
---
# <a name="walkthrough-create-a-margin-glyph"></a>Návod: Vytvoření okrajového piktogramu
Přizpůsobení vzhledu okraje editoru pomocí rozšíření vlastní editor. Tento názorný postup vloží vlastní piktogram na okraj indikátoru pokaždé, když se slova "todo" uveden v komentáři kódu.  
  
## <a name="prerequisites"></a>Požadavky  
 Spouští se v sadě Visual Studio 2015, nenainstalujete sadu Visual Studio SDK ze služby Stažení softwaru. Je zahrnutý jako volitelná funkce v instalačním programu sady Visual Studio. VS SDK můžete také nainstalovat později. Další informace najdete v tématu [instalace sady Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="create-a-mef-project"></a>Vytvořit projekt rozhraní MEF  
  
1.  Vytvořte projekt VSIX C#. (V **nový projekt** dialogového okna, vyberte **Visual C# / rozšíření**, pak **projekt VSIX**.) Pojmenujte řešení `TodoGlyphTest`.  
  
2.  Přidání položky projektu Editor třídění. Další informace najdete v tématu [vytváření rozšíření pomocí šablony položky editoru](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3.  Odstraníte existující soubory tříd.  
  
## <a name="define-the-glyph"></a>Definování glyf  
 Definování piktogram spuštěním <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactory> rozhraní.  
  
### <a name="to-define-the-glyph"></a>Chcete-li definovat glyf  
  
1.  Přidejte soubor třídy a pojmenujte ho `TodoGlyphFactory`.  
  
2.  Přidejte následující kód pomocí deklarace.  
  
     [!code-csharp[VSSDKTodoGlyphTest#1](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_1.cs)]
     [!code-vb[VSSDKTodoGlyphTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_1.vb)]  
  
3.  Přidejte třídu pojmenovanou `TodoGlyphFactory` , který implementuje <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactory>.  
  
     [!code-csharp[VSSDKTodoGlyphTest#2](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_2.cs)]
     [!code-vb[VSSDKTodoGlyphTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_2.vb)]  
  
4.  Přidáte soukromé pole, která definuje rozměry glyf.  
  
     [!code-csharp[VSSDKTodoGlyphTest#3](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_3.cs)]
     [!code-vb[VSSDKTodoGlyphTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_3.vb)]  
  
5.  Implementace `GenerateGlyph` definováním prvek piktogram uživatelského rozhraní (UI). `TodoTag` dále v tomto návodu je definována.  
  
     [!code-csharp[VSSDKTodoGlyphTest#4](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_4.cs)]
     [!code-vb[VSSDKTodoGlyphTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_4.vb)]  
  
6.  Přidejte třídu pojmenovanou `TodoGlyphFactoryProvider` , který implementuje <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactoryProvider>. Export této třídy s <xref:Microsoft.VisualStudio.Utilities.NameAttribute> z "TodoGlyph" <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> z po VsTextMarker <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "kód" a <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> z TodoTag.  
  
     [!code-csharp[VSSDKTodoGlyphTest#5](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_5.cs)]
     [!code-vb[VSSDKTodoGlyphTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_5.vb)]  
  
7.  Implementace <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactoryProvider.GetGlyphFactory%2A> metoda po vytvoření instance `TodoGlyphFactory`.  
  
     [!code-csharp[VSSDKTodoGlyphTest#6](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_6.cs)]
     [!code-vb[VSSDKTodoGlyphTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_6.vb)]  
  
## <a name="define-a-todo-tag-and-tagger"></a>Zadejte značku Todo a označovatel  
 Definování vztahů mezi prvek uživatelského rozhraní, který jste definovali v předchozím kroku a okraj indikátoru. Vytvořit typ značky a označovatel a exportujte ho pomocí označovatel poskytovatele.  
  
### <a name="to-define-a-todo-tag-and-tagger"></a>Chcete-li definovat todo značku a označovatel  
  
1.  Přidejte nový soubor třídy do projektu a pojmenujte ho `TodoTagger`.  
  
2.  Přidejte následující importy.  
  
     [!code-csharp[VSSDKTodoGlyphTest#7](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_7.cs)]
     [!code-vb[VSSDKTodoGlyphTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_7.vb)]  
  
3.  Přidejte třídu pojmenovanou `TodoTag`.  
  
     [!code-csharp[VSSDKTodoGlyphTest#8](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_8.cs)]
     [!code-vb[VSSDKTodoGlyphTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_8.vb)]  
  
4.  Upravte třídu s názvem `TodoTagger` , který implementuje <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> typu `TodoTag`.  
  
     [!code-csharp[VSSDKTodoGlyphTest#9](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_9.cs)]
     [!code-vb[VSSDKTodoGlyphTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_9.vb)]  
  
5.  K `TodoTagger` třídy, přidejte privátní pole pro <xref:Microsoft.VisualStudio.Text.Classification.IClassifier> a text k vyhledání v příslušné klasifikaci zahrnuje.  
  
     [!code-csharp[VSSDKTodoGlyphTest#10](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_10.cs)]
     [!code-vb[VSSDKTodoGlyphTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_10.vb)]  
  
6.  Přidáte konstruktor, který nastaví třídění.  
  
     [!code-csharp[VSSDKTodoGlyphTest#11](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_11.cs)]
     [!code-vb[VSSDKTodoGlyphTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_11.vb)]  
  
7.  Implementace <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> metoda tím, že hledá všechny klasifikace zahrnuje, jejichž názvy obsahují slovo "komentář" a jejichž text obsahuje hledaný text. Pokaždé, když se hledaný text nenajde, yield zpět nový <xref:Microsoft.VisualStudio.Text.Tagging.TagSpan%601> typu `TodoTag`.  
  
     [!code-csharp[VSSDKTodoGlyphTest#12](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_12.cs)]
     [!code-vb[VSSDKTodoGlyphTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_12.vb)]  
  
8.  Deklarace `TagsChanged` událostí.  
  
     [!code-csharp[VSSDKTodoGlyphTest#13](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_13.cs)]
     [!code-vb[VSSDKTodoGlyphTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_13.vb)]  
  
9. Přidejte třídu pojmenovanou `TodoTaggerProvider` , který implementuje <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider>a exportujte ho pomocí <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "kód" a <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> z TodoTag.  
  
     [!code-csharp[VSSDKTodoGlyphTest#14](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_14.cs)]
     [!code-vb[VSSDKTodoGlyphTest#14](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_14.vb)]  
  
10. Import <xref:Microsoft.VisualStudio.Text.Classification.IClassifierAggregatorService>.  
  
     [!code-csharp[VSSDKTodoGlyphTest#15](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_15.cs)]
     [!code-vb[VSSDKTodoGlyphTest#15](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_15.vb)]  
  
11. Implementace <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider.CreateTagger%2A> metoda po vytvoření instance `TodoTagger`.  
  
     [!code-csharp[VSSDKTodoGlyphTest#16](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_16.cs)]
     [!code-vb[VSSDKTodoGlyphTest#16](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_16.vb)]  
  
## <a name="build-and-test-the-code"></a>Vytváření a testování kódu  
 K otestování tohoto kódu sestavte řešení TodoGlyphTest a spusťte v experimentální instanci.  
  
### <a name="to-build-and-test-the-todoglyphtest-solution"></a>Pro vytváření a testování TodoGlyphTest řešení  
  
1.  Sestavte řešení.  
  
2.  Spusťte projekt stisknutím kombinace kláves **F5**. Druhou instanci aplikace Visual Studio spustí.  
  
3.  Ujistěte se, že je zobrazen indikátor okraje. (Na **nástroje** nabídky, klikněte na tlačítko **možnosti**. Na **textový Editor** stránky, ujistěte se, že **okraj indikátoru** je vybrán.)  
  
4.  Otevřete soubor kódu, který má komentáře. Přidáte slovo "todo" do jedné ze Poznámka částí.  
  
5.  Světle modrý kroužek s tmavě modrou osnovy se zobrazí v okraj indikátoru nalevo od okna kódu.