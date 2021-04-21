---
title: 'Postupy: přidávání nových listů do sešitů prostřednictvím kódu programu'
description: Zjistěte, jak můžete programově vytvořit list a pak přidat list do kolekce listů v sešitu.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- workbooks, adding worksheets
- workbooks, creating worksheets
- worksheets, creating
- worksheets, adding to workbooks
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: c093d61e38b3416fbef1e85dcf5af052c64db590
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/21/2021
ms.locfileid: "107827406"
---
# <a name="how-to-programmatically-add-new-worksheets-to-workbooks"></a>Postupy: přidávání nových listů do sešitů prostřednictvím kódu programu
  Můžete programově vytvořit list a potom přidat list do kolekce listů v sešitu.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="to-add-a-new-worksheet-to-a-workbook-in-a-document-level-customization"></a>Přidání nového listu do sešitu v přizpůsobení na úrovni dokumentu

1. Použijte <xref:Microsoft.Office.Interop.Excel.Worksheets.Add%2A> metodu <xref:Microsoft.Office.Interop.Excel.Sheets> kolekce.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet15":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet15":::

     Nový list je nativní <xref:Microsoft.Office.Interop.Excel.Worksheet> objekt, nikoli Hostitelská položka. Pokud chcete přidat <xref:Microsoft.Office.Tools.Excel.Worksheet> položku hostitele, přidejte list v době návrhu.

## <a name="to-add-a-new-worksheet-to-a-workbook-in-a-vsto-add-in"></a>Přidání nového listu do sešitu v doplňku VSTO

1. Použijte <xref:Microsoft.Office.Interop.Excel.Worksheets.Add%2A> metodu <xref:Microsoft.Office.Interop.Excel.Sheets> kolekce.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet11":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet11":::

     Nový list je nativní <xref:Microsoft.Office.Interop.Excel.Worksheet> objekt, nikoli Hostitelská položka. Můžete také vygenerovat <xref:Microsoft.Office.Tools.Excel.Worksheet> položku hostitele z nativního <xref:Microsoft.Office.Interop.Excel.Worksheet> objektu. Další informace najdete v tématu [rozšíření dokumentů aplikace Word a sešitů aplikace Excel v doplňkech VSTO za běhu](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).

## <a name="see-also"></a>Viz také
- [Práce s listy](../vsto/working-with-worksheets.md)
- [Přehled hostitelských položek a hostitelských ovládacích prvků](../vsto/host-items-and-host-controls-overview.md)
- [Postupy: Odstraňování listů ze sešitů prostřednictvím kódu programu](../vsto/how-to-programmatically-delete-worksheets-from-workbooks.md)
- [Postupy: Výběr listů prostřednictvím kódu programu](../vsto/how-to-programmatically-select-worksheets.md)
- [Automatizace Excelu pomocí rozšířených objektů](../vsto/automating-excel-by-using-extended-objects.md)
- [Globální přístup k objektům v projektech pro systém Office](../vsto/global-access-to-objects-in-office-projects.md)
- [Volitelné parametry v řešeních pro systém Office](../vsto/optional-parameters-in-office-solutions.md)
