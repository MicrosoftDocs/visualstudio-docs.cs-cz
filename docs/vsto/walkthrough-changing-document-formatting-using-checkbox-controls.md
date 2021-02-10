---
title: Změna formátování dokumentu pomocí ovládacích prvků CheckBox
description: Naučte se používat ovládací prvky model Windows Forms v přizpůsobení na úrovni dokumentu pro aplikaci Microsoft Word pro změnu formátování textu.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Word documents, changing formatting using controls
- documents [Office development in Visual Studio], formatting
- check boxes, Word documents
- documents [Office development in Visual Studio], check box controls
- controls [Office development in Visual Studio], adding to documents
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 4d83fb8fad6de0c932d371f7f874cea0ff9a8f80
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99958658"
---
# <a name="walkthrough-change-document-formatting-using-checkbox-controls"></a>Návod: Změna formátování dokumentu pomocí ovládacích prvků CheckBox
  Tento návod ukazuje, jak použít ovládací prvky model Windows Forms v přizpůsobení na úrovni dokumentu pro systém Microsoft Office Word pro změnu formátování textu.

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

 Tento návod znázorňuje následující úlohy:

- Přidání textu a ovládacího prvku do dokumentu v projektu na úrovni dokumentu v době návrhu.

- Formátování textu, je-li vybrána možnost.

  Chcete-li zobrazit výsledek jako dokončený vzorek, přečtěte si část ovládací prvky aplikace Word v [ukázkách vývoje pro Office a návody](../vsto/office-development-samples-and-walkthroughs.md).

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Požadavky
 K dokončení tohoto návodu budete potřebovat následující komponenty:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] nebo [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)]:

## <a name="create-the-project"></a>Vytvoření projektu
 Prvním krokem je vytvoření projektu wordového dokumentu.

### <a name="create-a-new-project"></a>Vytvoření nového projektu

