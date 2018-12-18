---
title: 'Postupy: Přidání ovládacích prvků ListObject do listů'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ListObject control, adding to worksheets
- controls [Office development in Visual Studio], adding to worksheets
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 402e7f80ea208d714b31bd61e25b352494310487
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49949250"
---
# <a name="how-to-add-listobject-controls-to-worksheets"></a>Postupy: Přidání ovládacích prvků ListObject do listů
  Můžete přidat <xref:Microsoft.Office.Tools.Excel.ListObject> ovládacích prvků na list aplikace Microsoft Office Excel v době návrhu a za běhu v projektech na úrovni dokumentu.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 Můžete také přidat <xref:Microsoft.Office.Tools.Excel.ListObject> ovládacích prvků za běhu v doplňku VSTO projekty.  
  
 Toto téma popisuje následující úkoly:  
  
- [Přidání ovládacích prvků ListObject v době návrhu](#designtime)  
  
- [Přidání ovládacích prvků ListObject za běhu v projektu úrovni dokumentu](#runtimedoclevel)  
  
- [Přidání ovládacích prvků ListObject za běhu v projektu doplňku VSTO](#runtimeaddin)  
  
  Další informace o <xref:Microsoft.Office.Tools.Excel.ListObject> ovládacích prvků, naleznete v tématu [ListObject – ovládací prvek](../vsto/listobject-control.md).  
  
##  <a name="designtime"></a> Přidání ovládacích prvků ListObject v době návrhu  
 Existuje několik způsobů, jak přidat <xref:Microsoft.Office.Tools.Excel.ListObject> ovládacích prvků na list v projektu úrovni dokumentu v době návrhu: Z aplikace Excel v sadě Visual Studio **nástrojů**a od **zdroje dat** okna.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
### <a name="to-use-the-ribbon-in-excel"></a>Použít na pásu karet v Excelu  
  
1.  Na **vložit** kartě **tabulky** klikněte na možnost **tabulky**.  
  
2.  Vyberte buňku nebo buňky, které chcete zahrnout do seznamu a klikněte na tlačítko **OK**.  
  
#### <a name="to-use-the-toolbox"></a>Použití panelu nástrojů  
  
1.  Z **ovládací prvky Excelu** karty **nástrojů**, přetáhněte <xref:Microsoft.Office.Tools.Excel.ListObject> do listu.  
  
     **Přidat ovládací prvek ListObject** zobrazí se dialogové okno.  
  
2.  Vyberte buňku nebo buňky, které chcete zahrnout do seznamu a klikněte na tlačítko **OK**.  
  
     Pokud nechcete Ponecháme výchozí název, můžete změnit název v **vlastnosti** okna.  
  
#### <a name="to-use-the-data-sources-window"></a>Pokud chcete použít okno zdroje dat  
  
1.  Otevřít **zdroje dat** okna a vytvořte zdroj dat pro váš projekt. Další informace najdete v tématu [přidat nové připojení](../data-tools/add-new-connections.md).  
  
2.  Přetáhněte tabulku z **zdroje dat** okno do listu.  
  
     Vázaný na data <xref:Microsoft.Office.Tools.Excel.ListObject> ovládací prvek je přidán do listu. Další informace najdete v tématu [a datové vazby Windows Forms](/dotnet/framework/winforms/data-binding-and-windows-forms).  
  
##  <a name="runtimedoclevel"></a> Přidání ovládacích prvků ListObject za běhu v projektu úrovni dokumentu  
 Můžete přidat <xref:Microsoft.Office.Tools.Excel.ListObject> ovládací prvek dynamicky za běhu. To umožňuje vytvářet hostitelské ovládací prvky v reakci na události. Dynamicky vytvořený seznam objektů nejsou zachované v listu jako hostitele Určuje, kdy je uzavřen do listu. Další informace najdete v tématu [přidání ovládacích prvků do dokumentů Office za běhu](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
#### <a name="to-add-a-listobject-control-to-a-worksheet-programmatically"></a>Přidání ovládacího prvku ListObject do listu prostřednictvím kódu programu  
  
1.  V <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> obslužná rutina události `Sheet1`, vložte následující kód pro přidání <xref:Microsoft.Office.Tools.Excel.ListObject> ovládací prvek buňky **A1** prostřednictvím **A4**.  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#2](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#2)]
     [!code-vb[Trin_VstcoreHostControlsExcel#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#2)]  
  
##  <a name="runtimeaddin"></a> Přidání ovládacích prvků ListObject za běhu v projektu doplňku VSTO  
 Můžete přidat <xref:Microsoft.Office.Tools.Excel.ListObject> řízení prostřednictvím kódu programu k žádné otevřené listu v projektu doplňku VSTO. Dynamicky vytvořený seznam objektů nejsou zachované v listu jako hostování ovládacích prvků, když do listu se uloží a pak zavření. Další informace najdete v tématu [rozšíření Wordových dokumentů a Excelových sešitů v doplňcích VSTO za běhu](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
#### <a name="to-add-a-listobject-control-to-a-worksheet-programmatically"></a>Přidání ovládacího prvku ListObject do listu prostřednictvím kódu programu  
  
1.  Následující kód vygeneruje hostitelská položka worksheet, která je založená na open listu a potom přidá <xref:Microsoft.Office.Tools.Excel.ListObject> ovládací prvek buňky **A1** prostřednictvím **A4**.  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#8](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs#8)]
     [!code-vb[Trin_Excel_Dynamic_Controls#8](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb#8)]  
  
## <a name="see-also"></a>Viz také:  
 [Rozšíření dokumentů aplikace Word a sešitů aplikace Excel v doplňcích VSTO za běhu](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Ovládací prvky v dokumentech Office](../vsto/controls-on-office-documents.md)   
 [ListObject – ovládací prvek](../vsto/listobject-control.md)   
 [Automatizace aplikace Excel s použitím rozšířených objektů](../vsto/automating-excel-by-using-extended-objects.md)   
 [Přehled ovládacích prvků hostitele a hostitelské položky](../vsto/host-items-and-host-controls-overview.md)   
 [Postupy: Změna velikosti ovládacích prvků ListObject](../vsto/how-to-resize-listobject-controls.md)   
 [Vytvoření vazby dat k ovládacím prvkům v řešeních pro systém Office](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Programová omezení hostitelských položek a hostitelských ovládacích prvků](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  