---
title: Vázání dat k ovládacím prvkům v řešeních pro systém Office
description: Přečtěte si, jak můžete navazovat ovládací prvky model Windows Forms a hostitelské ovládací prvky v dokumentu systém Microsoft Office Wordu nebo excelovém listu na zdroj dat.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: ccc45e9ec389e265e69c81baaf569aa3eb3c978b
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/21/2021
ms.locfileid: "107825625"
---
# <a name="bind-data-to-controls-in-office-solutions"></a>Vázání dat k ovládacím prvkům v řešeních pro systém Office
  Ovládací prvky model Windows Forms a *hostitelské ovládací prvky* lze vytvořit pomocí systém Microsoft Office dokumentu aplikace Word nebo systém Microsoft Office listu aplikace Excel na zdroj dat, aby ovládací prvky automaticky zobrazily data. Data lze navazovat na ovládací prvky v projektech na úrovni aplikace i na úrovni dokumentu.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

 Hostitelské ovládací prvky rozšíří objekty, které jsou v objektech aplikace Word a Excel, jako jsou například ovládací prvky obsahu v aplikaci Word a pojmenované rozsahy v aplikaci Excel. Další informace naleznete v tématu [Přehled hostitelských položek a hostitelských ovládacích prvků](../vsto/host-items-and-host-controls-overview.md).

 Model Windows Forms i hostitelské ovládací prvky používají model model Windows Forms Data Binding, který podporuje *Jednoduché vázání dat* i *složité datové vazby* ke zdrojům dat, jako jsou datové sady a tabulky dat. Úplné informace o modelu vázání dat v model Windows Forms naleznete v tématu [BIND a model Windows Forms dat](/dotnet/framework/winforms/data-binding-and-windows-forms).

## <a name="simple-data-binding"></a>Jednoduchá datová vazba
 Jednoduchá vazba dat existuje, pokud je vlastnost ovládacího prvku svázána s jedním datovým prvkem, například hodnotou v tabulce dat. Například <xref:Microsoft.Office.Tools.Excel.NamedRange> ovládací prvek má <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> vlastnost, která může být svázána s polem v datové sadě. Když se změní pole v datové sadě, změní se také hodnota v pojmenovaném rozsahu. Všechny hostitelské ovládací prvky, s výjimkou <xref:Microsoft.Office.Tools.Word.XMLNodes> ovládacího prvku, podporují jednoduchou datovou vazbu. <xref:Microsoft.Office.Tools.Word.XMLNodes>Ovládací prvek je kolekce, a proto nepodporuje datovou vazbu.

 Chcete-li provést jednoduchou datovou vazbu na hostitelský ovládací prvek, přidejte <xref:System.Windows.Forms.Binding> do `DataBindings` vlastnosti ovládacího prvku. <xref:System.Windows.Forms.Binding>Objekt představuje jednoduchou vazbu mezi hodnotou vlastnosti ovládacího prvku a hodnotou datového elementu.

 Následující příklad ukazuje, jak vytvořit vazby <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> vlastnosti na datový prvek v projektu na úrovni dokumentu.

 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_BindableComponent/Sheet1.vb" id="Snippet4":::
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_BindableComponent/Sheet1.cs" id="Snippet4":::

 Návody, které ilustrují jednoduchou datovou vazbu, najdete v tématu [Návod: jednoduché datové vazby v projektu na úrovni dokumentu](../vsto/walkthrough-simple-data-binding-in-a-document-level-project.md) pro projekt na úrovni dokumentu a [Návod: jednoduché datové vazby v projektu doplňku VSTO](../vsto/walkthrough-simple-data-binding-in-vsto-add-in-project.md) pro projekt doplňku VSTO.

