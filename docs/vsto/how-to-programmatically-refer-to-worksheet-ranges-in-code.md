---
title: 'Postupy: odkazování na oblasti listů v kódu prostřednictvím kódu programu'
description: Přečtěte si, jak můžete pomocí sady Visual Studio programově odkazovat na obsah ovládacího prvku NamedRange nebo nativního objektu oblasti aplikace Excel v listu aplikace Microsoft Excel.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ranges, referring to
- worksheets, referring to ranges
- referring to worksheet ranges
- Excel [Office development in Visual Studio], referring to worksheet ranges
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 6ea4e3da3c67d55aedea0d85a0a35b8ed2cf93b6
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/21/2021
ms.locfileid: "107827081"
---
# <a name="how-to-programmatically-refer-to-worksheet-ranges-in-code"></a>Postupy: odkazování na oblasti listů v kódu prostřednictvím kódu programu
  Podobný proces se používá pro odkazování na obsah <xref:Microsoft.Office.Tools.Excel.NamedRange> ovládacího prvku nebo nativního objektu oblasti aplikace Excel.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="use-a-namedrange-control"></a>Použití ovládacího prvku NamedRange
 Následující příklad přidá <xref:Microsoft.Office.Tools.Excel.NamedRange> do listu a následně přidá text do buňky v rozsahu.

### <a name="to-refer-to-a-namedrange-control"></a>Odkazování na ovládací prvek NamedRange

1. Přiřaďte řetězec k <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> vlastnosti <xref:Microsoft.Office.Tools.Excel.NamedRange> ovládacího prvku. Tento kód musí být umístěn ve třídě listu, nikoli ve `ThisWorkbook` třídě.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet46":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet46":::

## <a name="use-native-excel-ranges"></a>Použít nativní oblasti aplikace Excel
 Následující příklad přidá do listu nativní rozsah aplikace Excel a následně přidá text do buňky v rozsahu.

### <a name="to-refer-to-a-native-range-object"></a>Odkazování na objekt nativního rozsahu

1. Přiřaďte řetězec k <xref:Microsoft.Office.Interop.Excel.Range.Value2%2A> Vlastnosti rozsahu.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet47":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet47":::

## <a name="see-also"></a>Viz také
- [Práce s rozsahy](../vsto/working-with-ranges.md)
- [Postupy: Kontrola pravopisu v listech prostřednictvím kódu programu](../vsto/how-to-programmatically-check-spelling-in-worksheets.md)
- [Postupy: používání stylů pro oblasti v sešitech prostřednictvím kódu programu](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)
- [Postupy: Automatické vyplňování oblastí pomocí přírůstkových změn dat prostřednictvím kódu programu](../vsto/how-to-programmatically-automatically-fill-ranges-with-incrementally-changing-data.md)
- [Postupy: hledání textu v oblastech listů prostřednictvím kódu programu](../vsto/how-to-programmatically-search-for-text-in-worksheet-ranges.md)
- [Ovládací prvek NamedRange](../vsto/namedrange-control.md)
- [Přehled hostitelských položek a hostitelských ovládacích prvků](../vsto/host-items-and-host-controls-overview.md)
- [Programové omezení hostitelských položek a hostitelských ovládacích prvků](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Volitelné parametry v řešeních pro systém Office](../vsto/optional-parameters-in-office-solutions.md)
