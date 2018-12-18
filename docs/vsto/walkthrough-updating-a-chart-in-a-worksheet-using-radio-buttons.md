---
title: 'Návod: Aktualizace grafu na listu s použitím přepínačů'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets, updating using managed controls
- controls [Office development in Visual Studio], updating worksheets
- worksheets, using radio buttons
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 5aff631d8c9b6bd65b8ae91c5d936d2669764791
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49866438"
---
# <a name="walkthrough-updating-a-chart-in-a-worksheet-using-radio-buttons"></a>Návod: Aktualizace grafu na listu s použitím přepínačů
  Tento návod ukazuje základy používání přepínací tlačítka na list aplikace Microsoft Office Excel poskytnout způsob, jak rychle přepínat mezi možnostmi uživatele. V takovém případě možnosti změnit styl grafu.  

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  

 Výsledek jako úplnou vzorovou najdete v ukázce ovládací prvky aplikace Excel v [Office Ukázky a návody vývoje](../vsto/office-development-samples-and-walkthroughs.md).  

 Tento návod znázorňuje následující úlohy:  

-   Přidání skupiny přepínačů na list.  

-   Změna stylu grafu, pokud je vybrána možnost.  

> [!NOTE]  
>  Váš počítač může v následujících pokynech zobrazovat odlišné názvy nebo umístění některých prvků uživatelského rozhraní sady Visual Studio. Tyto prvky jsou určeny edicí sady Visual Studio a použitým nastavením. Další informace najdete v tématu [přizpůsobení integrovaného vývojového prostředí sady Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  

## <a name="prerequisites"></a>Požadavky  
 K dokončení tohoto návodu budete potřebovat následující komponenty:  

-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  

-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] nebo [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].  

## <a name="add-a-chart-to-a-worksheet"></a>Přidání grafu na listu  
 Můžete vytvořit projekt Excelový sešit, který upravuje existující sešit. V tomto názorném postupu se přidat graf sešitu a pak použít tento sešit v novém řešení aplikace Excel. Zdroj dat v tomto návodu je to list s názvem **Data grafu**.  

### <a name="to-add-the-data"></a>Můžete přidat data  

1. Otevřete aplikaci Microsoft Excel.  

2. Klikněte pravým tlačítkem myši **Sheet3 –** kartu a potom klikněte na tlačítko **přejmenovat** v místní nabídce.  

3. Přejmenujte list na **Data grafu**.  

4. Přidejte následující data do **Data grafu** s buňky A4 se levý horní roh a E8 pravého dolního rohu.  

   ||1.|2. ČTVRTLETÍ|3. ČTVRTLETÍ|4.|  
   |-|--------|--------|--------|--------|  
   |– Západ|500|550|550|600|  
   |– Východ|600|625|675|700|  
   |– sever|450|470|490|510|  
   |– Jih|800|750|775|790|  

   V dalším kroku přidáte graf první sešit zobrazit data.  

### <a name="to-add-a-chart-in-excel"></a>Přidání grafu v aplikaci Excel  

1.  Na **vložit** kartě **grafy** klikněte na možnost **sloupec**a potom klikněte na tlačítko **všechny typy grafů**.  

2.  V **vložit graf** dialogové okno, klikněte na tlačítko **OK**.  

3.  Na **návrhu** kartě **Data** klikněte na možnost **vybrat Data**.  

4.  V **vybrat zdroj dat** dialogové okno, kliknutím na webu **Chartdata rozsah** a zrušte všechny výchozí výběr.  

5.  V **Data grafu** listu, vyberte blok buněk, který obsahuje čísla, která zahrnuje A4 v horním levém rohu E8 v pravém dolním rohu.  

6.  V **vybrat zdroj dat** dialogové okno, klikněte na tlačítko **OK**.  

7.  Změna umístění grafu tak, aby pravém horním rohu v souladu s buňky **E2**.  

8.  Uložte soubor na jednotce C a pojmenujte ho **ExcelChart.xlsx**.  

