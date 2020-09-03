---
title: 'Postupy: odebrání ochrany z listů prostřednictvím kódu programu'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets, unprotecting
- documents [Office development in Visual Studio], document protection
- document protection, removing from worksheets
- Unprotect method
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 72448f9d1e5c24c917459b8c2c59e317190e0a11
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85519870"
---
# <a name="how-to-programmatically-remove-protection-from-worksheets"></a>Postupy: odebrání ochrany z listů prostřednictvím kódu programu
  Můžete programově odebrat ochranu z systém Microsoft Office excelového listu.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 Následující příklad používá proměnnou `getPasswordFromUser` , která obsahuje heslo získané od uživatele.

## <a name="to-unprotect-a-worksheet-in-a-document-level-customization"></a>Odemknutí listu v přizpůsobení na úrovni dokumentu

1. Zavolejte <xref:Microsoft.Office.Tools.Excel.Worksheet.Unprotect%2A> metodu listu a v případě potřeby předejte heslo. V tomto příkladu se předpokládá, že pracujete s listem s názvem `Sheet1` .

     [!code-csharp[Trin_VstcoreExcelAutomation#28](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#28)]
     [!code-vb[Trin_VstcoreExcelAutomation#28](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#28)]

## <a name="to-unprotect-a-worksheet-in-a-vsto-add-in"></a>Odemknutí listu v doplňku VSTO

1. V <xref:Microsoft.Office.Interop.Excel._Worksheet.Unprotect%2A> případě potřeby zavolejte na aktivní list metodu a předejte heslo.

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#18](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#18)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#18](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#18)]

## <a name="see-also"></a>Viz také
- [Práce s listy](../vsto/working-with-worksheets.md)
- [Postupy: ochrana listů prostřednictvím kódu programu](../vsto/how-to-programmatically-protect-worksheets.md)
- [Postupy: Ochrana sešitů prostřednictvím kódu programu](../vsto/how-to-programmatically-protect-workbooks.md)
- [Postupy: skrývání listů prostřednictvím kódu programu](../vsto/how-to-programmatically-hide-worksheets.md)
- [Globální přístup k objektům v projektech pro systém Office](../vsto/global-access-to-objects-in-office-projects.md)
