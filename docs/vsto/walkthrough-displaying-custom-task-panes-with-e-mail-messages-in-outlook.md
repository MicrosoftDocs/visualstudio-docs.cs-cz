---
title: Zobrazení vlastních podoken úloh s e-mailovými zprávami v Outlooku
ms.date: 02/02/2017
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
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 9e94bedf95b58d9876d37eb496ede0c5ec9a8531
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/28/2019
ms.locfileid: "72985457"
---
# <a name="walkthrough-display-custom-task-panes-with-email-messages-in-outlook"></a>Návod: zobrazení vlastních podoken úloh s e-mailovými zprávami v aplikaci Outlook
  Tento návod ukazuje, jak zobrazit jedinečnou instanci vlastního podokna úloh s každou vytvořenou nebo otevřenou e-mailovou zprávou. Uživatelé mohou vlastní podokno úloh Zobrazit nebo skrýt pomocí tlačítka na pásu karet jednotlivých e-mailových zpráv.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

 Chcete-li zobrazit vlastní podokno úloh s více okny Průzkumníka nebo nástroje Inspector, je nutné vytvořit instanci vlastního podokna úloh pro každé otevřené okno. Další informace o chování vlastních podoken úloh v oknech Outlooku najdete v tématu [vlastní podokna úloh](../vsto/custom-task-panes.md).

> [!NOTE]
> Tento návod prezentuje kód doplňku VSTO v malých částech, aby bylo snazší diskutovat o logice za kódem.

 Tento návod znázorňuje následující úlohy:

- Návrh uživatelského rozhraní (UI) vlastního podokna úloh.

- Vytvoření vlastního uživatelského rozhraní pásu karet.

- Zobrazení uživatelského rozhraní vlastního pásu karet pomocí e-mailových zpráv.

- Vytvoření třídy pro správu oken Inspector a vlastních podoken úloh.

- Inicializace a vyčištění prostředků používaných doplňkem VSTO.

- Probíhá synchronizace přepínacího tlačítka pásu karet s vlastním podoknem úloh.

