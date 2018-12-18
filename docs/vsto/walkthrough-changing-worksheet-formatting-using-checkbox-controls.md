---
title: 'Návod: Změna formátování listů s použitím ovládacích prvků CheckBox'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets, changing formatting using managed controls
- worksheets, check box controls
- controls [Office development in Visual Studio], adding to worksheets
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: fae4a6cc21264e62c5a12db79c8a937f0a366314
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49843532"
---
# <a name="walkthrough-change-worksheet-formatting-using-checkbox-controls"></a>Návod: Změna formátování listů s použitím ovládacích prvků CheckBox
  Tento návod ukazuje základy používání zaškrtávacích políček na list aplikace Microsoft Office Excel Změna formátování. Nástroje pro vývoj pro Office v sadě Visual Studio použije k vytvoření a přidání kódu do projektu. Výsledek jako úplnou vzorovou najdete v ukázce ovládací prvky aplikace Excel v [Office Ukázky a návody vývoje](../vsto/office-development-samples-and-walkthroughs.md).  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 V tomto návodu se dozvíte, jak:  
  
-   Přidáte text a ovládacích prvků na list.  
  
-   Pokud je vybrána možnost formátování textu.  
  
-   Otestování vašeho projektu.  
  
> [!NOTE]  
>  Váš počítač může v následujících pokynech zobrazovat odlišné názvy nebo umístění některých prvků uživatelského rozhraní sady Visual Studio. Tyto prvky jsou určeny edicí sady Visual Studio a použitým nastavením. Další informace najdete v tématu [přizpůsobení integrovaného vývojového prostředí sady Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="prerequisites"></a>Požadavky  
 K dokončení tohoto návodu budete potřebovat následující komponenty:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] nebo [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].  
  
## <a name="create-the-project"></a>Vytvoření projektu  
 V tomto kroku vytvoříte projekt sešitu aplikace Excel s použitím sady Visual Studio.  
  
### <a name="to-create-a-new-project"></a>Chcete-li vytvořit nový projekt  
  
