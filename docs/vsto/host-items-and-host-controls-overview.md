---
title: Přehled hostitelských položek a hostitelských ovládacích prvků
ms.date: 02/02/2017
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
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: c349756eb12fe66800e209bd6a1aad5b8d2337ab
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "71255920"
---
# <a name="host-items-and-host-controls-overview"></a>Přehled hostitelských položek a hostitelských ovládacích prvků
  Hostitelských položek a hostitelských ovládacích prvků jsou typy, které vám pomůžou poskytnout programovací model pro řešení Office vytvořená pomocí vývojářských nástrojů pro Office v sadě Visual Studio. Hostitelské položky a hostitelské ovládací prvky umožňují interakci s objektovými modely systém Microsoft Office Word a systém Microsoft Office Excel, které jsou založeny na modelu COM, podobně jako interakce se spravovanými objekty, jako jsou například ovládací prvky model Windows Forms.

 [!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]

## <a name="host-items"></a>Hostitelské položky
 Položky hostitele jsou typy, které se nacházejí v horní části hierarchií objektového modelu v projektech pro systém Office. [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]Definuje následující položky hostitele pro řešení Word a Excel:

- <xref:Microsoft.Office.Tools.Word.Document>

- <xref:Microsoft.Office.Tools.Excel.Workbook>

- <xref:Microsoft.Office.Tools.Excel.Worksheet>

- <xref:Microsoft.Office.Tools.Excel.ChartSheet>

  Každý z těchto typů rozšiřuje objekt, který existuje nativně v modelu aplikace Word nebo Excel Object Model, který se nazývá *nativní objekt Office*. Například <xref:Microsoft.Office.Tools.Word.Document> Hostitelská položka rozšiřuje <xref:Microsoft.Office.Interop.Word.Document> objekt, který je definován v primárním sestavení vzájemné spolupráce pro Word.

  Položky hostitele mají obecně stejné základní funkce jako odpovídající objekty Office, ale jsou vylepšeny pomocí následujících funkcí:

- Schopnost hostovat spravované ovládací prvky, včetně hostitelských ovládacích prvků a model Windows Formsch ovládacích prvků.

- Bohatší modely událostí. Některé události dokumentu, sešitu a listu v nativních objektech aplikace Word a Excel jsou vyvolány pouze na úrovni aplikace. Hostitelské položky poskytují tyto události na úrovni dokumentu, aby bylo snazší zpracovávat události pro konkrétní dokument.

### <a name="understand-host-items-in-document-level-projects"></a>Porozumění položkám hostitele v projektech na úrovni dokumentu
 V projektech na úrovni dokumentu poskytují hostitelské položky vstupní bod pro svůj kód a mají návrháře, kteří vám pomůžou vyvíjet řešení.

 <xref:Microsoft.Office.Tools.Word.Document> <xref:Microsoft.Office.Tools.Excel.Worksheet> Položky hostitele a mají přidružené designery, které jsou vizuálním znázorněním dokumentu nebo listu, jako je model Windows Forms Designer. Pomocí tohoto návrháře můžete změnit obsah dokumentu nebo listu přímo v aplikaci Word nebo Excel a přetáhnout ovládací prvky na návrhovou plochu. Další informace najdete v tématu položka hostitele [dokumentu](../vsto/document-host-item.md) položka hostitele a [list](../vsto/worksheet-host-item.md).

 <xref:Microsoft.Office.Tools.Excel.Workbook>Hostitelská položka nepůsobí jako kontejner pro ovládací prvky, které mají uživatelské rozhraní. Místo toho Návrhář pro tuto položku hostitele funguje jako zásobník komponenty, který umožňuje přetáhnout komponentu, jako je například <xref:System.Data.DataSet> , na svou návrhovou plochu. Další informace najdete v tématu [položka hostitele sešitu](../vsto/workbook-host-item.md).

 Hostitelské položky nelze vytvořit programově v projektech na úrovni dokumentu. Místo toho použijte `ThisDocument` třídy, `ThisWorkbook` nebo `Sheet` *n* , které Visual Studio automaticky generuje v projektu v době návrhu. Tyto generované třídy jsou odvozeny z hostitelských položek a poskytují vstupní bod pro váš kód. Další informace najdete v tématu [programové omezení hostitelských položek a hostitelských ovládacích prvků](../vsto/programmatic-limitations-of-host-items-and-host-controls.md).

