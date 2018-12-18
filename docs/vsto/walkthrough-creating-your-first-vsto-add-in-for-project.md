---
title: 'Návod: Vytvoření vašeho prvního doplňku VSTO pro Project'
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
- Project [Office development in Visual Studio], creating your first project
- add-ins [Office development in Visual Studio], creating your first project
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 7fb6ece309fb0c5e7c67abf039d2b27a9f04236d
ms.sourcegitcommit: be938c7ecd756a11c9de3e6019a490d0e52b4190
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50671414"
---
# <a name="walkthrough-create-your-first-vsto-add-in-for-project"></a>Návod: Vytvoření vašeho prvního doplňku VSTO pro Project
  Tento návod ukazuje, jak k vytvoření doplňku VSTO pro aplikaci Microsoft Office Project. Funkce, které vytvoříte v tento druh řešení jsou k dispozici pro vlastní projekty bez ohledu na to, které jsou otevřené aplikace. Další informace najdete v tématu [přehled vývoje řešení pro Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md).  
  
 [!INCLUDE[appliesto_projallapp](../vsto/includes/appliesto-projallapp-md.md)]  
  
 Tento návod znázorňuje následující úlohy:  
  
- Vytvoření projektu doplňku VSTO pro Project.  
  
- Psaní kódu, který používá model objektu projektu přidejte úkol do nového projektu.  
  
- Vytváření a spouštění projektů a otestovat ho.  
  
- Čištění dokončený projekt tak, aby doplňku VSTO už nespouští automaticky na vašem vývojovém počítači.  
  
  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Požadavky  
 K dokončení tohoto návodu budete potřebovat následující komponenty:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Project_15_short](../vsto/includes/project-15-short-md.md)] nebo [!INCLUDE[Project_14_short](../vsto/includes/project-14-short-md.md)].  
  
## <a name="create-the-project"></a>Vytvoření projektu  
  
### <a name="to-create-a-new-project-in-visual-studio"></a>Chcete-li vytvořit nový projekt v sadě Visual Studio  
  
1.  Spustit [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  Na **souboru** nabídky, přejděte k **nový**a potom klikněte na tlačítko **projektu**.  
  
3.  V podokně šablony rozbalte **Visual C#** nebo **jazyka Visual Basic**a potom rozbalte **Office/SharePoint**.  
  
4.  V rozbalených **Office/SharePoint** uzlu, vyberte **Office Add-ins** uzlu.  
  
5.  V seznamu šablon projektu vyberte **doplněk aplikace Project 2010** nebo **doplněk Project 2013**.  
  
6.  V **název** zadejte **FirstProjectAddIn**.  
  
7.  Klikněte na tlačítko **OK**.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] vytvoří **FirstProjectAddIn** projekt a otevře **ThisAddIn** souboru kódu v editoru.  
  
## <a name="write-code-that-adds-a-new-task-to-a-project"></a>Napsat kód, který přidá nový úkol do projektu  
 V dalším kroku přidejte kód do soubor kódu ThisAddIn. Nový kód používá model objektu projektu přidáte nový úkol do projektu. Ve výchozím nastavení obsahuje soubor kódu ThisAddIn následující generovaného kódu:  
  
-   Částečnou definici `ThisAddIn` třídy. Tato třída představuje vstupní bod pro kód a poskytuje přístup k objektovému modelu projektu. Další informace najdete v tématu [doplňků Program VSTO](../vsto/programming-vsto-add-ins.md). Zbývající část `ThisAddIn` třída je definována v souboru skryté kódu, který byste neměli měnit.  
  
-   `ThisAddIn_Startup` a `ThisAddIn_Shutdown` obslužných rutin událostí. Tyto obslužné rutiny událostí jsou volány při načtení projektu a uvolnění doplňku VSTO. Pomocí těchto obslužných rutin událostí k inicializaci doplňku VSTO, když je načten a chcete vyčistit prostředky využívané třídou doplňku VSTO, když je uvolněn. Další informace najdete v tématu [události v projektech pro systém Office](../vsto/events-in-office-projects.md).  
  
### <a name="to-add-a-task-to-a-new-project"></a>Přidejte úkol do nového projektu  
  
