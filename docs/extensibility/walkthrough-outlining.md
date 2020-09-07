---
title: 'Návod: sbalení | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- editors [Visual Studio SDK], new - outlining
ms.assetid: d75a44aa-265a-44d4-9c28-457f59c4ff9f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- csharp
- vb
ms.openlocfilehash: 6e3e60fe873d7bcb512e56c844e76fcbef037d42
ms.sourcegitcommit: 5caad925ca0b5d136416144a279e984836d8f28c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2020
ms.locfileid: "89508922"
---
# <a name="walkthrough-outlining"></a>Návod: Sbalení
Nastavte funkce založené na jazycích, jako je například sbalení, definováním druhů textových oblastí, které chcete rozbalit nebo sbalit. Můžete definovat oblasti v kontextu jazykové služby nebo definovat vlastní příponu názvu souboru a typ obsahu a použít definici oblasti jenom na tento typ, nebo použít definice oblastí na existující typ obsahu (například "text"). Tento návod ukazuje, jak definovat a zobrazit oblasti osnovy.

## <a name="prerequisites"></a>Předpoklady
 Od sady Visual Studio 2015 nenainstalujete sadu Visual Studio SDK z webu Stažení softwaru. V instalačním programu sady Visual Studio je zahrnutý jako volitelná funkce. Sadu VS SDK můžete také nainstalovat později. Další informace najdete v tématu [instalace sady Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-managed-extensibility-framework-mef-project"></a>Vytvořit projekt Managed Extensibility Framework (MEF)

### <a name="to-create-a-mef-project"></a>Vytvoření projektu MEF

1. Vytvořte projekt VSIX. Pojmenujte řešení `OutlineRegionTest` .

2. Přidejte do projektu šablonu položky klasifikátoru editoru. Další informace naleznete v tématu [Vytvoření rozšíření pomocí šablony položky editoru](../extensibility/creating-an-extension-with-an-editor-item-template.md).

3. Odstraňte existující soubory třídy.

## <a name="implement-an-outlining-tagger"></a>Implementace autor značkyování osnovy
 Oblasti sbalení jsou označeny druhem značky ( <xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag> ). Tato značka poskytuje standardní chování při sbalení. Oblast s obrysem může být rozbalená nebo sbalená. Ohraničená oblast je označena znaménkem plus ( **+** ), pokud je sbalena, nebo znaménkem mínus ( **-** ), pokud je rozbalena, a rozbalená oblast je ohraničena svislou čárou.

 Následující kroky ukazují, jak definovat autor značky, který vytváří oblasti osnovy pro všechny oblasti oddělené hranatými závorkami (**[**,**]**).

### <a name="to-implement-an-outlining-tagger"></a>Implementace autor značkyování osnovy

1. Přidejte soubor třídy a pojmenujte ho `OutliningTagger` .

2. Importujte následující obory názvů.

     [!code-csharp[VSSDKOutlineRegionTest#1](../extensibility/codesnippet/CSharp/walkthrough-outlining_1.cs)]
     [!code-vb[VSSDKOutlineRegionTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_1.vb)]

3. Vytvořte třídu s názvem `OutliningTagger` a proveďte její implementaci <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> :

     [!code-csharp[VSSDKOutlineRegionTest#2](../extensibility/codesnippet/CSharp/walkthrough-outlining_2.cs)]
     [!code-vb[VSSDKOutlineRegionTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_2.vb)]

4. Přidejte některá pole ke sledování vyrovnávací paměti a snímku textu a Sestavujte sady řádků, které mají být označeny jako oblasti pro sbalení. Tento kód zahrnuje seznam objektů oblastí (pro pozdější definování), které reprezentují oblasti sbalení.

     [!code-csharp[VSSDKOutlineRegionTest#3](../extensibility/codesnippet/CSharp/walkthrough-outlining_3.cs)]
     [!code-vb[VSSDKOutlineRegionTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_3.vb)]

5. Přidejte konstruktor autor značky, který inicializuje pole, analyzuje vyrovnávací paměť a přidá do události obslužnou rutinu události <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> .

     [!code-csharp[VSSDKOutlineRegionTest#4](../extensibility/codesnippet/CSharp/walkthrough-outlining_4.cs)]
     [!code-vb[VSSDKOutlineRegionTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_4.vb)]

6. Implementujte <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> metodu, která vytvoří instanci rozsahů značek. V tomto příkladu se předpokládá, že rozsahy v <xref:Microsoft.VisualStudio.Text.NormalizedSpanCollection> předané metodě jsou souvislé, přestože nemusí vždy být v případě případu. Tato metoda vytvoří instanci nového rozsahu značek pro každou oblast sbalení.

     [!code-csharp[VSSDKOutlineRegionTest#5](../extensibility/codesnippet/CSharp/walkthrough-outlining_5.cs)]
     [!code-vb[VSSDKOutlineRegionTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_5.vb)]

7. Deklarujte `TagsChanged` obslužnou rutinu události.

     [!code-csharp[VSSDKOutlineRegionTest#6](../extensibility/codesnippet/CSharp/walkthrough-outlining_6.cs)]
     [!code-vb[VSSDKOutlineRegionTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_6.vb)]

8. Přidejte `BufferChanged` obslužnou rutinu události, která reaguje na události analýzou <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> vyrovnávací paměti textu.

     [!code-csharp[VSSDKOutlineRegionTest#7](../extensibility/codesnippet/CSharp/walkthrough-outlining_7.cs)]
     [!code-vb[VSSDKOutlineRegionTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_7.vb)]

9. Přidejte metodu, která analyzuje vyrovnávací paměť. Zde uvedený příklad slouží pouze pro ilustraci. Asynchronně analyzuje vyrovnávací paměť na vnořené oblasti osnovy.

     [!code-csharp[VSSDKOutlineRegionTest#8](../extensibility/codesnippet/CSharp/walkthrough-outlining_8.cs)]
     [!code-vb[VSSDKOutlineRegionTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_8.vb)]

10. Následující pomocná metoda získá celé číslo, které představuje úroveň sbalení, například 1 je dvojice složených závorek.

     [!code-csharp[VSSDKOutlineRegionTest#9](../extensibility/codesnippet/CSharp/walkthrough-outlining_9.cs)]
     [!code-vb[VSSDKOutlineRegionTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_9.vb)]

11. Následující pomocná metoda překládá oblast (definovaná dále v tomto článku) do SnapshotSpan.

     [!code-csharp[VSSDKOutlineRegionTest#10](../extensibility/codesnippet/CSharp/walkthrough-outlining_10.cs)]
     [!code-vb[VSSDKOutlineRegionTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_10.vb)]

12. Následující kód je určen pouze pro ilustraci. Definuje třídu PartialRegion, která obsahuje číslo řádku a posun začátku oblasti osnovy a odkaz na nadřazenou oblast (pokud existuje). Tento kód umožňuje analyzátoru nastavit vnořené oblasti sbalení. Odvozená třída oblasti obsahuje odkaz na číslo řádku na konci oblasti sbalení.

     [!code-csharp[VSSDKOutlineRegionTest#11](../extensibility/codesnippet/CSharp/walkthrough-outlining_11.cs)]
     [!code-vb[VSSDKOutlineRegionTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_11.vb)]

## <a name="implement-a-tagger-provider"></a>Implementace poskytovatele autor značky
 Exportujte poskytovatele autor značky pro svůj autor značky. Poskytovatel autor značky vytvoří `OutliningTagger` pro vyrovnávací paměť typu "text", nebo jinak vrátí, `OutliningTagger` Pokud vyrovnávací paměť již jednu obsahuje.

### <a name="to-implement-a-tagger-provider"></a>Implementace poskytovatele autor značky

1. Vytvořte třídu s názvem `OutliningTaggerProvider` , která implementuje <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider> , a exportujte ji pomocí atributů ContentType a TagType.

     [!code-csharp[VSSDKOutlineRegionTest#12](../extensibility/codesnippet/CSharp/walkthrough-outlining_12.cs)]
     [!code-vb[VSSDKOutlineRegionTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_12.vb)]

2. Implementujte <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider.CreateTagger%2A> metodu přidáním `OutliningTagger` do vlastností vyrovnávací paměti.

     [!code-csharp[VSSDKOutlineRegionTest#13](../extensibility/codesnippet/CSharp/walkthrough-outlining_13.cs)]
     [!code-vb[VSSDKOutlineRegionTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_13.vb)]

## <a name="build-and-test-the-code"></a>Sestavení a testování kódu
 Chcete-li otestovat tento kód, sestavte řešení OutlineRegionTest a spusťte ho v experimentální instanci.

### <a name="to-build-and-test-the-outlineregiontest-solution"></a>Sestavení a testování řešení OutlineRegionTest

1. Sestavte řešení.

2. Při spuštění tohoto projektu v ladicím programu se spustí druhá instance sady Visual Studio.

3. Vytvořte textový soubor. Zadejte nějaký text, který bude obsahovat levou hranatou závorku a pravou hranatou závorku.

    ```
    [
       Hello
    ]
    ```

4. Měla by existovat oblast osnovy, která zahrnuje závorky. Měli byste být schopni kliknout na symbol mínus nalevo od levé hranaté závorky, abyste mohli sbalit oblast osnovy. Když je oblast sbalena, symbol tři tečky (*...*) by se měl objevit nalevo od sbalené oblasti a automaticky otevírané okno obsahující text **najetí myší** by se mělo zobrazit při přesunutí ukazatele myši na tři tečky.

## <a name="see-also"></a>Viz také
- [Návod: propojení typu obsahu s příponou názvu souboru](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
