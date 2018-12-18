---
title: Přidání ovládacích prvků do dokumentů Office za běhu
ms.custom: ''
ms.date: 02/02/2017
ms.technology: office-development
ms.prod: visual-studio-dev15
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office documents [Office development in Visual Studio, Windows Forms controls
- host controls [Office development in Visual Studio], adding
- Windows Forms controls [Office development in Visual Studio], adding
- Office documents [Office development in Visual Studio, host controls
- user controls [Office development in Visual Studio], adding at runtime
- documents [Office development in Visual Studio], Windows Forms controls
- document-level customizations [Office development in Visual Studio], host controls
- documents [Office development in Visual Studio], host controls
- document-level customizations [Office development in Visual Studio], Windows Forms controls
- controls [Office development in Visual Studio], adding at runtime
- helper methods [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: 2ad16bc414e6d67b563240bcd2bceb15e9c34e97
ms.sourcegitcommit: 81e9d90843ead658bc73b30c869f25921d99e116
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/26/2018
ms.locfileid: "52305634"
---
# <a name="add-controls-to-office-documents-at-runtime"></a>Přidání ovládacích prvků do dokumentů Office za běhu
  Můžete přidat ovládací prvky do dokumentu Microsoft Office Word a sešit aplikace Microsoft Office Excel za běhu. Můžete také odebrat je za běhu. Ovládací prvky, které můžete přidat nebo odebrat za běhu se nazývají *dynamické ovládací prvky*.  

 [!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]  

 Toto téma popisuje následující:  

- [Spravovat ovládacích prvků za běhu pomocí kolekce ovládacích prvků](#ControlsCollection).  

- [Přidání hostitelských ovládacích prvků do dokumentů](#HostControls).  

- [Přidání ovládacích prvků Windows Forms do dokumentů](#WindowsForms).  

  ![odkaz na video](../vsto/media/playvideo.gif "odkaz na video") související video ukázku naleznete v tématu [jak to: Přidání ovládacích prvků do dokumentu plochu za běhu?](http://go.microsoft.com/fwlink/?LinkId=132782).  

##  <a name="ControlsCollection"></a> Spravovat ovládacích prvků za běhu pomocí kolekce ovládacích prvků  
 Pokud chcete přidat, získat nebo odebrání ovládacích prvků za běhu, použijte pomocné metody <xref:Microsoft.Office.Tools.Excel.ControlCollection> a <xref:Microsoft.Office.Tools.Word.ControlCollection> objekty.  

 Přístup k těmto objektům způsob závisí na typu projektu, který vyvíjíte:  

-   V projektu na úrovni dokumentu pro Excel, použijte <xref:Microsoft.Office.Tools.Excel.Worksheet.Controls%2A> vlastnost `Sheet1`, `Sheet2`, a `Sheet3` třídy. Další informace o těchto tříd naleznete v tématu [hostitelská položka Worksheet](../vsto/worksheet-host-item.md).  

-   V projektu na úrovni dokumentu pro Word, použijte <xref:Microsoft.Office.Tools.Word.Document.Controls%2A> vlastnost `ThisDocument` třídy. Další informace o této třídy najdete v tématu [hostitelská položka Document](../vsto/document-host-item.md).  

-   V projekt doplňku VSTO pro Excel nebo Word použít `Controls` vlastnost <xref:Microsoft.Office.Tools.Excel.Worksheet> nebo <xref:Microsoft.Office.Tools.Word.Document> , který vygenerujete v době běhu. Další informace o generování těchto objektů za běhu, naleznete v tématu [rozšíření Wordových dokumentů a Excelových sešitů v doplňcích VSTO za běhu](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  

### <a name="add-controls"></a>Přidání ovládacích prvků  
 <xref:Microsoft.Office.Tools.Excel.ControlCollection> a <xref:Microsoft.Office.Tools.Word.ControlCollection> typy zahrnují pomocné metody, které vám umožní přidat hostitelské ovládací prvky a běžných ovládacích prvků Windows Forms do dokumentů a listy nástroje. Každý název metody má formát `Add` *třídu ovládacího prvku*, kde *třídu ovládacího prvku* je název třídy ovládacího prvku, který chcete přidat. Například, chcete-li přidat <xref:Microsoft.Office.Tools.Excel.NamedRange> ovládacího prvku do dokumentu, použijte <xref:Microsoft.Office.Tools.Excel.ControlCollection.AddNamedRange%2A> metody.  

 Následující příklad kódu přidá <xref:Microsoft.Office.Tools.Excel.NamedRange> k `Sheet1` v projektu úrovni dokumentu pro Excel.  

 [!code-vb[Trin_ExcelWorkbookDynamicControls#3](../vsto/codesnippet/VisualBasic/trin_excelworkbookdynamiccontrols4/ThisWorkbook.vb#3)]
 [!code-csharp[Trin_ExcelWorkbookDynamicControls#3](../vsto/codesnippet/CSharp/trin_excelworkbookdynamiccontrols4/ThisWorkbook.cs#3)]  

### <a name="access-and-delete-controls"></a>Ovládacích prvků přístupu a delete  
 Můžete použít `Controls` vlastnost <xref:Microsoft.Office.Tools.Excel.Worksheet> nebo <xref:Microsoft.Office.Tools.Word.Document> iterovat přes všechny ovládací prvky v dokumentu, včetně ovládacích prvků přidaných v době návrhu. Ovládací prvky, které můžete přidat v době návrhu se také označují jako *statické ovládací prvky*.  

 Dynamické ovládací prvky můžete odebrat pomocí volání `Delete` ovládacího prvku, nebo pomocí volání metody `Remove` metoda každou kolekci ovládacích prvků. Následující příklad kódu používá <xref:Microsoft.Office.Tools.Excel.ControlCollection.Remove%2A> metoda odebrání <xref:Microsoft.Office.Tools.Excel.NamedRange> z `Sheet1` v projektu úrovni dokumentu pro Excel.  

 [!code-vb[Trin_ExcelWorkbookDynamicControls#4](../vsto/codesnippet/VisualBasic/trin_excelworkbookdynamiccontrols4/ThisWorkbook.vb#4)]
 [!code-csharp[Trin_ExcelWorkbookDynamicControls#4](../vsto/codesnippet/CSharp/trin_excelworkbookdynamiccontrols4/ThisWorkbook.cs#4)]  

 Nelze odebrat statické ovládací prvky za běhu. Pokud se pokusíte použít `Delete` nebo `Remove` metoda odebrání statický ovládací prvek <xref:Microsoft.Office.Tools.CannotRemoveControlException> bude vyvolána výjimka.  

> [!NOTE]  
>  Neodebírejte programově ovládacích prvků v `Shutdown` obslužná rutina události dokumentu. Prvky uživatelského rozhraní dokumentu již nejsou k dispozici při `Shutdown` událost se vyvolá. Pokud chcete odebrat ovládací prvky před zavřením dokumentu, přidejte svůj kód obslužné rutiny události pro jiné události, jako například <xref:Microsoft.Office.Tools.Word.Document.BeforeClose> nebo <xref:Microsoft.Office.Tools.Word.Document.BeforeSave> pro Word, nebo <xref:Microsoft.Office.Tools.Excel.Workbook.BeforeClose>, nebo <xref:Microsoft.Office.Tools.Excel.Workbook.BeforeSave> pro aplikaci Excel.  

##  <a name="HostControls"></a> Přidání hostitelských ovládacích prvků do dokumentů  
 Když přidáte do dokumentů prostřednictvím kódu programu hostitelské ovládací prvky je nutné zadat název, který jednoznačně identifikuje ovládací prvek a musíte určit, kde chcete-li přidat ovládací prvek v dokumentu. Konkrétní pokyny naleznete v následujících tématech:  

- [Postupy: Přidání ovládacích prvků ListObject do listů](../vsto/how-to-add-listobject-controls-to-worksheets.md)  

- [Postupy: Přidání ovládacích prvků NamedRange do listů](../vsto/how-to-add-namedrange-controls-to-worksheets.md)  

- [Postupy: Přidání ovládacích prvků graf do listů](../vsto/how-to-add-chart-controls-to-worksheets.md)  

- [Postupy: Přidání obsahu ovládacích prvků do dokumentů aplikace Word](../vsto/how-to-add-content-controls-to-word-documents.md)  

- [Postupy: Přidání ovládacích prvků záložek do dokumentů aplikace Word](../vsto/how-to-add-bookmark-controls-to-word-documents.md)  

  Další informace o hostitelských ovládacích prvcích najdete v tématu [hostovat položky a hostujte Přehled ovládacích prvků](../vsto/host-items-and-host-controls-overview.md).  

  Po uložení a pak zavření dokumentu z jejich události jsou odpojené všechny dynamicky generovaný hostitelské ovládací prvky a mohly být ztraceny jejich data vazbu funkce. Přidejte kód do svého řešení k opětovnému vytvoření hostitelské ovládací prvky, když znovu otevřete dokument. Další informace najdete v tématu [uchování dynamických ovládacích prvků v dokumentech systému Office](../vsto/persisting-dynamic-controls-in-office-documents.md).  

> [!NOTE]  
>  Nejsou zadány pomocné metody pro následující hostování ovládacích prvků, protože tyto ovládací prvky nemohou být přidány do dokumentů prostřednictvím kódu programu: <xref:Microsoft.Office.Tools.Excel.XmlMappedRange>, <xref:Microsoft.Office.Tools.Word.XMLNode>, a <xref:Microsoft.Office.Tools.Word.XMLNodes>.  

##  <a name="WindowsForms"></a> Přidání ovládacích prvků Windows Forms do dokumentů  
 Při přidávání ovládacího prvku Windows Forms se prostřednictvím kódu programu k dokumentu, je nutné zadat umístění ovládacího prvku a název, který jednoznačně identifikuje ovládací prvek. [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] Poskytuje pomocné metody pro každý ovládací prvek. Tyto metody jsou přetěžované, takže můžete předat rozsah nebo konkrétní souřadnice pro umístění ovládacího prvku.  

 Po uložení a pak zavření dokumentu, se odeberou všechny dynamicky vytvořený ovládací prvky Windows Forms z dokumentu. Přidejte kód do svého řešení k opětovnému vytvoření ovládacích prvků, když znovu otevřete dokument. Pokud vytvoříte dynamické ovládací prvky Windows Forms pomocí doplňku VSTO, jsou ponechána obálky ActiveX pro ovládací prvky v dokumentu. Další informace najdete v tématu [uchování dynamických ovládacích prvků v dokumentech systému Office](../vsto/persisting-dynamic-controls-in-office-documents.md).  

> [!NOTE]  
>  Ovládací prvky Windows Forms nelze přidat do chráněných dokumentů prostřednictvím kódu programu. Je-li programově odemknout Wordového dokumentu nebo listu aplikace Excel k přidání ovládacího prvku, musíte napsat další kód a odeberte obálky ovládacího prvku ActiveX při zavření dokumentu. Obálky ovládacího prvku ActiveX není automaticky odstraněn z chráněných dokumentů.  

### <a name="add-custom-controls"></a>Přidání vlastních ovládacích prvků  
 Pokud chcete přidat <xref:System.Windows.Forms.Control> , která není podporována k dispozici pomocné metody, jako jsou vlastní uživatelský ovládací prvek, pomocí následujících metod:  

- Pro aplikaci Excel, použijte jednu z <xref:Microsoft.Office.Tools.Excel.ControlCollection.AddControl%2A> metody <xref:Microsoft.Office.Tools.Excel.ControlCollection> objektu.  

- Pro Word, použijte jednu z <xref:Microsoft.Office.Tools.Word.ControlCollection.AddControl%2A> metody <xref:Microsoft.Office.Tools.Word.ControlCollection> objektu.  

  Chcete-li přidat ovládací prvek, předejte <xref:System.Windows.Forms.Control>, umístění pro ovládací prvek a s názvem, který jednoznačně identifikuje ovládací prvek `AddControl` metoda. `AddControl` Metoda vrátí objekt, který definuje, jak ovládací prvek komunikuje s listem nebo dokumentu. `AddControl` Metoda vrátí hodnotu <xref:Microsoft.Office.Tools.Excel.ControlSite> (pro aplikace Excel) nebo <xref:Microsoft.Office.Tools.Word.ControlSite> objektu (pro aplikaci Word).  

  Následující příklad kódu ukazuje, jak používat <xref:Microsoft.Office.Tools.Excel.ControlCollection.AddControl%2A> způsob, jak dynamicky přidat vlastní uživatelský ovládací prvek do listu v projektu aplikace Excel úrovni dokumentu. V tomto příkladu je název uživatelského ovládacího prvku `UserControl1`a <xref:Microsoft.Office.Interop.Excel.Range> jmenuje `range1`. Pokud chcete použít tento příklad, spusťte jej z `Sheet` *n* třídy v projektu.  

  [!code-vb[Trin_VstcoreProgrammingControlsExcel#2](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#2)]
  [!code-csharp[Trin_VstcoreProgrammingControlsExcel#2](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#2)]  

### <a name="use-members-of-custom-controls"></a>Použití vlastních ovládacích prvků členů  
 Po použití jedné z `AddControl` metody pro přidání ovládacího prvku na listu nebo dokumentu, můžete teď mít dva objekty jiného ovládacího prvku:  

- <xref:System.Windows.Forms.Control> , Který představuje vlastní ovládací prvek.  

- `ControlSite`, `OLEObject`, Nebo `OLEControl` objekt, který představuje ovládací prvek po byl přidán do listu nebo dokumentu.  

  Mnoho vlastností a metod jsou sdíleny mezi těmito ovládacími prvky. Je důležité, že tyto členy přistupujete prostřednictvím příslušný ovládací prvek:  

- Chcete-li přístup ke členům, které patří pouze do vlastního ovládacího prvku, použijte <xref:System.Windows.Forms.Control>.  

- Chcete-li přístup ke členům, které jsou sdíleny ovládací prvky, použijte `ControlSite`, `OLEObject`, nebo `OLEControl` objektu.  

  Pokud přistupujete ke sdílenému členu z <xref:System.Windows.Forms.Control>, může selhat bez upozornění a oznámení, nebo může vytvořit neplatný výsledky. Vždy použít metody nebo vlastnosti `ControlSite`, `OLEObject`, nebo `OLEControl` objekt Pokud potřebujete metoda nebo vlastnost není k dispozici, teprve pak by vám odkaz <xref:System.Windows.Forms.Control>.  

  Například i <xref:Microsoft.Office.Tools.Excel.ControlSite> třídy a <xref:System.Windows.Forms.Control> třídy `Top` vlastnost. Chcete-li získat nebo nastavit vzdálenost mezi horní části ovládacího prvku a horním okrajem dokumentu, použijte <xref:Microsoft.Office.Tools.Excel.ControlSite.Top%2A> vlastnost <xref:Microsoft.Office.Tools.Excel.ControlSite>, nikoli <xref:System.Windows.Forms.Control.Top%2A> vlastnost <xref:System.Windows.Forms.Control>.  

  [!code-vb[Trin_VstcoreProgrammingControlsExcel#3](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#3)]
  [!code-csharp[Trin_VstcoreProgrammingControlsExcel#3](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#3)]  

## <a name="see-also"></a>Viz také:  
 [Ovládací prvky v dokumentech Office](../vsto/controls-on-office-documents.md)   
 [Uchování dynamických ovládacích prvků v dokumentech Office](../vsto/persisting-dynamic-controls-in-office-documents.md)   
 [Postupy: Přidání ovládacích prvků ListObject do listů](../vsto/how-to-add-listobject-controls-to-worksheets.md)   
 [Postupy: Přidání ovládacích prvků NamedRange do listů](../vsto/how-to-add-namedrange-controls-to-worksheets.md)   
 [Postupy: Přidání ovládacích prvků graf do listů](../vsto/how-to-add-chart-controls-to-worksheets.md)   
 [Postupy: Přidání ovládacích prvků obsahu do dokumentů aplikace Word](../vsto/how-to-add-content-controls-to-word-documents.md)   
 [Postupy: Přidání ovládacích prvků záložek do dokumentů aplikace Word](../vsto/how-to-add-bookmark-controls-to-word-documents.md)   
 [Ovládací prvky Windows Forms na dokumenty Office – přehled](../vsto/windows-forms-controls-on-office-documents-overview.md)   
 [Postupy: Přidání ovládacích prvků Windows Forms do dokumentů Office](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)   
