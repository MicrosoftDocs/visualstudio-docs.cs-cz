---
title: Synchronizace vlastního podokna úloh s tlačítkem na pásu karet
description: Přečtěte si, jak můžete vytvořit vlastní podokno úloh, které uživatelé mohou skrýt nebo zobrazit kliknutím na přepínací tlačítko na pásu karet.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
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
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 9ac8c4ef96a421ece6c0591d4340d570d71c08e3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99846280"
---
# <a name="walkthrough-synchronize-a-custom-task-pane-with-a-ribbon-button"></a>Návod: Synchronizace vlastního podokna úloh s tlačítkem na pásu karet
  Tento návod ukazuje, jak vytvořit vlastní podokno úloh, které mohou uživatelé skrýt nebo zobrazit kliknutím na přepínací tlačítko na pásu karet. Vždy byste měli vytvořit prvek uživatelského rozhraní (UI), například tlačítko, které mohou uživatelé kliknout k zobrazení nebo skrytí vlastního podokna úloh, protože systém Microsoft Office aplikace neposkytují uživatelům výchozí způsob, jak zobrazit nebo skrýt vlastní podokna úloh.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

 I když tento návod používá specifickou aplikaci Excel, koncepce znázorněné v tomto návodu se vztahují na všechny aplikace, které jsou uvedeny výše.

 Tento návod znázorňuje následující úlohy:

- Návrh uživatelského rozhraní vlastního podokna úloh.

- Přidání přepínacího tlačítka na pás karet.

- Probíhá synchronizace přepínacího tlačítka s vlastním podoknem úloh.

