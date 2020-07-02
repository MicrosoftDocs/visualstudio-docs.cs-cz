---
title: 'Postupy: kopírování listů prostřednictvím kódu programu'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets, copying
- Excel [Office development in Visual Studio], copying worksheets
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 8226f337994c686d4d370e91831bc1262d3ef85e
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/30/2020
ms.locfileid: "85546078"
---
# <a name="how-to-programmatically-copy-worksheets"></a>Postupy: kopírování listů prostřednictvím kódu programu
  Můžete vytvořit kopii listu a vložit tento list před nebo za existující list v sešitu. Pokud nezadáte místo pro vložení listu, aplikace Excel vytvoří nový sešit, který bude obsahovat nový list.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

> [!NOTE]
> Bez ohledu na to, jestli kopírujete list programově, nebo když koncový uživatel zkopíruje list ručně, není na novém listu žádný kód a ovládací prvky na novém listu nebudou fungovat. Důvodem je to, že nově kopírovaný list je <xref:Microsoft.Office.Interop.Excel.Worksheet> objekt, nikoli <xref:Microsoft.Office.Tools.Excel.Worksheet> položka hostitele. Ovládací prvky model Windows Forms a hostitelské ovládací prvky lze přidat pouze k položkám hostitele. Další informace najdete v tématu [programové omezení hostitelských položek a hostitelských ovládacích prvků](../vsto/programmatic-limitations-of-host-items-and-host-controls.md).

## <a name="to-add-a-copied-worksheet-to-a-workbook-in-a-document-level-customization"></a>Přidání zkopírovaného listu do sešitu v přizpůsobení na úrovni dokumentu

1. Použijte <xref:Microsoft.Office.Interop.Excel.Worksheets.Copy%2A> metodu ke zkopírování prvního listu v aktuálním sešitu a kopii umístěte za třetí list.

     [!code-csharp[Trin_VstcoreExcelAutomation#16](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#16)]
     [!code-vb[Trin_VstcoreExcelAutomation#16](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#16)]

## <a name="to-add-a-copied-worksheet-to-a-workbook-in-a-vsto-add-in"></a>Přidání zkopírovaného listu do sešitu v doplňku VSTO

1. Použijte <xref:Microsoft.Office.Interop.Excel.Worksheets.Copy%2A> metodu ke zkopírování prvního listu v aktuálním sešitu a kopii umístěte za třetí list.

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#12](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#12)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#12](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#12)]

## <a name="see-also"></a>Viz také:
- [Práce s listy](../vsto/working-with-worksheets.md)
- [Přehled hostitelských položek a hostitelských ovládacích prvků](../vsto/host-items-and-host-controls-overview.md)
- [Postupy: přidávání nových listů do sešitů prostřednictvím kódu programu](../vsto/how-to-programmatically-add-new-worksheets-to-workbooks.md)
- [Postupy: Odstraňování listů ze sešitů prostřednictvím kódu programu](../vsto/how-to-programmatically-delete-worksheets-from-workbooks.md)
- [Postupy: Výběr listů prostřednictvím kódu programu](../vsto/how-to-programmatically-select-worksheets.md)
- [Automatizace Excelu pomocí rozšířených objektů](../vsto/automating-excel-by-using-extended-objects.md)
- [Globální přístup k objektům v projektech pro systém Office](../vsto/global-access-to-objects-in-office-projects.md)
- [Programové omezení hostitelských položek a hostitelských ovládacích prvků](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Volitelné parametry v řešeních pro systém Office](../vsto/optional-parameters-in-office-solutions.md)
