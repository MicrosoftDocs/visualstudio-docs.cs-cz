---
title: 'Návod: Vytvoření vašeho prvního doplňku VSTO pro Outlook'
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
- Outlook [Office development in Visual Studio], creating your first project
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: fc0f2e7cc7dc40dc305f7860223b5d4acf19a573
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49950960"
---
# <a name="walkthrough-create-your-first-vsto-add-in-for-outlook"></a>Návod: Vytvoření vašeho prvního doplňku VSTO pro Outlook
  Tento návod ukazuje, jak k vytvoření doplňku VSTO pro aplikaci Microsoft Office Outlook. Funkce, které vytvoříte v tento druh řešení jsou k dispozici aplikace samostatně, bez ohledu na to, který je otevřený položky aplikace Outlook. Další informace najdete v tématu [přehled vývoje řešení pro Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md).  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
 Tento návod znázorňuje následující úlohy:  
  
- Vytvoření projektu doplňku VSTO v Outlooku pro aplikaci Outlook.  
  
- Psaní kódu, který používá model objektu aplikace Outlook přidat text do předmětu a textu z nového e-mailovou zprávu.  
  
- Vytváření a spouštění projektů a otestovat ho.  
  
- Čištění dokončený projekt tak, aby doplňku VSTO už nespouští automaticky na vašem vývojovém počítači.  
  
  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Požadavky  
 K dokončení tohoto návodu budete potřebovat následující komponenty:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Microsoft Outlook  
  
## <a name="create-the-project"></a>Vytvoření projektu  
  
### <a name="to-create-a-new-outlook-project-in-visual-studio"></a>Chcete-li vytvořit nový projekt aplikace Outlook v sadě Visual Studio  
  
1.  Spustit [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  Na **souboru** nabídky, přejděte k **nový**a potom klikněte na tlačítko **projektu**.  
  
3.  V podokně šablony rozbalte **Visual C#** nebo **jazyka Visual Basic**a potom rozbalte **Office/SharePoint**.  
  
4.  V rozbalených **Office/SharePoint** uzlu, vyberte **Office Add-ins** uzlu.  
  
5.  V seznamu šablon projektu vyberte projekt doplňku VSTO pro Outlook.  
  
6.  V **název** zadejte **FirstOutlookAddIn**.  
  
7.  Klikněte na tlačítko **OK**.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] vytvoří **FirstOutlookAddIn** projekt a otevře **ThisAddIn** souboru kódu v editoru.  
  
## <a name="write-code-that-adds-text-to-each-new-mail-message"></a>Napsat kód, který přidá text pro každou novou e-mailovou zprávu  
 V dalším kroku přidejte kód do soubor kódu ThisAddIn. Nový kód používá model objektu aplikace Outlook přidat text do každé nové e-mailovou zprávu. Ve výchozím nastavení obsahuje soubor kódu ThisAddIn následující generovaného kódu:  
  
-   Částečnou definici `ThisAddIn` třídy. Tato třída představuje vstupní bod pro kód a poskytuje přístup k modelu objektů aplikace Outlook. Další informace najdete v tématu [doplňků Program VSTO](../vsto/programming-vsto-add-ins.md). Zbývající část `ThisAddIn` třída je definována v souboru skryté kódu, který byste neměli měnit.  
  
-   `ThisAddIn_Startup` a `ThisAddIn_Shutdown` obslužných rutin událostí. Tyto obslužné rutiny událostí se volá, když aplikace Outlook načte a uvolní doplňku VSTO. Pomocí těchto obslužných rutin událostí k inicializaci doplňku VSTO, když je načten a chcete vyčistit prostředky využívané třídou doplňku VSTO, když je uvolněn. Další informace najdete v tématu [události v projektech pro systém Office](../vsto/events-in-office-projects.md).  
  
### <a name="to-add-text-to-the-subject-and-body-of-each-new-mail-message"></a>Chcete-li přidat text pro předmět a text každého nového e-mailovou zprávu  
  
