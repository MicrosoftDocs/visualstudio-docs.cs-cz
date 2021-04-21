---
title: Vlastní podokna úloh
description: Přečtěte si, že vlastní podokna úloh poskytují způsob, jak vytvořit vlastní podokno úloh a poskytnout uživatelům známé rozhraní pro přístup k funkcím vašeho řešení.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, task panes
- user interface panels [Office development in Visual Studio]
- task panes [Office development in Visual Studio]
- user interfaces [Office development in Visual Studio], custom task panes
- custom task panes [Office development in Visual Studio], creating
- task panes [Office development in Visual Studio]. multiple application windows
- custom task panes [Office development in Visual Studio], multiple application windows
- task panes [Office development in Visual Studio], creating
- application-level add-ins [Office development in Visual Studio], custom task panes
- multiple applications windows with custom task panes [Office development in Visual Studio]
- add-ins [Office development in Visual Studio], custom task panes
- custom task panes [Office development in Visual Studio]
- task panes [Office development in Visual Studio], about custom task panes
- custom task panes [Office development in Visual Studio], about custom task panes
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 6c35d963b426fe24a43bef24617f79c042c272e9
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/21/2021
ms.locfileid: "107828160"
---
# <a name="custom-task-panes"></a>Vlastní podokna úloh
  Podokna úloh jsou panely uživatelského rozhraní, které jsou obvykle ukotveny na jednu stranu okna aplikace systém Microsoft Office. Vlastní podokna úloh poskytují způsob, jak vytvořit vlastní podokno úloh a poskytnout uživatelům známé rozhraní pro přístup k funkcím vašeho řešení. Rozhraní může například obsahovat ovládací prvky, které spouštějí kód pro úpravu dokumentů nebo zobrazení dat ze zdroje dat.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

> [!NOTE]
> Vlastní podokno úloh se liší od podokna akce. Podokno akce je součástí přizpůsobení na úrovni dokumentu pro systém Microsoft Office Word a systém Microsoft Office Excel. Další informace najdete v tématu [Přehled podokna akcí](../vsto/actions-pane-overview.md).

## <a name="benefits-of-custom-task-panes"></a>Výhody vlastních podoken úloh
 Vlastní podokna úloh umožňují integrovat funkce do známého uživatelského rozhraní. Vlastní podokno úloh můžete rychle vytvořit pomocí nástrojů sady Visual Studio.

### <a name="familiar-user-interface"></a>Známé uživatelské rozhraní
 Uživatelé aplikací v systému systém Microsoft Office jsou již obeznámeni s používáním podoken úloh, jako je podokno úloh **styly a formátování** ve Wordu. Vlastní podokna úloh se chovají stejně jako další podokna úloh v systému systém Microsoft Office. Uživatelé mohou ukotvit vlastní podokna úloh do různých stran okna aplikace nebo mohou přetahovat vlastní podokna úloh na libovolné místo v okně. Můžete vytvořit doplněk VSTO, který bude zobrazovat více vlastních podoken úloh najednou a uživatelé mohou řídit každé podokno úloh samostatně.

### <a name="windows-forms-support"></a>Podpora Windows Forms
 Uživatelské rozhraní vlastního podokna úloh, které vytvoříte pomocí vývojářských nástrojů pro Office v sadě Visual Studio, je založené na model Windows Forms ovládacích prvcích. Pro návrh uživatelského rozhraní pro vlastní podokno úloh můžete použít známý Návrhář formulářů. Podporu datových vazeb v model Windows Forms můžete použít také k vytvoření vazby zdroje dat k ovládacím prvkům v podokně úloh.

## <a name="create-a-custom-task-pane"></a>Vytvoření vlastního podokna úloh
 Základní vlastní podokno úloh můžete vytvořit ve dvou krocích:

1. Vytvořte uživatelské rozhraní pro vlastní podokno úloh přidáním model Windows Forms ovládacích prvků k <xref:System.Windows.Forms.UserControl> objektu.

