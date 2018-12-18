---
title: 'Postupy: programové přidání obrázků a objektů WordArt do dokumentů'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], adding pictures
- Word documents, adding pictures
- Word documents, adding Word Art
- graphics, adding to Word documents
- WordArt, adding to documents
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 61399df32ef0f22d1d0aacf23dea45c1357c7579
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/11/2018
ms.locfileid: "35255103"
---
# <a name="how-to-programmatically-add-pictures-and-word-art-to-documents"></a>Postupy: programové přidání obrázků a objektů WordArt do dokumentů
  Obrázky a kresby můžete přidat do dokumentů v době návrhu nebo při běhu. WordArt umožňuje přidat dekorativní textu do dokumentů aplikace Microsoft Office Word. Tyto speciální textové efekty jsou kreslení objekty, které můžete přizpůsobit a vložit do dokumentu.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## <a name="add-a-picture-at-design-time"></a>Přidání obrázku v době návrhu  
 Pokud vyvíjíte přizpůsobení na úrovni dokumentu, můžete přidat obrázku do dokumentu v době návrhu.  
  
### <a name="to-add-a-picture-to-a-word-document-at-design-time"></a>Přidání obrázku do dokumentu aplikace Word v době návrhu  
  
1.  Umístěte kurzor, kam chcete vložit obrázek v dokumentu.  
  
2.  Klikněte **vložit** karty na pásu karet.  
  
3.  V **ilustrace** klikněte na možnost **obrázek**.  
  
4.  V **vložit obrázek** dialogové okno, přejděte na obrázek, který chcete vložit a klikněte na tlačítko **vložit**.  
  
     Na obrázku se přidá do vašeho dokumentu v aktuálním umístění kurzoru.  
  
## <a name="add-a-picture-at-runtime"></a>Přidání obrázku za běhu  
 Vložení obrázku do dokumentu na aktuální pozici kurzoru.  
  
### <a name="to-add-a-picture-at-the-cursor-location"></a>Přidání obrázku v umístění kurzoru  
  
1.  Volání <xref:Microsoft.Office.Interop.Word.InlineShapes.AddPicture%2A> metodu <xref:Microsoft.Office.Interop.Word.InlineShapes> kolekce a předejte jí názvu souboru.  
  
     [!code-vb[Trin_VstcoreWordAutomation#108](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#108)]
     [!code-csharp[Trin_VstcoreWordAutomation#108](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#108)]  
  
## <a name="add-wordart-at-design-time"></a>Přidat WordArt v době návrhu  
 Pokud vyvíjíte přizpůsobení na úrovni dokumentu, můžete přidat WordArt do dokumentů v době návrhu.  
  
### <a name="to-add-wordart-to-a-word-document-at-design-time"></a>Přidání WordArt do dokumentů aplikace Word v době návrhu  
  
1.  Umístěte kurzor, kam chcete vložit WordArt v dokumentu.  
  
2.  Klikněte **vložit** karty na pásu karet.  
  
3.  V **Text** klikněte na možnost **WordArt**a potom vyberte mezi styly.  
  
4.  Přidat text, který se má zobrazit v dokumentu, který má **upravit Text objektu WordArt** dialogové okno a klikněte na tlačítko **OK**.  
  
     Text se přidá do dokumentu s vybraný styl WordArt použít.  
  
## <a name="add-wordart-at-runtime"></a>Přidat WordArt za běhu  
 WordArt můžete vložit do dokumentu na aktuální pozici kurzoru. Postup se liší pro přizpůsobení na úrovni dokumentu a doplňků VSTO.  
  
### <a name="to-add-wordart-at-the-cursor-location-in-a-document-level-customization"></a>Chcete-li přidat WordArt do umístění kurzoru v přizpůsobení na úrovni dokumentu  
  
1.  Získá pozici levého a horního aktuální umístění kurzoru.  
  
     [!code-vb[Trin_VstcoreWordAutomation#109](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#109)]
     [!code-csharp[Trin_VstcoreWordAutomation#109](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#109)]  
  
2.  Volání <xref:Microsoft.Office.Interop.Word.Shapes.AddTextEffect%2A> metodu <xref:Microsoft.Office.Interop.Word.Shapes> objektu v dokumentu.  
  
     [!code-vb[Trin_VstcoreWordAutomation#110](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#110)]
     [!code-csharp[Trin_VstcoreWordAutomation#110](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#110)]  
  
### <a name="to-add-wordart-at-the-cursor-location-in-a-vsto-add-in"></a>Chcete-li přidat WordArt do umístění kurzoru v doplňku VSTO  
  
1.  Získá pozici levého a horního aktuální umístění kurzoru.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#109](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#109)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#109](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#109)]  
  
2.  Volání <xref:Microsoft.Office.Interop.Word.Shapes.AddTextEffect%2A> metodu <xref:Microsoft.Office.Interop.Word.Shapes> objekt aktivní dokument (nebo do jiného dokumentu, který zadáte).  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#110](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#110)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#110](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#110)]  
  
## <a name="compile-the-code"></a>Kompilace kódu  
  
-   Obrázek s názvem *SamplePicture.jpg* musí existovat na jednotce c:.  
  
## <a name="see-also"></a>Viz také:  
 [Postupy: otevírání stávajících dokumentů prostřednictvím kódu programu](../vsto/how-to-programmatically-open-existing-documents.md)   
 [Postupy: programové vkládání textu do dokumentů aplikace Word](../vsto/how-to-programmatically-insert-text-into-word-documents.md)   
 [Postupy: programové obnovení výběru po hledání](../vsto/how-to-programmatically-restore-selections-after-searches.md)   
 [Postupy: ukládání dokumentů prostřednictvím kódu programu](../vsto/how-to-programmatically-save-documents.md)   
 [Volitelné parametry v řešeních pro systém Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  