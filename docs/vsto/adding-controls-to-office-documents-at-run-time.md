---
title: Přidání ovládacích prvků do dokumentů Office v době běhu
description: Naučte se, jak přidat ovládací prvky do systém Microsoft Office dokumentů aplikace Word a systém Microsoft Office excelového sešitu za běhu.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office documents [Office development in Visual Studio, Windows Forms controls
- host controls [Office development in Visual Studio], adding
- Windows Forms controls [Office development in Visual Studio], adding
- Office documents [Office development in Visual Studio, host controls
- user controls [Office development in Visual Studio], adding at run time
- documents [Office development in Visual Studio], Windows Forms controls
- document-level customizations [Office development in Visual Studio], host controls
- documents [Office development in Visual Studio], host controls
- document-level customizations [Office development in Visual Studio], Windows Forms controls
- controls [Office development in Visual Studio], adding at run time
- helper methods [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: e971556605a120b4ef475f434390c6dcf7b17938
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/08/2020
ms.locfileid: "96844839"
---
# <a name="add-controls-to-office-documents-at-run-time"></a>Přidání ovládacích prvků do dokumentů Office v době běhu
  Ovládací prvky lze přidat do systém Microsoft Office dokumentů aplikace Word a systém Microsoft Office excelový sešit v době běhu. Můžete je také odebrat v době běhu. Ovládací prvky, které přidáte nebo odeberete za běhu, se nazývají *dynamické ovládací prvky*.

 [!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]

 Toto téma popisuje následující:

- [Spravujte ovládací prvky v době běhu pomocí kolekcí ovládacích prvků](#ControlsCollection).

- [Přidejte do dokumentů ovládací prvky hostitele](#HostControls).

- [Přidejte model Windows Forms ovládací prvky do dokumentů](#WindowsForms).

## <a name="manage-controls-at-run-time-by-using-control-collections"></a><a name="ControlsCollection"></a> Správa ovládacích prvků v době běhu pomocí kolekcí ovládacích prvků
 Chcete-li přidat, získat nebo odebrat ovládací prvky v době běhu, použijte pomocné metody <xref:Microsoft.Office.Tools.Excel.ControlCollection> a <xref:Microsoft.Office.Tools.Word.ControlCollection> objekty.

 Způsob, jakým přistupujete k těmto objektům, závisí na typu projektu, který vyvíjíte:

- V projektu na úrovni dokumentu pro aplikaci Excel použijte <xref:Microsoft.Office.Tools.Excel.Worksheet.Controls%2A> vlastnost `Sheet1` `Sheet2` třídy, a `Sheet3` . Další informace o těchto třídách naleznete v tématu [položka hostitele na listu](../vsto/worksheet-host-item.md).

- V projektu na úrovni dokumentu pro aplikaci Word použijte <xref:Microsoft.Office.Tools.Word.Document.Controls%2A> vlastnost `ThisDocument` třídy. Další informace o této třídě naleznete v tématu [položka hostitele dokumentu](../vsto/document-host-item.md).

- V projektu doplňku VSTO pro Excel nebo Word použijte `Controls` vlastnost <xref:Microsoft.Office.Tools.Excel.Worksheet> nebo <xref:Microsoft.Office.Tools.Word.Document> , kterou jste v době běhu vygenerovali. Další informace o generování těchto objektů v době běhu najdete v tématu [rozšiřování dokumentů aplikace Word a sešitů aplikace Excel v doplňcích VSTO za běhu](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).

### <a name="add-controls"></a>Přidat ovládací prvky
 <xref:Microsoft.Office.Tools.Excel.ControlCollection>Typy a <xref:Microsoft.Office.Tools.Word.ControlCollection> zahrnují pomocné metody, které lze použít k přidání ovládacích prvků hostitele a běžných model Windows Formsch ovládacích prvků do dokumentů a listů. Každý název metody má `Add` *třídu ovládacího prvku* Format, kde *Třída ovládacího prvku* je název třídy ovládacího prvku, který chcete přidat. Například pro přidání <xref:Microsoft.Office.Tools.Excel.NamedRange> ovládacího prvku do dokumentu použijte <xref:Microsoft.Office.Tools.Excel.ControlCollection.AddNamedRange%2A> metodu.

 Následující příklad kódu přidá <xref:Microsoft.Office.Tools.Excel.NamedRange> do `Sheet1` v projektu na úrovni dokumentu pro Excel.

 [!code-vb[Trin_ExcelWorkbookDynamicControls#3](../vsto/codesnippet/VisualBasic/trin_excelworkbookdynamiccontrols4/ThisWorkbook.vb#3)]
 [!code-csharp[Trin_ExcelWorkbookDynamicControls#3](../vsto/codesnippet/CSharp/trin_excelworkbookdynamiccontrols4/ThisWorkbook.cs#3)]

### <a name="access-and-delete-controls"></a>Ovládací prvky pro přístup a odstranění
 Můžete použít `Controls` vlastnost <xref:Microsoft.Office.Tools.Excel.Worksheet> nebo <xref:Microsoft.Office.Tools.Word.Document> k iterování všech ovládacích prvků v dokumentu, včetně ovládacích prvků, které jste přidali v době návrhu. Ovládací prvky, které přidáte v době návrhu, se nazývají také *statické ovládací prvky*.

 Dynamické ovládací prvky lze odebrat voláním `Delete` metody ovládacího prvku nebo voláním `Remove` metody každé kolekce ovládacích prvků. Následující příklad kódu používá <xref:Microsoft.Office.Tools.Excel.ControlCollection.Remove%2A> metodu pro odebrání <xref:Microsoft.Office.Tools.Excel.NamedRange> z `Sheet1` v projektu na úrovni dokumentu v aplikaci Excel.

 [!code-vb[Trin_ExcelWorkbookDynamicControls#4](../vsto/codesnippet/VisualBasic/trin_excelworkbookdynamiccontrols4/ThisWorkbook.vb#4)]
 [!code-csharp[Trin_ExcelWorkbookDynamicControls#4](../vsto/codesnippet/CSharp/trin_excelworkbookdynamiccontrols4/ThisWorkbook.cs#4)]

 V době běhu nelze odebrat statické ovládací prvky. Pokud se pokusíte použít `Delete` metodu nebo `Remove` pro odebrání statického ovládacího prvku, <xref:Microsoft.Office.Tools.CannotRemoveControlException> bude vyvolána výjimka.

> [!NOTE]
> Neodstraňujte programově ovládací prvky v `Shutdown` obslužné rutině události v dokumentu. Prvky uživatelského rozhraní dokumentu již nejsou při vyvolání události k dispozici `Shutdown` . Chcete-li odebrat ovládací prvky před zavřením dokumentu, přidejte kód do obslužné rutiny události pro jinou událost, například <xref:Microsoft.Office.Tools.Word.Document.BeforeClose> nebo <xref:Microsoft.Office.Tools.Word.Document.BeforeSave> pro Word, nebo <xref:Microsoft.Office.Tools.Excel.Workbook.BeforeClose> <xref:Microsoft.Office.Tools.Excel.Workbook.BeforeSave> pro aplikaci Excel.

## <a name="add-host-controls-to-documents"></a><a name="HostControls"></a> Přidat do dokumentů ovládací prvky hostitele

Když programově přidáte ovládací prvky hostitele do dokumentů, je nutné zadat název, který jednoznačně identifikuje ovládací prvek, a musíte určit, kam chcete ovládací prvek přidat do dokumentu. Konkrétní pokyny najdete v následujících tématech:

- [Postupy: Přidání ovládacích prvků ListObject do listů](../vsto/how-to-add-listobject-controls-to-worksheets.md)

- [Postupy: Přidání ovládacích prvků NamedRange do listů](../vsto/how-to-add-namedrange-controls-to-worksheets.md)

- [Postupy: Přidání ovládacích prvků grafu do listů](../vsto/how-to-add-chart-controls-to-worksheets.md)

- [Postupy: Přidání ovládacích prvků obsahu do dokumentů aplikace Word](../vsto/how-to-add-content-controls-to-word-documents.md)

- [Postupy: Přidání ovládacích prvků záložek do dokumentů aplikace Word](../vsto/how-to-add-bookmark-controls-to-word-documents.md)

Další informace o hostitelských ovládacích prvcích naleznete v tématu Přehled hostitelských [položek a hostitelských ovládacích prvků](../vsto/host-items-and-host-controls-overview.md).

Když se dokument uloží a pak zavře, všechny dynamicky vytvořené hostitelské ovládací prvky se odpojí od jejich událostí a ztratí své funkce datových vazeb. Do svého řešení můžete přidat kód pro opětovné vytvoření hostitelského ovládacího prvku, když je dokument znovu otevřen. Další informace najdete v tématu [trvalé dynamické ovládací prvky v dokumentech Office](../vsto/persisting-dynamic-controls-in-office-documents.md).

> [!NOTE]
> Pomocné metody nejsou k dispozici pro následující hostitelské ovládací prvky, protože tyto ovládací prvky nelze programově přidat do dokumentů: <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> , a <xref:Microsoft.Office.Tools.Word.XMLNode> <xref:Microsoft.Office.Tools.Word.XMLNodes> .

## <a name="add-windows-forms-controls-to-documents"></a><a name="WindowsForms"></a> Přidání ovládacích prvků model Windows Forms do dokumentů
 Když programově přidáte model Windows Forms ovládací prvek do dokumentu, je nutné zadat umístění ovládacího prvku a název, který jednoznačně identifikuje ovládací prvek. [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]Poskytuje podpůrné metody pro každý ovládací prvek. Tyto metody jsou přetíženy, takže můžete předat buď rozsah, nebo konkrétní souřadnice pro umístění ovládacího prvku.

 Když se dokument uloží a pak zavře, všechny dynamicky vytvořené model Windows Forms ovládací prvky se z dokumentu odeberou. Do svého řešení můžete přidat kód, aby bylo možné znovu vytvořit ovládací prvky při opětovném otevření dokumentu. Pokud vytvoříte dynamické model Windows Forms ovládací prvky pomocí doplňku VSTO, budou v dokumentu ponechány obálky ActiveX pro ovládací prvky. Další informace najdete v tématu [trvalé dynamické ovládací prvky v dokumentech Office](../vsto/persisting-dynamic-controls-in-office-documents.md).

> [!NOTE]
> Ovládací prvky model Windows Forms nelze programově přidat do chráněných dokumentů. Pokud programově zrušíte ochranu dokumentu aplikace Word nebo listu aplikace Excel pro přidání ovládacího prvku, je nutné zapsat další kód, který odebere obálku ActiveX ovládacího prvku při zavření dokumentu. Obálka ActiveX ovládacího prvku není automaticky odstraněna z chráněných dokumentů.

### <a name="add-custom-controls"></a>Přidání vlastních ovládacích prvků
 Pokud chcete přidat objekt <xref:System.Windows.Forms.Control> , který není podporován dostupnými podpůrnými metodami, jako je například vlastní uživatelský ovládací prvek, použijte následující metody:

- V Excelu použijte jednu z <xref:Microsoft.Office.Tools.Excel.ControlCollection.AddControl%2A> metod <xref:Microsoft.Office.Tools.Excel.ControlCollection> objektu.

- V případě aplikace Word použijte jednu z <xref:Microsoft.Office.Tools.Word.ControlCollection.AddControl%2A> metod <xref:Microsoft.Office.Tools.Word.ControlCollection> objektu.

  Chcete-li přidat ovládací prvek, předejte rozhraní <xref:System.Windows.Forms.Control> , umístění ovládacího prvku a název, který jednoznačně identifikuje ovládací prvek pro `AddControl` metodu. `AddControl`Metoda vrátí objekt, který definuje, jak ovládací prvek komunikuje s listem nebo dokumentem. `AddControl`Metoda vrátí <xref:Microsoft.Office.Tools.Excel.ControlSite> (pro Excel) nebo <xref:Microsoft.Office.Tools.Word.ControlSite> objekt (pro Word).

  Následující příklad kódu ukazuje, jak použít <xref:Microsoft.Office.Tools.Excel.ControlCollection.AddControl%2A> metodu k dynamickému Přidání vlastního uživatelského ovládacího prvku do listu v projektu aplikace Excel na úrovni dokumentu. V tomto příkladu je uživatelský ovládací prvek pojmenován `UserControl1` a má <xref:Microsoft.Office.Interop.Excel.Range> název `range1` . Chcete-li použít tento příklad, spusťte jej z `Sheet` třídy *n* v projektu.

  [!code-vb[Trin_VstcoreProgrammingControlsExcel#2](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#2)]
  [!code-csharp[Trin_VstcoreProgrammingControlsExcel#2](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#2)]

### <a name="use-members-of-custom-controls"></a>Použití členů vlastních ovládacích prvků
 Po použití jedné z `AddControl` metod pro přidání ovládacího prvku do listu nebo dokumentu máte nyní dva různé objekty ovládacích prvků:

- <xref:System.Windows.Forms.Control>, Který představuje vlastní ovládací prvek.

- `ControlSite`Objekt, `OLEObject` nebo `OLEControl` , který představuje ovládací prvek po jeho přidání do listu nebo dokumentu.

  Mezi těmito ovládacími prvky se sdílí mnoho vlastností a metod. Je důležité, abyste měli přístup k těmto členům prostřednictvím příslušného ovládacího prvku:

- Pro přístup ke členům, kteří patří pouze do vlastního ovládacího prvku, použijte <xref:System.Windows.Forms.Control> .

- Pro přístup ke členům, které jsou sdíleny ovládacími prvky, použijte `ControlSite` `OLEObject` objekt, nebo `OLEControl` .

  Pokud přistupujete ke sdílenému členu z <xref:System.Windows.Forms.Control> , může selhat bez upozornění nebo oznámení nebo může způsobit neplatné výsledky. Vždy používejte metody nebo vlastnosti `ControlSite` `OLEObject` objektu, nebo, pokud není `OLEControl` požadovaná metoda nebo vlastnost k dispozici; pouze pak byste měli odkazovat na <xref:System.Windows.Forms.Control> .

  Například <xref:Microsoft.Office.Tools.Excel.ControlSite> Třída i <xref:System.Windows.Forms.Control> Třída mají `Top` vlastnost. Chcete-li získat nebo nastavit vzdálenost mezi horním okrajem ovládacího prvku a horním okrajem dokumentu, použijte <xref:Microsoft.Office.Tools.Excel.ControlSite.Top%2A> vlastnost <xref:Microsoft.Office.Tools.Excel.ControlSite> , nikoli <xref:System.Windows.Forms.Control.Top%2A> vlastnost <xref:System.Windows.Forms.Control> .

  [!code-vb[Trin_VstcoreProgrammingControlsExcel#3](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#3)]
  [!code-csharp[Trin_VstcoreProgrammingControlsExcel#3](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#3)]

## <a name="see-also"></a>Viz také
- [Ovládací prvky v dokumentech Office](../vsto/controls-on-office-documents.md)
- [Trvalé dynamické ovládací prvky v dokumentech Office](../vsto/persisting-dynamic-controls-in-office-documents.md)
- [Postupy: Přidání ovládacích prvků ListObject do listů](../vsto/how-to-add-listobject-controls-to-worksheets.md)
- [Postupy: Přidání ovládacích prvků NamedRange do listů](../vsto/how-to-add-namedrange-controls-to-worksheets.md)
- [Postupy: Přidání ovládacích prvků grafu do listů](../vsto/how-to-add-chart-controls-to-worksheets.md)
- [Postupy: Přidání ovládacích prvků obsahu do dokumentů aplikace Word](../vsto/how-to-add-content-controls-to-word-documents.md)
- [Postupy: Přidání ovládacích prvků záložek do dokumentů aplikace Word](../vsto/how-to-add-bookmark-controls-to-word-documents.md)
- [Přehled model Windows Formsch ovládacích prvků v dokumentech Office](../vsto/windows-forms-controls-on-office-documents-overview.md)
- [Postupy: Přidání ovládacích prvků model Windows Forms do dokumentů Office](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)