9. Ukončete aplikaci Excel.  

## <a name="create-a-new-project"></a>Vytvoření nového projektu  
 V tomto kroku vytvoříte projekt sešitu aplikace Excel na základě **ExcelGraf** sešitu.  

### <a name="to-create-a-new-project"></a>Chcete-li vytvořit nový projekt  

1.  Vytvořte projekt sešitu aplikace Excel s názvem **Můj Excelový graf**. V průvodci vyberte **zkopírovat existující dokument**.  

     Další informace najdete v tématu [postupy: vytvoření Office projekty v sadě Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  

2.  Klikněte na tlačítko **Procházet** tlačítko a přejděte do sešitu, který jste vytvořili dříve v tomto návodu.  

3.  Klikněte na tlačítko **OK**.  

     Visual Studio otevře nový sešit aplikace Excel v návrháři a přidá **Můj Excelový graf** projektu **Průzkumníka řešení**.  

## <a name="set-properties-of-the-chart"></a>Nastavit vlastnosti grafu  
 Když vytvoříte nový projekt Excelový sešit, který používá existující sešit, hostitelské ovládací prvky jsou vytvořeny automaticky pro všechny pojmenované oblasti, seznam objektů a grafy v sešitu. Můžete změnit název <xref:Microsoft.Office.Tools.Excel.Chart> ovládacího prvku s použitím **vlastnosti** okna.  

### <a name="to-change-the-name-of-the-chart-control"></a>Chcete-li změnit název ovládacího prvku grafu  

1.  Vyberte <xref:Microsoft.Office.Tools.Excel.Chart> ovládací prvek v návrháři a změnit následující vlastnosti v **vlastnosti** okna.  

    |Vlastnost|Hodnota|  
    |--------------|-----------|  
    |**Jméno**|**dataChart**|  
    |**HasLegend**|**false**|  

## <a name="add-controls"></a>Přidání ovládacích prvků  
 Tento list používá přepínačů a poskytuje tak uživatelům způsob, jak rychle změnit styl grafu. Ale přepínačů musí být výhradně – při výběru tlačítka lze vybrat žádné jiné tlačítko ve skupině ve stejnou dobu. Toto chování není standardní ve výchozím nastavení při přidání několika přepínačů na list.  

 Jeden způsob, jak přidat toto chování je k seskupení přepínačů v uživatelský ovládací prvek, napište svůj kód za uživatelský ovládací prvek a potom přidat uživatelský ovládací prvek do listu.  

### <a name="to-add-a-user-control"></a>Chcete-li přidat uživatelský ovládací prvek  

1.  Vyberte **Můj Excelový graf** projekt **Průzkumníka řešení**.  

2.  Na **projektu** nabídky, klikněte na tlačítko **přidat novou položku**.  

3.  V **přidat novou položku** dialogové okno, klikněte na tlačítko **uživatelský ovládací prvek**, ovládací prvek pojmenujte **ChartOptions,** a klikněte na tlačítko **přidat**.  

### <a name="to-add-radio-buttons-to-the-user-control"></a>Přidání přepínačů uživatelského ovládacího prvku  

1. Pokud uživatelský ovládací prvek není viditelný v návrháři, klikněte dvakrát na **ChartOptions** v **Průzkumníka řešení**.  

2. Z **běžné ovládací prvky** karty **nástrojů**, přetáhněte **přepínač** řídit uživatelského ovládacího prvku a změňte následující vlastnosti.  


   | Vlastnost | Hodnota |
   |----------|------------------|
   | **Jméno** | **columnChart** |
   | **Text** | **Sloupcový graf** |


3. Přidejte druhé tlačítko přepínače do uživatelského ovládacího prvku a změňte následující vlastnosti.  


   | Vlastnost | Hodnota |
   |----------|---------------|
   | **Jméno** | **barChart** |
   | **Text** | **Pruhový graf** |


4. Přidejte třetí přepínač uživatelského ovládacího prvku a změňte následující vlastnosti.  


   | Vlastnost | Hodnota |
   |----------|----------------|
   | **Jméno** | **lineChart** |
   | **Text** | **Spojnicový graf** |


5. Přidejte čtvrtý přepínač uživatelského ovládacího prvku a změňte následující vlastnosti.  

   |Vlastnost|Hodnota|  
   |--------------|-----------|  
   |**Jméno**|**areaBlockChart**|  
   |**Text**|**Plošný graf bloku**|  

   Dále napište kód pro aktualizaci grafu, když dojde ke kliknutí na tlačítko přepínače.  

## <a name="change-the-chart-style-when-a-radio-button-is-selected"></a>Změna stylu grafu vyberete přepínací tlačítko  
 Nyní můžete přidat kód pro změnu stylu grafu. Veřejná událost vytvoření uživatelského ovládacího prvku, přidejte vlastnost, která má nastaven typ výběru a vytvořit obslužnou rutinu události pro `CheckedChanged` událostí všech přepínačů.  

### <a name="to-create-an-event-and-property-on-a-user-control"></a>Vytvoření události a vlastnost na uživatelský ovládací prvek  

1.  V **Průzkumníka řešení**, klikněte pravým tlačítkem na uživatelský ovládací prvek a potom klikněte na tlačítko **zobrazit kód**.  

2.  Přidejte kód, který `ChartOptions` třídy za účelem vytvoření `SelectionChanged` událostí a `Selection` vlastnost.  

     [!code-vb[Trin_VstcoreProgrammingControlsExcel#13](../vsto/codesnippet/VisualBasic/my excel chart/ChartOptions.vb#13)]
     [!code-cs[Trin_VstcoreProgrammingControlsExcel#13](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/ChartOptions.cs#13)]  

### <a name="to-handle-the-checkedchanged-event-of-the-radio-buttons"></a>Chcete zpracovat událost CheckedChanged přepínačů  

1.  Nastavit typ grafu `CheckedChanged` obslužná rutina události `areaBlockChart` přepínač a následně vyvolání události.  

     [!code-vb[Trin_VstcoreProgrammingControlsExcel#14](../vsto/codesnippet/VisualBasic/my excel chart/ChartOptions.vb#14)]
     [!code-cs[Trin_VstcoreProgrammingControlsExcel#14](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/ChartOptions.cs#14)]  

2.  Nastavit typ grafu `CheckedChanged` obslužná rutina události `barChart` přepínač.  

     [!code-vb[Trin_VstcoreProgrammingControlsExcel#15](../vsto/codesnippet/VisualBasic/my excel chart/ChartOptions.vb#15)]
     [!code-cs[Trin_VstcoreProgrammingControlsExcel#15](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/ChartOptions.cs#15)]  

3.  Nastavit typ grafu `CheckedChanged` obslužná rutina události `columnChart` přepínač.  

     [!code-vb[Trin_VstcoreProgrammingControlsExcel#16](../vsto/codesnippet/VisualBasic/my excel chart/ChartOptions.vb#16)]
     [!code-cs[Trin_VstcoreProgrammingControlsExcel#16](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/ChartOptions.cs#16)]  

4.  Nastavit typ grafu `CheckedChanged` obslužná rutina události `lineChart` přepínač.  

     [!code-vb[Trin_VstcoreProgrammingControlsExcel#17](../vsto/codesnippet/VisualBasic/my excel chart/ChartOptions.vb#17)]
     [!code-cs[Trin_VstcoreProgrammingControlsExcel#17](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/ChartOptions.cs#17)]  

5.  V jazyce C# je nutné přidat obslužné rutiny událostí pro přepínací tlačítka. Můžete přidat kód, který `ChartOptions` konstruktor pod volání `InitializeComponent`. Informace o tom, jak vytváření obslužných rutin událostí, naleznete v tématu [postupy: vytváření obslužných rutin událostí v projektech pro systém Office](../vsto/how-to-create-event-handlers-in-office-projects.md).  

     [!code-cs[Trin_VstcoreProgrammingControlsExcel#18](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/ChartOptions.cs#18)]  

## <a name="add-the-user-control-to-the-worksheet"></a>Přidat uživatelský ovládací prvek do listu  
 Při sestavování řešení se automaticky přidá do nového uživatelského ovládacího prvku **nástrojů**. Potom můžete přetáhnout ovládací prvek z **nástrojů** do listu.  

### <a name="to-add-the-user-control-your-worksheet"></a>Chcete-li přidat uživatelský ovládací prvek list  

1.  Na **sestavení** nabídky, klikněte na tlačítko **sestavit řešení**.  

     **ChartOptions** uživatelský ovládací prvek je přidán do **nástrojů**.  

2.  V **Průzkumníka řešení**, klikněte pravým tlačítkem na **Sheet1.vb** nebo **Sheet1.cs**a potom klikněte na tlačítko **Návrhář zobrazení**.  

3.  Přetáhněte **ChartOptions** ovládacího prvku **nástrojů** do listu.  

     Nový ovládací prvek s názvem `my_Excel_Chart_ChartOptions1` se přidá do vašeho projektu.  

4.  Změňte název ovládacího prvku na **ChartOptions1**.  

## <a name="change-the-chart-type"></a>Změnit typ grafu  
 Chcete-li změnit typ grafu, vytvořte obslužnou rutinu události, která nastavuje styl podle možnosti vybrané v uživatelského ovládacího prvku.  

### <a name="to-change-the-type-of-chart-that-is-displayed-in-the-worksheet"></a>Chcete-li změnit typ grafu, který se zobrazí v listu  

1.  Přidejte následující obslužnou rutinu události pro `Sheet1` třídy.  

     [!code-vb[Trin_VstcoreProgrammingControlsExcel#19](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#19)]
     [!code-cs[Trin_VstcoreProgrammingControlsExcel#19](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#19)]  

2.  V jazyce C#, musíte přidat obslužnou rutinu události pro uživatelský ovládací prvek <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> události, jak je znázorněno níže. Informace o tom, jak vytváření obslužných rutin událostí, naleznete v tématu [postupy: vytváření obslužných rutin událostí v projektech pro systém Office](../vsto/how-to-create-event-handlers-in-office-projects.md).  

     [!code-cs[Trin_VstcoreProgrammingControlsExcel#20](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#20)]  

## <a name="test-the-application"></a>Testování aplikace  
 Teď můžete otestovat sešit k ověření, že grafu je navržen tak správně, když vyberete tlačítko přepínače.  

### <a name="to-test-your-workbook"></a>K otestování vašeho sešitu  

1.  Stisknutím klávesy **F5** ke spuštění projektu.  

2.  Vyberte různé přepínače.  

3.  Potvrďte, že styl grafu se změní tak, aby odpovídaly výběr.  

## <a name="next-steps"></a>Další kroky  
 Tento návod ukazuje základy používání přepínacích tlačítek a styly grafu na listech. Tady jsou některé úlohy, které by mohl pocházet Další:  

-   Nasazení projektu. Další informace najdete v tématu [nasazení řešení Office](../vsto/deploying-an-office-solution.md).  

-   Pomocí tlačítka k naplnění textové pole. Další informace najdete v tématu [návod: zobrazení textu v textovém poli na listu s použitím tlačítka](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-worksheet-using-a-button.md).  

-   Změna formátování v listu pomocí zaškrtávacích políček. Další informace najdete v tématu [návod: Změna formátování listů s použitím ovládacích prvků CheckBox](../vsto/walkthrough-changing-worksheet-formatting-using-checkbox-controls.md).  

## <a name="see-also"></a>Viz také:  
 [Návody pro aplikaci Excel](../vsto/walkthroughs-using-excel.md)  

