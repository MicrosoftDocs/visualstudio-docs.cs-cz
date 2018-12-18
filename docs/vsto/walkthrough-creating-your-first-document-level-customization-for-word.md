---
title: 'Návod: Vytvoření prvního přizpůsobení na úrovni dokumentu pro Word'
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
- Word [Office development in Visual Studio], creating your first project
- document-level customizations [Office development in Visual Studio], creating your first project
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 1c5c25163a49e51b0759e57318d6119edec97983
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49928812"
---
# <a name="walkthrough-create-your-first-document-level-customization-for-word"></a>Návod: Vytvoření prvního přizpůsobení na úrovni dokumentu pro Word
  Tento úvodní názorný postup ukazuje, jak k vytvoření přizpůsobení na úrovni dokumentu pro aplikaci Microsoft Office Word. Funkce, které vytvoříte v tento druh řešení jsou k dispozici pouze při otevření určitého dokumentu. Nelze použít přizpůsobení úrovni dokumentu provést změny celou aplikaci, například zobrazení novou kartu pásu karet, když jakýkoliv dokument je otevřen.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 Tento návod znázorňuje následující úlohy:  
  
- Vytvoření projektu dokumentu aplikace Word.  
  
- Přidání textu do dokumentu, který je hostovaný v návrháři aplikace Visual Studio.  
  
- Psaní kódu, který používá objektový model aplikace Word se při otevření přidat text do přizpůsobeného dokumentu.  
  
- Vytváření a spouštění projektů a otestovat ho.  
  
- Čištění projektu k odstranění nepotřebných sestavení souborů a nastavení zabezpečení z vývojového počítače.  
  
  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Požadavky  
 K dokončení tohoto návodu budete potřebovat následující komponenty:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Microsoft Word  
  
## <a name="create-the-project"></a>Vytvoření projektu  
  
### <a name="to-create-a-new-word-document-project-in-visual-studio"></a>K vytvoření nového projektu dokumentu aplikace Word v sadě Visual Studio  
  
1.  Spustit [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  Na **souboru** nabídky, přejděte k **nový**a potom klikněte na tlačítko **projektu**.  
  
3.  V podokně šablony rozbalte **Visual C#** nebo **jazyka Visual Basic**a potom rozbalte **Office/SharePoint**.  
  
4.  V rozbalených **Office/SharePoint** uzlu, vyberte **Office Add-ins** uzlu.  
  
5.  V seznamu šablon projektu vyberte projekt dokument VSTO pro Word.  
  
6.  V **název** zadejte **FirstDocumentCustomization**.  
  
7.  Klikněte na tlačítko **OK**.  
  
     **Visual Studio Tools for Office Project Wizard** otevře.  
  
8.  Vyberte **vytvoříte nový textový dokument**a klikněte na tlačítko **OK**.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] vytvoří **FirstDocumentCustomization** projektu a přidá **FirstDocumentCustomization** dokumentu a ThisDocument souboru kódu do projektu. **FirstDocumentCustomization** dokument se automaticky otevře v návrháři.  
  
## <a name="close-and-reopen-the-document-in-the-designer"></a>Zavření a opětovném otevření dokumentu v Návrháři  
 Pokud jste úmyslně nebo neúmyslně zavřít dokument v Návrháři při vývoji projektu, můžete ho znovu otevřít.  
  
### <a name="to-close-and-reopen-the-document-in-the-designer"></a>Zavřít a znovu otevřít dokument v Návrháři  
  
1.  Kliknutím na Zavřít dokument **Zavřít** tlačítko (X) pro okna návrháře.  
  
2.  V **Průzkumníka řešení**, klikněte pravým tlačítkem myši **ThisDocument** soubor kódu a klikněte na tlačítko **Návrhář zobrazení**.  
  
     \- nebo –  
  
     V **Průzkumníka řešení**, dvakrát klikněte **ThisDocument** soubor kódu.  
  
## <a name="add-text-to-the-document-in-the-designer"></a>Přidání textu do dokumentu v Návrháři  
 Uživatelské rozhraní (UI) můžete navrhnout vaše přizpůsobení pomocí úpravy dokumentu, který je otevřen v návrháři. Můžete například přidat text, tabulek nebo ovládací prvky aplikace Word. Další informace o tom, jak používat návrháře, naleznete v tématu [projektech pro systém Office v prostředí sady Visual Studio](../vsto/office-projects-in-the-visual-studio-environment.md).  
  
### <a name="to-add-text-to-your-document-by-using-the-designer"></a>Přidání textu do dokumentu pomocí návrháře  
  
1.  V dokumentu, který je v Návrháři otevřený zadejte následující text.  
  
     **Tento text byl přidán s použitím návrháře.**  
  
## <a name="add-text-to-the-document-programmatically"></a>Přidání textu do dokumentů prostřednictvím kódu programu  
 V dalším kroku přidejte kód do souboru kódu ThisDocument. Nový kód používá objektový model aplikace Word přidat druhý odstavec textu do dokumentu. Ve výchozím nastavení ThisDocument soubor kódu obsahuje následující generovaného kódu:  
  
-   Částečnou definici `ThisDocument` třída, která představuje programovací model dokument a poskytuje přístup k objektovému modelu Wordu. Další informace najdete v tématu [hostitelská položka Document](../vsto/document-host-item.md) a [přehled modelu objektů aplikace Word](../vsto/word-object-model-overview.md). Zbývající část `ThisDocument` třída je definována v souboru skryté kódu, který byste neměli měnit.  
  
