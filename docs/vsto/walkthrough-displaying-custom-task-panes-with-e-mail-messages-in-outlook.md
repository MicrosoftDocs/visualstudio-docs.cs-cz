---
title: 'Návod: Zobrazení vlastních podoken úloh s e-mailové zprávy v aplikaci Outlook'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Outlook [Office development in Visual Studio], custom task panes
- task panes [Office development in Visual Studio], displaying with e-mail messages
- displaying custom task panes in e-mail
- e-mail [Office development in Visual Studio], custom task panes displayed in
- custom task panes [Office development in Visual Studio], displaying with e-mail messages
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 1c25121e96005486450397938aad3c24f89d26cc
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49828465"
---
# <a name="walkthrough-display-custom-task-panes-with-email-messages-in-outlook"></a>Návod: Zobrazení vlastních podoken úloh s e-mailové zprávy v aplikaci Outlook
  Tento návod ukazuje, jak zobrazit jedinečnou instanci vlastního podokna úloh s každou e-mailové zprávy, který je vytvořen nebo otevřen. Uživatelům můžete zobrazit nebo skrýt podokno úloh s použitím tlačítko na pásu karet z každého e-mailové zprávy.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
 K zobrazení vlastního podokna úloh s více Průzkumníka nebo kontrola systému windows, musíte vytvořit instance vlastního podokna úloh pro všechna okna, která je otevřena. Další informace o chování vlastních podoken úloh v aplikaci Outlook windows najdete v tématu [vlastní podokna úloh](../vsto/custom-task-panes.md).  
  
> [!NOTE]  
>  Tento názorný postup představuje kód doplňku VSTO v malých oddílech, aby bylo snazší fattica logiku za kód.  
  
 Tento návod znázorňuje následující úlohy:  
  
-   Návrh uživatelského rozhraní (UI) z vlastního podokna úloh.  
  
-   Vytvoření vlastního uživatelského rozhraní pásu karet.  
  
-   Zobrazení vlastního uživatelského rozhraní pásu karet pomocí e-mailové zprávy.  
  
-   Vytvoření třídy pro správu Inspector windows a vlastní podokna úloh.  
  
-   Inicializace a Uklízení prostředky využívané třídou doplňku VSTO.  
  
-   Synchronizace přepínací tlačítko pásu karet pomocí vlastního podokna úloh.  
  
