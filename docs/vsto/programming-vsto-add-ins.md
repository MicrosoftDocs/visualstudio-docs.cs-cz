---
title: Programové doplňky VSTO
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
ms.openlocfilehash: 240995eb744f8107503c108cbcdbbb8522748b79
ms.sourcegitcommit: 8c4dc60b665e7065a5231d6b61380731221d9fc5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/23/2020
ms.locfileid: "87115336"
---
# <a name="program-vsto-add-ins"></a>Programové doplňky VSTO
  Když rozšíříte systém Microsoft Office aplikaci vytvořením doplňku VSTO, napíšete kód přímo proti `ThisAddIn` třídě v projektu. Tuto třídu můžete použít k provádění úloh, jako je například přístup k objektovému modelu aplikace systém Microsoft Office hosta, přizpůsobení uživatelského rozhraní (UI) aplikace a vystavení objektů v doplňku VSTO do dalších řešení pro Office.

 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]

 Některé aspekty psaní kódu v projektech doplňku VSTO se liší od jiných typů projektů v aplikaci Visual Studio. Mnohé z těchto rozdílů způsobují způsob, jakým jsou modely objektů Office vystaveny spravovanému kódu. Další informace najdete v tématu [psaní kódu v řešeních pro systém Office](../vsto/writing-code-in-office-solutions.md).

 Obecné informace o doplňcích VSTO a dalších typech řešení, které můžete vytvořit pomocí nástrojů pro vývoj pro Office v sadě Visual Studio, najdete v tématu [Přehled vývoje řešení pro systém office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md).