### <a name="understand-host-items-in-vsto-add-in-projects"></a>Principy hostitelských položek v projektech doplňku VSTO
 Při vytváření doplňku VSTO nemáte ve výchozím nastavení přístup k žádným položkám hostitele. <xref:Microsoft.Office.Tools.Word.Document> <xref:Microsoft.Office.Tools.Excel.Workbook> <xref:Microsoft.Office.Tools.Excel.Worksheet> V programu Word a excelové doplňky VSTO ale můžete v době běhu vygenerovat a hostovat položky.

 Po vygenerování položky hostitele můžete provádět úlohy, jako je přidání ovládacích prvků do dokumentů. Další informace najdete v tématu [rozšiřování dokumentů aplikace Word a sešitů aplikace Excel v doplňkech VSTO za běhu](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).

## <a name="host-controls"></a>Hostitelské ovládací prvky
 Hostitelské ovládací prvky rozšíří různé objekty uživatelského rozhraní (UI) do objektových modelů aplikace Word a Excel, jako například `Microsoft.Office.Interop.Word.ContentControl` <xref:Microsoft.Office.Interop.Excel.Range> objekty a.

 Pro excelové projekty jsou k dispozici následující ovládací prvky hostitele:

- [Ovládací prvek grafu](../vsto/chart-control.md)

- [Ovládací prvek ListObject](../vsto/listobject-control.md)

- [Ovládací prvek NamedRange](../vsto/namedrange-control.md)

- [Ovládací prvek XmlMappedRange –](../vsto/xmlmappedrange-control.md)

  Pro projekty aplikace Word jsou k dispozici následující ovládací prvky hostitele:

- [Ovládací prvek záložek](../vsto/bookmark-control.md)

- [Ovládací prvky obsahu](../vsto/content-controls.md)

- [XMLNode – ovládací prvek](../vsto/xmlnode-control.md)

- [Ovládací prvek XMLNodes](../vsto/xmlnodes-control.md)

  Hostitelské ovládací prvky, které se přidají do dokumentů Office, se chovají jako nativní objekty Office. Nicméně ovládací prvky hostitele mají další funkce, včetně událostí a funkcí datové vazby. Například pokud chcete zachytit události nativního <xref:Microsoft.Office.Interop.Excel.Range> objektu v aplikaci Excel, je nutné nejprve zpracovat událost změny listu. Pak je nutné určit, zda došlo ke změně v rámci <xref:Microsoft.Office.Interop.Excel.Range> . Naproti tomu <xref:Microsoft.Office.Tools.Excel.NamedRange> má hostitelský ovládací prvek <xref:Microsoft.Office.Tools.Excel.NamedRange.Change> událost, kterou lze zpracovat přímo.

  Vztah mezi položkou hostitele a ovládacími prvky hostitele je podobný relaci mezi ovládacími prvky Windows Form a model Windows Forms. Stejně jako umístíte ovládací prvek textové pole do formuláře Windows, umístěte <xref:Microsoft.Office.Tools.Excel.NamedRange> ovládací prvek na <xref:Microsoft.Office.Tools.Excel.Worksheet> položku hostitele. Následující ilustrace znázorňuje vztah mezi položkami hostitele a hostitelskými ovládacími prvky.

  ![Vztah mezi hostitelskými položkami a hostitelskými ovládacími prvky](../vsto/media/hostitemscontrols.png "Vztah mezi hostitelskými položkami a hostitelskými ovládacími prvky")

  Můžete také použít ovládací prvky model Windows Forms v řešeních pro systém Office tak, že je přidáte přímo na plochu dokumentu aplikace Word a Excel. Další informace najdete v tématu [přehled model Windows Formsch ovládacích prvků v dokumentech Office](../vsto/windows-forms-controls-on-office-documents-overview.md).

> [!NOTE]
> Přidávání hostitelských ovládacích prvků nebo model Windows Forms ovládacích prvků do vnořeného dokumentu aplikace Word není podporováno.