> [!NOTE]  
>  Váš počítač může v následujících pokynech zobrazovat odlišné názvy nebo umístění některých prvků uživatelského rozhraní sady Visual Studio. Tyto prvky jsou určeny edicí sady Visual Studio a použitým nastavením. Další informace najdete v tématu [přizpůsobení integrovaného vývojového prostředí sady Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="prerequisites"></a>Požadavky  
 K dokončení tohoto návodu budete potřebovat následující komponenty:  
  
- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
- Microsoft [!INCLUDE[Outlook_15_short](../vsto/includes/outlook-15-short-md.md)] nebo aplikace Microsoft Outlook 2010.  
  
  ![odkaz na video](../vsto/media/playvideo.gif "odkaz na video") související video ukázku naleznete v tématu [jak mohu: použití podokna úloh v aplikaci Outlook?](http://go.microsoft.com/fwlink/?LinkID=130309).  
  
## <a name="create-the-project"></a>Vytvoření projektu  
 Vlastní podokna úloh jsou implementovány v doplňcích VSTO. Začněte vytvořením projektu doplňku VSTO pro Outlook.  
  
### <a name="to-create-a-new-project"></a>Chcete-li vytvořit nový projekt  
  
1.  Vytvoření **doplňku aplikace Outlook** projektu s názvem **OutlookMailItemTaskPane**. Použití **doplňku aplikace Outlook** šablony projektu. Další informace najdete v tématu [postupy: vytvoření Office projekty v sadě Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Otevře *ThisAddIn.cs* nebo *ThisAddIn.vb* soubor kódu a přidá **OutlookMailItemTaskPane** projektu **Průzkumníka řešení**.  
  
## <a name="design-the-user-interface-of-the-custom-task-pane"></a>Návrh uživatelského rozhraní vlastního podokna úloh  
 Neexistuje žádné vizuálního návrháře pro vlastní podokna úloh, ale můžete navrhnout uživatelský ovládací prvek, že chcete v uživatelském rozhraní. V podokně úloh v tomto doplňku VSTO má jednoduché uživatelské rozhraní, která obsahuje <xref:System.Windows.Forms.TextBox> ovládacího prvku. Dále v tomto názorném postupu se přidat uživatelský ovládací prvek do vlastního podokna úloh.  
  
### <a name="to-design-the-user-interface-of-the-custom-task-pane"></a>K návrhu uživatelského rozhraní vlastního podokna úloh  
  
1.  V **Průzkumníka řešení**, klikněte na tlačítko **OutlookMailItemTaskPane** projektu.  
  
2.  Na **projektu** nabídky, klikněte na tlačítko **přidat uživatelský ovládací prvek**.  
  
3.  V **přidat novou položku** dialogové okno pole, změňte název uživatelský ovládací prvek **TaskPaneControl**a potom klikněte na tlačítko **přidat**.  
  
     Uživatelský ovládací prvek se otevře v návrháři.  
  
4.  Z **běžné ovládací prvky** karty **nástrojů**, přetáhněte **textového pole** ovládacího prvku do uživatelského ovládacího prvku.  
  
## <a name="design-the-user-interface-of-the-ribbon"></a>Návrh uživatelského rozhraní na pásu karet  
 Jedním z cílů tohoto doplňku VSTO je poskytnout uživatelům způsob, jak skrýt nebo zobrazit podokno úloh na pásu karet každou e-mailové zprávy. K poskytování uživatelského rozhraní, vytvoření vlastního uživatelského rozhraní pásu karet, která zobrazuje přepínací tlačítko, které mohou uživatelé kliknout a zobrazit nebo skrýt podokno úloh.  
  
### <a name="to-create-a-custom-ribbon-ui"></a>Vytvoření vlastního uživatelského rozhraní pásu karet  
  
1.  Na **projektu** nabídky, klikněte na tlačítko **přidat novou položku**.  
  
2.  V **přidat novou položku** dialogu **pás karet (vizuální návrhář)**.  
  
3.  Změňte název nového pásu karet na **ManageTaskPaneRibbon**a klikněte na tlačítko **přidat**.  
  
     *ManageTaskPaneRibbon.cs* nebo *ManageTaskPaneRibbon.vb* soubor se otevře v Návrháři pásu karet a zobrazí výchozí kartu a skupinu.  
  
4.  V Návrháři pásu karet klikněte na tlačítko **group1**.  
  
5.  V **vlastnosti** okno, nastaveno **popisek** vlastnost **správce podokna úloh**.  
  
6.  Z **ovládací prvky Ribbon Office** karty **nástrojů**, přetáhněte ovládací prvek ToggleButton na **správce podokna úloh** skupiny.  
  
7.  Klikněte na tlačítko **toggleButton1**.  
  
8.  V **vlastnosti** okno, nastaveno **popisek** vlastnost **zobrazit podokno úloh**.  
  
## <a name="display-the-custom-ribbon-user-interface-with-email-messages"></a>Zobrazit vlastní uživatelské rozhraní pásu karet pomocí e-mailové zprávy  
 Vlastního podokna úloh, který vytvoříte v tomto návodu je navržen pro zobrazí pouze v systému windows Inspector, které obsahují e-mailové zprávy. Proto nastavte vlastnosti, které chcete zobrazit vlastní uživatelské rozhraní pásu karet pouze pomocí těchto oken.  
  
### <a name="to-display-the-custom-ribbon-ui-with-email-messages"></a>Zobrazit vlastní uživatelské rozhraní pásu karet pomocí e-mailové zprávy  
  
1.  V Návrháři pásu karet klikněte na tlačítko **ManageTaskPaneRibbon** pásu karet.  
  
2.  V **vlastnosti** okna, klikněte rozevírací seznam vedle **RibbonType**a vyberte **Microsoft.Outlook.Mail.Compose** a  **Microsoft.Outlook.Mail.Read**.  
  
## <a name="create-a-class-to-manage-inspector-windows-and-custom-task-panes"></a>Vytvořte třídu pro správu inspector windows a vlastních podoken úloh  
 Existuje několik případů, ve kterých doplňku VSTO musí určit, které vlastního podokna úloh spojené s konkrétní e-mailové zprávy. Tyto případy zahrnují následující:  
  
- Když uživatel zavírá e-mailovou zprávu. V takovém případě doplňku VSTO musíte odebrat odpovídající vlastního podokna úloh k zajištění, že se správně vyčistí prostředky využívané třídou doplňku VSTO.  
  
- Když uživatel zavírá vlastního podokna úloh. V takovém případě doplňku VSTO musí aktualizovat stav přepínacího tlačítka na pás karet e-mailové zprávy.  
  
- Když uživatel klepne na přepínací tlačítko na pásu karet. V takovém případě doplňku VSTO musí skrýt nebo zobrazit příslušné podokno úloh.  
  
  Povolit doplňku VSTO pro sledovat, které vlastního podokna úloh je spojené s každou otevřít e-mailové zprávy, vytvořte vlastní třídu, která zabalí dvojice <xref:Microsoft.Office.Interop.Outlook.Inspector> a <xref:Microsoft.Office.Tools.CustomTaskPane> objekty. Tato třída vytvoří nový objekt podokno úloh pro každou e-mailovou zprávu a odstraní vlastního podokna úloh, při zavření odpovídající e-mailové zprávy.  
  
### <a name="to-create-a-class-to-manage-inspector-windows-and-custom-task-panes"></a>Pro vytvoření třídy pro správu inspector windows a vlastních podoken úloh  
  
1.  V **Průzkumníku řešení**, klikněte pravým tlačítkem myši *ThisAddIn.cs* nebo *ThisAddIn.vb* souboru a pak klikněte na tlačítko **zobrazit kód**.  
  
2.  Na začátek souboru přidejte následující příkazy.  
  
     [!code-csharp[Trin_OutlookMailItemTaskPane#2](../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ThisAddIn.cs#2)]
     [!code-vb[Trin_OutlookMailItemTaskPane#2](../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ThisAddIn.vb#2)]  
  
3.  Přidejte následující kód, který *ThisAddIn.cs* nebo *ThisAddIn.vb* souboru mimo `ThisAddIn` třídy (Visual C#, přidejte tento kód `OutlookMailItemTaskPane` oboru názvů). `InspectorWrapper` Třída spravuje pár <xref:Microsoft.Office.Interop.Outlook.Inspector> a <xref:Microsoft.Office.Tools.CustomTaskPane> objekty. Definici této třídy v následujících krocích se dokončí.  
  
     [!code-csharp[Trin_OutlookMailItemTaskPane#3](../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ThisAddIn.cs#3)]
     [!code-vb[Trin_OutlookMailItemTaskPane#3](../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ThisAddIn.vb#3)]  
  
4.  Přidejte následující konstruktor za kód, který jste přidali v předchozím kroku. Tento konstruktor vytvoří a inicializuje nového vlastního podokna úloh, který je přidružen <xref:Microsoft.Office.Interop.Outlook.Inspector> objekt, který je předán. V jazyce C#, konstruktor také připisuje obslužných rutin událostí k <xref:Microsoft.Office.Interop.Outlook.InspectorEvents_Event.Close> událost <xref:Microsoft.Office.Interop.Outlook.Inspector> objekt a <xref:Microsoft.Office.Tools.CustomTaskPane.VisibleChanged> událost <xref:Microsoft.Office.Tools.CustomTaskPane> objektu.  
  
     [!code-csharp[Trin_OutlookMailItemTaskPane#4](../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ThisAddIn.cs#4)]
     [!code-vb[Trin_OutlookMailItemTaskPane#4](../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ThisAddIn.vb#4)]  
  
5.  Přidejte následující metodu za kód, který jste přidali v předchozím kroku. Tato metoda je obslužná rutina události <xref:Microsoft.Office.Tools.CustomTaskPane.VisibleChanged> událost <xref:Microsoft.Office.Tools.CustomTaskPane> objekt, který je součástí `InspectorWrapper` třídy. Tento kód aktualizuje stav přepínacího tlačítka vždy, když uživatel otevře nebo zavře vlastního podokna úloh.  
  
     [!code-csharp[Trin_OutlookMailItemTaskPane#5](../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ThisAddIn.cs#5)]
     [!code-vb[Trin_OutlookMailItemTaskPane#5](../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ThisAddIn.vb#5)]  
  
6.  Přidejte následující metodu za kód, který jste přidali v předchozím kroku. Tato metoda je obslužná rutina události <xref:Microsoft.Office.Interop.Outlook.InspectorEvents_Event.Close> událost <xref:Microsoft.Office.Interop.Outlook.Inspector> objekt, který obsahuje aktuální e-mailové zprávy. Obslužná rutina události uvolní prostředky při zavření e-mailové zprávy. Obslužná rutina události taky odstraní aktuální vlastního podokna úloh z `CustomTaskPanes` kolekce. To pomáhá zabránit více instancí vlastního podokna úloh po otevření další e-mailové zprávy.  
  
     [!code-csharp[Trin_OutlookMailItemTaskPane#6](../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ThisAddIn.cs#6)]
     [!code-vb[Trin_OutlookMailItemTaskPane#6](../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ThisAddIn.vb#6)]  
  
7.  Přidejte následující kód za kód, který jste přidali v předchozím kroku. Později v tomto návodu bude volat tuto vlastnost z metody v Uživatelském rozhraní pásu karet vlastní zobrazení nebo skrytí vlastního podokna úloh.  
  
     [!code-csharp[Trin_OutlookMailItemTaskPane#7](../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ThisAddIn.cs#7)]
     [!code-vb[Trin_OutlookMailItemTaskPane#7](../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ThisAddIn.vb#7)]  
  
## <a name="initialize-and-clean-up-resources-used-by-the-add-in"></a>Inicializace a vyčištění prostředky využívané třídou doplňku  
 Přidejte kód, který `ThisAddIn` třídy k inicializaci doplňku VSTO, když je načten a chcete vyčistit prostředky využívané třídou doplňku VSTO, když je uvolněn. Nastavením obslužné rutiny události pro inicializaci doplňku VSTO <xref:Microsoft.Office.Interop.Outlook.InspectorsEvents_Event.NewInspector> událostí a předáním všechny existující e-mailové zprávy této obslužné rutiny události. Když je uvolněn doplněk VSTO, odpojení obslužné rutiny události a vyčištění objekty používané doplňku VSTO.  
  
### <a name="to-initialize-and-clean-up-resources-used-by-the-vsto-add-in"></a>K inicializaci a vyčistit prostředky využívané třídou doplňku VSTO  
  
1. V *ThisAddIn.cs* nebo *ThisAddIn.vb* souboru, vyhledejte definici `ThisAddIn` třídy.  
  
2. Přidejte následující deklarace do `ThisAddIn` třídy:  
  
   - `inspectorWrappersValue` Pole obsahuje všechny <xref:Microsoft.Office.Interop.Outlook.Inspector> a `InspectorWrapper` objekty, které se spravují přes doplňku VSTO.  
  
   - `inspectors` Pole udržuje odkaz na sadu windows Inspectoru v aktuální instanci aplikace Outlook. Tento odkaz zabraňuje systému uvolňování paměti v uvolňování paměti, která obsahuje obslužnou rutinu události pro <xref:Microsoft.Office.Interop.Outlook.InspectorsEvents_Event.NewInspector> události, které deklarujete v dalším kroku.  
  
     [!code-csharp[Trin_OutlookMailItemTaskPane#8](../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ThisAddIn.cs#8)]
     [!code-vb[Trin_OutlookMailItemTaskPane#8](../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ThisAddIn.vb#8)]  
  
3. Nahradit `ThisAddIn_Startup` metodu s následujícím kódem. Připojí obslužnou rutinu události pro tento kód <xref:Microsoft.Office.Interop.Outlook.InspectorsEvents_Event.NewInspector> události a předává všechny existující <xref:Microsoft.Office.Interop.Outlook.Inspector> objekt obslužné rutiny události. Pokud uživatel načte doplňku VSTO po aplikace Outlook je již spuštěna, doplňku VSTO používá tyto informace k vytvoření vlastních podoken úloh pro všechny e-mailové zprávy, které už jsou otevřená.  
  
    [!code-csharp[Trin_OutlookMailItemTaskPane#9](../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ThisAddIn.cs#9)]
    [!code-vb[Trin_OutlookMailItemTaskPane#9](../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ThisAddIn.vb#9)]  
  
4. Nahradit `ThisAddIn_ShutDown` metodu s následujícím kódem. Odpojí tento kód <xref:Microsoft.Office.Interop.Outlook.InspectorsEvents_Event.NewInspector> obslužné rutiny události a vyčistí objekty používané doplňku VSTO.  
  
    [!code-csharp[Trin_OutlookMailItemTaskPane#10](../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ThisAddIn.cs#10)]
    [!code-vb[Trin_OutlookMailItemTaskPane#10](../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ThisAddIn.vb#10)]  
  
5. Přidejte následující <xref:Microsoft.Office.Interop.Outlook.InspectorsEvents_Event.NewInspector> obslužnou rutinu události `ThisAddIn` třídy. Pokud se nová <xref:Microsoft.Office.Interop.Outlook.Inspector> obsahuje e-mailovou zprávu, metoda vytvoří instanci nové `InspectorWrapper` objektu, který chcete spravovat vztah mezi e-mailové zprávy a odpovídající podokna úloh.  
  
    [!code-csharp[Trin_OutlookMailItemTaskPane#11](../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ThisAddIn.cs#11)]
    [!code-vb[Trin_OutlookMailItemTaskPane#11](../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ThisAddIn.vb#11)]  
  
6. Přidejte následující vlastnost, která má `ThisAddIn` třídy. Tato vlastnost poskytuje privátní `inspectorWrappersValue` kód mimo pole `ThisAddIn` třídy.  
  
    [!code-csharp[Trin_OutlookMailItemTaskPane#12](../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ThisAddIn.cs#12)]
    [!code-vb[Trin_OutlookMailItemTaskPane#12](../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ThisAddIn.vb#12)]  
  
## <a name="checkpoint"></a>Kontrolní bod  
 Sestavte projekt k zajištění, že se zkompiluje bez chyb.  
  
### <a name="to-build-your-project"></a>K sestavení projektu  
  
1.  V **Průzkumníku řešení**, klikněte pravým tlačítkem myši **OutlookMailItemTaskPane** projektu a pak klikněte na tlačítko **sestavení**. Ověřte, že se projekt zkompiluje bez chyb.  
  
## <a name="synchronize-the-ribbon-toggle-button-with-the-custom-task-pane"></a>Synchronizovat přepínací tlačítko pásu karet pomocí vlastního podokna úloh  
 Přepínací tlačítko se zobrazí stisknuto, když se zobrazuje podokno úloh, se zobrazí na nesmí být stisknuto po skrytí podokna úloh. Chcete-li synchronizovat stav tlačítka s vlastní podokno úloh, upravte <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton.Click> obslužná rutina události přepínacího tlačítka.  
  
### <a name="to-synchronize-the-custom-task-pane-with-the-toggle-button"></a>Synchronizace vlastního podokna úloh s přepínací tlačítko  
  
1.  V Návrháři pásu karet klikněte dvakrát na **zobrazit podokno úloh** přepínacího tlačítka.  
  
     Visual Studio vygeneruje obslužnou rutinu události s názvem automaticky `toggleButton1_Click`, která zpracovává <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton.Click> události přepínacího tlačítka. Visual Studio také otevře *ManageTaskPaneRibbon.cs* nebo *ManageTaskPaneRibbon.vb* souboru v editoru kódu.  
  
2.  Přidejte následující příkazy k hornímu okraji *ManageTaskPaneRibbon.cs* nebo *ManageTaskPaneRibbon.vb* souboru.  
  
     [!code-csharp[Trin_OutlookMailItemTaskPane#14](../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ManageTaskPaneRibbon.cs#14)]
     [!code-vb[Trin_OutlookMailItemTaskPane#14](../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ManageTaskPaneRibbon.vb#14)]  
  
3.  Nahradit `toggleButton1_Click` obslužné rutiny události s následujícím kódem. Když uživatel klikne na přepínací tlačítko, tato metoda skryje nebo zobrazí vlastního podokna úloh, která souvisí s aktuálním okně Inspektor.  
  
     [!code-csharp[Trin_OutlookMailItemTaskPane#15](../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ManageTaskPaneRibbon.cs#15)]
     [!code-vb[Trin_OutlookMailItemTaskPane#15](../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ManageTaskPaneRibbon.vb#15)]  
  
## <a name="test-the-project"></a>Testování projektu  
 Při spuštění ladění projektu se otevře aplikace Outlook a načtení doplňku VSTO. Doplněk VSTO zobrazuje jedinečnou instanci vlastního podokna úloh s každou e-mailovou zprávu, která je otevřena. Vytvořte několik nových e-mailové zprávy pro otestování kódu.  
  
### <a name="to-test-the-vsto-add-in"></a>K otestování doplňku VSTO  
  
1. Stisknutím klávesy **F5**.  
  
2. V aplikaci Outlook, klikněte na tlačítko **nový** vytvořte novou e-mailové zprávy.  
  
3. Na pásu karet e-mailové zprávy, klikněte na tlačítko **Add-Ins** kartu a potom klikněte na tlačítko **zobrazit podokno úloh** tlačítko.  
  
    Ověřte, že podokna úloh s názvem **podokno úloh** se zobrazí u e-mailové zprávy.  
  
4. V podokně úloh zadejte **prvního podokna úloh** v textovém poli.  
  
5. Zavřete podokno úloh.  
  
    Ověřte, že stav **zobrazit podokno úloh** tlačítko změní tak, aby se už stiskne.  
  
6. Klikněte na tlačítko **zobrazit podokno úloh** tlačítko znovu.  
  
    Ověřte, že se otevře podokno úloh a textovém poli stále obsahuje řetězec **prvního podokna úloh**.  
  
7. V aplikaci Outlook, klikněte na tlačítko **nový** vytvořte druhý e-mailové zprávy.  
  
8. Na pásu karet e-mailové zprávy, klikněte na tlačítko **Add-Ins** kartu a potom klikněte na tlačítko **zobrazit podokno úloh** tlačítko.  
  
    Ověřte, že podokna úloh s názvem **podokno úloh** se zobrazí u e-mailové zprávě, a do textového pole v tomto podokně je prázdný.  
  
9. V podokně úloh zadejte **druhé podokno úloh** v textovém poli.  
  
10. Změňte fokus na první e-mailové zprávy.  
  
     Ověřte, že podokna úloh, který je přidružený k této e-mailová zpráva stále zobrazuje **prvního podokna úloh** v textovém poli.  
  
    Tento doplněk VSTO také zpracovává více pokročilé scénáře, které můžete vyzkoušet. Například můžete otestovat chování při zobrazení e-mailů pomocí **další položku** a **předchozí položka** tlačítka. Můžete také testovat chování při uvolnění doplňku VSTO, otevřete několik e-mailové zprávy a pak znovu načtěte doplňku VSTO.  
  
## <a name="next-steps"></a>Další kroky  
 Další informace o tom, jak vytvořit vlastní podokna úloh naleznete v těchto tématech:  
  
-   Vytvoření vlastního podokna úloh v doplňku VSTO pro jinou aplikaci. Další informace o aplikacích, které podporují vlastní podokna úloh, naleznete v tématu [vlastní podokna úloh](../vsto/custom-task-panes.md).  
  
-   Automatizace aplikací sady Microsoft Office s použitím vlastního podokna úloh. Další informace najdete v tématu [návod: automatizace aplikace z vlastního podokna úloh](../vsto/walkthrough-automating-an-application-from-a-custom-task-pane.md).  
  
-   Vytvoření tlačítka pásu karet v Excelu, který umožňuje skrýt nebo zobrazit vlastního podokna úloh. Další informace najdete v tématu [návod: synchronizace vlastního podokna úloh s tlačítkem pásu karet](../vsto/walkthrough-synchronizing-a-custom-task-pane-with-a-ribbon-button.md).  
  
## <a name="see-also"></a>Viz také:  
 [Vlastní podokna úloh](../vsto/custom-task-panes.md)   
 [Postupy: Přidání vlastního podokna úloh do aplikace](../vsto/how-to-add-a-custom-task-pane-to-an-application.md)   
 [Návod: Automatizace aplikace z vlastního podokna úloh](../vsto/walkthrough-automating-an-application-from-a-custom-task-pane.md)   
 [Návod: Synchronizace vlastního podokna úloh s tlačítkem pásu karet](../vsto/walkthrough-synchronizing-a-custom-task-pane-with-a-ribbon-button.md)   
 [Přehled pásu karet](../vsto/ribbon-overview.md)   
 [Přehled modelu objektů aplikace Outlook](../vsto/outlook-object-model-overview.md)   
 [Přístup k pásu karet za běhu](../vsto/accessing-the-ribbon-at-run-time.md)  
  
  