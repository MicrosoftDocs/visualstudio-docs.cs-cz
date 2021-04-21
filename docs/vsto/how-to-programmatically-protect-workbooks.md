---
title: 'Postupy: Ochrana sešitů prostřednictvím kódu programu'
description: Přečtěte si, jak můžete chránit sešit aplikace Microsoft Excel, aby uživatelé nemohli přidávat ani odstraňovat listy a zároveň Odemknout sešit prostřednictvím kódu programu.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- workbooks, passwords
- documents [Office development in Visual Studio], document protection
- workbooks, unprotecting
- document protection, removing from workbooks
- document protection, adding to workbooks
- workbooks, protecting
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 9f0b479c56be6da7b14f87263c8c01d66910ac20
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/21/2021
ms.locfileid: "107827105"
---
# <a name="how-to-programmatically-protect-workbooks"></a>Postupy: Ochrana sešitů prostřednictvím kódu programu
  Systém Microsoft Office excelový sešit můžete chránit tak, aby uživatelé nemohli přidávat ani odstraňovat listy a zároveň Odemknout sešit prostřednictvím kódu programu. Volitelně můžete zadat heslo, určit, jestli chcete strukturu chránit (takže uživatelé nemohou přesunout listy kolem) a určit, jestli chcete, aby byl sešit chráněný.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 Ochrana sešitu nebrání uživatelům upravovat buňky. Chcete-li chránit data, je nutné tyto listy chránit. Další informace najdete v tématu [How to: program Protecting lists](../vsto/how-to-programmatically-protect-worksheets.md).

 Následující příklady kódu používají proměnnou k omezení hesla získaného od uživatele.

## <a name="protect-a-workbook-that-is-part-of-a-document-level-customization"></a>Ochrana sešitu, který je součástí přizpůsobení na úrovni dokumentu

### <a name="to-protect-a-workbook"></a>Ochrana sešitu

1. Zavolejte <xref:Microsoft.Office.Tools.Excel.Workbook.Protect%2A> metodu sešitu a zahrňte heslo. Chcete-li použít následující příklad kódu, spusťte jej ve `ThisWorkbook` třídě, nikoli v tabulce typu.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/ThisWorkbook.cs" id="Snippet10":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/ThisWorkbook.vb" id="Snippet10":::

### <a name="to-unprotect-a-workbook"></a>Odemknutí sešitu

1. Zavolejte <xref:Microsoft.Office.Tools.Excel.Workbook.Unprotect%2A> metodu a předejte heslo, pokud je požadováno. Chcete-li použít následující příklad kódu, spusťte jej ve `ThisWorkbook` třídě, nikoli v tabulce typu.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/ThisWorkbook.cs" id="Snippet11":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/ThisWorkbook.vb" id="Snippet11":::

## <a name="protect-a-workbook-by-using-an-application-level-add-in"></a>Ochrana sešitu pomocí doplňku na úrovni aplikace

### <a name="to-protect-a-workbook"></a>Ochrana sešitu

1. Zavolejte <xref:Microsoft.Office.Interop.Excel._Workbook.Protect%2A> metodu sešitu a zahrňte heslo. Tento příklad kódu používá aktivní sešit. Chcete-li použít tento příklad, spusťte kód z `ThisAddIn` třídy v projektu.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet6":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet6":::

### <a name="to-unprotect-a-workbook"></a>Odemknutí sešitu

1. Zavolejte <xref:Microsoft.Office.Interop.Excel._Workbook.Unprotect%2A> metodu aktivního sešitu a předejte heslo, pokud je potřeba. Chcete-li použít tento příklad, spusťte kód z `ThisAddIn` třídy v projektu.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet7":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet7":::

## <a name="see-also"></a>Viz také
- [Práce se sešity](../vsto/working-with-workbooks.md)
- [Postupy: ochrana listů prostřednictvím kódu programu](../vsto/how-to-programmatically-protect-worksheets.md)
- [Postupy: skrývání listů prostřednictvím kódu programu](../vsto/how-to-programmatically-hide-worksheets.md)
- [Volitelné parametry v řešeních pro systém Office](../vsto/optional-parameters-in-office-solutions.md)