### <a name="add-host-controls-to-your-documents"></a>Přidání ovládacích prvků hostitele do dokumentů
 V projektech na úrovni dokumentu můžete přidat hostitelské ovládací prvky do dokumentů aplikace Word nebo sešitů aplikace Excel v době návrhu následujícími způsoby:

- Přidejte do dokumentu ovládací prvky hostitele v době návrhu stejným způsobem, jako byste přidali nativní objekt.

- Přetáhněte ovládací prvky hostitele ze **sady nástrojů** do dokumentů a listů. Ovládací prvky hostování aplikace Excel jsou k dispozici na kartě **ovládací prvky aplikace Excel** v projektech aplikace Excel a ovládací prvky hostitele aplikace Word jsou k dispozici na kartě **ovládací prvky aplikace Word** v projektech aplikace Word.

- Přetáhněte ovládací prvky hostitele z okna **zdroje dat** do svých dokumentů a listů. To umožňuje přidat ovládací prvky, které jsou již svázány s daty. Další informace najdete v tématu [vázání dat k ovládacím prvkům v řešeních pro systém Office](../vsto/binding-data-to-controls-in-office-solutions.md).

  V projektech doplňku na úrovni dokumentu a VSTO můžete do dokumentů v době běhu přidat také některé ovládací prvky hostitele. Další informace najdete v tématu [Přidání ovládacích prvků do dokumentů Office v době běhu](../vsto/adding-controls-to-office-documents-at-run-time.md).

  Další informace o tom, jak přidat hostitelské ovládací prvky do dokumentů, naleznete v následujících tématech:

- [Postupy: Přidání ovládacích prvků grafu do listů](../vsto/how-to-add-chart-controls-to-worksheets.md)

- [Postupy: Přidání ovládacích prvků ListObject do listů](../vsto/how-to-add-listobject-controls-to-worksheets.md)

- [Postupy: Přidání ovládacích prvků NamedRange do listů](../vsto/how-to-add-namedrange-controls-to-worksheets.md)

- [Postupy: Přidání ovládacích prvků XmlMappedRange – do listů](../vsto/how-to-add-xmlmappedrange-controls-to-worksheets.md)

- [Postupy: Přidání ovládacích prvků záložek do dokumentů aplikace Word](../vsto/how-to-add-bookmark-controls-to-word-documents.md)

- [Postupy: Přidání ovládacích prvků obsahu do dokumentů aplikace Word](../vsto/how-to-add-content-controls-to-word-documents.md)

- [Postupy: Přidání ovládacích prvků XMLNode do dokumentů aplikace Word](../vsto/how-to-add-xmlnode-controls-to-word-documents.md)

- [Postupy: Přidání ovládacích prvků XMLNodes do dokumentů aplikace Word](../vsto/how-to-add-xmlnodes-controls-to-word-documents.md)

### <a name="name-host-controls"></a>Název hostitelských ovládacích prvků
 Při přetažení hostitelského ovládacího prvku z **panelu nástrojů** do dokumentu je ovládací prvek automaticky pojmenován pomocí typu ovládacího prvku s přírůstkovým číslem na konci. Například záložky mají název **bookmark1**, **bookmark2**a tak dále. Pokud k přidání ovládacího prvku používáte nativní funkce Wordu nebo Excelu, můžete mu dát konkrétní název v okamžiku, kdy ho vytvoříte. Můžete také přejmenovat ovládací prvky změnou hodnoty vlastnosti **název** v okně **vlastnosti** .

> [!NOTE]
> Pro pojmenování hostitelských ovládacích prvků nelze použít vyhrazená slova. Například pokud přidáte <xref:Microsoft.Office.Tools.Excel.NamedRange> ovládací prvek do listu a změníte název na **systém**, dojde k chybám při sestavování projektu.

