---
title: 'Návod: Zobrazení textu v textovém poli na listu s použitím tlačítka'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- text [Office development in Visual Studio], displaying worksheets
- worksheets, displaying text
- text boxes, displaying text in worksheets
- text [Office development in Visual Studio], text boxes
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 25294e9cb8f57036603ec4817fcbd59976a358a3
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49840282"
---
# <a name="walkthrough-display-text-in-a-text-box-in-a-worksheet-using-a-button"></a>Návod: Zobrazení textu v textovém poli na listu s použitím tlačítka
  Tento návod ukazuje základy používání tlačítka a textová pole v aplikaci Microsoft Office Excel listů a jak vytvářet projekty aplikace Excel pomocí nástroje pro vývoj pro Office v sadě Visual Studio. Výsledek jako úplnou vzorovou najdete v ukázce ovládací prvky aplikace Excel v [Office Ukázky a návody vývoje](../vsto/office-development-samples-and-walkthroughs.md).  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 V tomto návodu se dozvíte, jak:  
  
-   Přidání ovládacích prvků na list.  
  
-   Vyplnění textové pole, když dojde ke kliknutí na tlačítko.  
  
-   Otestování vašeho projektu.  
  
> [!NOTE]  
>  Váš počítač může v následujících pokynech zobrazovat odlišné názvy nebo umístění některých prvků uživatelského rozhraní sady Visual Studio. Tyto prvky jsou určeny edicí sady Visual Studio a použitým nastavením. Další informace najdete v tématu [přizpůsobení integrovaného vývojového prostředí sady Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="prerequisites"></a>Požadavky  
 K dokončení tohoto návodu budete potřebovat následující komponenty:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] nebo [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].  
  
## <a name="create-the-project"></a>Vytvoření projektu  
 V tomto kroku vytvoříte projekt sešitu aplikace Excel pomocí sady Visual Studio.  
  
### <a name="to-create-a-new-project"></a>Chcete-li vytvořit nový projekt  
  
1.  Vytvořte projekt sešitu aplikace Excel s názvem **Moje aplikace Excel tlačítko**. Ujistěte se, že **vytvoříte nový textový dokument** zaškrtnuto. Další informace najdete v tématu [postupy: vytvoření Office projekty v sadě Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     Visual Studio otevře nový sešit aplikace Excel v návrháři a přidá **Moje aplikace Excel tlačítko** projektu **Průzkumníka řešení**.  
  
## <a name="add-controls-to-the-worksheet"></a>Přidání ovládacích prvků na list  
 V tomto návodu budete potřebovat tlačítko a textové pole na prvním listu.  
  
### <a name="to-add-a-button-and-a-text-box"></a>Chcete-li přidat tlačítko a textové pole  
  
1. Ověřte, že **Moje aplikace Excel Button.xlsx** sešitu je otevřen v návrháři aplikace Visual Studio s `Sheet1` zobrazí.  
  
2. Z **běžné ovládací prvky** kartu na panelu nástrojů přetáhněte <xref:Microsoft.Office.Tools.Excel.Controls.TextBox> k `Sheet1`.  
  
3. Z **zobrazení** nabídce vyberte možnost **okno vlastností**.  
  
4. Ujistěte se, že **TextBox1** se nezobrazuje **vlastnosti** okno rozevíracího seznamu a změnit **název** vlastnosti textového pole na **ZobrazenýText**.  
  
5. Přetáhněte **tlačítko** na ovládací prvek `Sheet1` a změnit následující vlastnosti:  
  
   |Vlastnost|Hodnota|  
   |--------------|-----------|  
   |**Jméno**|**insertText**|  
   |**Text**|**Vložit Text**|  
  
   Teď můžete psát kód spustit, když dojde ke kliknutí na tlačítko.  
  
## <a name="populate-the-text-box-when-the-button-is-clicked"></a>Rozbalte textové pole, když dojde ke kliknutí na tlačítko  
 Pokaždé, když uživatel klikne na tlačítko **Hello World!** se připojí do textového pole.  
  
### <a name="to-write-to-the-text-box-when-the-button-is-clicked"></a>Po kliknutí na tlačítko zapsat do textového pole  
  
1.  V **Průzkumníka řešení**, klikněte pravým tlačítkem na **List1**a potom klikněte na tlačítko **zobrazit kód** v místní nabídce.  
  
2.  Přidejte následující kód, který <xref:System.Windows.Forms.Control.Click> obslužná rutina události tlačítka:  
  
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#11](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#11)]
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#11](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#11)]  
  
3.  V C#, je nutné přidat obslužnou rutinu události pro <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> události, jak je znázorněno níže. Informace o vytváření obslužných rutin událostí, naleznete v tématu [postupy: vytváření obslužných rutin událostí v projektech pro systém Office](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#12](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#12)]  
  
## <a name="test-the-application"></a>Testování aplikace  
 Teď můžete otestovat sešitu, abyste měli jistotu, že zpráva **Hello World!** v textovém poli se zobrazí, když kliknete na tlačítko.  
  
### <a name="to-test-your-workbook"></a>K otestování vašeho sešitu  
  
1.  Stisknutím klávesy **F5** ke spuštění projektu.  
  
2.  Klikněte na tlačítko.  
  
3.  Ujistěte se, že **Hello World!** Zobrazí se v textovém poli.  
  
## <a name="next-steps"></a>Další kroky  
 Tento návod ukazuje základy používání tlačítka a textová pole na listech aplikace Excel. Tady jsou některé úlohy, které by mohl pocházet Další:  
  
-   Nasazení projektu. Další informace najdete v tématu [nasazení řešení Office](../vsto/deploying-an-office-solution.md).  
  
-   Chcete-li změnit formátování pomocí zaškrtávacích políček. Další informace najdete v tématu [návod: Změna formátování listů s použitím ovládacích prvků CheckBox](../vsto/walkthrough-changing-worksheet-formatting-using-checkbox-controls.md).  
  
## <a name="see-also"></a>Viz také:  
 [Postupy: Přidání ovládacích prvků Windows Forms do dokumentů Office](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)   
 [Návody pro aplikaci Excel](../vsto/walkthroughs-using-excel.md)   
 [Omezení ovládacích prvků Windows Forms v dokumentech Office](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)  
  
  