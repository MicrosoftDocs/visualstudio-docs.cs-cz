---
title: 'Návod: Vytvoření vašeho prvního doplňku VSTO pro Excel'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application-level add-ins [Office development in Visual Studio], creating your first project
- Office development in Visual Studio, creating your first project
- add-ins [Office development in Visual Studio], creating your first project
- Excel [Office development in Visual Studio], creating your first project
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 6a9b7540a42dbaf7b7079793158d33d761199720
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49949900"
---
# <a name="walkthrough-create-your-first-vsto-add-in-for-excel"></a>Návod: Vytvoření vašeho prvního doplňku VSTO pro Excel
  Tento úvodní návod ukazuje, jak vytvořit doplňkem úrovni aplikace pro Microsoft Office Excel. Funkce, které vytvoříte v tento druh řešení jsou k dispozici pro vlastní, bez ohledu na to, které jsou otevřené sešity aplikace.  
  
 [!INCLUDE[appliesto_xlallapp](../vsto/includes/appliesto-xlallapp-md.md)]  
  
 Tento návod znázorňuje následující úlohy:  
  
- Vytvoření projektu doplňku VSTO v Excelu pro aplikaci Excel.  
  
- Psaní kódu, který používá objektový model aplikace Excel se při uložení přidat text do sešitu.  
  
- Vytváření a spouštění projektů a otestovat ho.  
  
- Čištění dokončený projekt tak, aby doplňku VSTO už nespouští automaticky na vašem vývojovém počítači.  
  
  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Požadavky  
 K dokončení tohoto návodu budete potřebovat následující komponenty:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] nebo [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].  
  
## <a name="create-the-project"></a>Vytvoření projektu  
  
#### <a name="to-create-a-new-excel-vsto-add-in-project-in-visual-studio"></a>Chcete-li vytvořit nový projekt doplňku VSTO pro Excel v sadě Visual Studio  
  
1.  Spustit [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  Na **souboru** nabídky, přejděte k **nový**a potom klikněte na tlačítko **projektu**.  
  
3.  V podokně šablony rozbalte **Visual C#** nebo **jazyka Visual Basic**a potom rozbalte **Office/SharePoint**.  
  
4.  V rozbalených **Office/SharePoint** uzlu, vyberte **Office Add-ins** uzlu.  
  
5.  V seznamu šablon projektu vyberte **doplněk aplikace Excel 2010** nebo **doplněk Excelu 2013**.  
  
6.  V **název** zadejte **FirstExcelAddIn**.  
  
7.  Klikněte na tlačítko **OK**.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] vytvoří **FirstExcelAddIn** projekt a otevře soubor kódu ThisAddIn v editoru.  
  
## <a name="write-code-to-add-text-to-the-saved-workbook"></a>Napsání kódu pro přidání textu k sešitu uložený  
 V dalším kroku přidejte kód do soubor kódu ThisAddIn. Nový kód používá objektový model aplikace Excel k vložení často používaný text v prvním řádku v aktivním listu. V aktivním listu je list, který je otevřený, když uživatel uloží sešit. Ve výchozím nastavení obsahuje soubor kódu ThisAddIn následující generovaného kódu:  
  
-   Částečnou definici `ThisAddIn` třídy. Tato třída představuje vstupní bod pro kód a poskytuje přístup k objektovému modelu Excelu. Další informace najdete v tématu [doplňků Program VSTO](../vsto/programming-vsto-add-ins.md). Zbývající část `ThisAddIn` třída je definována v souboru skryté kódu, který byste neměli měnit.  
  
-   `ThisAddIn_Startup` a `ThisAddIn_Shutdown` obslužných rutin událostí. Tyto obslužné rutiny událostí jsou volány při Excel načte a uvolní doplňku VSTO. Pomocí těchto obslužných rutin událostí k inicializaci doplňku VSTO, když je načten a chcete vyčistit prostředky využívané třídou váš doplněk, pokud je uvolněna. Další informace najdete v tématu [události v projektech pro systém Office](../vsto/events-in-office-projects.md).  
  
### <a name="to-add-a-line-of-text-to-the-saved-workbook"></a>Chcete-li přidat řádek textu uložené sešitu  
  
