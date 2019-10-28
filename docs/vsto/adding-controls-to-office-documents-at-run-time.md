---
title: Přidání ovládacích prvků do dokumentů Office v době běhu
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
ms.openlocfilehash: 44bf1de5d550a264a63ba7293fe1bdc0c9630aee
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/28/2019
ms.locfileid: "72986326"
---
# <a name="add-controls-to-office-documents-at-run-time"></a>Přidání ovládacích prvků do dokumentů Office v době běhu
  Ovládací prvky lze přidat do systém Microsoft Office dokumentů aplikace Word a systém Microsoft Office excelový sešit v době běhu. Můžete je také odebrat v době běhu. Ovládací prvky, které přidáte nebo odeberete za běhu, se nazývají *dynamické ovládací prvky*.

 [!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]

 Toto téma popisuje následující:

- [Spravujte ovládací prvky v době běhu pomocí kolekcí ovládacích prvků](#ControlsCollection).

- [Přidejte do dokumentů ovládací prvky hostitele](#HostControls).

- [Přidejte model Windows Forms ovládací prvky do dokumentů](#WindowsForms).

## <a name="ControlsCollection"></a>Správa ovládacích prvků v době běhu pomocí kolekcí ovládacích prvků
 Chcete-li přidat, získat nebo odebrat ovládací prvky v době běhu, použijte pomocné metody objektů <xref:Microsoft.Office.Tools.Excel.ControlCollection> a <xref:Microsoft.Office.Tools.Word.ControlCollection>.

 Způsob, jakým přistupujete k těmto objektům, závisí na typu projektu, který vyvíjíte:

- V projektu na úrovni dokumentu pro aplikaci Excel použijte vlastnost <xref:Microsoft.Office.Tools.Excel.Worksheet.Controls%2A> třídy `Sheet1`, `Sheet2`a `Sheet3`. Další informace o těchto třídách naleznete v tématu [položka hostitele na listu](../vsto/worksheet-host-item.md).

- V projektu na úrovni dokumentu pro aplikaci Word použijte vlastnost <xref:Microsoft.Office.Tools.Word.Document.Controls%2A> třídy `ThisDocument`. Další informace o této třídě naleznete v tématu [položka hostitele dokumentu](../vsto/document-host-item.md).

- V projektu doplňku VSTO pro Excel nebo Word použijte vlastnost `Controls` <xref:Microsoft.Office.Tools.Excel.Worksheet> nebo <xref:Microsoft.Office.Tools.Word.Document> generované v době běhu. Další informace o generování těchto objektů v době běhu najdete v tématu [rozšiřování dokumentů aplikace Word a sešitů aplikace Excel v doplňcích VSTO za běhu](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).

### <a name="add-controls"></a>Přidat ovládací prvky
 Typy <xref:Microsoft.Office.Tools.Excel.ControlCollection> a <xref:Microsoft.Office.Tools.Word.ControlCollection> zahrnují pomocné metody, které lze použít k přidání hostitelských ovládacích prvků a běžných model Windows Forms ovládacích prvků do dokumentů a listů. Každý název metody má formát `Add`*třídy ovládacího prvku*, kde *Třída ovládacího prvku* je název třídy ovládacího prvku, který chcete přidat. Například pro přidání ovládacího prvku <xref:Microsoft.Office.Tools.Excel.NamedRange> do dokumentu použijte metodu <xref:Microsoft.Office.Tools.Excel.ControlCollection.AddNamedRange%2A>.

 Následující příklad kódu přidá <xref:Microsoft.Office.Tools.Excel.NamedRange> pro `Sheet1` v projektu na úrovni dokumentu pro aplikaci Excel.

 [!code-vb[Trin_ExcelWorkbookDynamicControls#3](../vsto/codesnippet/VisualBasic/trin_excelworkbookdynamiccontrols4/ThisWorkbook.vb#3)]
 [!code-csharp[Trin_ExcelWorkbookDynamicControls#3](../vsto/codesnippet/CSharp/trin_excelworkbookdynamiccontrols4/ThisWorkbook.cs#3)]

### <a name="access-and-delete-controls"></a>Ovládací prvky pro přístup a odstranění
 Můžete použít vlastnost `Controls` <xref:Microsoft.Office.Tools.Excel.Worksheet> nebo <xref:Microsoft.Office.Tools.Word.Document> k iterování všech ovládacích prvků v dokumentu, včetně ovládacích prvků, které jste přidali v době návrhu. Ovládací prvky, které přidáte v době návrhu, se nazývají také *statické ovládací prvky*.

 Dynamické ovládací prvky lze odebrat voláním metody `Delete` ovládacího prvku nebo voláním metody `Remove` každé kolekce ovládacích prvků. Následující příklad kódu používá metodu <xref:Microsoft.Office.Tools.Excel.ControlCollection.Remove%2A> k odebrání <xref:Microsoft.Office.Tools.Excel.NamedRange> z `Sheet1` v projektu na úrovni dokumentu v aplikaci Excel.

 [!code-vb[Trin_ExcelWorkbookDynamicControls#4](../vsto/codesnippet/VisualBasic/trin_excelworkbookdynamiccontrols4/ThisWorkbook.vb#4)]
 [!code-csharp[Trin_ExcelWorkbookDynamicControls#4](../vsto/codesnippet/CSharp/trin_excelworkbookdynamiccontrols4/ThisWorkbook.cs#4)]

 V době běhu nelze odebrat statické ovládací prvky. Pokud se pokusíte použít metodu `Delete` nebo `Remove` k odebrání statického ovládacího prvku, bude vyvolána <xref:Microsoft.Office.Tools.CannotRemoveControlException>.

> [!NOTE]
> Neodstraňujte programově ovládací prvky v `Shutdown` obslužné rutině události v dokumentu. Prvky uživatelského rozhraní dokumentu již nejsou k dispozici, když je vyvolána událost `Shutdown`. Chcete-li odebrat ovládací prvky před zavřením dokumentu, přidejte kód do obslužné rutiny události pro jinou událost, například <xref:Microsoft.Office.Tools.Word.Document.BeforeClose> nebo <xref:Microsoft.Office.Tools.Word.Document.BeforeSave> pro Word nebo <xref:Microsoft.Office.Tools.Excel.Workbook.BeforeClose>nebo <xref:Microsoft.Office.Tools.Excel.Workbook.BeforeSave> pro aplikaci Excel.

## <a name="HostControls"></a>Přidat do dokumentů ovládací prvky hostitele

Když programově přidáte ovládací prvky hostitele do dokumentů, je nutné zadat název, který jednoznačně identifikuje ovládací prvek, a musíte určit, kam chcete ovládací prvek přidat do dokumentu. Konkrétní pokyny najdete v následujících tématech:

- [Postupy: Přidání ovládacích prvků ListObject do listů](../vsto/how-to-add-listobject-controls-to-worksheets.md)

- [Postupy: Přidání ovládacích prvků NamedRange do listů](../vsto/how-to-add-namedrange-controls-to-worksheets.md)

- [Postupy: Přidání ovládacích prvků grafu do listů](../vsto/how-to-add-chart-controls-to-worksheets.md)

- [Postupy: Přidání ovládacích prvků obsahu do dokumentů aplikace Word](../vsto/how-to-add-content-controls-to-word-documents.md)

- [Postupy: Přidání ovládacích prvků záložek do dokumentů aplikace Word](../vsto/how-to-add-bookmark-controls-to-word-documents.md)

Další informace o hostitelských ovládacích prvcích naleznete v tématu Přehled hostitelských [položek a hostitelských ovládacích prvků](../vsto/host-items-and-host-controls-overview.md).

Když se dokument uloží a pak zavře, všechny dynamicky vytvořené hostitelské ovládací prvky se odpojí od jejich událostí a ztratí své funkce datových vazeb. Do svého řešení můžete přidat kód pro opětovné vytvoření hostitelského ovládacího prvku, když je dokument znovu otevřen. Další informace najdete v tématu [trvalé dynamické ovládací prvky v dokumentech Office](../vsto/persisting-dynamic-controls-in-office-documents.md).

> [!NOTE]
> Pomocné metody nejsou k dispozici pro následující hostitelské ovládací prvky, protože tyto ovládací prvky nelze programově přidat do dokumentů: <xref:Microsoft.Office.Tools.Excel.XmlMappedRange>, <xref:Microsoft.Office.Tools.Word.XMLNode>a <xref:Microsoft.Office.Tools.Word.XMLNodes>.

## <a name="WindowsForms"></a>Přidání ovládacích prvků model Windows Forms do dokumentů
 Když programově přidáte model Windows Forms ovládací prvek do dokumentu, je nutné zadat umístění ovládacího prvku a název, který jednoznačně identifikuje ovládací prvek. [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] poskytuje pomocné metody pro každý ovládací prvek. Tyto metody jsou přetíženy, takže můžete předat buď rozsah, nebo konkrétní souřadnice pro umístění ovládacího prvku.

 Když se dokument uloží a pak zavře, všechny dynamicky vytvořené model Windows Forms ovládací prvky se z dokumentu odeberou. Do svého řešení můžete přidat kód, aby bylo možné znovu vytvořit ovládací prvky při opětovném otevření dokumentu. Pokud vytvoříte dynamické model Windows Forms ovládací prvky pomocí doplňku VSTO, budou v dokumentu ponechány obálky ActiveX pro ovládací prvky. Další informace najdete v tématu [trvalé dynamické ovládací prvky v dokumentech Office](../vsto/persisting-dynamic-controls-in-office-documents.md).

> [!NOTE]
> Ovládací prvky model Windows Forms nelze programově přidat do chráněných dokumentů. Pokud programově zrušíte ochranu dokumentu aplikace Word nebo listu aplikace Excel pro přidání ovládacího prvku, je nutné zapsat další kód, který odebere obálku ActiveX ovládacího prvku při zavření dokumentu. Obálka ActiveX ovládacího prvku není automaticky odstraněna z chráněných dokumentů.

### <a name="add-custom-controls"></a>Přidání vlastních ovládacích prvků
 Chcete-li přidat <xref:System.Windows.Forms.Control>, který není podporován dostupnými podpůrnými metodami, jako je například vlastní uživatelský ovládací prvek, použijte následující metody:

- V Excelu použijte jednu z <xref:Microsoft.Office.Tools.Excel.ControlCollection.AddControl%2A> metod objektu <xref:Microsoft.Office.Tools.Excel.ControlCollection>.

- V případě aplikace Word použijte jednu z <xref:Microsoft.Office.Tools.Word.ControlCollection.AddControl%2A> metod objektu <xref:Microsoft.Office.Tools.Word.ControlCollection>.

  Chcete-li přidat ovládací prvek, předejte <xref:System.Windows.Forms.Control>, umístění ovládacího prvku a název, který jednoznačně identifikuje ovládací prvek `AddControl` metody. Metoda `AddControl` vrátí objekt, který definuje, jak ovládací prvek komunikuje s listem nebo dokumentem. Metoda `AddControl` vrátí <xref:Microsoft.Office.Tools.Excel.ControlSite> (pro Excel) nebo objekt <xref:Microsoft.Office.Tools.Word.ControlSite> (pro Word).

  Následující příklad kódu ukazuje, jak použít metodu <xref:Microsoft.Office.Tools.Excel.ControlCollection.AddControl%2A> k dynamickému Přidání vlastního uživatelského ovládacího prvku do listu v projektu aplikace Excel na úrovni dokumentu. V tomto příkladu je uživatelský ovládací prvek pojmenován `UserControl1`a <xref:Microsoft.Office.Interop.Excel.Range> má název `range1`. Chcete-li použít tento příklad, spusťte jej z `Sheet`*n* třídy v projektu.

  [!code-vb[Trin_VstcoreProgrammingControlsExcel#2](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#2)]
  [!code-csharp[Trin_VstcoreProgrammingControlsExcel#2](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#2)]

### <a name="use-members-of-custom-controls"></a>Použití členů vlastních ovládacích prvků
 Po použití jedné z metod `AddControl` pro přidání ovládacího prvku do listu nebo dokumentu máte nyní dva různé objekty ovládacích prvků:

- <xref:System.Windows.Forms.Control>, který představuje vlastní ovládací prvek.

- Objekt `ControlSite`, `OLEObject`nebo `OLEControl`, který představuje ovládací prvek po jeho přidání do listu nebo dokumentu.

  Mezi těmito ovládacími prvky se sdílí mnoho vlastností a metod. Je důležité, abyste měli přístup k těmto členům prostřednictvím příslušného ovládacího prvku:

- Pro přístup ke členům, kteří patří pouze do vlastního ovládacího prvku, použijte <xref:System.Windows.Forms.Control>.

- Chcete-li získat přístup ke členům, které jsou sdíleny ovládacími prvky, použijte objekt `ControlSite`, `OLEObject`nebo `OLEControl`.

  Pokud ke sdílenému členu přistupujete z <xref:System.Windows.Forms.Control>, může to selhat bez upozornění nebo oznámení nebo může způsobit neplatné výsledky. Vždy používejte metody nebo vlastnosti objektu `ControlSite`, `OLEObject`nebo `OLEControl`, pokud není požadovaná metoda nebo vlastnost k dispozici; pak byste měli odkazovat na <xref:System.Windows.Forms.Control>.

  Například třída <xref:Microsoft.Office.Tools.Excel.ControlSite> i třída <xref:System.Windows.Forms.Control> mají vlastnost `Top`. Chcete-li získat nebo nastavit vzdálenost mezi horním okrajem ovládacího prvku a horním okrajem dokumentu, použijte vlastnost <xref:Microsoft.Office.Tools.Excel.ControlSite.Top%2A> <xref:Microsoft.Office.Tools.Excel.ControlSite>, nikoli vlastnost <xref:System.Windows.Forms.Control.Top%2A> <xref:System.Windows.Forms.Control>.

  [!code-vb[Trin_VstcoreProgrammingControlsExcel#3](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#3)]
  [!code-csharp[Trin_VstcoreProgrammingControlsExcel#3](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#3)]

## <a name="see-also"></a>Viz také:
- [Ovládací prvky v dokumentech Office](../vsto/controls-on-office-documents.md)
- [Trvalé dynamické ovládací prvky v dokumentech Office](../vsto/persisting-dynamic-controls-in-office-documents.md)
- [Postupy: Přidání ovládacích prvků ListObject do listů](../vsto/how-to-add-listobject-controls-to-worksheets.md)
- [Postupy: Přidání ovládacích prvků NamedRange do listů](../vsto/how-to-add-namedrange-controls-to-worksheets.md)
- [Postupy: Přidání ovládacích prvků grafu do listů](../vsto/how-to-add-chart-controls-to-worksheets.md)
- [Postupy: Přidání ovládacích prvků obsahu do dokumentů aplikace Word](../vsto/how-to-add-content-controls-to-word-documents.md)
- [Postupy: Přidání ovládacích prvků záložek do dokumentů aplikace Word](../vsto/how-to-add-bookmark-controls-to-word-documents.md)
- [Přehled model Windows Formsch ovládacích prvků v dokumentech Office](../vsto/windows-forms-controls-on-office-documents-overview.md)
- [Postupy: Přidání ovládacích prvků model Windows Forms do dokumentů Office](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)