2. Vytvořte instanci vlastního podokna úloh předáním uživatelského ovládacího prvku do <xref:Microsoft.Office.Tools.CustomTaskPaneCollection> objektu v doplňku VSTO. Tato kolekce vrátí nový <xref:Microsoft.Office.Tools.CustomTaskPane> objekt, který lze použít pro úpravu vzhledu podokna úloh a reakci na události uživatele.

   Další informace najdete v tématu [Postup: Přidání vlastního podokna úloh do aplikace](../vsto/how-to-add-a-custom-task-pane-to-an-application.md).

### <a name="create-the-user-interface"></a>Vytvoření uživatelského rozhraní
 Všechna vlastní podokna úloh, která jsou vytvořena pomocí vývojářských nástrojů pro Office v sadě Visual Studio, obsahují <xref:System.Windows.Forms.UserControl> objekt. Tento uživatelský ovládací prvek poskytuje uživatelské rozhraní vlastního podokna úloh. Uživatelský ovládací prvek lze vytvořit v době návrhu nebo v době běhu. Pokud vytvoříte uživatelský ovládací prvek v době návrhu, můžete pomocí Návrhář formulářů vytvořit uživatelské rozhraní podokna úloh.

### <a name="instantiate-the-custom-task-pane"></a>Vytvoření instance vlastního podokna úloh
 Po vytvoření uživatelského ovládacího prvku, který obsahuje uživatelské rozhraní vlastního podokna úloh, je nutné vytvořit instanci <xref:Microsoft.Office.Tools.CustomTaskPane> . Chcete-li to provést, předejte uživatelský ovládací prvek <xref:Microsoft.Office.Tools.CustomTaskPaneCollection> v doplňku VSTO voláním jedné z <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.Add%2A> metod. Tato kolekce je vystavena jako `CustomTaskPanes` pole `ThisAddIn` třídy. Následující příklad kódu je určen ke spuštění z `ThisAddIn` třídy.

 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_TaskPaneBasic/ThisAddIn.vb" id="Snippet2":::
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_TaskPaneBasic/ThisAddIn.cs" id="Snippet2":::

 <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.Add%2A>Metody vrací nový <xref:Microsoft.Office.Tools.CustomTaskPane> objekt. Pomocí tohoto objektu můžete změnit vzhled podokna úloh a reagovat na události uživatele.

### <a name="control-the-task-pane-in-multiple-windows"></a>Řízení podokna úloh ve více oknech
 Vlastní podokna úloh jsou přidružena k oknu rámce dokumentu, který prezentuje zobrazení dokumentu nebo položky uživateli. Podokno úloh je viditelné pouze v případě, že je přidružené okno viditelné.

 Chcete-li zjistit, které okno zobrazuje vlastní podokno úloh, použijte <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.Add%2A> při vytváření podokna úloh příslušné přetížení metody:

- Chcete-li přidružit podokno úloh k aktivnímu oknu, použijte <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.Add%2A> metodu.