1. V souboru kódu ThisAddIn deklarovat pole s názvem `inspectors` v `ThisAddIn` třídy. `inspectors` Pole udržuje odkaz na sadu windows Inspectoru v aktuální instanci aplikace Outlook. Tento odkaz zabraňuje systému uvolňování paměti v uvolňování paměti, která obsahuje obslužnou rutinu události pro <xref:Microsoft.Office.Interop.Outlook.InspectorsEvents_Event.NewInspector> událostí.  
  
    [!code-vb[Trin_OutlookAddInTutorial#1](../vsto/codesnippet/VisualBasic/Trin_OutlookAddInTutorial/ThisAddIn.vb#1)]
    [!code-csharp[Trin_OutlookAddInTutorial#1](../vsto/codesnippet/CSharp/Trin_OutlookAddInTutorial/ThisAddIn.cs#1)]  
  
2. Nahradit `ThisAddIn_Startup` metodu s následujícím kódem. Připojí obslužnou rutinu události pro tento kód <xref:Microsoft.Office.Interop.Outlook.InspectorsEvents_Event.NewInspector> událostí.  
  
    [!code-vb[Trin_OutlookAddInTutorial#2](../vsto/codesnippet/VisualBasic/Trin_OutlookAddInTutorial/ThisAddIn.vb#2)]
    [!code-csharp[Trin_OutlookAddInTutorial#2](../vsto/codesnippet/CSharp/Trin_OutlookAddInTutorial/ThisAddIn.cs#2)]  
  
3. V soubor kódu ThisAddIn, přidejte následující kód, který `ThisAddIn` třídy. Tento kód definuje obslužnou rutinu události pro <xref:Microsoft.Office.Interop.Outlook.InspectorsEvents_Event.NewInspector> událostí.  
  
    Když uživatel vytvoří novou e-mailovou zprávu, tato obslužná rutina události přidá text řádku předmětu a těla zprávy.  
  
    [!code-vb[Trin_OutlookAddInTutorial#3](../vsto/codesnippet/VisualBasic/Trin_OutlookAddInTutorial/ThisAddIn.vb#3)]
    [!code-csharp[Trin_OutlookAddInTutorial#3](../vsto/codesnippet/CSharp/Trin_OutlookAddInTutorial/ThisAddIn.cs#3)]  
  
   V předchozích příkladech kódu upravit každé nové e-mailovou zprávu, použijte následující objekty:  
  
-   `Application` Pole `ThisAddIn` třídy. `Application` Pole vrátí <xref:Microsoft.Office.Interop.Outlook.Application> objektu, který představuje aktuální instanci aplikace Outlook.  
  
-   `Inspector` Parametr obslužné rutiny události pro <xref:Microsoft.Office.Interop.Outlook.InspectorsEvents_Event.NewInspector> událostí. `Inspector` Parametr je <xref:Microsoft.Office.Interop.Outlook.Inspector> objektu, který představuje okně Inspektor novou e-mailovou zprávu. Další informace najdete v tématu [řešení pro aplikaci Outlook](../vsto/outlook-solutions.md).  
  
## <a name="test-the-project"></a>Testování projektu  
 Při sestavení a spuštění projektu, ověřte, že text se zobrazí v řádku předmětu a textu novou e-mailovou zprávu.  
  
### <a name="to-test-the-project"></a>Otestování projektu  
  
1.  Stisknutím klávesy **F5** sestavení a spuštění projektu.  
  
     Při sestavování projektu kód je zkompilován do sestavení, která je zahrnutá ve výstupní složce sestavení pro projekt. Visual Studio také vytvoří sadu položky registru, které umožňují Outlook zjišťovat a načíst doplněk VSTO, a nakonfiguruje nastavení zabezpečení na vývojovém počítači povolit doplňku VSTO pro spuštění. Další informace najdete v tématu [přehled procesu sestavení řešení Office](../vsto/walkthrough-creating-your-first-vsto-add-in-for-outlook.md).  
  
2.  V Outlooku vytvořte novou e-mailovou zprávu.  
  
3.  Ověřte, že následující text je přidán řádek předmětu a těla zprávy.  
  
     **Tento text byl přidán s použitím kódu.**  
  
4.  Zavřete aplikaci Outlook.  
  
## <a name="clean-up-the-project"></a>Vyčistěte projekt  
 Po dokončení vývoje projektu doplňku VSTO sestavení, položky registru a nastavení zabezpečení odeberte z vývojového počítače. V opačném případě doplňku VSTO se spustí při každém otevření aplikace Outlook na vývojovém počítači.  
  
### <a name="to-clean-up-your-project"></a>Chcete-li vyčistit projekt  
  
1.  V sadě Visual Studio na **sestavení** nabídky, klikněte na tlačítko **Vyčistit řešení**.  
  
## <a name="next-steps"></a>Další kroky  
 Teď, když jste vytvořili základní doplňku VSTO pro Outlook, můžete další informace o tom, jak vývoj doplňků VSTO z těchto témat:  
  
-   Obecné programovacích úloh, které můžete provést s použitím doplňků VSTO pro Outlook Další informace najdete v tématu [doplňků Program VSTO](../vsto/programming-vsto-add-ins.md).  
  
-   Použití objektového modelu aplikace Outlook. Další informace najdete v tématu [řešení pro aplikaci Outlook](../vsto/outlook-solutions.md).  
  
-   Přizpůsobení uživatelského rozhraní Outlooku například přidat vlastní kartu na pás karet nebo vytvořením vlastní vlastního podokna úloh. Další informace najdete v tématu [přizpůsobení uživatelského rozhraní Office](../vsto/office-ui-customization.md).  
  
-   Sestavování a ladění doplňků VSTO pro Outlook. Další informace najdete v tématu [řešení pro systém Office sestavení](../vsto/building-office-solutions.md).  
  
-   Nasazení doplňků VSTO pro Outlook. Další informace najdete v tématu [nasazení řešení Office](../vsto/deploying-an-office-solution.md).  
  
## <a name="see-also"></a>Viz také:  
 [Programování doplňků VSTO](../vsto/programming-vsto-add-ins.md)   
 [Řešení pro aplikaci Outlook](../vsto/outlook-solutions.md)   
 [Přizpůsobení uživatelského rozhraní systému Office](../vsto/office-ui-customization.md)   
 [Vytváření řešení pro systém Office](../vsto/building-office-solutions.md)   
 [Nasazení řešení Office](../vsto/deploying-an-office-solution.md)   
 [Přehled šablon projektů Office](../vsto/office-project-templates-overview.md)  
  
  