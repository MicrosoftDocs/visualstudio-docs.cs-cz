---
title: 'Postupy: Výběr listů prostřednictvím kódu programu'
description: Pomocí sady Visual Studio programově vyberte listy aplikace Microsoft Excel s položkou hostitele listu nebo kolekcí listů sešitu aplikace Excel.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets, selecting
- Excel projects, selecting worksheets
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 04f410292fff686e7604e917e6c3fa7002c65273
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/21/2021
ms.locfileid: "107826249"
---
# <a name="how-to-programmatically-select-worksheets"></a>Postupy: Výběr listů prostřednictvím kódu programu
  <xref:Microsoft.Office.Tools.Excel.Worksheet.Select%2A>Metoda vybere zadaný objekt, který přesune výběr uživatele do nového objektu. Použijte <xref:Microsoft.Office.Tools.Excel.Worksheet.Activate%2A> metodu, pokud chcete přenést fokus na objekt beze změny výběru uživatele.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 Pokud chcete vybrat existující list v doplňku VSTO nebo pokud byl list vytvořen v době běhu v přizpůsobení na úrovni dokumentu, je nutné k němu přistupovat pomocí excelové kolekce excelového <xref:Microsoft.Office.Interop.Excel.Sheets> sešitu. v opačném případě můžete k <xref:Microsoft.Office.Tools.Excel.Worksheet> položce hostitele přistupovat přímo.

## <a name="use-the-worksheet-host-item"></a>Použít položku hostitele listu
 V přizpůsobení na úrovni dokumentu přidejte následující kód do souboru *List1. vb* nebo *List1. cs*.

### <a name="to-select-the-first-worksheet-in-a-workbook-using-a-host-item"></a>Výběr prvního listu v sešitu pomocí položky hostitele

1. Zavolejte <xref:Microsoft.Office.Tools.Excel.Worksheet.Select%2A> metodu `Sheet1` .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet19":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet19":::

## <a name="use-the-sheets-collection-of-the-excel-workbook"></a>Použití kolekce listů excelového sešitu
 Přístup k listu pomocí kolekce aplikace Excel <xref:Microsoft.Office.Interop.Excel.Sheets> .

### <a name="to-select-the-first-worksheet-in-a-workbook-using-the-sheets-collection-of-the-excel-workbook"></a>Výběr prvního listu v sešitu pomocí kolekce listů sešitu aplikace Excel

1. Voláním <xref:Microsoft.Office.Interop.Excel.Sheets.Select%2A> metody <xref:Microsoft.Office.Interop.Excel.Sheets> kolekce vyberte první list aktivního sešitu.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet20":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet20":::

## <a name="see-also"></a>Viz také
- [Práce s listy](../vsto/working-with-worksheets.md)
- [Postupy: tisk listů prostřednictvím kódu programu](../vsto/how-to-programmatically-print-worksheets.md)
- [Postupy: Odstraňování listů ze sešitů prostřednictvím kódu programu](../vsto/how-to-programmatically-delete-worksheets-from-workbooks.md)
- [Postupy: skrývání listů prostřednictvím kódu programu](../vsto/how-to-programmatically-hide-worksheets.md)
- [Postupy: ochrana listů prostřednictvím kódu programu](../vsto/how-to-programmatically-protect-worksheets.md)
- [Položka hostitele listu](../vsto/worksheet-host-item.md)
- [Globální přístup k objektům v projektech pro systém Office](../vsto/global-access-to-objects-in-office-projects.md)
- [Programové omezení hostitelských položek a hostitelských ovládacích prvků](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Volitelné parametry v řešeních pro systém Office](../vsto/optional-parameters-in-office-solutions.md)
- [Přehled hostitelských položek a hostitelských ovládacích prvků](../vsto/host-items-and-host-controls-overview.md)
