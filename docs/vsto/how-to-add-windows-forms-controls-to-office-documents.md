---
title: 'Postupy: Přidání ovládacích prvků Windows forms do dokumentů Office'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office documents [Office development in Visual Studio, Windows Forms controls
- Windows Forms controls [Office development in Visual Studio], adding
- controls [Office development in Visual Studio], Windows Forms controls
- documents [Office development in Visual Studio], Windows Forms controls
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 7b5a6246a79d2d1f910b6ca39ce290f6c325dbe6
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49892750"
---
# <a name="how-to-add-windows-forms-controls-to-office-documents"></a>Postupy: Přidání ovládacích prvků Windows Forms do dokumentů Office
  Můžete přidat ovládací prvky Windows Forms pro Microsoft Office Excelu nebo dokumentů Microsoft Office Word v době návrhu v projektech na úrovni dokumentu. Za běhu můžete přidat ovládací prvky v přizpůsobeních na úrovni dokumentu a doplňky VSTO. Například můžete přidat <xref:Microsoft.Office.Tools.Excel.Controls.ComboBox> ovládací prvek do listu aplikace tak, aby uživatelé můžou vybrat ze seznamu možností.  
  
 [!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]  
  
 Toto téma popisuje následující úkoly:  
  
- [Přidání ovládacích prvků v době návrhu](#designtime)  
  
- [Přidání ovládacích prvků za běhu v projektech na úrovni dokumentu](#runtimedoclevel)  
  
- [Přidání ovládacích prvků za běhu v doplňcích VSTO](#runtimeaddin)  
  
  ![odkaz na video](../vsto/media/playvideo.gif "odkaz na video") související video ukázku naleznete v tématu [jak to: Přidání ovládacích prvků do dokumentu plochu za běhu?](http://go.microsoft.com/fwlink/?LinkId=132782).  
  
##  <a name="designtime"></a> Přidání ovládacích prvků v době návrhu  
 Existuje několik způsobů, jak přidat ovládací prvky Windows Forms do dokumentů v projektu úrovni dokumentu v době návrhu.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
### <a name="to-drag-a-windows-forms-control-to-the-document"></a>Přetáhněte ovládací prvek Windows Forms do dokumentu  
  
1.  Vytvořte nebo otevřete k projektu sešitu aplikace Excel nebo projektu dokumentu aplikace Word v sadě Visual Studio tak, aby dokument je zobrazen v návrháři. Informace o vytváření projektů, naleznete v tématu [postupy: vytvoření Office projekty v sadě Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
2.  V **běžné ovládací prvky** karty **nástrojů**, klepněte na ovládací prvek, který chcete přidat a přetáhněte ji do dokumentu.  
  
    > [!NOTE]  
    >  Když vyberete ovládací prvek v aplikaci Excel, zobrazí se **=EMBED("WinForms.Control.Host","")** v **řádek vzorců**. Tento text je nutné a by neměl být odstraněn.  
  
### <a name="to-draw-a-windows-forms-control-on-the-document"></a>Chcete-li nakreslit ovládacího prvku Windows Forms v dokumentu  
  
1.  Vytvořte nebo otevřete k projektu sešitu aplikace Excel nebo projektu dokumentu aplikace Word v sadě Visual Studio tak, aby dokument je zobrazen v návrháři. Informace o vytváření projektů, naleznete v tématu [postupy: vytvoření Office projekty v sadě Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
2.  V **běžné ovládací prvky** karty **nástrojů**, klepněte na ovládací prvek, který chcete přidat.  
  
3.  V dokumentu klikněte na požadované levého horního rohu ovládacího prvku na nalezen a přetáhněte na požadované místo pravého dolního rohu ovládacího prvku, který má být umístěná.  
  
     Ovládací prvek se přidá do dokumentu na zadaném umístění a velikost.  
  
    > [!NOTE]  
    >  Když vyberete ovládací prvek v aplikaci Excel, zobrazí se **=EMBED("WinForms.Control.Host","")** v **řádek vzorců**. Tento text je nutné a by neměl být odstraněn.  
  
### <a name="to-add-a-windows-forms-control-to-the-document-by-single-clicking-the-control"></a>Do dokumentu přidat ovládací prvek Windows Forms s jedním klepnutím na ovládací prvek  
  
1.  Vytvořte nebo otevřete k projektu sešitu aplikace Excel nebo projektu dokumentu aplikace Word v sadě Visual Studio tak, aby dokument je zobrazen v návrháři. Informace o vytváření projektů, naleznete v tématu [postupy: vytvoření Office projekty v sadě Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
2.  V **běžné ovládací prvky** karty **nástrojů**, klepněte na ovládací prvek, který chcete přidat  
  
3.  Jeden dokument, klikněte na tlačítko, kam chcete přidat ovládací prvek.  
  
     Ovládací prvek je přidán do dokumentu s výchozí velikostí.  
  
    > [!NOTE]  
    >  Když vyberete ovládací prvek v aplikaci Excel, zobrazí se **=EMBED("WinForms.Control.Host","")** v **řádek vzorců**. Tento text je nutné a by neměl být odstraněn.  
  
### <a name="to-add-a-windows-forms-control-to-the-document-by-double-clicking-the-control"></a>Přidání ovládacího prvku Windows Forms do dokumentů poklepáním na ovládací prvek  
  
1.  Vytvořte nebo otevřete k projektu sešitu aplikace Excel nebo projektu dokumentu aplikace Word v sadě Visual Studio tak, aby dokument je zobrazen v návrháři. Informace o vytváření projektů, naleznete v tématu [postupy: vytvoření Office projekty v sadě Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
2.  V **běžné ovládací prvky** karty **nástrojů**, poklepejte na ovládací prvek, který chcete přidat.  
  
     Ovládací prvek je přidán do dokumentu v centru dokumentu nebo aktivního podokna.  
  
    > [!NOTE]  
    >  Když vyberete ovládací prvek v aplikaci Excel, zobrazí se **=EMBED("WinForms.Control.Host","")** v **řádek vzorců**. Tento text je nutné a by neměl být odstraněn.  
  
### <a name="to-add-a-windows-forms-control-to-the-document-by-pressing-the-enter-key"></a>Přidání ovládacího prvku Windows Forms do dokumentů stisknutím klávesy Enter  
  
1.  Vytvořte nebo otevřete k projektu sešitu aplikace Excel nebo projektu dokumentu aplikace Word v sadě Visual Studio tak, aby dokument je zobrazen v návrháři. Informace o vytváření projektů, naleznete v tématu [postupy: vytváření projektů pro Office v sadě Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
2.  V **běžné ovládací prvky** karty **nástrojů**, klepněte na ovládací prvek, který chcete přidat a stiskněte klávesu **Enter** klíč.  
  
     Ovládací prvek je přidán do dokumentu v centru dokumentu nebo aktivního podokna.  
  
    > [!NOTE]  
    >  Když vyberete ovládací prvek v aplikaci Excel, zobrazí se **=EMBED("WinForms.Control.Host","")** v **řádek vzorců**. Tento text je nutné a by neměl být odstraněn.  
  
##  <a name="runtimedoclevel"></a> Přidání ovládacích prvků za běhu v projektech na úrovni dokumentu  
 Můžete programově přidat ovládací prvky Windows Forms do dokumentu za běhu. V aplikaci Word, použijte metody <xref:Microsoft.Office.Tools.Word.DocumentBase.Controls%2A> vlastnost `ThisDocument` třídy. V aplikaci Excel, použití metod pro posunutí <xref:Microsoft.Office.Tools.Excel.WorksheetBase.Controls%2A> vlastnost `Sheet` *n* třídy. Každá metoda má několik přetížení, která vám umožní určit umístění ovládacího prvku různými způsoby.  
  
 Při přidávání ovládacího prvku Windows Forms do dokumentů za běhu, ovládací prvek není trvalý v dokumentu, při zavření dokumentu. Můžete znovu vytvořit ovládací prvek při příštím otevření dokumentu. Další informace najdete v tématu [přidání ovládacích prvků do dokumentů Office za běhu](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
### <a name="to-add-a-windows-forms-control-at-runtime"></a>Přidání ovládacího prvku Windows Forms v době běhu  
  
1.  Použijte metodu, která má název přidat\<*třídu ovládacího prvku*> (kde *třídu ovládacího prvku* je název třídy ovládacího prvku Windows Forms, který chcete přidat, jako například <xref:Microsoft.Office.Tools.Word.ControlExtensions.AddButton%2A>).  
  
     Následující příklad kódu ukazuje, jak přidat <xref:Microsoft.Office.Tools.Excel.Controls.Button> do buňky **C5** z `Sheet1` v projektu úrovni dokumentu pro Excel.  
  
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#4](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#4)]
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#4](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#4)]  
  
##  <a name="runtimeaddin"></a> Přidání ovládacích prvků za běhu v doplňcích VSTO  
 Můžete přidat ovládací prvky Windows Forms prostřednictvím kódu programu do libovolného otevřeného dokumentu za běhu. Generovat položku hostitele, která je založená na open dokumentu nebo listu. Potom v aplikaci Word, použijte metody <xref:Microsoft.Office.Tools.Word.Document.Controls%2A> vlastnosti nové položky hostitele. V aplikaci Excel, použití metod pro posunutí <xref:Microsoft.Office.Tools.Excel.Worksheet.Controls%2A> vlastnosti nové položky hostitele. Každá metoda má několik přetížení, která vám umožní určit umístění ovládacího prvku různými způsoby.  
  
 Při přidávání ovládacího prvku Windows Forms do dokumentů za běhu, ovládací prvek není trvalý v dokumentu, při zavření dokumentu. Můžete znovu vytvořit ovládací prvek při příštím otevření dokumentu. Další informace najdete v tématu [přidání ovládacích prvků do dokumentů Office za běhu](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
 Další informace o generování hostitelských položkách v projekty doplňku VSTO v tématu [rozšíření Wordových dokumentů a Excelových sešitů v doplňcích VSTO za běhu](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
### <a name="to-add-a-windows-forms-control-at-runtime"></a>Přidání ovládacího prvku Windows Forms v době běhu  
  
1.  Použijte metodu, která má název přidat\<*třídu ovládacího prvku*> (kde *třídu ovládacího prvku* je název třídy ovládacího prvku Windows Forms, který chcete přidat, jako například <xref:Microsoft.Office.Tools.Word.ControlExtensions.AddButton%2A>).  
  
    > [!NOTE]  
    >  V doplňku VSTO projekty, které cílí [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] nebo novější, je třeba přidat odkaz na *Microsoft.Office.Tools.Excel.v4.0.Utilities.dll* nebo *Microsoft.Office.Tools.Word.v4.0.Utilities.dll* sestavení, abyste mohli přidat\<*třídu ovládacího prvku*> metody.  
  
     Následující příklad kódu ukazuje, jak přidat <xref:Microsoft.Office.Tools.Word.Controls.Button> do prvního odstavce aktivního dokumentu pomocí doplňku VSTO pro Word.  
  
     [!code-vb[Trin_WordAddInDynamicControls#7](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#7)]
     [!code-csharp[Trin_WordAddInDynamicControls#7](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#7)]  
  
## <a name="see-also"></a>Viz také:  
 [Ovládací prvky Windows Forms na dokumenty Office – přehled](../vsto/windows-forms-controls-on-office-documents-overview.md)   
 [Přidání ovládacích prvků do dokumentů Office za běhu](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Postupy: Změna velikosti ovládacích prvků v buňkách listu](../vsto/how-to-resize-controls-within-worksheet-cells.md)   
 [Přehled ovládacích prvků hostitele a hostitelské položky](../vsto/host-items-and-host-controls-overview.md)   
 [Volitelné parametry v řešeních pro systém Office](../vsto/optional-parameters-in-office-solutions.md)  
  