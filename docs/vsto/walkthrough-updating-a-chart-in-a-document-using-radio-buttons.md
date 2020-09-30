---
title: 'Návod: aktualizace grafu v dokumentu pomocí přepínačů'
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], updating using controls
- controls [Office development in Visual Studio], updating documents
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: f4b39949deb3bcbf3d9330ca8d820a5841b0f4c4
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/30/2020
ms.locfileid: "91584292"
---
# <a name="walkthrough-update-a-chart-in-a-document-using-radio-buttons"></a>Návod: aktualizace grafu v dokumentu pomocí přepínačů
  Tento návod ukazuje, jak pomocí přepínačů v přizpůsobení na úrovni dokumentu pro systém Microsoft Office Word dát uživatelům možnost vybrat styly grafů v dokumentu.

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

 Tento návod znázorňuje následující úlohy:

- Přidání grafu do dokumentu v projektu na úrovni dokumentu v době návrhu.

- Seskupení přepínačů přidáním do uživatelského ovládacího prvku.

- Změna stylu grafu, je-li vybrána možnost.

  Chcete-li zobrazit výsledek jako dokončený vzorek, přečtěte si část ovládací prvky aplikace Word v [ukázkách vývoje pro Office a návody](../vsto/office-development-samples-and-walkthroughs.md).

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Předpoklady
 K dokončení tohoto návodu budete potřebovat následující komponenty:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] nebo [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)]:

## <a name="create-the-project"></a>Vytvoření projektu
 Prvním krokem je vytvoření projektu wordového dokumentu.

### <a name="to-create-a-new-project"></a>Vytvoření nového projektu

