---
title: 'Návod: Vytvoření prvního přizpůsobení na úrovni dokumentu pro Excel'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, creating your first project
- Excel [Office development in Visual Studio], creating your first project
- document-level customizations [Office development in Visual Studio], creating your first project
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: ce16e3c2aca99acf6de9a7ce74c0c2ff46c0dcbb
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49849031"
---
# <a name="walkthrough-create-your-first-document-level-customization-for-excel"></a>Návod: Vytvoření prvního přizpůsobení na úrovni dokumentu pro Excel
  Tento úvodní názorný postup ukazuje, jak k vytvoření přizpůsobení na úrovni dokumentu pro aplikaci Microsoft Office Excel. Funkce, které vytvoříte v tento druh řešení jsou k dispozici pouze při otevření konkrétní sešitu. Nelze použít přizpůsobení úrovni dokumentu provést změny celou aplikaci, například zobrazení novou kartu pásu karet při otevření libovolné sešitu.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 Tento návod znázorňuje následující úlohy:  
  
- Vytvoření projektu sešitu aplikace Excel.  
  
- Přidání textu do listu, která je hostována v návrháři aplikace Visual Studio.  
  
- Psaní kódu, který se používá k přidání text do přizpůsobené listu, při otevření modelu objektů aplikace Excel.  
  
- Vytváření a spouštění projektů a otestovat ho.  
  
- Čištění dokončený projekt k odstranění nepotřebných sestavení souborů a nastavení zabezpečení z vývojového počítače.  
  
  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Požadavky  
 K dokončení tohoto návodu budete potřebovat následující komponenty:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] nebo [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].  
  
## <a name="create-the-project"></a>Vytvoření projektu  
  
### <a name="to-create-a-new-excel-workbook-project-in-visual-studio"></a>Chcete-li vytvořit nový projekt sešitu aplikace Excel v sadě Visual Studio  
  