> [!NOTE]
> Váš počítač může v následujících pokynech zobrazovat odlišné názvy nebo umístění některých prvků uživatelského rozhraní sady Visual Studio. Tyto prvky jsou určeny edicí sady Visual Studio a použitým nastavením. Další informace najdete v tématu [Přizpůsobení integrovaného vývojového prostředí (IDE) sady Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Požadavky
 K dokončení tohoto návodu budete potřebovat následující komponenty:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- Microsoft Excel nebo Microsoft [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] .

## <a name="create-the-add-in-project"></a>Vytvoření projektu doplňku
 V tomto kroku vytvoříte projekt doplňku VSTO pro Excel.

### <a name="to-create-a-new-project"></a>Vytvoření nového projektu

1. Pomocí šablony projektu doplňku aplikace Excel vytvořte projekt doplňku aplikace Excel s názvem **SynchronizeTaskPaneAndRibbon**. Další informace najdete v tématu [Postupy: vytváření projektů pro systém Office v sadě Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] otevře soubor kódu **ThisAddIn.cs** nebo **ThisAddIn. vb** a přidá projekt **SynchronizeTaskPaneAndRibbon** do **Průzkumník řešení**.

## <a name="add-a-toggle-button-to-the-ribbon"></a>Přidání přepínacího tlačítka na pás karet
 Jedním z pokynů pro návrh aplikací pro Office je, že uživatelé by měli mít vždycky kontrolu nad uživatelským rozhraním aplikace Office. Chcete-li uživatelům povolit řízení vlastního podokna úloh, můžete přidat přepínací tlačítko pásu karet, které zobrazí a skryje podokno úloh. Chcete-li vytvořit přepínací tlačítko, přidejte položku **pás karet (vizuální Návrhář)** do projektu. Návrhář pomáhá přidat a umístit ovládací prvky, nastavit vlastnosti ovládacího prvku a zpracovat události ovládacího prvku. Další informace najdete v tématu [Návrhář pásu karet](../vsto/ribbon-designer.md).

### <a name="to-add-a-toggle-button-to-the-ribbon"></a>Přidání přepínacího tlačítka na pás karet

1. V nabídce **projekt** klikněte na příkaz **Přidat novou položku**.

2. V dialogovém okně **Přidat novou položku** vyberte možnost **pás karet (vizuální Návrhář)**.

3. Změňte název nového pásu karet na **ManageTaskPaneRibbon** a klikněte na **Přidat**.

     Otevře se soubor **ManageTaskPaneRibbon.cs** nebo **ManageTaskPaneRibbon. vb** v Návrháři pásu karet a zobrazí výchozí kartu a skupinu.

4. V Návrháři pásu karet klikněte na **Group1**.

5. V okně **vlastnosti** nastavte vlastnost **popisek** na **Správce podokna úloh**.

6. Na kartě **ovládací prvky pásu karet Office** přetáhněte  **ToggleButton** do skupiny **Správce podokna úloh** .

7. Klikněte na **ToggleButton1**.

8. V okně **vlastnosti** nastavte vlastnost **popisek** na **Zobrazit podokno úloh**.

## <a name="design-the-user-interface-of-the-custom-task-pane"></a>Návrh uživatelského rozhraní vlastního podokna úloh
 Neexistuje žádný vizuální Návrhář pro vlastní podokna úloh, ale můžete navrhnout uživatelský ovládací prvek s požadovaným rozložením. Později v tomto návodu přidáte uživatelský ovládací prvek do vlastního podokna úloh.

### <a name="to-design-the-user-interface-of-the-custom-task-pane"></a>Návrh uživatelského rozhraní vlastního podokna úloh

1. V nabídce **projekt** klikněte na příkaz **Přidat uživatelský ovládací prvek**.

2. V dialogovém okně **Přidat novou položku** změňte název uživatelského ovládacího prvku na **TaskPaneControl** a klikněte na tlačítko **Přidat**.

     Uživatelský ovládací prvek se otevře v návrháři.

3. Na kartě **běžné ovládací prvky** **panelu nástrojů** přetáhněte ovládací prvek **TextBox** do uživatelského ovládacího prvku.

## <a name="create-the-custom-task-pane"></a>Vytvoření vlastního podokna úloh
 Pokud chcete vytvořit vlastní podokno úloh při spuštění doplňku VSTO, přidejte uživatelský ovládací prvek do podokna úloh v <xref:Microsoft.Office.Tools.AddIn.Startup> obslužné rutině události doplňku VSTO. Ve výchozím nastavení se vlastní podokno úloh nezobrazí. Později v tomto návodu přidáte kód, který zobrazí nebo skryje podokno úloh, když uživatel klikne na přepínací tlačítko, které jste přidali na pás karet.

### <a name="to-create-the-custom-task-pane"></a>Vytvoření vlastního podokna úloh

1. V **Průzkumník řešení** rozbalte položku **Excel**.

2. Klikněte pravým tlačítkem na **ThisAddIn.cs** nebo **ThisAddIn. vb** a klikněte na **Zobrazit kód**.

3. Do třídy `ThisAddIn` přidejte následující kód. Tento kód deklaruje instanci `TaskPaneControl` jako člena `ThisAddIn` .

     [!code-csharp[Trin_TaskPaneRibbonSynchronize#1](../vsto/codesnippet/CSharp/Trin_TaskPaneRibbonSynchronize/ThisAddIn.cs#1)]
     [!code-vb[Trin_TaskPaneRibbonSynchronize#1](../vsto/codesnippet/VisualBasic/Trin_TaskPaneRibbonSynchronize/ThisAddIn.vb#1)]

4. Proměnnou `ThisAddIn_Startup` obslužné rutiny události nahraďte následujícím kódem. Tento kód přidá `TaskPaneControl` objekt do `CustomTaskPanes` pole, ale nezobrazuje vlastní podokno úloh (ve výchozím nastavení <xref:Microsoft.Office.Tools.CustomTaskPane.Visible%2A> <xref:Microsoft.Office.Tools.CustomTaskPane> je vlastnost třídy **nepravdivá**). Kód jazyka Visual C# také připojí obslužnou rutinu události k <xref:Microsoft.Office.Tools.CustomTaskPane.VisibleChanged> události.

     [!code-csharp[Trin_TaskPaneRibbonSynchronize#2](../vsto/codesnippet/CSharp/Trin_TaskPaneRibbonSynchronize/ThisAddIn.cs#2)]
     [!code-vb[Trin_TaskPaneRibbonSynchronize#2](../vsto/codesnippet/VisualBasic/Trin_TaskPaneRibbonSynchronize/ThisAddIn.vb#2)]

5. Do třídy přidejte následující metodu `ThisAddIn` . Tato metoda zpracovává <xref:Microsoft.Office.Tools.CustomTaskPane.VisibleChanged> událost. Když uživatel zavře podokno úloh kliknutím na tlačítko **Zavřít** (X), tato metoda aktualizuje stav přepínacího tlačítka na pásu karet.

     [!code-csharp[Trin_TaskPaneRibbonSynchronize#3](../vsto/codesnippet/CSharp/Trin_TaskPaneRibbonSynchronize/ThisAddIn.cs#3)]
     [!code-vb[Trin_TaskPaneRibbonSynchronize#3](../vsto/codesnippet/VisualBasic/Trin_TaskPaneRibbonSynchronize/ThisAddIn.vb#3)]

6. Přidejte do třídy následující vlastnost `ThisAddIn` . Tato vlastnost zveřejňuje privátní `myCustomTaskPane1` objekt pro jiné třídy. Později v tomto návodu přidáte kód do `MyRibbon` třídy, která tuto vlastnost používá.

     [!code-csharp[Trin_TaskPaneRibbonSynchronize#4](../vsto/codesnippet/CSharp/Trin_TaskPaneRibbonSynchronize/ThisAddIn.cs#4)]
     [!code-vb[Trin_TaskPaneRibbonSynchronize#4](../vsto/codesnippet/VisualBasic/Trin_TaskPaneRibbonSynchronize/ThisAddIn.vb#4)]

## <a name="hide-and-show-the-custom-task-pane-by-using-the-toggle-button"></a>Skrytí a zobrazení vlastního podokna úloh pomocí přepínacího tlačítka
 Posledním krokem je přidání kódu, který zobrazí nebo skryje vlastní podokno úloh, když uživatel klikne na přepínací tlačítko na pásu karet.

### <a name="to-display-and-hide-the-custom-task-pane-by-using-the-toggle-button"></a>Zobrazení a skrytí vlastního podokna úloh pomocí přepínacího tlačítka

1. V Návrháři pásu karet poklikejte na přepínací tlačítko **podokna zobrazit podokno úloh** .

     Visual Studio automaticky vygeneruje obslužnou rutinu události s názvem `toggleButton1_Click` , která zpracovává <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton.Click> událost přepínacího tlačítka. Visual Studio také otevře soubor *MyRibbon.cs* nebo *MyRibbon. vb* v editoru kódu.

2. Proměnnou `toggleButton1_Click` obslužné rutiny události nahraďte následujícím kódem. Když uživatel klikne na přepínací tlačítko, tento kód zobrazí nebo skryje vlastní podokno úloh v závislosti na tom, zda je přepínací tlačítko stisknuté nebo nestisknuté.

     [!code-vb[Trin_TaskPaneRibbonSynchronize#5](../vsto/codesnippet/VisualBasic/Trin_TaskPaneRibbonSynchronize/ManageTaskPaneRibbon.vb#5)]
     [!code-csharp[Trin_TaskPaneRibbonSynchronize#5](../vsto/codesnippet/CSharp/Trin_TaskPaneRibbonSynchronize/ManageTaskPaneRibbon.cs#5)]

## <a name="test-the-add-in"></a>Test doplňku
 Při spuštění projektu se aplikace Excel otevře bez zobrazení vlastního podokna úloh. Kliknutím na tlačítko přepínacího tlačítka na pásu karet otestujete kód.

### <a name="to-test-your-vsto-add-in"></a>Testování doplňku VSTO

1. Stisknutím klávesy **F5** spusťte projekt.

     Potvrďte, že se otevře Excel a na pásu karet se zobrazí karta **Doplňky** .

2. Na pásu karet klikněte na kartu **Doplňky** .

3. Ve skupině **Správce podokna úloh** klikněte na tlačítko Zobrazit přepínací tlačítko **podokna úloh** .

     Ověřte, že se podokno úlohy při kliknutí na přepínací tlačítko střídavě zobrazuje a skryje.

4. Když je podokno úloh viditelné, klikněte na tlačítko **Zavřít** (X) v horní části podokna úloh.

     Ověřte, že se přepínací tlačítko nestisklo.

## <a name="next-steps"></a>Další kroky
 Další informace o tom, jak vytvořit vlastní podokna úloh, najdete v těchto tématech:

- Vytvoření vlastního podokna úloh v doplňku VSTO pro jinou aplikaci. Další informace o aplikacích, které podporují vlastní podokna úloh, najdete v tématu [vlastní podokna úloh](../vsto/custom-task-panes.md).

- Automatizujte aplikaci z vlastního podokna úloh. Další informace najdete v tématu [Návod: automatizace aplikace z vlastního podokna úloh](../vsto/walkthrough-automating-an-application-from-a-custom-task-pane.md).

- Slouží k vytvoření vlastního podokna úloh pro každou e-mailovou zprávu, která je otevřena v aplikaci Outlook. Další informace najdete v tématu [Návod: zobrazení vlastních podoken úloh s e-mailovými zprávami v aplikaci Outlook](../vsto/walkthrough-displaying-custom-task-panes-with-e-mail-messages-in-outlook.md).

## <a name="see-also"></a>Viz také
- [Vlastní podokna úloh](../vsto/custom-task-panes.md)
- [Postupy: Přidání vlastního podokna úloh do aplikace](../vsto/how-to-add-a-custom-task-pane-to-an-application.md)
- [Návod: automatizace aplikace z vlastního podokna úloh](../vsto/walkthrough-automating-an-application-from-a-custom-task-pane.md)
- [Návod: zobrazení vlastních podoken úloh s e-mailovými zprávami v aplikaci Outlook](../vsto/walkthrough-displaying-custom-task-panes-with-e-mail-messages-in-outlook.md)
- [Přehled pásu karet](../vsto/ribbon-overview.md)
