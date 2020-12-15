---
title: 'Postupy: tisk dokumentů aplikace Visio prostřednictvím kódu programu'
description: Přečtěte si, jak můžete vytisknout celý dokument Microsoft Visia nebo jenom vytisknout konkrétní stránku v tomto dokumentu.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visio [Office development in Visual Studio], printing Visio documents
- documents [Office development in Visual Studio], printing Visio documents
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 46babb5c989f647706bcbe87412adcdeeb0476d7
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/15/2020
ms.locfileid: "97523775"
---
# <a name="how-to-programmatically-print-visio-documents"></a>Postupy: tisk dokumentů aplikace Visio prostřednictvím kódu programu
  Můžete vytisknout kompletní systém Microsoft Office dokument Visia nebo pouze konkrétní stránku.

 Podrobnosti o metodách tisku najdete v referenční dokumentaci k jazyku VBA pro [Microsoft.Office.Interop.Visio.Document. Metoda Print](/office/vba/api/Visio.Document.Print) a metoda [Microsoft. Office. Interop. Visio. Page. Print](/office/vba/api/Visio.Page.Print)

## <a name="print-a-visio-document"></a>Tisk dokumentu aplikace Visio

### <a name="to-print-a-complete-document"></a>Tisk celého dokumentu

- Zavolejte `Microsoft.Office.Interop.Visio.Document.Print` metodu `Microsoft.Office.Interop.Visio.Document` objektu, který chcete vytisknout.

     Následující příklad kódu vytiskne aktivní dokument. Chcete-li použít tento příklad, spusťte kód z `ThisAddIn` třídy v projektu.

     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#8](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#8)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#8](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#8)]

## <a name="print-a-page-of-a-visio-document"></a>Tisk stránky dokumentu aplikace Visio

### <a name="to-print-a-page-of-a-document"></a>Tisk stránky dokumentu

- Zavolejte `Microsoft.Office.Interop.Visio.Pages.Print` metodu `Microsoft.Office.Interop.Visio.Pages` objektu, který chcete vytisknout.

     Následující příklad kódu vytiskne první stránku aktivního dokumentu. Chcete-li použít tento příklad, spusťte kód z `ThisAddIn` třídy v projektu.

     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#9](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#9)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#9](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#9)]

## <a name="see-also"></a>Viz také
- [Řešení aplikace Visio](../vsto/visio-solutions.md)
- [Přehled modelu objektů aplikace Visio](../vsto/visio-object-model-overview.md)
- [Postupy: vytváření nových dokumentů aplikace Visio prostřednictvím kódu programu](../vsto/how-to-programmatically-create-new-visio-documents.md)
- [Postupy: otevírání dokumentů aplikace Visio prostřednictvím kódu programu](../vsto/how-to-programmatically-open-visio-documents.md)
- [Postupy: zavírání dokumentů aplikace Visio prostřednictvím kódu programu](../vsto/how-to-programmatically-close-visio-documents.md)
- [Postupy: ukládání dokumentů aplikace Visio prostřednictvím kódu programu](../vsto/how-to-programmatically-save-visio-documents.md)
