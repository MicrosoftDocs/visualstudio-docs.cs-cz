---
title: Aktualizovat graf v listu pomocí přepínačů
description: Seznamte se se základy používání přepínačů na listu Microsoft Excelu a poskytněte tak uživateli možnost rychlého přepínání mezi možnostmi.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets, updating using managed controls
- controls [Office development in Visual Studio], updating worksheets
- worksheets, using radio buttons
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: b1c9da3b1d019c77988ef01e1b3c019dd3f1d775
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99937313"
---
# <a name="walkthrough-updating-a-chart-in-a-worksheet-using-radio-buttons"></a>Návod: Aktualizace grafu na listu s použitím přepínačů
  V tomto návodu se dozvíte základy používání přepínačů na listu systém Microsoft Office Excel, které uživateli umožňují rychle přepínat mezi možnostmi. V takovém případě možnosti změní styl grafu.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 Chcete-li zobrazit výsledek jako dokončený vzorek, přečtěte si ukázku ovládací prvky aplikace Excel v [ukázkách vývoje pro Office a návody](../vsto/office-development-samples-and-walkthroughs.md).

 Tento návod znázorňuje následující úlohy:

- Přidání skupiny přepínacích tlačítek do listu.

- Změna stylu grafu, je-li vybrána možnost.

> [!NOTE]
> Váš počítač může v následujících pokynech zobrazovat odlišné názvy nebo umístění některých prvků uživatelského rozhraní sady Visual Studio. Tyto prvky jsou určeny edicí sady Visual Studio a použitým nastavením. Další informace najdete v tématu [Přizpůsobení integrovaného vývojového prostředí (IDE) sady Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Požadavky
 K dokončení tohoto návodu budete potřebovat následující komponenty:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] nebo [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)]:

## <a name="add-a-chart-to-a-worksheet"></a>Přidání grafu do listu
 Můžete vytvořit projekt sešitu aplikace Excel, který přizpůsobí existující sešit. V tomto návodu přidáte graf do sešitu a pak ho použijete v novém excelovém řešení. Zdroj dat v tomto návodu je list s názvem **data pro graf**.

### <a name="to-add-the-data"></a>Přidání dat

1. Otevřete Microsoft Excel.

2. Klikněte pravým tlačítkem na kartu **Sheet3** a potom v místní nabídce klikněte na **Přejmenovat** .

3. Přejmenujte list na **data pro graf**.

4. Do levého horního rohu přidejte následující data **pro graf** s buňkou A4 a E8 pravý dolní roh.

   |Oblast/čtvrtletí|Q1|Q2|Q3|Q4|
   |-|--------|--------|--------|--------|
   |West|500|550|550|600|
   |East|600|625|675|700|
   |North|450|470|490|510|
   |South|800|750|775|790|

   V dalším kroku přidejte graf na první list, abyste zobrazili data.

### <a name="to-add-a-chart-in-excel"></a>Přidání grafu v Excelu

1. Na kartě **Vložit** ve skupině **grafy** klikněte na **sloupec** a pak klikněte na **všechny typy grafů**.

2. V dialogovém okně **Vložit graf** klikněte na tlačítko **OK**.

3. Na kartě **Návrh** ve skupině **data** klikněte na **Vybrat data**.

4. V dialogovém okně **Vybrat zdroj dat** klikněte do pole **ChartData rozsah** a zrušte zaškrtnutí všech výchozích výběrů.

5. V seznamu **data pro graf** Vyberte blok buněk obsahující čísla, která obsahují a4 v levém horním rohu do E8 v pravém dolním rohu.

6. V dialogovém okně **Vybrat zdroj dat** klikněte na tlačítko **OK**.

7. Přemístěte graf tak, aby se v pravém horním rohu zarovnala buňka **E2**.

8. Uložte soubor na jednotku C a pojmenujte ji **ExcelChart.xlsx**.

9. Ukončete aplikaci Excel.

## <a name="create-a-new-project"></a>Vytvoření nového projektu
 V tomto kroku vytvoříte projekt sešitu aplikace Excel na základě **ExcelChart** sešitu.

### <a name="to-create-a-new-project"></a>Vytvoření nového projektu

