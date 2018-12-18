---
title: 'Návod: Aktualizace grafu v dokumentu s použitím přepínačů'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], updating using controls
- controls [Office development in Visual Studio], updating documents
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 5e82c50c83a8824b4570779034b0480aa0615a30
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49904671"
---
# <a name="walkthrough-update-a-chart-in-a-document-using-radio-buttons"></a>Návod: Aktualizace grafu v dokumentu s použitím přepínačů
  Tento návod ukazuje, jak pomocí přepínačů v přizpůsobení úrovni dokumentu pro aplikaci Microsoft Office Word a poskytuje tak uživatelům možnost vybrat styly grafu v dokumentu.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 Tento návod znázorňuje následující úlohy:  
  
- Přidání grafu do dokumentu v projektu úrovni dokumentu v době návrhu.  
  
- Seskupování přepínačů jejich přidáním do uživatelského ovládacího prvku.  
  
- Změna stylu grafu, pokud je vybrána možnost.  
  
  Výsledek jako úplnou vzorovou najdete v ukázce ovládací prvky aplikace Word v [Office Ukázky a návody vývoje](../vsto/office-development-samples-and-walkthroughs.md).  
  
  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Požadavky  
 K dokončení tohoto návodu budete potřebovat následující komponenty:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] nebo [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].  
  
## <a name="create-the-project"></a>Vytvoření projektu  
 Prvním krokem je vytvoření projektu dokumentu aplikace Word.  
  
### <a name="to-create-a-new-project"></a>Chcete-li vytvořit nový projekt  
  
