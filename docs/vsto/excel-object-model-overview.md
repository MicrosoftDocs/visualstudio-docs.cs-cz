---
title: Přehled modelu objektů aplikace Excel
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "81649415"
---
# <a name="excel-object-model-overview"></a>Přehled modelu objektů aplikace Excel
  Pro vývoj řešení, která používají systém Microsoft Office Excel, můžete pracovat s objekty poskytovanými modelem objektu aplikace Excel. V tomto tématu se seznámíte s nejdůležitějšími objekty:

- <xref:Microsoft.Office.Interop.Excel.Application>

- <xref:Microsoft.Office.Interop.Excel.Workbook>

- <xref:Microsoft.Office.Interop.Excel.Worksheet>

- <xref:Microsoft.Office.Interop.Excel.Range>

  [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

[!include[Add-ins note](includes/addinsnote.md)]

  Objektový model pečlivě sleduje uživatelské rozhraní. <xref:Microsoft.Office.Interop.Excel.Application>Objekt představuje celou aplikaci a každý <xref:Microsoft.Office.Interop.Excel.Workbook> objekt obsahuje kolekci `Worksheet` objektů. Odtud je hlavní abstrakce, která představuje buňky <xref:Microsoft.Office.Interop.Excel.Range> , objekt, který umožňuje pracovat s jednotlivými buňkami nebo skupinami buněk.

  Kromě modelu objektu aplikace *Excel poskytují projekty* Office v sadě Visual Studio i hostitelské *ovládací prvky* , které rozšířily některé objekty v objektovém modelu aplikace Excel. Hostitelské položky a hostitelské ovládací prvky se chovají stejně jako objekty aplikace Excel, které rozšiřuje, ale mají také další funkce, jako jsou například funkce vazby dat a dodatečné události. Další informace naleznete v tématu [Automatizace aplikace Excel pomocí rozšířených objektů](../vsto/automating-excel-by-using-extended-objects.md) a [položek hostitele a Přehled hostitelských ovládacích prvků](../vsto/host-items-and-host-controls-overview.md).

  Toto téma poskytuje stručný přehled modelu objektů aplikace Excel. Prostředky, ve kterých se můžete dozvědět více o celém modelu objektů aplikace Excel, naleznete v [dokumentaci k objektovému modelu aplikace Excel](#ExcelOMDocumentation).

## <a name="access-objects-in-an-excel-project"></a>Přístup k objektům v projektu aplikace Excel
 Když vytvoříte nový projekt doplňku VSTO pro Excel, Visual Studio automaticky vytvoří soubor kódu *ThisAddIn. vb* nebo *ThisAddIn.cs* . K objektu aplikace můžete přistupovat pomocí `Me.Application` nebo `this.Application` .

 Při vytváření nového projektu na úrovni dokumentu pro aplikaci Excel máte možnost vytvořit nový sešit aplikace Excel nebo projekt excelové šablony. Visual Studio automaticky vytvoří následující soubory kódu v novém projektu aplikace Excel pro sešit i šablony projektů.

|Visual Basic|C#|
|------------------|---------|
|ThisWorkbook. vb|ThisWorkbook.cs|
|List1. vb|Sheet1.cs|
|List2. vb|Sheet2.cs|
|Sheet3. vb|Sheet3.cs|

 `Globals`Třídu v projektu můžete použít k přístupu `ThisWorkbook` , `Sheet1` , `Sheet2` nebo `Sheet3` mimo příslušné třídy. Další informace najdete v tématu [globální přístup k objektům v projektech Office](../vsto/global-access-to-objects-in-office-projects.md). Následující příklad volá <xref:Microsoft.Office.Interop.Excel._Worksheet.PrintPreview%2A> metodu bez ohledu na to, `Sheet1` zda je kód umístěn v jedné z `Sheet` tříd *n* nebo `ThisWorkbook` třídy.

 [!code-csharp[Trin_VstcoreExcelAutomation#82](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#82)]
 [!code-vb[Trin_VstcoreExcelAutomation#82](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#82)]

 Vzhledem k tomu, že jsou data v excelovém dokumentu vysoce strukturovaná, objektový model je hierarchický a jednoduchý. Excel poskytuje stovky objektů, se kterými můžete chtít pracovat, ale můžete získat dobrý začátek na objektovém modelu tím, že se zaměříte na malou podmnožinu dostupných objektů. Mezi tyto objekty patří následující čtyři:

- Aplikace

- sešit

- list

- Rozsah

  Mnohé práce s excelovým centrům jsou kolem těchto čtyř objektů a jejich členů.

### <a name="application-object"></a>Objekt aplikace
 Excelový <xref:Microsoft.Office.Interop.Excel.Application> objekt představuje samotnou aplikaci Excel. <xref:Microsoft.Office.Interop.Excel.Application>Objekt zpřístupňuje skvělé informace o spuštěné aplikaci, možnosti použité u této instance a aktuální uživatelské objekty otevřené v rámci instance.

> [!NOTE]
> V Excelu byste neměli nastavit <xref:Microsoft.Office.Interop.Excel.ApplicationClass.EnableEvents%2A> vlastnost <xref:Microsoft.Office.Interop.Excel.Application> objektu na **false**. Nastavení této vlastnosti na hodnotu false zabraňuje aplikaci Excel ve vyvolání jakýchkoli událostí, včetně událostí hostitelských ovládacích prvků.

### <a name="workbook-object"></a>Objekt sešitu
 <xref:Microsoft.Office.Interop.Excel.Workbook>Objekt představuje jeden sešit v aplikaci Excel.

 Vývojové nástroje pro Office v sadě Visual Studio rozšiřuje <xref:Microsoft.Office.Interop.Excel.Workbook> objekt zadáním <xref:Microsoft.Office.Tools.Excel.Workbook> typu. Tento typ vám umožní přístup ke všem funkcím <xref:Microsoft.Office.Interop.Excel.Workbook> objektu. Další informace najdete v tématu [položka hostitele sešitu](../vsto/workbook-host-item.md).

### <a name="worksheet-object"></a>list – objekt
 <xref:Microsoft.Office.Interop.Excel.Worksheet>Objekt je členem <xref:Microsoft.Office.Interop.Excel.Worksheets> kolekce. Mnohé z vlastností, metod a událostí <xref:Microsoft.Office.Interop.Excel.Worksheet> jsou identické nebo podobné členům poskytovaným <xref:Microsoft.Office.Interop.Excel.Application> <xref:Microsoft.Office.Interop.Excel.Workbook> objekty nebo.

 Excel poskytuje <xref:Microsoft.Office.Interop.Excel.Sheets> kolekci jako vlastnost <xref:Microsoft.Office.Interop.Excel.Workbook> objektu. Každý člen <xref:Microsoft.Office.Interop.Excel.Sheets> kolekce je buď <xref:Microsoft.Office.Interop.Excel.Worksheet> <xref:Microsoft.Office.Interop.Excel.Chart> objekt, nebo.

 Vývojové nástroje pro Office v sadě Visual Studio rozšiřuje <xref:Microsoft.Office.Interop.Excel.Worksheet> objekt zadáním <xref:Microsoft.Office.Tools.Excel.Worksheet> typu. Tento typ vám umožní přístup ke všem funkcím <xref:Microsoft.Office.Interop.Excel.Worksheet> objektu a také k novým funkcím, jako je například schopnost hostovat spravované ovládací prvky a zpracovávat nové události. Další informace najdete v tématu [položka hostitele na listu](../vsto/worksheet-host-item.md).

### <a name="range-object"></a>rozsah – objekt
 <xref:Microsoft.Office.Interop.Excel.Range>Objekt je objekt, který budete používat ve svých aplikacích v Excelu. Než budete moci manipulovat s libovolnou oblastí v aplikaci Excel, je nutné ji vyjádřit jako <xref:Microsoft.Office.Interop.Excel.Range> objekt a pracovat s metodami a vlastnostmi tohoto rozsahu. <xref:Microsoft.Office.Interop.Excel.Range>Objekt představuje buňku, řádek, sloupec, výběr buněk, které obsahují jeden nebo více bloků buněk, které mohou nebo nemusí být souvislé nebo dokonce skupina buněk na více listech.

 Visual Studio rozšiřuje <xref:Microsoft.Office.Interop.Excel.Range> objekt tím, že poskytuje <xref:Microsoft.Office.Tools.Excel.NamedRange> <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> typy a. Tyto typy mají většinu stejných funkcí jako <xref:Microsoft.Office.Interop.Excel.Range> objekt a také nové funkce, jako je například schopnost datové vazby a nové události. Další informace naleznete v tématu [NamedRange Control](../vsto/namedrange-control.md) and [XmlMappedRange – Control](../vsto/xmlmappedrange-control.md).

## <a name="use-the-excel-object-model-documentation"></a><a name="ExcelOMDocumentation"></a> Použití dokumentace k objektovému modelu Excelu
 Úplné informace o objektovém modelu aplikace Excel naleznete v tématu odkaz na primární definiční sestavení (PIA) aplikace Excel a referenční materiály k objektovému modelu VBA.

### <a name="primary-interop-assembly-reference"></a>Odkaz na primární definiční sestavení
 Referenční dokumentace k aplikaci Excel PIA popisuje typy v primárním sestavení vzájemné spolupráce pro aplikaci Excel. Tato dokumentace je k dispozici z následujícího umístění: [odkaz na primární definiční sestavení aplikace Excel 2010](office-primary-interop-assemblies.md).

 Další informace o návrhu aplikace Excel PIA, jako jsou rozdíly mezi třídami a rozhraními PIA a jak jsou implementovány události v PIA, naleznete v tématu [Přehled tříd a rozhraní v primárních sestaveních vzájemné spolupráce pro systém Office](/previous-versions/office/office-12/ms247299(v=office.12)).

### <a name="vba-object-model-reference"></a>Referenční dokumentace modelu objektu VBA
 Odkaz model objektu VBA odkazuje na dokumentový model objektu aplikace Excel, protože je vystavený pro jazyk Visual Basic for Application kód (VBA). Další informace najdete v tématu [referenční materiály k objektovému modelu excelu 2010](/office/vba/api/overview/Excel/object-model).

 Všechny objekty a členy v referencích objektového modelu VBA odpovídají typům a členům v aplikaci Excel PIA. Například objekt list v odkazu modelu objektu VBA odpovídá <xref:Microsoft.Office.Interop.Excel.Worksheet> objektu v aplikaci Excel PIA. I když odkaz na objektový model VBA poskytuje příklady kódu pro většinu vlastností, metod a událostí, je nutné překládat kód VBA v tomto odkazu na Visual Basic nebo Visual C#, pokud je chcete použít v projektu aplikace Excel, který vytvoříte pomocí sady Visual Studio.

### <a name="related-topics"></a>Související témata

|Nadpis|Popis|
|-----------|-----------------|
|[Řešení pro Excel](../vsto/excel-solutions.md)|Vysvětluje, jak lze vytvořit přizpůsobení na úrovni dokumentu a doplňky VSTO pro systém Microsoft Office Excel.|
|[Práce s rozsahy](../vsto/working-with-ranges.md)|Obsahuje příklady, které ukazují, jak provádět běžné úlohy s rozsahy.|
|[Práce s listy](../vsto/working-with-worksheets.md)|Obsahuje příklady, které ukazují, jak provádět běžné úkoly s listy.|
|[Práce se sešity](../vsto/working-with-workbooks.md)|Obsahuje příklady, které ukazují, jak provádět běžné úkoly se sešity.|
