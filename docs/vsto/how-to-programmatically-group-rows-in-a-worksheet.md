---
title: 'Postupy: seskupování řádků v listu prostřednictvím kódu programu'
description: Přečtěte si, jak můžete programově seskupit jeden nebo několik celých řádků v Microsoft Excelu pomocí ovládacího prvku NamedRange nebo nativního objektu Range Excelu.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets, creating groups
- groups, creating in worksheets
- ranges, creating groups
- worksheets, clearing groups
- groups
- groups [Office development in Visual Studio], clearing in worksheets
- worksheets, ungrouping rows and columns
- rows [Office development in Visual Studio], ungrouping
- columns [Office development in Visual Studio], ungrouping
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: eaa0bbcc2c26a36e43e862cbe5a8f117c2a1fb26
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99885414"
---
# <a name="how-to-programmatically-group-rows-in-a-worksheet"></a>Postupy: seskupování řádků v listu prostřednictvím kódu programu
  Můžete seskupit jeden nebo více celých řádků. Chcete-li vytvořit skupinu na listu, použijte <xref:Microsoft.Office.Tools.Excel.NamedRange> ovládací prvek nebo nativní objekt oblasti aplikace Excel.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="use-a-namedrange-control"></a>Použití ovládacího prvku NamedRange
 Pokud přidáte <xref:Microsoft.Office.Tools.Excel.NamedRange> ovládací prvek do projektu na úrovni dokumentu v době návrhu, můžete pomocí ovládacího prvku programově vytvořit skupinu. Následující příklad předpokládá, že <xref:Microsoft.Office.Tools.Excel.NamedRange> na stejném listu jsou tři ovládací prvky: `data2001` , `data2002` a `dataAll` . Každý pojmenovaný rozsah odkazuje na celý řádek v listu.

### <a name="to-create-a-group-of-namedrange-controls-on-a-worksheet"></a>Vytvoření skupiny ovládacích prvků NamedRange na listu

1. Seskupit tři pojmenované rozsahy voláním <xref:Microsoft.Office.Tools.Excel.NamedRange.Group%2A> metody každého rozsahu. Tento kód musí být umístěn ve třídě listu, nikoli ve `ThisWorkbook` třídě.

     [!code-csharp[Trin_VstcoreExcelAutomation#32](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#32)]
     [!code-vb[Trin_VstcoreExcelAutomation#32](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#32)]

    > [!NOTE]
    > Chcete-li zrušit seskupení řádků, zavolejte <xref:Microsoft.Office.Tools.Excel.NamedRange.Ungroup%2A> metodu.

## <a name="use-native-excel-ranges"></a>Použít nativní oblasti aplikace Excel
 Kód předpokládá, že máte tři oblasti aplikace Excel s názvem `data2001` , `data2002` a `dataAll` na listu.

### <a name="to-create-a-group-of-excel-ranges-in-a-worksheet"></a>Vytvoření skupiny oblastí aplikace Excel v listu

1. Seskupit tři pojmenované rozsahy voláním <xref:Microsoft.Office.Interop.Excel.Range.Group%2A> metody každého rozsahu. Následující příklad předpokládá, že existují tři <xref:Microsoft.Office.Interop.Excel.Range> ovládací prvky s názvem `data2001` , `data2002` a `dataAll` na stejném listu. Každý pojmenovaný rozsah odkazuje na celý řádek v listu.

     [!code-csharp[Trin_VstcoreExcelAutomation#33](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#33)]
     [!code-vb[Trin_VstcoreExcelAutomation#33](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#33)]

    > [!NOTE]
    > Chcete-li zrušit seskupení řádků, zavolejte <xref:Microsoft.Office.Interop.Excel.Range.Ungroup%2A> metodu.

## <a name="see-also"></a>Viz také
- [Práce s listy](../vsto/working-with-worksheets.md)
- [Ovládací prvek NamedRange](../vsto/namedrange-control.md)
- [Postupy: Přidání ovládacích prvků NamedRange do listů](../vsto/how-to-add-namedrange-controls-to-worksheets.md)
- [Volitelné parametry v řešeních pro systém Office](../vsto/optional-parameters-in-office-solutions.md)