1. Spustit [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2. Na **souboru** nabídky, přejděte k **nový**a potom klikněte na tlačítko **projektu**.  
  
3. V podokně šablony rozbalte **Visual C#** nebo **jazyka Visual Basic**a potom rozbalte **Office/SharePoint**.  
  
4. V rozbalených **Office/SharePoint** uzlu, vyberte **Office Add-ins** uzlu.  
  
5. V seznamu šablon projektu vyberte projekt doplňku VSTO pro Excel.  
  
6. V **název** zadejte **FirstWorkbookCustomization**.  
  
7. Klikněte na tlačítko **OK**.  
  
    **Visual Studio Tools for Office Project Wizard** otevře.  
  
8. Vyberte **vytvoříte nový textový dokument**a klikněte na tlačítko **OK**.  
  
   - [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] vytvoří **FirstWorkbookCustomization** projektu a přidá následující soubory do projektu.  
  
   - *FirstWorkbookCustomization*.xlsx – představuje Excelový sešit v projektu. Obsahuje všechny listy a grafy.  
  
   - List1 (*.vb* soubor v jazyce Visual Basic nebo *.cs* souboru pro jazyk Visual C#)-list, který poskytuje návrhová plocha a kód pro první listu v sešitu. Další informace najdete v tématu [hostitelská položka Worksheet](../vsto/worksheet-host-item.md).  
  
   - List2 (*.vb* soubor v jazyce Visual Basic nebo *.cs* souboru pro jazyk Visual C#)-list, který poskytuje návrhová plocha a kód pro druhý listu v sešitu.  
  
   - Sheet3 – (*.vb* soubor v jazyce Visual Basic nebo *.cs* souboru pro jazyk Visual C#)-list, který poskytuje návrhová plocha a kód pro třetí listu v sešitu.  
  
   - ThisWorkbook (*.vb* soubor v jazyce Visual Basic nebo *.cs* souboru pro jazyk Visual C#) – obsahuje návrhová plocha a kód pro přizpůsobení na úrovni sešitu. Další informace najdete v tématu [hostitelská položka Workbook](../vsto/workbook-host-item.md).  
  
     Soubor kódu List1 je automaticky otevřít v návrháři.  
  
## <a name="close-and-reopen-worksheets-in-the-designer"></a>Zavřete a znovu otevřete listů v Návrháři  
 Pokud úmyslně nebo neúmyslně zavření sešitu nebo listu v Návrháři při vývoji projektu, můžete ho znovu otevřít.  
  
### <a name="to-close-and-reopen-a-worksheet-in-the-designer"></a>Zavřít a znovu otevřít sešit v Návrháři  
  
1.  Sešit zavřete kliknutím **Zavřít** tlačítko (X) pro okna návrháře.  
  
2.  V **Průzkumníka řešení**, klikněte pravým tlačítkem myši **List1** soubor kódu a klikněte na tlačítko **Návrhář zobrazení**.  
  
     \- nebo –  
  
     V **Průzkumníka řešení**, dvakrát klikněte **List1** soubor kódu.  
  
## <a name="add-text-to-a-worksheet-in-the-designer"></a>Přidejte text do listu v Návrháři  
 Uživatelské rozhraní (UI) můžete navrhnout vaše přizpůsobení tak, že upravíte list, který je otevřen v návrháři. Můžete například přidat text do buněk, použít ve vzorcích nebo přidat ovládací prvky aplikace Excel. Další informace o tom, jak používat návrháře, naleznete v tématu [projektech pro systém Office v prostředí sady Visual Studio](../vsto/office-projects-in-the-visual-studio-environment.md).  
  
### <a name="to-add-text-to-a-worksheet-by-using-the-designer"></a>Chcete-li přidat text do listu pomocí návrháře  
  
1.  V listu, který je otevřen v Návrháři vyberte buňku **A1**a potom zadejte následující text.  
  
     **Tento text byl přidán s použitím návrháře.**  
  
> [!WARNING]  
>  Pokud přidáte tento řádek textu do buňky **A2**, se přepíše jiným kódem v tomto příkladu.  
  
## <a name="add-text-to-a-worksheet-programmatically"></a>Přidejte text do listu prostřednictvím kódu programu  
 V dalším kroku přidejte kód do souboru kódu List1. Nový kód používá objektový model aplikace Excel k přidání druhý řádek textu do sešitu. Ve výchozím nastavení List1 soubor kódu obsahuje následující generovaného kódu:  
  
-   Částečnou definici `Sheet1` třída, která představuje programovací model list a poskytuje přístup k objektovému modelu Excelu. Další informace najdete [hostitelská položka Worksheet](../vsto/worksheet-host-item.md) a [přehled modelu objektů aplikace Word](../vsto/word-object-model-overview.md). Zbývající část `Sheet1` třída je definována v souboru skryté kódu, který byste neměli měnit.  
  
-   `Sheet1_Startup` a `Sheet1_Shutdown` obslužných rutin událostí. Tyto obslužné rutiny událostí jsou volány při Excel načte a uvolní vaše vlastní nastavení. Pomocí těchto obslužných rutin událostí k inicializaci přizpůsobením při spuštění a chcete vyčistit prostředky využívané třídou vaše vlastní nastavení, když je uvolněn. Další informace najdete v tématu [události v projektech pro systém Office](../vsto/events-in-office-projects.md).  
  
### <a name="to-add-a-second-line-of-text-to-the-worksheet-by-using-code"></a>Chcete-li přidat druhý řádek textu do listu s použitím kódu  
  
1.  V **Průzkumníka řešení**, klikněte pravým tlačítkem na **List1**a potom klikněte na tlačítko **zobrazit kód**.  
  
     V sadě Visual Studio otevře soubor kódu.  
  
2.  Nahradit `Sheet1_Startup` obslužné rutiny události s následujícím kódem. Po otevření List1 tento kód přidá druhý řádek textu do listu.  
  
     [!code-csharp[Trin_ExcelWorkbookTutorial#1](../vsto/codesnippet/CSharp/Trin_ExcelWorkbookTutorial/Sheet1.cs#1)]
     [!code-vb[Trin_ExcelWorkbookTutorial#1](../vsto/codesnippet/VisualBasic/Trin_ExcelWorkbookTutorial/Sheet1.vb#1)]  
  
## <a name="test-the-project"></a>Testování projektu  
  
### <a name="to-test-your-workbook"></a>K otestování vašeho sešitu  
  
1.  Stisknutím klávesy **F5** sestavení a spuštění projektu.  
  
     Při sestavování projektu kód je zkompilován do sestavení, který je přidružený sešit. Visual Studio vloží kopii sešitu a sestavení ve výstupní složce sestavení pro projekt, a nakonfiguruje nastavení zabezpečení na vývojovém počítači povolit vlastní nastavení pro spuštění. Další informace najdete v tématu [řešení pro systém Office sestavení](../vsto/building-office-solutions.md).  
  
2.  V sešitu ověřte, že vidíte následující text.  
  
     **Tento text byl přidán s použitím návrháře.**  
  
     **Tento text byl přidán s použitím kódu.**  
  
3.  Zavření sešitu.  
  
## <a name="clean-up-the-project"></a>Vyčistěte projekt  
 Po dokončení vývoje projektu, byste měli odebrat soubory ve výstupní složce sestavení a nastavení zabezpečení vytvořeného procesem sestavení.  
  
### <a name="to-clean-up-the-completed-project-on-your-development-computer"></a>Chcete-li vyčistit dokončený projekt na vašem vývojovém počítači  
  
1.  V sadě Visual Studio na **sestavení** nabídky, klikněte na tlačítko **Vyčistit řešení**.  
  
## <a name="next-steps"></a>Další kroky  
 Teď, když jste vytvořili základní přizpůsobení úrovni dokumentu pro Excel, můžete další informace o tom, jak vyvíjet vlastní nastavení v těchto tématech:  
  
-   Obecné programování úkolů, které můžete provádět v přizpůsobeních na úrovni dokumentu: [programování přizpůsobení na úrovni dokumentu](../vsto/programming-document-level-customizations.md).  
  
-   Úkoly programování, které jsou specifické pro přizpůsobení na úrovni dokumentu pro Excel: [řešení pro Excel](../vsto/excel-solutions.md).  
  
-   Použití objektového modelu aplikace Excel: [přehled modelu objektů aplikace Excel](../vsto/excel-object-model-overview.md).  
  
-   Přizpůsobení uživatelského rozhraní aplikace Excel, například podle přidat vlastní kartu na pás karet nebo vytvořit vlastní podokna akcí: [přizpůsobení uživatelského rozhraní Office](../vsto/office-ui-customization.md).  
  
-   Provádění úloh, které nejsou možné pomocí objektového modelu Excelu (například hostování spravované ovládací prvky v dokumentech a vazba ovládacích prvků aplikace Excel k datům s použitím Windows Forms pomocí rozšířených objektů aplikace Excel, poskytuje nástroje pro vývoj pro Office v sadě Visual Studio data vazby modelu): [automatizace aplikace Excel s použitím rozšířených objektů](../vsto/automating-excel-by-using-extended-objects.md).  
  
-   Sestavování a ladění přizpůsobení úrovni dokumentu pro aplikaci Excel: [řešení pro systém Office sestavení](../vsto/building-office-solutions.md).  
  
-   Nasazení přizpůsobení úrovni dokumentu pro aplikaci Excel: [nasazení řešení Office](../vsto/deploying-an-office-solution.md).  
  
## <a name="see-also"></a>Viz také:  
 [Přehled vývoje řešení pro Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)   
 [Řešení pro aplikaci Excel](../vsto/excel-solutions.md)   
 [Programování přizpůsobení na úrovni dokumentu](../vsto/programming-document-level-customizations.md)   
 [Přehled modelu objektů aplikace Excel](../vsto/excel-object-model-overview.md)   
 [Automatizace aplikace Excel s použitím rozšířených objektů](../vsto/automating-excel-by-using-extended-objects.md)   
 [Přizpůsobení uživatelského rozhraní systému Office](../vsto/office-ui-customization.md)   
 [Vytváření řešení pro systém Office](../vsto/building-office-solutions.md)   
 [Nasazení řešení Office](../vsto/deploying-an-office-solution.md)   
 [Přehled šablon projektů Office](../vsto/office-project-templates-overview.md)  
  
  