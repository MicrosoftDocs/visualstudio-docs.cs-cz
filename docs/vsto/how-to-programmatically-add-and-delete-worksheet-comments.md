---
title: 'Postupy: přidávání a odstraňování komentářů v listech prostřednictvím kódu programu'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ranges, comments
- worksheets, comments
- comments, worksheets
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: dc02a659c50a5b207f2f53d0a8781b0d23419301
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/30/2020
ms.locfileid: "85520078"
---
# <a name="how-to-programmatically-add-and-delete-worksheet-comments"></a>Postupy: přidávání a odstraňování komentářů v listech prostřednictvím kódu programu
  Komentáře můžete programově přidávat a odstraňovat v systém Microsoft Office listech aplikace Excel. Komentáře lze přidat pouze do jednoduchých buněk, nikoli do oblastí s více buňkami.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="add-and-delete-a-comment-in-a-document-level-project"></a>Přidání a odstranění komentáře v projektu na úrovni dokumentu
 V následujících příkladech se předpokládá, že je k dispozici ovládací prvek s jednou buňkou s <xref:Microsoft.Office.Tools.Excel.NamedRange> `dateComment` názvem na listu `Sheet1` .

### <a name="to-add-a-new-comment-to-a-named-range"></a>Přidání nového komentáře do pojmenovaného rozsahu

1. Zavolejte <xref:Microsoft.Office.Tools.Excel.NamedRange.AddComment%2A> metodu <xref:Microsoft.Office.Tools.Excel.NamedRange> ovládacího prvku a zadejte text komentáře. Tento kód musí být umístěn ve `Sheet1` třídě.

     [!code-csharp[Trin_VstcoreExcelAutomation#30](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#30)]
     [!code-vb[Trin_VstcoreExcelAutomation#30](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#30)]

#### <a name="to-delete-a-comment-from-a-named-range"></a>Odstranění komentáře z pojmenovaného rozsahu

1. Ověřte, zda komentář v rozsahu existuje a zda je odstraněn. Tento kód musí být umístěn ve `Sheet1` třídě.

     [!code-csharp[Trin_VstcoreExcelAutomation#29](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#29)]
     [!code-vb[Trin_VstcoreExcelAutomation#29](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#29)]

## <a name="add-and-delete-a-comment-in-a-vsto-add-in-project"></a>Přidání a odstranění komentáře v projektu doplňku VSTO
 V následujících příkladech se předpokládá, že je <xref:Microsoft.Office.Interop.Excel.Range> `dateComment` v aktivním listu jedna buňka s názvem.

### <a name="to-add-a-new-comment-to-an-excel-range"></a>Přidání nového komentáře do rozsahu aplikace Excel

1. Zavolejte <xref:Microsoft.Office.Interop.Excel.Range.AddComment%2A> metodu <xref:Microsoft.Office.Interop.Excel.Range> a zadejte text komentáře.

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#20](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#20)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#20](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#20)]

### <a name="to-delete-a-comment-from-an-excel-range"></a>Odstranění komentáře z oblasti aplikace Excel

1. Ověřte, zda komentář v rozsahu existuje a zda je odstraněn.

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#19](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#19)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#19](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#19)]

## <a name="see-also"></a>Viz také:
- [Práce s listy](../vsto/working-with-worksheets.md)
- [Postupy: zobrazování komentářů v listech prostřednictvím kódu programu](../vsto/how-to-programmatically-display-worksheet-comments.md)
- [Ovládací prvek NamedRange](../vsto/namedrange-control.md)
