---
title: 'Postupy: vytváření nových sešitů prostřednictvím kódu programu'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Excel [Office development in Visual Studio], creating workbooks
- workbooks, creating
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 6a23f4b089d580d482193d278f22e4990d343097
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/30/2020
ms.locfileid: "85545974"
---
# <a name="how-to-programmatically-create-new-workbooks"></a>Postupy: vytváření nových sešitů prostřednictvím kódu programu
  Když vytvoříte sešit programově, jedná se o nativní <xref:Microsoft.Office.Interop.Excel.Workbook> objekt, nikoli o <xref:Microsoft.Office.Tools.Excel.Workbook> hostitelskou položku.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 Můžete vygenerovat <xref:Microsoft.Office.Tools.Excel.Workbook> položku hostitele pro <xref:Microsoft.Office.Interop.Excel.Workbook> objekt v projektu doplňku VSTO. Další informace najdete v tématu [rozšiřování dokumentů aplikace Word a sešitů aplikace Excel v doplňkech VSTO za běhu](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).

## <a name="to-create-a-new-workbook"></a>Vytvoření nového sešitu

1. Použijte <xref:Microsoft.Office.Interop.Excel.Workbooks.Add%2A> metodu <xref:Microsoft.Office.Interop.Excel.Workbooks> kolekce.

     [!code-csharp[Trin_VstcoreExcelAutomation#1](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#1)]
     [!code-vb[Trin_VstcoreExcelAutomation#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#1)]

    > [!NOTE]
    > Sešit můžete vytvořit na základě jiné šablony, než je výchozí šablona: předejte šablonu, kterou chcete použít jako parametr <xref:Microsoft.Office.Interop.Excel.Workbooks.Add%2A> metody.

## <a name="see-also"></a>Viz také:
- [Rozšiřování dokumentů aplikace Word a excelových sešitů v doplňcích VSTO za běhu](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Přidání ovládacích prvků do dokumentů Office v době běhu](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Práce se sešity](../vsto/working-with-workbooks.md)
- [Postupy: otevírání sešitů prostřednictvím kódu programu](../vsto/how-to-programmatically-open-workbooks.md)
- [Postupy: ukládání sešitů prostřednictvím kódu programu](../vsto/how-to-programmatically-save-workbooks.md)
- [Postupy: zavírání sešitů prostřednictvím kódu programu](../vsto/how-to-programmatically-close-workbooks.md)
- [Programové omezení hostitelských položek a hostitelských ovládacích prvků](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Volitelné parametry v řešeních pro systém Office](../vsto/optional-parameters-in-office-solutions.md)
- [Přehled hostitelských položek a hostitelských ovládacích prvků](../vsto/host-items-and-host-controls-overview.md)
