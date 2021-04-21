---
title: 'Návod: automatizace aplikace z vlastního podokna úloh'
description: Vytvořte vlastní podokno úloh, které automatizuje aplikaci Microsoft PowerPoint vložením dat do snímku, když uživatel klikne na ovládací prvek MonthCalendar v vlastním podokně úloh.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- task panes [Office development in Visual Studio], PowerPoint
- PowerPoint [Office development in Visual Studio], custom task panes
- automating Office applications
- custom task panes [Office development in Visual Studio], automating applications
- custom task panes [Office development in Visual Studio], PowerPoint
- task panes [Office development in Visual Studio], automating applications
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: f57ad0c858abb5f151e1b425224b5af34d464c0f
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/21/2021
ms.locfileid: "107824663"
---
# <a name="walkthrough-automate-an-application-from-a-custom-task-pane"></a>Návod: automatizace aplikace z vlastního podokna úloh
  Tento návod ukazuje, jak vytvořit vlastní podokno úloh, které automatizuje PowerPoint. Vlastní podokno úloh vloží data do snímku, když uživatel klikne <xref:System.Windows.Forms.MonthCalendar> na ovládací prvek, který se nachází v podokně vlastní úlohy.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

 I když tento návod používá specifickou aplikaci PowerPoint, koncepce znázorněné v tomto návodu se vztahují na všechny aplikace, které jsou uvedeny výše.

 Tento návod znázorňuje následující úlohy:

- Návrh uživatelského rozhraní vlastního podokna úloh.

- Automatizace PowerPointu z vlastního podokna úloh.

- Zobrazení vlastního podokna úloh v aplikaci PowerPoint.

