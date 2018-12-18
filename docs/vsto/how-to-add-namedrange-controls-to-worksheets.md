---
title: 'Postupy: Přidání ovládacích prvků NamedRange do listů'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ranges, adding to worksheets
- NamedRange control, adding to worksheets
- controls [Office development in Visual Studio], adding to worksheets
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 35febfa4c4d13b3f5d3d279f7d1c35e96051d54b
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49867114"
---
# <a name="how-to-add-namedrange-controls-to-worksheets"></a>Postupy: Přidání ovládacích prvků NamedRange do listů
  Můžete přidat <xref:Microsoft.Office.Tools.Excel.NamedRange> ovládacích prvků na list aplikace Microsoft Office Excel v době návrhu a za běhu v projektech na úrovni dokumentu.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 Můžete také přidat <xref:Microsoft.Office.Tools.Excel.NamedRange> ovládacích prvků za běhu v doplňku VSTO projekty.  
  
 Toto téma popisuje následující úkoly:  
  
- [Přidání ovládacích prvků NamedRange v době návrhu](#designtime)  
  
- [Přidání ovládacích prvků NamedRange za běhu v projektu úrovni dokumentu](#runtimedoclevel)  
  
- [Přidání ovládacích prvků NamedRange za běhu v projektu doplňku VSTO](#runtimeaddin)  
  
  Další informace o <xref:Microsoft.Office.Tools.Excel.NamedRange> ovládacích prvků, naleznete v tématu [namedrange – ovládací prvek](../vsto/namedrange-control.md).  
  
##  <a name="designtime"></a> Přidání ovládacích prvků NamedRange v době návrhu  
 Existuje několik způsobů, jak přidat <xref:Microsoft.Office.Tools.Excel.NamedRange> ovládacích prvků na list v projektu úrovni dokumentu v době návrhu: z aplikace Excel v sadě Visual Studio **nástrojů**a od **zdroje dat** okna.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
### <a name="to-add-a-namedrange-control-to-a-worksheet-using-the-name-box-in-excel"></a>Chcete-li přidat namedrange – ovládací prvek na listu s použitím pole názvu v aplikaci Excel  
  
1.  Vyberte buňku nebo buňky, které chcete zahrnout v pojmenovaném rozsahu.  
  
2.  V **pole název**, zadejte název rozsahu a stiskněte klávesu **Enter**.  
  
     **Pole název** se nachází vedle řádku vzorců nad sloupci **A** listu.  
  
### <a name="to-add-a-namedrange-control-to-a-worksheet-using-the-toolbox"></a>Přidání ovládacího prvku NamedRange do listu pomocí panelu nástrojů  
  
1.  Otevřít **nástrojů** a klikněte na tlačítko **ovládací prvky Excelu** kartu.  
  
2.  Klikněte na tlačítko <xref:Microsoft.Office.Tools.Excel.NamedRange> a přetáhněte ji do listu.  
  
     **Přidat pojmenované rozsah** zobrazí se dialogové okno.  
  
3.  Vyberte buňku nebo buňky, které chcete zahrnout v pojmenovaném rozsahu.  
  
4.  Klikněte na tlačítko **OK**.  
  
     Pokud nechcete, aby výchozí název, který je přiřazen do ovládacího prvku, můžete změnit název v **vlastnosti** okna.  
  
### <a name="to-add-a-namedrange-control-to-a-worksheet-using-the-data-sources-window"></a>Přidání ovládacího prvku NamedRange do listu pomocí okna zdrojů dat  
  
1.  Otevřít **zdroje dat** okna a vytvořte zdroj dat pro váš projekt. Další informace najdete v tématu [přidat nové připojení](../data-tools/add-new-connections.md).  
  
2.  Přetáhněte jedno pole z **zdroje dat** okno do listu.  
  
     Vázaný na data <xref:Microsoft.Office.Tools.Excel.NamedRange> ovládací prvek je přidán do listu. Další informace najdete v tématu [a datové vazby Windows Forms](/dotnet/framework/winforms/data-binding-and-windows-forms).  
  
##  <a name="runtimedoclevel"></a> Přidání ovládacích prvků NamedRange za běhu v projektu úrovni dokumentu  
 Můžete přidat <xref:Microsoft.Office.Tools.Excel.NamedRange> řízení prostřednictvím kódu programu na list za běhu. To umožňuje vytvářet hostitelské ovládací prvky v reakci na události. Dynamicky generovaný pojmenované oblasti nejsou zachované v listu jako hostitele Určuje, kdy je uzavřen do listu. Další informace najdete v tématu [přidání ovládacích prvků do dokumentů Office za běhu](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
### <a name="to-add-a-namedrange-control-to-a-worksheet-programmatically"></a>Přidání ovládacího prvku NamedRange do listu prostřednictvím kódu programu  
  
1.  V <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> obslužná rutina události `Sheet1`, vložte následující kód pro přidání <xref:Microsoft.Office.Tools.Excel.NamedRange> ovládacího prvku do buňky **A1** a nastavte jeho <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> vlastnost `Hello world!`  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#3](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#3)]
     [!code-vb[Trin_VstcoreHostControlsExcel#3](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#3)]  
  
##  <a name="runtimeaddin"></a> Přidání ovládacích prvků NamedRange za běhu v projektu doplňku VSTO  
 Můžete přidat <xref:Microsoft.Office.Tools.Excel.NamedRange> řízení prostřednictvím kódu programu k žádné otevřené listu v projektu doplňku VSTO. Dynamicky generovaný pojmenované oblasti nejsou zachované v listu jako hostitele Určuje, kdy je uzavřen do listu. Další informace najdete v tématu [rozšíření Wordových dokumentů a Excelových sešitů v doplňcích VSTO za běhu](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
### <a name="to-add-a-namedrange-control-to-a-worksheet-programmatically"></a>Přidání ovládacího prvku NamedRange do listu prostřednictvím kódu programu  
  
1.  Následující kód vygeneruje hostitelská položka worksheet, která je založená na open listu a potom přidá <xref:Microsoft.Office.Tools.Excel.NamedRange> ovládacího prvku do buňky **A1** a nastaví její <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> vlastnost `Hello world`.  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#7](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs#7)]
     [!code-vb[Trin_Excel_Dynamic_Controls#7](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb#7)]  
  
## <a name="see-also"></a>Viz také:  
 [Rozšíření dokumentů aplikace Word a sešitů aplikace Excel v doplňcích VSTO za běhu](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Ovládací prvky v dokumentech Office](../vsto/controls-on-office-documents.md)   
 [Namedrange – ovládací prvek](../vsto/namedrange-control.md)   
 [Automatizace aplikace Excel s použitím rozšířených objektů](../vsto/automating-excel-by-using-extended-objects.md)   
 [Přehled ovládacích prvků hostitele a hostitelské položky](../vsto/host-items-and-host-controls-overview.md)   
 [Postupy: Změna velikosti ovládacích prvků NamedRange](../vsto/how-to-resize-namedrange-controls.md)   
 [Programová omezení hostitelských položek a hostitelských ovládacích prvků](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  