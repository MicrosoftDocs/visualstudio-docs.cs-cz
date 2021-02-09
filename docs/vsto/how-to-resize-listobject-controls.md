---
title: 'Postupy: Změna velikosti ovládacích prvků ListObject'
description: Přečtěte si, jak můžete pomocí sady Visual Studio programově měnit velikost ovládacích prvků ListObject v sešitu Microsoft Excelu.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- controls [Office development in Visual Studio], resizing
- ListObject control, resizing
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: e839e253e54e7c9c0358bef7330f9e330684b809
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99927831"
---
# <a name="how-to-resize-listobject-controls"></a>Postupy: Změna velikosti ovládacích prvků ListObject
  Velikost <xref:Microsoft.Office.Tools.Excel.ListObject> ovládacího prvku se nastavuje při jeho přidání do systém Microsoft Office excelového sešitu, ale můžete ho chtít později změnit. Například může být vhodné změnit seznam se dvěma sloupci na tři sloupce.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 Můžete změnit velikost <xref:Microsoft.Office.Tools.Excel.ListObject> ovládacích prvků v době návrhu nebo v době běhu v projektech na úrovni dokumentu. <xref:Microsoft.Office.Tools.Excel.ListObject>V projektu doplňku VSTO můžete změnit velikost ovládacích prvků v době běhu.

 V tomto tématu jsou popsány následující úlohy:

- [Změnit velikost ovládacích prvků ListObject v době návrhu](#designtime)

- [Změna velikosti ovládacích prvků ListObject v době běhu v projektu na úrovni dokumentu](#runtimedoclevel)

- [Změna velikosti ovládacích prvků ListObject v době běhu v projektu doplňku VSTO](#runtimeaddin)

  Další informace o <xref:Microsoft.Office.Tools.Excel.ListObject> ovládacích prvcích naleznete v tématu [ListObject Control](../vsto/listobject-control.md).

## <a name="resize-a-listobject-control-at-design-time"></a><a name="designtime"></a> Změna velikosti ovládacího prvku ListObject v době návrhu
 Chcete-li změnit velikost seznamu, můžete kliknout a přetáhnout jeden z úchytů pro změnu velikosti nebo můžete změnit jeho velikost v dialogovém okně **změnit velikost seznamu** .

### <a name="to-resize-a-list-by-using-the-resize-list-dialog-box"></a>Změna velikosti seznamu pomocí dialogového okna změnit velikost seznamu

1. Klikněte kamkoli do  <xref:Microsoft.Office.Tools.Excel.ListObject> tabulky.   >  Zobrazí se karta **Návrh** nástrojů tabulky na pásu karet.

2. V části Vlastnosti klikněte na **změnit velikost tabulky**.

    ![VSTO_ResizeTable](../vsto/media/vsto-resizetable.png)

3. Vyberte nový rozsah dat pro tabulku.

4. Klikněte na **OK**.

## <a name="resize-a-listobject-control-at-run-time-in-a-document-level-project"></a><a name="runtimedoclevel"></a> Změna velikosti ovládacího prvku ListObject v době běhu v projektu na úrovni dokumentu
 Můžete změnit velikost <xref:Microsoft.Office.Tools.Excel.ListObject> ovládacího prvku v době běhu pomocí <xref:Microsoft.Office.Tools.Excel.ListObject.Resize%2A> metody. Tuto metodu nelze použít k přesunutí <xref:Microsoft.Office.Tools.Excel.ListObject> ovládacího prvku na nové místo na listu. Hlavičky musí zůstat ve stejném řádku a <xref:Microsoft.Office.Tools.Excel.ListObject> ovládací prvek změnit velikost musí překrývat původní objekt seznamu. Ovládací prvek se změněnou velikostí <xref:Microsoft.Office.Tools.Excel.ListObject> musí obsahovat řádek záhlaví a alespoň jeden řádek dat.

### <a name="to-resize-a-list-object-programmatically"></a>Chcete-li změnit velikost objektu seznamu prostřednictvím kódu programu

1. Vytvoří <xref:Microsoft.Office.Tools.Excel.ListObject> ovládací prvek, který pokrývá buňku **a1** až **B3** `Sheet1` .

     [!code-csharp[Trin_VstcoreHostControlsExcel#6](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#6)]
     [!code-vb[Trin_VstcoreHostControlsExcel#6](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#6)]

2. Změňte velikost seznamu tak, aby zahrnoval buňky **a1** až **C5**.

     [!code-csharp[Trin_VstcoreHostControlsExcel#7](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#7)]
     [!code-vb[Trin_VstcoreHostControlsExcel#7](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#7)]

## <a name="resize-a-listobject-at-run-time-in-a-vsto-add-in-project"></a><a name="runtimeaddin"></a> Změna velikosti ListObject v době běhu v projektu doplňku VSTO
 Velikost <xref:Microsoft.Office.Tools.Excel.ListObject> ovládacího prvku můžete změnit na libovolný otevřený list za běhu. Další informace o tom, jak přidat <xref:Microsoft.Office.Tools.Excel.ListObject> ovládací prvek do listu pomocí doplňku VSTO, najdete v tématu [Postupy: Přidání ovládacích prvků ListObject do listů](../vsto/how-to-add-listobject-controls-to-worksheets.md).

### <a name="to-resize-a-list-object-programmatically"></a>Chcete-li změnit velikost objektu seznamu prostřednictvím kódu programu

1. Vytvoří <xref:Microsoft.Office.Tools.Excel.ListObject> ovládací prvek, který pokrývá buňku **a1** až **B3** `Sheet1` .

     [!code-csharp[Trin_Excel_Dynamic_Controls#12](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs#12)]
     [!code-vb[Trin_Excel_Dynamic_Controls#12](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb#12)]

2. Změňte velikost seznamu tak, aby zahrnoval buňky **a1** až **C5**.

     [!code-csharp[Trin_Excel_Dynamic_Controls#13](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs#13)]
     [!code-vb[Trin_Excel_Dynamic_Controls#13](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb#13)]

## <a name="see-also"></a>Viz také
- [Rozšiřování dokumentů aplikace Word a excelových sešitů v doplňcích VSTO za běhu](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Ovládací prvky v dokumentech Office](../vsto/controls-on-office-documents.md)
- [Přidání ovládacích prvků do dokumentů Office v době běhu](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Přehled hostitelských položek a hostitelských ovládacích prvků](../vsto/host-items-and-host-controls-overview.md)
- [Automatizace Excelu pomocí rozšířených objektů](../vsto/automating-excel-by-using-extended-objects.md)
- [Ovládací prvek ListObject](../vsto/listobject-control.md)
- [Postupy: Přidání ovládacích prvků ListObject do listů](../vsto/how-to-add-listobject-controls-to-worksheets.md)
- [Postupy: Změna velikosti ovládacích prvků záložek](../vsto/how-to-resize-bookmark-controls.md)
- [Postupy: Změna velikosti ovládacích prvků NamedRange](../vsto/how-to-resize-namedrange-controls.md)