1. Vytvořte projekt sešitu aplikace Excel s názvem **Moje excelový graf**. V průvodci vyberte možnost **zkopírovat existující dokument**.

     Další informace najdete v tématu [Postupy: vytváření projektů pro systém Office v sadě Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

2. Klikněte na tlačítko **Procházet** a přejděte k sešitu, který jste vytvořili dříve v tomto návodu.

3. Klikněte na **OK**.

     Visual Studio otevře nový sešit aplikace Excel v návrháři a přidá projekt **aplikace Excel do grafu** **Průzkumník řešení**.

## <a name="set-properties-of-the-chart"></a>Nastavit vlastnosti grafu
 Při vytváření nového projektu excelového sešitu, který používá existující sešit, se automaticky vytvoří hostitelské ovládací prvky pro všechny pojmenované rozsahy, objekty seznamu a grafy v sešitu. Název <xref:Microsoft.Office.Tools.Excel.Chart> ovládacího prvku lze změnit pomocí okna **vlastnosti** .

### <a name="to-change-the-name-of-the-chart-control"></a>Změna názvu ovládacího prvku grafu

1. Vyberte <xref:Microsoft.Office.Tools.Excel.Chart> ovládací prvek v návrháři a v okně **vlastnosti** změňte následující vlastnosti.

    |Vlastnost|Hodnota|
    |--------------|-----------|
    |**Název**|**datachart**|
    |**HasLegend**|**chybné**|

## <a name="add-controls"></a>Přidat ovládací prvky
 Tento list používá přepínače k tomu, aby uživatelům poskytoval způsob, jak rychle změnit styl grafu. Přepínače musí být exkluzivní – Pokud je vybráno jedno tlačítko, nelze současně vybrat žádné jiné tlačítko ve skupině. K tomuto chování dochází ve výchozím nastavení, když přidáte několik přepínačů do listu.

 Jedním ze způsobů, jak toto chování přidat, je seskupení přepínačů do uživatelského ovládacího prvku, zápis kódu za uživatelský ovládací prvek a přidání uživatelského ovládacího prvku do listu.

### <a name="to-add-a-user-control"></a>Přidání uživatelského ovládacího prvku

1. V **Průzkumník řešení** vyberte **svůj projekt excelový graf** .

2. V nabídce **projekt** klikněte na příkaz **Přidat novou položku**.

3. V dialogovém okně **Přidat novou položku** klikněte na **uživatelský ovládací prvek**, pojmenujte **ChartOptions** ovládacího prvku a klikněte na **Přidat**.

### <a name="to-add-radio-buttons-to-the-user-control"></a>Přidání přepínačů do uživatelského ovládacího prvku

1. Pokud uživatelský ovládací prvek není viditelný v návrháři, poklikejte na **ChartOptions** v **Průzkumník řešení**.

2. Na kartě **běžné ovládací prvky** **panelu nástrojů** přetáhněte ovládací prvek **přepínač** na uživatelský ovládací prvek a změňte následující vlastnosti.

   | Vlastnost | Hodnota |
   |----------|------------------|
   | **Název** | **columnChart** |
   | **Text** | **Sloupcový graf** |

3. Přidejte druhý přepínač do uživatelského ovládacího prvku a změňte následující vlastnosti.

   | Vlastnost | Hodnota |
   |----------|---------------|
   | **Název** | **barChart** |
   | **Text** | **Pruhový graf** |

4. Přidejte do uživatelského ovládacího prvku třetí přepínač a změňte následující vlastnosti.

   | Vlastnost | Hodnota |
   |----------|----------------|
   | **Název** | **lineChart** |
   | **Text** | **Spojnicový graf** |

5. Přidejte do uživatelského ovládacího prvku čtvrtý přepínač a změňte následující vlastnosti.

   |Vlastnost|Hodnota|
   |--------------|-----------|
   |**Název**|**areaBlockChart**|
   |**Text**|**Graf bloku oblasti**|

   V dalším kroku napište kód, aby se graf aktualizoval při kliknutí na přepínač.

## <a name="change-the-chart-style-when-a-radio-button-is-selected"></a>Změna stylu grafu, když je vybrán přepínač
 Nyní můžete přidat kód pro změnu stylu grafu. Chcete-li to provést, vytvořte veřejnou událost v uživatelském ovládacím prvku, přidejte vlastnost pro nastavení typu výběru a vytvořte obslužnou rutinu události pro `CheckedChanged` událost každého přepínacího tlačítka.

### <a name="to-create-an-event-and-property-on-a-user-control"></a>Vytvoření události a vlastnosti v uživatelském ovládacím prvku

1. V **Průzkumník řešení** klikněte pravým tlačítkem myši na uživatelský ovládací prvek a pak klikněte na **Zobrazit kód**.

2. Přidejte kód do `ChartOptions` třídy pro vytvoření `SelectionChanged` události a `Selection` Vlastnosti.

     [!code-vb[Trin_VstcoreProgrammingControlsExcel#13](../vsto/codesnippet/VisualBasic/my excel chart/ChartOptions.vb#13)]
     [!code-cs[Trin_VstcoreProgrammingControlsExcel#13](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/ChartOptions.cs#13)]

### <a name="to-handle-the-checkedchanged-event-of-the-radio-buttons"></a>Zpracování událostí CheckedChanged přepínačů

1. Nastavte typ grafu v `CheckedChanged` obslužné rutině události pro `areaBlockChart` přepínač a pak událost vyvolejte.

     [!code-vb[Trin_VstcoreProgrammingControlsExcel#14](../vsto/codesnippet/VisualBasic/my excel chart/ChartOptions.vb#14)]
     [!code-cs[Trin_VstcoreProgrammingControlsExcel#14](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/ChartOptions.cs#14)]

2. Nastavte typ grafu v `CheckedChanged` obslužné rutině události pro `barChart` přepínač.

     [!code-vb[Trin_VstcoreProgrammingControlsExcel#15](../vsto/codesnippet/VisualBasic/my excel chart/ChartOptions.vb#15)]
     [!code-cs[Trin_VstcoreProgrammingControlsExcel#15](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/ChartOptions.cs#15)]

3. Nastavte typ grafu v `CheckedChanged` obslužné rutině události pro `columnChart` přepínač.

     [!code-vb[Trin_VstcoreProgrammingControlsExcel#16](../vsto/codesnippet/VisualBasic/my excel chart/ChartOptions.vb#16)]
     [!code-cs[Trin_VstcoreProgrammingControlsExcel#16](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/ChartOptions.cs#16)]

4. Nastavte typ grafu v `CheckedChanged` obslužné rutině události pro `lineChart` přepínač.

     [!code-vb[Trin_VstcoreProgrammingControlsExcel#17](../vsto/codesnippet/VisualBasic/my excel chart/ChartOptions.vb#17)]
     [!code-cs[Trin_VstcoreProgrammingControlsExcel#17](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/ChartOptions.cs#17)]

5. V jazyce C# je nutné přidat obslužné rutiny události pro přepínače. Do konstruktoru lze přidat kód `ChartOptions` pod volání `InitializeComponent` . Informace o tom, jak vytvořit obslužné rutiny událostí, naleznete v tématu [How to: Create event handlers in Office Projects](../vsto/how-to-create-event-handlers-in-office-projects.md).

     [!code-cs[Trin_VstcoreProgrammingControlsExcel#18](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/ChartOptions.cs#18)]

## <a name="add-the-user-control-to-the-worksheet"></a>Přidat uživatelský ovládací prvek do listu
 Při sestavování řešení se nový uživatelský ovládací prvek automaticky přidá do **sady nástrojů**. Ovládací prvek pak můžete přetáhnout ze sady **nástrojů** na list.

### <a name="to-add-the-user-control-your-worksheet"></a>Přidání uživatelského ovládacího prvku list

1. V nabídce **Sestavení** klikněte na **Sestavit řešení**.

     Uživatelský ovládací prvek **ChartOptions** se přidá do **sady nástrojů**.

2. V **Průzkumník řešení** klikněte pravým tlačítkem na **List1. vb** nebo **Sheet1.cs** a potom klikněte na tlačítko **Návrhář zobrazení**.

3. Přetáhněte ovládací prvek **ChartOptions** ze **sady nástrojů** na list.

     Do projektu se přidá nový ovládací prvek s názvem `my_Excel_Chart_ChartOptions1` .

4. Změňte název ovládacího prvku na **ChartOptions1**.

## <a name="change-the-chart-type"></a>Změnit typ grafu
 Chcete-li změnit typ grafu, vytvořte obslužnou rutinu události, která nastaví styl podle možnosti vybrané v uživatelském ovládacím prvku.

### <a name="to-change-the-type-of-chart-that-is-displayed-in-the-worksheet"></a>Chcete-li změnit typ grafu, který je zobrazen na listu

1. Přidejte do třídy následující obslužnou rutinu události `Sheet1` .

     [!code-vb[Trin_VstcoreProgrammingControlsExcel#19](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#19)]
     [!code-cs[Trin_VstcoreProgrammingControlsExcel#19](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#19)]

2. V jazyce C# je nutné přidat obslužnou rutinu události pro uživatelský ovládací prvek do <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> události, jak je znázorněno níže. Informace o tom, jak vytvořit obslužné rutiny událostí, naleznete v tématu [How to: Create event handlers in Office Projects](../vsto/how-to-create-event-handlers-in-office-projects.md).

     [!code-cs[Trin_VstcoreProgrammingControlsExcel#20](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#20)]

## <a name="test-the-application"></a>Testování aplikace
 Nyní můžete otestovat sešit, abyste ověřili, že je graf správně ve stylu, když vyberete přepínač.

### <a name="to-test-your-workbook"></a>Test sešitu

1. Stisknutím klávesy **F5** spusťte projekt.

2. Vyberte různé přepínače.

3. Potvrďte, že se styl grafu změní tak, aby odpovídal výběru.

## <a name="next-steps"></a>Další kroky
 Tento názorný postup ukazuje základy používání přepínačů a stylů grafů na listech. Tady jsou některé úkoly, které mohou být další:

- Nasazení projektu. Další informace najdete v tématu [nasazení řešení pro Office](../vsto/deploying-an-office-solution.md).

- Použití tlačítka k naplnění textového pole. Další informace najdete v tématu [Návod: zobrazení textu v textovém poli na listu pomocí tlačítka](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-worksheet-using-a-button.md).

- Změňte formátování listu pomocí zaškrtávacích políček. Další informace najdete v tématu [Návod: Změna formátování listu pomocí ovládacích prvků CheckBox](../vsto/walkthrough-changing-worksheet-formatting-using-checkbox-controls.md).

## <a name="see-also"></a>Viz také
- [Návody pomocí Excelu](../vsto/walkthroughs-using-excel.md)
