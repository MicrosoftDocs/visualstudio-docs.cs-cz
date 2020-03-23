---
title: Program Doplňků VSTO
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VST.ProjectItem.Addin
- VST.ProjectItem.AddinProject
- thisAddIn
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ICustomTaskPaneConsumer interface
- add-ins [Office development in Visual Studio], programming
- IRibbonExtensibility interface
- UI customizing [Office development in Visual Studio]
- Office applications [Office development in Visual Studio], application-level add-ins
- programming [Office development in Visual Studio], application-level add-ins
- ThisAddIn class
- user interfaces [Office development in Visual Studio], customizing
- writing code for Office solutions
- host items [Office development in Visual Studio], AddIn
- application development [Office development in Visual Studio], application-level add-ins
- add-ins [Office development in Visual Studio], ThisAddIn class
- application-level add-ins [Office development in Visual Studio], ThisAddIn class
- FormRegionStartup interface
- ThisAddIn_Startup
- application-level add-ins [Office development in Visual Studio], programming
- ThisAddIn_Shutdown
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 93470ebcea306d3cea762d60e061994b2bf27cc8
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/13/2020
ms.locfileid: "79301704"
---
# <a name="program-vsto-add-ins"></a>Program Doplňků VSTO
  Při rozšíření aplikace sady Microsoft Office vytvořením doplňku VSTO napíšete kód přímo proti `ThisAddIn` třídě v projektu. Tuto třídu můžete použít k provádění úkolů, jako je například přístup k objektovému modelu hostitelské aplikace sady Microsoft Office, přizpůsobení uživatelského rozhraní (UI) aplikace a vystavení objektů v doplňku VSTO jiným řešením sady Office.

 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]

 Některé aspekty psaní kódu v projektech doplňku VSTO se liší od jiných typů projektů v sadě Visual Studio. Mnohé z těchto rozdílů jsou způsobeny způsobem, jakým jsou objektové modely sady Office vystaveny spravovanému kódu. Další informace naleznete [v tématu Zápis kódu v řešeních sady Office](../vsto/writing-code-in-office-solutions.md).

 Obecné informace o doplňcích VSTO a dalších typech řešení, které můžete vytvořit pomocí nástrojů pro vývoj office v sadě Visual Studio, naleznete v [tématu Přehled vývoje řešení sady Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md).

