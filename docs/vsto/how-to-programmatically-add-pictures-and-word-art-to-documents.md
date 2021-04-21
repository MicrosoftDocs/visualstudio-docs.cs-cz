---
title: Přidávání obrázků a aplikace Word Art do dokumentů prostřednictvím kódu programu
description: Přečtěte si, jak můžete přidávat obrázky a kreslit objekty do dokumentů v době návrhu nebo v době běhu.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], adding pictures
- Word documents, adding pictures
- Word documents, adding Word Art
- graphics, adding to Word documents
- WordArt, adding to documents
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 445857200dfb269dd71f7cb3d446d025048cb3ac
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/21/2021
ms.locfileid: "107828433"
---
# <a name="how-to-programmatically-add-pictures-and-word-art-to-documents"></a>Postupy: Přidávání obrázků a aplikace Word Art do dokumentů prostřednictvím kódu programu
  Obrázky a kresby objektů můžete přidat do dokumentů v době návrhu nebo během doby běhu. WordArt umožňuje přidat do systém Microsoft Office wordové dokumenty dekorativní text. Tyto speciální textové efekty jsou kresby objektů, které lze přizpůsobit a vkládat do dokumentu.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="add-a-picture-at-design-time"></a>Přidání obrázku v době návrhu
 Pokud vyvíjíte přizpůsobení na úrovni dokumentu, můžete k dokumentu přidat obrázek v době návrhu.

### <a name="to-add-a-picture-to-a-word-document-at-design-time"></a>Přidání obrázku do dokumentu aplikace Word v době návrhu

1. Umístěte kurzor na místo, kam chcete vložit obrázek do dokumentu.

2. Klikněte na kartu **Vložit** na pás karet.

3. Ve skupině **ilustrace** klikněte na možnost **Obrázek**.

4. V dialogovém okně **Vložit obrázek** přejděte na obrázek, který chcete vložit, a klikněte na **Vložit**.

     Obrázek se přidá do dokumentu v aktuálním umístění kurzoru.

## <a name="add-a-picture-at-run-time"></a>Přidání obrázku v době běhu
 Do dokumentu můžete vložit obrázek v aktuálním umístění kurzoru.

### <a name="to-add-a-picture-at-the-cursor-location"></a>Přidání obrázku do umístění kurzoru

1. Zavolejte <xref:Microsoft.Office.Interop.Word.InlineShapes.AddPicture%2A> metodu <xref:Microsoft.Office.Interop.Word.InlineShapes> kolekce a předejte jí název souboru.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet108":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet108":::

## <a name="add-wordart-at-design-time"></a>Přidat WordArt v době návrhu
 Pokud vyvíjíte přizpůsobení na úrovni dokumentu, můžete do dokumentu přidat WordArt v době návrhu.

### <a name="to-add-wordart-to-a-word-document-at-design-time"></a>Přidání objektu WordArt do dokumentu aplikace Word v době návrhu

1. Umístěte kurzor na místo, kam chcete vložit WordArt do dokumentu.

2. Klikněte na kartu **Vložit** na pás karet.

3. Ve skupině **text** klikněte na **WordArt** a pak vyberte styl WordArt.

4. Přidejte text, který se má zobrazit v dokumentu, do dialogového okna **Upravit text WordArtu** a klikněte na tlačítko **OK**.

     Text se přidá do dokumentu s použitým vybraným stylem WordArt.

## <a name="add-wordart-at-run-time"></a>Přidat WordArt v době běhu
 WordArt můžete vložit do dokumentu v aktuálním umístění kurzoru. Postup se liší v přizpůsobení na úrovni dokumentu a doplňku VSTO.

### <a name="to-add-wordart-at-the-cursor-location-in-a-document-level-customization"></a>Přidání objektu WordArt v umístění kurzoru v přizpůsobení na úrovni dokumentu

1. Získá levou a horní pozici aktuálního umístění kurzoru.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet109":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet109":::

2. Zavolejte <xref:Microsoft.Office.Interop.Word.Shapes.AddTextEffect%2A> metodu <xref:Microsoft.Office.Interop.Word.Shapes> objektu v dokumentu.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet110":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet110":::

### <a name="to-add-wordart-at-the-cursor-location-in-a-vsto-add-in"></a>Přidání objektu WordArt do umístění kurzoru v doplňku VSTO

1. Získá levou a horní pozici aktuálního umístění kurzoru.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet109":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet109":::

2. Zavolejte <xref:Microsoft.Office.Interop.Word.Shapes.AddTextEffect%2A> metodu <xref:Microsoft.Office.Interop.Word.Shapes> objektu aktivního dokumentu (nebo jiný dokument, který zadáte).

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet110":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet110":::

## <a name="compile-the-code"></a>Kompilovat kód

- Na jednotce C musí existovat obrázek s názvem *SamplePicture.jpg* .

## <a name="see-also"></a>Viz také
- [Postupy: otevírání existujících dokumentů prostřednictvím kódu programu](../vsto/how-to-programmatically-open-existing-documents.md)
- [Postupy: vkládání textu do dokumentů aplikace Word prostřednictvím kódu programu](../vsto/how-to-programmatically-insert-text-into-word-documents.md)
- [Postupy: obnovení výběru po hledání prostřednictvím kódu programu](../vsto/how-to-programmatically-restore-selections-after-searches.md)
- [Postupy: ukládání dokumentů prostřednictvím kódu programu](../vsto/how-to-programmatically-save-documents.md)
- [Volitelné parametry v řešeních pro systém Office](../vsto/optional-parameters-in-office-solutions.md)
