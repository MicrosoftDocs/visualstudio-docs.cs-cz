---
title: 'Postupy: používání stylů pro oblasti v sešitech prostřednictvím kódu programu'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ranges, styles
- styles, workbook ranges
- workbooks, styles
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: d6f115468bccc2d805b019b9a0ef15cea3605f36
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/30/2020
ms.locfileid: "85546156"
---
# <a name="how-to-programmatically-apply-styles-to-ranges-in-workbooks"></a>Postupy: používání stylů pro oblasti v sešitech prostřednictvím kódu programu
  Pojmenované styly můžete použít pro oblasti v sešitech. Aplikace Excel poskytuje řadu předdefinovaných stylů.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 V dialogovém okně **Formátovat buňky** se zobrazí všechny možnosti, které můžete použít k formátování buněk, a každá z těchto možností je k dispozici ve vašem kódu. Chcete-li zobrazit toto dialogové okno v aplikaci Excel, klikněte na položku **buňky** v nabídce **Formát** .

## <a name="to-apply-a-style-to-a-named-range-in-a-document-level-customization"></a>Použití stylu na pojmenovaný rozsah v přizpůsobení na úrovni dokumentu

1. Vytvořte nový styl a nastavte jeho atributy.

     [!code-csharp[Trin_VstcoreExcelAutomation#53](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#53)]
     [!code-vb[Trin_VstcoreExcelAutomation#53](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#53)]

2. Vytvořte <xref:Microsoft.Office.Tools.Excel.NamedRange> ovládací prvek, přiřaďte k němu text a pak použijte nový styl. Tento kód musí být umístěn ve třídě listu, nikoli ve `ThisWorkbook` třídě.

     [!code-csharp[Trin_VstcoreExcelAutomation#54](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#54)]
     [!code-vb[Trin_VstcoreExcelAutomation#54](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#54)]

## <a name="to-clear-a-style-from-a-named-range-in-a-document-level-customization"></a>Vymazání stylu z pojmenovaného rozsahu v přizpůsobení na úrovni dokumentu

1. Aplikuje normální styl na rozsah. Tento kód musí být umístěn ve třídě listu, nikoli ve `ThisWorkbook` třídě.

     [!code-csharp[Trin_VstcoreExcelAutomation#55](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#55)]
     [!code-vb[Trin_VstcoreExcelAutomation#55](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#55)]

## <a name="to-apply-a-style-to-a-named-range-in-a-vsto-add-in"></a>Použití stylu na pojmenovaný rozsah v doplňku VSTO

1. Vytvořte nový styl a nastavte jeho atributy.

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#28](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#28)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#28](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#28)]

2. Vytvořte <xref:Microsoft.Office.Interop.Excel.Range> , přiřaďte k němu text a pak použijte nový styl.

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#29](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#29)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#29](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#29)]

## <a name="to-clear-a-style-from-a-named-range-in-a-vsto-add-in"></a>Vymazání stylu z pojmenovaného rozsahu v doplňku VSTO

1. Aplikuje normální styl na rozsah.

     [!code-csharp[Trin_VstcoreExcelAutomation#56](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#56)]
     [!code-vb[Trin_VstcoreExcelAutomation#56](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#56)]

## <a name="see-also"></a>Viz také:
- [Práce s rozsahy](../vsto/working-with-ranges.md)
- [Ovládací prvek NamedRange](../vsto/namedrange-control.md)
- [Globální přístup k objektům v projektech pro systém Office](../vsto/global-access-to-objects-in-office-projects.md)
- [Volitelné parametry v řešeních pro systém Office](../vsto/optional-parameters-in-office-solutions.md)