1.  Vytvoření projektu Wordového dokumentu s názvem **Moje možnosti grafu**. V průvodci vyberte **vytvoříte nový textový dokument**. Další informace najdete v tématu [postupy: vytvoření Office projekty v sadě Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     Visual Studio otevře nový Wordový dokument v návrháři a přidá **Moje možnosti grafu** projektu **Průzkumníka řešení**.  
  
## <a name="add-a-chart-to-the-document"></a>Přidání grafu do dokumentu  
  
### <a name="to-add-a-chart"></a>Chcete-li přidat graf  
  
1.  V dokumentu aplikace Word, který je hostován v návrháři aplikace Visual Studio na pásu karet, klepněte **vložit** kartu.  
  
2.  V **Text** klikněte na položku **vložit objekt** tlačítko rozevíracího seznamu a klikněte na tlačítko **objekt**.  
  
     **Objekt** zobrazí se dialogové okno.  
  
3.  V **typ objektu** seznamu **vytvořit nový** kartu, vyberte možnost **Microsoft graf** a potom klikněte na tlačítko **OK**.  
  
     Graf je přidán do dokumentu na pozici kurzoru a **datový list** zobrazí se okno s daty výchozí.  
  
4.  Zavřít **datový list** okna přijměte výchozí hodnoty v grafu a klikněte do dokumentu můžete fokus přesunout mimo grafu.  
  
5.  Klikněte pravým tlačítkem na graf a potom klikněte na tlačítko **formát objektu**.  
  
6.  Na **rozložení** karty **formát objektu** dialogu **čtverec** a klikněte na tlačítko **OK**.  
  
## <a name="add-a-user-control-to-the-project"></a>Přidat uživatelský ovládací prvek do projektu  
 Přepínací tlačítka v dokumentu se vzájemně nevylučují ve výchozím nastavení. Můžete nastavit, je správně je tím přidáte do uživatelského ovládacího prvku a pak zápis kódu pro ovládací prvek výběru funkce.  
  
### <a name="to-add-a-user-control"></a>Chcete-li přidat uživatelský ovládací prvek  
  
1.  Vyberte **Moje možnosti grafu** projekt **Průzkumníka řešení**.  
  
2.  Na **projektu** nabídky, klikněte na tlačítko **přidat novou položku**.  
  
3.  V **přidat novou položku** dialogové okno, klikněte na tlačítko **uživatelský ovládací prvek**, ovládací prvek pojmenujte **ChartOptions,** a klikněte na tlačítko **přidat**.  
  
### <a name="to-add-windows-form-controls-to-the-user-control"></a>Chcete-li přidat ovládací prvky formuláře Windows do uživatelského ovládacího prvku  
  
1.  Pokud uživatelský ovládací prvek není viditelný v návrháři, klikněte dvakrát na **ChartOptions** v **Průzkumníka řešení**.  
  
2.  Z **běžné ovládací prvky** karty **nástrojů**, přetáhněte první **přepínač** řídit uživatelského ovládacího prvku a změňte následující vlastnosti.  
  
    |Vlastnost|Hodnota|  
    |--------------|-----------|  
    |**Jméno**|**columnChart**|  
    |**Text**|**Sloupcový graf**|  
  
3.  Přidejte druhý **přepínač** uživateli určit a změnit následující vlastnosti.  
  
    |Vlastnost|Hodnota|  
    |--------------|-----------|  
    |**Jméno**|**barChart**|  
    |**Text**|**Pruhový graf**|  
  
4.  Přidat třetí **přepínač** uživateli určit a změnit následující vlastnosti.  
  
    |Vlastnost|Hodnota|  
    |--------------|-----------|  
    |**Jméno**|**lineChart**|  
    |**Text**|**Spojnicový graf**|  
  
5.  Přidat čtvrtý **přepínač** uživateli určit a změnit následující vlastnosti.  
  
    |Vlastnost|Hodnota|  
    |--------------|-----------|  
    |**Jméno**|**areaBlockChart**|  
    |**Text**|**Plošný graf bloku**|  
  
## <a name="add-references"></a>Přidání odkazů  
 Pro přístup k grafu z uživatelského ovládacího prvku na dokument, musí mít odkaz na `Microsoft.Office.Interop.Graph` sestavení ve vašem projektu.  
  
### <a name="to-add-a-reference-to-the-microsoftofficeinteropgraph-assembly"></a>Chcete-li přidat odkaz na sestavení Microsoft.Office.Interop.Graph  
  
1.  Na **projektu** nabídky, klikněte na tlačítko **přidat odkaz**.  
  
     **Přidat odkaz** zobrazí se dialogové okno.  
  
2.  Na **.NET** kartu, vyberte možnost **Microsoft.Office.Interop.Graph** a klikněte na tlačítko **OK**. Vyberte 14.0.0.0 verzi sestavení.  
  
## <a name="change-the-chart-style-when-a-radio-button-is-selected"></a>Změna stylu grafu vyberete přepínací tlačítko  
 Chcete-li správně funguje, vytvořte veřejná událost na uživatelský ovládací prvek tlačítka, přidejte vlastnost nastavit typ výběru a postup pro vytvoření `CheckedChanged` událostí všech přepínačů.  
  
### <a name="to-create-an-event-and-property-on-a-user-control"></a>Vytvoření události a vlastnost na uživatelský ovládací prvek  
  
1.  V **Průzkumníka řešení**, klikněte pravým tlačítkem na uživatelský ovládací prvek a potom klikněte na tlačítko **zobrazit kód**.  
  
2.  Přidejte kód k vytvoření `SelectionChanged` událostí a `Selection` vlastnost `ChartOptions` třídy.  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#9](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ChartOptions.cs#9)]
     [!code-vb[Trin_VstcoreProgrammingControlsWord#9](../vsto/codesnippet/VisualBasic/my chart options/ChartOptions.vb#9)]  
  
### <a name="to-handle-the-checkedchange-event-of-the-radio-buttons"></a>Zpracování události CheckedChange přepínačů  
  
1.  Nastavit typ grafu `CheckedChanged` obslužná rutina události `areaBlockChart` přepínač a následně vyvolání události.  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#10](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ChartOptions.cs#10)]
     [!code-vb[Trin_VstcoreProgrammingControlsWord#10](../vsto/codesnippet/VisualBasic/my chart options/ChartOptions.vb#10)]  
  
2.  Nastavit typ grafu `CheckedChanged` obslužná rutina události `barChart` přepínač.  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#11](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ChartOptions.cs#11)]
     [!code-vb[Trin_VstcoreProgrammingControlsWord#11](../vsto/codesnippet/VisualBasic/my chart options/ChartOptions.vb#11)]  
  
3.  Nastavit typ grafu `CheckedChanged` obslužná rutina události `columnChart` přepínač.  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#12](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ChartOptions.cs#12)]
     [!code-vb[Trin_VstcoreProgrammingControlsWord#12](../vsto/codesnippet/VisualBasic/my chart options/ChartOptions.vb#12)]  
  
4.  Nastavit typ grafu `CheckedChanged` obslužná rutina události `lineChart` přepínač.  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#13](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ChartOptions.cs#13)]
     [!code-vb[Trin_VstcoreProgrammingControlsWord#13](../vsto/codesnippet/VisualBasic/my chart options/ChartOptions.vb#13)]  
  
5.  V jazyce C# je nutné přidat obslužné rutiny událostí pro přepínací tlačítka. Můžete přidat kód, který `ChartOptions` konstruktor pod volání `InitializeComponent`. Informace o vytváření obslužných rutin událostí, naleznete v tématu [postupy: vytváření obslužných rutin událostí v projektech pro systém Office](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#14](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ChartOptions.cs#14)]  
  
## <a name="add-the-user-control-to-the-document"></a>Přidat uživatelský ovládací prvek v dokumentu  
 Při sestavování řešení se automaticky přidá do nového uživatelského ovládacího prvku **nástrojů**. Potom můžete přetáhnout ovládací prvek z **nástrojů** do dokumentu.  
  
### <a name="to-add-the-user-control-your-document"></a>Chcete-li přidat uživatelský ovládací prvek dokumentu  
  
1.  Na **sestavení** nabídky, klikněte na tlačítko **sestavit řešení**.  
  
     **ChartOptions** uživatelský ovládací prvek je přidán do **nástrojů**.  
  
2.  V **Průzkumníka řešení**, klikněte pravým tlačítkem na **ThisDocument.vb** nebo **ThisDocument.cs**a potom klikněte na tlačítko **Návrhář zobrazení**.  
  
3.  Přetáhněte `ChartOptions` ovládacího prvku **nástrojů** v dokumentu.  
  
     V **vlastnosti** okna, název ovládacího prvku, který jste právě přidán do dokumentu `ChartOptions1`.  
  
## <a name="change-the-chart-type"></a>Změnit typ grafu  
 Vytvořte obslužnou rutinu události, chcete-li změnit typ grafu podle možnosti vybrané v uživatelského ovládacího prvku.  
  
### <a name="to-change-the-type-of-chart-that-is-displayed-in-the-document"></a>Chcete-li změnit typ grafu, který se zobrazí v dokumentu  
  
1.  Přidejte následující obslužnou rutinu události pro `ThisDocument` třídy.  
  
     [!code-vb[Trin_VstcoreProgrammingControlsWord#15](../vsto/codesnippet/VisualBasic/my chart options/ThisDocument.vb#15)]
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#15](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#15)]  
  
2.  V C#, je nutné přidat obslužnou rutinu události pro uživatelský ovládací prvek <xref:Microsoft.Office.Tools.Word.Document.Startup> událostí.  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#16](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#16)]  
  
## <a name="test-the-application"></a>Testování aplikace  
 Teď můžete otestovat váš dokument, abyste měli jistotu, že je vyberete tlačítko přepínače správně aktualizován styl grafu.  
  
### <a name="to-test-your-document"></a>K otestování vašeho dokumentu  
  
1.  Stisknutím klávesy **F5** ke spuštění projektu.  
  
2.  Vyberte různé přepínače.  
  
3.  Potvrďte, že styl grafu se změní tak, aby odpovídaly výběr.  
  
## <a name="next-steps"></a>Další kroky  
 Tady jsou některé úlohy, které by mohl pocházet Další:  
  
-   Pomocí tlačítka k naplnění textové pole. Další informace najdete v tématu [návod: zobrazení textu v textovém poli v dokumentu s použitím tlačítka](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-document-using-a-button.md).  
  
-   Změna formátování tak, že vyberete styl pole se seznamem. Další informace najdete v tématu [návod: Změna formátování dokumentů s použitím ovládacích prvků CheckBox](../vsto/walkthrough-changing-document-formatting-using-checkbox-controls.md).  
  
## <a name="see-also"></a>Viz také:  
 [Návody pro aplikaci Word](../vsto/walkthroughs-using-word.md)   
 [Ukázky vývoje pro Office a názorné postupy](../vsto/office-development-samples-and-walkthroughs.md)   
 [Omezení ovládacích prvků Windows Forms v dokumentech Office](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)  
  
  