---
title: 'Postupy: vyplnění ListObject ovládací prvky s daty'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: e9e255d4099a90173b9dbc7ff6fd7b2225d0622d
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/11/2018
ms.locfileid: "35255701"
---
# <a name="how-to-fill-listobject-controls-with-data"></a>Postupy: vyplnění ListObject ovládací prvky s daty
  Datová vazba můžete použít jako způsob, jak rychle přidat data do dokumentu. Po vazbě dat na objekt seznamu, můžete odpojit seznam objektů, zobrazí data, ale se už neváže ke zdroji dat.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 ![odkaz na video](../vsto/media/playvideo.gif "odkaz na video") související Videoukázka, najdete v části [jak I: vytvořit seznam v aplikaci Excel, která je připojena k seznamu služby SharePoint?](http://go.microsoft.com/fwlink/?LinkID=130263).  
  
### <a name="to-bind-data-to-a-listobject-control"></a>K vytvoření vazby dat k ovládacímu prvku ListObject  
  
1.  Vytvoření <xref:System.Data.DataTable> na úrovni třídy.  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#20](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet4.cs#20)]
     [!code-vb[Trin_VstcoreHostControlsExcel#20](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet4.vb#20)]  
  
2.  Přidání sloupců ukázka a dat v `Startup` obslužnou rutinu události `Sheet1` – třída (v projektech na úrovni dokumentu) nebo `ThisAddIn` – třída (v projektu na úrovni aplikace).  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#21](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet4.cs#21)]
     [!code-vb[Trin_VstcoreHostControlsExcel#21](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet4.vb#21)]  
  
3.  Volání <xref:Microsoft.Office.Tools.Excel.ListObject.SetDataBinding%2A> metoda a předejte jí názvy sloupců v pořadí, v jakém se mají zobrazit. Pořadí sloupců v seznamu objektu se může lišit od pořadí, ve kterém se zobrazí <xref:System.Data.DataTable>.  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#22](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet4.cs#22)]
     [!code-vb[Trin_VstcoreHostControlsExcel#22](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet4.vb#22)]  
  
### <a name="to-disconnect-the-listobject-control-from-the-data-source"></a>Chcete-li odpojit ovládacího prvku ListObject ze zdroje dat.  
  
1.  Volání <xref:Microsoft.Office.Tools.Excel.ListObject.Disconnect%2A> metodu `List1`.  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#23](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet4.cs#23)]
     [!code-vb[Trin_VstcoreHostControlsExcel#23](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet4.vb#23)]  
  
## <a name="compile-the-code"></a>Kompilace kódu  
 Tento příklad kódu předpokládá, že už máte existující <xref:Microsoft.Office.Tools.Excel.ListObject> s názvem `list1` na listu, ve kterém se zobrazí tento kód.  
  
## <a name="see-also"></a>Viz také:  
 [Rozšíření dokumentů aplikace Word a sešitů aplikace Excel v doplňcích VSTO za běhu](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Ovládací prvky v dokumentech Office](../vsto/controls-on-office-documents.md)   
 [Přidání ovládacích prvků do dokumentů Office za běhu](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Postupy: sloupců objektu ListObject mapy k datům](../vsto/how-to-map-listobject-columns-to-data.md)   
 [Automatizace aplikace Excel s použitím rozšířených objektů](../vsto/automating-excel-by-using-extended-objects.md)   
 [ListObject – ovládací prvek](../vsto/listobject-control.md)   
 [Vázání dat k ovládacím prvkům v řešeních pro systém Office](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Postupy: naplnění listů daty z databáze](../vsto/how-to-populate-worksheets-with-data-from-a-database.md)   
 [Postupy: naplnění dokumentů daty ze služeb](../vsto/how-to-populate-documents-with-data-from-services.md)  
  
  