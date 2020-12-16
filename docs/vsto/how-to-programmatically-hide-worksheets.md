---
title: 'Postupy: skrývání listů prostřednictvím kódu programu'
description: Přečtěte si, jak programově zobrazit nebo skrýt libovolný list v sešitu Microsoft Excelu pomocí položky hostitele na listu.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- hidden worksheets
- worksheets, hiding
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 9a5ba61c7db0a62cf3e97fb8e4df5cb655e9f2dd
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/15/2020
ms.locfileid: "97525668"
---
# <a name="how-to-programmatically-hide-worksheets"></a>Postupy: skrývání listů prostřednictvím kódu programu
  V sešitu můžete zobrazit nebo skrýt kterýkoli list. Chcete-li skrýt list, použijte položku hostitele listu nebo přejděte k listu pomocí kolekce listů sešitu.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="use-the-worksheet-host-item"></a>Použít položku hostitele listu
 Pokud byl sešit přidán v době návrhu v přizpůsobení na úrovni dokumentu, použijte <xref:Microsoft.Office.Tools.Excel.Worksheet.Visible%2A> vlastnost pro skrytí zadaného listu.

### <a name="to-hide-a-worksheet-using-a-worksheet-host-item"></a>Skrytí listu pomocí položky hostitele na listu

1. Nastavte <xref:Microsoft.Office.Tools.Excel.Worksheet.Visible%2A> vlastnost `Sheet1` položky hostitele na <xref:Microsoft.Office.Interop.Excel.XlSheetVisibility.xlSheetHidden> hodnotu výčtu.

     [!code-csharp[Trin_VstcoreExcelAutomation#25](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#25)]
     [!code-vb[Trin_VstcoreExcelAutomation#25](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#25)]

## <a name="use-the-sheets-collection-of-the-excel-workbook"></a>Použití kolekce listů excelového sešitu
 Přístup k listům prostřednictvím kolekce aplikace systém Microsoft Office Excel <xref:Microsoft.Office.Interop.Excel.Sheets> v následujících případech:

- Chcete skrýt list v doplňku VSTO.

- List, který chcete skrýt, byl vytvořen v době běhu v přizpůsobení na úrovni dokumentu.

### <a name="to-hide-a-worksheet-using-the-sheets-collection-of-the-excel-workbook"></a>Skrytí listu pomocí kolekce listů sešitu aplikace Excel

1. Nastavte <xref:Microsoft.Office.Interop.Excel.Worksheets.Visible%2A> vlastnost listu na <xref:Microsoft.Office.Interop.Excel.XlSheetVisibility.xlSheetHidden> hodnotu výčtu.

     [!code-csharp[Trin_VstcoreExcelAutomation#26](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#26)]
     [!code-vb[Trin_VstcoreExcelAutomation#26](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#26)]

## <a name="see-also"></a>Viz také
- [Práce s listy](../vsto/working-with-worksheets.md)
- [Postupy: Odstraňování listů ze sešitů prostřednictvím kódu programu](../vsto/how-to-programmatically-delete-worksheets-from-workbooks.md)
- [Postupy: přesouvání listů v sešitech prostřednictvím kódu programu](../vsto/how-to-programmatically-move-worksheets-within-workbooks.md)
- [Postupy: ochrana listů prostřednictvím kódu programu](../vsto/how-to-programmatically-protect-worksheets.md)
- [Přehled hostitelských položek a hostitelských ovládacích prvků](../vsto/host-items-and-host-controls-overview.md)
- [Globální přístup k objektům v projektech pro systém Office](../vsto/global-access-to-objects-in-office-projects.md)