1. Vytvořte projekt wordového dokumentu s názvem **Moje formátování Wordu**. V průvodci vyberte možnost **vytvořit nový dokument**.

     Další informace najdete v tématu [Postupy: vytváření projektů pro systém Office v sadě Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     Visual Studio otevře nový wordový dokument v návrháři a přidá projekt **formátování moje aplikace** do **Průzkumník řešení**.

## <a name="add-text-and-controls-to-the-word-document"></a>Přidání textu a ovládacích prvků do dokumentu aplikace Word
 Pro tento návod přidejte do dokumentu aplikace Word tři zaškrtávací políčka a nějaký text v <xref:Microsoft.Office.Tools.Word.Bookmark> ovládacím prvku. Zaškrtávací políčka zobrazí uživateli možnosti formátování textu.

### <a name="add-three-check-boxes"></a>Přidat tři zaškrtávací políčka

1. Ověřte, že je dokument otevřený v návrháři sady Visual Studio.

2. Na kartě **běžné ovládací prvky** **panelu nástrojů** přetáhněte první <xref:Microsoft.Office.Tools.Word.Controls.CheckBox> ovládací prvek do dokumentu.

3. V okně **vlastnosti** změňte následující vlastnosti.

    |Vlastnost|Hodnota|
    |--------------|-----------|
    |**Název**|**applyBoldFont**|
    |**Text**|**Bold**|

4. Stisknutím klávesy **ENTER** přesuňte kurzor pod první zaškrtávací políčko.

5. Do dokumentu pod zaškrtávacím políčkem přidejte druhé zaškrtávací políčko `ApplyBoldFont` a změňte následující vlastnosti.

    |Vlastnost|Hodnota|
    |--------------|-----------|
    |**Název**|**applyItalicFont**|
    |**Text**|**Kurzíva**|

6. Stisknutím klávesy **ENTER** přesuňte kurzor pod druhé zaškrtávací políčko.

7. Přidejte třetí zaškrtávací políčko do dokumentu pod `ApplyItalicFont` zaškrtávacím políčkem a změňte následující vlastnosti.

    |Vlastnost|Hodnota|
    |--------------|-----------|
    |**Název**|**applyUnderlineFont**|
    |**Text**|**Podtržení**|

### <a name="add-text-and-a-bookmark-control"></a>Přidání textu a ovládacího prvku záložka

1. Přesuňte kurzor pod ovládací prvky zaškrtávací políčko a zadejte následující text:

    **Chcete-li změnit formátování tohoto textu, klikněte na zaškrtávací políčko.**

2. Z karty **ovládací prvky aplikace Word** v **panelu nástrojů** přetáhněte <xref:Microsoft.Office.Tools.Word.Bookmark> ovládací prvek do dokumentu.

    Zobrazí se dialogové okno **Přidat ovládací prvek záložky** .

3. Vyberte text, který jste přidali do dokumentu, a klikněte na **OK**.

    <xref:Microsoft.Office.Tools.Word.Bookmark>Do vybraného textu v dokumentu se přidá ovládací prvek s názvem **bookmark1** .

4. V okně **vlastnosti** změňte hodnotu vlastnosti **(název)** na **fontText.**

   Dále napište kód pro formátování textu, když je zaškrtnuto nebo vymazáno zaškrtávací políčko.

## <a name="format-the-text-when-a-check-box-is-checked-or-cleared"></a>Naformátovat text, pokud je zaškrtnuto nebo vymazáno zaškrtávací políčko
 Když uživatel vybere možnost formátování, změňte formát textu v dokumentu.

### <a name="change-formatting-when-a-check-box-is-selected"></a>Změnit formátování, je-li zaškrtnuto zaškrtávací políčko

1. Klikněte pravým tlačítkem na `ThisDocument` **Průzkumník řešení** a pak klikněte na **Zobrazit kód** v místní nabídce.

2. Pouze pro C# přidejte do třídy **ThisDocument** následující konstanty.

     [!code-csharp[Trin_VstcoreProgrammingControlsWord#2](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#2)]

3. Do <xref:System.Windows.Forms.Control.Click> obslužné rutiny události zaškrtávacího políčka přidejte následující kód `applyBoldFont` .

     [!code-vb[Trin_VstcoreProgrammingControlsWord#3](../vsto/codesnippet/VisualBasic/my chart options/ThisDocument.vb#3)]
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#3](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#3)]

4. Do <xref:System.Windows.Forms.Control.Click> obslužné rutiny události zaškrtávacího políčka přidejte následující kód `applyItalicFont` .

     [!code-vb[Trin_VstcoreProgrammingControlsWord#4](../vsto/codesnippet/VisualBasic/my chart options/ThisDocument.vb#4)]
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#4](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#4)]

5. Do <xref:System.Windows.Forms.Control.Click> obslužné rutiny události zaškrtávacího políčka přidejte následující kód `applyUnderlineFont` .

     [!code-vb[Trin_VstcoreProgrammingControlsWord#5](../vsto/codesnippet/VisualBasic/my chart options/ThisDocument.vb#5)]
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#5](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#5)]

6. V jazyce C# je nutné přidat obslužné rutiny události pro textová pole do <xref:Microsoft.Office.Tools.Word.Document.Startup> události. Informace o tom, jak vytvořit obslužné rutiny událostí, naleznete v tématu [How to: Create event handlers in Office Projects](../vsto/how-to-create-event-handlers-in-office-projects.md).

     [!code-csharp[Trin_VstcoreProgrammingControlsWord#6](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#6)]

## <a name="test-the-application"></a>Testování aplikace
 Teď můžete dokument otestovat a ověřit, jestli je text správně formátovaný, když zaškrtnete nebo zrušíte zaškrtnutí políčka.

### <a name="test-your-document"></a>Testování dokumentu

1. Stisknutím klávesy **F5** spusťte projekt.

2. Zaškrtněte nebo zrušte zaškrtnutí políčka.

3. Potvrďte, že je text správně naformátovaný.

## <a name="next-steps"></a>Další kroky
 Tento názorný postup ukazuje základy používání zaškrtávacích políček a programovou změnu formátování textu u dokumentů aplikace Word. Tady jsou některé úkoly, které mohou být další:

- K naplnění textového pole použijte tlačítko. Další informace najdete v tématu [Návod: zobrazení textu v textovém poli v dokumentu pomocí tlačítka](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-document-using-a-button.md).

- Výběr stylů grafu pomocí přepínačů Další informace najdete v tématu [Návod: aktualizace grafu v dokumentu pomocí přepínačů](../vsto/walkthrough-updating-a-chart-in-a-document-using-radio-buttons.md).

## <a name="see-also"></a>Viz také
- [Návody pomocí aplikace Word](../vsto/walkthroughs-using-word.md)
- [Ukázky a návody pro vývoj pro Office](../vsto/office-development-samples-and-walkthroughs.md)
- [Ovládací prvek NamedRange](../vsto/namedrange-control.md)
- [Omezení model Windows Formsch ovládacích prvků v dokumentech Office](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)
