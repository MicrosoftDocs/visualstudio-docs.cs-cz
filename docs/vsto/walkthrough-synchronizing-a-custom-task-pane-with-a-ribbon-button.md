---
title: 'Návod: Synchronizace vlastního podokna úloh s tlačítkem pásu karet'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- custom task panes [Office development in Visual Studio], showing and hiding
- showing custom task panes
- Ribbon [Office development in Visual Studio], custom task panes
- toggle buttons [Office development in Visual Studio]
- custom task panes [Office development in Visual Studio], synchronizing with Ribbon button
- user interfaces [Office development in Visual Studio], custom task panes
- synchronization [Office development in Visual Studio], custom task panes
- task panes [Office development in Visual Studio], showing and hiding
- custom task panes [Office development in Visual Studio], creating
- hiding custom task panes
- task panes [Office development in Visual Studio], creating
- task panes [Office development in Visual Studio], synchronizing with Ribbon button
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 7b6c36e93d9dd8dd4ef81d0d124ae33e842a16d7
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "35676061"
---
# <a name="walkthrough-synchronize-a-custom-task-pane-with-a-ribbon-button"></a>Návod: Synchronizace vlastního podokna úloh s tlačítkem pásu karet
  Tento návod ukazuje, jak vytvořit vlastního podokna úloh, které uživatelé můžou skrýt nebo zobrazit kliknutím na přepínací tlačítko na pásu karet. Vždy byste měli vytvořit prvek uživatelského rozhraní (UI), jako je například tlačítko, který mohou uživatelé kliknout a zobrazit nebo skrýt vlastního podokna úloh, protože aplikace Microsoft Office se neposkytuje výchozí způsob, jak uživatelé zobrazení nebo skrytí vlastních podoken úloh.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
 I když tento návod používá konkrétně aplikace Excel, koncepty jsme vám ukázali podle návodu platí pro všechny aplikace, které jsou uvedené výše.  
  
 Tento návod znázorňuje následující úlohy:  
  
-   Návrh uživatelského rozhraní vlastního podokna úloh.  
  
-   Přidání přepínacího tlačítka na pás karet.  
  
-   Synchronizace přepínacího tlačítka s vlastní podokno úloh.  
  
> [!NOTE]  
>  Váš počítač může v následujících pokynech zobrazovat odlišné názvy nebo umístění některých prvků uživatelského rozhraní sady Visual Studio. Tyto prvky jsou určeny edicí sady Visual Studio a použitým nastavením. Další informace najdete v tématu [přizpůsobení integrovaného vývojového prostředí sady Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="prerequisites"></a>Požadavky  
 K dokončení tohoto návodu budete potřebovat následující komponenty:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Aplikace Microsoft Excel nebo Microsoft [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)].  
  
## <a name="create-the-add-in-project"></a>Vytvořte projekt doplňku  
 V tomto kroku vytvoříte projekt doplňku VSTO pro Excel.  
  
### <a name="to-create-a-new-project"></a>Chcete-li vytvořit nový projekt  
  
