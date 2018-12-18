---
title: 'Postupy: sloupců objektu ListObject Mapa k datům'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data [Office development in Visual Studio], mapping to ListObject column
- ListObject control, mapping data
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: b77d33b8d30ed7f581e27e1cbe07d0c90715ff04
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "35676446"
---
# <a name="how-to-map-listobject-columns-to-data"></a>Postupy: sloupců objektu ListObject Mapa k datům
  Po vytvoření vazby <xref:Microsoft.Office.Tools.Excel.ListObject> mít pod kontrolou <xref:System.Data.DataTable>, možná nebudete chtít zobrazit všechny sloupce v seznamu, nebo může být některé sloupce, které nejsou vázány na data. Můžete namapovat sloupce, které chcete zobrazit v <xref:Microsoft.Office.Tools.Excel.ListObject> při volání <xref:Microsoft.Office.Tools.Excel.ListObject.SetDataBinding%2A> metody.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 ![odkaz na video](../vsto/media/playvideo.gif "odkaz na video") související video ukázku naleznete v tématu [jak mohu: vytvořit seznam v aplikaci Excel, který je připojený k serveru SharePoint?](http://go.microsoft.com/fwlink/?LinkID=130263).  
  
## <a name="map-columns"></a>Mapování sloupce  
  
### <a name="to-map-a-data-table-to-columns-in-a-list"></a>K mapování tabulky dat na sloupce v seznamu  
  
1.  Vytvořte <xref:System.Data.DataTable> na úrovni třídy.  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#16](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet3.cs#16)]
     [!code-vb[Trin_VstcoreHostControlsExcel#16](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet3.vb#16)]  
  
2.  Přidejte příklad sloupců a data v `Startup` obslužná rutina události `Sheet1` třídy (v projektu úrovni dokumentu) nebo `ThisAddIn` třídy (v projektu doplňku VSTO).  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#17](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet3.cs#17)]
     [!code-vb[Trin_VstcoreHostControlsExcel#17](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet3.vb#17)]  
  
3.  Volání <xref:Microsoft.Office.Tools.Excel.ListObject.SetDataBinding%2A> a předáte do názvů sloupce v pořadí, by měla objevit. Objekt seznamu bude vázán na nově vytvořený <xref:System.Data.DataTable>, ale pořadí sloupců v objektu seznamu se bude lišit od pořadí, jsou uvedeny v <xref:System.Data.DataTable>.  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#18](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet3.cs#18)]
     [!code-vb[Trin_VstcoreHostControlsExcel#18](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet3.vb#18)]  
  
## <a name="specify-unmapped-columns"></a>Zadejte nenamapované sloupce  
 Při mapování sloupců <xref:System.Data.DataTable>, můžete také určit, že některé sloupce by neměla být vázána na data předávání prázdný řetězec. Nový sloupec, který není vázán na data se pak přidá do <xref:Microsoft.Office.Tools.Excel.ListObject> ovládacího prvku.  
  
### <a name="to-specify-an-unmapped-column-when-mapping-listobject-columns"></a>Chcete-li určit Nemapovaný sloupec při mapování sloupců objektu ListObject  
  
1.  Volání <xref:Microsoft.Office.Tools.Excel.ListObject.SetDataBinding%2A> a předáte do názvů sloupce v pořadí, by měla objevit. Označuje, kde je přidat Nemapovaný sloupec; použijte prázdný řetězec v tomto případě mezi sloupci title a poslední sloupec názvu.  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#19](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet3.cs#19)]
     [!code-vb[Trin_VstcoreHostControlsExcel#19](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet3.vb#19)]  
  
## <a name="compile-the-code"></a>Kompilace kódu  
 Tento příklad kódu předpokládá, že už máte existující <xref:Microsoft.Office.Tools.Excel.ListObject> s názvem `list1` na listu, ve kterém se zobrazí tento kód.  
  
## <a name="see-also"></a>Viz také:  
 [Rozšíření dokumentů aplikace Word a sešitů aplikace Excel v doplňcích VSTO za běhu](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Ovládací prvky v dokumentech Office](../vsto/controls-on-office-documents.md)   
 [Přidání ovládacích prvků do dokumentů Office za běhu](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Postupy: výplň ListObject – ovládací prvky s daty](../vsto/how-to-fill-listobject-controls-with-data.md)   
 [Automatizace aplikace Excel s použitím rozšířených objektů](../vsto/automating-excel-by-using-extended-objects.md)   
 [ListObject – ovládací prvek](../vsto/listobject-control.md)  
  
  