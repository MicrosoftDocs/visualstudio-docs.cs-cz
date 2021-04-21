---
title: 'Postupy: používání stylů pro oblasti v sešitech prostřednictvím kódu programu'
description: Přečtěte si, jak můžete použít pojmenované styly na oblasti v sešitech. Aplikace Excel poskytuje řadu předdefinovaných stylů.
ms.custom: SEO-VS-2020
titleSuffix: ''
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: b1ce30c9a0e21bd4b8860f7a4d17191c48cd2ad9
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/21/2021
ms.locfileid: "107828303"
---
# <a name="how-to-programmatically-apply-styles-to-ranges-in-workbooks"></a>Postupy: používání stylů pro oblasti v sešitech prostřednictvím kódu programu
  Pojmenované styly můžete použít pro oblasti v sešitech. Aplikace Excel poskytuje řadu předdefinovaných stylů.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 V dialogovém okně **Formátovat buňky** se zobrazí všechny možnosti, které můžete použít k formátování buněk, a každá z těchto možností je k dispozici ve vašem kódu. Chcete-li zobrazit toto dialogové okno v aplikaci Excel, klikněte na položku **buňky** v nabídce **Formát** .

## <a name="to-apply-a-style-to-a-named-range-in-a-document-level-customization"></a>Použití stylu na pojmenovaný rozsah v přizpůsobení na úrovni dokumentu

1. Vytvořte nový styl a nastavte jeho atributy.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet53":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet53":::

2. Vytvořte <xref:Microsoft.Office.Tools.Excel.NamedRange> ovládací prvek, přiřaďte k němu text a pak použijte nový styl. Tento kód musí být umístěn ve třídě listu, nikoli ve `ThisWorkbook` třídě.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet54":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet54":::

## <a name="to-clear-a-style-from-a-named-range-in-a-document-level-customization"></a>Vymazání stylu z pojmenovaného rozsahu v přizpůsobení na úrovni dokumentu

1. Aplikuje normální styl na rozsah. Tento kód musí být umístěn ve třídě listu, nikoli ve `ThisWorkbook` třídě.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet55":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet55":::

## <a name="to-apply-a-style-to-a-named-range-in-a-vsto-add-in"></a>Použití stylu na pojmenovaný rozsah v doplňku VSTO

1. Vytvořte nový styl a nastavte jeho atributy.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet28":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet28":::

2. Vytvořte <xref:Microsoft.Office.Interop.Excel.Range> , přiřaďte k němu text a pak použijte nový styl.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet29":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet29":::

## <a name="to-clear-a-style-from-a-named-range-in-a-vsto-add-in"></a>Vymazání stylu z pojmenovaného rozsahu v doplňku VSTO

1. Aplikuje normální styl na rozsah.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet56":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet56":::

## <a name="see-also"></a>Viz také
- [Práce s rozsahy](../vsto/working-with-ranges.md)
- [Ovládací prvek NamedRange](../vsto/namedrange-control.md)
- [Globální přístup k objektům v projektech pro systém Office](../vsto/global-access-to-objects-in-office-projects.md)
- [Volitelné parametry v řešeních pro systém Office](../vsto/optional-parameters-in-office-solutions.md)
