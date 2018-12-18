---
title: Programování doplňků VSTO
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 522a3cbac565e217f0b6525fb6288f5b79908a78
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "35675900"
---
# <a name="program-vsto-add-ins"></a>Programování doplňků VSTO
  Při vytvoření doplňku VSTO můžete rozšířit aplikace Microsoft Office, můžete psát kód přímo `ThisAddIn` třídu ve vašem projektu. Tato třída slouží k provádění úloh, jako je například přístup k modelu objektu hostitelské aplikace Microsoft Office, přizpůsobení uživatelského rozhraní (UI) aplikace a zveřejnění objekty v doplňku VSTO pro ostatní řešení pro Office.  
  
 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]  
  
 Některé aspekty psaní kódu v doplňku VSTO projektů se liší od ostatních typů projektů v sadě Visual Studio. Mnohé z těchto rozdílů jsou způsobeny tím, jak Office objektové modely jsou přístupné pro spravovaný kód. Další informace najdete v tématu [psaní kódu v řešeních pro systém Office](../vsto/writing-code-in-office-solutions.md).  
  
 Obecné informace o doplňcích VSTO a jiné druhy řešení můžete vytvořit pomocí nástroje pro vývoj pro Office v sadě Visual Studio najdete v tématu [přehled vývoje řešení pro Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md).  
  
