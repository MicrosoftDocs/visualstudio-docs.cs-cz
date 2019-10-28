---
title: 'Postupy: Změna velikosti ovládacích prvků ListObject'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- controls [Office development in Visual Studio], resizing
- ListObject control, resizing
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: fdebceb7ed6357542877bf13522425f7c013da73
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/28/2019
ms.locfileid: "72985757"
---
# <a name="how-to-resize-listobject-controls"></a>Postupy: Změna velikosti ovládacích prvků ListObject
  Velikost ovládacího prvku <xref:Microsoft.Office.Tools.Excel.ListObject> nastavíte, když ho přidáte do systém Microsoft Office excelového sešitu; později je ale vhodné změnit jeho velikost. Například může být vhodné změnit seznam se dvěma sloupci na tři sloupce.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 Můžete změnit velikost <xref:Microsoft.Office.Tools.Excel.ListObject> ovládacích prvků v době návrhu nebo v době běhu v projektech na úrovni dokumentu. Můžete změnit velikost <xref:Microsoft.Office.Tools.Excel.ListObject> ovládacích prvků za běhu v projektu doplňku VSTO.

 V tomto tématu jsou popsány následující úlohy:

- [Změnit velikost ovládacích prvků ListObject v době návrhu](#designtime)

- [Změna velikosti ovládacích prvků ListObject v době běhu v projektu na úrovni dokumentu](#runtimedoclevel)

- [Změna velikosti ovládacích prvků ListObject v době běhu v projektu doplňku VSTO](#runtimeaddin)

  Další informace o ovládacích prvcích <xref:Microsoft.Office.Tools.Excel.ListObject> naleznete v tématu [ListObject Control](../vsto/listobject-control.md).

## <a name="designtime"></a>Změna velikosti ovládacího prvku ListObject v době návrhu
 Chcete-li změnit velikost seznamu, můžete kliknout a přetáhnout jeden z úchytů pro změnu velikosti nebo můžete změnit jeho velikost v dialogovém okně **změnit velikost seznamu** .

### <a name="to-resize-a-list-by-using-the-resize-list-dialog-box"></a>Změna velikosti seznamu pomocí dialogového okna změnit velikost seznamu

1. Klikněte kamkoli do tabulky <xref:Microsoft.Office.Tools.Excel.ListObject>. Zobrazí se karta **Nástroje tabulky** > **Návrh** na pásu karet.

2. V části Vlastnosti klikněte na **změnit velikost tabulky**.

    ![VSTO_ResizeTable](../vsto/media/vsto-resizetable.png)

3. Vyberte nový rozsah dat pro tabulku.

4. Klikněte na tlačítko **OK**.

## <a name="runtimedoclevel"></a>Změna velikosti ovládacího prvku ListObject v době běhu v projektu na úrovni dokumentu
 Můžete změnit velikost ovládacího prvku <xref:Microsoft.Office.Tools.Excel.ListObject> v době běhu pomocí metody <xref:Microsoft.Office.Tools.Excel.ListObject.Resize%2A>. Tuto metodu nelze použít k přesunutí ovládacího prvku <xref:Microsoft.Office.Tools.Excel.ListObject> do nového umístění na listu. Hlavičky musí zůstat ve stejném řádku a ovládací prvek <xref:Microsoft.Office.Tools.Excel.ListObject> se změněnou velikostí musí překrývat původní objekt seznamu. <xref:Microsoft.Office.Tools.Excel.ListObject> ovládací prvek se změněnou velikostí musí obsahovat řádek záhlaví a alespoň jeden řádek dat.

### <a name="to-resize-a-list-object-programmatically"></a>Chcete-li změnit velikost objektu seznamu prostřednictvím kódu programu

1. Vytvoří ovládací prvek <xref:Microsoft.Office.Tools.Excel.ListObject>, který pokrývá buňku **a1** až **B3** v `Sheet1`.

     [!code-csharp[Trin_VstcoreHostControlsExcel#6](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#6)]
     [!code-vb[Trin_VstcoreHostControlsExcel#6](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#6)]

2. Změňte velikost seznamu tak, aby zahrnoval buňky **a1** až **C5**.

     [!code-csharp[Trin_VstcoreHostControlsExcel#7](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#7)]
     [!code-vb[Trin_VstcoreHostControlsExcel#7](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#7)]

## <a name="runtimeaddin"></a>Změna velikosti ListObject v době běhu v projektu doplňku VSTO
 Velikost ovládacího prvku <xref:Microsoft.Office.Tools.Excel.ListObject> můžete změnit na jakémkoli otevřeném listu za běhu. Další informace o tom, jak přidat ovládací prvek <xref:Microsoft.Office.Tools.Excel.ListObject> do listu pomocí doplňku VSTO, najdete v tématu [Postup: Přidání ovládacích prvků ListObject do listů](../vsto/how-to-add-listobject-controls-to-worksheets.md).

### <a name="to-resize-a-list-object-programmatically"></a>Chcete-li změnit velikost objektu seznamu prostřednictvím kódu programu

1. Vytvoří ovládací prvek <xref:Microsoft.Office.Tools.Excel.ListObject>, který pokrývá buňku **a1** až **B3** v `Sheet1`.

     [!code-csharp[Trin_Excel_Dynamic_Controls#12](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs#12)]
     [!code-vb[Trin_Excel_Dynamic_Controls#12](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb#12)]

2. Změňte velikost seznamu tak, aby zahrnoval buňky **a1** až **C5**.

     [!code-csharp[Trin_Excel_Dynamic_Controls#13](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs#13)]
     [!code-vb[Trin_Excel_Dynamic_Controls#13](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb#13)]

## <a name="see-also"></a>Viz také:
- [Rozšiřování dokumentů aplikace Word a excelových sešitů v doplňcích VSTO za běhu](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Ovládací prvky v dokumentech Office](../vsto/controls-on-office-documents.md)
- [Přidání ovládacích prvků do dokumentů Office v době běhu](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Přehled hostitelských položek a hostitelských ovládacích prvků](../vsto/host-items-and-host-controls-overview.md)
- [Automatizace Excelu pomocí rozšířených objektů](../vsto/automating-excel-by-using-extended-objects.md)
- [Ovládací prvek ListObject](../vsto/listobject-control.md)
- [Postupy: Přidání ovládacích prvků ListObject do listů](../vsto/how-to-add-listobject-controls-to-worksheets.md)
- [Postupy: Změna velikosti ovládacích prvků záložek](../vsto/how-to-resize-bookmark-controls.md)
- [Postupy: Změna velikosti ovládacích prvků NamedRange](../vsto/how-to-resize-namedrange-controls.md)