- Chcete-li přidružit podokno úloh k dokumentu, který je hostován zadaným oknem, použijte <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.Add%2A> metodu.

  Některé aplikace Office vyžadují explicitní pokyny k vytvoření nebo zobrazení podokna úloh, když je otevřeno více než jedno okno. To je důležité vzít v úvahu, kde se má vytvořit instance vlastního podokna úloh v kódu, aby se zajistilo, že se podokno úloh zobrazí s příslušnými dokumenty nebo položkami v aplikaci. Další informace najdete v tématu [Správa vlastních podoken úloh v oknech aplikací](#Managing).

## <a name="access-the-application-from-the-task-pane"></a>Přístup k aplikaci z podokna úloh
 Chcete-li aplikaci automatizovat z uživatelského ovládacího prvku, můžete přímo získat přístup k objektovému modelu pomocí `Globals.ThisAddIn.Application` ve svém kódu. Statická `Globals` Třída poskytuje přístup k `ThisAddIn` objektu. `Application`Pole tohoto objektu je vstupním bodem do objektového modelu aplikace.

 Další informace o `Application` poli `ThisAddIn` objektu najdete v tématu [doplňky VSTO programu](../vsto/programming-vsto-add-ins.md). Návod, který ukazuje automatizaci aplikace z vlastního podokna úloh, naleznete v tématu [Návod: automatické použití aplikace z vlastního podokna úloh](../vsto/walkthrough-automating-an-application-from-a-custom-task-pane.md). Další informace o `Globals` třídě naleznete v tématu [globální přístup k objektům v projektech systému Office](../vsto/global-access-to-objects-in-office-projects.md).

## <a name="manage-the-user-interface-of-the-task-pane"></a>Správa uživatelského rozhraní podokna úloh
 Po vytvoření podokna úloh lze pomocí vlastností a událostí <xref:Microsoft.Office.Tools.CustomTaskPane> objektu řídit uživatelské rozhraní podokna úloh a reagovat na to, kdy uživatel změní podokno úloh.

### <a name="make-the-custom-task-pane-visible"></a>Nastavit vlastní podokno úloh jako viditelné
 Ve výchozím nastavení není podokno úloh viditelné. Aby bylo podokno úloh viditelné, je nutné nastavit <xref:Microsoft.Office.Tools.CustomTaskPane.Visible%2A> vlastnost na **hodnotu true**.

 Uživatelé můžou podokno úloh kdykoli zavřít kliknutím na tlačítko **Zavřít** (X) v horní části podokna úloh. Neexistuje však žádný výchozí způsob, jak uživatelům znovu otevřít vlastní podokno úloh. Pokud uživatel zavře vlastní podokno úloh, nemůže tento uživatel znovu zobrazit vlastní podokno úloh, pokud neposkytnete způsob, jak ho zobrazit.

 Pokud vytvoříte vlastní podokno úloh v doplňku VSTO, měli byste také vytvořit prvek uživatelského rozhraní, jako je třeba tlačítko, na které může uživatel kliknout a zobrazit nebo skrýt vlastní podokno úloh. Pokud vytvoříte vlastní podokno úloh v aplikaci systém Microsoft Office, která podporuje přizpůsobení pásu karet, můžete přidat skupinu ovládacích prvků na pás karet pomocí tlačítka, které zobrazí nebo skryje vlastní podokno úloh. Návod, který ukazuje, jak to provést, najdete v tématu [Návod: Synchronizace vlastního podokna úloh pomocí tlačítka pásu karet](../vsto/walkthrough-synchronizing-a-custom-task-pane-with-a-ribbon-button.md).

 Pokud vytvoříte vlastní podokno úloh v aplikaci systém Microsoft Office, která nepodporuje přizpůsobení pásu karet, můžete přidat a <xref:Microsoft.Office.Core.CommandBarButton> Zobrazit nebo skrýt vlastní podokno úloh.

### <a name="modify-the-appearance-of-the-task-pane"></a>Úprava vzhledu podokna úloh
 Velikost a umístění vlastního podokna úloh lze řídit pomocí vlastností <xref:Microsoft.Office.Tools.CustomTaskPane> objektu. Pomocí vlastností <xref:System.Windows.Forms.UserControl> objektu, který je obsažený v podokně vlastní úlohy, můžete v zobrazení vlastního podokna úloh provést mnoho dalších změn. Například můžete určit obrázek pozadí pro vlastní podokno úloh pomocí <xref:System.Windows.Forms.Control.BackgroundImage%2A> vlastnosti uživatelského ovládacího prvku.

 V následující tabulce jsou uvedeny změny, které můžete provést ve vlastním podokně úloh pomocí <xref:Microsoft.Office.Tools.CustomTaskPane> vlastností.

|Úkol|Vlastnost|
|----------|--------------|
|Změna velikosti podokna úloh|<xref:Microsoft.Office.Tools.CustomTaskPane.Height%2A><br /><br /> <xref:Microsoft.Office.Tools.CustomTaskPane.Width%2A>|
|Změna umístění podokna úloh|<xref:Microsoft.Office.Tools.CustomTaskPane.DockPosition%2A>|
|Skrytí podokna úloh nebo jeho viditelnost|<xref:Microsoft.Office.Tools.CustomTaskPane.Visible%2A>|
|Zabránění uživateli ve změně umístění podokna úloh|<xref:Microsoft.Office.Tools.CustomTaskPane.DockPositionRestrict%2A>|

### <a name="program-custom-task-pane-events"></a>Události vlastního podokna úloh programu
 Můžete chtít, aby doplněk VSTO reagoval v případě, že uživatel změní vlastní podokno úloh. Například pokud uživatel změní orientaci podokna ze svislé na vodorovný, může být vhodné změnit umístění ovládacích prvků.

 V následující tabulce jsou uvedeny události, které můžete zpracovat a reagovat tak na změny provedené uživatelem v podokně vlastní podokno úloh.

|Úkol|Událost|
|----------|-----------|
|Chcete-li reagovat, když uživatel změní umístění podokna úloh.|<xref:Microsoft.Office.Tools.CustomTaskPane.DockPositionChanged>|
|Chcete-li reagovat, když uživatel skryje podokno úloh nebo je bude viditelný.|<xref:Microsoft.Office.Tools.CustomTaskPane.VisibleChanged>|

## <a name="clean-up-resources-used-by-the-task-pane"></a>Vyčištění prostředků používaných podoknem úloh
 Když vytvoříte vlastní podokno úloh, <xref:Microsoft.Office.Tools.CustomTaskPane> objekt zůstane v paměti, dokud bude doplněk VSTO spuštěný. Objekt zůstane v paměti, i když uživatel klikne na tlačítko **Zavřít** (X) v rohu podokna úloh.

 Pokud chcete vyčistit prostředky používané v podokně úloh, když je ještě spuštěný doplněk VSTO, použijte <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.Remove%2A> <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.RemoveAt%2A> metody nebo. Tyto metody odstraňují zadaný <xref:Microsoft.Office.Tools.CustomTaskPane> objekt z `CustomTaskPanes` kolekce a volají `Dispose` metodu objektu.

 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]Při uvolnění doplňku VSTO se automaticky vyčistí prostředky používané vlastním podoknem úloh. Nevolejte <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.Remove%2A> <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.RemoveAt%2A> metody nebo v `ThisAddIn_Shutdown` obslužné rutině události v projektu. Tyto metody vyvolávají výjimku <xref:System.ObjectDisposedException> , protože [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] vyčistí prostředky využívané <xref:Microsoft.Office.Tools.CustomTaskPane> objektem před `ThisAddIn_Shutdown` voláním. Další informace o najdete v `ThisAddIn_Shutdown` tématu [události v projektech Office](../vsto/events-in-office-projects.md).