## <a name="use-the-thisaddin-class"></a>Použití třídy ThisAddIn
 Do třídy můžete začít psát kód doplňku VSTO `ThisAddIn` . Visual Studio automaticky vygeneruje tuto třídu v souboru kódu *ThisAddIn. vb* (in [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] ) nebo *ThisAddIn.cs* (v jazyce C#) v projektu doplňku VSTO. [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]Automaticky vytvoří instanci této třídy, když systém Microsoft Office aplikace načte doplněk VSTO.

 Ve třídě existují dvě výchozí obslužné rutiny událostí `ThisAddIn` . Chcete-li spustit kód při načtení doplňku VSTO, přidejte kód do `ThisAddIn_Startup` obslužné rutiny události. Chcete-li spustit kód těsně před uvolněním doplňku VSTO, přidejte kód do `ThisAddIn_Shutdown` obslužné rutiny události. Další informace o těchto obslužných rutinách událostí najdete v tématu [události v projektech pro systém Office](../vsto/events-in-office-projects.md).

> [!NOTE]
> V aplikaci Outlook se ve výchozím nastavení `ThisAddIn_Shutdown` obslužná rutina události nevolá vždy, když je doplněk VSTO uvolněný. Další informace najdete v tématu [události v projektech Office](../vsto/events-in-office-projects.md).

### <a name="access-the-object-model-of-the-host-application"></a>Přístup k objektovému modelu aplikace hostitele
 Chcete-li získat přístup k objektovému modelu aplikace hostitele, použijte `Application` pole `ThisAddIn` třídy. Toto pole vrátí objekt, který představuje aktuální instanci hostitelské aplikace. V následující tabulce je uveden typ vrácené hodnoty pro `Application` pole v každém projektu doplňku VSTO.

|Hostitelská aplikace|Typ návratové hodnoty|
|----------------------|-----------------------|
|systém Microsoft Office Excel|<xref:Microsoft.Office.Interop.Excel.Application>|
|systém Microsoft Office InfoPath|<xref:Microsoft.Office.Interop.InfoPath.Application>|
|systém Microsoft Office Outlook|<xref:Microsoft.Office.Interop.Outlook.Application>|
|systém Microsoft Office PowerPointu|[Aplikace](/previous-versions/office/developer/office-2010/ff764034(v=office.14))|
|systém Microsoft Office projekt|Microsoft. Office. Interop. MSProject. Application|
|systém Microsoft Office Visio|Microsoft. Office. Interop. Visio. Application|
|systém Microsoft Office Word|<xref:Microsoft.Office.Interop.Word.Application>|

 Následující příklad kódu ukazuje, jak použít `Application` pole k vytvoření nového sešitu v doplňku VSTO pro systém Microsoft Office Excel. Tento příklad je určen ke spuštění z `ThisAddIn` třídy.

```vb
Dim newWorkbook As Excel.Workbook = Me.Application.Workbooks.Add()
```

```csharp
Excel.Workbook newWorkbook = this.Application.Workbooks.Add(System.Type.Missing);
```

 Chcete-li provést stejnou věc mimo `ThisAddIn` třídu, použijte `Globals` objekt pro přístup ke `ThisAddIn` třídě. Další informace o `Globals` objektu naleznete v tématu [globální přístup k objektům v projektech systému Office](../vsto/global-access-to-objects-in-office-projects.md).

```vb
Dim newWorkbook As Excel.Workbook = Globals.ThisAddIn.Application.Workbooks.Add()
```

```csharp
Excel.Workbook newWorkbook = Globals.ThisAddIn.Application.Workbooks.Add(System.Type.Missing);
```

 Další informace o objektových modelech konkrétních aplikací systém Microsoft Office naleznete v následujících tématech:

- [Přehled modelu objektů aplikace Excel](../vsto/excel-object-model-overview.md)

- [Přehled modelu objektů aplikace Word](../vsto/word-object-model-overview.md)

- [Přehled modelu objektů aplikace Outlook](../vsto/outlook-object-model-overview.md)

- [Řešení InfoPath](../vsto/infopath-solutions.md)

- [Řešení aplikace PowerPoint](../vsto/powerpoint-solutions.md)

- [Řešení projektu](../vsto/project-solutions.md)

- [Přehled modelu objektů aplikace Visio](../vsto/visio-object-model-overview.md)

### <a name="access-a-document-when-the-office-application-starts"></a><a name="AccessingDocuments"></a>Přístup k dokumentu při spuštění aplikace Office
 Ne všechny [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] aplikace automaticky otevřou dokument při jejich spuštění a žádná z [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] aplikací při jejich spuštění neotevřela dokument. Proto nepřidávejte kód do `ThisAdd-In_Startup` obslužné rutiny události, pokud kód vyžaduje otevření dokumentu. Místo toho přidejte tento kód do události, kterou aplikace Office vyvolá, když uživatel vytvoří nebo otevře dokument. Tímto způsobem můžete zaručit, že dokument je otevřen před tím, než kód provede operace.

 Následující příklad kódu funguje s dokumentem v aplikaci Word pouze v případě, že uživatel vytvoří dokument nebo otevře existující dokument.

 [!code-csharp[Trin_WordAddIn_Menus#3](../vsto/codesnippet/CSharp/trin_wordaddin_menus.cs/thisaddin.cs#3)]
 [!code-vb[Trin_WordAddIn_Menus#3](../vsto/codesnippet/VisualBasic/trin_wordaddin_menus.vb/thisaddin.vb#3)]

### <a name="thisaddin-members-to-use-for-other-tasks"></a>ThisAddIn členové, kteří se mají použít pro jiné úkoly
 Následující tabulka popisuje další běžné úlohy a ukazuje, které členy třídy můžete `ThisAddIn` použít k provádění úkolů.

|Úkol|Člen, který se má použít|
|----------|-------------------|
|Spusťte kód pro inicializaci doplňku VSTO při načtení doplňku VSTO.|Přidejte kód do `ThisAddIn_Startup` metody. Toto je výchozí obslužná rutina události pro <xref:Microsoft.Office.Tools.AddInBase.Startup> událost. Další informace najdete v tématu [události v projektech Office](../vsto/events-in-office-projects.md).|
|Spusťte kód pro vyčištění prostředků používaných doplňkem VSTO před uvolněním doplňku VSTO.|Přidejte kód do `ThisAddIn_Shutdown` metody. Toto je výchozí obslužná rutina události pro <xref:Microsoft.Office.Tools.AddInBase.Shutdown> událost. Další informace najdete v tématu [události v projektech Office](../vsto/events-in-office-projects.md). **Poznámka:**  V aplikaci Outlook se ve výchozím nastavení `ThisAddIn_Shutdown` obslužná rutina události nevolá vždy, když je doplněk VSTO uvolněný. Další informace najdete v tématu [události v projektech Office](../vsto/events-in-office-projects.md).|
|Zobrazí vlastní podokno úloh.|Použijte `CustomTaskPanes` pole. Další informace najdete v tématu [vlastní podokna úloh](../vsto/custom-task-panes.md).|
|Vystavte objekty v doplňku VSTO pro další systém Microsoft Office řešení.|Přepsat <xref:Microsoft.Office.Tools.AddInBase.RequestComAddInAutomationService%2A> metodu. Další informace najdete v tématu [kód volání v doplňcích VSTO z jiných řešení pro Office](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md).|
|Přizpůsobení funkce v systém Microsoft Office systému implementací rozhraní rozšiřitelnosti.|Přepsat <xref:Microsoft.Office.Tools.AddInBase.RequestService%2A> metodu pro vrácení instance třídy, která implementuje rozhraní. Další informace najdete v tématu [Přizpůsobení funkcí uživatelského rozhraní pomocí rozhraní rozšiřitelnosti](../vsto/customizing-ui-features-by-using-extensibility-interfaces.md). **Poznámka:**  Chcete-li přizpůsobit uživatelské rozhraní pásu karet, můžete také přepsat <xref:Microsoft.Office.Tools.AddInBase.CreateRibbonExtensibilityObject%2A> metodu.|

### <a name="understand-the-design-of-the-thisaddin-class"></a>Pochopení návrhu třídy ThisAddIn
 V projektech, které cílí na [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] , <xref:Microsoft.Office.Tools.AddIn> je rozhraní. `ThisAddIn`Třída je odvozena z <xref:Microsoft.Office.Tools.AddInBase> třídy. Tato základní třída přesměruje všechna volání do jejích členů na vnitřní implementaci <xref:Microsoft.Office.Tools.AddIn> rozhraní v [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] .

 V projektech doplňku VSTO pro Outlook je `ThisAddIn` Třída odvozena od `Microsoft.Office.Tools.Outlook.OutlookAddIn` třídy v projektech, které cílí na .NET Framework 3,5, a z <xref:Microsoft.Office.Tools.Outlook.OutlookAddInBase> v projektech, které cílí na [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] . Tyto základní třídy poskytují některé další funkce pro podporu oblastí formuláře. Další informace o oblastech formuláře najdete v tématu [vytvoření oblastí formuláře aplikace Outlook](../vsto/creating-outlook-form-regions.md).

## <a name="customize-the-user-interface-of-microsoft-office-applications"></a>Přizpůsobení uživatelského rozhraní aplikací systém Microsoft Office
 Můžete programově přizpůsobit uživatelské rozhraní systém Microsoft Office aplikací pomocí doplňku VSTO. Můžete například přizpůsobit pás karet, zobrazit vlastní podokno úloh nebo vytvořit vlastní oblast formuláře v aplikaci Outlook. Další informace najdete v tématu [přizpůsobení uživatelského rozhraní systému Office](../vsto/office-ui-customization.md).

 Visual Studio poskytuje návrháře a třídy, které lze použít k vytvoření vlastních podoken úloh, přizpůsobení pásu karet a oblastí formulářů aplikace Outlook. Tito návrháři a třídy usnadňují proces přizpůsobení těchto funkcí. Další informace najdete v tématech [vlastní podokna úloh](../vsto/custom-task-panes.md), [Návrhář pásu karet](../vsto/ribbon-designer.md)a [vytváření oblastí formulářů aplikace Outlook](../vsto/creating-outlook-form-regions.md).

 Pokud chcete přizpůsobit jednu z těchto funkcí způsobem, který není podporován třídami a návrháři, můžete tyto funkce také přizpůsobit implementací *rozhraní rozšiřitelnosti* v doplňku VSTO. Další informace najdete v tématu [Přizpůsobení funkcí uživatelského rozhraní pomocí rozhraní rozšiřitelnosti](../vsto/customizing-ui-features-by-using-extensibility-interfaces.md).

 Kromě toho můžete upravit uživatelské rozhraní dokumentů aplikace Word a sešitů aplikace Excel vygenerováním položek hostitele, které zvyšují chování dokumentů a sešitů. To umožňuje přidat spravované ovládací prvky do dokumentů a listů. Další informace najdete v tématu [rozšiřování dokumentů aplikace Word a sešitů aplikace Excel v doplňkech VSTO za běhu](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).

## <a name="call-code-in-vsto-add-ins-from-other-solutions"></a>Volání kódu v doplňcích VSTO z jiných řešení
 Objekty v doplňku VSTO můžete vystavit jiným řešením, včetně dalších řešení pro Office. To je užitečné v případě, že doplněk VSTO poskytuje službu, kterou chcete povolit pro používání jiných řešení. Pokud máte například doplněk VSTO pro systém Microsoft Office Excel, který provádí výpočty s finančními daty z webové služby, další řešení mohou provádět tyto výpočty voláním do doplňku Excel VSTO v době běhu.

 Další informace najdete v tématu [kód volání v doplňcích VSTO z jiných řešení pro Office](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md).

## <a name="see-also"></a>Viz také
- [Vývoj řešení pro systém Office](../vsto/developing-office-solutions.md)
- [Rozšiřování dokumentů aplikace Word a excelových sešitů v doplňcích VSTO za běhu](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Volání kódu v doplňcích VSTO z jiných řešení pro systém Office](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md)
- [Návod: volání kódu v doplňku VSTO z jazyka VBA](../vsto/walkthrough-calling-code-in-a-vsto-add-in-from-vba.md)
- [Přizpůsobení funkcí uživatelského rozhraní pomocí rozhraní rozšiřitelnosti](../vsto/customizing-ui-features-by-using-extensibility-interfaces.md)
- [Postupy: vytváření projektů Office v sadě Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Architektura doplňků VSTO](../vsto/architecture-of-vsto-add-ins.md)
- [Psaní kódu v řešeních pro systém Office](../vsto/writing-code-in-office-solutions.md)
