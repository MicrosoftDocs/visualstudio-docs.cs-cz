---
title: Změna formátování listů pomocí ovládacích prvků CheckBox
description: Přečtěte si, jak můžete pomocí vývojářských nástrojů pro Office v sadě Visual Studio vytvořit a přidat kód do projektu.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets, changing formatting using managed controls
- worksheets, check box controls
- controls [Office development in Visual Studio], adding to worksheets
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 28b9f000c2e8517304387e2b203dfa7888b33d64
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/15/2020
ms.locfileid: "97527221"
---
# <a name="walkthrough-change-worksheet-formatting-using-checkbox-controls"></a>Návod: Změna formátování listů pomocí ovládacích prvků CheckBox
  Tento názorný postup ukazuje základy používání zaškrtávacích políček u systém Microsoft Office excelového listu ke změně formátování. Budete používat vývojové nástroje Office v sadě Visual Studio k vytvoření a přidání kódu do projektu. Chcete-li zobrazit výsledek jako dokončený vzorek, přečtěte si ukázku ovládací prvky aplikace Excel v [ukázkách vývoje pro Office a návody](../vsto/office-development-samples-and-walkthroughs.md).

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 V tomto návodu se naučíte:

- Přidejte text a ovládací prvky do listu.

- Naformátuje text, pokud je vybraná možnost.

- Otestujte svůj projekt.

> [!NOTE]
> Váš počítač může v následujících pokynech zobrazovat odlišné názvy nebo umístění některých prvků uživatelského rozhraní sady Visual Studio. Tyto prvky jsou určeny edicí sady Visual Studio a použitým nastavením. Další informace najdete v tématu [Přizpůsobení integrovaného vývojového prostředí (IDE) sady Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Předpoklady
 K dokončení tohoto návodu budete potřebovat následující komponenty:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] nebo [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)]:

## <a name="create-the-project"></a>Vytvoření projektu
 V tomto kroku vytvoříte projekt sešitu aplikace Excel pomocí sady Visual Studio.

### <a name="to-create-a-new-project"></a>Vytvoření nového projektu

