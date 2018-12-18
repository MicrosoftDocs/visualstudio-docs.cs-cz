---
title: Vytvoření vazby dat k ovládacím prvkům v řešeních pro systém Office
ms.custom: ''
ms.date: 02/02/2017
ms.technology: office-development
ms.prod: visual-studio-dev15
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office documents [Office development in Visual Studio], connecting to data
- data, data binding
- data binding
- data binding, Office solutions
- data binding, controls
- Office applications [Office development in Visual Studio], data binding
- controls, data binding
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: 5b5d7a52e4f8b9e6c9741d3b62bc18b2d4cb66f7
ms.sourcegitcommit: 20c0991d737c540750c613c380cd4cf5bb07de51
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/11/2018
ms.locfileid: "53248017"
---
# <a name="bind-data-to-controls-in-office-solutions"></a>Vytvoření vazby dat k ovládacím prvkům v řešeních pro systém Office
  Můžete svázat ovládací prvky Windows Forms a *hostování ovládacích prvků* na dokumentu aplikace Microsoft Office Word nebo list aplikace Microsoft Office Excel ke zdroji dat, ovládací prvky automaticky zobrazovat data. Vytvoření vazby dat k ovládacím prvkům v projektech na úrovni aplikace i na úrovni dokumentu.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 Hostitelské ovládací prvky rozšíření objekty, které jsou v aplikaci Word a Excel objektové modely, jako je například ovládací prvky obsahu v aplikaci Word a pojmenované oblasti v aplikaci Excel. Další informace najdete v tématu [hostovat položky a hostujte Přehled ovládacích prvků](../vsto/host-items-and-host-controls-overview.md).  
  
 Windows Forms a hostitelských ovládacích prvků pomocí vazby modelu Windows Forms dat, který podporuje obě *jednoduchou datovou vazbu* a *rozšířené datové vazby* ke zdrojům dat, jako jsou datové sady a data tabulky. Podrobnější informace o modelu vazby dat ve Windows Forms, naleznete v tématu [svázat Data a Windows Forms](/dotnet/framework/winforms/data-binding-and-windows-forms).  
  
 ![odkaz na video](../vsto/media/playvideo.gif "odkaz na video") související video ukázku naleznete v tématu [postup: Využití dat z databáze v aplikaci Excel? ](http://go.microsoft.com/fwlink/?LinkID=130287).  
  
## <a name="simple-data-binding"></a>Jednoduchá vazba dat  
 Jednoduchá vazba dat existuje, když vlastnosti ovládacího prvku je vázán na jeden datový prvek, jako jsou hodnoty v tabulce dat. Například <xref:Microsoft.Office.Tools.Excel.NamedRange> má ovládací prvek <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> vlastnost, která může být vázaný na pole v datové sadě. Při změně pole v datové sadě, změní se také hodnotu v pojmenovaném rozsahu. Hostování všech ovládacích prvků, s výjimkou <xref:Microsoft.Office.Tools.Word.XMLNodes> řídit, podporovat jednoduchou datovou vazbu. <xref:Microsoft.Office.Tools.Word.XMLNodes> Ovládací prvek je kolekce, a proto nepodporuje vytváření datových vazeb.  
  
 Chcete-li provést jednoduché datové vazby k hostitelského ovládacího prvku, přidejte <xref:System.Windows.Forms.Binding> k `DataBindings` vlastnost ovládacího prvku. A <xref:System.Windows.Forms.Binding> objekt představuje jednoduché vazby mezi hodnotou vlastnosti ovládacího prvku a hodnotou datový prvek.  
  
 Následující příklad ukazuje, jak vytvořit vazbu <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> vlastnost na datový prvek v projektu úrovni dokumentu.  
  
 [!code-vb[Trin_BindableComponent#4](../vsto/codesnippet/VisualBasic/Trin_BindableComponent/Sheet1.vb#4)]
 [!code-csharp[Trin_BindableComponent#4](../vsto/codesnippet/CSharp/Trin_BindableComponent/Sheet1.cs#4)]  
  
 Návody, které ukazuje, jednoduché datové vazby, naleznete v tématu [názorný postup: Jednoduché datové vazby v projektech na úrovni dokumentu](../vsto/walkthrough-simple-data-binding-in-a-document-level-project.md) pro projekt úrovni dokumentu a [názorný postup: Jednoduché datové vazby v projektu doplňku VSTO](../vsto/walkthrough-simple-data-binding-in-vsto-add-in-project.md) projektu doplňku VSTO.  
  
## <a name="complex-data-binding"></a>Rozšířené datové vazby  
 Rozšířené datové vazby existuje, když vlastnosti ovládacího prvku je vázán na více než jeden prvek dat, jako je například více sloupců v datové tabulce. <xref:Microsoft.Office.Tools.Excel.ListObject> Ovládací prvek pro Excel je pouze hostitelského ovládacího prvku, který podporuje komplexní datovou vazbu. Existují také mnoho ovládacích prvků Windows Forms, které podporují rozšířené datové vazby, jako je například <xref:System.Windows.Forms.DataGridView> ovládacího prvku.  
  
 Chcete-li provést rozšířené datové vazby, nastavte `DataSource` vlastnost ovládacího prvku na objekt zdroje dat, který podporuje rozšířené datové vazby. Například <xref:Microsoft.Office.Tools.Excel.ListObject.DataSource%2A> vlastnost <xref:Microsoft.Office.Tools.Excel.ListObject> ovládacího prvku mohou být vázány na více sloupců v datové tabulce. Všechna data v datové tabulce se zobrazí v <xref:Microsoft.Office.Tools.Excel.ListObject> ovládacího prvku a jako data v tabulce změny dat, <xref:Microsoft.Office.Tools.Excel.ListObject> také změní. Seznam zdrojů dat, které můžete použít pro rozšířené datové vazby najdete v tématu [zdroje dat podporované rozhraním Windows Forms](/dotnet/framework/winforms/data-sources-supported-by-windows-forms).  
  
 Následující příklad kódu vytvoří <xref:System.Data.DataSet> se dvěma <xref:System.Data.DataTable> objekty a naplní jednu z tabulek s daty. Kód poté vytvoří vazbu <xref:Microsoft.Office.Tools.Excel.ListObject> do tabulky, který obsahuje data. Tento příklad je určený pro úrovni dokumentu projektu aplikace Excel.  
  
 [!code-csharp[Trin_ExcelListObject#18](../vsto/codesnippet/CSharp/Trin_ExcelListObject/Trin_ExcelListObject.cs#18)]
 [!code-vb[Trin_ExcelListObject#18](../vsto/codesnippet/VisualBasic/Trin_ExcelListObject/Sheet1.vb#18)]  
  
 Postupy, které popisují rozšířené datové vazby, naleznete v tématu [názorný postup: Rozšířené datové vazby v projektech na úrovni dokumentu](../vsto/walkthrough-complex-data-binding-in-a-document-level-project.md) pro projekt úrovni dokumentu a [názorný postup: Rozšířené datové vazby v projektu doplňku VSTO](../vsto/walkthrough-complex-data-binding-in-vsto-add-in-project.md) projektu doplňku VSTO.  
  
## <a name="display-data-in-documents-and-workbooks"></a>Zobrazení dat v dokumentech a sešity  
 V projektech na úrovni dokumentu, můžete použít **zdroje dat** okno a snadno přidat ovládací prvky vázané na data do dokumentů nebo sešitů, stejně jako použijte pro model Windows Forms. Další informace o používání **zdroje dat** okna, naleznete v tématu [ovládací prvky vazby Windows Forms k datům v sadě Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md) a [přidat nové zdroje dat](../data-tools/add-new-data-sources.md).  
  
### <a name="drag-controls-from-the-data-sources-window"></a>Přetáhněte ovládací prvky z okna zdroje dat  
 Vytvoření ovládacího prvku na dokument při přetažení objektu na jeho z **zdroje dat** okna. Typ ovládacího prvku, který je vytvořen závisí na tom, jestli jsou vazby jeden sloupec dat nebo více sloupců dat.  
  
 V aplikaci Excel <xref:Microsoft.Office.Tools.Excel.NamedRange> ovládací prvek je vytvořen v listu pro jednotlivá pole jednotlivých a <xref:Microsoft.Office.Tools.Excel.ListObject> ovládací prvek je vytvořen pro každou oblast dat, která zahrnuje více řádků a sloupců. Můžete změnit toto výchozí nastavení tak, že vyberete v tabulce nebo pole **zdroje dat** okno a následným výběrem jiného ovládacího prvku z rozevíracího seznamu.  
  
 A <xref:Microsoft.Office.Tools.Word.ContentControl> ovládací prvek je přidán do dokumentů. Typ obsahu ovládacího prvku závisí na typu dat pole, které jste vybrali.  
  
### <a name="bind-data-in-document-level-projects-at-design-time"></a>Vytvoření vazby dat v projektech na úrovni dokumentu v době návrhu  
 Následující témata ukazují příklady vazba dat v době návrhu:  
  
-   [Postupy: Naplnění listů daty z databáze](../vsto/how-to-populate-worksheets-with-data-from-a-database.md)  
  
-   [Postupy: Naplnění dokumentů daty z databáze](../vsto/how-to-populate-documents-with-data-from-a-database.md)  
  
-   [Postupy: Naplnění dokumentů daty z objektů](../vsto/how-to-populate-documents-with-data-from-objects.md)  
  
-   [Postupy: Naplnění dokumentů daty ze služeb](../vsto/how-to-populate-documents-with-data-from-services.md)  
  
-   [Postupy: Procházení databázových záznamů na listu](../vsto/how-to-scroll-through-database-records-in-a-worksheet.md)  
  
### <a name="bind-data-in-vsto-add-in-projects"></a>Vytvoření vazby dat v projekty doplňků VSTO  
 V doplňku VSTO projektů můžete přidat ovládací prvky pouze za běhu. Následující témata ukazují příklady vazba dat za běhu:  
  
-   [Návod: Jednoduché datové vazby v projektu doplňku VSTO](../vsto/walkthrough-simple-data-binding-in-vsto-add-in-project.md)  
  
-   [Návod: Rozšířené datové vazby v projektu doplňku VSTO](../vsto/walkthrough-complex-data-binding-in-vsto-add-in-project.md)  
  
## <a name="update-data-that-is-bound-to-host-controls"></a>Aktualizovat data, která je vázána k hostitelské ovládací prvky  
 Vytváření datových vazeb mezi zdroji dat a hostitelského ovládacího prvku zahrnuje aktualizace obousměrný data. V jednoduché datové vazby, změny ve zdroji dat se automaticky projeví v hostitelského ovládacího prvku, ale explicitní volání konstruktoru se aktualizovat zdroj dat vyžadovat změny v hostitelského ovládacího prvku. Důvodem je, že v některých případech se změny v jednom poli vázané na data nepřijmou Pokud jsou doplněny změny v jiném poli vázané na data. Například může mít dvě pole, jeden pro stáří a jeden pro let zkušeností. Prostředí může mít maximálně věku. Uživatele nejde aktualizovat starší z 50 až 25 a pak prostředí od 30 do 10 Pokud uživatel provede změny ve stejnou dobu. Pokud chcete tento problém vyřešit, nebudou aktualizovány pole s jednoduchou datovou vazbu, dokud explicitně odesílá aktualizace kódu.  
  
 Aktualizace zdroje dat z hostitelské ovládací prvky, které umožňují jednoduché datové vazby, musíte odeslání aktualizací do zdroje dat v paměti (například <xref:System.Data.DataSet> nebo <xref:System.Data.DataTable>) a back-end databáze, pokud vaše řešení používá jeden.  
  
 Není potřeba explicitně aktualizovat zdroj dat v paměti, když provádíte pomocí rozšířené datové vazby <xref:Microsoft.Office.Tools.Excel.ListObject> ovládacího prvku. V takovém případě změny jsou automaticky odeslány do zdroje dat v paměti bez dalšího kódu.  
  
 Další informace najdete v tématu [jak: Aktualizace zdroje dat s použitím dat z hostitelského ovládacího prvku](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md).  
  
## <a name="see-also"></a>Viz také:  
 [Postup: Využití dat z databáze v aplikaci Excel?](http://go.microsoft.com/fwlink/?LinkID=130287)   
 [Windows Forms a datové vazby](/dotnet/framework/winforms/data-binding-and-windows-forms)   
 [Postupy: Vytvoření jednoduše vázaného ovládacího prvku ve formuláři Windows](/dotnet/framework/winforms/how-to-create-a-simple-bound-control-on-a-windows-form)   
 [Vytvoření vazby ovládacích prvků Windows Forms k datům v sadě Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Uložit data zpět do databáze](../data-tools/save-data-back-to-the-database.md)    
 [Aktualizace dat pomocí TableAdapter](../data-tools/update-data-by-using-a-tableadapter.md)    
 [Data v mezipaměti](../vsto/caching-data.md)   
 [Data v řešeních pro systém Office](../vsto/data-in-office-solutions.md)  
  
  