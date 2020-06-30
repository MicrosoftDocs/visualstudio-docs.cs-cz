---
title: Přidávání obrázků a aplikace Word Art do dokumentů prostřednictvím kódu programu
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 621051c827b08e66d68bc348401c2a939e279bcf
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/30/2020
ms.locfileid: "85538083"
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

     [!code-vb[Trin_VstcoreWordAutomation#108](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#108)]
     [!code-csharp[Trin_VstcoreWordAutomation#108](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#108)]

## <a name="add-wordart-at-design-time"></a>Přidat WordArt v době návrhu
 Pokud vyvíjíte přizpůsobení na úrovni dokumentu, můžete do dokumentu přidat WordArt v době návrhu.

### <a name="to-add-wordart-to-a-word-document-at-design-time"></a>Přidání objektu WordArt do dokumentu aplikace Word v době návrhu

1. Umístěte kurzor na místo, kam chcete vložit WordArt do dokumentu.

2. Klikněte na kartu **Vložit** na pás karet.

3. Ve skupině **text** klikněte na **WordArt**a pak vyberte styl WordArt.

4. Přidejte text, který se má zobrazit v dokumentu, do dialogového okna **Upravit text WordArtu** a klikněte na tlačítko **OK**.

     Text se přidá do dokumentu s použitým vybraným stylem WordArt.

## <a name="add-wordart-at-run-time"></a>Přidat WordArt v době běhu
 WordArt můžete vložit do dokumentu v aktuálním umístění kurzoru. Postup se liší v přizpůsobení na úrovni dokumentu a doplňku VSTO.

### <a name="to-add-wordart-at-the-cursor-location-in-a-document-level-customization"></a>Přidání objektu WordArt v umístění kurzoru v přizpůsobení na úrovni dokumentu

1. Získá levou a horní pozici aktuálního umístění kurzoru.

     [!code-vb[Trin_VstcoreWordAutomation#109](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#109)]
     [!code-csharp[Trin_VstcoreWordAutomation#109](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#109)]

2. Zavolejte <xref:Microsoft.Office.Interop.Word.Shapes.AddTextEffect%2A> metodu <xref:Microsoft.Office.Interop.Word.Shapes> objektu v dokumentu.

     [!code-vb[Trin_VstcoreWordAutomation#110](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#110)]
     [!code-csharp[Trin_VstcoreWordAutomation#110](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#110)]

### <a name="to-add-wordart-at-the-cursor-location-in-a-vsto-add-in"></a>Přidání objektu WordArt do umístění kurzoru v doplňku VSTO

1. Získá levou a horní pozici aktuálního umístění kurzoru.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#109](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#109)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#109](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#109)]

2. Zavolejte <xref:Microsoft.Office.Interop.Word.Shapes.AddTextEffect%2A> metodu <xref:Microsoft.Office.Interop.Word.Shapes> objektu aktivního dokumentu (nebo jiný dokument, který zadáte).

     [!code-vb[Trin_VstcoreWordAutomationAddIn#110](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#110)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#110](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#110)]

## <a name="compile-the-code"></a>Kompilovat kód

- Na jednotce C musí existovat obrázek s názvem *SamplePicture.jpg* .

## <a name="see-also"></a>Viz také
- [Postupy: otevírání existujících dokumentů prostřednictvím kódu programu](../vsto/how-to-programmatically-open-existing-documents.md)
- [Postupy: vkládání textu do dokumentů aplikace Word prostřednictvím kódu programu](../vsto/how-to-programmatically-insert-text-into-word-documents.md)
- [Postupy: obnovení výběru po hledání prostřednictvím kódu programu](../vsto/how-to-programmatically-restore-selections-after-searches.md)
- [Postupy: ukládání dokumentů prostřednictvím kódu programu](../vsto/how-to-programmatically-save-documents.md)
- [Volitelné parametry v řešeních pro systém Office](../vsto/optional-parameters-in-office-solutions.md)
