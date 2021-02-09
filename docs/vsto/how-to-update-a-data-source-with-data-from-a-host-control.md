---
title: 'Postupy: aktualizace zdroje dat s použitím dat z hostitelského ovládacího prvku'
description: Naučte se, jak můžete navázat hostitelský ovládací prvek ke zdroji dat a aktualizovat zdroj dat změnami provedenými v datech v ovládacím prvku.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], data source updates
- data [Office development in Visual Studio], updating a data source from a document
- host controls [Office development in Visual Studio], data source updates
- Office documents [Office development in Visual Studio, data sources
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 4df11976832359363c639a49dd767e7e87b41a26
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99894436"
---
# <a name="how-to-update-a-data-source-with-data-from-a-host-control"></a>Postupy: aktualizace zdroje dat s použitím dat z hostitelského ovládacího prvku
  Můžete navázat hostitelský ovládací prvek ke zdroji dat a aktualizovat zdroj dat změnami provedenými v datech v ovládacím prvku. V tomto procesu jsou dva hlavní kroky:

1. Aktualizuje zdroj dat v paměti změněnými daty v ovládacím prvku. Zdrojem dat v paměti je obvykle, <xref:System.Data.DataSet> <xref:System.Data.DataTable> nebo nějaký jiný datový objekt.

2. Aktualizuje databázi se změněnými daty ve zdroji dat v paměti. To platí pouze v případě, že je zdroj dat připojen k back-endové databázi, jako je například SQL Server nebo databáze systém Microsoft Office Access.

   Další informace o ovládacích prvcích hostování a datových vazbách naleznete v tématu Přehled hostitelských [položek a hostitelských ovládacích prvků](../vsto/host-items-and-host-controls-overview.md) a [vázání dat k ovládacím prvkům v řešeních pro systém Office](../vsto/binding-data-to-controls-in-office-solutions.md).

   [!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]

## <a name="update-the-in-memory-data-source"></a>Aktualizace zdroje dat v paměti
 Ve výchozím nastavení hostitelské ovládací prvky, které umožňují jednoduchou datovou vazbu (například ovládací prvky obsahu v dokumentu aplikace Word nebo pojmenovaném ovládacím prvku rozsahu na listu aplikace Excel), neukládají změny dat do zdroje dat v paměti. To znamená, že když koncový uživatel změní hodnotu v hostitelském ovládacím prvku a přejde pryč z ovládacího prvku, nová hodnota v ovládacím prvku se automaticky neuloží do zdroje dat.

 Chcete-li uložit data do zdroje dat, můžete napsat kód, který aktualizuje zdroj dat v reakci na konkrétní událost v době běhu, nebo můžete nakonfigurovat ovládací prvek tak, aby automaticky aktualizoval zdroj dat, když se změní hodnota v ovládacím prvku.

 Nemusíte ukládat <xref:Microsoft.Office.Tools.Excel.ListObject> změny do zdroje dat v paměti. Při navázání <xref:Microsoft.Office.Tools.Excel.ListObject> ovládacího prvku s daty <xref:Microsoft.Office.Tools.Excel.ListObject> ovládací prvek automaticky ukládá změny do zdroje dat v paměti bez nutnosti dalšího kódu.

### <a name="to-update-the-in-memory-data-source-at-run-time"></a>Aktualizace zdroje dat v paměti za běhu

- Zavolejte <xref:System.Windows.Forms.Binding.WriteValue%2A> metodu <xref:System.Windows.Forms.Binding> objektu, který sváže ovládací prvek se zdrojem dat.

     Následující příklad uloží změny provedené <xref:Microsoft.Office.Tools.Excel.NamedRange> v ovládacím prvku listu aplikace Excel do zdroje dat. V tomto příkladu se předpokládá, že máte <xref:Microsoft.Office.Tools.Excel.NamedRange> ovládací prvek s názvem `namedRange1` s <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> vlastností vázaný na pole ve zdroji dat.

     [!code-csharp[Trin_VstcoreDataExcel#1](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#1)]
     [!code-vb[Trin_VstcoreDataExcel#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#1)]

### <a name="automatically-update-the-in-memory-data-source"></a>Automatické aktualizace zdroje dat v paměti
 Můžete také nakonfigurovat ovládací prvek tak, aby automaticky aktualizován zdroj dat v paměti. V projektu na úrovni dokumentu můžete to provést pomocí kódu nebo návrháře. V projektu doplňku VSTO je nutné použít kód.

#### <a name="to-set-a-control-to-automatically-update-the-in-memory-data-source-by-using-code"></a>Nastavení ovládacího prvku na automatickou aktualizaci zdroje dat v paměti pomocí kódu

1. Použijte režim System. Windows. Forms. DataSourceUpdateMode. propropertychanged <xref:System.Windows.Forms.Binding> objektu, který sváže ovládací prvek se zdrojem dat. Existují dvě možnosti aktualizace zdroje dat:

   - Chcete-li aktualizovat zdroj dat při ověřování ovládacího prvku, nastavte tuto vlastnost na System. Windows. Forms. DataSourceUpdateMode. provaliding.

   - Chcete-li aktualizovat zdroj dat, když se změní hodnota vlastnosti vázané na data ovládacího prvku, nastavte tuto vlastnost na System. Windows. Forms. DataSourceUpdateMode.. PropertyChanged.

     > [!NOTE]
     > Možnost System. Windows. Forms. DataSourceUpdateMode. PropertyChanged se nevztahuje na ovládací prvky hostitele aplikace Word, protože aplikace Word nenabízí oznámení změny dokumentu nebo řízení-změna. Tuto možnost lze však použít pro model Windows Forms ovládací prvky v dokumentech aplikace Word.

     Následující příklad konfiguruje <xref:Microsoft.Office.Tools.Excel.NamedRange> ovládací prvek tak, aby automaticky aktualizoval zdroj dat, když se změní hodnota v ovládacím prvku. V tomto příkladu se předpokládá, že máte <xref:Microsoft.Office.Tools.Excel.NamedRange> ovládací prvek s názvem `namedRange1` s <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> vlastností vázaný na pole ve zdroji dat.

     [!code-csharp[Trin_VstcoreDataExcel#19](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#19)]
     [!code-vb[Trin_VstcoreDataExcel#19](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#19)]

#### <a name="to-set-a-control-to-automatically-update-the-in-memory-data-source-by-using-the-designer"></a>Nastavení ovládacího prvku na automatickou aktualizaci zdroje dat v paměti pomocí návrháře

1. V aplikaci Visual Studio otevřete dokument aplikace Word nebo excelový sešit v návrháři.

2. Klikněte na ovládací prvek, u kterého chcete zdroj dat automaticky aktualizovat.

3. V okně **vlastnosti** rozbalte vlastnost **(DataBindings)** .

4. Vedle vlastnosti **(rozšířené)** klikněte na tlačítko se třemi tečkami (![VisualStudioEllipsesButton snímek obrazovky](../vsto/media/vbellipsesbutton.png "Snímek obrazovky VisualStudioEllipsesButton")).

5. V dialogovém okně **formátování a rozšířené vazby** klikněte na rozevírací seznam **režim aktualizace zdroje dat** a vyberte jednu z následujících hodnot:

    - Chcete-li aktualizovat zdroj dat, když je ovládací prvek ověřen, vyberte možnost **ověření**.

    - Chcete-li aktualizovat zdroj dat, když se změní hodnota vlastnosti vázané na data ovládacího prvku, vyberte možnost- **propertyChanged**.

        > [!NOTE]
        > Možnost- **propertyChanged** se nevztahuje na hostitelské ovládací prvky aplikace Word, protože aplikace Word nenabízí oznámení změny dokumentu nebo řízení. Tuto možnost lze však použít pro model Windows Forms ovládací prvky v dokumentech aplikace Word.

6. Zavřete dialogové okno **formátování a rozšířené vazby** .

## <a name="update-the-database"></a>Aktualizace databáze
 Pokud je zdroj dat v paměti přidružený k databázi, je nutné aktualizovat databázi se změnami ve zdroji dat. Další informace o aktualizaci databáze naleznete v tématu [uložení dat zpět do databáze](../data-tools/save-data-back-to-the-database.md)  a [aktualizace dat pomocí TableAdapter](../data-tools/update-data-by-using-a-tableadapter.md) .

### <a name="to-update-the-database"></a>Postup aktualizace databáze

1. Zavolejte <xref:System.Windows.Forms.BindingSource.EndEdit%2A> metodu <xref:System.Windows.Forms.BindingSource> pro ovládací prvek.

     <xref:System.Windows.Forms.BindingSource>Automaticky se generuje při přidání ovládacího prvku vázaného na data do dokumentu nebo sešitu v době návrhu. <xref:System.Windows.Forms.BindingSource>Připojí ovládací prvek k typované datové sadě ve vašem projektu. Další informace najdete v tématu [Přehled komponent BindingSource](/dotnet/framework/winforms/controls/bindingsource-component-overview).

     Následující příklad kódu předpokládá, že projekt obsahuje <xref:System.Windows.Forms.BindingSource> pojmenovaný `customersBindingSource` .

     [!code-csharp[Trin_VstcoreDataExcel#20](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#20)]
     [!code-vb[Trin_VstcoreDataExcel#20](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#20)]

2. Volejte `Update` metodu generovaného TableAdapter ve vašem projektu.

     TableAdapter se automaticky vygeneruje při přidání ovládacího prvku vázaného na data do dokumentu nebo sešitu v době návrhu. TableAdapter spojuje typovou datovou sadu v projektu s databází. Další informace najdete v tématu [TableAdapter Overview](../data-tools/fill-datasets-by-using-tableadapters.md#tableadapter-overview).

     Následující příklad kódu předpokládá, že máte připojení k tabulce Customers v databázi Northwind a že projekt obsahuje TableAdapter s názvem `customersTableAdapter` a zadanou datovou sadu s názvem `northwindDataSet` .

     [!code-csharp[Trin_VstcoreDataExcel#21](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#21)]
     [!code-vb[Trin_VstcoreDataExcel#21](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#21)]

## <a name="see-also"></a>Viz také
- [Vázání dat k ovládacím prvkům v řešeních pro systém Office](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Ukládání dat zpět do databáze](../data-tools/save-data-back-to-the-database.md)
- [Aktualizace dat pomocí objektu TableAdapter](../data-tools/update-data-by-using-a-tableadapter.md)
- [Postupy: procházení databázových záznamů na listu](../vsto/how-to-scroll-through-database-records-in-a-worksheet.md)
- [Postupy: naplnění listů daty z databáze](../vsto/how-to-populate-worksheets-with-data-from-a-database.md)
- [Postupy: Naplnění dokumentů daty z objektů](../vsto/how-to-populate-documents-with-data-from-objects.md)
- [Postupy: Naplnění dokumentů daty z databáze](../vsto/how-to-populate-documents-with-data-from-a-database.md)
- [Postupy: Naplnění dokumentů daty ze služeb](../vsto/how-to-populate-documents-with-data-from-services.md)
