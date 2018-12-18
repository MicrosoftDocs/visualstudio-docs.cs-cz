---
title: 'Návod: Sbalení | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - outlining
ms.assetid: d75a44aa-265a-44d4-9c28-457f59c4ff9f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 740ed444770a440b54fe61b0c8ec8189691fe9a1
ms.sourcegitcommit: ef828606e9758c7a42a2f0f777c57b2d39041ac3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/06/2018
ms.locfileid: "39566921"
---
# <a name="walkthrough-outlining"></a>Návod: Sbalení
Nastavení funkce založené na jazyce jako třeba sbalování tak, že definujete druhy textu oblastí, které chcete rozbalit nebo sbalit. Můžete definovat oblastí v rámci služby jazyka, nebo definovat vlastní název souboru příponu a obsah zadejte a použít definici oblasti pouze tento typ nebo použít definice oblastí k existujícímu typu obsahu (jako je například "text"). Tento návod ukazuje, jak definovat a zobrazení sbalování oblastí.  
  
## <a name="prerequisites"></a>Požadavky  
 Spouští se v sadě Visual Studio 2015, nenainstalujete sadu Visual Studio SDK ze služby Stažení softwaru. Je zahrnutý jako volitelná funkce v instalačním programu sady Visual Studio. VS SDK můžete také nainstalovat později. Další informace najdete v tématu [instalace sady Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="create-a-managed-extensibility-framework-mef-project"></a>Vytvoření projektu Managed Extensibility Framework (MEF)  
  
### <a name="to-create-a-mef-project"></a>Chcete-li vytvořit projekt rozhraní MEF  
  
1.  Vytvořte projekt VSIX. Pojmenujte řešení `OutlineRegionTest`.  
  
2.  Přidejte do projektu šablony položky editoru třídění. Další informace najdete v tématu [vytváření rozšíření pomocí šablony položky editoru](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3.  Odstraníte existující soubory tříd.  
  
## <a name="implement-an-outlining-tagger"></a>Implementace sbalování označovatel  
 Sbalování oblastí jsou označené nástrojem druh značky (<xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag>). Tato značka poskytuje standardní sbalování chování. Ohraničené oblasti můžete rozbalit nebo sbalit. Ohraničené oblasti označené znaménko Plus (**+**) sbaleného nebo mínus (**-**) Pokud se rozbalí a rozbalená oblast je potřeba svislou čárou.  
  
 Následující kroky ukazují, jak definovat označovatel, který vytvoří sbalování oblastí pro všechny oblasti oddělen složenými závorkami (**[**,**]**).  
  
### <a name="to-implement-an-outlining-tagger"></a>K implementaci sbalování označovatel  
  
1.  Přidejte soubor třídy a pojmenujte ho `OutliningTagger`.  
  
2.  Importujte následující obory názvů.  
  
     [!code-csharp[VSSDKOutlineRegionTest#1](../extensibility/codesnippet/CSharp/walkthrough-outlining_1.cs)]
     [!code-vb[VSSDKOutlineRegionTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_1.vb)]  
  
3.  Vytvořte třídu s názvem `OutliningTagger`, a jeho implementaci <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601>:  
  
     [!code-csharp[VSSDKOutlineRegionTest#2](../extensibility/codesnippet/CSharp/walkthrough-outlining_2.cs)]
     [!code-vb[VSSDKOutlineRegionTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_2.vb)]  
  
4.  Přidáte některá pole ke sledování textové vyrovnávací paměti a snímek a accumulate sady řádků, které by měly být označeny jako sbalování oblastí. Tento kód obsahuje seznam objektů, které oblasti (chcete zadat později), které představují sbalování oblastí.  
  
     [!code-csharp[VSSDKOutlineRegionTest#3](../extensibility/codesnippet/CSharp/walkthrough-outlining_3.cs)]
     [!code-vb[VSSDKOutlineRegionTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_3.vb)]  
  
5.  Přidat označovatel konstruktor, který inicializuje pole, analyzuje vyrovnávací paměti a přidá obslužnou rutinu události pro <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> událostí.  
  
     [!code-csharp[VSSDKOutlineRegionTest#4](../extensibility/codesnippet/CSharp/walkthrough-outlining_4.cs)]
     [!code-vb[VSSDKOutlineRegionTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_4.vb)]  
  
6.  Implementace <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> zahrnuje metodu, která vytvoří instanci značky. Tento příklad předpokládá, že rozsahy v <xref:Microsoft.VisualStudio.Text.NormalizedSpanCollection> předaný metodě jsou souvislé, i když nemusí být vždy případu. Tato metoda vytvoří nová značka span pro každou sbalování oblastí.  
  
     [!code-csharp[VSSDKOutlineRegionTest#5](../extensibility/codesnippet/CSharp/walkthrough-outlining_5.cs)]
     [!code-vb[VSSDKOutlineRegionTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_5.vb)]  
  
7.  Deklarace `TagsChanged` obslužné rutiny události.  
  
     [!code-csharp[VSSDKOutlineRegionTest#6](../extensibility/codesnippet/CSharp/walkthrough-outlining_6.cs)]
     [!code-vb[VSSDKOutlineRegionTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_6.vb)]  
  
8.  Přidat `BufferChanged` obslužná rutina události, která reaguje na <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> události analýzou textové vyrovnávací paměti.  
  
     [!code-csharp[VSSDKOutlineRegionTest#7](../extensibility/codesnippet/CSharp/walkthrough-outlining_7.cs)]
     [!code-vb[VSSDKOutlineRegionTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_7.vb)]  
  
9. Přidejte metodu, která analyzuje vyrovnávací paměti. V příkladu, zde je pouze pro ilustraci. Analyzuje synchronně vyrovnávací paměť do vnořených sbalování oblastí.  
  
     [!code-csharp[VSSDKOutlineRegionTest#8](../extensibility/codesnippet/CSharp/walkthrough-outlining_8.cs)]
     [!code-vb[VSSDKOutlineRegionTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_8.vb)]  
  
10. Následující Pomocná metoda získá celé číslo představující úroveň osnovy, tak, aby 1 je pár levé závorky.  
  
     [!code-csharp[VSSDKOutlineRegionTest#9](../extensibility/codesnippet/CSharp/walkthrough-outlining_9.cs)]
     [!code-vb[VSSDKOutlineRegionTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_9.vb)]  
  
11. Následující Pomocná metoda výrazném SnapshotSpan oblast (definované dále v tomto článku).  
  
     [!code-csharp[VSSDKOutlineRegionTest#10](../extensibility/codesnippet/CSharp/walkthrough-outlining_10.cs)]
     [!code-vb[VSSDKOutlineRegionTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_10.vb)]  
  
12. Následující kód je pouze pro ilustraci. Definuje třídu PartialRegion, která obsahuje číslo řádku a posun zahájení sbalování oblastí a odkaz na nadřazený oblast (pokud existuje). Tento kód povoluje analyzátor, který má nastavení vnořené sbalování oblastí. Odvozené třídy oblasti obsahuje odkaz na číslo řádku na konec sbalování oblastí.  
  
     [!code-csharp[VSSDKOutlineRegionTest#11](../extensibility/codesnippet/CSharp/walkthrough-outlining_11.cs)]
     [!code-vb[VSSDKOutlineRegionTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_11.vb)]  
  
## <a name="implement-a-tagger-provider"></a>Implementace zprostředkovatele označovatel  
 Exportujte označovatel zprostředkovatele pro vaše označovatel. Přímým připojením vytvoří poskytovatel označovatel `OutliningTagger` vyrovnávací paměti obsahu typu "text" nebo jiný vrátí `OutliningTagger` Pokud vyrovnávací paměť již existuje.  
  
### <a name="to-implement-a-tagger-provider"></a>Pro implementaci zprostředkovatele označovatel  
  
1.  Vytvořte třídu s názvem `OutliningTaggerProvider` , který implementuje <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider>a exportovat ho pomocí atributů ContentType a typů.  
  
     [!code-csharp[VSSDKOutlineRegionTest#12](../extensibility/codesnippet/CSharp/walkthrough-outlining_12.cs)]
     [!code-vb[VSSDKOutlineRegionTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_12.vb)]  
  
2.  Implementace <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider.CreateTagger%2A> metodu tak, že přidáte `OutliningTagger` vlastností vyrovnávací paměti.  
  
     [!code-csharp[VSSDKOutlineRegionTest#13](../extensibility/codesnippet/CSharp/walkthrough-outlining_13.cs)]
     [!code-vb[VSSDKOutlineRegionTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_13.vb)]  
  
## <a name="build-and-test-the-code"></a>Vytváření a testování kódu  
 K otestování tohoto kódu sestavte řešení OutlineRegionTest a spusťte v experimentální instanci.  
  
### <a name="to-build-and-test-the-outlineregiontest-solution"></a>Pro vytváření a testování OutlineRegionTest řešení  
  
1.  Sestavte řešení.  
  
2.  Při spuštění tohoto projektu v ladicím programu se spustí druhé instanci aplikace Visual Studio.  
  
3.  Vytvořte textový soubor. Zadejte nějaký text, který obsahuje závorky otevírací a uzavírací hranaté závorce.  
  
    ```  
    [  
       Hello  
    ]  
    ```  
  
4.  Měla by existovat sbalování oblastí, obsahující oba závorky. Byste měli být schopni klepněte na znaménko Minus nalevo od levou závorku sbalte sbalování oblastí. Když sbalen oblast, na symbol tří teček (*...* ) by se měla zobrazit nalevo od sbaleného regionu a automaticky otevíraného okna obsahující text **najetí na text** by se měla zobrazit při přesunutí ukazatele myši na tři tečky.  
  
## <a name="see-also"></a>Viz také:  
 [Návod: Propojení typ obsahu, který má příponu názvu souboru](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)