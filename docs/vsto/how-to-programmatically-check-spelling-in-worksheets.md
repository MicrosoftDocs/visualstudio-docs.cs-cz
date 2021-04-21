---
title: 'Postupy: Kontrola pravopisu v listech prostřednictvím kódu programu'
description: Přečtěte si, jak můžete programově kontrolovat pravopis slov v listu Microsoft Excelu.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- spellchecking
- spelling checker, worksheets
- worksheets, checking spelling
- spelling, checking in worksheets
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 1bf35e225def686ae2424a89b7e5d6b77207ccee
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/21/2021
ms.locfileid: "107826054"
---
# <a name="how-to-programmatically-check-spelling-in-worksheets"></a>Postupy: Kontrola pravopisu v listech prostřednictvím kódu programu
  Můžete programově kontrolovat pravopis slov v listu. Dialogové okno **Pravopis** se zobrazí automaticky v případě, že se v listu nacházejí nesprávně napsaná slova.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="to-check-spelling-in-a-worksheet-in-a-document-level-customization"></a>Kontrola pravopisu v listu v přizpůsobení na úrovni dokumentu

1. Zavolejte <xref:Microsoft.Office.Tools.Excel.Worksheet.CheckSpelling%2A> metodu listu.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet45":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet45":::

## <a name="to-check-spelling-in-a-worksheet-in-a-vsto-add-in"></a>Kontrola pravopisu v listu v doplňku VSTO

1. Zavolejte <xref:Microsoft.Office.Interop.Excel._Worksheet.CheckSpelling%2A> metodu aktivního listu.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet22":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet22":::

## <a name="see-also"></a>Viz také
- [Práce s listy](../vsto/working-with-worksheets.md)
- [Postupy: spouštění výpočtů v aplikaci Excel prostřednictvím kódu programu](../vsto/how-to-programmatically-run-excel-calculations-programmatically.md)
- [Ovládací prvek NamedRange](../vsto/namedrange-control.md)
- [Volitelné parametry v řešeních pro systém Office](../vsto/optional-parameters-in-office-solutions.md)