## <a name="manage-custom-task-panes-in-multiple-application-windows"></a><a name="Managing"></a> Správa vlastních podoken úloh v několika oknech aplikací
 Když vytvoříte vlastní podokno úloh v aplikaci, která používá více oken k zobrazení dokumentů a dalších položek, je nutné provést další kroky, aby se zajistilo, že se podokno úloh zobrazí, pokud uživatel očekává, že je.

 Vlastní podokna úloh ve všech aplikacích jsou přidružena k oknu rámce dokumentu, který prezentuje zobrazení dokumentu nebo položky uživateli. Podokno úloh je viditelné pouze v případě, že je přidružené okno viditelné. Ale ne všechny aplikace používají okna snímků dokumentu stejným způsobem.

 Následující skupiny aplikací mají různé požadavky na vývoj:

- [Outlook](#Outlook)

- [Word, InfoPath a PowerPoint](#WordAndInfoPath)

## <a name="outlook"></a><a name="Outlook"></a> APL
 Když vytvoříte vlastní podokno úloh pro Outlook, vlastní podokno úloh je přidruženo k určitému Průzkumníku nebo oknu inspektora. V Průzkumníkovi jsou okna, která zobrazují obsah složky a Kontrolori jsou okna, která zobrazují položku, jako je například e-mailová zpráva nebo úloha.

 Chcete-li zobrazit vlastní podokno úloh s více okny Průzkumníka nebo nástroje Inspector, je nutné vytvořit novou instanci vlastního podokna úloh při otevření okna Průzkumník nebo inspektor. Chcete-li to provést, zpracujte událost, která je vyvolána při vytvoření Průzkumníka nebo okna inspektora, a pak vytvořte podokno úloh v obslužné rutině události. Můžete také zpracovávat události Průzkumníka a kontrolora pro skrytí nebo zobrazení podokna úloh v závislosti na tom, které okno je viditelné.

 Chcete-li přidružit podokno úloh k určitému Průzkumníku nebo nástroji Inspector, použijte <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.Add%2A> k vytvoření podokna úloh metodu a předejte <xref:Microsoft.Office.Interop.Outlook.Explorer> <xref:Microsoft.Office.Interop.Outlook.Inspector> objekt nebo do parametru *okna* . Další informace o vytváření vlastních podoken úloh najdete v tématu [Přehled vlastních](../vsto/custom-task-panes.md)podoken úloh.

- <xref:Microsoft.Office.Interop.Outlook.ExplorersEvents_Event.NewExplorer>

- <xref:Microsoft.Office.Interop.Outlook.ExplorerEvents_10_Event.Activate>

- <xref:Microsoft.Office.Interop.Outlook.ExplorerEvents_10_Event.Close>

- <xref:Microsoft.Office.Interop.Outlook.ExplorerEvents_10_Event.Deactivate>

  Chcete-li monitorovat stav oken inspektoru, můžete zpracovat následující události týkající se kontroly:

- <xref:Microsoft.Office.Interop.Outlook.InspectorsEvents_Event.NewInspector>

- <xref:Microsoft.Office.Interop.Outlook.InspectorEvents_10_Event.Activate>

- <xref:Microsoft.Office.Interop.Outlook.InspectorEvents_10_Event.Close>

- <xref:Microsoft.Office.Interop.Outlook.InspectorEvents_10_Event.Deactivate>

### <a name="prevent-multiple-instances-of-a-custom-task-pane-in-outlook"></a>Zabránit více instancím vlastního podokna úloh v aplikaci Outlook
 Chcete-li zabránit oknu aplikace Outlook v zobrazení více instancí vlastního podokna úloh, je nutné explicitně odebrat vlastní podokno úloh z `CustomTaskPanes` kolekce `ThisAddIn` třídy, pokud je každé okno zavřeno. Volejte <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.Remove%2A> metodu v události, která je vyvolána při zavření okna, například <xref:Microsoft.Office.Interop.Outlook.ExplorerEvents_10_Event.Close> nebo <xref:Microsoft.Office.Interop.Outlook.InspectorEvents_10_Event.Close> .

 Pokud vlastní podokno úloh explicitně neodeberete, zobrazí se v systému Outlook okna více instancí vlastního podokna úloh. Outlook občas recykluje okna a cyklická okna uchovávají odkazy na všechna vlastní podokna úloh, která jsou k nim připojena.

## <a name="word-infopath-and-powerpoint"></a><a name="WordAndInfoPath"></a> Word, InfoPath a PowerPoint
 Word, InfoPath a PowerPoint zobrazí každý dokument v jiném okně s rámcem dokumentu. Při vytváření vlastního podokna úloh pro tyto aplikace je vlastní podokno úloh přidruženo pouze k určitému dokumentu. Pokud uživatel otevře jiný dokument, vlastní podokno úloh je skryté, dokud nebude znovu viditelný předchozí dokument.

 Pokud chcete zobrazit vlastní podokno úloh s více dokumenty, vytvořte novou instanci vlastního podokna úloh, když uživatel vytvoří nový dokument nebo otevře existující dokument. Chcete-li to provést, zpracujte události, které jsou vyvolány při vytvoření nebo otevření dokumentu, a poté vytvořte podokno úloh v obslužných rutinách událostí. Můžete také zpracovat události dokumentu pro skrytí nebo zobrazení podokna úloh v závislosti na tom, který dokument je viditelný.

 Chcete-li přidružit podokno úloh k určitému oknu dokumentu, použijte <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.Add%2A> metodu k vytvoření podokna úloh a předejte <xref:Microsoft.Office.Interop.Word.Window> (pro Word),  <xref:Microsoft.Office.Interop.InfoPath.WindowObject> (pro aplikaci InfoPath) nebo [DocumentWindow](/previous-versions/office/developer/office-2010/ff762047(v=office.14)) (pro PowerPoint) do parametru *okna* .

### <a name="word-events"></a>Události aplikace Word
 Chcete-li monitorovat stav oken dokumentů ve Wordu, můžete zpracovat následující události:

- <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeClose>

- <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentOpen>

- <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.NewDocument>

- <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.WindowActivate>

- <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.WindowDeactivate>

### <a name="infopath-events"></a>Události aplikace InfoPath
 Chcete-li monitorovat stav oken dokumentů v aplikaci InfoPath, můžete zpracovat následující události:

- <xref:Microsoft.Office.Interop.InfoPath._ApplicationEvents_Event.NewXDocument>

- <xref:Microsoft.Office.Interop.InfoPath._ApplicationEvents_Event.WindowActivate>

- <xref:Microsoft.Office.Interop.InfoPath._ApplicationEvents_Event.WindowDeactivate>

- <xref:Microsoft.Office.Interop.InfoPath._ApplicationEvents_Event.XDocumentBeforeClose>

- <xref:Microsoft.Office.Interop.InfoPath._ApplicationEvents_Event.XDocumentOpen>

### <a name="powerpoint-events"></a>Události aplikace PowerPoint
 Chcete-li monitorovat stav oken dokumentů v aplikaci PowerPoint, můžete zpracovat následující události:

- [Microsoft.Office.Interop.PowerPoint.EApplication_Event. AfterNewPresentation](/previous-versions/office/developer/office-2010/ff761105(v%3doffice.14))

- [Microsoft.Office.Interop.PowerPoint.EApplication_Event. AfterPresentationOpen](/previous-versions/office/developer/office-2010/ff762843(v%3doffice.14))

- [Microsoft.Office.Interop.PowerPoint.EApplication_Event. NewPresentation](/previous-versions/office/developer/office-2010/ff761498(v%3doffice.14))

- [Microsoft.Office.Interop.PowerPoint.EApplication_Event. PresentationOpen](/previous-versions/office/developer/office-2010/ff760423(v=office.14))

- [Microsoft.Office.Interop.PowerPoint.EApplication_Event. WindowActivate](/previous-versions/office/developer/office-2010/ff761153(v=office.14))

- [Microsoft.Office.Interop.PowerPoint.EApplication_Event. WindowDeactivate](/previous-versions/office/developer/office-2010/ff763093(v=office.14))

## <a name="see-also"></a>Viz také
- [Postupy: Přidání vlastního podokna úloh do aplikace](../vsto/how-to-add-a-custom-task-pane-to-an-application.md)
- [Návod: automatizace aplikace z vlastního podokna úloh](../vsto/walkthrough-automating-an-application-from-a-custom-task-pane.md)
- [Návod: Synchronizace vlastního podokna úloh s tlačítkem na pásu karet](../vsto/walkthrough-synchronizing-a-custom-task-pane-with-a-ribbon-button.md)
- [Návod: zobrazení vlastních podoken úloh s e-mailovými zprávami v aplikaci Outlook](../vsto/walkthrough-displaying-custom-task-panes-with-e-mail-messages-in-outlook.md)