## <a name="use-the-thisaddin-class"></a>Použití thisaddin – třída  
 Můžete spustit zápis kódu doplňku VSTO `ThisAddIn` třídy. Automaticky generuje této třídy v sadě Visual Studio *ThisAddIn.vb* (v [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)]) nebo *ThisAddIn.cs* soubor v projektu doplňku VSTO kódu (v jazyce C#). [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] Automaticky vytvoří instanci této třídy za vás při načtení aplikace Microsoft Office doplňku VSTO.  
  
 Existují dva výchozích obslužných rutin událostí v `ThisAddIn` třídy. Pro spuštění kódu při načtení doplňku VSTO, přidejte kód pro `ThisAddIn_Startup` obslužné rutiny události. Pro spuštění kódu těsně před plánovaným doplňku VSTO uvolněna, přidejte kód pro `ThisAddIn_Shutdown` obslužné rutiny události. Další informace o těchto obslužných rutin událostí, naleznete v tématu [události v projektech pro systém Office](../vsto/events-in-office-projects.md).  
  
> [!NOTE]  
>  V Outlooku, ve výchozím nastavení `ThisAddIn_Shutdown` obslužná rutina události není vždy volá se, když doplňku VSTO je uvolněna. Další informace najdete v tématu [události v projektech pro systém Office](../vsto/events-in-office-projects.md).  
  
### <a name="access-the-object-model-of-the-host-application"></a>Přístup k modelu objektu hostitelské aplikace  
 Chcete-li získat přístup k modelu objektu hostitelské aplikace, použijte `Application` pole `ThisAddIn` třídy. Toto pole vrátí objekt, který představuje aktuální instanci aplikace hostitele. V následující tabulce jsou uvedeny typ vrácené hodnoty pro `Application` pole v každém projektu doplňku VSTO.  
  
|Hostitelské aplikace|Návratový typ hodnoty|  
|----------------------|-----------------------|  
|Aplikace Microsoft Office Excel|<xref:Microsoft.Office.Interop.Excel.Application>|  
|Aplikace Microsoft Office InfoPath|<xref:Microsoft.Office.Interop.InfoPath.Application>|  
|Aplikace Microsoft Office Outlook|<xref:Microsoft.Office.Interop.Outlook.Application>|  
|Aplikace Microsoft Office PowerPoint|<xref:Microsoft.Office.Interop.PowerPoint.Application>|  
|Aplikace Microsoft Office Project|Microsoft.Office.Interop.MSProject.Application|  
|Aplikace Microsoft Office Visio|Microsoft.Office.Interop.Visio.Application|  
|Aplikace Microsoft Office Word|<xref:Microsoft.Office.Interop.Word.Application>|  
  
 Následující příklad kódu ukazuje, jak používat `Application` pole, které chcete vytvořit nový sešit v doplňku VSTO pro aplikaci Microsoft Office Excel. Tento příklad je určen ke spuštění z `ThisAddIn` třídy.  
  
```vb  
Dim newWorkbook As Excel.Workbook = Me.Application.Workbooks.Add()  
```  
  
```csharp  
Excel.Workbook newWorkbook = this.Application.Workbooks.Add(System.Type.Missing);  
```  
  
 Chcete-li to samé udělá z mimo `ThisAddIn` třídy, použijte `Globals` objektu pro přístup k `ThisAddIn` třídy. Další informace o `Globals` objektu, najdete v článku [globální přístup k objektům v projektech Office](../vsto/global-access-to-objects-in-office-projects.md).  
  
```vb  
Dim newWorkbook As Excel.Workbook = Globals.ThisAddIn.Application.Workbooks.Add()  
```  
  
```csharp  
Excel.Workbook newWorkbook = Globals.ThisAddIn.Application.Workbooks.Add(System.Type.Missing);  
```  
  
 Další informace o objektové modely z konkrétní aplikace Microsoft Office naleznete v následujících tématech:  
  
-   [Přehled modelu objektů aplikace Excel](../vsto/excel-object-model-overview.md)  
  
-   [Přehled modelu objektů aplikace Word](../vsto/word-object-model-overview.md)  
  
-   [Přehled modelu objektů aplikace Outlook](../vsto/outlook-object-model-overview.md)  
  
-   [InfoPath – řešení](../vsto/infopath-solutions.md)  
  
-   [Řešení pro aplikaci PowerPoint](../vsto/powerpoint-solutions.md)  
  
-   [Projektová řešení](../vsto/project-solutions.md)  
  
-   [Přehled modelu objektů aplikace Visio](../vsto/visio-object-model-overview.md)  
  
###  <a name="AccessingDocuments"></a> Přístup k dokumentu, při spuštění aplikace Office  
 Ne všechny [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] aplikace automaticky otevře při spuštění je a žádný z dokumentu [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] aplikace otevřete dokument, když je spustíte. Proto nepřidávejte kód `ThisAdd-In_Startup` obslužná rutina události, pokud kód vyžaduje dokument otevřen. Místo toho přidejte tento kód na událost, která aplikace Office se vyvolá, když uživatel vytvoří nebo otevře dokument. Tímto způsobem můžete zajistit, že je před váš kód provádí operace v něm otevřený dokument.  
  
 Následující příklad kódu funguje s dokumentu ve Wordu, jenom když uživatel vytvoří dokument nebo otevře existující dokument.  
  
 [!code-csharp[Trin_WordAddIn_Menus#3](../vsto/codesnippet/CSharp/trin_wordaddin_menus.cs/thisaddin.cs#3)]
 [!code-vb[Trin_WordAddIn_Menus#3](../vsto/codesnippet/VisualBasic/trin_wordaddin_menus.vb/thisaddin.vb#3)]  
  
### <a name="thisaddin-members-to-use-for-other-tasks"></a>Členy třídy ThisAddIn používat pro jiné účely  
 Následující tabulka popisuje dalších běžných úkolů a ukazuje, kteří členové `ThisAddIn` třídy, které můžete použít k provádění úloh.  
  
|Úloha|Člen použití|  
|----------|-------------------|  
|Spusťte kód pro inicializaci doplňku VSTO při načtení doplňku VSTO.|Přidejte kód, který `ThisAddIn_Startup` metody. Toto je výchozí obslužnou rutinu <xref:Microsoft.Office.Tools.AddInBase.Startup> událostí. Další informace najdete v tématu [události v projektech pro systém Office](../vsto/events-in-office-projects.md).|  
|Spusťte kód pro vyčištění prostředků používali doplňku VSTO je uvolněna pomocí doplňku VSTO.|Přidejte kód, který `ThisAddIn_Shutdown` metody. Toto je výchozí obslužnou rutinu <xref:Microsoft.Office.Tools.AddInBase.Shutdown> událostí. Další informace najdete v tématu [události v projektech pro systém Office](../vsto/events-in-office-projects.md). **Poznámka:** v Outlooku, ve výchozím nastavení `ThisAddIn_Startup` obslužná rutina události není vždy volá se, když doplňku VSTO je uvolněna. Další informace najdete v tématu [události v projektech pro systém Office](../vsto/events-in-office-projects.md).|  
|Zobrazení vlastního podokna úloh.|Použití `CustomTaskPanes` pole. Další informace najdete v tématu [vlastní podokna úloh](../vsto/custom-task-panes.md).|  
|Vystavení objektů v doplňku VSTO pro ostatní řešení pro Microsoft Office.|Přepsat <xref:Microsoft.Office.Tools.AddInBase.RequestComAddInAutomationService%2A> metody. Další informace najdete v tématu [volání kódu v doplňcích VSTO z jiných řešení pro Office](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md).|  
|Přizpůsobení funkce v systému Microsoft Office pomocí implementace rozhraní rozšíření.|Přepsat <xref:Microsoft.Office.Tools.AddInBase.RequestService%2A> metoda vrátí instanci třídy, která implementuje rozhraní. Další informace najdete v tématu [funkcí přizpůsobení uživatelského rozhraní pomocí rozšiřujících rozhraní](../vsto/customizing-ui-features-by-using-extensibility-interfaces.md). **Poznámka:** přizpůsobit uživatelské rozhraní pásu karet, můžete také přepsat <xref:Microsoft.Office.Tools.AddInBase.CreateRibbonExtensibilityObject%2A> metody.|  
  
### <a name="understand-the-design-of-the-thisaddin-class"></a>Pochopení návrhu thisaddin – třída  
 V projektech, které se zaměřují [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)], <xref:Microsoft.Office.Tools.AddIn> je rozhraní. `ThisAddIn` Třída odvozena z <xref:Microsoft.Office.Tools.AddInBase> třídy. Tato základní třída všech volání jejích členů přesměruje na interní implementaci <xref:Microsoft.Office.Tools.AddIn> rozhraní v [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)].  
  
 V projekty doplňku VSTO pro Outlook `ThisAddIn` třída odvozena z `Microsoft.Office.Tools.Outlook.OutlookAddIn` tříd v projektech cílených rozhraní .NET Framework 3.5 a z <xref:Microsoft.Office.Tools.Outlook.OutlookAddInBase> v projektech, které se zaměřují [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]. Tyto základní třídy poskytují další funkce pro podporu oblastí formulářů. Další informace o oblasti formuláře, naleznete v tématu [oblastí formulářů aplikace Outlook vytvořit](../vsto/creating-outlook-form-regions.md).  
  
## <a name="customize-the-user-interface-of-microsoft-office-applications"></a>Přizpůsobení uživatelského rozhraní aplikace Microsoft Office  
 Aplikace Microsoft Office z uživatelského rozhraní lze přizpůsobit prostřednictvím kódu programu pomocí doplňku VSTO. Můžete například přizpůsobit pás karet, zobrazit vlastního podokna úloh nebo vytvořit vlastní formulář regionu v Outlooku. Další informace najdete v tématu [přizpůsobení uživatelského rozhraní Office](../vsto/office-ui-customization.md).  
  
 Visual Studio poskytuje návrháře a třídy, které můžete použít k vytvoření vlastních podoken úloh, vlastních nastavení pásu karet a oblastí formulářů aplikace Outlook. Tyto návrhářů a třídy pomoct zjednodušit proces přizpůsobení těchto funkcí. Další informace najdete v tématu [vlastní podokna úloh](../vsto/custom-task-panes.md), [Návrháře pásu karet](../vsto/ribbon-designer.md), a [oblastí formulářů aplikace Outlook vytvořit](../vsto/creating-outlook-form-regions.md).  
  
 Pokud chcete upravit některou z těchto funkcí způsobem, který nepodporuje třídy a návrháři, můžete také přizpůsobit tyto funkce pomocí implementace *rozšiřitelnost rozhraní* v doplňku VSTO. Další informace najdete v tématu [funkcí přizpůsobení uživatelského rozhraní pomocí rozšiřujících rozhraní](../vsto/customizing-ui-features-by-using-extensibility-interfaces.md).  
  
 Kromě toho můžete upravit dokumentů uživatelského rozhraní aplikace Word a sešitů aplikace Excel pomocí generování hostitelské položky, které rozšiřují chování dokumenty a sešity. To umožňuje přidat spravované ovládací prvky pro dokumenty a sešity. Další informace najdete v tématu [rozšíření Wordových dokumentů a Excelových sešitů v doplňcích VSTO za běhu](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
## <a name="call-code-in-vsto-add-ins-from-other-solutions"></a>Volání kódu v doplňcích VSTO z jiných řešení  
 V doplňku VSTO pro ostatní řešení, včetně jiných řešení pro Office můžete zveřejnit objekty. To je užitečné, pokud váš doplněk VSTO poskytuje službu, kterou chcete povolit použití jiných řešení. Například pokud máte doplňku VSTO pro Microsoft Office Excel, která provádí výpočty finančních dat z webové služby, jiná řešení provádět tyto výpočty pomocí volání do doplňku VSTO pro Excel v době běhu.  
  
 Další informace najdete v tématu [volání kódu v doplňcích VSTO z jiných řešení pro Office](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md).  
  
## <a name="see-also"></a>Viz také:  
 [Vývoj řešení pro systém Office](../vsto/developing-office-solutions.md)   
 [Rozšíření dokumentů aplikace Word a sešitů aplikace Excel v doplňcích VSTO za běhu](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Volání kódu v doplňcích VSTO z jiných řešení pro Office](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md)   
 [Návod: Volání kódu v doplňku VSTO z jazyka VBA](../vsto/walkthrough-calling-code-in-a-vsto-add-in-from-vba.md)   
 [Přizpůsobení funkcí uživatelského rozhraní pomocí rozšiřujících rozhraní](../vsto/customizing-ui-features-by-using-extensibility-interfaces.md)   
 [Postupy: vytváření projektů pro systém Office v sadě Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Architektura doplňků VSTO](../vsto/architecture-of-vsto-add-ins.md)   
 [Psaní kódu v řešeních pro systém Office](../vsto/writing-code-in-office-solutions.md)  
  
  