1. Vytvořte projekt wordového dokumentu s názvem **Moje možnosti grafu**. V průvodci vyberte možnost **vytvořit nový dokument**. Další informace najdete v tématu [Postupy: vytváření projektů pro systém Office v sadě Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     Visual Studio otevře nový wordový dokument v návrháři a přidá projekt **Možnosti grafu** do **Průzkumník řešení**.

## <a name="add-a-chart-to-the-document"></a>Přidání grafu do dokumentu

### <a name="to-add-a-chart"></a>Přidání grafu

1. V dokumentu aplikace Word, který je hostován v návrháři aplikace Visual Studio, klikněte na pásu karet na kartu **Vložit** .

2. Ve skupině **text** klikněte na rozevírací tlačítko **Vložit objekt** a klikněte na **objekt**.

     Otevře se dialogové okno **objekt** .

3. V seznamu **typ objektu** na kartě **vytvořit novou** vyberte **Microsoft Graph graf** a pak klikněte na **OK**.

     Do dokumentu v místě vložení se přidá graf a zobrazí se okno **datový list** s některými výchozími daty.

4. Zavřením okna **datového listu** přijměte výchozí hodnoty v grafu a kliknutím dovnitř dokumentu přesuňte fokus mimo graf.

5. Klikněte pravým tlačítkem na graf a pak klikněte na **Formát objektu**.

6. Na kartě **rozložení** dialogového okna **Formát objektu** vyberte **čtverc** a klikněte na tlačítko **OK**.

## <a name="add-a-user-control-to-the-project"></a>Přidat uživatelský ovládací prvek do projektu
 Přepínače na dokumentu se ve výchozím nastavení vzájemně nevylučují. Můžete je správně nasměrovat tak, že je přidáte do uživatelského ovládacího prvku a potom zapíšete kód pro řízení výběru.

### <a name="to-add-a-user-control"></a>Přidání uživatelského ovládacího prvku

1. V **Průzkumník řešení**vyberte projekt **Možnosti grafu** .

2. V nabídce **projekt** klikněte na příkaz **Přidat novou položku**.

3. V dialogovém okně **Přidat novou položku** klikněte na **uživatelský ovládací prvek**, pojmenujte **ChartOptions** ovládacího prvku a klikněte na **Přidat**.

### <a name="to-add-windows-form-controls-to-the-user-control"></a>Přidání ovládacích prvků Windows Form do uživatelského ovládacího prvku

1. Pokud uživatelský ovládací prvek není viditelný v návrháři, poklikejte na **ChartOptions** v **Průzkumník řešení**.

2. Na kartě **běžné ovládací prvky** **panelu nástrojů**přetáhněte první ovládací prvek **přepínač** na uživatelský ovládací prvek a změňte následující vlastnosti.

    |Vlastnost|Hodnota|
    |--------------|-----------|
    |**Název**|**columnChart**|
    |**Text**|**Sloupcový graf**|

3. Přidejte druhý **přepínač** do uživatelského ovládacího prvku a změňte následující vlastnosti.

    |Vlastnost|Hodnota|
    |--------------|-----------|
    |**Název**|**barChart**|
    |**Text**|**Pruhový graf**|

4. Přidejte do uživatelského ovládacího prvku třetí **přepínač** a změňte následující vlastnosti.

    |Vlastnost|Hodnota|
    |--------------|-----------|
    |**Název**|**lineChart**|
    |**Text**|**Spojnicový graf**|

5. Přidejte do uživatelského ovládacího prvku čtvrtý **přepínač** a změňte následující vlastnosti.

    |Vlastnost|Hodnota|
    |--------------|-----------|
    |**Název**|**areaBlockChart**|
    |**Text**|**Graf bloku oblasti**|

## <a name="add-references"></a>Přidat odkazy
 Chcete-li získat přístup k grafu z uživatelského ovládacího prvku v dokumentu, je nutné mít odkaz na `Microsoft.Office.Interop.Graph` sestavení v projektu.

### <a name="to-add-a-reference-to-the-microsoftofficeinteropgraph-assembly"></a>Přidání odkazu do sestavení Microsoft. Office. Interop. Graph

1. V nabídce **projekt** klikněte na příkaz **Přidat odkaz**.

     Zobrazí se dialogové okno **Přidat odkaz** .

2. Na kartě **.NET** vyberte **Microsoft. Office. Interop. Graph** a klikněte na **OK**. Vyberte verzi 14.0.0.0 sestavení.

## <a name="change-the-chart-style-when-a-radio-button-is-selected"></a>Změna stylu grafu, když je vybrán přepínač
 Chcete-li, aby tlačítka fungovala správně, vytvořte v uživatelském ovládacím prvku veřejnou událost, přidejte vlastnost pro nastavení typu výběru a vytvořte proceduru pro `CheckedChanged` událost každého přepínače.

### <a name="to-create-an-event-and-property-on-a-user-control"></a>Vytvoření události a vlastnosti v uživatelském ovládacím prvku

1. V **Průzkumník řešení**klikněte pravým tlačítkem myši na uživatelský ovládací prvek a pak klikněte na **Zobrazit kód**.

2. Přidejte kód pro vytvoření `SelectionChanged` události a `Selection` vlastnosti `ChartOptions` třídy.

     [!code-csharp[Trin_VstcoreProgrammingControlsWord#9](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ChartOptions.cs#9)]
     [!code-vb[Trin_VstcoreProgrammingControlsWord#9](../vsto/codesnippet/VisualBasic/my chart options/ChartOptions.vb#9)]

### <a name="to-handle-the-checkedchange-event-of-the-radio-buttons"></a>Zpracování událostí CheckedChange přepínačů

1. Nastavte typ grafu v `CheckedChanged` obslužné rutině události pro `areaBlockChart` přepínač a pak událost vyvolejte.

     [!code-csharp[Trin_VstcoreProgrammingControlsWord#10](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ChartOptions.cs#10)]
     [!code-vb[Trin_VstcoreProgrammingControlsWord#10](../vsto/codesnippet/VisualBasic/my chart options/ChartOptions.vb#10)]

2. Nastavte typ grafu v `CheckedChanged` obslužné rutině události pro `barChart` přepínač.

     [!code-csharp[Trin_VstcoreProgrammingControlsWord#11](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ChartOptions.cs#11)]
     [!code-vb[Trin_VstcoreProgrammingControlsWord#11](../vsto/codesnippet/VisualBasic/my chart options/ChartOptions.vb#11)]

3. Nastavte typ grafu v `CheckedChanged` obslužné rutině události pro `columnChart` přepínač.

     [!code-csharp[Trin_VstcoreProgrammingControlsWord#12](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ChartOptions.cs#12)]
     [!code-vb[Trin_VstcoreProgrammingControlsWord#12](../vsto/codesnippet/VisualBasic/my chart options/ChartOptions.vb#12)]

4. Nastavte typ grafu v `CheckedChanged` obslužné rutině události pro `lineChart` přepínač.

     [!code-csharp[Trin_VstcoreProgrammingControlsWord#13](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ChartOptions.cs#13)]
     [!code-vb[Trin_VstcoreProgrammingControlsWord#13](../vsto/codesnippet/VisualBasic/my chart options/ChartOptions.vb#13)]

5. V jazyce C# je nutné přidat obslužné rutiny události pro přepínače. Do konstruktoru lze přidat kód `ChartOptions` pod volání `InitializeComponent` . Informace o vytváření obslužných rutin událostí najdete v tématu [Postupy: vytváření obslužných rutin událostí v projektech pro systém Office](../vsto/how-to-create-event-handlers-in-office-projects.md).

     [!code-csharp[Trin_VstcoreProgrammingControlsWord#14](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ChartOptions.cs#14)]

## <a name="add-the-user-control-to-the-document"></a>Přidat uživatelský ovládací prvek do dokumentu
 Při sestavování řešení se nový uživatelský ovládací prvek automaticky přidá do **sady nástrojů**. Pak můžete ovládací prvek přetáhnout z **panelu nástrojů** do dokumentu.

### <a name="to-add-the-user-control-your-document"></a>Přidání uživatelského ovládacího prvku dokumentu

1. V nabídce **Sestavení** klikněte na **Sestavit řešení**.

     Uživatelský ovládací prvek **ChartOptions** se přidá do **sady nástrojů**.

2. V **Průzkumník řešení**klikněte pravým tlačítkem myši na **ThisDocument. vb** nebo **ThisDocument.cs**a pak klikněte na tlačítko **Návrhář zobrazení**.

3. Přetáhněte `ChartOptions` ovládací prvek z **panelu nástrojů** do dokumentu.

     V okně **vlastnosti** pojmenujte ovládací prvek, který jste právě přidali do dokumentu  `ChartOptions1` .

## <a name="change-the-chart-type"></a>Změnit typ grafu
 Vytvořte obslužnou rutinu události pro změnu typu grafu podle možnosti, která je vybrána v uživatelském ovládacím prvku.

### <a name="to-change-the-type-of-chart-that-is-displayed-in-the-document"></a>Chcete-li změnit typ grafu, který je zobrazen v dokumentu

1. Přidejte do třídy následující obslužnou rutinu události `ThisDocument` .

     [!code-vb[Trin_VstcoreProgrammingControlsWord#15](../vsto/codesnippet/VisualBasic/my chart options/ThisDocument.vb#15)]
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#15](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#15)]

2. V jazyce C# je nutné přidat do události obslužnou rutinu události pro uživatelský ovládací prvek <xref:Microsoft.Office.Tools.Word.Document.Startup> .

     [!code-csharp[Trin_VstcoreProgrammingControlsWord#16](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#16)]

## <a name="test-the-application"></a>Testování aplikace
 Teď můžete dokument otestovat a ujistit se, že se styl grafu po výběru přepínače správně aktualizuje.

### <a name="to-test-your-document"></a>Testování dokumentu

1. Stisknutím klávesy **F5** spusťte projekt.

2. Vyberte různé přepínače.

3. Potvrďte, že se styl grafu změní tak, aby odpovídal výběru.

## <a name="next-steps"></a>Další kroky
 Tady jsou některé úkoly, které mohou být další:

- Použití tlačítka k naplnění textového pole. Další informace najdete v tématu [Návod: zobrazení textu v textovém poli v dokumentu pomocí tlačítka](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-document-using-a-button.md).

- Změna formátování výběrem stylu v poli se seznamem. Další informace naleznete v tématu [Návod: Změna formátování dokumentu pomocí ovládacích prvků CheckBox](../vsto/walkthrough-changing-document-formatting-using-checkbox-controls.md).

## <a name="see-also"></a>Viz také
- [Návody pomocí aplikace Word](../vsto/walkthroughs-using-word.md)
- [Ukázky a návody pro vývoj pro Office](../vsto/office-development-samples-and-walkthroughs.md)
- [Omezení model Windows Formsch ovládacích prvků v dokumentech Office](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)
