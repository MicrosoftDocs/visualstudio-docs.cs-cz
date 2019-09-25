---
title: 'Postupy: Vyplnit ovládací prvky ListObject daty'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- disconnecting from data sources
- ListObject control, disconnecting from a data source
- ListObject control, filling with data
- data [Office development in Visual Studio], adding to worksheets
- data binding, ListObject controls
- worksheets, populating with data
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: a0916ca11d4df5f6b69376d7223143afbb407f6e
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2019
ms.locfileid: "71255881"
---
# <a name="how-to-fill-listobject-controls-with-data"></a>Postupy: Vyplnit ovládací prvky ListObject daty
  Datovou vazbu můžete použít jako způsob, jak rychle přidat data do dokumentu. Po vytvoření vazby dat k objektu seznamu můžete odpojit objekt seznamu, aby zobrazil data, ale již není svázán se zdrojem dat.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 ![odkaz na video](../vsto/media/playvideo.gif "odkaz na video") Související video ukázku najdete v tématu [návody: Vytvořit seznam v aplikaci Excel, který je připojen k seznamu služby SharePoint? ](http://go.microsoft.com/fwlink/?LinkID=130263).

### <a name="to-bind-data-to-a-listobject-control"></a>Vytvoření vazby dat k ovládacímu prvku ListObject

1. <xref:System.Data.DataTable> Vytvořte na úrovni třídy.

     [!code-csharp[Trin_VstcoreHostControlsExcel#20](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet4.cs#20)]
     [!code-vb[Trin_VstcoreHostControlsExcel#20](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet4.vb#20)]

2. Přidejte vzorové sloupce a data do `Startup` obslužné rutiny `Sheet1` události třídy (v projektu na úrovni dokumentu) nebo `ThisAddIn` třídy (v projektu na úrovni aplikace).

     [!code-csharp[Trin_VstcoreHostControlsExcel#21](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet4.cs#21)]
     [!code-vb[Trin_VstcoreHostControlsExcel#21](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet4.vb#21)]

3. <xref:Microsoft.Office.Tools.Excel.ListObject.SetDataBinding%2A> Zavolejte metodu a předejte názvy sloupců v pořadí, ve kterém by se měly zobrazit. Pořadí sloupců v objektu list se může lišit od pořadí, ve kterém se nacházejí v <xref:System.Data.DataTable>.

     [!code-csharp[Trin_VstcoreHostControlsExcel#22](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet4.cs#22)]
     [!code-vb[Trin_VstcoreHostControlsExcel#22](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet4.vb#22)]

### <a name="to-disconnect-the-listobject-control-from-the-data-source"></a>Odpojení ovládacího prvku ListObject ze zdroje dat

1. <xref:Microsoft.Office.Tools.Excel.ListObject.Disconnect%2A> Zavolejte`List1`metodu.

     [!code-csharp[Trin_VstcoreHostControlsExcel#23](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet4.cs#23)]
     [!code-vb[Trin_VstcoreHostControlsExcel#23](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet4.vb#23)]

## <a name="compile-the-code"></a>Kompilace kódu
 Tento příklad kódu předpokládá, že máte existující <xref:Microsoft.Office.Tools.Excel.ListObject> pojmenovanou `list1` na listu, ve kterém se zobrazuje tento kód.

## <a name="see-also"></a>Viz také:
- [Rozšiřování dokumentů aplikace Word a excelových sešitů v doplňcích VSTO za běhu](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Ovládací prvky v dokumentech Office](../vsto/controls-on-office-documents.md)
- [Přidání ovládacích prvků do dokumentů Office v době běhu](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Postupy: Mapování sloupců ListObject na data](../vsto/how-to-map-listobject-columns-to-data.md)
- [Automatizace aplikace Excel s použitím rozšířených objektů](../vsto/automating-excel-by-using-extended-objects.md)
- [Ovládací prvek ListObject](../vsto/listobject-control.md)
- [Vázání dat k ovládacím prvkům v řešeních pro systém Office](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Postupy: Naplnění listů daty z databáze](../vsto/how-to-populate-worksheets-with-data-from-a-database.md)
- [Postupy: Naplnění dokumentů daty ze služeb](../vsto/how-to-populate-documents-with-data-from-services.md)
