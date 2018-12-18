---
title: 'Postupy: programové skupiny řádků v listech'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: aa9624f90a337fb85ba2868b3b5c4f3cb1553ffb
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/11/2018
ms.locfileid: "35258733"
---
# <a name="how-to-programmatically-group-rows-in-a-worksheet"></a>Postupy: programové skupiny řádků v listech
  Můžete seskupit jeden nebo více celou řádků. Chcete-li vytvořit skupinu v listu, použijte <xref:Microsoft.Office.Tools.Excel.NamedRange> ovládací prvek nebo objekt rozsahu nativní aplikace Excel.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="use-a-namedrange-control"></a>Použití ovládacího prvku NamedRange  
 Pokud přidáte <xref:Microsoft.Office.Tools.Excel.NamedRange> ovládacího prvku do projektu úrovni dokumentu v době návrhu, můžete použít ovládací prvek prostřednictvím kódu programu vytvořte skupinu. V následujícím příkladu se předpokládá, že existují tři <xref:Microsoft.Office.Tools.Excel.NamedRange> ovládacích prvků na stejné listu: `data2001`, `data2002`, a `dataAll`. Každé pojmenované oblasti odkazuje na celý řádek do listu.  
  
### <a name="to-create-a-group-of-namedrange-controls-on-a-worksheet"></a>Chcete-li vytvořit skupinu ovládacích prvků NamedRange do listu  
  
1.  Skupina tří pojmenované oblasti voláním <xref:Microsoft.Office.Tools.Excel.NamedRange.Group%2A> metoda každého rozsahu. Tento kód musí být umístěny v listu třída, není v `ThisWorkbook` třídy.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#32](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#32)]
     [!code-vb[Trin_VstcoreExcelAutomation#32](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#32)]  
  
    > [!NOTE]  
    >  Chcete-li zrušit seskupení řádků, zavolejte <xref:Microsoft.Office.Tools.Excel.NamedRange.Ungroup%2A> metoda.  
  
## <a name="use-native-excel-ranges"></a>Použít nativní oblastí aplikace Excel  
 Kód předpokládá, že máte tři oblastí aplikace Excel s názvem `data2001`, `data2002`, a `dataAll` na listu.  
  
### <a name="to-create-a-group-of-excel-ranges-in-a-worksheet"></a>Chcete-li vytvořit skupinu oblastí aplikace Excel v listu  
  
1.  Skupina tří pojmenované oblasti voláním <xref:Microsoft.Office.Interop.Excel.Range.Group%2A> metoda každého rozsahu. V následujícím příkladu se předpokládá, že existují tři <xref:Microsoft.Office.Interop.Excel.Range> ovládací prvky s názvem `data2001`, `data2002`, a `dataAll` na stejném listu. Každé pojmenované oblasti odkazuje na celý řádek do listu.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#33](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#33)]
     [!code-vb[Trin_VstcoreExcelAutomation#33](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#33)]  
  
    > [!NOTE]  
    >  Chcete-li zrušit seskupení řádků, zavolejte <xref:Microsoft.Office.Interop.Excel.Range.Ungroup%2A> metoda.  
  
## <a name="see-also"></a>Viz také:  
 [Práce s listy](../vsto/working-with-worksheets.md)   
 [NamedRange – ovládací prvek](../vsto/namedrange-control.md)   
 [Postupy: Přidání ovládacích prvků NamedRange do listů](../vsto/how-to-add-namedrange-controls-to-worksheets.md)   
 [Volitelné parametry v řešeních pro systém Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  