---
title: 'Návod: sbalení | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - outlining
ms.assetid: d75a44aa-265a-44d4-9c28-457f59c4ff9f
caps.latest.revision: 31
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7c1dd3d28b9978b52c95b5ff905d57720ed10f5d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68201959"
---
# <a name="walkthrough-outlining"></a>Návod: Sbalení
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Můžete implementovat funkce založené na jazyce, jako je sbalení, a to definováním druhů textových oblastí, které chcete rozbalit nebo sbalit. Oblasti můžete definovat v kontextu jazykové služby, případně můžete definovat vlastní příponu názvu souboru a typ obsahu a použít definici oblasti jenom na tento typ, nebo můžete použít definice oblastí na existující typ obsahu (například "text"). Tento návod ukazuje, jak definovat a zobrazit oblasti osnovy.  
  
## <a name="prerequisites"></a>Předpoklady  
 Od sady Visual Studio 2015 nenainstalujete sadu Visual Studio SDK z webu Stažení softwaru. V instalačním programu sady Visual Studio je zahrnutý jako volitelná funkce. Sadu VS SDK můžete také nainstalovat později. Další informace najdete v tématu [instalace sady Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-managed-extensibility-framework-mef-project"></a>Vytvoření projektu Managed Extensibility Framework (MEF)  
  
#### <a name="to-create-a-mef-project"></a>Vytvoření projektu MEF  
  
1. Vytvořte projekt VSIX. Pojmenujte řešení `OutlineRegionTest` .  
  
2. Přidejte do projektu šablonu položky klasifikátoru editoru. Další informace naleznete v tématu [Vytvoření rozšíření pomocí šablony položky editoru](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3. Odstraňte existující soubory třídy.  
  
## <a name="implementing-an-outlining-tagger"></a>Implementace autor značkyování osnovy  
 Oblasti sbalení jsou označeny druhem značky ( <xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag> ). Tato značka poskytuje standardní chování při sbalení. Oblast s obrysem může být rozbalená nebo sbalená. Ohraničená oblast je označena znaménkem PLUS, pokud je sbalena, nebo znaménkem mínus, pokud je rozbalena, a rozbalená oblast je ohraničena svislou čárou.  
  
 Následující kroky ukazují, jak definovat autor značky, který vytváří oblasti osnovy pro všechny oblasti, které jsou odděleny "[" a "]".  
  
#### <a name="to-implement-an-outlining-tagger"></a>Implementace autor značkyování osnovy  
  
1. Přidejte soubor třídy a pojmenujte ho `OutliningTagger` .  
  
2. Importujte následující obory názvů.  
  
     [!code-csharp[VSSDKOutlineRegionTest#1](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#1)]
     [!code-vb[VSSDKOutlineRegionTest#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#1)]  
  
3. Vytvořte třídu s názvem `OutliningTagger` a proveďte její implementaci <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> :  
  
     [!code-csharp[VSSDKOutlineRegionTest#2](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#2)]
     [!code-vb[VSSDKOutlineRegionTest#2](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#2)]  
  
4. Přidejte některá pole ke sledování vyrovnávací paměti a snímku textu a Sestavujte sady řádků, které mají být označeny jako oblasti pro sbalení. Tento kód zahrnuje seznam objektů oblastí (pro pozdější definování), které reprezentují oblasti sbalení.  
  
     [!code-csharp[VSSDKOutlineRegionTest#3](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#3)]
     [!code-vb[VSSDKOutlineRegionTest#3](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#3)]  
  
5. Přidejte konstruktor autor značky, který inicializuje pole, analyzuje vyrovnávací paměť a přidá do události obslužnou rutinu události <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> .  
  
     [!code-csharp[VSSDKOutlineRegionTest#4](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#4)]
     [!code-vb[VSSDKOutlineRegionTest#4](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#4)]  
  
6. Implementujte <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> metodu, která vytvoří instanci rozsahů značek. Tento příklad předpokládá, že rozsahy v <xref:Microsoft.VisualStudio.Text.NormalizedSpanCollection> předané metodě jsou souvislé, přestože to nemusí vždy být případ. Tato metoda vytvoří instanci nového rozsahu značek pro každou oblast sbalení.  
  
     [!code-csharp[VSSDKOutlineRegionTest#5](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#5)]
     [!code-vb[VSSDKOutlineRegionTest#5](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#5)]  
  
7. Deklarujte `TagsChanged` obslužnou rutinu události.  
  
     [!code-csharp[VSSDKOutlineRegionTest#6](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#6)]
     [!code-vb[VSSDKOutlineRegionTest#6](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#6)]  
  
8. Přidejte `BufferChanged` obslužnou rutinu události, která reaguje na události analýzou <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> vyrovnávací paměti textu.  
  
     [!code-csharp[VSSDKOutlineRegionTest#7](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#7)]
     [!code-vb[VSSDKOutlineRegionTest#7](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#7)]  
  
9. Přidejte metodu, která analyzuje vyrovnávací paměť. Zde uvedený příklad slouží pouze pro ilustraci. Asynchronně analyzuje vyrovnávací paměť na vnořené oblasti osnovy.  
  
     [!code-csharp[VSSDKOutlineRegionTest#8](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#8)]
     [!code-vb[VSSDKOutlineRegionTest#8](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#8)]  
  
10. Následující pomocná metoda získá celé číslo, které představuje úroveň sbalení, například 1 je dvojice složených závorek.  
  
     [!code-csharp[VSSDKOutlineRegionTest#9](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#9)]
     [!code-vb[VSSDKOutlineRegionTest#9](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#9)]  
  
11. Následující pomocná metoda překládá oblast (definovaná dále v tomto tématu) do SnapshotSpan.  
  
     [!code-csharp[VSSDKOutlineRegionTest#10](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#10)]
     [!code-vb[VSSDKOutlineRegionTest#10](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#10)]  
  
12. Následující kód je určen pouze pro ilustraci. Definuje třídu PartialRegion, která obsahuje číslo řádku a posun začátku oblasti osnovy a také odkaz na nadřazenou oblast (pokud existuje). To umožňuje, aby analyzátor nastavil vnořené oblasti sbalení. Odvozená třída oblasti obsahuje odkaz na číslo řádku na konci oblasti sbalení.  
  
     [!code-csharp[VSSDKOutlineRegionTest#11](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#11)]
     [!code-vb[VSSDKOutlineRegionTest#11](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#11)]  
  
## <a name="implementing-a-tagger-provider"></a>Implementace poskytovatele autor značky  
 Pro svůj autor značky musíte exportovat poskytovatele autor značky. Poskytovatel autor značky vytvoří `OutliningTagger` pro vyrovnávací paměť typu "text", nebo jinak vrátí, `OutliningTagger` Pokud vyrovnávací paměť již jednu obsahuje.  
  
#### <a name="to-implement-a-tagger-provider"></a>Implementace poskytovatele autor značky  
  
1. Vytvořte třídu s názvem `OutliningTaggerProvider` , která implementuje <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider> , a exportujte ji pomocí atributů ContentType a TagType.  
  
     [!code-csharp[VSSDKOutlineRegionTest#12](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#12)]
     [!code-vb[VSSDKOutlineRegionTest#12](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#12)]  
  
2. Implementujte <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider.CreateTagger%2A> metodu přidáním `OutliningTagger` do vlastností vyrovnávací paměti.  
  
     [!code-csharp[VSSDKOutlineRegionTest#13](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#13)]
     [!code-vb[VSSDKOutlineRegionTest#13](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#13)]  
  
## <a name="building-and-testing-the-code"></a>Sestavování a testování kódu  
 Chcete-li otestovat tento kód, sestavte řešení OutlineRegionTest a spusťte ho v experimentální instanci.  
  
#### <a name="to-build-and-test-the-outlineregiontest-solution"></a>Sestavení a testování řešení OutlineRegionTest  
  
1. Sestavte řešení.  
  
2. Při spuštění tohoto projektu v ladicím programu je vytvořena instance druhé instance aplikace Visual Studio.  
  
3. Vytvořte textový soubor. Zadejte nějaký text, který obsahuje levou složenou závorku a pravou složenou závorku.  
  
    ```  
    [  
       Hello  
    ]  
    ```  
  
4. Měla by existovat oblast osnovy, která obsahuje obě složené závorky. Měli byste být schopni kliknout na symbol mínus vlevo od levé složené závorky, abyste mohli sbalit oblast osnovy. Když je oblast sbalena, symbol tři tečky (...) by se měl objevit nalevo od sbalené oblasti a automaticky otevírané okno obsahující text **najetí myší** by se mělo zobrazit při přesunutí ukazatele myši na tři tečky.  
  
## <a name="see-also"></a>Viz také  
 [Návod: Propojení typu obsahu s příponou názvu souboru](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