> [!NOTE]
> Váš počítač může v následujících pokynech zobrazovat odlišné názvy nebo umístění některých prvků uživatelského rozhraní sady Visual Studio. Tyto prvky jsou určeny edicí sady Visual Studio a použitým nastavením. Další informace najdete v tématu [Přizpůsobení integrovaného vývojového prostředí (IDE) sady Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Požadavky
 K dokončení tohoto návodu budete potřebovat následující komponenty:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- Microsoft [!INCLUDE[Outlook_15_short](../vsto/includes/outlook-15-short-md.md)] nebo Microsoft Outlook 2010.

## <a name="create-the-project"></a>Vytvoření projektu
 Vlastní podokna úloh jsou implementovaná v doplňcích VSTO. Začněte tím, že vytvoříte projekt doplňku VSTO pro Outlook.

### <a name="to-create-a-new-project"></a>Vytvoření nového projektu

1. Vytvořte projekt **doplňku pro Outlook** s názvem **OutlookMailItemTaskPane**. Použijte šablonu projektu **doplňku pro Outlook** . Další informace najdete v tématu [Postupy: vytváření projektů pro systém Office v sadě Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] otevře soubor kódu *ThisAddIn.cs* nebo *ThisAddIn. vb* a přidá projekt **OutlookMailItemTaskPane** do **Průzkumník řešení**.

## <a name="design-the-user-interface-of-the-custom-task-pane"></a>Návrh uživatelského rozhraní vlastního podokna úloh
 Není k dispozici žádný vizuální Návrhář pro vlastní podokna úloh, ale můžete navrhnout uživatelský ovládací prvek se svým uživatelským ROZHRANÍm, které chcete. Vlastní podokno úloh v tomto doplňku VSTO má jednoduché uživatelské rozhraní, které obsahuje ovládací prvek <xref:System.Windows.Forms.TextBox>. Později v tomto návodu přidáte uživatelský ovládací prvek do vlastního podokna úloh.

### <a name="to-design-the-user-interface-of-the-custom-task-pane"></a>Návrh uživatelského rozhraní vlastního podokna úloh

1. V **Průzkumník řešení**klikněte na projekt **OutlookMailItemTaskPane** .

2. V nabídce **projekt** klikněte na příkaz **Přidat uživatelský ovládací prvek**.

3. V dialogovém okně **Přidat novou položku** změňte název uživatelského ovládacího prvku na **TaskPaneControl**a potom klikněte na tlačítko **Přidat**.

     Uživatelský ovládací prvek se otevře v návrháři.

4. Na kartě **běžné ovládací prvky** **panelu nástrojů**přetáhněte ovládací prvek **TextBox** do uživatelského ovládacího prvku.

## <a name="design-the-user-interface-of-the-ribbon"></a>Návrh uživatelského rozhraní pásu karet
 Jedním z cílů tohoto doplňku VSTO je poskytnout uživatelům způsob, jak skrýt nebo zobrazit vlastní podokno úloh na pásu karet jednotlivých e-mailových zpráv. K poskytnutí uživatelského rozhraní můžete vytvořit vlastní uživatelské rozhraní pásu karet, které zobrazí přepínací tlačítko, na které uživatelé můžou kliknout a zobrazit nebo skrýt vlastní podokno úloh.

### <a name="to-create-a-custom-ribbon-ui"></a>Vytvoření vlastního uživatelského rozhraní pásu karet

1. V nabídce **projekt** klikněte na příkaz **Přidat novou položku**.

2. V dialogovém okně **Přidat novou položku** vyberte možnost **pás karet (vizuální Návrhář)** .

3. Změňte název nového pásu karet na **ManageTaskPaneRibbon**a klikněte na **Přidat**.

     Otevře se soubor *ManageTaskPaneRibbon.cs* nebo *ManageTaskPaneRibbon. vb* v Návrháři pásu karet a zobrazí výchozí kartu a skupinu.

4. V Návrháři pásu karet klikněte na **Group1**.

5. V okně **vlastnosti** nastavte vlastnost **popisek** na **Správce podokna úloh**.

6. Na kartě **ovládací prvky pásu karet Office** přetáhněteovládací prvek ToggleButton do skupiny **Správce podokna úloh** .

7. Klikněte na **ToggleButton1**.

8. V okně **vlastnosti** nastavte vlastnost **popisek** na **Zobrazit podokno úloh**.

## <a name="display-the-custom-ribbon-user-interface-with-email-messages"></a>Zobrazit uživatelské rozhraní vlastního pásu karet pomocí e-mailových zpráv
 Vlastní podokno úloh, které vytvoříte v tomto průvodci, je navrženo tak, aby se zobrazilo pouze s okny inspektoru obsahujícím e-mailové zprávy. Proto nastavte vlastnosti tak, aby zobrazovaly vlastní uživatelské rozhraní pásu karet jenom s těmito okny.

### <a name="to-display-the-custom-ribbon-ui-with-email-messages"></a>Zobrazení uživatelského rozhraní vlastního pásu karet pomocí e-mailových zpráv

1. V Návrháři pásu karet klikněte na pás karet **ManageTaskPaneRibbon** .

2. V okně **vlastnosti** klikněte na rozevírací seznam vedle **RibbonType**a vyberte **Microsoft. Outlook. mail.** Form a **Microsoft. Outlook. mail. Read**.

## <a name="create-a-class-to-manage-inspector-windows-and-custom-task-panes"></a>Vytvoření třídy pro správu oken Inspector a vlastních podoken úloh
 V některých případech musí doplněk VSTO určit, které vlastní podokno úloh je přidruženo k konkrétní e-mailové zprávě. Tyto případy jsou následující:

- Když uživatel zavře e-mailovou zprávu. V takovém případě musí doplněk VSTO odebrat odpovídající vlastní podokno úloh, aby se zajistilo správné vyčištění prostředků používaných doplňkem VSTO.

- Když uživatel zavře vlastní podokno úloh. V takovém případě musí doplněk VSTO aktualizovat stav přepínacího tlačítka na pásu karet e-mailové zprávy.

- Když uživatel klikne na pás karet na tlačítko přepínacího tlačítka. V takovém případě musí doplněk VSTO skrýt nebo zobrazit odpovídající podokno úloh.

  Aby doplněk VSTO mohl sledovat, které vlastní podokno úloh je přidružené k jednotlivým otevřeným e-mailovým zprávám, vytvořte vlastní třídu, která obaluje páry objektů <xref:Microsoft.Office.Interop.Outlook.Inspector> a <xref:Microsoft.Office.Tools.CustomTaskPane>. Tato třída vytvoří nový objekt vlastního podokna úloh pro každou e-mailovou zprávu a odstraní vlastní podokno úloh při zavření odpovídající e-mailové zprávy.

### <a name="to-create-a-class-to-manage-inspector-windows-and-custom-task-panes"></a>Vytvoření třídy pro správu oken Inspector a vlastních podoken úloh

1. V **Průzkumník řešení**klikněte pravým tlačítkem myši na soubor *ThisAddIn.cs* nebo *ThisAddIn. vb* a pak klikněte na **Zobrazit kód**.

2. Na začátek souboru přidejte následující příkazy.

     [!code-csharp[Trin_OutlookMailItemTaskPane#2](../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ThisAddIn.cs#2)]
     [!code-vb[Trin_OutlookMailItemTaskPane#2](../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ThisAddIn.vb#2)]

3. Přidejte následující kód do souboru *ThisAddIn.cs* nebo *ThisAddIn. vb* mimo třídu `ThisAddIn` (pro vizuál C#přidejte tento kód do`OutlookMailItemTaskPane`oboru názvů). Třída `InspectorWrapper` spravuje dvojici objektů <xref:Microsoft.Office.Interop.Outlook.Inspector> a <xref:Microsoft.Office.Tools.CustomTaskPane>. Definici této třídy dokončíte v následujících krocích.

     [!code-csharp[Trin_OutlookMailItemTaskPane#3](../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ThisAddIn.cs#3)]
     [!code-vb[Trin_OutlookMailItemTaskPane#3](../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ThisAddIn.vb#3)]

4. Přidejte následující konstruktor za kód, který jste přidali v předchozím kroku. Tento konstruktor vytvoří a inicializuje nové vlastní podokno úloh, které je spojeno s předaným objektem <xref:Microsoft.Office.Interop.Outlook.Inspector>. V C#nástroji konstruktor také připojí obslužné rutiny události k události<xref:Microsoft.Office.Interop.Outlook.InspectorEvents_Event.Close>objektu<xref:Microsoft.Office.Interop.Outlook.Inspector>a k události<xref:Microsoft.Office.Tools.CustomTaskPane.VisibleChanged>objektu<xref:Microsoft.Office.Tools.CustomTaskPane>.

     [!code-csharp[Trin_OutlookMailItemTaskPane#4](../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ThisAddIn.cs#4)]
     [!code-vb[Trin_OutlookMailItemTaskPane#4](../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ThisAddIn.vb#4)]

5. Po kódu, který jste přidali v předchozím kroku, přidejte následující metodu. Tato metoda je obslužná rutina události pro událost <xref:Microsoft.Office.Tools.CustomTaskPane.VisibleChanged> objektu <xref:Microsoft.Office.Tools.CustomTaskPane>, která je obsažena ve třídě `InspectorWrapper`. Tento kód aktualizuje stav přepínacího tlačítka vždy, když uživatel otevře nebo zavře vlastní podokno úloh.

     [!code-csharp[Trin_OutlookMailItemTaskPane#5](../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ThisAddIn.cs#5)]
     [!code-vb[Trin_OutlookMailItemTaskPane#5](../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ThisAddIn.vb#5)]

6. Po kódu, který jste přidali v předchozím kroku, přidejte následující metodu. Tato metoda je obslužná rutina události <xref:Microsoft.Office.Interop.Outlook.InspectorEvents_Event.Close> události <xref:Microsoft.Office.Interop.Outlook.Inspector> objektu, který obsahuje aktuální e-mailovou zprávu. Obslužná rutina události uvolní prostředky, když je e-mailová zpráva zavřena. Obslužná rutina události také odebere aktuální vlastní podokno úloh z kolekce `CustomTaskPanes`. To pomáhá zabránit více instancím vlastního podokna úloh při otevření další e-mailové zprávy.

     [!code-csharp[Trin_OutlookMailItemTaskPane#6](../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ThisAddIn.cs#6)]
     [!code-vb[Trin_OutlookMailItemTaskPane#6](../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ThisAddIn.vb#6)]

7. Po kódu, který jste přidali v předchozím kroku, přidejte následující kód. Později v tomto návodu budete volat tuto vlastnost z metody ve vlastním uživatelském rozhraní pásu karet pro zobrazení nebo skrytí vlastního podokna úloh.

     [!code-csharp[Trin_OutlookMailItemTaskPane#7](../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ThisAddIn.cs#7)]
     [!code-vb[Trin_OutlookMailItemTaskPane#7](../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ThisAddIn.vb#7)]

## <a name="initialize-and-clean-up-resources-used-by-the-add-in"></a>Inicializace a vyčištění prostředků používaných doplňkem
 Přidejte kód do třídy `ThisAddIn` k inicializaci doplňku VSTO po jeho načtení a k vyčištění prostředků používaných doplňkem VSTO při jeho uvolnění. Doplněk VSTO inicializujete nastavením obslužné rutiny události pro událost <xref:Microsoft.Office.Interop.Outlook.InspectorsEvents_Event.NewInspector> a předáním všech stávajících e-mailových zpráv do této obslužné rutiny události. Když je doplněk VSTO uvolněný, odpojte obslužnou rutinu události a vyčistěte objekty používané doplňkem VSTO.

### <a name="to-initialize-and-clean-up-resources-used-by-the-vsto-add-in"></a>Inicializace a vyčištění prostředků používaných doplňkem VSTO

1. V souboru *ThisAddIn.cs* nebo *ThisAddIn. vb* vyhledejte definici třídy `ThisAddIn`.

2. Do třídy `ThisAddIn` přidejte následující deklarace:

   - Pole `inspectorWrappersValue` obsahuje všechny objekty <xref:Microsoft.Office.Interop.Outlook.Inspector> a `InspectorWrapper`, které jsou spravovány doplňkem VSTO.

   - Pole `inspectors` udržuje odkaz na kolekci oken inspektorů v aktuální instanci Outlooku. Tento odkaz zabrání systému uvolňování paměti uvolnit paměť, která obsahuje obslužnou rutinu události <xref:Microsoft.Office.Interop.Outlook.InspectorsEvents_Event.NewInspector> události, kterou deklarujete v dalším kroku.

     [!code-csharp[Trin_OutlookMailItemTaskPane#8](../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ThisAddIn.cs#8)]
     [!code-vb[Trin_OutlookMailItemTaskPane#8](../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ThisAddIn.vb#8)]

3. Metodu `ThisAddIn_Startup` nahraďte následujícím kódem. Tento kód připojí obslužnou rutinu události k události <xref:Microsoft.Office.Interop.Outlook.InspectorsEvents_Event.NewInspector> a předá každý existující objekt <xref:Microsoft.Office.Interop.Outlook.Inspector> obslužné rutině události. Pokud uživatel načte doplněk VSTO po spuštění Outlooku, doplněk VSTO tyto informace použije k vytvoření vlastních podoken úloh pro všechny e-mailové zprávy, které jsou už otevřené.

    [!code-csharp[Trin_OutlookMailItemTaskPane#9](../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ThisAddIn.cs#9)]
    [!code-vb[Trin_OutlookMailItemTaskPane#9](../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ThisAddIn.vb#9)]

4. Metodu `ThisAddIn_ShutDown` nahraďte následujícím kódem. Tento kód odpojí obslužnou rutinu události <xref:Microsoft.Office.Interop.Outlook.InspectorsEvents_Event.NewInspector> a vyčistí objekty používané doplňkem VSTO.

    [!code-csharp[Trin_OutlookMailItemTaskPane#10](../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ThisAddIn.cs#10)]
    [!code-vb[Trin_OutlookMailItemTaskPane#10](../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ThisAddIn.vb#10)]

5. Do `ThisAddIn` třídy přidejte následující obslužnou rutinu události <xref:Microsoft.Office.Interop.Outlook.InspectorsEvents_Event.NewInspector>. Pokud nový <xref:Microsoft.Office.Interop.Outlook.Inspector> obsahuje e-mailovou zprávu, metoda vytvoří instanci nového objektu `InspectorWrapper` pro správu vztahu mezi e-mailovou zprávou a odpovídajícím podoknem úloh.

    [!code-csharp[Trin_OutlookMailItemTaskPane#11](../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ThisAddIn.cs#11)]
    [!code-vb[Trin_OutlookMailItemTaskPane#11](../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ThisAddIn.vb#11)]

6. Do třídy `ThisAddIn` přidejte následující vlastnost. Tato vlastnost zpřístupňuje soukromé `inspectorWrappersValue` pole kódu mimo `ThisAddIn` třídu.

    [!code-csharp[Trin_OutlookMailItemTaskPane#12](../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ThisAddIn.cs#12)]
    [!code-vb[Trin_OutlookMailItemTaskPane#12](../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ThisAddIn.vb#12)]

## <a name="checkpoint"></a>Kontrolní bod
 Sestavte projekt, aby se zajistilo, že zkompiluje bez chyb.

### <a name="to-build-your-project"></a>Sestavení projektu

1. V **Průzkumník řešení**klikněte pravým tlačítkem na projekt **OutlookMailItemTaskPane** a pak klikněte na **sestavit**. Ověřte, že se projekt zkompiluje bez chyb.

## <a name="synchronize-the-ribbon-toggle-button-with-the-custom-task-pane"></a>Synchronizace přepínacího tlačítka pásu karet s vlastním podoknem úloh
 Přepínací tlačítko se zobrazí, když je podokno úlohy zobrazené, a když je podokno úloh skryté, zobrazí se nestisknuté. Chcete-li synchronizovat stav tlačítka s vlastním podoknem úloh, upravte obslužnou rutinu události <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton.Click> přepínacího tlačítka.

### <a name="to-synchronize-the-custom-task-pane-with-the-toggle-button"></a>Synchronizace vlastního podokna úloh pomocí přepínacího tlačítka

1. V Návrháři pásu karet poklikejte na přepínací tlačítko **podokna zobrazit podokno úloh** .

     Visual Studio automaticky generuje obslužnou rutinu události s názvem `toggleButton1_Click`, která zpracovává událost <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton.Click> přepínacího tlačítka. Visual Studio také otevře soubor *ManageTaskPaneRibbon.cs* nebo *ManageTaskPaneRibbon. vb* v editoru kódu.

2. Přidejte následující příkazy do horní části souboru *ManageTaskPaneRibbon.cs* nebo *ManageTaskPaneRibbon. vb* .

     [!code-csharp[Trin_OutlookMailItemTaskPane#14](../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ManageTaskPaneRibbon.cs#14)]
     [!code-vb[Trin_OutlookMailItemTaskPane#14](../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ManageTaskPaneRibbon.vb#14)]

3. `toggleButton1_Click` obslužnou rutinu události nahraďte následujícím kódem. Když uživatel klikne na přepínací tlačítko, tato metoda skryje nebo zobrazí vlastní podokno úloh, které je spojeno s aktuálním oknem inspektoru.

     [!code-csharp[Trin_OutlookMailItemTaskPane#15](../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ManageTaskPaneRibbon.cs#15)]
     [!code-vb[Trin_OutlookMailItemTaskPane#15](../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ManageTaskPaneRibbon.vb#15)]

## <a name="test-the-project"></a>Testování projektu
 Po zahájení ladění projektu se otevře Outlook a načte se doplněk VSTO. Doplněk VSTO zobrazuje jedinečnou instanci vlastního podokna úloh s každou otevřenou e-mailovou zprávou. Vytvořením několika nových e-mailových zpráv otestujete kód.

### <a name="to-test-the-vsto-add-in"></a>Test doplňku VSTO

1. Stiskněte klávesu **F5**.

2. V Outlooku klikněte na **Nový** a vytvořte novou e-mailovou zprávu.

3. Na pásu karet e-mailové zprávy klikněte na kartu **Doplňky** a pak klikněte na tlačítko **Zobrazit podokno úloh** .

    Ověřte, že se v e-mailové zprávě zobrazuje podokno úloh s názvem **Moje podokno úloh** .

4. V podokně úloh zadejte do textového pole **první podokno úloh** .

5. Zavřete podokno úloh.

    Ověřte, že se stav tlačítka **Zobrazit podokno úloh** změní tak, aby se už nestiskl.

6. Znovu klikněte na tlačítko **Zobrazit podokno úloh** .

    Ověřte, zda se otevře podokno úloh a zda textové pole stále obsahuje **první podokno úloh**.

7. V Outlooku klikněte na **Nový** a vytvořte druhou e-mailovou zprávu.

8. Na pásu karet e-mailové zprávy klikněte na kartu **Doplňky** a pak klikněte na tlačítko **Zobrazit podokno úloh** .

    Ověřte, že se v e-mailové zprávě zobrazuje podokno úloh s názvem **Moje podokno úloh** a že je textové pole v tomto podokně úloh prázdné.

9. V podokně úloh zadejte do textového pole **druhý panel úloh** .

10. Změňte fokus na první e-mailovou zprávu.

     Ověřte, že podokno úloh, které je přidruženo k této e-mailové zprávě, stále zobrazuje **první podokno úloh** v textovém poli.

    Tento doplněk VSTO také zpracovává pokročilejší scénáře, které můžete vyzkoušet. Můžete například otestovat chování při zobrazení e-mailů pomocí tlačítek **Další položka** a **předchozí položka** . Můžete také otestovat chování při uvolnění doplňku VSTO, otevřít několik e-mailových zpráv a pak znovu načíst doplněk VSTO.

## <a name="next-steps"></a>Další kroky
 Další informace o tom, jak vytvořit vlastní podokna úloh, najdete v těchto tématech:

- Vytvoření vlastního podokna úloh v doplňku VSTO pro jinou aplikaci. Další informace o aplikacích, které podporují vlastní podokna úloh, najdete v tématu [vlastní podokna úloh](../vsto/custom-task-panes.md).

- Automatizujte systém Microsoft Office aplikaci pomocí vlastního podokna úloh. Další informace najdete v tématu [Návod: automatizace aplikace z vlastního podokna úloh](../vsto/walkthrough-automating-an-application-from-a-custom-task-pane.md).

- Vytvořte v Excelu tlačítko pás karet, které se dá použít k skrytí nebo zobrazení vlastního podokna úloh. Další informace najdete v tématu [Návod: Synchronizace vlastního podokna úloh pomocí tlačítka pásu karet](../vsto/walkthrough-synchronizing-a-custom-task-pane-with-a-ribbon-button.md).

## <a name="see-also"></a>Viz také:
- [Vlastní podokna úloh](../vsto/custom-task-panes.md)
- [Postupy: Přidání vlastního podokna úloh do aplikace](../vsto/how-to-add-a-custom-task-pane-to-an-application.md)
- [Návod: automatizace aplikace z vlastního podokna úloh](../vsto/walkthrough-automating-an-application-from-a-custom-task-pane.md)
- [Návod: Synchronizace vlastního podokna úloh s tlačítkem na pásu karet](../vsto/walkthrough-synchronizing-a-custom-task-pane-with-a-ribbon-button.md)
- [Přehled pásu karet](../vsto/ribbon-overview.md)
- [Přehled modelu objektů aplikace Outlook](../vsto/outlook-object-model-overview.md)
- [Přístup k pásu karet za běhu](../vsto/accessing-the-ribbon-at-run-time.md)
