---
title: Přehled ovládacích prvků hostitele a hostitelské položky
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- host controls [Office development in Visual Studio], adding
- Office documents [Office development in Visual Studio, host controls
- host items [Office development in Visual Studio]
- application development [Office development in Visual Studio], host items
- Office applications [Office development in Visual Studio], host items
- host controls [Office development in Visual Studio], listed
- Excel [Office development in Visual Studio], host items
- host controls [Office Development in Visual Stuio], naming
- host controls [Office development in Visual Studio]
- host controls [Office development in Visual Studio], about host controls
- document-level customizations [Office development in Visual Studio], host controls
- Office applications [Office development in Visual Studio], host controls
- documents [Office development in Visual Studio], host controls
- controls [Office development in Visual Studio], host controls
- application development [Office development in Visual Studio], host controls
- Excel [Office development in Visual Studio], host controls
- host items [Office development in Visual Studio], about host items
- host items [Office development in Visual Studio], listed
- documents [Office development in Visual Studio], host items
- data binding [Office development in Visual Studio], host controls
- Office documents [Office development in Visual Studio, host items
- Word [Office development in Visual Studio], host items
- document-level customizations [Office development in Visual Studio], host items
- Word [Office development in Visual Studio], host controls
- host controls [Office development in Visual Studio], deleting
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 48ce311a767d68ce1402961d2ddf4cf8b673637c
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49937496"
---
# <a name="host-items-and-host-controls-overview"></a>Přehled ovládacích prvků hostitele a hostitelské položky
  Hostitelských položek a hostitelských ovládacích prvků jsou typy, které poskytují programovací model pro řešení Office, které jsou vytvořeny pomocí nástroje pro vývoj pro Office v sadě Visual Studio. Hostitelských položek a hostitelských ovládacích prvků Ujistěte se, interakci s objektové modely aplikace Microsoft Office Word a Microsoft Office Excel, které jsou založeny na modelu COM, více jako interakci s spravované objekty, jako jsou například ovládací prvky Windows Forms.  
  
 [!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]  
  
## <a name="host-items"></a>Hostitelské položky  
 Hostitelské položky jsou typy, které jsou v horní části hierarchie objektů modelu v projektech pro systém Office. [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] Definuje následující položky hostitele řešení aplikace Word a Excel:  
  
- <xref:Microsoft.Office.Tools.Word.Document>  
  
- <xref:Microsoft.Office.Tools.Excel.Workbook>  
  
- <xref:Microsoft.Office.Tools.Excel.Worksheet>  
  
- <xref:Microsoft.Office.Tools.Excel.ChartSheet>  
  
  Každý z těchto typů rozšiřuje objekt, který existuje nativně v modelu objektů aplikace Word nebo Excel volána *nativní objekt Office*. Například <xref:Microsoft.Office.Tools.Word.Document> hostitelský objekt rozšiřuje <xref:Microsoft.Office.Interop.Word.Document> objekt, který je definován v primární spolupracující sestavení pro aplikaci Word.  
  
  Hostitelské položky obvykle mají stejné základní funkce jako odpovídajících objektech systému Office, ale jsou vylepšené o následující funkce:  
  
- Možnost hostování spravované ovládací prvky, včetně hostitelské ovládací prvky a ovládací prvky Windows Forms.  
  
- Modely bohatší událostí. Některé události dokumentu, sešitu a listu v nativní modely objektů aplikace Word a Excel jsou vyvolány pouze na úrovni aplikace. Hostitelské položky poskytují tyto události na úrovni dokumentu, tak, aby bylo jednodušší zpracování událostí pro určitého dokumentu.  
  
### <a name="understand-host-items-in-document-level-projects"></a>Vysvětlení hostitelské položky v projektech na úrovni dokumentu  
 V projektech na úrovni dokumentu hostitelské položky poskytují vstupní bod pro kód a mají návrhářů, které pomáhají při vývoji řešení.  
  
 <xref:Microsoft.Office.Tools.Word.Document> a <xref:Microsoft.Office.Tools.Excel.Worksheet> hostitelských položek mají přidružené návrhářích, které jsou vizuální znázornění dokumentu nebo listu, jako jsou Návrhář formulářů Windows. Tento návrhář slouží k úpravě obsahu dokumentu nebo listu přímo v aplikaci Word nebo Excel a přetáhněte ovládací prvky na návrhovou plochu. Další informace najdete v tématu [hostitelská položka Document](../vsto/document-host-item.md) a [hostitelská položka Worksheet](../vsto/worksheet-host-item.md).  
  
 <xref:Microsoft.Office.Tools.Excel.Workbook> Hostitelský objekt nepostupuje jako kontejner pro ovládací prvky, které mají uživatelské rozhraní. Místo toho návrháře pro tuto položku hostitele funguje jako součást na panelu můžete přetáhnout komponentu, jako například <xref:System.Data.DataSet>, na jeho plochu návrhu. Další informace najdete v tématu [hostitelská položka Workbook](../vsto/workbook-host-item.md).  
  
 Hostitelské položky nelze programově v projektech na úrovni dokumentu. Místo toho použijte `ThisDocument`, `ThisWorkbook`, nebo `Sheet` *n* třídy, které sada Visual Studio se automaticky generuje ve vašem projektu v době návrhu. Tyto vygenerované třídy odvozovat z hostitelských položek a poskytují vstupní bod pro kód. Další informace najdete v tématu [programová omezení hostitelských položek a hostitelských ovládacích prvků](../vsto/programmatic-limitations-of-host-items-and-host-controls.md).  
  
### <a name="understand-host-items-in-vsto-add-in-projects"></a>Vysvětlení hostitelské položky v projekty doplňků VSTO  
 Při vytváření doplňku VSTO nemají přístup k položkám všechny hostitele ve výchozím nastavení. Však můžete vygenerovat <xref:Microsoft.Office.Tools.Word.Document>, <xref:Microsoft.Office.Tools.Excel.Workbook>, a <xref:Microsoft.Office.Tools.Excel.Worksheet> hostovat položek v aplikaci Word a doplňků aplikace Excel VSTO za běhu.  
  
 Jakmile vygenerujete položku hostitele, můžete provádět úlohy, jako je přidání ovládacích prvků do dokumentů. Další informace najdete v tématu [rozšíření Wordových dokumentů a Excelových sešitů v doplňcích VSTO za běhu](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
## <a name="host-controls"></a>Hostitelské ovládací prvky  
 Hostitelské ovládací prvky rozšíření různých objektů uživatelského rozhraní (UI) v aplikaci Word a Excel objektové modely, jako například `Microsoft.Office.Interop.Word.ContentControl` a <xref:Microsoft.Office.Interop.Excel.Range> objekty.  
  
 Následující hostitelské ovládací prvky jsou k dispozici pro projekty aplikace Excel:  
  
- [Graf – ovládací prvek](../vsto/chart-control.md)  
  
- [ListObject – ovládací prvek](../vsto/listobject-control.md)  
  
- [Namedrange – ovládací prvek](../vsto/namedrange-control.md)  
  
- [Xmlmappedrange – ovládací prvek](../vsto/xmlmappedrange-control.md)  
  
  Následující hostitelské ovládací prvky jsou k dispozici pro projekty aplikace Word:  
  
- [BOOKMARK – ovládací prvek](../vsto/bookmark-control.md)  
  
- [Ovládací prvky obsahu](../vsto/content-controls.md)  
  
- [XmlNode – ovládací prvek](../vsto/xmlnode-control.md)  
  
- [XmlNodes – ovládací prvek](../vsto/xmlnodes-control.md)  
  
  Hostitelské ovládací prvky, které jsou přidány do dokumentů Office se chovat jako nativní objektů systému Office; hostitelské ovládací prvky však mají další funkce, včetně událostí a funkcí datové vazby. Například, když chcete zaznamenat události nativní <xref:Microsoft.Office.Interop.Excel.Range> objektu v aplikaci Excel, musíte nejprve zpracování události změny listu. Pak musíte určit, jestli ke změně došlo v rámci <xref:Microsoft.Office.Interop.Excel.Range>. Naproti tomu <xref:Microsoft.Office.Tools.Excel.NamedRange> má hostitelský ovládací prvek <xref:Microsoft.Office.Tools.Excel.NamedRange.Change> událost, která dokáže zpracovat přímo.  
  
  Vztah mezi položkou hostitelů a hostitelských ovládacích prvků je podobný vztahu mezi ovládací prvky formuláře Windows a Windows Forms. Stejně jako byste umístit ovládací prvek textové pole ve formuláři Windows Forms, umístíte <xref:Microsoft.Office.Tools.Excel.NamedRange> ovládání na <xref:Microsoft.Office.Tools.Excel.Worksheet> hostitelský objekt. Následující ilustrace znázorňuje vztah mezi hostitelských položek a hostitelských ovládacích prvků.  
  
  ![Vztah mezi hostitelských položek a hostitelských ovládacích prvků](../vsto/media/hostitemscontrols.png "vztah mezi hostitelských položek a hostitelských ovládacích prvků")  
  
  Můžete také použít ovládacích prvků Windows Forms v řešeních pro systém Office tak, že přidáte přímo na plochu dokumentu aplikace Word a Excel. Další informace najdete v tématu [ovládací prvky Windows Forms v přehledu dokumenty Office](../vsto/windows-forms-controls-on-office-documents-overview.md).  
  
> [!NOTE]  
>  Přidání hostitelské ovládací prvky nebo ovládacích prvků Windows Forms do vnořeného dokumentu aplikace Word se nepodporuje.  
  
### <a name="add-host-controls-to-your-documents"></a>Přidat hostitelské ovládací prvky do dokumentů  
 V projektech na úrovni dokumentu můžete přidat hostitelské ovládací prvky do dokumentů aplikace Word nebo sešitů aplikace Excel v době návrhu následujícími způsoby:  
  
- Přidat hostitelské ovládací prvky do dokumentu v době návrhu stejným způsobem by přidat nativní objekt.  
  
- Přetáhněte ovládací prvky hostitele z **nástrojů** na dokumenty a sešity. Jsou k dispozici v aplikaci Excel hostitelské ovládací prvky **ovládací prvky Excelu** kartu v projektech aplikace Excel a hostitel Wordu ovládací prvky jsou k dispozici v **ovládací prvky aplikace Word** kartu v projektech aplikace Word.  
  
- Přetáhněte ovládací prvky hostitele z **zdroje dat** okna do své dokumenty a sešity. To umožňuje přidat ovládací prvky, které jsou již vázán na data. Další informace najdete v tématu [vytvoření vazby dat k ovládacím prvkům v řešeních pro systém Office](../vsto/binding-data-to-controls-in-office-solutions.md).  
  
  Na úrovni dokumentu a projekty doplňku VSTO můžete také přidat několik hostitelských ovládacích prvků do dokumentů za běhu. Další informace najdete v tématu [přidání ovládacích prvků do dokumentů Office za běhu](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
  Další informace o tom, jak přidat hostitelské ovládací prvky k dokumentům naleznete v následujících tématech:  
  
- [Postupy: Přidání ovládacích prvků graf do listů](../vsto/how-to-add-chart-controls-to-worksheets.md)  
  
- [Postupy: Přidání ovládacích prvků ListObject do listů](../vsto/how-to-add-listobject-controls-to-worksheets.md)  
  
- [Postupy: Přidání ovládacích prvků NamedRange do listů](../vsto/how-to-add-namedrange-controls-to-worksheets.md)  
  
- [Postupy: Přidání ovládacích prvků XMLMappedRange do listů](../vsto/how-to-add-xmlmappedrange-controls-to-worksheets.md)  
  
- [Postupy: Přidání ovládacích prvků záložek do dokumentů aplikace Word](../vsto/how-to-add-bookmark-controls-to-word-documents.md)  
  
- [Postupy: Přidání obsahu ovládacích prvků do dokumentů aplikace Word](../vsto/how-to-add-content-controls-to-word-documents.md)  
  
- [Postupy: Přidání ovládacích prvků XMLNode do dokumentů aplikace Word](../vsto/how-to-add-xmlnode-controls-to-word-documents.md)  
  
- [Postupy: Přidání ovládacích prvků XMLNodes do dokumentů aplikace Word](../vsto/how-to-add-xmlnodes-controls-to-word-documents.md)  
  
### <a name="name-host-controls"></a>Název hostitelské ovládací prvky  
 Při přetažení hostitelského ovládacího prvku z **nástrojů** ke svému dokumentu, je ovládací prvek automaticky pojmenuje typ ovládacího prvku pomocí pořadové číslo na konci. Například název záložky **bookmark1**, **bookmark2**, a tak dále. Pokud používáte nativní funkce aplikace Word nebo Excel k přidání ovládacího prvku, můžete jí určitý název v době, kterou vytvoříte. Můžete také přejmenovat ovládacích prvků tak, že změníte hodnotu **název** vlastnost **vlastnosti** okna.  
  
> [!NOTE]  
>  Vyhrazená slova pro název hostitelské ovládací prvky nelze použít. Například, pokud chcete přidat <xref:Microsoft.Office.Tools.Excel.NamedRange> ovládací prvek do listu a změňte název na **systému**, dojde k chybám při sestavení projektu.  
  
### <a name="delete-host-controls"></a>Odstranit hostitelské ovládací prvky  
 V projektech na úrovni dokumentu, můžete odstranit hostitelské ovládací prvky v době návrhu výběrem ovládacího prvku na listu aplikace Excel nebo dokument aplikace Word a stisknutím klávesy **odstranit** klíč. Nicméně je nutné použít **definovat název** dialogové okno v aplikaci Excel a odstranit <xref:Microsoft.Office.Tools.Excel.NamedRange> ovládacích prvků.  
  
 Pokud chcete přidat hostitelského ovládacího prvku na dokument v době návrhu, neměli byste je odstraňovat prostřednictvím kódu programu za běhu vzhledem k tomu, že při příštím pokusu o použití ovládacího prvku v kódu, je vyvolána výjimka. `Delete` Metoda hostitelského ovládacího prvku odebere jenom hostitelských ovládacích prvků, které jsou přidány do dokumentu za běhu. Při volání `Delete` metoda hostitelského ovládacího prvku, který byl vytvořen v době návrhu, je vyvolána výjimka.  
  
 Například <xref:Microsoft.Office.Tools.Excel.NamedRange.Delete%2A> metodu <xref:Microsoft.Office.Tools.Excel.NamedRange> pouze úspěšně odstraní <xref:Microsoft.Office.Tools.Excel.NamedRange> -li programově přidal do listu, který je označován jako dynamicky vytváření hostitelských ovládacích prvků. Dynamicky generovaný hostitelských ovládacích prvků může být odebrán také tím, že předáte název ovládacího prvku, který má `Remove` metodu <xref:Microsoft.Office.Tools.Excel.Worksheet.Controls%2A> nebo <xref:Microsoft.Office.Tools.Word.Document.Controls%2A> vlastnost. Další informace najdete v tématu [přidání ovládacích prvků do dokumentů Office za běhu](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
 Pokud koncoví uživatelé odstraní hostitelského ovládacího prvku z dokumentu za běhu, řešení se nemusí podařit neočekávaným způsobem. Funkce ochrany dokumentu ve Wordu a Excelu můžete chránit hostitelské ovládací prvky odstranit. Další informace najdete v tématu [Office Ukázky a návody vývoje](../vsto/office-development-samples-and-walkthroughs.md).  
  
> [!NOTE]  
>  Neodebírejte ovládacích prvků při prostřednictvím kódu programu `Shutdown` obslužná rutina události dokumentu nebo listu. Prvky uživatelského rozhraní již nejsou k dispozici při `Shutdown` dojde k události. Pokud chcete odebrání ovládacích prvků, než aplikaci zavře, přidejte svůj kód na jinou obslužnou rutinu události, jako `BeforeClose` nebo `BeforeSave`.  
  
### <a name="program-against-host-control-events"></a>Program ošetření událostí ovládacího prvku hostitele  
 Jedním ze způsobů, hostitelské ovládací prvky rozšíření objektů systému Office, je přidání událostí. Například <xref:Microsoft.Office.Interop.Excel.Range> objektu v aplikaci Excel a <xref:Microsoft.Office.Interop.Word.Bookmark> objektu ve Wordu nemají události, ale [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] rozšiřuje tyto objekty tak, že přidáte programovatelný události. Můžete používat a psát kód s využitím těchto událostí stejný způsobem, jakým přistupujete událostí ovládacích prvků ve formulářích Windows: pomocí rozevíracího seznamu událostí v jazyce Visual Basic a stránku vlastností události v jazyce C#. Další informace najdete v tématu [názorný postup: Program ošetření událostí ovládacího prvku NamedRange](../vsto/walkthrough-programming-against-events-of-a-namedrange-control.md).  
  
> [!NOTE]  
>  Neměli nastavíte <xref:Microsoft.Office.Interop.Excel._Application.EnableEvents%2A> vlastnost <xref:Microsoft.Office.Interop.Excel.Application> objektu v aplikaci Excel a **false**. Nastavení této vlastnosti na **false** brání vyvolání žádné události, včetně událostí hostitelské ovládací prvky aplikace Excel.  
  
## <a name="see-also"></a>Viz také:  
 [Programová omezení hostitelských položek a hostitelských ovládacích prvků](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Programování doplňků VSTO](../vsto/programming-vsto-add-ins.md)   
 [Programování přizpůsobení na úrovni dokumentu](../vsto/programming-document-level-customizations.md)   
 [Automatizace aplikace Word s použitím rozšířených objektů](../vsto/automating-word-by-using-extended-objects.md)   
 [Automatizace aplikace Excel s použitím rozšířených objektů](../vsto/automating-excel-by-using-extended-objects.md)   
 [Ovládací prvky v dokumentech Office](../vsto/controls-on-office-documents.md)   
 [Vytvoření vazby dat k ovládacím prvkům v řešeních pro systém Office](../vsto/binding-data-to-controls-in-office-solutions.md)  
  