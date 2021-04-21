---
title: Zobrazit text v textovém poli na listu pomocí tlačítka
description: Naučte se základy používání tlačítek a textových polí v listech Microsoft Excelu. Také Vytvářejte projekty aplikace Excel pomocí nástrojů pro vývoj pro Office v sadě Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- text [Office development in Visual Studio], displaying worksheets
- worksheets, displaying text
- text boxes, displaying text in worksheets
- text [Office development in Visual Studio], text boxes
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: b1209bf903f5a5b9c0005d9ba4ba6a891752aedd
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/21/2021
ms.locfileid: "107827783"
---
# <a name="walkthrough-display-text-in-a-text-box-in-a-worksheet-using-a-button"></a>Návod: zobrazení textu v textovém poli na listu s použitím tlačítka
  Tento názorný postup ukazuje základy používání tlačítek a textových polí v systém Microsoft Office excelových listů a vytváření projektů aplikace Excel pomocí nástrojů pro vývoj pro Office v sadě Visual Studio. Chcete-li zobrazit výsledek jako dokončený vzorek, přečtěte si ukázku ovládací prvky aplikace Excel v [ukázkách vývoje pro Office a návody](../vsto/office-development-samples-and-walkthroughs.md).

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 V tomto návodu se naučíte:

- Přidejte ovládací prvky do listu.

- Naplnění textového pole při kliknutí na tlačítko

- Otestujte svůj projekt.

> [!NOTE]
> Váš počítač může v následujících pokynech zobrazovat odlišné názvy nebo umístění některých prvků uživatelského rozhraní sady Visual Studio. Tyto prvky jsou určeny edicí sady Visual Studio a použitým nastavením. Další informace najdete v tématu [Přizpůsobení integrovaného vývojového prostředí (IDE) sady Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Požadavky
 K dokončení tohoto návodu budete potřebovat následující komponenty:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] nebo [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)]:

## <a name="create-the-project"></a>Vytvoření projektu
 V tomto kroku vytvoříte projekt sešitu aplikace Excel pomocí sady Visual Studio.

### <a name="to-create-a-new-project"></a>Vytvoření nového projektu

1. Vytvořte projekt sešitu aplikace Excel pomocí tlačítka název **aplikace Excel**. Ujistěte se, že je vybraná možnost **vytvořit nový dokument** . Další informace najdete v tématu [Postupy: vytváření projektů pro systém Office v sadě Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     Visual Studio otevře nový excelový sešit v návrháři a přidá projekt **tlačítka aplikace Excel** do **Průzkumník řešení**.

## <a name="add-controls-to-the-worksheet"></a>Přidat ovládací prvky do listu
 Pro tento návod budete potřebovat tlačítko a textové pole na prvním listu.

### <a name="to-add-a-button-and-a-text-box"></a>Přidání tlačítka a textového pole

1. Ověřte, že je sešit **Button.xlsxv aplikaci Excel** otevřený v návrháři aplikace Visual Studio se `Sheet1` zobrazeným.

2. Na kartě **běžné ovládací prvky** panelu nástrojů přetáhněte <xref:Microsoft.Office.Tools.Excel.Controls.TextBox> na `Sheet1` .

3. V nabídce **zobrazení** vyberte **okno Vlastnosti**.

4. Ujistěte se, že je v rozevíracím seznamu okno **vlastnosti** zobrazen parametr **TextBox1** a změňte vlastnost **název** textového pole na **zobrazenýtext**.

5. Přetáhněte ovládací prvek **tlačítko** na `Sheet1` a změňte následující vlastnosti:

   |Vlastnost|Hodnota|
   |--------------|-----------|
   |**Název**|**insertText**|
   |**Text**|**Vložit text**|

   Nyní napište kód, který se spustí po kliknutí na tlačítko.

## <a name="populate-the-text-box-when-the-button-is-clicked"></a>Naplnit textové pole při kliknutí na tlačítko
 Pokaždé, když uživatel klikne na tlačítko, **Hello World!** je připojen k textovému poli.

### <a name="to-write-to-the-text-box-when-the-button-is-clicked"></a>Zápis do textového pole při kliknutí na tlačítko

1. V **Průzkumník řešení** klikněte pravým tlačítkem na **List1** a pak klikněte na **Zobrazit kód** v místní nabídce.

2. Přidejte následující kód do <xref:System.Windows.Forms.Control.Click> obslužné rutiny události tlačítka:

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb" id="Snippet11":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs" id="Snippet11":::

3. V jazyce C# je nutné přidat obslužnou rutinu události k <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> události, jak je znázorněno níže. Informace o vytváření obslužných rutin událostí najdete v tématu [Postupy: vytváření obslužných rutin událostí v projektech pro systém Office](../vsto/how-to-create-event-handlers-in-office-projects.md).

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs" id="Snippet12":::

## <a name="test-the-application"></a>Testování aplikace
 Nyní můžete otestovat sešit, abyste se ujistili, že se **Hello World zpráva.** se zobrazí v textovém poli po kliknutí na tlačítko.

### <a name="to-test-your-workbook"></a>Test sešitu

1. Stisknutím klávesy **F5** spusťte projekt.

2. Klikněte na tlačítko.

3. Potvrďte, že **Hello World!** zobrazí se v textovém poli.

## <a name="next-steps"></a>Další kroky
 Tento návod ukazuje základy používání tlačítek a textových polí na listech aplikace Excel. Tady jsou některé úkoly, které mohou být další:

- Nasazení projektu. Další informace najdete v tématu [nasazení řešení pro Office](../vsto/deploying-an-office-solution.md).

- Změna formátování pomocí zaškrtávacích políček. Další informace najdete v tématu [Návod: Změna formátování listu pomocí ovládacích prvků CheckBox](../vsto/walkthrough-changing-worksheet-formatting-using-checkbox-controls.md).

## <a name="see-also"></a>Viz také
- [Postupy: Přidání ovládacích prvků model Windows Forms do dokumentů Office](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)
- [Návody pomocí Excelu](../vsto/walkthroughs-using-excel.md)
- [Omezení model Windows Formsch ovládacích prvků v dokumentech Office](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)
