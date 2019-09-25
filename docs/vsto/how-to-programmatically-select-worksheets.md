---
title: 'Postupy: Programové vybírání listů'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets, selecting
- Excel projects, selecting worksheets
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 20ebc8fea14b3dc52c802543f97318ec7fae7529
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2019
ms.locfileid: "71255632"
---
# <a name="how-to-programmatically-select-worksheets"></a>Postupy: Programové vybírání listů
  <xref:Microsoft.Office.Tools.Excel.Worksheet.Select%2A> Metoda vybere zadaný objekt, který přesune výběr uživatele do nového objektu. Použijte metodu <xref:Microsoft.Office.Tools.Excel.Worksheet.Activate%2A> , pokud chcete přenést fokus na objekt beze změny výběru uživatele.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 Pokud chcete vybrat existující list v doplňku VSTO nebo pokud byl list vytvořen v době běhu v přizpůsobení na úrovni dokumentu, je nutné k němu přistupovat pomocí excelové <xref:Microsoft.Office.Interop.Excel.Sheets> kolekce excelového sešitu. v opačném případě získáte přístup k <xref:Microsoft.Office.Tools.Excel.Worksheet>Hostitelská položka přímo.

## <a name="use-the-worksheet-host-item"></a>Použít položku hostitele listu
 V přizpůsobení na úrovni dokumentu přidejte následující kód do souboru *List1. vb* nebo *Sheet1.cs*.

### <a name="to-select-the-first-worksheet-in-a-workbook-using-a-host-item"></a>Výběr prvního listu v sešitu pomocí položky hostitele

1. <xref:Microsoft.Office.Tools.Excel.Worksheet.Select%2A> Zavolejte`Sheet1`metodu.

     [!code-csharp[Trin_VstcoreExcelAutomation#19](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#19)]
     [!code-vb[Trin_VstcoreExcelAutomation#19](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#19)]

## <a name="use-the-sheets-collection-of-the-excel-workbook"></a>Použití kolekce listů excelového sešitu
 Přístup k listu pomocí kolekce aplikace Excel <xref:Microsoft.Office.Interop.Excel.Sheets> .

### <a name="to-select-the-first-worksheet-in-a-workbook-using-the-sheets-collection-of-the-excel-workbook"></a>Výběr prvního listu v sešitu pomocí kolekce listů sešitu aplikace Excel

1. Voláním <xref:Microsoft.Office.Interop.Excel.Sheets> metody kolekce vyberte první list aktivního sešitu. <xref:Microsoft.Office.Interop.Excel.Sheets.Select%2A>

     [!code-csharp[Trin_VstcoreExcelAutomation#20](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#20)]
     [!code-vb[Trin_VstcoreExcelAutomation#20](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#20)]

## <a name="see-also"></a>Viz také:
- [Práce s listy](../vsto/working-with-worksheets.md)
- [Postupy: Programové listy tisku](../vsto/how-to-programmatically-print-worksheets.md)
- [Postupy: Programové odstraňování listů ze sešitů](../vsto/how-to-programmatically-delete-worksheets-from-workbooks.md)
- [Postupy: Programové skrývání listů](../vsto/how-to-programmatically-hide-worksheets.md)
- [Postupy: Programové zabezpečení listů](../vsto/how-to-programmatically-protect-worksheets.md)
- [Položka hostitele listu](../vsto/worksheet-host-item.md)
- [Globální přístup k objektům v projektech pro systém Office](../vsto/global-access-to-objects-in-office-projects.md)
- [Programové omezení hostitelských položek a hostitelských ovládacích prvků](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Volitelné parametry v řešeních pro systém Office](../vsto/optional-parameters-in-office-solutions.md)
- [Přehled hostitelských položek a hostitelských ovládacích prvků](../vsto/host-items-and-host-controls-overview.md)
