---
title: Přehled objektového modelu aplikace Excel
ms.date: 08/14/2019
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Worksheet object
- Range object
- object models [Office development in Visual Studio], Excel
- object models [Office development in Visual Studio], Office
- Workbook class
- objects [Office development in Visual Studio], Office object models
- Excel object model
- Office object models
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: a823692a5cc0f154c514edff4fe9398de0efd212
ms.sourcegitcommit: ade07bd1cf69b8b494d171ae648cfdd54f7800d3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/21/2020
ms.locfileid: "81649415"
---
# <a name="excel-object-model-overview"></a>Přehled objektového modelu aplikace Excel
  Chcete-li vyvíjet řešení, která používají aplikaci Microsoft Office Excel, můžete pracovat s objekty poskytovanými objektovým modelem aplikace Excel. Toto téma představuje nejdůležitější objekty:

- <xref:Microsoft.Office.Interop.Excel.Application>

- <xref:Microsoft.Office.Interop.Excel.Workbook>

- <xref:Microsoft.Office.Interop.Excel.Worksheet>

- <xref:Microsoft.Office.Interop.Excel.Range>

  [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

[!include[Add-ins note](includes/addinsnote.md)]

  Objektový model pozorně sleduje uživatelské rozhraní. Objekt <xref:Microsoft.Office.Interop.Excel.Application> představuje celou aplikaci <xref:Microsoft.Office.Interop.Excel.Workbook> a každý objekt `Worksheet` obsahuje kolekci objektů. Odtud je hlavní abstrakce, která <xref:Microsoft.Office.Interop.Excel.Range> představuje buňky, objekt, který umožňuje pracovat s jednotlivými buňkami nebo skupinami buněk.

  Kromě objektového modelu aplikace Excel poskytují projekty sady Office v sadě Visual Studio *položky hostitele* a *ovládací prvky hostitele,* které rozšiřují některé objekty v objektovém modelu aplikace Excel. Hostitelské položky a ovládací prvky hostitele se chovají jako objekty aplikace Excel, které rozšiřují, ale mají také další funkce, jako jsou možnosti vazby dat a další události. Další informace naleznete [v tématu Automatizace excelu pomocí rozšířených objektů](../vsto/automating-excel-by-using-extended-objects.md) a [hostitelských položek a přehledu ovládacích prvků hostitele](../vsto/host-items-and-host-controls-overview.md).

  Toto téma obsahuje stručný přehled objektového modelu aplikace Excel. Materiály, kde se můžete dozvědět více o celém objektovém modelu aplikace Excel, naleznete [v tématu Použití dokumentace k objektovému modelu aplikace Excel](#ExcelOMDocumentation).

## <a name="access-objects-in-an-excel-project"></a>Přístup k objektům v projektu aplikace Excel
 Při vytváření nového projektu doplňku VSTO pro Excel visual studio automaticky vytvoří soubor kódu *ThisAddIn.vb* nebo *ThisAddIn.cs.* K objektu Aplikace můžete `Me.Application` `this.Application`přistupovat pomocí aplikace nebo .

 Když vytvoříte nový projekt na úrovni dokumentu pro Excel, máte možnost vytvořit nový excelový sešit nebo projekt šablony aplikace Excel. Visual Studio automaticky vytvoří následující soubory kódu v novém projektu aplikace Excel pro projekty sešitu i šablony.

|Visual Basic|C#|
|------------------|---------|
|Tentoworkbook.vb|ThisWorkbook.cs|
|List1.vb|Sheet1.cs|
|List2.vb|Sheet2.cs|
|List3.vb|Sheet3.cs|

 `Globals` Třídu v projektu můžete použít `ThisWorkbook` `Sheet1`pro `Sheet2`přístup `Sheet3` , , nebo z mimo příslušnou třídu. Další informace naleznete [v tématu Globální přístup k objektům v projektech sady Office](../vsto/global-access-to-objects-in-office-projects.md). Následující příklad volá <xref:Microsoft.Office.Interop.Excel._Worksheet.PrintPreview%2A> `Sheet1` metodu bez ohledu na to, zda `Sheet`je kód umístěn v jedné z *n* třídy nebo třídy. `ThisWorkbook`

 [!code-csharp[Trin_VstcoreExcelAutomation#82](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#82)]
 [!code-vb[Trin_VstcoreExcelAutomation#82](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#82)]

 Vzhledem k tomu, že data v dokumentu aplikace Excel jsou vysoce strukturovaná, je objektový model hierarchický a přímočarý. Aplikace Excel poskytuje stovky objektů, se kterými můžete chtít pracovat, ale můžete získat dobrý start na objektový model zaostřením na malou podmnožinu dostupných objektů. Mezi tyto objekty patří následující čtyři:

- Aplikace

- sešit

- list

- Rozsah

  Velká část práce vykonaná s aplikací Excel se soustředí na tyto čtyři objekty a jejich členy.

### <a name="application-object"></a>Aplikační objekt
 <xref:Microsoft.Office.Interop.Excel.Application> Excel objekt představuje samotnou aplikaci Aplikace Excel. Objekt <xref:Microsoft.Office.Interop.Excel.Application> zveřejňuje velké množství informací o spuštěné aplikaci, možnosti použité pro tuto instanci a aktuální uživatelské objekty otevřít v rámci instance.

> [!NOTE]
> Vlastnost objektu <xref:Microsoft.Office.Interop.Excel.ApplicationClass.EnableEvents%2A> v aplikaci <xref:Microsoft.Office.Interop.Excel.Application> Excel byste neměli nastavovat na **hodnotu false**. Nastavení této vlastnosti na false zabrání aplikaci Excel ve vyvolání všech událostí, včetně událostí ovládacích prvků hostitele.

### <a name="workbook-object"></a>Objekt sešitu
 Objekt <xref:Microsoft.Office.Interop.Excel.Workbook> představuje jeden sešit v aplikaci Excel.

 Vývojové nástroje sady Office v <xref:Microsoft.Office.Interop.Excel.Workbook> sadě Visual <xref:Microsoft.Office.Tools.Excel.Workbook> Studio rozšiřují objekt poskytnutím typu. Tento typ umožňuje přístup ke <xref:Microsoft.Office.Interop.Excel.Workbook> všem funkcím objektu. Další informace naleznete v tématu [Položka hostitele sešitu](../vsto/workbook-host-item.md).

### <a name="worksheet-object"></a>list – objekt
 Objekt <xref:Microsoft.Office.Interop.Excel.Worksheet> je členem <xref:Microsoft.Office.Interop.Excel.Worksheets> kolekce. Mnoho vlastností, metod a událostí <xref:Microsoft.Office.Interop.Excel.Worksheet> jsou identické nebo podobné členy <xref:Microsoft.Office.Interop.Excel.Application> <xref:Microsoft.Office.Interop.Excel.Workbook> poskytované nebo objekty.

 Aplikace Excel <xref:Microsoft.Office.Interop.Excel.Sheets> poskytuje kolekci <xref:Microsoft.Office.Interop.Excel.Workbook> jako vlastnost objektu. Každý člen <xref:Microsoft.Office.Interop.Excel.Sheets> kolekce je <xref:Microsoft.Office.Interop.Excel.Worksheet> buď <xref:Microsoft.Office.Interop.Excel.Chart> nebo objekt.

 Vývojové nástroje sady Office v <xref:Microsoft.Office.Interop.Excel.Worksheet> sadě Visual <xref:Microsoft.Office.Tools.Excel.Worksheet> Studio rozšiřují objekt poskytnutím typu. Tento typ umožňuje přístup ke <xref:Microsoft.Office.Interop.Excel.Worksheet> všem funkcím objektu, stejně jako nové funkce, jako je například možnost hostitele spravované ovládací prvky a zpracování nových událostí. Další informace naleznete v tématu [Host item listu](../vsto/worksheet-host-item.md).

### <a name="range-object"></a>rozsah – objekt
 Objekt <xref:Microsoft.Office.Interop.Excel.Range> je objekt, který budete používat nejvíce v aplikacích aplikace aplikace Aplikace Excel. Před manipulací s libovolnou oblastí v aplikaci <xref:Microsoft.Office.Interop.Excel.Range> Excel je nutné ji vyjádřit jako objekt a pracovat s metodami a vlastnostmi tohoto rozsahu. Objekt <xref:Microsoft.Office.Interop.Excel.Range> představuje buňku, řádek, sloupec, výběr buněk, které obsahují jeden nebo více bloků buněk, které mohou nebo nemusí být souvislé, nebo dokonce skupinu buněk na více listech.

 Visual Studio rozšiřuje <xref:Microsoft.Office.Interop.Excel.Range> objekt <xref:Microsoft.Office.Tools.Excel.NamedRange> tím, <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> že poskytuje a typy. Tyto typy mají většinu stejných <xref:Microsoft.Office.Interop.Excel.Range> funkcí jako objekt, stejně jako nové funkce, jako je například schopnost datové vazby a nové události. Další informace naleznete v tématu [NamedRange ovládací prvek](../vsto/namedrange-control.md) a [XmlMappedRange ovládací prvek](../vsto/xmlmappedrange-control.md).

## <a name="use-the-excel-object-model-documentation"></a><a name="ExcelOMDocumentation"></a>Použití dokumentace k objektovému modelu aplikace Excel
 Úplné informace o objektovém modelu aplikace Excel naleznete v odkazu na odkaz na primární sestavení aplikace Excel (PIA) a odkaz na objektový model VBA.

### <a name="primary-interop-assembly-reference"></a>Odkaz na sestavení primárního interopu
 Referenční dokumentace aplikace Excel PIA popisuje typy v primárním sestavení interop pro Excel. Tato dokumentace je k dispozici z následujícího umístění: [Excel 2010 primární interop odkaz na sestavení](office-primary-interop-assemblies.md).

 Další informace o návrhu pia aplikace Excel, jako jsou rozdíly mezi třídami a rozhraními v PIA a způsob implementace událostí v PIA, naleznete v [tématu Přehled tříd a rozhraní v primárních sestaveních meziop sady Office](/previous-versions/office/office-12/ms247299(v=office.12)).

### <a name="vba-object-model-reference"></a>Odkaz na objektový model VBA
 Odkaz na objektový model VBA dokumentuje objektový model aplikace Excel tak, jak je vystaven kódu jazyka Visual Basic for Applications (VBA). Další informace naleznete v [tématu Excel 2010 objektový model odkaz .](/office/vba/api/overview/Excel/object-model)

 Všechny objekty a členy v odkazu objektového modelu VBA odpovídají typům a členům v aplikaci Excel PIA. Například objekt List v odkazu objektového modelu VBA <xref:Microsoft.Office.Interop.Excel.Worksheet> odpovídá objektu v aplikaci Excel PIA. Přestože odkaz objektového modelu VBA poskytuje příklady kódu pro většinu vlastností, metod a událostí, je nutné přeložit kód VBA v tomto odkazu na Visual Basic nebo Visual C#, pokud je chcete použít v projektu aplikace Excel, který vytvoříte pomocí sady Visual Studio.

### <a name="related-topics"></a>Související témata

|Nadpis|Popis|
|-----------|-----------------|
|[Řešení aplikace Excel](../vsto/excel-solutions.md)|Vysvětluje, jak můžete vytvořit vlastní nastavení na úrovni dokumentu a doplňky VSTO pro aplikaci Microsoft Office Excel.|
|[Práce s rozsahy](../vsto/working-with-ranges.md)|Obsahuje příklady, které ukazují, jak provádět běžné úkoly s rozsahy.|
|[Práce s listy](../vsto/working-with-worksheets.md)|Obsahuje příklady, které ukazují, jak provádět běžné úkoly s listy.|
|[Práce se sešity](../vsto/working-with-workbooks.md)|Obsahuje příklady, které ukazují, jak provádět běžné úkoly se sešity.|
