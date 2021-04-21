---
title: 'Postupy: odebrání ochrany z listů prostřednictvím kódu programu'
description: Přečtěte si, jak můžete pomocí sady Visual Studio programově odebrat ochranu z listu Microsoft Excelu.
ms.custom: SEO-VS-2020
titleSuffix: ''
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: c392ee3434edf9211a4a3061e7a83a8621960430
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/21/2021
ms.locfileid: "107824156"
---
# <a name="how-to-programmatically-remove-protection-from-worksheets"></a>Postupy: odebrání ochrany z listů prostřednictvím kódu programu
  Můžete programově odebrat ochranu z systém Microsoft Office excelového listu.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 Následující příklad používá proměnnou `getPasswordFromUser` , která obsahuje heslo získané od uživatele.

## <a name="to-unprotect-a-worksheet-in-a-document-level-customization"></a>Odemknutí listu v přizpůsobení na úrovni dokumentu

1. Zavolejte <xref:Microsoft.Office.Tools.Excel.Worksheet.Unprotect%2A> metodu listu a v případě potřeby předejte heslo. V tomto příkladu se předpokládá, že pracujete s listem s názvem `Sheet1` .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet28":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet28":::

## <a name="to-unprotect-a-worksheet-in-a-vsto-add-in"></a>Odemknutí listu v doplňku VSTO

1. V <xref:Microsoft.Office.Interop.Excel._Worksheet.Unprotect%2A> případě potřeby zavolejte na aktivní list metodu a předejte heslo.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet18":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet18":::

## <a name="see-also"></a>Viz také
- [Práce s listy](../vsto/working-with-worksheets.md)
- [Postupy: ochrana listů prostřednictvím kódu programu](../vsto/how-to-programmatically-protect-worksheets.md)
- [Postupy: Ochrana sešitů prostřednictvím kódu programu](../vsto/how-to-programmatically-protect-workbooks.md)
- [Postupy: skrývání listů prostřednictvím kódu programu](../vsto/how-to-programmatically-hide-worksheets.md)
- [Globální přístup k objektům v projektech pro systém Office](../vsto/global-access-to-objects-in-office-projects.md)
