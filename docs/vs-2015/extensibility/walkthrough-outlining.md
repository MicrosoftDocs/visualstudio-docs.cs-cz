---
title: 'Návod: Sbalení | Dokumentace Microsoftu'
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
- editors [Visual Studio SDK], new - outlining
ms.assetid: d75a44aa-265a-44d4-9c28-457f59c4ff9f
caps.latest.revision: 31
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 897ff6a39716f424c40fa587d905847a0dbb3682
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51805265"
---
# <a name="walkthrough-outlining"></a>Návod: Sbalení
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Budete moct implementovat založený na jazyce funkce, jako je například sbalování tak, že definujete druhy textu oblastí, které chcete rozbalit nebo sbalit. Můžete definovat oblastí v rámci služby jazyka, nebo můžete definovat vlastní název souboru příponu a obsah zadejte a použít definici oblasti s pouze tímto typem nebo oblasti definice můžete použít k existujícímu typu obsahu (jako je například "text"). Tento návod ukazuje, jak definovat a zobrazení sbalování oblastí.  
  
## <a name="prerequisites"></a>Požadavky  
 Spouští se v sadě Visual Studio 2015, nenainstalujete sadu Visual Studio SDK ze služby Stažení softwaru. Je zahrnut jako volitelná funkce v instalačním programu sady Visual Studio. VS SDK můžete také nainstalovat později. Další informace najdete v tématu [instalace sady Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-managed-extensibility-framework-mef-project"></a>Vytvoření projektu Managed Extensibility Framework (MEF)  
  
#### <a name="to-create-a-mef-project"></a>Chcete-li vytvořit projekt rozhraní MEF  
  
1.  Vytvoření projektu VSIX. Pojmenujte řešení `OutlineRegionTest`.  
  
2.  Přidejte do projektu šablony položky editoru třídění. Další informace najdete v tématu [vytváření rozšíření pomocí šablony položky editoru](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3.  Odstraníte existující soubory tříd.  
  
## <a name="implementing-an-outlining-tagger"></a>Implementace sbalování Označovatel  
 Sbalování oblastí jsou označené nástrojem druh značky (<xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag>). Tato značka poskytuje standardní sbalování chování. Ohraničené oblasti můžete rozbalit nebo sbalit. Ohraničené oblasti je označená jako sbaleného znaménko PLUS nebo mínus, pokud se rozbalí a rozbalená oblast je potřeba svislou čárou.  
  
 Následující kroky ukazují, jak definovat označovatel, který vytvoří sbalování oblastí pro všechny oblasti, které jsou odděleny "[" a "]".  
  
#### <a name="to-implement-an-outlining-tagger"></a>K implementaci sbalování označovatel  
  
1.  Přidejte soubor třídy a pojmenujte ho `OutliningTagger`.  
  
2.  Importujte následující obory názvů.  
  
     [!code-csharp[VSSDKOutlineRegionTest#1](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#1)]
     [!code-vb[VSSDKOutlineRegionTest#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#1)]  
  
3.  Vytvořte třídu s názvem `OutliningTagger`, a jeho implementaci <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601>:  
  
     [!code-csharp[VSSDKOutlineRegionTest#2](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#2)]
     [!code-vb[VSSDKOutlineRegionTest#2](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#2)]  
  
4.  Přidáte některá pole ke sledování textové vyrovnávací paměti a snímek a accumulate sady řádků, které by měly být označeny jako sbalování oblastí. Tento kód obsahuje seznam objektů, které oblasti (chcete zadat později), které představují sbalování oblastí.  
  
     [!code-csharp[VSSDKOutlineRegionTest#3](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#3)]
     [!code-vb[VSSDKOutlineRegionTest#3](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#3)]  
  
5.  Přidat označovatel konstruktor, který inicializuje pole, analyzuje vyrovnávací paměti a přidá obslužnou rutinu události pro <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> událostí.  
  
     [!code-csharp[VSSDKOutlineRegionTest#4](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#4)]
     [!code-vb[VSSDKOutlineRegionTest#4](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#4)]  
  
6.  Implementace <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> zahrnuje metodu, která vytvoří instanci značky. Tento příklad předpokládá, že rozsahy v <xref:Microsoft.VisualStudio.Text.NormalizedSpanCollection> předaný metodě jsou souvislé, i když to nemusí být vždy případu. Tato metoda vytvoří nová značka span pro každou sbalování oblastí.  
  
     [!code-csharp[VSSDKOutlineRegionTest#5](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#5)]
     [!code-vb[VSSDKOutlineRegionTest#5](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#5)]  
  
7.  Deklarace `TagsChanged` obslužné rutiny události.  
  
     [!code-csharp[VSSDKOutlineRegionTest#6](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#6)]
     [!code-vb[VSSDKOutlineRegionTest#6](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#6)]  
  
8.  Přidat `BufferChanged` obslužná rutina události, která reaguje na <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> události analýzou textové vyrovnávací paměti.  
  
     [!code-csharp[VSSDKOutlineRegionTest#7](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#7)]
     [!code-vb[VSSDKOutlineRegionTest#7](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#7)]  
  
9. Přidejte metodu, která analyzuje vyrovnávací paměti. V příkladu, zde je pouze pro ilustraci. Analyzuje synchronně vyrovnávací paměť do vnořených sbalování oblastí.  
  
     [!code-csharp[VSSDKOutlineRegionTest#8](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#8)]
     [!code-vb[VSSDKOutlineRegionTest#8](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#8)]  
  
10. Následující Pomocná metoda získá celé číslo představující úroveň osnovy, tak, aby 1 je pár levé závorky.  
  
     [!code-csharp[VSSDKOutlineRegionTest#9](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#9)]
     [!code-vb[VSSDKOutlineRegionTest#9](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#9)]  
  
11. Následující Pomocná metoda výrazném SnapshotSpan oblast (definované dále v tomto tématu).  
  
     [!code-csharp[VSSDKOutlineRegionTest#10](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#10)]
     [!code-vb[VSSDKOutlineRegionTest#10](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#10)]  
  
12. Následující kód je pouze pro ilustraci. Definuje třídu PartialRegion, která obsahuje číslo řádku a posun zahájení sbalování oblastí a také odkaz na nadřazený oblast (pokud existuje). To umožňuje analyzátor, který má nastavení vnořené sbalování oblastí. Odvozené třídy oblasti obsahuje odkaz na číslo řádku na konec sbalování oblastí.  
  
     [!code-csharp[VSSDKOutlineRegionTest#11](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#11)]
     [!code-vb[VSSDKOutlineRegionTest#11](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#11)]  
  
## <a name="implementing-a-tagger-provider"></a>Implementace zprostředkovatele Označovatel  
 Je nutné exportovat označovatel zprostředkovatele pro vaše označovatel. Přímým připojením vytvoří poskytovatel označovatel `OutliningTagger` vyrovnávací paměti obsahu typu "text" nebo jiný vrátí `OutliningTagger` Pokud vyrovnávací paměť již existuje.  
  
#### <a name="to-implement-a-tagger-provider"></a>Pro implementaci zprostředkovatele označovatel  
  
1.  Vytvořte třídu s názvem `OutliningTaggerProvider` , který implementuje <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider>a exportovat ho pomocí atributů ContentType a typů.  
  
     [!code-csharp[VSSDKOutlineRegionTest#12](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#12)]
     [!code-vb[VSSDKOutlineRegionTest#12](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#12)]  
  
2.  Implementace <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider.CreateTagger%2A> metodu tak, že přidáte `OutliningTagger` vlastností vyrovnávací paměti.  
  
     [!code-csharp[VSSDKOutlineRegionTest#13](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#13)]
     [!code-vb[VSSDKOutlineRegionTest#13](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#13)]  
  
## <a name="building-and-testing-the-code"></a>Vytváření a testování kódu  
 K otestování tohoto kódu sestavte řešení OutlineRegionTest a spusťte v experimentální instanci.  
  
#### <a name="to-build-and-test-the-outlineregiontest-solution"></a>Pro vytváření a testování OutlineRegionTest řešení  
  
1.  Sestavte řešení.  
  
2.  Při spuštění tohoto projektu v ladicím programu, je vytvořena instance druhou instanci aplikace Visual Studio.  
  
3.  Vytvořte textový soubor. Zadejte nějaký text, který obsahuje levou složenou závorku a pravou složenou závorku.  
  
    ```  
    [  
       Hello  
    ]  
    ```  
  
4.  Měla by existovat sbalování oblastí, obsahující oba složené závorky. Byste měli být schopni klepněte na znaménko MINUS nalevo od levou složenou závorku sbalte sbalování oblastí. Když sbalen oblast, na symbol tří teček (...) by se měla zobrazit nalevo od sbaleného regionu a automaticky otevíraného okna obsahující text **najetí na text** by se měla zobrazit při přesunutí ukazatele myši na tři tečky.  
  
## <a name="see-also"></a>Viz také  
 [Návod: Propojení typu obsahu s příponou názvu souboru](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)