1. V soubor kódu ThisAddIn, přidejte následující kód, který `ThisAddIn` třídy. Definuje obslužnou rutinu události pro nový kód <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.WorkbookBeforeSave> událost, která se vyvolá, když je sešit uložený.  
  
    Když uživatel uloží sešit, přidá obslužnou rutinu události nového textu na začátku aktivního listu.  
  
    [!code-vb[Trin_ExcelAddInTutorial#1](../vsto/codesnippet/VisualBasic/Trin_ExcelAddInTutorial/ThisAddIn.vb#1)]
    [!code-csharp[Trin_ExcelAddInTutorial#1](../vsto/codesnippet/CSharp/Trin_ExcelAddInTutorial/ThisAddIn.cs#1)]  
  
2. Pokud používáte C#, přidejte následující kód vyžaduje k `ThisAddIn_Startup` obslužné rutiny události. Tento kód slouží k připojení `Application_WorkbookBeforeSave` obslužné rutině události <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.WorkbookBeforeSave> událostí.  
  
    [!code-csharp[Trin_ExcelAddInTutorial#2](../vsto/codesnippet/CSharp/Trin_ExcelAddInTutorial/ThisAddIn.cs#2)]  
  
   Chcete-li upravit sešit uložený, použijte v předchozích příkladech kódu následující objekty:  
  
-   `Application` Pole `ThisAddIn` třídy. `Application` Pole vrátí <xref:Microsoft.Office.Interop.Excel.Application> objektu, který představuje aktuální instanci aplikace Excel.  
  
-   `Wb` Parametr obslužné rutiny události pro <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.WorkbookBeforeSave> událostí. `Wb` Parametr je <xref:Microsoft.Office.Interop.Excel.Workbook> objektu, který představuje uložený sešitu. Další informace najdete v tématu [přehled modelu objektů aplikace Excel](../vsto/excel-object-model-overview.md).  
  
## <a name="test-the-project"></a>Testování projektu  
  
### <a name="to-test-the-project"></a>Otestování projektu  
  
1.  Stisknutím klávesy **F5** sestavení a spuštění projektu.  
  
     Při sestavování projektu kód je zkompilován do sestavení, která je zahrnutá ve výstupní složce sestavení pro projekt. Visual Studio také vytvoří sadu položky registru, které umožňují Excel zjišťovat a načíst doplněk VSTO, a nakonfiguruje nastavení zabezpečení na vývojovém počítači povolit doplňku VSTO pro spuštění. Další informace najdete v tématu [řešení pro systém Office sestavení](../vsto/building-office-solutions.md).  
  
2.  V Excelu uložte sešit.  
  
3.  Ověřte, že následující text je přidán do sešitu.  
  
     **Tento text byl přidán s použitím kódu.**  
  
4.  Zavřete aplikaci Excel.  
  
## <a name="clean-up-the-project"></a>Vyčistěte projekt  
 Po dokončení vývoje projektu doplňku VSTO sestavení, položky registru a nastavení zabezpečení odeberte z vývojového počítače. V opačném případě doplňku VSTO bude nadále spuštěna pokaždé, když otevřete aplikaci Excel na vašem vývojovém počítači.  
  
### <a name="to-clean-up-the-completed-project-on-your-development-computer"></a>Chcete-li vyčistit dokončený projekt na vašem vývojovém počítači  
  
1.  V sadě Visual Studio na **sestavení** nabídky, klikněte na tlačítko **Vyčistit řešení**.  
  
## <a name="next-steps"></a>Další kroky  
 Teď, když jste vytvořili základní doplňku VSTO pro Excel, můžete další informace o tom, jak vývoj doplňků VSTO z těchto témat:  
  
-   Obecné programování úkolů, které můžete provádět v doplňcích VSTO: [doplňků Program VSTO](../vsto/programming-vsto-add-ins.md).  
  
-   Úkoly programování, které jsou specifické pro doplňky VSTO pro Excel: [řešení pro Excel](../vsto/excel-solutions.md).  
  
-   Použití objektového modelu aplikace Excel: [přehled modelu objektů aplikace Excel](../vsto/excel-object-model-overview.md).  
  
-   Přizpůsobení uživatelského rozhraní (UI) aplikace Excel, například podle přidat vlastní kartu na pás karet nebo vytváření vlastních vlastního podokna úloh: [přizpůsobení uživatelského rozhraní Office](../vsto/office-ui-customization.md).  
  
-   Sestavování a ladění doplňků VSTO pro Excel: [řešení pro systém Office sestavení](../vsto/building-office-solutions.md).  
  
-   Nasazení doplňků VSTO pro Excel: [nasazení řešení Office](../vsto/deploying-an-office-solution.md).  
  
## <a name="see-also"></a>Viz také:  
 [Přehled vývoje řešení pro Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)   
 [Řešení pro aplikaci Excel](../vsto/excel-solutions.md)   
 [Programování doplňků VSTO](../vsto/programming-vsto-add-ins.md)   
 [Přehled modelu objektů aplikace Excel](../vsto/excel-object-model-overview.md)   
 [Přizpůsobení uživatelského rozhraní systému Office](../vsto/office-ui-customization.md)   
 [Vytváření řešení pro systém Office](../vsto/building-office-solutions.md)   
 [Nasazení řešení Office](../vsto/deploying-an-office-solution.md)   
 [Přehled šablon projektů Office](../vsto/office-project-templates-overview.md)  
  
  