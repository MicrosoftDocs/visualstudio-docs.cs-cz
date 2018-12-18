---
title: Přehled modelu objektů aplikace Excel
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 8ca93cae45eed272b683275896efcf83229ca9a3
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49880790"
---
# <a name="excel-object-model-overview"></a>Přehled modelu objektů aplikace Excel
  K vývoji řešení, která používají Microsoft Office Excel, můžete pracovat s objekty poskytované objektovému modelu Excelu. Toto téma představuje nejdůležitější objekty:  
  
- <xref:Microsoft.Office.Interop.Excel.Application>  
  
- <xref:Microsoft.Office.Interop.Excel.Workbook>  
  
- <xref:Microsoft.Office.Interop.Excel.Worksheet>  
  
- <xref:Microsoft.Office.Interop.Excel.Range>  
  
  [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
  Objektový model přesně dodržuje uživatelského rozhraní. <xref:Microsoft.Office.Interop.Excel.Application> Objekt představuje celé aplikace a každé <xref:Microsoft.Office.Interop.Excel.Workbook> objekt obsahuje kolekci `Worksheet` objekty. Tady je hlavní odběru, který představuje buňky <xref:Microsoft.Office.Interop.Excel.Range> objektu, který umožňuje pracovat s jednotlivé buňky nebo skupiny buněk.  
  
  Kromě objektovému modelu Excelu, projektech pro systém Office v sadě Visual Studio poskytují *hostovat položky* a *hostování ovládacích prvků* , které rozšiřují některé objekty v objektovém modelu Excelu. Hostitelských položek a hostitelských ovládacích prvků se chovat jako objekty aplikace Excel, které jejich rozšíření, ale mají také další funkce, jako jsou datové vazby funkce a další události. Další informace najdete v tématu [automatizace aplikace Excel s použitím rozšířených objektů](../vsto/automating-excel-by-using-extended-objects.md) a [hostovat položky a hostujte Přehled ovládacích prvků](../vsto/host-items-and-host-controls-overview.md).  
  
  Toto téma nabízí stručný přehled modelu objektů aplikace Excel. Prostředky, kde můžete dozvědět více o celý model objektů aplikace Excel, naleznete v tématu [použijte dokumentaci modelu objektů aplikace Excel](#ExcelOMDocumentation).  
  
  ![odkaz na video](../vsto/media/playvideo.gif "odkaz na video") související video ukázku naleznete v tématu [jak na to: použití obslužných rutin událostí v aplikaci Excel 2007 Doplněk?](http://go.microsoft.com/fwlink/?LinkID=130291), a [jak tvary použití I: vytvoření bublinového grafu v aplikaci Excel? ](http://go.microsoft.com/fwlink/?LinkID=130313).  
  
## <a name="access-objects-in-an-excel-project"></a>Přístup k objektům v projektu aplikace Excel  
 Při vytváření nového projektu doplňku VSTO pro Excel, sada Visual Studio automaticky vytvoří *ThisAddIn.vb* nebo *ThisAddIn.cs* soubor kódu. Objekt aplikace přístupné prostřednictvím `Me.Application` nebo `this.Application`.  
  
 Když vytvoříte nový projekt na úrovni dokumentu pro Excel, máte možnost vytvořit nový projekt Excelový sešit nebo šablonu v Excelu. Visual Studio automaticky vytvoří následující soubory kódu v projektu nový Excelový sešit a šablony projektů.  
  
|Visual Basic|C#|  
|------------------|---------|  
|ThisWorkbook.vb|ThisWorkbook.cs|  
|Sheet1.vb|Sheet1.cs|  
|Sheet2.vb|Sheet2.cs|  
|Sheet3.vb|Sheet3.cs|  
  
 Můžete použít `Globals` třídu ve vašem projektu pro přístup k `ThisWorkbook`, `Sheet1`, `Sheet2`, nebo `Sheet3` z mimo příslušné třídy. Další informace najdete v tématu [globální přístup k objektům v projektech Office](../vsto/global-access-to-objects-in-office-projects.md). Následující příklad volá <xref:Microsoft.Office.Interop.Excel._Worksheet.PrintPreview%2A> metoda `Sheet1` bez ohledu na to, zda je kód umístěn v jednom z `Sheet` *n* třídy nebo `ThisWorkbook` třídy.  
  
 [!code-csharp[Trin_VstcoreExcelAutomation#82](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#82)]
 [!code-vb[Trin_VstcoreExcelAutomation#82](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#82)]  
  
 Protože vysoce strukturovaná data v dokumentu aplikace Excel, je objektový model hierarchické a jednoduché. Excel nabízí stovky objektů, se kterými můžete pracovat, ale můžete získat dobrý začátek na objektový model se zaměříte na malou podmnožinu dostupných objektů. Mezi tyto objekty patří následující čtyři:  
  
- Aplikace  
  
- sešit  
  
- list  
  
- Rozsah  
  
  Velká část práce v Excelu se soustředí kolem tyto čtyři objekty a jejich členy.  
  
### <a name="application-object"></a>Objekt aplikace  
 V aplikaci Excel <xref:Microsoft.Office.Interop.Excel.Application> objekt představuje samotná aplikace Excel. <xref:Microsoft.Office.Interop.Excel.Application> Objekt poskytuje spoustu informací o běžící aplikaci možnosti použít pro tuto instanci a otevřete aktuální uživatelské objekty v instanci.  
  
> [!NOTE]  
>  Neměli nastavíte <xref:Microsoft.Office.Interop.Excel.ApplicationClass.EnableEvents%2A> vlastnost <xref:Microsoft.Office.Interop.Excel.Application> objektu v aplikaci Excel a **false**. Nastavení této vlastnosti na hodnotu false zabrání Excelu vyvolání žádné události, včetně událostí hostitelské ovládací prvky.  
  
### <a name="workbook-object"></a>Objekt sešitu  
 <xref:Microsoft.Office.Interop.Excel.Workbook> Objekt představuje jeden sešitu aplikace Excel.  
  
 Vývojářské nástroje balíku Office v sadě Visual Studio rozšířit <xref:Microsoft.Office.Interop.Excel.Workbook> objekt tím, že poskytuje <xref:Microsoft.Office.Tools.Excel.Workbook> typu. Tento typ poskytuje přístup ke všem funkcím <xref:Microsoft.Office.Interop.Excel.Workbook> objektu. Další informace najdete v tématu [hostitelská položka Workbook](../vsto/workbook-host-item.md).  
  
### <a name="worksheet-object"></a>list – objekt  
 <xref:Microsoft.Office.Interop.Excel.Worksheet> Objektu je členem skupiny <xref:Microsoft.Office.Interop.Excel.Worksheets> kolekce. Mnoho vlastností, metody a události <xref:Microsoft.Office.Interop.Excel.Worksheet> jsou stejné nebo podobné členům poskytované <xref:Microsoft.Office.Interop.Excel.Application> nebo <xref:Microsoft.Office.Interop.Excel.Workbook> objekty.  
  
 Poskytuje aplikace Excel <xref:Microsoft.Office.Interop.Excel.Sheets> kolekce jako vlastnost <xref:Microsoft.Office.Interop.Excel.Workbook> objektu. Každý člen <xref:Microsoft.Office.Interop.Excel.Sheets> kolekce je buď <xref:Microsoft.Office.Interop.Excel.Worksheet> nebo <xref:Microsoft.Office.Interop.Excel.Chart> objektu.  
  
 Vývojářské nástroje balíku Office v sadě Visual Studio rozšířit <xref:Microsoft.Office.Interop.Excel.Worksheet> objekt tím, že poskytuje <xref:Microsoft.Office.Tools.Excel.Worksheet> typu. Tento typ poskytuje přístup ke všem funkcím <xref:Microsoft.Office.Interop.Excel.Worksheet> objektu, jakož i nové funkce, jako je schopnost hostovat spravované ovládací prvky a zpracovávat nové události. Další informace najdete v tématu [hostitelská položka Worksheet](../vsto/worksheet-host-item.md).  
  
### <a name="range-object"></a>rozsah – objekt  
 <xref:Microsoft.Office.Interop.Excel.Range> Objekt je objekt, který budete používat většinu v rámci aplikace Excel. Předtím, než můžete pracovat s libovolnou oblast v rámci aplikace Excel, musíte ho jako express <xref:Microsoft.Office.Interop.Excel.Range> objektu a práce s metodami a vlastnostmi tohoto rozsahu. A <xref:Microsoft.Office.Interop.Excel.Range> objekt představuje buňky, řádek, sloupec, výběru buněk, který obsahuje jeden nebo více bloků buněk, které nemusí nebo může být souvislé, nebo dokonce skupinu buněk na několik listů.  
  
 Visual Studio rozšiřuje <xref:Microsoft.Office.Interop.Excel.Range> objekt tím, že poskytuje <xref:Microsoft.Office.Tools.Excel.NamedRange> a <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> typy. Tyto typy mají stejné funkce jako většina <xref:Microsoft.Office.Interop.Excel.Range> objektu, jakož i nové funkce, jako jsou datové vazby funkce a nové události. Další informace najdete v tématu [namedrange – ovládací prvek](../vsto/namedrange-control.md) a [xmlmappedrange – ovládací prvek](../vsto/xmlmappedrange-control.md).  
  
##  <a name="ExcelOMDocumentation"></a> Použijte dokumentaci modelu objektů aplikace Excel  
 Podrobnější informace o objektu modelu Excelu mohou odkazovat na referenční primární sestavení vzájemné spolupráce (PIA) aplikace Excel a referenční dokumentace objektového modelu VBA.  
  
### <a name="primary-interop-assembly-reference"></a>Odkaz na primární spolupracující sestavení  
 Referenční dokumentaci Excel PIA popisují typy ve primárního spolupracujícího sestavení pro aplikaci Excel. Tato dokumentace je k dispozici z následujícího umístění: [odkaz na primární spolupracující sestavení aplikace Excel 2010](http://go.microsoft.com/fwlink/?LinkId=189585).  
  
 Další informace o návrhu aplikace Excel PIA, jako jsou rozdíly mezi třídami a rozhraní v PIA a jak jsou implementované událostí v PIA, naleznete v tématu [přehled třídy a rozhraní v primární spolupracující sestavení Office](http://go.microsoft.com/fwlink/?LinkId=189592).  
  
### <a name="vba-object-model-reference"></a>Referenční dokumentace objektového modelu VBA  
 Referenční dokumentace objektového modelu VBA dokumenty objektovému modelu Excelu. protože je vystavena do jazyka Visual Basic pro kód Applications (VBA). Další informace najdete v tématu [referenční dokumentace objektového modelu Excelu 2010](http://go.microsoft.com/fwlink/?LinkId=199768).  
  
 Všechny objekty a členy v referenční dokumentace objektového modelu VBA odpovídají typy a členy v aplikaci Excel PIA. Například objekt listu v referenční dokumentace objektového modelu VBA odpovídá <xref:Microsoft.Office.Interop.Excel.Worksheet> objektu v aplikaci Excel PIA. I když referenční dokumentace objektového modelu VBA poskytuje příklady kódu pro většinu vlastnosti, metody a události, musí překládat kód VBA v této referenční dokumentace jazyka Visual Basic nebo Visual C#, pokud chcete použít v projektu aplikace Excel, který vytvoříte pomocí sady Visual Studio.  
  
### <a name="related-topics"></a>Související témata  
  
|Název|Popis|  
|-----------|-----------------|  
|[Řešení pro aplikaci Excel](../vsto/excel-solutions.md)|Vysvětluje, jak vytvořit přizpůsobení na úrovni dokumentu a doplňky VSTO pro aplikaci Microsoft Office Excel.|  
|[Práce s oblastmi](../vsto/working-with-ranges.md)|Poskytuje příklady, které ukazují, jak provádět běžné úlohy s rozsahy adres.|  
|[Práce s listy](../vsto/working-with-worksheets.md)|Poskytuje příklady, které ukazují, jak provádět běžné úlohy s listy.|  
|[Práce se sešity](../vsto/working-with-workbooks.md)|Poskytuje příklady, které ukazují, jak provádět běžné úkoly se sešity.|  
  
  