## <a name="complex-data-binding"></a>Složitá datová vazba
 Pokud je vlastnost ovládacího prvku svázaná s více než jedním datovým prvkem, jako je například více sloupců v tabulce dat, existuje složitá datová vazba. <xref:Microsoft.Office.Tools.Excel.ListObject>Ovládací prvek pro Excel je jediným ovládacím prvkem hostitele, který podporuje složitou datovou vazbu. Existuje také řada model Windows Formsch ovládacích prvků, které podporují složitou datovou vazbu, jako je například <xref:System.Windows.Forms.DataGridView> ovládací prvek.

 Chcete-li provést složitou datovou vazbu, nastavte `DataSource` vlastnost ovládacího prvku na objekt zdroje dat, který je podporován složitou datovou vazbou. Například <xref:Microsoft.Office.Tools.Excel.ListObject.DataSource%2A> vlastnost <xref:Microsoft.Office.Tools.Excel.ListObject> ovládacího prvku může být svázána s více sloupci v tabulce dat. Všechna data v datové tabulce se zobrazí v <xref:Microsoft.Office.Tools.Excel.ListObject> ovládacím prvku a data v tabulce dat se <xref:Microsoft.Office.Tools.Excel.ListObject> také změní. Seznam zdrojů dat, které lze použít pro složitou datovou vazbu, najdete v tématu [zdroje dat podporované nástrojem model Windows Forms](/dotnet/framework/winforms/data-sources-supported-by-windows-forms).

 Následující příklad kódu vytvoří <xref:System.Data.DataSet> se dvěma <xref:System.Data.DataTable> objekty a naplní jednu z tabulek daty. Kód pak váže na <xref:Microsoft.Office.Tools.Excel.ListObject> tabulku, která obsahuje data. Tento příklad je pro projekt na úrovni dokumentu aplikace Excel.

 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_ExcelListObject/Trin_ExcelListObject.cs" id="Snippet18":::
 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_ExcelListObject/Sheet1.vb" id="Snippet18":::

 Návody, které ukazují komplexní datovou vazbu, naleznete v tématu [Návod: komplexní datové vazby v projektu na úrovni dokumentu](../vsto/walkthrough-complex-data-binding-in-a-document-level-project.md) pro projekt na úrovni dokumentu a [Návod: komplexní datové vazby v projektu doplňku VSTO](../vsto/walkthrough-complex-data-binding-in-vsto-add-in-project.md) pro projekt doplňku VSTO.

## <a name="display-data-in-documents-and-workbooks"></a>Zobrazení dat v dokumentech a sešitech
 V projektech na úrovni dokumentu můžete použít okno **zdroje dat** k tomu, abyste mohli snadno přidávat ovládací prvky vázané na data do dokumentů nebo sešitů stejným způsobem jako při použití model Windows Forms. Další informace o používání okna **zdroje dat** naleznete v tématu [BIND model Windows Forms Controls to data in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md) a [Add New Data Sources](../data-tools/add-new-data-sources.md).

### <a name="drag-controls-from-the-data-sources-window"></a>Přetáhněte ovládací prvky z okna zdroje dat.
 Ovládací prvek je v dokumentu vytvořen při přetažení objektu z okna **zdroje dat** . Typ ovládacího prvku, který je vytvořen, závisí na tom, zda vytváříte vazbu na jeden sloupec dat nebo více sloupců dat.

 V aplikaci Excel <xref:Microsoft.Office.Tools.Excel.NamedRange> je na listu vytvořen ovládací prvek pro jednotlivá jednotlivá pole a <xref:Microsoft.Office.Tools.Excel.ListObject> ovládací prvek je vytvořen pro každý rozsah dat, který obsahuje více řádků a sloupců. Toto výchozí nastavení můžete změnit tak, že v okně **zdroje dat** vyberete tabulku nebo pole a v rozevíracím seznamu vyberete jiný ovládací prvek.

 <xref:Microsoft.Office.Tools.Word.ContentControl>Do dokumentů je přidán ovládací prvek. Typ ovládacího prvku obsahu závisí na typu dat pole, které jste vybrali.

### <a name="bind-data-in-document-level-projects-at-design-time"></a>Vázání dat v projektech na úrovni dokumentu v době návrhu
 V následujících tématech jsou uvedeny příklady vazeb data v době návrhu:

