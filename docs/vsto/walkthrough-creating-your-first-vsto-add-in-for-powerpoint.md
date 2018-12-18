---
title: 'Návod: Vytvoření vašeho prvního doplňku VSTO pro PowerPoint'
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
- PowerPoint [Office development in Visual Studio], creating your first project
- add-ins [Office development in Visual Studio], creating your first project
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: cea6e61a1afd734ca0ae52a704a2d881371f5817
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49882585"
---
# <a name="walkthrough-create-your-first-vsto-add-in-for-powerpoint"></a>Návod: Vytvoření vašeho prvního doplňku VSTO pro PowerPoint
  Tento návod ukazuje, jak k vytvoření doplňku VSTO pro Microsoft Office PowerPoint. Funkce, které vytvoříte v tento druh řešení jsou k dispozici pro vlastní, bez ohledu na to, které jsou otevřené prezentace aplikace. Další informace najdete v tématu [přehled vývoje řešení pro Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md).  
  
 [!INCLUDE[appliesto_pptallapp](../vsto/includes/appliesto-pptallapp-md.md)]  
  
 Tento návod znázorňuje následující úlohy:  
  
- Vytvoření projektu doplňku VSTO pro PowerPoint pro aplikaci PowerPoint.  
  
- Psaní kódu, který používá model objektu aplikace PowerPoint přidáte textové pole pro každý nový snímek.  
  
- Vytváření a spouštění projektů a otestovat ho.  
  
- Čištění projektu tak, aby doplňku VSTO už nespouští automaticky na vašem vývojovém počítači.  
  
  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Požadavky  
 K dokončení tohoto návodu budete potřebovat následující komponenty:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   PowerPoint  
  
## <a name="create-the-project"></a>Vytvoření projektu  
  
### <a name="to-create-a-new-project"></a>Chcete-li vytvořit nový projekt  
  
1.  Spustit [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  Na **souboru** nabídky, přejděte k **nový**a potom klikněte na tlačítko **projektu**.  
  
3.  V podokně šablony rozbalte **Visual C#** nebo **jazyka Visual Basic**a potom rozbalte **Office/SharePoint**.  
  
4.  V rozbalených **Office/SharePoint** uzlu, vyberte **Office Add-ins** uzlu.  
  
5.  V seznamu šablon projektu vyberte projekt doplňku VSTO v PowerPointu.  
  
6.  V **název** zadejte **FirstPowerPointAddIn**.  
  
7.  Klikněte na tlačítko **OK**.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] vytvoří **FirstPowerPointAddIn** projekt a otevře **ThisAddIn** souboru kódu v editoru.  
  
## <a name="write-code-that-adds-text-to-each-new-slide"></a>Napsat kód, který přidá text pro každý nový snímek  
 V dalším kroku přidejte kód do soubor kódu ThisAddIn. Nový kód používá model objektu aplikace PowerPoint přidáte textové pole pro každý nový snímek. Ve výchozím nastavení obsahuje soubor kódu ThisAddIn následující generovaného kódu:  
  
-   Částečnou definici `ThisAddIn` třídy. Tato třída představuje vstupní bod pro kód a poskytuje přístup k objektovému modelu aplikace PowerPoint. Další informace najdete v tématu [doplňků Program VSTO](../vsto/programming-vsto-add-ins.md). Zbývající část `ThisAddIn` třída je definována v souboru skryté kódu, který byste neměli měnit.  
  
-   `ThisAddIn_Startup` a `ThisAddIn_Shutdown` obslužných rutin událostí. Tyto obslužné rutiny událostí jsou volány při PowerPoint načte a uvolní doplňku VSTO. Pomocí těchto obslužných rutin událostí k inicializaci doplňku VSTO, když je načten a chcete vyčistit prostředky využívané třídou doplňku VSTO, když je uvolněn. Další informace najdete v tématu [události v projektech pro systém Office](../vsto/events-in-office-projects.md).  
  
### <a name="to-add-a-text-box-to-each-new-slide"></a>Chcete-li přidat textové pole pro každý nový snímek  
  
