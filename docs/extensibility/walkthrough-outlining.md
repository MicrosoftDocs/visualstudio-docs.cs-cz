---
title: 'Návod: Osnova | Dokumenty společnosti Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - outlining
ms.assetid: d75a44aa-265a-44d4-9c28-457f59c4ff9f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 97b9dcbb2a24f1a3ed336a4a6bb7de4a15e907b4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697217"
---
# <a name="walkthrough-outlining"></a>Návod: Sbalení
Nastavte funkce založené na jazyce, jako je například osnova, definováním typů oblastí textu, které chcete rozbalit nebo sbalit. Můžete definovat oblasti v kontextu jazykové služby nebo definovat vlastní příponu názvu souboru a typ obsahu a použít definici oblasti pouze na tento typ nebo použít definice oblasti na existující typ obsahu (například "text"). Tento návod ukazuje, jak definovat a zobrazit osnovy oblastí.

## <a name="prerequisites"></a>Požadavky
 Počínaje Visual Studio 2015, nenainstalujete Visual Studio SDK ze služby stažení. Je součástí volitelné funkce v nastavení sady Visual Studio. VS SDK můžete také nainstalovat později. Další informace naleznete [v tématu Instalace sady Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-managed-extensibility-framework-mef-project"></a>Vytvoření projektu spravovaného rámce rozšiřitelnosti (MEF)

### <a name="to-create-a-mef-project"></a>Vytvoření projektu MEF

1. Vytvořte projekt VSIX. Pojmenujte `OutlineRegionTest`řešení .

2. Přidejte do projektu šablonu položky třídění editoru. Další informace naleznete [v tématu Vytvoření rozšíření se šablonou položky editoru](../extensibility/creating-an-extension-with-an-editor-item-template.md).

3. Odstraňte existující soubory tříd.

## <a name="implement-an-outlining-tagger"></a>Implementace značkování osnovy
 Osnova regiony jsou označeny druh<xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag>značky ( ). Tato značka poskytuje standardní nastínění chování. Nastíněnou oblast lze rozbalit nebo sbalit. Načrtnutá oblast je označena znaménkem Plus**+**(**-**), pokud je sbalená, nebo znaménko Mínus ( ) pokud je rozbalená a rozbalené oblasti je ohraničeno svislou čárou.

 Následující kroky ukazují, jak definovat tagger, který vytvoří osnovu oblastí pro všechny oblasti vymezené závorkami (**[**,**]**.

### <a name="to-implement-an-outlining-tagger"></a>Implementace značkování osnovy

1. Přidejte soubor třídy `OutliningTagger`a pojmenujte jej .

2. Importujte následující obory názvů.

     [!code-csharp[VSSDKOutlineRegionTest#1](../extensibility/codesnippet/CSharp/walkthrough-outlining_1.cs)]
     [!code-vb[VSSDKOutlineRegionTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_1.vb)]

3. Vytvořte třídu s `OutliningTagger`názvem <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601>a nechat ji implementovat :

     [!code-csharp[VSSDKOutlineRegionTest#2](../extensibility/codesnippet/CSharp/walkthrough-outlining_2.cs)]
     [!code-vb[VSSDKOutlineRegionTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_2.vb)]

4. Přidejte některá pole pro sledování textové vyrovnávací paměti a snímku a akumulovat sady řádků, které by měly být označeny jako osnovy oblastí. Tento kód obsahuje seznam Region objekty (které mají být definovány později), které představují osnovy oblastí.

     [!code-csharp[VSSDKOutlineRegionTest#3](../extensibility/codesnippet/CSharp/walkthrough-outlining_3.cs)]
     [!code-vb[VSSDKOutlineRegionTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_3.vb)]

5. Přidejte konstruktor tagger, který inicializuje pole, analyzuje vyrovnávací paměť a <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> přidá do události obslužnou rutinu události.

     [!code-csharp[VSSDKOutlineRegionTest#4](../extensibility/codesnippet/CSharp/walkthrough-outlining_4.cs)]
     [!code-vb[VSSDKOutlineRegionTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_4.vb)]

6. Implementujte <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> metodu, která konkretizuje rozsahy značek. Tento příklad předpokládá, že rozpětí <xref:Microsoft.VisualStudio.Text.NormalizedSpanCollection> v předané do metody jsou souvislé, i když nemusí být vždy případ. Tato metoda konkretizovat nové značky rozpětí pro každou z osnovy oblastí.

     [!code-csharp[VSSDKOutlineRegionTest#5](../extensibility/codesnippet/CSharp/walkthrough-outlining_5.cs)]
     [!code-vb[VSSDKOutlineRegionTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_5.vb)]

7. Deklarujte obslužnou rutinu `TagsChanged` události.

     [!code-csharp[VSSDKOutlineRegionTest#6](../extensibility/codesnippet/CSharp/walkthrough-outlining_6.cs)]
     [!code-vb[VSSDKOutlineRegionTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_6.vb)]

8. Přidejte `BufferChanged` obslužnou <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> rutinu události, která reaguje na události analýzou textové vyrovnávací paměti.

     [!code-csharp[VSSDKOutlineRegionTest#7](../extensibility/codesnippet/CSharp/walkthrough-outlining_7.cs)]
     [!code-vb[VSSDKOutlineRegionTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_7.vb)]

9. Přidejte metodu, která analyzuje vyrovnávací paměť. Zde uvedený příklad je pouze ilustrační. Synchronně analyzuje vyrovnávací paměť do vnořených oblastí osnovy.

     [!code-csharp[VSSDKOutlineRegionTest#8](../extensibility/codesnippet/CSharp/walkthrough-outlining_8.cs)]
     [!code-vb[VSSDKOutlineRegionTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_8.vb)]

10. Následující pomocná metoda získá celé číslo, které představuje úroveň osnovy, tak, že 1 je dvojice složených závorek nejvíce vlevo.

     [!code-csharp[VSSDKOutlineRegionTest#9](../extensibility/codesnippet/CSharp/walkthrough-outlining_9.cs)]
     [!code-vb[VSSDKOutlineRegionTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_9.vb)]

11. Následující pomocná metoda překládá Region (definované dále v tomto článku) do SnapshotSpan.

     [!code-csharp[VSSDKOutlineRegionTest#10](../extensibility/codesnippet/CSharp/walkthrough-outlining_10.cs)]
     [!code-vb[VSSDKOutlineRegionTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_10.vb)]

12. Následující kód je pouze pro ilustraci. Definuje třídu PartialRegion, která obsahuje číslo řádku a posun začátku oblasti osnovy a odkaz na nadřazenou oblast (pokud existuje). Tento kód umožňuje analyzátoru nastavit vnořené osnovy oblastí. Odvozená třída Region obsahuje odkaz na číslo řádku konce oblasti osnovy.

     [!code-csharp[VSSDKOutlineRegionTest#11](../extensibility/codesnippet/CSharp/walkthrough-outlining_11.cs)]
     [!code-vb[VSSDKOutlineRegionTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_11.vb)]

## <a name="implement-a-tagger-provider"></a>Implementace poskytovatele taggeru
 Exportujte poskytovatele taggeru pro tagger. Zprostředkovatel tagger vytvoří `OutliningTagger` pro vyrovnávací paměť typu obsahu "text", `OutliningTagger` nebo vrátí, pokud vyrovnávací paměť již má.

### <a name="to-implement-a-tagger-provider"></a>Implementace poskytovatele taggeru

1. Vytvořte třídu s názvem, `OutliningTaggerProvider` která implementuje <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider>, a exportujte ji pomocí atributů ContentType a TagType.

     [!code-csharp[VSSDKOutlineRegionTest#12](../extensibility/codesnippet/CSharp/walkthrough-outlining_12.cs)]
     [!code-vb[VSSDKOutlineRegionTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_12.vb)]

2. Implementujte <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider.CreateTagger%2A> metodu `OutliningTagger` přidáním vlastností vyrovnávací paměti.

     [!code-csharp[VSSDKOutlineRegionTest#13](../extensibility/codesnippet/CSharp/walkthrough-outlining_13.cs)]
     [!code-vb[VSSDKOutlineRegionTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_13.vb)]

## <a name="build-and-test-the-code"></a>Sestavení a testování kódu
 Chcete-li tento kód otestovat, vytvořte řešení OutlineRegionTest a spusťte jej v experimentální instanci.

### <a name="to-build-and-test-the-outlineregiontest-solution"></a>Vytvoření a testování řešení OutlineRegionTest

1. Sestavte řešení.

2. Při spuštění tohoto projektu v ladicím programu je spuštěna druhá instance sady Visual Studio.

3. Vytvořte textový soubor. Zadejte text, který obsahuje jak otevírací závorky, tak i uzavírací závorky.

    ```
    [
       Hello
    ]
    ```

4. Měla by existovat oblast osnovy, která zahrnuje obě závorky. Měli byste být schopni kliknout na znaménko mínus nalevo od otevřené závorky, abyste sbalili oblast osnovy. Při sbalení oblasti by se měl vlevo od sbalené oblasti zobrazit symbol tří selips (*...*) a při přesunutí ukazatele na tři tečky by se mělo zobrazit vyskakovací okno obsahující **text vznášející ho najetého textu.**

## <a name="see-also"></a>Viz také
- [Návod: Propojení typu obsahu s příponou názvu souboru](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