> [!NOTE]
> Váš počítač může v následujících pokynech zobrazovat odlišné názvy nebo umístění některých prvků uživatelského rozhraní sady Visual Studio. Tyto prvky jsou určeny edicí sady Visual Studio a použitým nastavením. Další informace najdete v tématu [Přizpůsobení integrovaného vývojového prostředí (IDE) sady Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Požadavky
 K dokončení tohoto návodu budete potřebovat následující komponenty:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- Microsoft PowerPoint 2010 nebo [!INCLUDE[PowerPoint_15_short](../vsto/includes/powerpoint-15-short-md.md)] .

## <a name="create-the-add-in-project"></a>Vytvoření projektu doplňku
 Prvním krokem je vytvoření projektu doplňku VSTO pro PowerPoint.

### <a name="to-create-a-new-project"></a>Vytvoření nového projektu

1. Pomocí šablony projektu doplňku aplikace PowerPoint vytvořte projekt doplňku VSTO pro PowerPoint s názvem **MyAddIn**. Další informace najdete v tématu [Postupy: vytváření projektů pro systém Office v sadě Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] otevře soubor kódu **ThisAddIn. cs** nebo **ThisAddIn. vb** a přidá projekt **MyAddIn** do **Průzkumník řešení**.

## <a name="design-the-user-interface-of-the-custom-task-pane"></a>Návrh uživatelského rozhraní vlastního podokna úloh
 Neexistuje žádný vizuální Návrhář pro vlastní podokna úloh, ale můžete navrhnout uživatelský ovládací prvek s požadovaným rozložením. Později v tomto návodu přidáte uživatelský ovládací prvek do vlastního podokna úloh.

#### <a name="to-design-the-user-interface-of-the-custom-task-pane"></a>Návrh uživatelského rozhraní vlastního podokna úloh

1. V nabídce **projekt** klikněte na příkaz **Přidat uživatelský ovládací prvek**.

2. V dialogovém okně **Přidat novou položku** změňte název uživatelského ovládacího prvku na **MyUserControl** a klikněte na tlačítko **Přidat**.

     Uživatelský ovládací prvek se otevře v návrháři.

3. Na kartě **běžné ovládací prvky** **panelu nástrojů** přetáhněte ovládací prvek **MonthCalendar** do uživatelského ovládacího prvku.

     Pokud je ovládací prvek **MonthCalendar** větší než návrhová plocha uživatelského ovládacího prvku, změňte velikost uživatelského ovládacího prvku tak, aby odpovídala ovládacímu prvku **MonthCalendar** .

## <a name="automate-powerpoint-from-the-custom-task-pane"></a>Automatizace PowerPointu z vlastního podokna úloh
 Účelem doplňku VSTO je umístit vybrané datum na první snímek aktivní prezentace. Použijte <xref:System.Windows.Forms.MonthCalendar.DateChanged> událost ovládacího prvku k přidání vybraného data vždy, když se změní.

### <a name="to-automate-powerpoint-from-the-custom-task-pane"></a>Automatizace PowerPointu z vlastního podokna úloh

1. V Návrháři dvakrát klikněte na <xref:System.Windows.Forms.MonthCalendar> ovládací prvek.

     Otevře se soubor **MyUserControl. cs** nebo **MyUserControl. vb** a vytvoří se obslužná rutina události pro <xref:System.Windows.Forms.MonthCalendar.DateChanged> událost.

2. Na začátek souboru přidejte následující kód. Tento kód vytvoří aliasy pro <xref:Microsoft.Office.Core> obory názvů [aplikace a PowerPoint](/previous-versions/office/developer/office-2010/ff763170%28v%3doffice.14%29) .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_TaskPaneMonthCalendar/MyUserControl.cs" id="Snippet1":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_TaskPaneMonthCalendar/MyUserControl.vb" id="Snippet1":::

3. Do třídy `MyUserControl` přidejte následující kód. Tento kód deklaruje objekt [Shape](/previous-versions/office/developer/office-2010/ff760244(v=office.14)) jako člena `MyUserControl` . V následujícím kroku použijete tento [obrazec](/previous-versions/office/developer/office-2010/ff760244(v=office.14)) k přidání textového pole do snímku v aktivní prezentaci.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_TaskPaneMonthCalendar/MyUserControl.cs" id="Snippet2":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_TaskPaneMonthCalendar/MyUserControl.vb" id="Snippet2":::

4. Proměnnou `monthCalendar1_DateChanged` obslužné rutiny události nahraďte následujícím kódem. Tento kód přidá do prvního snímku v aktivní prezentaci textové pole a pak do textového pole přidá aktuálně vybrané datum. Tento kód používá `Globals.ThisAddIn` objekt pro přístup k objektovému modelu aplikace PowerPoint.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_TaskPaneMonthCalendar/MyUserControl.cs" id="Snippet3":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_TaskPaneMonthCalendar/MyUserControl.vb" id="Snippet3":::

5. V **Průzkumník řešení** klikněte pravým tlačítkem na projekt **MyAddIn** a pak klikněte na **sestavit**. Ověřte, že se projekt vytváří bez chyb.

## <a name="display-the-custom-task-pane"></a>Zobrazit vlastní podokno úloh
 Pokud chcete zobrazit vlastní podokno úloh při spuštění doplňku VSTO, přidejte uživatelský ovládací prvek do podokna úloh v <xref:Microsoft.Office.Tools.AddIn.Startup> obslužné rutině události doplňku VSTO.

### <a name="to-display-the-custom-task-pane"></a>Zobrazení vlastního podokna úloh

1. V **Průzkumník řešení** rozbalte možnost **PowerPoint**.

2. Klikněte pravým tlačítkem na **ThisAddIn. cs** nebo **ThisAddIn. vb** a klikněte na **Zobrazit kód**.

3. Do třídy `ThisAddIn` přidejte následující kód. Tento kód deklaruje instance `MyUserControl` a <xref:Microsoft.Office.Tools.CustomTaskPane> jako členy `ThisAddIn` třídy.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_TaskPaneMonthCalendar/ThisAddIn.vb" id="Snippet4":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_TaskPaneMonthCalendar/ThisAddIn.cs" id="Snippet4":::

4. Proměnnou `ThisAddIn_Startup` obslužné rutiny události nahraďte následujícím kódem. Tento kód vytvoří nový <xref:Microsoft.Office.Tools.CustomTaskPane> přidáním `MyUserControl` objektu do `CustomTaskPanes` kolekce. Kód také zobrazí podokno úloh.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_TaskPaneMonthCalendar/ThisAddIn.vb" id="Snippet5":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_TaskPaneMonthCalendar/ThisAddIn.cs" id="Snippet5":::

## <a name="test-the-add-in"></a>Test doplňku
 Při spuštění projektu se otevře PowerPoint a v doplňku VSTO se zobrazí vlastní podokno úloh. Klikněte na <xref:System.Windows.Forms.MonthCalendar> ovládací prvek pro otestování kódu.

### <a name="to-test-your-vsto-add-in"></a>Testování doplňku VSTO

1. Stisknutím klávesy **F5** spusťte projekt.

2. Potvrďte, že se vlastní podokno úloh zobrazuje.

3. Klikněte na datum v <xref:System.Windows.Forms.MonthCalendar> ovládacím prvku v podokně úloh.

     Datum je vloženo do prvního snímku v aktivní prezentaci.

## <a name="next-steps"></a>Další kroky
 Další informace o tom, jak vytvořit vlastní podokna úloh, najdete v těchto tématech:

- Vytvoření vlastního podokna úloh v doplňku VSTO pro jinou aplikaci. Další informace o aplikacích, které podporují vlastní podokna úloh, najdete v tématu [vlastní podokna úloh](../vsto/custom-task-panes.md).

- Umožňuje vytvořit tlačítko pásu karet, které se dá použít k skrytí nebo zobrazení vlastního podokna úloh. Další informace najdete v tématu [Návod: Synchronizace vlastního podokna úloh pomocí tlačítka pásu karet](../vsto/walkthrough-synchronizing-a-custom-task-pane-with-a-ribbon-button.md).

- Slouží k vytvoření vlastního podokna úloh pro každou e-mailovou zprávu, která je otevřena v aplikaci Outlook. Další informace najdete v tématu [Návod: zobrazení vlastních podoken úloh s e-mailovými zprávami v aplikaci Outlook](../vsto/walkthrough-displaying-custom-task-panes-with-e-mail-messages-in-outlook.md).

## <a name="see-also"></a>Viz také
- [Vlastní podokna úloh](../vsto/custom-task-panes.md)
- [Postupy: Přidání vlastního podokna úloh do aplikace](../vsto/how-to-add-a-custom-task-pane-to-an-application.md)
- [Návod: Synchronizace vlastního podokna úloh s tlačítkem na pásu karet](../vsto/walkthrough-synchronizing-a-custom-task-pane-with-a-ribbon-button.md)
- [Návod: zobrazení vlastních podoken úloh s e-mailovými zprávami v aplikaci Outlook](../vsto/walkthrough-displaying-custom-task-panes-with-e-mail-messages-in-outlook.md)
