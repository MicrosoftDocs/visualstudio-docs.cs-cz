---
title: 'Postupy: zobrazení seznamu všech listů v sešitech prostřednictvím kódu programu'
description: Přečtěte si, jak můžete programově zobrazit seznam všech listů v sešitu Microsoft Excelu pomocí sady Visual Studio.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- workbooks, listing worksheets
- worksheets, listing
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 1446a4323ac190ede301e3a1cc55ccf1cae3b491
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99885310"
---
# <a name="how-to-programmatically-list-all-worksheets-in-a-workbook"></a>Postupy: zobrazení seznamu všech listů v sešitech prostřednictvím kódu programu
  <xref:Microsoft.Office.Interop.Excel.Workbook>Třída poskytuje <xref:Microsoft.Office.Interop.Excel.Worksheets> objekt. Tento objekt obsahuje kolekci všech <xref:Microsoft.Office.Interop.Excel.Worksheet> objektů v sešitu.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="to-list-all-existing-worksheets-in-a-workbook-in-a-document-level-customization"></a>Vypsání všech stávajících listů v sešitu v přizpůsobení na úrovni dokumentu

1. Iterujte pomocí <xref:Microsoft.Office.Interop.Excel.Worksheets> kolekce a odešlete název každého listu na posun buňky od <xref:Microsoft.Office.Tools.Excel.NamedRange> ovládacího prvku.

     [!code-csharp[Trin_VstcoreExcelAutomation#21](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#21)]
     [!code-vb[Trin_VstcoreExcelAutomation#21](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#21)]

## <a name="to-list-all-existing-worksheets-in-a-workbook-in-a-vsto-add-in"></a>Vypsání všech stávajících listů v sešitu v doplňku VSTO

1. Iterujte pomocí <xref:Microsoft.Office.Interop.Excel.Worksheets> kolekce a odešlete název každého listu na posun buňky od <xref:Microsoft.Office.Interop.Excel.Range> objektu.

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#13](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#13)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#13](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#13)]

## <a name="see-also"></a>Viz také
- [Práce s listy](../vsto/working-with-worksheets.md)
- [Postupy: přidávání nových listů do sešitů prostřednictvím kódu programu](../vsto/how-to-programmatically-add-new-worksheets-to-workbooks.md)
- [Postupy: přesouvání listů v sešitech prostřednictvím kódu programu](../vsto/how-to-programmatically-move-worksheets-within-workbooks.md)
- [Globální přístup k objektům v projektech pro systém Office](../vsto/global-access-to-objects-in-office-projects.md)
