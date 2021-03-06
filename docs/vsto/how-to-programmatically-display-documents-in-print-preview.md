---
title: 'Postupy: zobrazování dokumentů v náhledu tisku prostřednictvím kódu programu'
description: Přečtěte si, jak můžete prostřednictvím kódu programu v dokumentu Microsoft Wordu zobrazit dokumenty v náhledu tisku.
ms.custom: SEO-VS-2020
titleSuffix: ''
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 90979fbc7cd0b46329b8d9e9bc142e8cf0066db0
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/21/2021
ms.locfileid: "107825885"
---
# <a name="how-to-programmatically-display-documents-in-print-preview"></a>Postupy: zobrazování dokumentů v náhledu tisku prostřednictvím kódu programu
  Pokud vaše řešení vygeneruje sestavu, může být vhodné zobrazit sestavu pro uživatele v režimu náhledu tisku.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="procedures-for-document-level-customizations"></a>Postupy pro přizpůsobení na úrovni dokumentu

### <a name="to-display-a-document-in-print-preview-by-calling-the-printpreview-method"></a>Zobrazení dokumentu v náhledu tisku voláním metody PrintPreview

1. Zavolejte <xref:Microsoft.Office.Tools.Word.Document.PrintPreview%2A> metodu <xref:Microsoft.Office.Tools.Word.Document> třídy. Chcete-li použít tento příklad kódu, spusťte jej z `ThisDocument` třídy v projektu.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet13":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet13":::

### <a name="to-display-a-document-in-print-preview-by-setting-the-printpreview-property"></a>Zobrazení dokumentu v náhledu tisku nastavením vlastnosti PrintPreview

1. Nastavte <xref:Microsoft.Office.Interop.Word._Application.PrintPreview%2A> vlastnost <xref:Microsoft.Office.Interop.Word.Application> objektu na **hodnotu true**.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet14":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet14":::

## <a name="procedures-for-vsto-add-ins"></a>Postupy pro doplňky VSTO

### <a name="to-display-a-document-in-print-preview-by-calling-the-printpreview-method"></a>Zobrazení dokumentu v náhledu tisku voláním metody PrintPreview

1. Zavolejte <xref:Microsoft.Office.Interop.Word._Document.PrintPreview%2A> metodu, kterou chcete <xref:Microsoft.Office.Interop.Word.Document> Zobrazit ve verzi Preview. Chcete-li použít tento příklad kódu, spusťte jej z `ThisAddIn` třídy v projektu.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet13":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet13":::

### <a name="to-display-a-document-in-print-preview-by-setting-the-printpreview-property"></a>Zobrazení dokumentu v náhledu tisku nastavením vlastnosti PrintPreview

1. Nastavte <xref:Microsoft.Office.Interop.Word._Application.PrintPreview%2A> vlastnost <xref:Microsoft.Office.Interop.Word.Application> objektu na **hodnotu true**.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet14":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet14":::

## <a name="see-also"></a>Viz také
- [Postupy: tisk dokumentů prostřednictvím kódu programu](../vsto/how-to-programmatically-print-documents.md)
- [Postupy: otevírání existujících dokumentů prostřednictvím kódu programu](../vsto/how-to-programmatically-open-existing-documents.md)
- [Postupy: vytváření nových dokumentů prostřednictvím kódu programu](../vsto/how-to-programmatically-create-new-documents.md)
