---
title: 'Postupy: tisk dokumentů prostřednictvím kódu programu'
description: Přečtěte si, jak můžete vytisknout celý dokument aplikace Microsoft Word nebo část dokumentu na výchozí tiskárnu.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Word [Office development in Visual Studio], printing documents
- documents [Office development in Visual Studio], printing
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: c81e22bbf3af08c150f1e1156ee62f1666f59638
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99956630"
---
# <a name="how-to-programmatically-print-documents"></a>Postupy: tisk dokumentů prostřednictvím kódu programu
  Můžete vytisknout celý systém Microsoft Office wordový dokument nebo část dokumentu na výchozí tiskárnu.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="print-a-document-that-is-part-of-a-document-level-customization"></a>Tisk dokumentu, který je součástí přizpůsobení na úrovni dokumentu

### <a name="to-print-the-entire-document"></a>Tisk celého dokumentu

1. Zavolejte <xref:Microsoft.Office.Tools.Word.Document.PrintOut%2A> metodu `ThisDocument` třídy v projektu pro vytištění celého dokumentu. Chcete-li použít tento příklad, spusťte kód z `ThisDocument` třídy.

     [!code-vb[Trin_VstcoreWordAutomation#11](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#11)]
     [!code-csharp[Trin_VstcoreWordAutomation#11](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#11)]

### <a name="to-print-the-current-page-of-the-document"></a>Tisk aktuální stránky dokumentu

1. Zavolejte <xref:Microsoft.Office.Tools.Word.Document.PrintOut%2A> metodu `ThisDocument` třídy v projektu a určete, zda bude vytištěna jedna kopie aktuální stránky. Chcete-li použít tento příklad, spusťte kód z `ThisDocument` třídy.

     [!code-vb[Trin_VstcoreWordAutomation#12](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#12)]
     [!code-csharp[Trin_VstcoreWordAutomation#12](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#12)]

## <a name="print-a-document-by-using-a-vsto-add-in"></a>Tisk dokumentu pomocí doplňku VSTO

### <a name="to-print-an-entire-document"></a>Tisk celého dokumentu

1. Zavolejte <xref:Microsoft.Office.Interop.Word._Document.PrintOut%2A> metodu <xref:Microsoft.Office.Interop.Word.Document> objektu, který chcete vytisknout. Následující příklad kódu vytiskne aktivní dokument. Chcete-li použít tento příklad, spusťte kód z `ThisAddIn` třídy v projektu.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#11](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#11)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#11](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#11)]

### <a name="to-print-the-current-page-of-a-document"></a>Tisk aktuální stránky dokumentu

1. Zavolejte <xref:Microsoft.Office.Interop.Word._Document.PrintOut%2A> metodu <xref:Microsoft.Office.Interop.Word.Document> objektu, který chcete vytisknout, a určete, že bude vytištěna jedna kopie aktuální stránky. Následující příklad kódu vytiskne aktivní dokument. Chcete-li použít tento příklad, spusťte kód z `ThisAddIn` třídy v projektu.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#12](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#12)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#12](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#12)]

## <a name="see-also"></a>Viz také
- [Volitelné parametry v řešeních pro systém Office](../vsto/optional-parameters-in-office-solutions.md)