1.  Vytvoření projektu doplňku aplikace Excel s názvem **SynchronizeTaskPaneAndRibbon**, pomocí šablony projektu doplňku aplikace Excel. Další informace najdete v tématu [postupy: vytvoření Office projekty v sadě Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Otevře **ThisAddIn.cs** nebo **ThisAddIn.vb** soubor kódu a přidá **SynchronizeTaskPaneAndRibbon** projektu **Průzkumníka řešení**.  
  
## <a name="add-a-toggle-button-to-the-ribbon"></a>Přidání přepínacího tlačítka na pás karet  
 Jedním z pokynů pro návrh aplikace Office je, že uživatelé by měli vždy mít ovládací prvek uživatelského rozhraní aplikace Office. Umožňuje uživatelům řídit vlastního podokna úloh, můžete přidat přepínací tlačítko pásu karet, který zobrazí a skryje podokno úloh. Chcete-li vytvořit přepínací tlačítko, přidejte **pás karet (vizuální návrhář)** položky do projektu. Návrhář pomáhá přidat a umístit ovládací prvky, nastavit vlastnosti ovládacího prvku a zpracovat události ovládacího prvku. Další informace najdete v tématu [Návrháře pásu karet](../vsto/ribbon-designer.md).  
  
### <a name="to-add-a-toggle-button-to-the-ribbon"></a>Přidání přepínacího tlačítka na pás karet  
  
1.  Na **projektu** nabídky, klikněte na tlačítko **přidat novou položku**.  
  
2.  V **přidat novou položku** dialogu **pás karet (vizuální návrhář)**.  
  
3.  Změňte název nového pásu karet na **ManageTaskPaneRibbon**a klikněte na tlačítko **přidat**.  
  
     **ManageTaskPaneRibbon.cs** nebo **ManageTaskPaneRibbon.vb** soubor se otevře v Návrháři pásu karet a zobrazí výchozí kartu a skupinu.  
  
4.  V Návrháři pásu karet klikněte na tlačítko **group1**.  
  
5.  V **vlastnosti** okno, nastaveno **popisek** vlastnost **správce podokna úloh**.  
  
6.  Z **ovládací prvky Ribbon Office** karty **nástrojů**, přetáhněte **ToggleButton** na **správce podokna úloh** skupiny.  
  
7.  Klikněte na tlačítko **toggleButton1**.  
  
8.  V **vlastnosti** okno, nastaveno **popisek** vlastnost **zobrazit podokno úloh**.  
  
## <a name="design-the-user-interface-of-the-custom-task-pane"></a>Návrh uživatelského rozhraní vlastního podokna úloh  
 Neexistuje žádné vizuálního návrháře pro vlastní podokna úloh, ale můžete navrhnout uživatelský ovládací prvek rozložení, které chcete. Dále v tomto názorném postupu se přidat uživatelský ovládací prvek do vlastního podokna úloh.  
  
### <a name="to-design-the-user-interface-of-the-custom-task-pane"></a>K návrhu uživatelského rozhraní vlastního podokna úloh  
  
1.  Na **projektu** nabídky, klikněte na tlačítko **přidat uživatelský ovládací prvek**.  
  
2.  V **přidat novou položku** dialogové okno pole, změňte název uživatelský ovládací prvek **TaskPaneControl**a klikněte na tlačítko **přidat**.  
  
     Uživatelský ovládací prvek se otevře v návrháři.  
  
3.  Z **běžné ovládací prvky** karty **nástrojů**, přetáhněte **textového pole** ovládacího prvku do uživatelského ovládacího prvku.  
  
## <a name="create-the-custom-task-pane"></a>Vytvoření vlastního podokna úloh  
 Pokud chcete vytvořit vlastní podokno úloh při spuštění doplňku VSTO, přidat uživatelský ovládací prvek do podokna úloh v <xref:Microsoft.Office.Tools.AddIn.Startup> obslužná rutina události doplňku VSTO. Ve výchozím nastavení se nezobrazí podokno úloh. Dále v tomto názorném postupu přidáte kód, který se bude zobrazení nebo skrytí podokna úloh, když uživatel klikne na přepínací tlačítko, které jste přidali na pás karet.  
  
### <a name="to-create-the-custom-task-pane"></a>Vytvoření vlastního podokna úloh  
  
1.  V **Průzkumníka řešení**, rozbalte **Excel**.  
  
2.  Klikněte pravým tlačítkem na **ThisAddIn.cs** nebo **ThisAddIn.vb** a klikněte na tlačítko **zobrazit kód**.  
  
3.  Přidejte následující kód, který `ThisAddIn` třídy. Tento kód deklaruje instanci `TaskPaneControl` jako člen `ThisAddIn`.  
  
     [!code-csharp[Trin_TaskPaneRibbonSynchronize#1](../vsto/codesnippet/CSharp/Trin_TaskPaneRibbonSynchronize/ThisAddIn.cs#1)]
     [!code-vb[Trin_TaskPaneRibbonSynchronize#1](../vsto/codesnippet/VisualBasic/Trin_TaskPaneRibbonSynchronize/ThisAddIn.vb#1)]  
  
4.  Nahradit `ThisAddIn_Startup` obslužné rutiny události s následujícím kódem. Tento kód přidá `TaskPaneControl` objektu `CustomTaskPanes` pole, ale nejsou zobrazeny v podokně úloh (ve výchozím nastavení, <xref:Microsoft.Office.Tools.CustomTaskPane.Visible%2A> vlastnost <xref:Microsoft.Office.Tools.CustomTaskPane> třída je **false**). Kód jazyka Visual C# také připisuje obslužnou rutinu události pro <xref:Microsoft.Office.Tools.CustomTaskPane.VisibleChanged> událostí.  
  
     [!code-csharp[Trin_TaskPaneRibbonSynchronize#2](../vsto/codesnippet/CSharp/Trin_TaskPaneRibbonSynchronize/ThisAddIn.cs#2)]
     [!code-vb[Trin_TaskPaneRibbonSynchronize#2](../vsto/codesnippet/VisualBasic/Trin_TaskPaneRibbonSynchronize/ThisAddIn.vb#2)]  
  
5.  Přidejte následující metodu do `ThisAddIn` třídy. Tato metoda obsluhuje <xref:Microsoft.Office.Tools.CustomTaskPane.VisibleChanged> událostí. Když uživatel zavírá podokna úloh po kliknutí **Zavřít** tlačítko (X), tato metoda aktualizace, stav přepínacího tlačítko na pásu karet.  
  
     [!code-csharp[Trin_TaskPaneRibbonSynchronize#3](../vsto/codesnippet/CSharp/Trin_TaskPaneRibbonSynchronize/ThisAddIn.cs#3)]
     [!code-vb[Trin_TaskPaneRibbonSynchronize#3](../vsto/codesnippet/VisualBasic/Trin_TaskPaneRibbonSynchronize/ThisAddIn.vb#3)]  
  
6.  Přidejte následující vlastnost, která má `ThisAddIn` třídy. Tato vlastnost poskytuje privátní `myCustomTaskPane1` objekt do jiné třídy. Dále v tomto názorném postupu přidáte kód, který `MyRibbon` třídu, která používá tuto vlastnost.  
  
     [!code-csharp[Trin_TaskPaneRibbonSynchronize#4](../vsto/codesnippet/CSharp/Trin_TaskPaneRibbonSynchronize/ThisAddIn.cs#4)]
     [!code-vb[Trin_TaskPaneRibbonSynchronize#4](../vsto/codesnippet/VisualBasic/Trin_TaskPaneRibbonSynchronize/ThisAddIn.vb#4)]  
  
## <a name="hide-and-show-the-custom-task-pane-by-using-the-toggle-button"></a>Skrytí a zobrazení vlastního podokna úloh pomocí přepínacího tlačítka  
 Posledním krokem je přidání kódu, který zobrazí nebo skryje podokno úloh, když uživatel klikne na přepínací tlačítko na pásu karet.  
  
### <a name="to-display-and-hide-the-custom-task-pane-by-using-the-toggle-button"></a>K zobrazení a skrytí vlastního podokna úloh pomocí přepínacího tlačítka  
  
1.  V Návrháři pásu karet klikněte dvakrát na **zobrazit podokno úloh** přepínacího tlačítka.  
  
     Visual Studio vygeneruje obslužnou rutinu události s názvem automaticky `toggleButton1_Click`, která zpracovává <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton.Click> události přepínacího tlačítka. Visual Studio také otevře *MyRibbon.cs* nebo *MyRibbon.vb* souboru v editoru kódu.  
  
2.  Nahradit `toggleButton1_Click` obslužné rutiny události s následujícím kódem. Když uživatel klikne na přepínací tlačítko, tento kód zobrazí nebo skryje podokno úloh, v závislosti na tom, jestli je přepínací tlačítko stisknuté nebo nestisknuté.  
  
     [!code-vb[Trin_TaskPaneRibbonSynchronize#5](../vsto/codesnippet/VisualBasic/Trin_TaskPaneRibbonSynchronize/ManageTaskPaneRibbon.vb#5)]
     [!code-csharp[Trin_TaskPaneRibbonSynchronize#5](../vsto/codesnippet/CSharp/Trin_TaskPaneRibbonSynchronize/ManageTaskPaneRibbon.cs#5)]  
  
## <a name="test-the-add-in"></a>Testování v aplikaci  
 Při spuštění projektu se otevře Excel bez zobrazení vlastního podokna úloh. Klikněte na přepínací tlačítko na pásu karet pro otestování kódu.  
  
### <a name="to-test-your-vsto-add-in"></a>K otestování vašeho doplňku VSTO  
  
1.  Stisknutím klávesy **F5** ke spuštění projektu.  
  
     Potvrďte, že se otevře Excel a **Add-Ins** kartě se zobrazí na pásu karet.  
  
2.  Klikněte na tlačítko **Add-Ins** kartu na pásu karet.  
  
3.  V **správce podokna úloh** klikněte na položku **zobrazit podokno úloh** přepínacího tlačítka.  
  
     Ověřte, že v podokně úloh střídavě zobrazí a skryté klepnete přepínacího tlačítka.  
  
4.  Když v podokně úloh je zobrazen, klikněte na tlačítko **Zavřít** tlačítko (X) v horním rohu podokna úloh.  
  
     Ověřte, že se nebudou stisknutí přepínacího tlačítka.  
  
## <a name="next-steps"></a>Další kroky  
 Další informace o tom, jak vytvořit vlastní podokna úloh naleznete v těchto tématech:  
  
-   Vytvoření vlastního podokna úloh v doplňku VSTO pro jinou aplikaci. Další informace o aplikacích, které podporují vlastní podokna úloh, naleznete v tématu [vlastní podokna úloh](../vsto/custom-task-panes.md).  
  
-   Automatizace aplikace z vlastního podokna úloh. Další informace najdete v tématu [návod: automatizace aplikace z vlastního podokna úloh](../vsto/walkthrough-automating-an-application-from-a-custom-task-pane.md).  
  
-   Vytvoření vlastního podokna úloh pro každou e-mailové zprávy, která je otevřena v Outlooku. Další informace najdete v tématu [návod: zobrazení vlastních podoken úloh s e-mailové zprávy v aplikaci Outlook](../vsto/walkthrough-displaying-custom-task-panes-with-e-mail-messages-in-outlook.md).  
  
## <a name="see-also"></a>Viz také:  
 [Vlastní podokna úloh](../vsto/custom-task-panes.md)   
 [Postupy: Přidání vlastního podokna úloh do aplikace](../vsto/how-to-add-a-custom-task-pane-to-an-application.md)   
 [Návod: Automatizace aplikace z vlastního podokna úloh](../vsto/walkthrough-automating-an-application-from-a-custom-task-pane.md)   
 [Návod: Zobrazení vlastních podoken úloh s e-mailové zprávy v aplikaci Outlook](../vsto/walkthrough-displaying-custom-task-panes-with-e-mail-messages-in-outlook.md)   
 [Přehled pásu karet](../vsto/ribbon-overview.md)  
  
  