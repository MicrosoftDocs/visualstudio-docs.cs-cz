---
title: 'Postupy: aktualizace zdroje dat s použitím dat z hostitelského ovládacího prvku'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], data source updates
- data [Office development in Visual Studio], updating a data source from a document
- host controls [Office development in Visual Studio], data source updates
- Office documents [Office development in Visual Studio, data sources
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 3a31bac6b3cbd13fcff8c841c9947e8c14f8984a
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49839762"
---
# <a name="how-to-update-a-data-source-with-data-from-a-host-control"></a>Postupy: aktualizace zdroje dat s použitím dat z hostitelského ovládacího prvku
  Můžete vytvořit vazbu hostitelského ovládacího prvku do zdroje dat a aktualizovat zdroj dat změny provedené u dat v ovládacím prvku. V tomto procesu existují dva hlavní kroky:  
  
1. Aktualizujte zdroj dat v paměti změněných dat v ovládacím prvku. Obvykle je zdroje dat v paměti <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, nebo jiný datový objekt.  
  
2. Aktualizujte databázi s změněná data ve zdroji dat v paměti. To platí jenom v případě, že zdroj dat je připojený k back-end databáze, jako je například databáze systému SQL Server nebo Microsoft Office Access.  
  
   Další informace o hostitelské ovládací prvky a datové vazby, naleznete v tématu [hostovat položky a hostujte Přehled ovládacích prvků](../vsto/host-items-and-host-controls-overview.md) a [vytvoření vazby dat k ovládacím prvkům v řešeních pro systém Office](../vsto/binding-data-to-controls-in-office-solutions.md).  
  
   [!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]  
  
## <a name="update-the-in-memory-data-source"></a>Aktualizace zdroje dat v paměti  
 Ve výchozím nastavení hostitelské ovládací prvky, které umožňují jednoduché datové vazby (jako je například ovládací prvky obsahu na dokumentu aplikace Word nebo pojmenované oblasti ovládacího prvku na listu aplikace Excel) bez uložení změn dat do zdroje dat v paměti. To znamená když koncový uživatel změní hodnotu v ovládacím prvku hostitele a pak přejde mimo ovládací prvek, nová hodnota v ovládacím prvku není automaticky uloženy do zdroje dat.  
  
 Chcete-li uložit data do zdroje dat, můžete napsat kód, který aktualizuje zdroj dat v reakci na konkrétní událost za běhu nebo můžete konfigurovat řízení se automaticky aktualizovat zdroj dat při změně hodnoty v ovládacím prvku.  
  
 Není potřeba uložit <xref:Microsoft.Office.Tools.Excel.ListObject> změny do zdroje dat v paměti. Po vytvoření vazby <xref:Microsoft.Office.Tools.Excel.ListObject> ovládacího prvku k datům, <xref:Microsoft.Office.Tools.Excel.ListObject> ovládací prvek automaticky uloží změny do zdroje dat v paměti bez potřeby dalšího kódu.  
  
### <a name="to-update-the-in-memory-data-source-at-runtime"></a>Chcete-li aktualizovat zdroje dat v paměti za běhu  
  
-   Volání <xref:System.Windows.Forms.Binding.WriteValue%2A> metodu <xref:System.Windows.Forms.Binding> objekt, který váže ovládací prvek na zdroj dat.  
  
     Uloží změny provedené v následujícím příkladu <xref:Microsoft.Office.Tools.Excel.NamedRange> ovládací prvek na listu aplikace Excel do datového zdroje. Tento příklad předpokládá, že máte <xref:Microsoft.Office.Tools.Excel.NamedRange> ovládací prvek s názvem `namedRange1` s jeho <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> vlastnost vázána na pole ve zdroji dat.  
  
     [!code-csharp[Trin_VstcoreDataExcel#1](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#1)]
     [!code-vb[Trin_VstcoreDataExcel#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#1)]  
  
### <a name="automatically-update-the-in-memory-data-source"></a>Automaticky aktualizovat zdroj dat v paměti  
 Ovládací prvek lze také nakonfigurovat tak, aby automaticky aktualizuje zdroj dat v paměti. V úrovni dokumentu projektu můžete to provést pomocí kódu nebo návrháře. V projektu doplňku VSTO je nutné použít kód.  
  
#### <a name="to-set-a-control-to-automatically-update-the-in-memory-data-source-by-using-code"></a>Chcete-li nastavit ovládací prvek se automaticky aktualizovat zdroj dat v paměti pomocí kódu  
  
1. Použít režim System.Windows.Forms.DataSourceUpdateMode.OnPropertyChanged <xref:System.Windows.Forms.Binding> objekt, který váže ovládací prvek na zdroj dat. Existují dvě možnosti pro aktualizaci zdroje dat:  
  
   - Aktualizace zdroje dat, když ovládací prvek je ověřen, nastavte tuto vlastnost na System.Windows.Forms.DataSourceUpdateMode.OnValidation.  
  
   - Pokud chcete aktualizovat zdroj dat při změně hodnoty vlastnosti vázané na data ovládacího prvku, nastavte tuto vlastnost na System.Windows.Forms.DataSourceUpdateMode.OnPropertyChanged.  
  
     > [!NOTE]  
     >  Možnost System.Windows.Forms.DataSourceUpdateMode.OnPropertyChanged se nevztahují na hostitelské ovládací prvky aplikace Word, protože slovo nemá nabídka dokumentů – nebo ovládací prvek – změna oznámení. Tato možnost je však možné pro ovládací prvky Windows Forms v dokumentech aplikace Word.  
  
     Následující příklad nastaví <xref:Microsoft.Office.Tools.Excel.NamedRange> ovládací prvek se automaticky aktualizovat zdroj dat při změně hodnoty v ovládacím prvku. Tento příklad předpokládá, že máte <xref:Microsoft.Office.Tools.Excel.NamedRange> ovládací prvek s názvem `namedRange1` s jeho <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> vlastnost vázána na pole ve zdroji dat.  
  
     [!code-csharp[Trin_VstcoreDataExcel#19](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#19)]
     [!code-vb[Trin_VstcoreDataExcel#19](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#19)]  
  
#### <a name="to-set-a-control-to-automatically-update-the-in-memory-data-source-by-using-the-designer"></a>Chcete-li nastavit ovládací prvek se automaticky aktualizovat zdroj dat v paměti pomocí návrháře  
  
1.  V sadě Visual Studio otevřete Wordový dokument nebo Excelový sešit v návrháři.  
  
2.  Klepněte na ovládací prvek, který chcete automaticky aktualizovat zdroj dat.  
  
3.  V **vlastnosti** okna, rozbalte **(DataBindings)** vlastnost.  
  
4.  Vedle položky **(rozšířené)** vlastnosti, klikněte na tlačítko se třemi tečkami (![VisualStudioEllipsesButton snímek obrazovky](../vsto/media/vbellipsesbutton.png "snímek obrazovky VisualStudioEllipsesButton")).  
  
5.  V **formátování a rozšířené vazby** dialogové okno, klikněte na tlačítko **režim aktualizace zdroje dat** rozevíracího seznamu a vyberte jednu z následujících hodnot:  
  
    -   Chcete-li aktualizovat zdroj dat, když ovládací prvek je ověřen, vyberte **OnValidation**.  
  
    -   Chcete-li aktualizovat zdroj dat při změně hodnoty vlastnosti vázané na data ovládacího prvku, vyberte **OnPropertyChanged –**.  
  
        > [!NOTE]  
        >  **OnPropertyChanged –** možnost se nevztahuje na hostitelské ovládací prvky aplikace Word, protože slovo nemá nabídka dokumentů – nebo ovládací prvek – změna oznámení. Tato možnost je však možné pro ovládací prvky Windows Forms v dokumentech aplikace Word.  
  
6.  Zavřít **formátování a rozšířené vazby** dialogové okno.  
  
## <a name="update-the-database"></a>Aktualizace databáze  
 Pokud zdroj dat v paměti je přidružen k databázi, je nutné aktualizovat databázi se změny do zdroje dat. Další informace o aktualizaci databáze najdete v tématu [uložit data zpět do databáze](../data-tools/save-data-back-to-the-database.md) a [aktualizace dat pomocí TableAdapter](../data-tools/update-data-by-using-a-tableadapter.md) .  
  
### <a name="to-update-the-database"></a>Postup aktualizace databáze  
  
1.  Volání <xref:System.Windows.Forms.BindingSource.EndEdit%2A> metodu <xref:System.Windows.Forms.BindingSource> pro ovládací prvek.  
  
     <xref:System.Windows.Forms.BindingSource> Se automaticky vygeneruje, když přidáte ovládací prvek vázaný na data do dokumentu nebo sešitu v době návrhu. <xref:System.Windows.Forms.BindingSource> Ovládacího prvku se připojí k typové datové sady ve vašem projektu. Další informace najdete v tématu [přehled komponenty BindingSource](/dotnet/framework/winforms/controls/bindingsource-component-overview).  
  
     Následující příklad kódu předpokládá, že váš projekt obsahuje <xref:System.Windows.Forms.BindingSource> s názvem `customersBindingSource`.  
  
     [!code-csharp[Trin_VstcoreDataExcel#20](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#20)]
     [!code-vb[Trin_VstcoreDataExcel#20](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#20)]  
  
2.  Volání `Update` metody generované třídy TableAdapter ve vašem projektu.  
  
     TableAdapter není automaticky vygenerován, když přidáte ovládací prvek vázaný na data do dokumentu nebo sešitu v době návrhu. TableAdapter připojí k databázi typové datové sady ve vašem projektu. Další informace najdete v tématu [TableAdapter – přehled](../data-tools/fill-datasets-by-using-tableadapters.md#tableadapter-overview).  
  
     Následující příklad kódu předpokládá, že máte připojení k tabulku Customers v databázi Northwind a že váš projekt obsahuje TableAdapter s názvem `customersTableAdapter` a typové datové sady s názvem `northwindDataSet`.  
  
     [!code-csharp[Trin_VstcoreDataExcel#21](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#21)]
     [!code-vb[Trin_VstcoreDataExcel#21](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#21)]  
  
## <a name="see-also"></a>Viz také:  
 [Vytvoření vazby dat k ovládacím prvkům v řešeních pro systém Office](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Uložit data zpět do databáze](../data-tools/save-data-back-to-the-database.md)    
 [Aktualizace dat pomocí TableAdapter](../data-tools/update-data-by-using-a-tableadapter.md)    
 [Postupy: procházení databázových záznamů na listu](../vsto/how-to-scroll-through-database-records-in-a-worksheet.md)   
 [Postupy: naplnění listů daty z databáze](../vsto/how-to-populate-worksheets-with-data-from-a-database.md)   
 [Postupy: naplnění dokumentů daty z objektů](../vsto/how-to-populate-documents-with-data-from-objects.md)   
 [Postupy: naplnění dokumentů daty z databáze](../vsto/how-to-populate-documents-with-data-from-a-database.md)   
 [Postupy: naplnění dokumentů daty ze služeb](../vsto/how-to-populate-documents-with-data-from-services.md)  
  
  