1. V soubor kódu ThisAddIn, přidejte následující kód, který `ThisAddIn` třídy. Tento kód definuje obslužnou rutinu události pro [Microsoft.Office.Interop.PowerPoint.EApplication_Event.PresentationNewSlide](/previous-versions/office/developer/office-2010/ff762876(v%3doffice.14)) událost <xref:Microsoft.Office.Interop.PowerPoint.Application> objektu.  
  
    Když uživatel přidá nový snímek na aktivní prezentace, tato obslužná rutina události přidá do textového pole k hornímu okraji nový snímek a přidá nějaký text do textového pole.  
  
    [!code-vb[Trin_PowerPointAddInTutorial#1](../vsto/codesnippet/VisualBasic/Trin_PowerPointAddInTutorial/ThisAddIn.vb#1)]
    [!code-csharp[Trin_PowerPointAddInTutorial#1](../vsto/codesnippet/CSharp/Trin_PowerPointAddInTutorial/ThisAddIn.cs#1)]  
  
2. Pokud používáte C#, přidejte následující kód, který `ThisAddIn_Startup` obslužné rutiny události. Tento kód se nejde připojit `Application_PresentationNewSlide` obslužné rutině události [Microsoft.Office.Interop.PowerPoint.EApplication_Event.PresentationNewSlide](/previous-versions/office/developer/office-2010/ff762876(v%3doffice.14)) událostí.  
  
    [!code-csharp[Trin_PowerPointAddInTutorial#2](../vsto/codesnippet/CSharp/Trin_PowerPointAddInTutorial/ThisAddIn.cs#2)]  
  
   V předchozích příkladech kódu upravit každý nový snímek, použijte následující objekty:  
  
-   `Application` Pole `ThisAddIn` třídy. `Application` Pole vrátí <xref:Microsoft.Office.Interop.PowerPoint.Application> objektu, který představuje aktuální instanci aplikace PowerPoint.  
  
-   `Sld` Parametr obslužné rutiny události pro [Microsoft.Office.Interop.PowerPoint.EApplication_Event.PresentationNewSlide](/previous-versions/office/developer/office-2010/ff762876(v%3doffice.14)) událostí. `Sld` Parametr je <xref:Microsoft.Office.Interop.PowerPoint.Slide> objektu, který reprezentuje nový snímek. Další informace najdete v tématu [řešení pro aplikaci PowerPoint](../vsto/powerpoint-solutions.md).  
  
## <a name="test-the-project"></a>Testování projektu  
 Při sestavení a spuštění projektu, ověřte, že do textového pole zobrazuje v nových snímků, které přidáte do prezentace.  
  
### <a name="to-test-the-project"></a>Otestování projektu  
  
1.  Stisknutím klávesy **F5** sestavení a spuštění projektu.  
  
     Při sestavování projektu kód je zkompilován do sestavení, které je umístěn ve výstupní složce sestavení pro projekt. Visual Studio také vytvoří sadu položky registru, kterými může zjišťovat a načíst doplňku VSTO v aplikaci PowerPoint a nakonfiguruje nastavení zabezpečení na vývojovém počítači povolit doplňku VSTO pro spuštění. Další informace najdete v tématu [řešení pro systém Office sestavení](../vsto/building-office-solutions.md).  
  
2.  V aplikaci PowerPoint přidejte nový snímek active prezentaci.  
  
3.  Ověřte, že následující text je přidán do nového textového pole v horní části snímku.  
  
     **Tento text byl přidán s použitím kódu.**  
  
4.  Zavřete aplikaci PowerPoint.  
  
## <a name="clean-up-the-project"></a>Vyčistěte projekt  
 Po dokončení vývoje projektu doplňku VSTO sestavení, položky registru a nastavení zabezpečení odeberte z vývojového počítače. V opačném případě doplňku VSTO se spustí pokaždé, když otevřete aplikaci PowerPoint ve vývojovém počítači.  
  
### <a name="to-clean-up-your-project"></a>Chcete-li vyčistit projekt  
  
1.  V sadě Visual Studio na **sestavení** nabídky, klikněte na tlačítko **Vyčistit řešení**.  
  
## <a name="next-steps"></a>Další kroky  
 Teď, když jste vytvořili základní doplňku VSTO pro PowerPoint, můžete další informace o tom, jak vývoj doplňků VSTO z těchto témat:  
  
-   Obecné programovacích úloh, které můžete provádět v doplňcích VSTO pro PowerPoint. Další informace najdete v tématu [doplňků Program VSTO](../vsto/programming-vsto-add-ins.md).  
  
-   Použití objektového modelu aplikace PowerPoint. Další informace najdete v tématu [řešení pro aplikaci PowerPoint](../vsto/powerpoint-solutions.md).  
  
-   Přizpůsobení uživatelského rozhraní PowerPointu například přidat vlastní kartu na pás karet nebo vytvořením vlastní vlastního podokna úloh. Další informace najdete v tématu [přizpůsobení uživatelského rozhraní Office](../vsto/office-ui-customization.md).  
  
-   Sestavování a ladění doplňků VSTO pro PowerPoint. Další informace najdete v tématu [řešení pro systém Office sestavení](../vsto/building-office-solutions.md).  
  
-   Nasazení doplňků VSTO pro PowerPoint. Další informace najdete v tématu [nasazení řešení Office](../vsto/deploying-an-office-solution.md).  
  
## <a name="see-also"></a>Viz také:  
 [Programování doplňků VSTO](../vsto/programming-vsto-add-ins.md)   
 [Řešení pro aplikaci PowerPoint](../vsto/powerpoint-solutions.md)   
 [Přizpůsobení uživatelského rozhraní systému Office](../vsto/office-ui-customization.md)   
 [Vytváření řešení pro systém Office](../vsto/building-office-solutions.md)   
 [Nasazení řešení Office](../vsto/deploying-an-office-solution.md)   
 [Přehled šablon projektů Office](../vsto/office-project-templates-overview.md)  
  
  