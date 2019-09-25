---
title: 'Postupy: Mapování sloupců ListObject na data'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data [Office development in Visual Studio], mapping to ListObject column
- ListObject control, mapping data
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 6e0056687e8ca28af4dbc9032d7bbee0cf976378
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2019
ms.locfileid: "71253674"
---
# <a name="how-to-map-listobject-columns-to-data"></a>Postupy: Mapování sloupců ListObject na data
  Když svážete <xref:Microsoft.Office.Tools.Excel.ListObject> ovládací prvek s objektem <xref:System.Data.DataTable>, nebudete chtít zobrazit všechny sloupce v seznamu, nebo můžete mít určité sloupce, které nejsou vázány na data. Můžete namapovat, které sloupce se mají zobrazit v <xref:Microsoft.Office.Tools.Excel.ListObject> při <xref:Microsoft.Office.Tools.Excel.ListObject.SetDataBinding%2A> volání metody.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 ![odkaz na video](../vsto/media/playvideo.gif "odkaz na video") Související video ukázku najdete v tématu [návody: Vytvořit seznam v aplikaci Excel, který je připojen k seznamu služby SharePoint? ](http://go.microsoft.com/fwlink/?LinkID=130263).

## <a name="map-columns"></a>Sloupce mapy

### <a name="to-map-a-data-table-to-columns-in-a-list"></a>Mapování tabulky dat na sloupce v seznamu

1. <xref:System.Data.DataTable> Vytvořte na úrovni třídy.

     [!code-csharp[Trin_VstcoreHostControlsExcel#16](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet3.cs#16)]
     [!code-vb[Trin_VstcoreHostControlsExcel#16](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet3.vb#16)]

2. Přidejte vzorové sloupce a data do `Startup` obslužné rutiny `Sheet1` události třídy (v projektu na úrovni dokumentu) nebo `ThisAddIn` třídy (v projektu doplňku VSTO).

     [!code-csharp[Trin_VstcoreHostControlsExcel#17](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet3.cs#17)]
     [!code-vb[Trin_VstcoreHostControlsExcel#17](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet3.vb#17)]

3. <xref:Microsoft.Office.Tools.Excel.ListObject.SetDataBinding%2A> Zavolejte metodu a předejte názvy sloupců v pořadí, ve kterém by se měly zobrazit. Objekt list bude vázán na nově vytvořený <xref:System.Data.DataTable>, ale pořadí sloupců v objektu list se bude lišit od pořadí, <xref:System.Data.DataTable>v němž jsou uvedeny.

     [!code-csharp[Trin_VstcoreHostControlsExcel#18](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet3.cs#18)]
     [!code-vb[Trin_VstcoreHostControlsExcel#18](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet3.vb#18)]

## <a name="specify-unmapped-columns"></a>Zadat nemapované sloupce
 Když namapujete sloupce na <xref:System.Data.DataTable>, můžete také určit, že některé sloupce by neměly být vázány na data předáním prázdného řetězce. Nový sloupec, který není vázán na data, je poté přidán do <xref:Microsoft.Office.Tools.Excel.ListObject> ovládacího prvku.

### <a name="to-specify-an-unmapped-column-when-mapping-listobject-columns"></a>Určení nemapovaného sloupce při mapování sloupců ListObject

1. <xref:Microsoft.Office.Tools.Excel.ListObject.SetDataBinding%2A> Zavolejte metodu a předejte názvy sloupců v pořadí, ve kterém by se měly zobrazit. Použijte prázdný řetězec k označení místa přidání nemapovaného sloupce; v tomto případě mezi sloupcem nadpisu a názvem sloupce Příjmení.

     [!code-csharp[Trin_VstcoreHostControlsExcel#19](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet3.cs#19)]
     [!code-vb[Trin_VstcoreHostControlsExcel#19](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet3.vb#19)]

## <a name="compile-the-code"></a>Kompilace kódu
 Tento příklad kódu předpokládá, že máte existující <xref:Microsoft.Office.Tools.Excel.ListObject> pojmenovanou `list1` na listu, ve kterém se zobrazuje tento kód.

## <a name="see-also"></a>Viz také:
- [Rozšiřování dokumentů aplikace Word a excelových sešitů v doplňcích VSTO za běhu](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Ovládací prvky v dokumentech Office](../vsto/controls-on-office-documents.md)
- [Přidání ovládacích prvků do dokumentů Office v době běhu](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Postupy: Vyplnit ovládací prvky ListObject daty](../vsto/how-to-fill-listobject-controls-with-data.md)
- [Automatizace aplikace Excel s použitím rozšířených objektů](../vsto/automating-excel-by-using-extended-objects.md)
- [Ovládací prvek ListObject](../vsto/listobject-control.md)