-   `ThisDocument_Startup` a `ThisDocument_Shutdown` obslužných rutin událostí. Tyto obslužné rutiny událostí jsou volány při otevření a zavření dokumentu. Pomocí těchto obslužných rutin událostí k inicializaci přizpůsobením při otevření dokumentu a chcete vyčistit prostředky využívané třídou přizpůsobením při zavření dokumentu. Další informace najdete v tématu [události v projektech pro systém Office](../vsto/events-in-office-projects.md).  
  
### <a name="to-add-a-second-paragraph-of-text-to-the-document-by-using-code"></a>Přidat druhý odstavec textu v dokumentu s použitím kódu  
  
1.  V **Průzkumníka řešení**, klikněte pravým tlačítkem na **ThisDocument**a potom klikněte na tlačítko **zobrazit kód**.  
  
     V sadě Visual Studio otevře soubor kódu.  
  
2.  Nahradit `ThisDocument_Startup` obslužné rutiny události s následujícím kódem. Po otevření dokumentu tento kód přidá odstavec textu do dokumentu.  
  
     [!code-vb[Trin_WordDocumentTutorial#1](../vsto/codesnippet/VisualBasic/FirstDocumentCustomization/ThisDocument.vb#1)]
     [!code-csharp[Trin_WordDocumentTutorial#1](../vsto/codesnippet/CSharp/FirstDocumentCustomization/ThisDocument.cs#1)]  
  
    > [!NOTE]  
    >  Tento kód používá index hodnotu 1 pro přístup k prvního odstavce <xref:Microsoft.Office.Tools.Word.Document.Paragraphs%2A> vlastnost. Přestože Visual Basic a Visual C# použít pole založené na 0, spodní hranice pole většina kolekcí v objektovém modelu aplikace Word je 1. Další informace najdete v tématu [psaní kódu v řešeních pro systém Office](../vsto/writing-code-in-office-solutions.md).  
  
## <a name="test-the-project"></a>Testování projektu  
  
### <a name="to-test-your-document"></a>K otestování vašeho dokumentu  
  
1.  Stisknutím klávesy **F5** sestavení a spuštění projektu.  
  
     Při sestavování projektu kód je zkompilován do sestavení, který je přidružený dokument. Visual Studio vloží kopii dokumentu a sestavení ve výstupní složce sestavení pro projekt, a nakonfiguruje nastavení zabezpečení na vývojovém počítači povolit vlastní nastavení pro spuštění. Další informace najdete v tématu [řešení pro systém Office sestavení](../vsto/building-office-solutions.md).  
  
2.  V dokumentu ověřte, že vidíte následující text.  
  
     **Tento text byl přidán s použitím návrháře.**  
  
     **Tento text byl přidán s použitím kódu.**  
  
3.  Zavřete dokument.  
  
## <a name="clean-up-the-project"></a>Vyčistěte projekt  
 Po dokončení vývoje projektu, byste měli odebrat soubory ve výstupní složce sestavení a nastavení zabezpečení vytvořeného procesem sestavení.  
  
### <a name="to-clean-up-the-completed-project-on-your-development-computer"></a>Chcete-li vyčistit dokončený projekt na vašem vývojovém počítači  
  
1.  V sadě Visual Studio na **sestavení** nabídky, klikněte na tlačítko **Vyčistit řešení**.  
  
## <a name="next-steps"></a>Další kroky  
 Teď, když jste vytvořili základní přizpůsobení úrovni dokumentu pro Word, můžete další informace o tom, jak vyvíjet vlastní nastavení v těchto tématech:  
  
-   Obecné programování úkolů, které můžete provádět v přizpůsobeních na úrovni dokumentu: [programování přizpůsobení na úrovni dokumentu](../vsto/programming-document-level-customizations.md).  
  
-   Úkoly programování, které jsou specifické pro přizpůsobení na úrovni dokumentu pro Word: [řešení aplikace Word](../vsto/word-solutions.md).  
  
-   Použití objektového modelu aplikace Word: [přehled modelu objektů aplikace Word](../vsto/word-object-model-overview.md).  
  
-   Přizpůsobení uživatelského rozhraní aplikace Word, například podle přidat vlastní kartu na pás karet nebo vytvořit vlastní podokna akcí: [přizpůsobení uživatelského rozhraní Office](../vsto/office-ui-customization.md).  
  
-   Provádění úloh, které nejsou možné pomocí objektového modelu aplikace Word (například hostování spravované ovládací prvky v dokumentech a ovládací prvky aplikace Word připojení k datům s použitím dat Windows Forms pomocí rozšířených objektů aplikace Word poskytuje řešení pro systém Office v sadě Visual Studio vazby modelu): [automatizace aplikace Word s použitím rozšířených objektů](../vsto/automating-word-by-using-extended-objects.md).  
  
-   Sestavování a ladění přizpůsobení na úrovni dokumentu pro Word: [řešení pro systém Office sestavení](../vsto/building-office-solutions.md).  
  
-   Nasazení přizpůsobení na úrovni dokumentu pro Word: [nasazení řešení Office](../vsto/deploying-an-office-solution.md).  
  
## <a name="see-also"></a>Viz také:  
 [Přehled vývoje řešení pro Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)   
 [Řešení aplikace Word](../vsto/word-solutions.md)   
 [Programování přizpůsobení na úrovni dokumentu](../vsto/programming-document-level-customizations.md)   
 [Přehled modelu objektů aplikace Word](../vsto/word-object-model-overview.md)   
 [Automatizace aplikace Word s použitím rozšířených objektů](../vsto/automating-word-by-using-extended-objects.md)   
 [Přizpůsobení uživatelského rozhraní systému Office](../vsto/office-ui-customization.md)   
 [Vytváření řešení pro systém Office](../vsto/building-office-solutions.md)   
 [Nasazení řešení Office](../vsto/deploying-an-office-solution.md)   
 [Přehled šablon projektů Office](../vsto/office-project-templates-overview.md)  
  
  