## <a name="use-the-thisaddin-class"></a>Použití třídy ThisAddIn
 Můžete začít psát kód doplňku VSTO `ThisAddIn` ve třídě. Visual Studio automaticky generuje tuto třídu v Souboru [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)]kódu *ThisAddIn.vb* (in ) nebo *ThisAddIn.cs* (v jazyce C#) v projektu doplňku VSTO. Automaticky [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] konkretizovat tuto třídu pro vás při načtení aplikace Sady Microsoft Office váš doplněk VSTO.

 Ve `ThisAddIn` třídě jsou dvě výchozí obslužné rutiny událostí. Chcete-li spustit kód při načtení doplňku VSTO, přidejte kód do obslužné rutiny `ThisAddIn_Startup` události. Chcete-li spustit kód těsně před uvolněním doplňku VSTO, přidejte kód do obslužné rutiny `ThisAddIn_Shutdown` události. Další informace o těchto obslužných rutinách událostí naleznete [v tématu Události v projektech sady Office](../vsto/events-in-office-projects.md).

> [!NOTE]
> V aplikaci Outlook `ThisAddIn_Shutdown` ve výchozím nastavení není obslužná rutina události vždy volána při uvolnění doplňku VSTO. Další informace naleznete [v tématu Události v projektech sady Office](../vsto/events-in-office-projects.md).

### <a name="access-the-object-model-of-the-host-application"></a>Přístup k objektovému modelu hostitelské aplikace
 Chcete-li získat přístup k objektovému modelu hostitelské aplikace, použijte `Application` pole třídy. `ThisAddIn` Toto pole vrátí objekt, který představuje aktuální instanci hostitelské aplikace. V následující tabulce je uveden typ `Application` vrácené hodnoty pro pole v každém projektu doplňku VSTO.

|Hostitelská aplikace|Typ vrácené hodnoty|
|----------------------|-----------------------|
|Microsoft Office Excel|<xref:Microsoft.Office.Interop.Excel.Application>|
|Microsoft Office InfoPath|<xref:Microsoft.Office.Interop.InfoPath.Application>|
|Microsoft Office Outlook|<xref:Microsoft.Office.Interop.Outlook.Application>|
|Microsoft Office PowerPoint|[Aplikace](/previous-versions/office/developer/office-2010/ff764034(v=office.14))|
|Microsoft Office Project|Microsoft.Office.Interop.MSProject.Application|
|Microsoft Office Visio|Aplikace Microsoft.Office.Interop.Visio.Application|
|Microsoft Office Word|<xref:Microsoft.Office.Interop.Word.Application>|

 Následující příklad kódu ukazuje, `Application` jak pomocí tohoto pole vytvořit nový sešit v doplňku VSTO pro aplikaci Microsoft Office Excel. Tento příklad je určen ke `ThisAddIn` spuštění z třídy.

```vb
Dim newWorkbook As Excel.Workbook = Me.Application.Workbooks.Add()
```

```csharp
Excel.Workbook newWorkbook = this.Application.Workbooks.Add(System.Type.Missing);
```

 Chcete-li provést totéž `ThisAddIn` mimo třídu, `Globals` použijte `ThisAddIn` objekt pro přístup ke třídě. Další informace o `Globals` objektu naleznete v [tématu Globální přístup k objektům v projektech sady Office](../vsto/global-access-to-objects-in-office-projects.md).

```vb
Dim newWorkbook As Excel.Workbook = Globals.ThisAddIn.Application.Workbooks.Add()
```

```csharp
Excel.Workbook newWorkbook = Globals.ThisAddIn.Application.Workbooks.Add(System.Type.Missing);
```

 Další informace o objektových modelech konkrétních aplikací sady Microsoft Office naleznete v následujících tématech:

- [Přehled objektového modelu aplikace Excel](../vsto/excel-object-model-overview.md)

- [Objektový model aplikace Word – přehled](../vsto/word-object-model-overview.md)

- [Přehled objektového modelu aplikace Outlook](../vsto/outlook-object-model-overview.md)

- [Řešení aplikace InfoPath](../vsto/infopath-solutions.md)

- [Řešení powerpointu](../vsto/powerpoint-solutions.md)

- [Projektová řešení](../vsto/project-solutions.md)

- [Přehled objektového modelu visiu](../vsto/visio-object-model-overview.md)

### <a name="access-a-document-when-the-office-application-starts"></a><a name="AccessingDocuments"></a>Přístup k dokumentu při spuštění aplikace Office
 Ne [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] všechny aplikace automaticky otevřou dokument při jejich [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] spuštění a žádná z aplikací neotevře dokument při jejich spuštění. Proto nepřidávejte kód do `ThisAdd-In_Startup` obslužné rutiny události, pokud kód vyžaduje, aby byl dokument otevřen. Místo toho přidejte tento kód k události, kterou aplikace Office vyvolá, když uživatel vytvoří nebo otevře dokument. Tímto způsobem můžete zaručit, že dokument je otevřen před kód provádí operace na něm.

 Následující příklad kódu funguje s dokumentem ve Wordu pouze v případě, že uživatel vytvoří dokument nebo otevře existující dokument.

 [!code-csharp[Trin_WordAddIn_Menus#3](../vsto/codesnippet/CSharp/trin_wordaddin_menus.cs/thisaddin.cs#3)]
 [!code-vb[Trin_WordAddIn_Menus#3](../vsto/codesnippet/VisualBasic/trin_wordaddin_menus.vb/thisaddin.vb#3)]

### <a name="thisaddin-members-to-use-for-other-tasks"></a>Členové ThisAddIn, které se mají používat pro jiné úkoly
 Následující tabulka popisuje další běžné úkoly a `ThisAddIn` ukazuje, kteří členové třídy, které můžete použít k provádění úkolů.

|Úkol|Člen k použití|
|----------|-------------------|
|Spusťte kód pro inicializaci doplňku VSTO při načtení doplňku VSTO.|Přidejte kód `ThisAddIn_Startup` do metody. Toto je výchozí obslužná rutina <xref:Microsoft.Office.Tools.AddInBase.Startup> události pro událost. Další informace naleznete [v tématu Události v projektech sady Office](../vsto/events-in-office-projects.md).|
|Spusťte kód pro vyčištění prostředků používaných doplňkem VSTO před uvolněním doplňku VSTO.|Přidejte kód `ThisAddIn_Shutdown` do metody. Toto je výchozí obslužná rutina <xref:Microsoft.Office.Tools.AddInBase.Shutdown> události pro událost. Další informace naleznete [v tématu Události v projektech sady Office](../vsto/events-in-office-projects.md). **Poznámka:**  V aplikaci Outlook `ThisAddIn_Startup` ve výchozím nastavení není obslužná rutina události vždy volána při uvolnění doplňku VSTO. Další informace naleznete [v tématu Události v projektech sady Office](../vsto/events-in-office-projects.md).|
|Zobrazení vlastního podokna úloh|Použijte `CustomTaskPanes` pole. Další informace naleznete v [tématu Vlastní podokna úloh](../vsto/custom-task-panes.md).|
|Zveřejňujte objekty v doplňku VSTO jiným řešením sady Microsoft Office.|Přepsat metodu. <xref:Microsoft.Office.Tools.AddInBase.RequestComAddInAutomationService%2A> Další informace naleznete [v tématu Volání kódu v doplňcích VSTO z jiných řešení sady Office](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md).|
|Přizpůsobte funkci v systému Microsoft Office implementací rozhraní rozšiřitelnosti.|Přepsat metodu <xref:Microsoft.Office.Tools.AddInBase.RequestService%2A> vrátit instanci třídy, která implementuje rozhraní. Další informace naleznete v [tématu Přizpůsobení funkcí uživatelského rozhraní pomocí rozhraní rozšiřitelnosti](../vsto/customizing-ui-features-by-using-extensibility-interfaces.md). **Poznámka:**  Chcete-li přizpůsobit uzonování pásu <xref:Microsoft.Office.Tools.AddInBase.CreateRibbonExtensibilityObject%2A> karet, můžete také přepsat metodu.|

### <a name="understand-the-design-of-the-thisaddin-class"></a>Principy návrhu třídy ThisAddIn
 V projektech, [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] <xref:Microsoft.Office.Tools.AddIn> které cílí na rozhraní , je rozhraní. Třída `ThisAddIn` je odvozena <xref:Microsoft.Office.Tools.AddInBase> od třídy. Tato základní třída přesměruje všechna volání na své <xref:Microsoft.Office.Tools.AddIn> členy [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]na vnitřní implementaci rozhraní v rozhraní .

 V projektech doplňku VSTO `ThisAddIn` pro aplikaci `Microsoft.Office.Tools.Outlook.OutlookAddIn` Outlook je třída odvozena od třídy v <xref:Microsoft.Office.Tools.Outlook.OutlookAddInBase> projektech, [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]které cílí na rozhraní .NET Framework 3.5, a z projektů, které cílí na rozhraní . Tyto základní třídy poskytují některé další funkce pro podporu oblastí formuláře. Další informace o oblastech formulářů naleznete v [tématu Vytvoření oblastí formulářů aplikace Outlook](../vsto/creating-outlook-form-regions.md).

## <a name="customize-the-user-interface-of-microsoft-office-applications"></a>Přizpůsobení uživatelského rozhraní aplikací sady Microsoft Office
 Pomocí doplňku VSTO můžete programově přizpůsobit rozhraní aplikací sady Microsoft Office. Pás karet můžete například přizpůsobit, zobrazit vlastní podokno úloh nebo vytvořit vlastní oblast formuláře v aplikaci Outlook. Další informace naleznete v [tématu Vlastní nastavení uživatelského rozhraní office](../vsto/office-ui-customization.md).

 Visual Studio poskytuje návrháře a třídy, které můžete použít k vytvoření vlastních podoken úloh, vlastního nastavení pásu karet a oblastí formulářů aplikace Outlook. Tyto návrháři a třídy pomáhají zjednodušit proces přizpůsobení těchto funkcí. Další informace naleznete [v tématech Vlastní podokna úloh](../vsto/custom-task-panes.md), Návrhář [pásu karet](../vsto/ribbon-designer.md)a Vytvoření oblastí [formulářů aplikace Outlook](../vsto/creating-outlook-form-regions.md).

 Pokud chcete přizpůsobit jednu z těchto funkcí způsobem, který není podporován třídami a návrháři, můžete také přizpůsobit tyto funkce implementací *rozhraní rozšiřitelnosti* v doplňku VSTO. Další informace naleznete v [tématu Přizpůsobení funkcí uživatelského rozhraní pomocí rozhraní rozšiřitelnosti](../vsto/customizing-ui-features-by-using-extensibility-interfaces.md).

 Kromě toho můžete upravit ui dokumentů aplikace Word a sešitů aplikace Excel generováním hostitelských položek, které rozšiřují chování dokumentů a sešitů. To umožňuje přidat spravované ovládací prvky do dokumentů a listů. Další informace naleznete [v tématu Rozšíření dokumentů aplikace Word a sešitů aplikace Excel v doplňcích VSTO za běhu](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).

## <a name="call-code-in-vsto-add-ins-from-other-solutions"></a>Kód volání v doplňcích VSTO z jiných řešení
 Objekty v doplňku VSTO můžete vystavit jiným řešením, včetně jiných řešení sady Office. To je užitečné, pokud doplněk VSTO poskytuje službu, kterou chcete povolit další řešení k použití. Máte-li například doplněk VSTO pro aplikaci Microsoft Office Excel, který provádí výpočty finančních dat z webové služby, mohou tyto výpočty provádět jiná řešení voláním doplňku Aplikace Excel VSTO za běhu.

 Další informace naleznete [v tématu Volání kódu v doplňcích VSTO z jiných řešení sady Office](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md).

## <a name="see-also"></a>Viz také
- [Vývoj řešení Office](../vsto/developing-office-solutions.md)
- [Rozšíření wordových dokumentů a excelových sešitů v doplňcích VSTO za běhu](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Kód volání v doplňcích VSTO z jiných řešení Office](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md)
- [Návod: Volání kódu v doplňku VSTO z vsto z VBA](../vsto/walkthrough-calling-code-in-a-vsto-add-in-from-vba.md)
- [Přizpůsobení funkcí uživatelského rozhraní pomocí rozhraní rozšiřitelnosti](../vsto/customizing-ui-features-by-using-extensibility-interfaces.md)
- [Postup: Vytvoření projektů Office v Sadě Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Architektura doplňků VSTO](../vsto/architecture-of-vsto-add-ins.md)
- [Psaní kódu v řešeních Office](../vsto/writing-code-in-office-solutions.md)