1. Vytvořte projekt sešitu aplikace Excel s názvem **Moje formátování aplikace Excel**. Ujistěte se, že je vybraná možnost **vytvořit nový dokument** . Další informace najdete v tématu [Postupy: vytváření projektů pro systém Office v sadě Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     Visual Studio otevře nový excelový sešit v návrháři a přidá projekt **formátování aplikace Excel** do **Průzkumník řešení**.

## <a name="add-text-and-controls-to-the-worksheet"></a>Přidat text a ovládací prvky do listu
 V tomto návodu budete potřebovat tři <xref:Microsoft.Office.Tools.Excel.Controls.CheckBox> ovládací prvky a nějaký text v <xref:Microsoft.Office.Tools.Excel.NamedRange> ovládacím prvku.

### <a name="to-add-three-check-boxes"></a>Přidání tří zaškrtávacích políček

1. Ověřte, že je sešit otevřený v návrháři sady Visual Studio a `Sheet1` je otevřený.

2. Na kartě **běžné ovládací prvky** **panelu nástrojů** přetáhněte <xref:Microsoft.Office.Tools.Excel.Controls.CheckBox> ovládací prvek na nebo poblíž buňky **B2** v hodnotě **List1**.

3. V nabídce **zobrazení** vyberte okno **vlastnosti** .

4. Ujistěte se, že se vlastnost **checkBox1** zobrazuje v poli seznam názvů objektů v okně **vlastnosti** , a změňte následující vlastnosti:

    |Vlastnost|Hodnota|
    |--------------|-----------|
    |**Název**|**applyBoldFont**|
    |**Text**|**Tučný**|

5. Přetáhněte druhé zaškrtávací políčko na buňku **B4** nebo poblíž něj a změňte následující vlastnosti:

    |Vlastnost|Hodnota|
    |--------------|-----------|
    |**Název**|**applyItalicFont**|
    |**Text**|**Kurzíva**|

6. Přetáhněte třetí zaškrtávací políčko na buňku **B6** nebo poblíž něj a změňte následující vlastnosti:

    |Vlastnost|Hodnota|
    |--------------|-----------|
    |**Název**|**applyUnderlineFont**|
    |**Text**|**Podtržení**|

7. Zaškrtněte všechny tři ovládací prvky zaškrtávací políčko při držení klávesy **CTRL** .

8. Ve skupině Uspořádat na kartě Formát v Excelu klikněte na **Zarovnat** a pak klikněte na **Zarovnat doleva**.

     Tři ovládací prvky zaškrtávací políčko jsou zarovnány na levou stranu na pozici prvního ovládacího prvku, který jste vybrali.

     V dalším kroku přetáhnete <xref:Microsoft.Office.Tools.Excel.NamedRange> ovládací prvek do listu.

    > [!NOTE]
    > Ovládací prvek můžete přidat také <xref:Microsoft.Office.Tools.Excel.NamedRange> tak, že do pole **název** zadáte **textFont** .

#### <a name="to-add-text-to-a-namedrange-control"></a>Přidání textu do ovládacího prvku NamedRange

1. Z karty **ovládací prvky aplikace Excel** v panelu nástrojů přetáhněte <xref:Microsoft.Office.Tools.Excel.NamedRange> ovládací prvek do buňky **B9**.

2. Ověřte, zda se **$B $9** zobrazí v upravitelném textovém poli a zda je vybrána buňka **B9** . Pokud ne, klikněte na buňku **B9** a vyberte ji.

3. Klikněte na **OK**.

4. Buňka **B9** se stala rozsahem s názvem `NamedRange1` .

    List neobsahuje žádné viditelné údaje, ale `NamedRange1` zobrazí se v **poli název** (hned nad listem na levé straně), když je vybraná buňka **B9** .

5. Ujistěte se, že je **NamedRange1** viditelný v poli seznam názvů objektů v okně **vlastnosti** a změňte následující vlastnosti:

   |Vlastnost|Hodnota|
   |--------------|-----------|
   |**Název**|**textFont**|
   |**Argument**|**Chcete-li změnit formátování tohoto textu, klikněte na zaškrtávací políčko.**|

   Dále napište kód pro formátování textu, když je vybrána možnost.

## <a name="format-the-text-when-an-option-is-selected"></a>Formátování textu při výběru možnosti
 V této části napíšete kód, takže když uživatel vybere možnost formátování, změní se formát textu v listu.

### <a name="to-change-formatting-when-a-check-box-is-selected"></a>Změna formátování, když je zaškrtnuto zaškrtávací políčko

1. Klikněte pravým tlačítkem na **List1** a pak klikněte na **Zobrazit kód** v místní nabídce.

2. Do <xref:System.Windows.Forms.Control.Click> obslužné rutiny události zaškrtávacího políčka přidejte následující kód `applyBoldFont` :

     [!code-vb[Trin_VstcoreProgrammingControlsExcel#7](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#7)]
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#7](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#7)]

3. Do <xref:System.Windows.Forms.Control.Click> obslužné rutiny události zaškrtávacího políčka přidejte následující kód `applyItalicFont` :

     [!code-vb[Trin_VstcoreProgrammingControlsExcel#8](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#8)]
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#8](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#8)]

4. Do <xref:System.Windows.Forms.Control.Click> obslužné rutiny události zaškrtávacího políčka přidejte následující kód `applyUnderlineFont` :

     [!code-vb[Trin_VstcoreProgrammingControlsExcel#9](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#9)]
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#9](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#9)]

5. V jazyce C# je nutné přidat obslužné rutiny události pro zaškrtávací políčka do <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> události, jak je znázorněno níže. Informace o vytváření obslužných rutin událostí najdete v tématu [Postupy: vytváření obslužných rutin událostí v projektech pro systém Office](../vsto/how-to-create-event-handlers-in-office-projects.md).

     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#10](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#10)]

## <a name="test-the-application"></a>Testování aplikace
 Nyní můžete otestovat sešit, abyste se ujistili, že je text správně formátovaný, když zaškrtnete nebo zrušíte zaškrtnutí políčka.

### <a name="to-test-your-workbook"></a>Test sešitu

1. Stisknutím klávesy **F5** spusťte projekt.

2. Zaškrtněte nebo zrušte zaškrtnutí políčka.

3. Potvrďte, že je text správně naformátovaný.

## <a name="next-steps"></a>Další kroky
 Tento názorný postup ukazuje základy používání zaškrtávacích políček a formátování textu v listech aplikace Excel. Tady jsou některé úkoly, které mohou být další:

- Nasazení projektu. Další informace najdete v tématu [nasazení řešení pro systém Office pomocí technologie ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md).
- Použití tlačítka k naplnění textového pole. Další informace najdete v tématu [Návod: zobrazení textu v textovém poli na listu pomocí tlačítka](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-worksheet-using-a-button.md).

## <a name="see-also"></a>Viz také
- [Návody pomocí Excelu](../vsto/walkthroughs-using-excel.md)
- [Ovládací prvek NamedRange](../vsto/namedrange-control.md)
- [Omezení model Windows Formsch ovládacích prvků v dokumentech Office](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)