1. V soubor kódu ThisAddIn, přidejte následující kód, který `ThisAddIn` třídy. Tento kód definuje obslužnou rutinu události pro `NewProject` událost `Microsoft.Office.Interop.MSProject.Application` třídy.  
  
    Když uživatel vytvoří nový projekt, tato obslužná rutina události přidá úkol do projektu.  
  
    [!code-vb[Trin_ProjectAddInTutorial#1](../vsto/codesnippet/VisualBasic/Trin_ProjectAddInTutorial/ThisAddIn.vb#1)]
    [!code-csharp[Trin_ProjectAddInTutorial#1](../vsto/codesnippet/CSharp/Trin_ProjectAddInTutorial/ThisAddIn.cs#1)]  
  
   Chcete-li upravit projekt, tento příklad kódu používá následující objekty:  
  
-   `Application` Pole `ThisAddIn` třídy. `Application` Pole vrátí `Microsoft.Office.Interop.MSProject.Application` objektu, který představuje aktuální instanci aplikace Project.  
  
-   `pj` Parametr obslužné rutiny události pro událost NewProject. `pj` Parametr je `Microsoft.Office.Interop.MSProject.Project` objektu, který představuje projekt. Další informace najdete v tématu [projektů řešení](../vsto/project-solutions.md).  
  
1.  Pokud používáte C#, přidejte následující kód, který `ThisAddIn_Startup` obslužné rutiny události. Tento kód se připojí `Application_Newproject` obslužné rutiny události s NewProject událostí.  
  
     [!code-csharp[Trin_ProjectAddInTutorial#2](../vsto/codesnippet/CSharp/Trin_ProjectAddInTutorial/ThisAddIn.cs#2)]  
  
  
## <a name="test-the-project"></a>Testování projektu  
 Při sestavení a spuštění projektu, ověřte, že je nová úloha se zobrazí v výsledný nový projekt.  
  
### <a name="to-test-the-project"></a>Otestování projektu  
  
1.  Stisknutím klávesy **F5** sestavení a spuštění projektu. Aplikace Microsoft Project spustí a automaticky se otevře nový prázdný projekt.  
  
     Při sestavování projektu kód je zkompilován do sestavení, která je zahrnutá ve výstupní složce sestavení pro projekt. Visual Studio také vytvoří sadu položky registru, které umožňují projektu zjišťovat a načíst doplněk VSTO, a nakonfiguruje nastavení zabezpečení na vývojovém počítači povolit doplňku VSTO pro spuštění. Další informace najdete v tématu [přehled procesu sestavení řešení Office](/previous-versions/visualstudio/visual-studio-2010/h2c9cdc0(v=vs.100)).  
  
2.  Ověřte, že je do prázdného projektu přidán nový úkol.  
  
3.  Ověřte, že tento text se zobrazí v **název úkolu** pole úkolu.  
  
     **Tento text byl přidán s použitím kódu.**  
  
4.  Zavřete aplikaci Microsoft Project.  
  
## <a name="clean-up-the-project"></a>Vyčistěte projekt  
 Po dokončení vývoje projektu doplňku VSTO sestavení, položky registru a nastavení zabezpečení odeberte z vývojového počítače. V opačném případě doplňku VSTO se spustí pokaždé, když otevřete aplikaci Microsoft Project na vývojovém počítači.  
  
### <a name="to-clean-up-your-project"></a>Chcete-li vyčistit projekt  
  
1.  V sadě Visual Studio na **sestavení** nabídky, klikněte na tlačítko **Vyčistit řešení**.  
  
## <a name="next-steps"></a>Další kroky  
 Teď, když jste vytvořili základní doplňku VSTO pro Project, můžete další informace o tom, jak vývoj doplňků VSTO z těchto témat:  
  
-   Obecné programování úkolů, které můžete provádět v doplňcích VSTO pro Project: [doplňků Program VSTO](../vsto/programming-vsto-add-ins.md).  
  
-   Použití objektového modelu projektu: [projektů řešení](../vsto/project-solutions.md).  
  
-   Sestavování a ladění doplňků VSTO pro Project: [řešení pro systém Office sestavení](../vsto/building-office-solutions.md).  
  
-   Nasazení doplňků VSTO pro Project: [nasazení řešení Office](../vsto/deploying-an-office-solution.md).  
  
## <a name="see-also"></a>Viz také:  
 [Programování doplňků VSTO](../vsto/programming-vsto-add-ins.md)   
 [Projektová řešení](../vsto/project-solutions.md)   
 [Vytváření řešení pro systém Office](../vsto/building-office-solutions.md)   
 [Nasazení řešení Office](../vsto/deploying-an-office-solution.md)   
 [Přehled šablon projektů Office](../vsto/office-project-templates-overview.md)  
  
  