### <a name="delete-host-controls"></a>Odstranit hostitelské ovládací prvky
 V projektech na úrovni dokumentu lze ovládací prvky hostitele odstranit v době návrhu výběrem ovládacího prvku na listu aplikace Excel nebo dokumentu aplikace Word a stisknutím klávesy **Delete** . Chcete-li však odstranit ovládací prvky, je nutné použít dialogové okno **definovat název** v aplikaci Excel <xref:Microsoft.Office.Tools.Excel.NamedRange> .

 Přidáte-li hostitelský ovládací prvek do dokumentu v době návrhu, neměli byste jej během doby běhu v kódu programu odebrat programově, protože při příštím pokusu o použití ovládacího prvku v kódu je vyvolána výjimka. `Delete`Metoda hostitelského řízení odebírá pouze ovládací prvky hostitele, které jsou přidány do dokumentu v době běhu. Pokud voláte `Delete` metodu hostitelského ovládacího prvku, který byl vytvořen v době návrhu, je vyvolána výjimka.

 Například <xref:Microsoft.Office.Tools.Excel.NamedRange.Delete%2A> Metoda <xref:Microsoft.Office.Tools.Excel.NamedRange> pouze úspěšně odstraní, <xref:Microsoft.Office.Tools.Excel.NamedRange> Pokud byla programově přidána do listu, který je označován jako dynamické vytváření hostitelských ovládacích prvků. Dynamicky vytvořené ovládací prvky hostitele lze také odebrat předáním názvu ovládacího prvku do `Remove` metody <xref:Microsoft.Office.Tools.Excel.Worksheet.Controls%2A> <xref:Microsoft.Office.Tools.Word.Document.Controls%2A> vlastnosti nebo. Další informace najdete v tématu [Přidání ovládacích prvků do dokumentů Office v době běhu](../vsto/adding-controls-to-office-documents-at-run-time.md).

 Pokud koncoví uživatelé odstraní hostitelský ovládací prvek z dokumentu za běhu, řešení může selhat neočekávaným způsobem. Pomocí funkcí ochrany dokumentů ve Wordu a Excelu můžete chránit ovládací prvky hostitele před smazáním. Další informace najdete v tématu [ukázky a návody pro vývoj pro Office](../vsto/office-development-samples-and-walkthroughs.md).

> [!NOTE]
> Neodstraňujte programově ovládací prvky během `Shutdown` obslužné rutiny události v dokumentu nebo listu. Prvky uživatelského rozhraní již nejsou k dispozici, pokud `Shutdown` dojde k události. Chcete-li odebrat ovládací prvky před zavřením aplikace, přidejte svůj kód do jiné obslužné rutiny události, jako je například `BeforeClose` nebo `BeforeSave` .

### <a name="program-against-host-control-events"></a>Program proti událostem řízení hostitele
 Jedním ze způsobů, jakými ovládací prvky hostování rozšíří objekty Office, je přidání událostí. Například <xref:Microsoft.Office.Interop.Excel.Range> objekt v Excelu a <xref:Microsoft.Office.Interop.Word.Bookmark> objekt ve Wordu nemá události, ale [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] rozšiřuje tyto objekty přidáním programovatelné události. K těmto událostem můžete přistupovat a Code stejným způsobem jako při přístupu k událostem ovládacích prvků na model Windows Forms: prostřednictvím rozevíracího seznamu události v Visual Basic a stránky vlastností události v jazyce C#. Další informace naleznete v tématu [Návod: program v událostech ovládacího prvku NamedRange](../vsto/walkthrough-programming-against-events-of-a-namedrange-control.md).

> [!NOTE]
> V Excelu byste neměli nastavit <xref:Microsoft.Office.Interop.Excel._Application.EnableEvents%2A> vlastnost <xref:Microsoft.Office.Interop.Excel.Application> objektu na **false**. Nastavení této vlastnosti na **hodnotu false** zabraňuje aplikaci Excel ve vyvolání jakýchkoli událostí, včetně událostí hostitelských ovládacích prvků.

## <a name="see-also"></a>Viz také
- [Programové omezení hostitelských položek a hostitelských ovládacích prvků](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Programové doplňky VSTO](../vsto/programming-vsto-add-ins.md)
- [Přizpůsobení na úrovni dokumentu programu](../vsto/programming-document-level-customizations.md)
- [Automatizace Wordu pomocí rozšířených objektů](../vsto/automating-word-by-using-extended-objects.md)
- [Automatizace Excelu pomocí rozšířených objektů](../vsto/automating-excel-by-using-extended-objects.md)
- [Ovládací prvky v dokumentech Office](../vsto/controls-on-office-documents.md)
- [Vázání dat k ovládacím prvkům v řešeních pro systém Office](../vsto/binding-data-to-controls-in-office-solutions.md)
