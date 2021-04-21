---
title: 'Postupy: řazení dat v listech prostřednictvím kódu programu'
description: Přečtěte si, jak můžete pomocí sady Visual Studio programově seřadit data, která jsou obsažena v oblastech a seznamech listů za běhu.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data sorting, worksheets
- data [Office development in Visual Studio], sorting in worksheets
- worksheets, sorting data
- sorting data, in worksheets
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 024bf53b7fc7f3a6e32e10b7107c9a62d8c40cee
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/21/2021
ms.locfileid: "107825014"
---
# <a name="how-to-programmatically-sort-data-in-worksheets"></a>Postupy: řazení dat v listech prostřednictvím kódu programu
  Data, která jsou obsažena v oblasti a v seznamech, můžete řadit v době běhu. Následující kód seřadí rozsah více sloupců s názvem `Fruits` daty v prvním sloupci a následně data ve druhém sloupci.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="sort-data-in-a-document-level-customization"></a>Řazení dat v přizpůsobení na úrovni dokumentu

### <a name="to-sort-data-in-a-namedrange-control"></a>Řazení dat v ovládacím prvku NamedRange

1. Zavolejte <xref:Microsoft.Office.Tools.Excel.NamedRange.Sort%2A> metodu <xref:Microsoft.Office.Tools.Excel.NamedRange> ovládacího prvku. Následující příklad vyžaduje <xref:Microsoft.Office.Tools.Excel.NamedRange> ovládací prvek s názvem `Fruits` na listu. Tento kód musí být umístěn ve třídě listu, nikoli ve `ThisWorkbook` třídě.

    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet78":::
    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet78":::

   Vložte následující kód do *List1. vb* nebo *List1. cs* a seřaďte data v <xref:Microsoft.Office.Tools.Excel.ListObject> ovládacím prvku. Kód předpokládá, že máte <xref:Microsoft.Office.Tools.Excel.ListObject> ovládací prvek s názvem `fruitList` v listu s názvem `Sheet1` .

### <a name="to-sort-data-in-a-listobject-control"></a>Řazení dat v ovládacím prvku ListObject

1. Zavolejte <xref:Microsoft.Office.Interop.Excel.Range.Sort%2A> metodu <xref:Microsoft.Office.Tools.Excel.ListObject.Range%2A> vlastnosti <xref:Microsoft.Office.Tools.Excel.ListObject> hostitelského ovládacího prvku.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet79":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet79":::

## <a name="sort-data-in-a-vsto-add-in"></a>Řazení dat v doplňku VSTO

### <a name="to-sort-data-in-a-native-range"></a>Řazení dat v nativním rozsahu

1. Zavolejte <xref:Microsoft.Office.Interop.Excel.Range.Sort%2A> metodu nativního <xref:Microsoft.Office.Interop.Excel.Range> ovládacího prvku aplikace Excel. Následující příklad vyžaduje nativní ovládací prvek aplikace Excel s názvem `Fruits` na listu.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet23":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet23":::

### <a name="to-sort-data-in-a-listobject-control"></a>Řazení dat v ovládacím prvku ListObject

1. Zavolejte <xref:Microsoft.Office.Interop.Excel.Range.Sort%2A> metodu <xref:Microsoft.Office.Tools.Excel.ListObject.Range%2A> vlastnosti nativního <xref:Microsoft.Office.Interop.Excel.ListObject> ovládacího prvku aplikace Excel. Následující příklad předpokládá, že máte nativní <xref:Microsoft.Office.Interop.Excel.ListObject> ovládací prvek aplikace Excel s názvem `fruitList` v aktivním listu.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet24":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet24":::

## <a name="see-also"></a>Viz také
- [Práce s listy](../vsto/working-with-worksheets.md)
- [Postupy: Automatické vyplňování oblastí pomocí přírůstkových změn dat prostřednictvím kódu programu](../vsto/how-to-programmatically-automatically-fill-ranges-with-incrementally-changing-data.md)
- [Postupy: odkazování na oblasti listů v kódu prostřednictvím kódu programu](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)
- [Postupy: používání stylů pro oblasti v sešitech prostřednictvím kódu programu](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)
- [Ovládací prvek NamedRange](../vsto/namedrange-control.md)
- [Ovládací prvek ListObject](../vsto/listobject-control.md)
- [Volitelné parametry v řešeních pro systém Office](../vsto/optional-parameters-in-office-solutions.md)