1.  Vytvořte projekt sešitu aplikace Excel s názvem **formátování v mé aplikaci Excel**. Ujistěte se, že **vytvoříte nový textový dokument** zaškrtnuto. Další informace najdete v tématu [postupy: vytvoření Office projekty v sadě Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     Visual Studio otevře nový sešit aplikace Excel v návrháři a přidá **formátování v mé aplikaci Excel** projektu **Průzkumníka řešení**.  
  
## <a name="add-text-and-controls-to-the-worksheet"></a>Přidání textu a ovládacích prvků na list  
 V tomto návodu budete potřebovat tři <xref:Microsoft.Office.Tools.Excel.Controls.CheckBox> ovládací prvky a některé text <xref:Microsoft.Office.Tools.Excel.NamedRange> ovládacího prvku.  
  
### <a name="to-add-three-check-boxes"></a>Chcete-li přidat tři políčka  
  
1.  Ověřte, zda je sešit otevřít v návrháři aplikace Visual Studio a které `Sheet1` je otevřený.  
  
2.  Z **běžné ovládací prvky** karty **nástrojů**, přetáhněte <xref:Microsoft.Office.Tools.Excel.Controls.CheckBox> ovládacího prvku na nebo blízko ní buňky **B2** v **List1**.  
  
3.  Z **zobrazení** nabídce vyberte možnost **vlastnosti** okna.  
  
4.  Ujistěte se, že **Checkbox1** je viditelný v objektu název seznamu **vlastnosti** okna a změnit následující vlastnosti:  
  
    |Vlastnost|Hodnota|  
    |--------------|-----------|  
    |**Jméno**|**applyBoldFont**|  
    |**Text**|**Tučné**|  
  
5.  Přetáhněte druhý zaškrtávací políčko na nebo blízko ní buňky **B4** a změnit následující vlastnosti:  
  
    |Vlastnost|Hodnota|  
    |--------------|-----------|  
    |**Jméno**|**applyItalicFont**|  
    |**Text**|**Kurzíva**|  
  
6.  Přetáhněte třetí zaškrtávací políčko na nebo blízko ní buňky **B6** a změnit následující vlastnosti:  
  
    |Vlastnost|Hodnota|  
    |--------------|-----------|  
    |**Jméno**|**applyUnderlineFont**|  
    |**Text**|**Podtržení**|  
  
7.  Vyberte všechny tři zaškrtávací políčka při držení **Ctrl** klíč.  
  
8.  Ve skupině uspořádat kartě formátu v Excelu klikněte na tlačítko **zarovnat**a potom klikněte na tlačítko **Zarovnat doleva**.  
  
     Tři zaškrtávací políčka jsou zarovnány na levé straně na pozici první ovládací prvek, který jste vybrali.  
  
     V dalším kroku při přetahování <xref:Microsoft.Office.Tools.Excel.NamedRange> ovládacího prvku do listu.  
  
    > [!NOTE]  
    >  Můžete také přidat <xref:Microsoft.Office.Tools.Excel.NamedRange> ovládacího prvku tak, že zadáte **textFont** do **název** pole.  
  
#### <a name="to-add-text-to-a-namedrange-control"></a>Chcete-li přidat text do ovládacího prvku NamedRange  
  
1. Z **ovládací prvky Excelu** kartu na panelu nástrojů přetáhněte <xref:Microsoft.Office.Tools.Excel.NamedRange> ovládacího prvku do buňky **B9**.  
  
2. Ověřte, že **$B$ 9** se zobrazí v upravitelné textové pole a buňka **B9** zaškrtnuto. Pokud není, klikněte na buňku **B9** ji vyberte.  
  
3. Klikněte na tlačítko **OK**.  
  
4. Buňka **B9** stane oblast s názvem `NamedRange1`.  
  
    Není by na listu, ale `NamedRange1` se zobrazí v **pole název** (přímo nad list na levé straně) při buňky **B9** zaškrtnuto.  
  
5. Ujistěte se, že **NamedRange1** je viditelný v objektu název seznamu **vlastnosti** okna a změnit následující vlastnosti:  
  
   |Vlastnost|Hodnota|  
   |--------------|-----------|  
   |**Jméno**|**textFont**|  
   |**Hodnota2**|**Klikněte na zaškrtávací políčko, chcete-li změnit formátování tento text.**|  
  
   Dále napište kód k formátování textu, pokud je vybrána možnost.  
  
## <a name="format-the-text-when-an-option-is-selected"></a>Pokud je vybrána možnost formátování textu  
 V této části napíšete kód tak, že když uživatel vybere možnost formátování, se změní na formát textu v listu.  
  
### <a name="to-change-formatting-when-a-check-box-is-selected"></a>Chcete-li změnit formátování při zaškrtávací políčko zaškrtnuto  
  
1.  Klikněte pravým tlačítkem na **List1**a potom klikněte na tlačítko **zobrazit kód** v místní nabídce.  
  
2.  Přidejte následující kód, který <xref:System.Windows.Forms.Control.Click> obslužná rutina události `applyBoldFont` zaškrtávací políčko:  
  
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#7](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#7)]
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#7](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#7)]  
  
3.  Přidejte následující kód, který <xref:System.Windows.Forms.Control.Click> obslužná rutina události `applyItalicFont` zaškrtávací políčko:  
  
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#8](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#8)]
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#8](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#8)]  
  
4.  Přidejte následující kód, který <xref:System.Windows.Forms.Control.Click> obslužná rutina události `applyUnderlineFont` zaškrtávací políčko:  
  
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#9](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#9)]
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#9](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#9)]  
  
5.  V jazyce C#, je nutné přidat obslužné rutiny událostí pro políček <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> události, jak je znázorněno níže. Informace o vytváření obslužných rutin událostí, naleznete v tématu [postupy: vytváření obslužných rutin událostí v projektech pro systém Office](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#10](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#10)]  
  
## <a name="test-the-application"></a>Testování aplikace  
 Teď můžete otestovat sešitu, abyste měli jistotu, že text je správný při zaškrtněte nebo zrušte zaškrtnutí políčka.  
  
### <a name="to-test-your-workbook"></a>K otestování vašeho sešitu  
  
1.  Stisknutím klávesy **F5** ke spuštění projektu.  
  
2.  Vyberte nebo zrušte zaškrtnutí políčka.  
  
3.  Potvrďte, že je správně formátovaný text.  
  
## <a name="next-steps"></a>Další kroky  
 Tento návod ukazuje základy používání zaškrtávacích políček a formátování textu na listech aplikace Excel. Tady jsou některé úlohy, které by mohl pocházet Další:  
  
-   Nasazení projektu. Další informace najdete v tématu [nasazení řešení Office s použitím technologie ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md).  
-   Pomocí tlačítka k naplnění textové pole. Další informace najdete v tématu [návod: zobrazení textu v textovém poli na listu s použitím tlačítka](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-worksheet-using-a-button.md).  
  
## <a name="see-also"></a>Viz také:  
 [Návody pro aplikaci Excel](../vsto/walkthroughs-using-excel.md)   
 [Namedrange – ovládací prvek](../vsto/namedrange-control.md)   
 [Omezení ovládacích prvků Windows Forms v dokumentech Office](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)  
  