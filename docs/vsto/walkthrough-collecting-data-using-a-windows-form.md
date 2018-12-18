---
title: 'Návod: Shromažďování dat pomocí formuláře Windows'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data [Office development in Visual Studio], Windows Forms
- Windows Forms [Office development in Visual Studio], collecting data
- forms [Office development in Visual Studio], walkthroughs
- worksheets [Office development in Visual Studio], collecting data
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 1d48f2a104505e6b6ea9942847d8cd4dd2f3e669
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49900472"
---
# <a name="walkthrough-collect-data-by-using-a-windows-form"></a>Návod: Shromažďování dat pomocí formuláře Windows
  Tento návod ukazuje, jak otevřít formulář Windows z přizpůsobení úrovni dokumentu pro aplikaci Microsoft Office Excel, shromažďování informací od uživatele a zápisu informací do buňky listu.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 I když tento návod používá konkrétně projektu úrovni dokumentu pro Excel, se vztahují na jiné projekty Office koncepty jsme vám ukázali podle návodu.  
  
## <a name="prerequisites"></a>Požadavky  
 K dokončení tohoto návodu budete potřebovat následující komponenty:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] nebo [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].  
  
> [!NOTE]  
>  Váš počítač může v následujících pokynech zobrazovat odlišné názvy nebo umístění některých prvků uživatelského rozhraní sady Visual Studio. Tyto prvky jsou určeny edicí sady Visual Studio a použitým nastavením. Další informace najdete v tématu [přizpůsobení integrovaného vývojového prostředí sady Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="create-a-new-project"></a>Vytvoření nového projektu  
 Prvním krokem je vytvoření projektu sešitu aplikace Excel.  
  
### <a name="to-create-a-new-project"></a>Chcete-li vytvořit nový projekt  
  
1.  Vytvořte projekt sešitu aplikace Excel s názvem **WinFormInput**a vyberte **vytvoříte nový textový dokument** v průvodci. Další informace najdete v tématu [postupy: vytváření projektů pro systém Office v sadě Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     Visual Studio otevře nový sešit aplikace Excel v návrháři a přidá **WinFormInput** projektu **Průzkumníka řešení**.  
  
## <a name="add-a-namedrange-control-to-the-worksheet"></a>Přidání ovládacího prvku NamedRange do listu  
  
### <a name="to-add-a-named-range-to-sheet1"></a>Chcete-li přidat pojmenované oblasti List1  
  
1.  Vyberte buňku **A1** na `Sheet1`.  
  
2.  V **název** zadejte **formInput**.  
  
     **Název** pole je umístěno vlevo od řádku vzorců nad sloupci **A** listu.  
  
3.  Stisknutím klávesy **zadejte**.  
  
     A <xref:Microsoft.Office.Tools.Excel.NamedRange> ovládací prvek je přidán do buňky **A1**. Není by na listu, ale **formInput** se zobrazí v **název** pole (přímo nad list na levé straně) a **vlastnosti** okno při Buňka **A1** zaškrtnuto.  
  
## <a name="add-a-windows-form-to-the-project"></a>Přidat formulář Windows do projektu  
 Vytvoření formuláře Windows k požádat uživatele o informace.  
  
### <a name="to-add-a-windows-form"></a>Chcete-li přidat formulář Windows  
  
1. Vyberte projekt **WinFormInput** v **Průzkumníka řešení**.  
  
2. Na **projektu** nabídky, klikněte na tlačítko **přidat formulář Windows**.  
  
3. Název formuláře **GetInputString.vb** nebo **GetInputString.cs**a potom klikněte na tlačítko **přidat**.  
  
    Otevře se v Návrháři nový formulář.  
  
4. Přidat <xref:System.Windows.Forms.TextBox> a <xref:System.Windows.Forms.Button> do formuláře.  
  
5. Klikněte na tlačítko, vyhledejte vlastnost **Text** v **vlastnosti** okna a změnit text, který má **OK**.  
  
   V dalším kroku přidejte kód pro `ThisWorkbook.vb` nebo `ThisWorkbook.cs` ke shromažďování informací o uživateli.  
  
## <a name="display-the-windows-form-and-collecting-information"></a>Zobrazí se formulář Windows a shromažďování údajů o informace  
 Vytvoření instance `GetInputString` formuláře Windows a zobrazit ho a pak zapsat informace uživatele do buňky v listu.  
  
#### <a name="to-display-the-form-and-collect-information"></a>Zobrazení formuláře a shromažďovat informace  
  
1. Klikněte pravým tlačítkem na **ThisWorkbook.vb** nebo **ThisWorkbook.cs** v **Průzkumníka řešení**a potom klikněte na tlačítko **zobrazit kód**.  
  
2. V <xref:Microsoft.Office.Tools.Excel.Workbook.Open> obslužná rutina události `ThisWorkbook`, přidejte následující kód k deklaraci proměnné pro formulář `GetInputString` a poté zobrazí formulář.  
  
   > [!NOTE]  
   >  V jazyce C#, musíte přidat obslužnou rutinu události, jak je znázorněno <xref:Microsoft.Office.Tools.Excel.Workbook.Startup> následující událost. Informace o vytváření obslužných rutin událostí, naleznete v tématu [postupy: vytváření obslužných rutin událostí v projektech pro systém Office](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
    [!code-csharp[Trin_VstcoreProgrammingCollectingData#1](../vsto/codesnippet/CSharp/WinFormInputCS/ThisWorkbook.cs#1)]
    [!code-vb[Trin_VstcoreProgrammingCollectingData#1](../vsto/codesnippet/VisualBasic/WinFormInput/ThisWorkbook.vb#1)]  
  
3. Vytvořit metodu nazvanou `WriteStringToCell` , který zapíše text do pojmenované oblasti. Tato metoda je volána z formuláře a uživatelský vstup je předán <xref:Microsoft.Office.Tools.Excel.NamedRange> ovládacího prvku, `formInput`, v buňce **A1**.  
  
    [!code-csharp[Trin_VstcoreProgrammingCollectingData#2](../vsto/codesnippet/CSharp/WinFormInputCS/ThisWorkbook.cs#2)]
    [!code-vb[Trin_VstcoreProgrammingCollectingData#2](../vsto/codesnippet/VisualBasic/WinFormInput/ThisWorkbook.vb#2)]  
  
   Dál přidejte kód do formuláře klikněte na tlačítko na zpracování událostí.  
  
## <a name="send-information-to-the-worksheet"></a>Odesílat informace do listu  
  
### <a name="to-send-information-to-the-worksheet"></a>Odesílat informace do listu  
  
1.  Klikněte pravým tlačítkem na **GetInputString** v **Průzkumníka řešení**a potom klikněte na tlačítko **Návrhář zobrazení**.  
  
2.  Dvakrát klikněte na tlačítko k otevření souboru kódu pomocí tlačítka <xref:System.Windows.Forms.Control.Click> přidali obslužnou rutinu události.  
  
3.  Přidejte kód do obslužné rutiny události využívat vstupu z textového pole, odeslat ho do funkce `WriteStringToCell`a pak zavřete formulář.  
  
     [!code-csharp[Trin_VstcoreProgrammingCollectingData#3](../vsto/codesnippet/CSharp/WinFormInputCS/GetInputString.cs#3)]
     [!code-vb[Trin_VstcoreProgrammingCollectingData#3](../vsto/codesnippet/VisualBasic/WinFormInput/GetInputString.vb#3)]  
  
## <a name="test"></a>Test  
 Nyní můžete spustit projekt. Zobrazí se formulář Windows a váš vstup, zobrazí se v listu.  
  
### <a name="to-test-your-workbook"></a>K otestování vašeho sešitu  
  
1.  Stisknutím klávesy **F5** ke spuštění projektu.  
  
2.  Potvrďte, že se zobrazí formulář Windows.  
  
3.  Typ **Hello World** textového pole a pak klikněte na **OK**.  
  
4.  Ujistěte se, že **Hello World** se zobrazí v buňce **A1** listu.  
  
## <a name="next-steps"></a>Další kroky  
 Tento návod ukazuje základní informace o zobrazení formuláře Windows a předání dat do listu. Další úlohy, které můžete provádět, patří:  
  
-   Pomocí ovládacích prvků Windows Forms na Excelový sešit nebo dokument aplikace Word. Další informace najdete v tématu [ovládací prvky Windows Forms v přehledu dokumenty Office](../vsto/windows-forms-controls-on-office-documents-overview.md).  
  
-   Úprava uživatelského rozhraní aplikace Microsoft Office z přizpůsobení úrovni dokumentu nebo doplňku VSTO. Další informace najdete v tématu [přizpůsobení uživatelského rozhraní Office](../vsto/office-ui-customization.md).  
  
## <a name="see-also"></a>Viz také:  
 [Vývoj řešení pro systém Office](../vsto/developing-office-solutions.md)   
 [Psaní kódu v řešeních pro systém Office](../vsto/writing-code-in-office-solutions.md)   
 [Programování doplňků VSTO](../vsto/programming-vsto-add-ins.md)   
 [Programování přizpůsobení na úrovni dokumentu](../vsto/programming-document-level-customizations.md)   
 [Návody pro aplikaci Word](../vsto/walkthroughs-using-word.md)   
 [Návody pro aplikaci Excel](../vsto/walkthroughs-using-excel.md)  
  
  