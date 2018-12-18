---
title: 'Návod: Automatizace aplikace z vlastního podokna úloh'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 25d6dd29f989f1ea2bbf95ce2b32e7d031e1953e
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "35675725"
---
# <a name="walkthrough-automate-an-application-from-a-custom-task-pane"></a>Návod: Automatizace aplikace z vlastního podokna úloh
  Tento návod ukazuje, jak vytvořit vlastního podokna úloh, který automatizuje aplikace PowerPoint. Vlastního podokna úloh vloží data do snímku, když uživatel klikne <xref:System.Windows.Forms.MonthCalendar> ovládací prvek, který je v podokně úloh.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
 I když tento návod používá konkrétně aplikace PowerPoint, koncepty jsme vám ukázali podle návodu platí pro všechny aplikace, které jsou uvedené výše.  
  
 Tento návod znázorňuje následující úlohy:  
  
-   Návrh uživatelského rozhraní vlastního podokna úloh.  
  
-   Automatizace aplikace PowerPoint z vlastního podokna úloh.  
  
-   Zobrazení vlastního podokna úloh v aplikaci PowerPoint.  
  
> [!NOTE]  
>  Váš počítač může v následujících pokynech zobrazovat odlišné názvy nebo umístění některých prvků uživatelského rozhraní sady Visual Studio. Tyto prvky jsou určeny edicí sady Visual Studio a použitým nastavením. Další informace najdete v tématu [přizpůsobení integrovaného vývojového prostředí sady Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="prerequisites"></a>Požadavky  
 K dokončení tohoto návodu budete potřebovat následující komponenty:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Aplikace Microsoft PowerPoint 2010 nebo [!INCLUDE[PowerPoint_15_short](../vsto/includes/powerpoint-15-short-md.md)].  
  
## <a name="create-the-add-in-project"></a>Vytvořte projekt doplňku  
 Prvním krokem je vytvoření projektu doplňku VSTO pro PowerPoint.  
  
### <a name="to-create-a-new-project"></a>Chcete-li vytvořit nový projekt  
  
1.  Vytvoření projektu doplňku VSTO pro PowerPoint s názvem **MyAddIn**, pomocí šablony projektu doplňku PowerPoint. Další informace najdete v tématu [postupy: vytvoření Office projekty v sadě Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Otevře **ThisAddIn.cs** nebo **ThisAddIn.vb** soubor kódu a přidá **MyAddIn** projektu **Průzkumníka řešení**.  
  
## <a name="design-the-user-interface-of-the-custom-task-pane"></a>Návrh uživatelského rozhraní vlastního podokna úloh  
 Neexistuje žádné vizuálního návrháře pro vlastní podokna úloh, ale můžete navrhnout uživatelský ovládací prvek rozložení, které chcete. Dále v tomto názorném postupu se přidat uživatelský ovládací prvek do vlastního podokna úloh.  
  
#### <a name="to-design-the-user-interface-of-the-custom-task-pane"></a>K návrhu uživatelského rozhraní vlastního podokna úloh  
  
1.  Na **projektu** nabídky, klikněte na tlačítko **přidat uživatelský ovládací prvek**.  
  
2.  V **přidat novou položku** dialogové okno pole, změňte název uživatelský ovládací prvek **MyUserControl**a klikněte na tlačítko **přidat**.  
  
     Uživatelský ovládací prvek se otevře v návrháři.  
  
3.  Z **běžné ovládací prvky** karty **nástrojů**, přetáhněte **MonthCalendar** ovládacího prvku do uživatelského ovládacího prvku.  
  
     Pokud **MonthCalendar** ovládacího prvku je větší než uživatelského ovládacího prvku na návrhovou plochu, změna velikosti uživatelského ovládacího prvku podle **MonthCalendar** ovládacího prvku.  
  
## <a name="automate-powerpoint-from-the-custom-task-pane"></a>Automatizace aplikace PowerPoint z vlastního podokna úloh  
 Účelem doplňku VSTO je do vybraného data na první snímek aktivní prezentace. Použití <xref:System.Windows.Forms.MonthCalendar.DateChanged> události ovládacího prvku pro přidání vybraného data pokaždé, když se změní.  
  
### <a name="to-automate-powerpoint-from-the-custom-task-pane"></a>K automatizaci aplikace PowerPoint z vlastního podokna úloh  
  
1.  V Návrháři dvakrát klikněte <xref:System.Windows.Forms.MonthCalendar> ovládacího prvku.  
  
     **MyUserControl.cs** nebo **MyUserControl.vb** soubor se otevře a obslužná rutina události <xref:System.Windows.Forms.MonthCalendar.DateChanged> události.  
  
2.  Na začátek souboru přidejte následující kód. Tento kód vytvoří aliasy pro <xref:Microsoft.Office.Core> a <xref:Microsoft.Office.Interop.PowerPoint> obory názvů.  
  
     [!code-csharp[Trin_TaskPaneMonthCalendar#1](../vsto/codesnippet/CSharp/Trin_TaskPaneMonthCalendar/MyUserControl.cs#1)]
     [!code-vb[Trin_TaskPaneMonthCalendar#1](../vsto/codesnippet/VisualBasic/Trin_TaskPaneMonthCalendar/MyUserControl.vb#1)]  
  
3.  Přidejte následující kód, který `MyUserControl` třídy. Tento kód deklaruje <xref:Microsoft.Office.Interop.PowerPoint.Shape> objektu jako člen `MyUserControl`. V tomto kroku použijete to <xref:Microsoft.Office.Interop.PowerPoint.Shape> přidáte textové pole na snímek v aktivní prezentace.  
  
     [!code-csharp[Trin_TaskPaneMonthCalendar#2](../vsto/codesnippet/CSharp/Trin_TaskPaneMonthCalendar/MyUserControl.cs#2)]
     [!code-vb[Trin_TaskPaneMonthCalendar#2](../vsto/codesnippet/VisualBasic/Trin_TaskPaneMonthCalendar/MyUserControl.vb#2)]  
  
4.  Nahradit `monthCalendar1_DateChanged` obslužné rutiny události s následujícím kódem. Tento kód přidá textové pole aktivní prezentace na první snímek a pak přidá do textového pole aktuálně vybrané datum. Tento kód používá `Globals.ThisAddIn` objektu pro přístup k modelu objektů aplikace PowerPoint.  
  
     [!code-csharp[Trin_TaskPaneMonthCalendar#3](../vsto/codesnippet/CSharp/Trin_TaskPaneMonthCalendar/MyUserControl.cs#3)]
     [!code-vb[Trin_TaskPaneMonthCalendar#3](../vsto/codesnippet/VisualBasic/Trin_TaskPaneMonthCalendar/MyUserControl.vb#3)]  
  
5.  V **Průzkumníku řešení**, klikněte pravým tlačítkem myši **MyAddIn** projektu a pak klikněte na tlačítko **sestavení**. Ověřte, že projekt se sestaví bez chyb.  
  
## <a name="display-the-custom-task-pane"></a>Zobrazit podokno úloh  
 Chcete-li zobrazit podokno úloh při spuštění doplňku VSTO, přidat uživatelský ovládací prvek do podokna úloh v <xref:Microsoft.Office.Tools.AddIn.Startup> obslužná rutina události doplňku VSTO.  
  
### <a name="to-display-the-custom-task-pane"></a>Pokud chcete zobrazit podokno úloh  
  
1.  V **Průzkumníka řešení**, rozbalte **PowerPoint**.  
  
2.  Klikněte pravým tlačítkem na **ThisAddIn.cs** nebo **ThisAddIn.vb** a klikněte na tlačítko **zobrazit kód**.  
  
3.  Přidejte následující kód, který `ThisAddIn` třídy. Tento kód deklaruje instance `MyUserControl` a <xref:Microsoft.Office.Tools.CustomTaskPane> jako členy `ThisAddIn` třídy.  
  
     [!code-vb[Trin_TaskPaneMonthCalendar#4](../vsto/codesnippet/VisualBasic/Trin_TaskPaneMonthCalendar/ThisAddIn.vb#4)]
     [!code-csharp[Trin_TaskPaneMonthCalendar#4](../vsto/codesnippet/CSharp/Trin_TaskPaneMonthCalendar/ThisAddIn.cs#4)]  
  
4.  Nahradit `ThisAddIn_Startup` obslužné rutiny události s následujícím kódem. Tento kód vytvoří novou <xref:Microsoft.Office.Tools.CustomTaskPane> tak, že přidáte `MyUserControl` objektu `CustomTaskPanes` kolekce. Kód také zobrazí v podokně úloh.  
  
     [!code-vb[Trin_TaskPaneMonthCalendar#5](../vsto/codesnippet/VisualBasic/Trin_TaskPaneMonthCalendar/ThisAddIn.vb#5)]
     [!code-csharp[Trin_TaskPaneMonthCalendar#5](../vsto/codesnippet/CSharp/Trin_TaskPaneMonthCalendar/ThisAddIn.cs#5)]  
  
## <a name="test-the-add-in"></a>Testování v aplikaci  
 Při spuštění projektu se otevře aplikace PowerPoint a doplňku VSTO zobrazí vlastního podokna úloh. Klikněte na tlačítko <xref:System.Windows.Forms.MonthCalendar> ovládací prvek pro otestování kódu.  
  
### <a name="to-test-your-vsto-add-in"></a>K otestování vašeho doplňku VSTO  
  
1.  Stisknutím klávesy **F5** ke spuštění projektu.  
  
2.  Potvrďte, že je viditelná vlastního podokna úloh.  
  
3.  Klikněte na datum v <xref:System.Windows.Forms.MonthCalendar> ovládacího prvku v podokně úloh.  
  
     Datum je vložen do první snímkem v aktivní prezentace.  
  
## <a name="next-steps"></a>Další kroky  
 Další informace o tom, jak vytvořit vlastní podokna úloh naleznete v těchto tématech:  
  
-   Vytvoření vlastního podokna úloh v doplňku VSTO pro jinou aplikaci. Další informace o aplikacích, které podporují vlastní podokna úloh, naleznete v tématu [vlastní podokna úloh](../vsto/custom-task-panes.md).  
  
-   Vytvoření tlačítka pásu karet, který umožňuje skrýt nebo zobrazit vlastního podokna úloh. Další informace najdete v tématu [návod: synchronizace vlastního podokna úloh s tlačítkem pásu karet](../vsto/walkthrough-synchronizing-a-custom-task-pane-with-a-ribbon-button.md).  
  
-   Vytvoření vlastního podokna úloh pro každou e-mailové zprávy, která je otevřena v Outlooku. Další informace najdete v tématu [návod: zobrazení vlastních podoken úloh s e-mailové zprávy v aplikaci Outlook](../vsto/walkthrough-displaying-custom-task-panes-with-e-mail-messages-in-outlook.md).  
  
## <a name="see-also"></a>Viz také:  
 [Vlastní podokna úloh](../vsto/custom-task-panes.md)   
 [Postupy: Přidání vlastního podokna úloh do aplikace](../vsto/how-to-add-a-custom-task-pane-to-an-application.md)   
 [Návod: Synchronizace vlastního podokna úloh s tlačítkem pásu karet](../vsto/walkthrough-synchronizing-a-custom-task-pane-with-a-ribbon-button.md)   
 [Návod: Zobrazení vlastních podoken úloh s e-mailové zprávy v aplikaci Outlook](../vsto/walkthrough-displaying-custom-task-panes-with-e-mail-messages-in-outlook.md)  
  
  