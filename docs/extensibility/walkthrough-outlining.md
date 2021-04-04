---
title: 'Návod: sbalení | Microsoft Docs'
description: Naučte se definovat a zobrazovat oblasti osnovy v kontextu jazykové služby nebo vlastní přípony názvu souboru a typu obsahu.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- editors [Visual Studio SDK], new - outlining
ms.assetid: d75a44aa-265a-44d4-9c28-457f59c4ff9f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- csharp
- vb
ms.openlocfilehash: 7bf4c0cc8757ea4f034da2ac17d6c76971f86305
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2021
ms.locfileid: "106217226"
---
# <a name="walkthrough-outlining"></a>Návod: Sbalení
Nastavte funkce založené na jazycích, jako je například sbalení, definováním druhů textových oblastí, které chcete rozbalit nebo sbalit. Můžete definovat oblasti v kontextu jazykové služby nebo definovat vlastní příponu názvu souboru a typ obsahu a použít definici oblasti jenom na tento typ, nebo použít definice oblastí na existující typ obsahu (například "text"). Tento návod ukazuje, jak definovat a zobrazit oblasti osnovy.

## <a name="prerequisites"></a>Požadavky
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

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs" id="Snippet1":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb" id="Snippet1":::

3. Vytvořte třídu s názvem `OutliningTagger` a proveďte její implementaci <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> :

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs" id="Snippet2":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb" id="Snippet2":::

4. Přidejte některá pole ke sledování vyrovnávací paměti a snímku textu a Sestavujte sady řádků, které mají být označeny jako oblasti pro sbalení. Tento kód zahrnuje seznam objektů oblastí (pro pozdější definování), které reprezentují oblasti sbalení.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs" id="Snippet3":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb" id="Snippet3":::

5. Přidejte konstruktor autor značky, který inicializuje pole, analyzuje vyrovnávací paměť a přidá do události obslužnou rutinu události <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> .

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs" id="Snippet4":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb" id="Snippet4":::

6. Implementujte <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> metodu, která vytvoří instanci rozsahů značek. V tomto příkladu se předpokládá, že rozsahy v <xref:Microsoft.VisualStudio.Text.NormalizedSpanCollection> předané metodě jsou souvislé, přestože nemusí vždy být v případě případu. Tato metoda vytvoří instanci nového rozsahu značek pro každou oblast sbalení.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs" id="Snippet5":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb" id="Snippet5":::

7. Deklarujte `TagsChanged` obslužnou rutinu události.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs" id="Snippet6":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb" id="Snippet6":::

8. Přidejte `BufferChanged` obslužnou rutinu události, která reaguje na události analýzou <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> vyrovnávací paměti textu.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs" id="Snippet7":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb" id="Snippet7":::

9. Přidejte metodu, která analyzuje vyrovnávací paměť. Zde uvedený příklad slouží pouze pro ilustraci. Asynchronně analyzuje vyrovnávací paměť na vnořené oblasti osnovy.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs" id="Snippet8":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb" id="Snippet8":::

10. Následující pomocná metoda získá celé číslo, které představuje úroveň sbalení, například 1 je dvojice složených závorek.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs" id="Snippet9":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb" id="Snippet9":::

11. Následující pomocná metoda překládá oblast (definovaná dále v tomto článku) do SnapshotSpan.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs" id="Snippet10":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb" id="Snippet10":::

12. Následující kód je určen pouze pro ilustraci. Definuje třídu PartialRegion, která obsahuje číslo řádku a posun začátku oblasti osnovy a odkaz na nadřazenou oblast (pokud existuje). Tento kód umožňuje analyzátoru nastavit vnořené oblasti sbalení. Odvozená třída oblasti obsahuje odkaz na číslo řádku na konci oblasti sbalení.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs" id="Snippet11":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb" id="Snippet11":::

## <a name="implement-a-tagger-provider"></a>Implementace poskytovatele autor značky
 Exportujte poskytovatele autor značky pro svůj autor značky. Poskytovatel autor značky vytvoří `OutliningTagger` pro vyrovnávací paměť typu "text", nebo jinak vrátí, `OutliningTagger` Pokud vyrovnávací paměť již jednu obsahuje.

### <a name="to-implement-a-tagger-provider"></a>Implementace poskytovatele autor značky

1. Vytvořte třídu s názvem `OutliningTaggerProvider` , která implementuje <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider> , a exportujte ji pomocí atributů ContentType a TagType.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs" id="Snippet12":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb" id="Snippet12":::

2. Implementujte <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider.CreateTagger%2A> metodu přidáním `OutliningTagger` do vlastností vyrovnávací paměti.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs" id="Snippet13":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb" id="Snippet13":::

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
