---
title: 'Postupy: mapování sloupců ListObject na data'
description: Zjistěte, jak můžete namapovat, které sloupce se mají zobrazit v ListObject při volání metody SetDataBinding.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data [Office development in Visual Studio], mapping to ListObject column
- ListObject control, mapping data
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 68cb12503d0f8ad59de92f965c0ed51fbc0d7f40
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/21/2021
ms.locfileid: "107827458"
---
# <a name="how-to-map-listobject-columns-to-data"></a>Postupy: mapování sloupců ListObject na data
  Když svážete <xref:Microsoft.Office.Tools.Excel.ListObject> ovládací prvek s objektem, nebudete <xref:System.Data.DataTable> chtít zobrazit všechny sloupce v seznamu, nebo můžete mít určité sloupce, které nejsou vázány na data. Můžete namapovat, které sloupce se mají zobrazit v <xref:Microsoft.Office.Tools.Excel.ListObject> při volání <xref:Microsoft.Office.Tools.Excel.ListObject.SetDataBinding%2A> metody.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="map-columns"></a>Sloupce mapy

### <a name="to-map-a-data-table-to-columns-in-a-list"></a>Mapování tabulky dat na sloupce v seznamu

1. Vytvořte na <xref:System.Data.DataTable> úrovni třídy.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet3.cs" id="Snippet16":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet3.vb" id="Snippet16":::

2. Přidejte vzorové sloupce a data do `Startup` obslužné rutiny události `Sheet1` třídy (v projektu na úrovni dokumentu) nebo `ThisAddIn` třídy (v projektu doplňku VSTO).

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet3.cs" id="Snippet17":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet3.vb" id="Snippet17":::

3. Zavolejte <xref:Microsoft.Office.Tools.Excel.ListObject.SetDataBinding%2A> metodu a předejte názvy sloupců v pořadí, ve kterém by se měly zobrazit. Objekt list bude vázán na nově vytvořený <xref:System.Data.DataTable> , ale pořadí sloupců v objektu list se bude lišit od pořadí, v němž jsou uvedeny <xref:System.Data.DataTable> .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet3.cs" id="Snippet18":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet3.vb" id="Snippet18":::

## <a name="specify-unmapped-columns"></a>Zadat nemapované sloupce
 Když namapujete sloupce na <xref:System.Data.DataTable> , můžete také určit, že některé sloupce by neměly být vázány na data předáním prázdného řetězce. Nový sloupec, který není vázán na data, je poté přidán do <xref:Microsoft.Office.Tools.Excel.ListObject> ovládacího prvku.

### <a name="to-specify-an-unmapped-column-when-mapping-listobject-columns"></a>Určení nemapovaného sloupce při mapování sloupců ListObject

1. Zavolejte <xref:Microsoft.Office.Tools.Excel.ListObject.SetDataBinding%2A> metodu a předejte názvy sloupců v pořadí, ve kterém by se měly zobrazit. Použijte prázdný řetězec k označení místa přidání nemapovaného sloupce; v tomto případě mezi sloupcem nadpisu a názvem sloupce Příjmení.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet3.cs" id="Snippet19":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet3.vb" id="Snippet19":::

## <a name="compile-the-code"></a>Kompilovat kód
 Tento příklad kódu předpokládá, že máte existující <xref:Microsoft.Office.Tools.Excel.ListObject> pojmenovanou `list1` na listu, ve kterém se zobrazuje tento kód.

## <a name="see-also"></a>Viz také
- [Rozšiřování dokumentů aplikace Word a excelových sešitů v doplňcích VSTO za běhu](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Ovládací prvky v dokumentech Office](../vsto/controls-on-office-documents.md)
- [Přidání ovládacích prvků do dokumentů Office v době běhu](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Postupy: vyplnění ovládacích prvků ListObject daty](../vsto/how-to-fill-listobject-controls-with-data.md)
- [Automatizace Excelu pomocí rozšířených objektů](../vsto/automating-excel-by-using-extended-objects.md)
- [Ovládací prvek ListObject](../vsto/listobject-control.md)