- [Postupy: naplnění listů daty z databáze](../vsto/how-to-populate-worksheets-with-data-from-a-database.md)

- [Postupy: Naplnění dokumentů daty z databáze](../vsto/how-to-populate-documents-with-data-from-a-database.md)

- [Postupy: Naplnění dokumentů daty z objektů](../vsto/how-to-populate-documents-with-data-from-objects.md)

- [Postupy: Naplnění dokumentů daty ze služeb](../vsto/how-to-populate-documents-with-data-from-services.md)

- [Postupy: procházení databázových záznamů na listu](../vsto/how-to-scroll-through-database-records-in-a-worksheet.md)

### <a name="bind-data-in-vsto-add-in-projects"></a>Vázání dat v projektech doplňku VSTO
 V projektech doplňku VSTO můžete přidat ovládací prvky pouze v době běhu. V následujících tématech jsou uvedeny příklady vazeb dat za běhu:

- [Návod: jednoduché datové vazby v projektu doplňku VSTO](../vsto/walkthrough-simple-data-binding-in-vsto-add-in-project.md)

- [Návod: komplexní datová vazba v projektu doplňku VSTO](../vsto/walkthrough-complex-data-binding-in-vsto-add-in-project.md)

## <a name="update-data-that-is-bound-to-host-controls"></a>Aktualizace dat vázaných na hostitelské ovládací prvky
 Datová vazba mezi zdrojem dat a ovládacím prvkem hostitele zahrnuje aktualizaci dat s obousměrnou aktualizací. V jednoduché datové vazbě se změny ve zdroji dat automaticky odrážejí v hostitelském ovládacím prvku, ale změny v ovládacím prvku host vyžadují explicitní volání pro aktualizaci zdroje dat. Důvodem je, že v některých případech nejsou změny v jednom poli vázané na data přijaty, pokud nejsou doprovázeny změnami v jiném poli vázaného na data. Můžete mít například dvě pole, jednu pro věk a jednu pro roky. Prostředí nemůže překročit stáří. Uživatel nemůže aktualizovat stáří z 50 na 25 a potom z 30 až 10, pokud změny neprovádí ve stejnou dobu. Chcete-li tento problém vyřešit, pole s jednoduchou datovou vazbou nejsou aktualizována, dokud nebudou aktualizace explicitně odesílány pomocí kódu.

 Chcete-li aktualizovat zdroj dat z hostitelských ovládacích prvků, které umožňují jednoduchou datovou vazbu, je nutné odeslat aktualizace zdroje dat v paměti (například <xref:System.Data.DataSet> nebo <xref:System.Data.DataTable> ) a do back-endové databáze, pokud vaše řešení používá jeden.

 Pokud provádíte komplexní datovou vazbu pomocí ovládacího prvku, nemusíte explicitně aktualizovat zdroj dat v paměti <xref:Microsoft.Office.Tools.Excel.ListObject> . V takovém případě se změny automaticky odesílají do zdroje dat v paměti bez dalšího kódu.

 Další informace najdete v tématu [Postup: aktualizace zdroje dat s daty z hostitelského ovládacího prvku](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md).

## <a name="see-also"></a>Viz také
- [Datová vazba a model Windows Forms](/dotnet/framework/winforms/data-binding-and-windows-forms)
- [Postupy: vytvoření jednoduchého ovládacího prvku vázaného na formulář Windows](/dotnet/framework/winforms/how-to-create-a-simple-bound-control-on-a-windows-form)
- [Vytvoření vazby ovládacích prvků modelu Windows Forms k datům v sadě Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [Ukládání dat zpět do databáze](../data-tools/save-data-back-to-the-database.md)
- [Aktualizace dat pomocí objektu TableAdapter](../data-tools/update-data-by-using-a-tableadapter.md)
- [Data mezipaměti](../vsto/caching-data.md)
- [Data v řešeních pro systém Office](../vsto/data-in-office-solutions.md)
