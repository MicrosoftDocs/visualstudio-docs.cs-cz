---
title: 'Postupy: zobrazování dokumentů v náhledu tisku prostřednictvím kódu programu'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Word [Office development in Visual Studio], displaying documents in print preview
- documents [Office development in Visual Studio], displaying in print preview
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 036f8a45d5605b55b9743a22d598a13780641c97
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/30/2020
ms.locfileid: "85545909"
---
# <a name="how-to-programmatically-display-documents-in-print-preview"></a>Postupy: zobrazování dokumentů v náhledu tisku prostřednictvím kódu programu
  Pokud vaše řešení vygeneruje sestavu, může být vhodné zobrazit sestavu pro uživatele v režimu náhledu tisku.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="procedures-for-document-level-customizations"></a>Postupy pro přizpůsobení na úrovni dokumentu

### <a name="to-display-a-document-in-print-preview-by-calling-the-printpreview-method"></a>Zobrazení dokumentu v náhledu tisku voláním metody PrintPreview

1. Zavolejte <xref:Microsoft.Office.Tools.Word.Document.PrintPreview%2A> metodu <xref:Microsoft.Office.Tools.Word.Document> třídy. Chcete-li použít tento příklad kódu, spusťte jej z `ThisDocument` třídy v projektu.

     [!code-vb[Trin_VstcoreWordAutomation#13](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#13)]
     [!code-csharp[Trin_VstcoreWordAutomation#13](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#13)]

### <a name="to-display-a-document-in-print-preview-by-setting-the-printpreview-property"></a>Zobrazení dokumentu v náhledu tisku nastavením vlastnosti PrintPreview

1. Nastavte <xref:Microsoft.Office.Interop.Word._Application.PrintPreview%2A> vlastnost <xref:Microsoft.Office.Interop.Word.Application> objektu na **hodnotu true**.

     [!code-vb[Trin_VstcoreWordAutomation#14](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#14)]
     [!code-csharp[Trin_VstcoreWordAutomation#14](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#14)]

## <a name="procedures-for-vsto-add-ins"></a>Postupy pro doplňky VSTO

### <a name="to-display-a-document-in-print-preview-by-calling-the-printpreview-method"></a>Zobrazení dokumentu v náhledu tisku voláním metody PrintPreview

1. Zavolejte <xref:Microsoft.Office.Interop.Word._Document.PrintPreview%2A> metodu, kterou chcete <xref:Microsoft.Office.Interop.Word.Document> Zobrazit ve verzi Preview. Chcete-li použít tento příklad kódu, spusťte jej z `ThisAddIn` třídy v projektu.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#13](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#13)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#13](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#13)]

### <a name="to-display-a-document-in-print-preview-by-setting-the-printpreview-property"></a>Zobrazení dokumentu v náhledu tisku nastavením vlastnosti PrintPreview

1. Nastavte <xref:Microsoft.Office.Interop.Word._Application.PrintPreview%2A> vlastnost <xref:Microsoft.Office.Interop.Word.Application> objektu na **hodnotu true**.

     [!code-vb[Trin_VstcoreWordAutomation#14](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#14)]
     [!code-csharp[Trin_VstcoreWordAutomation#14](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#14)]

## <a name="see-also"></a>Viz také:
- [Postupy: tisk dokumentů prostřednictvím kódu programu](../vsto/how-to-programmatically-print-documents.md)
- [Postupy: otevírání existujících dokumentů prostřednictvím kódu programu](../vsto/how-to-programmatically-open-existing-documents.md)
- [Postupy: vytváření nových dokumentů prostřednictvím kódu programu](../vsto/how-to-programmatically-create-new-documents.md)
