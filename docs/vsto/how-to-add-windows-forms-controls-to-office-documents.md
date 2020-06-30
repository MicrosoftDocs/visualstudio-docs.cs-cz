---
title: 'Postupy: Přidání ovládacích prvků Windows Forms do dokumentů Office'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office documents [Office development in Visual Studio, Windows Forms controls
- Windows Forms controls [Office development in Visual Studio], adding
- controls [Office development in Visual Studio], Windows Forms controls
- documents [Office development in Visual Studio], Windows Forms controls
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: b12d51ffe3a2e647a067b95d320e8beb70cac384
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/30/2020
ms.locfileid: "85547534"
---
# <a name="how-to-add-windows-forms-controls-to-office-documents"></a>Postupy: Přidání ovládacích prvků model Windows Forms do dokumentů Office
  Můžete přidat model Windows Forms ovládací prvky pro systém Microsoft Office Excelu a systém Microsoft Office wordové dokumenty v době návrhu v projektech na úrovni dokumentu. V době běhu můžete přidat ovládací prvky v přizpůsobení na úrovni dokumentu a v Doplňkech VSTO. Můžete například přidat <xref:Microsoft.Office.Tools.Excel.Controls.ComboBox> ovládací prvek do listu, aby si uživatelé mohli vybrat ze seznamu možností.

 [!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]

 V tomto tématu jsou popsány následující úlohy:

- [Přidat ovládací prvky v době návrhu](#designtime)

- [Přidat ovládací prvky za běhu v projektech na úrovni dokumentu](#runtimedoclevel)

- [Přidání ovládacích prvků v době běhu v doplňcích VSTO](#runtimeaddin)

## <a name="add-controls-at-design-time"></a><a name="designtime"></a>Přidat ovládací prvky v době návrhu
 Existuje několik způsobů, jak přidat model Windows Forms ovládací prvky do dokumentu v projektu na úrovni dokumentu v době návrhu.

 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

### <a name="to-drag-a-windows-forms-control-to-the-document"></a>Postup přetažení ovládacího prvku model Windows Forms do dokumentu

1. V aplikaci Visual Studio vytvořte nebo otevřete projekt sešitu aplikace Excel nebo projekt wordového dokumentu tak, aby byl dokument viditelný v návrháři. Informace o vytváření projektů naleznete v tématu [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

2. Na kartě **běžné ovládací prvky** **panelu nástrojů**klikněte na ovládací prvek, který chcete přidat, a přetáhněte ho do dokumentu.

    > [!NOTE]
    > Když vyberete ovládací prvek v aplikaci Excel, zobrazí se na **řádku vzorců** **= vložení ("WinForms. Control. host", ")** . Tento text je nezbytný a neměl by být odstraněn.

### <a name="to-draw-a-windows-forms-control-on-the-document"></a>Nakreslení ovládacího prvku model Windows Forms v dokumentu

1. V aplikaci Visual Studio vytvořte nebo otevřete projekt sešitu aplikace Excel nebo projekt wordového dokumentu tak, aby byl dokument viditelný v návrháři. Informace o vytváření projektů naleznete v tématu [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

2. Na kartě **běžné ovládací prvky** **panelu nástrojů**klikněte na ovládací prvek, který chcete přidat.

3. V dokumentu klikněte na místo, kde chcete umístit levý horní roh ovládacího prvku, a přetáhněte jej na místo, kde chcete umístit pravý dolní roh ovládacího prvku.

     Ovládací prvek je přidán do dokumentu se zadaným umístěním a velikostí.

    > [!NOTE]
    > Když vyberete ovládací prvek v aplikaci Excel, zobrazí se na **řádku vzorců** **= vložení ("WinForms. Control. host", ")** . Tento text je nezbytný a neměl by být odstraněn.

### <a name="to-add-a-windows-forms-control-to-the-document-by-single-clicking-the-control"></a>Přidání ovládacího prvku model Windows Forms k dokumentu jediným kliknutím na ovládací prvek

1. V aplikaci Visual Studio vytvořte nebo otevřete projekt sešitu aplikace Excel nebo projekt wordového dokumentu tak, aby byl dokument viditelný v návrháři. Informace o vytváření projektů naleznete v tématu [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

2. Na kartě **běžné ovládací prvky** **panelu nástrojů**klikněte na ovládací prvek, který chcete přidat.

3. V jednom dokumentu klikněte na místo, kam chcete ovládací prvek přidat.

     Ovládací prvek je přidán do dokumentu s výchozí velikostí.

    > [!NOTE]
    > Když vyberete ovládací prvek v aplikaci Excel, zobrazí se na **řádku vzorců** **= vložení ("WinForms. Control. host", ")** . Tento text je nezbytný a neměl by být odstraněn.

### <a name="to-add-a-windows-forms-control-to-the-document-by-double-clicking-the-control"></a>Chcete-li přidat ovládací prvek model Windows Forms do dokumentu dvojitým kliknutím na ovládací prvek

1. V aplikaci Visual Studio vytvořte nebo otevřete projekt sešitu aplikace Excel nebo projekt wordového dokumentu tak, aby byl dokument viditelný v návrháři. Informace o vytváření projektů naleznete v tématu [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

2. Na kartě **běžné ovládací prvky** **panelu nástrojů**dvakrát klikněte na ovládací prvek, který chcete přidat.

     Ovládací prvek je přidán do dokumentu uprostřed dokumentu nebo aktivního podokna.

    > [!NOTE]
    > Když vyberete ovládací prvek v aplikaci Excel, zobrazí se na **řádku vzorců** **= vložení ("WinForms. Control. host", ")** . Tento text je nezbytný a neměl by být odstraněn.

### <a name="to-add-a-windows-forms-control-to-the-document-by-pressing-the-enter-key"></a>Přidání ovládacího prvku model Windows Forms do dokumentu stisknutím klávesy ENTER

1. V aplikaci Visual Studio vytvořte nebo otevřete projekt sešitu aplikace Excel nebo projekt wordového dokumentu tak, aby byl dokument viditelný v návrháři. Informace o vytváření projektů naleznete v tématu [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

2. Na kartě **běžné ovládací prvky** **panelu nástrojů**klikněte na ovládací prvek, který chcete přidat, a stiskněte klávesu **ENTER** .

     Ovládací prvek je přidán do dokumentu uprostřed dokumentu nebo aktivního podokna.

    > [!NOTE]
    > Když vyberete ovládací prvek v aplikaci Excel, zobrazí se na **řádku vzorců** **= vložení ("WinForms. Control. host", ")** . Tento text je nezbytný a neměl by být odstraněn.

## <a name="add-controls-at-run-time-in-document-level-projects"></a><a name="runtimedoclevel"></a>Přidat ovládací prvky za běhu v projektech na úrovni dokumentu
 V době běhu můžete programově přidat model Windows Forms ovládací prvky do dokumentu. V aplikaci Word použijte metody <xref:Microsoft.Office.Tools.Word.DocumentBase.Controls%2A> vlastnosti `ThisDocument` třídy. V aplikaci Excel použijte metody <xref:Microsoft.Office.Tools.Excel.WorksheetBase.Controls%2A> vlastnosti `Sheet` třídy *n* . Každá metoda má několik přetížení, která umožňují určit umístění ovládacího prvku různými způsoby.

 Při přidání ovládacího prvku model Windows Forms do dokumentu v době běhu není ovládací prvek při zavření dokumentu uložen v dokumentu. Ovládací prvek lze znovu vytvořit při příštím otevření dokumentu. Další informace najdete v tématu [Přidání ovládacích prvků do dokumentů Office v době běhu](../vsto/adding-controls-to-office-documents-at-run-time.md).

### <a name="to-add-a-windows-forms-control-at-run-time"></a>Přidání ovládacího prvku model Windows Forms v době běhu

1. Použijte metodu, která má název Add \<*control class*> (kde *Třída ovládacího prvku* je název třídy model Windows Forms ovládacího prvku, který chcete přidat, například <xref:Microsoft.Office.Tools.Word.ControlExtensions.AddButton%2A> ).

     Následující příklad kódu ukazuje, jak přidat <xref:Microsoft.Office.Tools.Excel.Controls.Button> do buňky **C5** `Sheet1` v projektu na úrovni dokumentu v aplikaci Excel.

     [!code-vb[Trin_VstcoreProgrammingControlsExcel#4](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#4)]
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#4](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#4)]

## <a name="add-controls-at-run-time-in-vsto-add-ins"></a><a name="runtimeaddin"></a>Přidání ovládacích prvků v době běhu v doplňcích VSTO
 Můžete přidat ovládací prvky model Windows Forms programově do libovolného otevřeného dokumentu v době běhu. Nejprve vygenerujte hostitelskou položku, která je založena na otevřeném dokumentu nebo listu. Pak ve Wordu použijte metody <xref:Microsoft.Office.Tools.Word.Document.Controls%2A> Vlastnosti nové položky hostitele. V aplikaci Excel použijte metody <xref:Microsoft.Office.Tools.Excel.Worksheet.Controls%2A> Vlastnosti nové položky hostitele. Každá metoda má několik přetížení, která umožňují určit umístění ovládacího prvku různými způsoby.

 Při přidání ovládacího prvku model Windows Forms do dokumentu v době běhu není ovládací prvek při zavření dokumentu uložen v dokumentu. Ovládací prvek lze znovu vytvořit při příštím otevření dokumentu. Další informace najdete v tématu [Přidání ovládacích prvků do dokumentů Office v době běhu](../vsto/adding-controls-to-office-documents-at-run-time.md).

 Další informace o generování položek hostitele v projektech doplňku VSTO najdete v tématu [rozšiřování dokumentů aplikace Word a excelových sešitů v doplňcích VSTO za běhu](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).

### <a name="to-add-a-windows-forms-control-at-run-time"></a>Přidání ovládacího prvku model Windows Forms v době běhu

1. Použijte metodu, která má název Add \<*control class*> (kde *Třída ovládacího prvku* je název třídy model Windows Forms ovládacího prvku, který chcete přidat, například <xref:Microsoft.Office.Tools.Word.ControlExtensions.AddButton%2A> ).

    > [!NOTE]
    > V projektech doplňku VSTO, které cílí na [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] nebo novější, je nutné přidat odkaz na *Microsoft.Office.Tools.Excel.v4.0.Utilities.dll* nebo *Microsoft.Office.Tools.Word.v4.0.Utilities.dll* sestavení před tím, než budete moci získat přístup k \<*control class*> metodám Add.

     Následující příklad kódu ukazuje, jak přidat do <xref:Microsoft.Office.Tools.Word.Controls.Button> prvního odstavce aktivního dokumentu pomocí doplňku aplikace Word VSTO.

     [!code-vb[Trin_WordAddInDynamicControls#7](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#7)]
     [!code-csharp[Trin_WordAddInDynamicControls#7](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#7)]

## <a name="see-also"></a>Viz také
- [Přehled model Windows Formsch ovládacích prvků v dokumentech Office](../vsto/windows-forms-controls-on-office-documents-overview.md)
- [Přidání ovládacích prvků do dokumentů Office v době běhu](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Postupy: Změna velikosti ovládacích prvků v buňkách listu](../vsto/how-to-resize-controls-within-worksheet-cells.md)
- [Přehled hostitelských položek a hostitelských ovládacích prvků](../vsto/host-items-and-host-controls-overview.md)
- [Volitelné parametry v řešeních pro systém Office](../vsto/optional-parameters-in-office-solutions.md)
