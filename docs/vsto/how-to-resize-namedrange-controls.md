---
title: 'Postupy: Změna velikosti ovládacích prvků NamedRange'
description: Přečtěte si, jak můžete pomocí sady Visual Studio programově měnit velikost ovládacích prvků NamedRange v sešitu Microsoft Excelu.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- controls [Office development in Visual Studio], resizing
- NamedRange control, resizing
- ranges, resizing in Excel
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 043def019d30ee629e672a081cd5aea73bca4304
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/15/2020
ms.locfileid: "97528185"
---
# <a name="how-to-resize-namedrange-controls"></a>Postupy: Změna velikosti ovládacích prvků NamedRange
  Velikost ovládacího prvku můžete nastavit, <xref:Microsoft.Office.Tools.Excel.NamedRange> když ho přidáte do dokumentu aplikace systém Microsoft Office Excel, ale budete ho chtít později změnit.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 Můžete změnit velikost pojmenovaného rozsahu v době návrhu nebo v době běhu v projektech na úrovni dokumentu. Můžete také změnit velikost pojmenovaných rozsahů za běhu v Doplňkech VSTO na úrovni aplikace.

 V tomto tématu jsou popsány následující úlohy:

- [Změnit velikost ovládacích prvků NamedRange v době návrhu](#designtime)

- [Změna velikosti ovládacích prvků NamedRange v době běhu v projektu na úrovni dokumentu](#runtimedoclevel)

- [Změna velikosti ovládacích prvků NamedRange v době běhu v projektu doplňku VSTO](#runtimeaddin)

## <a name="resize-namedrange-controls-at-design-time"></a><a name="designtime"></a> Změnit velikost ovládacích prvků NamedRange v době návrhu
 Velikost pojmenovaného rozsahu můžete změnit v dialogovém okně **definovat název** podle definice.

### <a name="to-resize-a-named-range-by-using-the-define-name-dialog-box"></a>Změna velikosti pojmenovaného rozsahu pomocí dialogového okna definovat název

1. Klikněte pravým tlačítkem myši na <xref:Microsoft.Office.Tools.Excel.NamedRange> ovládací prvek.

2. V místní nabídce klikněte na možnost **Spravovat pojmenované rozsahy** .

     Zobrazí se dialogové okno **definovat název** .

3. Vyberte pojmenovaný rozsah, u kterého chcete změnit velikost.

4. Zrušte zaškrtnutí políčka **odkazovat na** .

5. Vyberte buňky, které chcete použít k definování velikosti pojmenovaného rozsahu.

6. Klikněte na **OK**.

## <a name="resize-namedrange-controls-at-run-time-in-a-document-level-project"></a><a name="runtimedoclevel"></a> Změna velikosti ovládacích prvků NamedRange v době běhu v projektu na úrovni dokumentu
 Velikost pojmenovaného rozsahu lze změnit programově pomocí <xref:Microsoft.Office.Tools.Excel.NamedRange.RefersTo%2A> Vlastnosti.

> [!NOTE]
> V okně **vlastnosti** <xref:Microsoft.Office.Tools.Excel.NamedRange.RefersTo%2A> je vlastnost označena jako jen pro čtení.

### <a name="to-resize-a-named-range-programmatically"></a>Postup při změně velikosti pojmenovaného rozsahu prostřednictvím kódu programu

1. Vytvoří <xref:Microsoft.Office.Tools.Excel.NamedRange> ovládací prvek na buňce **a1** `Sheet1` .

     [!code-csharp[Trin_VstcoreHostControlsExcel#4](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#4)]
     [!code-vb[Trin_VstcoreHostControlsExcel#4](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#4)]

2. Změňte velikost pojmenovaného rozsahu tak, aby zahrnoval buňku **B1**.

     [!code-csharp[Trin_VstcoreHostControlsExcel#5](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#5)]
     [!code-vb[Trin_VstcoreHostControlsExcel#5](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#5)]

## <a name="resize-namedrange-controls-at-run-time-in-a-vsto-add-in-project"></a><a name="runtimeaddin"></a> Změna velikosti ovládacích prvků NamedRange v době běhu v projektu doplňku VSTO
 Velikost <xref:Microsoft.Office.Tools.Excel.NamedRange> ovládacího prvku můžete změnit na libovolný otevřený list za běhu. Další informace o tom, jak přidat <xref:Microsoft.Office.Tools.Excel.NamedRange> ovládací prvek do listu pomocí doplňku VSTO, najdete v tématu [Postupy: Přidání ovládacích prvků NamedRange do listů](../vsto/how-to-add-namedrange-controls-to-worksheets.md).

### <a name="to-resize-a-named-range-programmatically"></a>Postup při změně velikosti pojmenovaného rozsahu prostřednictvím kódu programu

1. Vytvoří <xref:Microsoft.Office.Tools.Excel.NamedRange> ovládací prvek na buňce **a1** `Sheet1` .

     [!code-csharp[Trin_Excel_Dynamic_Controls#10](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs#10)]
     [!code-vb[Trin_Excel_Dynamic_Controls#10](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb#10)]

2. Změňte velikost pojmenovaného rozsahu tak, aby zahrnoval buňku **B1**.

     [!code-csharp[Trin_Excel_Dynamic_Controls#11](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs#11)]
     [!code-vb[Trin_Excel_Dynamic_Controls#11](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb#11)]

## <a name="see-also"></a>Viz také
- [Rozšiřování dokumentů aplikace Word a excelových sešitů v doplňcích VSTO za běhu](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Přidání ovládacích prvků do dokumentů Office v době běhu](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Ovládací prvky v dokumentech Office](../vsto/controls-on-office-documents.md)
- [Přehled hostitelských položek a hostitelských ovládacích prvků](../vsto/host-items-and-host-controls-overview.md)
- [Automatizace Excelu pomocí rozšířených objektů](../vsto/automating-excel-by-using-extended-objects.md)
- [Ovládací prvek NamedRange](../vsto/namedrange-control.md)
- [Postupy: Přidání ovládacích prvků NamedRange do listů](../vsto/how-to-add-namedrange-controls-to-worksheets.md)
- [Postupy: Změna velikosti ovládacích prvků záložek](../vsto/how-to-resize-bookmark-controls.md)
- [Postupy: Změna velikosti ovládacích prvků ListObject](../vsto/how-to-resize-listobject-controls.md)
