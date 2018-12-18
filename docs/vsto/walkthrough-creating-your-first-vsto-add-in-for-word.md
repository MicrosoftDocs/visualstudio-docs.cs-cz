---
title: 'Návod: Vytvoření vašeho prvního doplňku VSTO pro Word'
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
- Word [Office development in Visual Studio], creating your first project
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: cf20b3f742bfc5ff6de6af080f3651f9d9027234
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49940967"
---
# <a name="walkthrough-create-your-first-vsto-add-in-for-word"></a>Návod: Vytvoření vašeho prvního doplňku VSTO pro Word
  Tento úvodní názorný postup ukazuje, jak k vytvoření doplňku VSTO pro Microsoft Office Word. Funkce, které vytvoříte v tento druh řešení jsou k dispozici aplikace samostatně, bez ohledu na to, které jsou otevřené dokumenty.  
  
 [!INCLUDE[appliesto_wdallapp](../vsto/includes/appliesto-wdallapp-md.md)]  
  
 Tento návod znázorňuje následující úlohy:  
  
- Vytvoření projektu doplňku VSTO pro Word.  
  
- Psaní kódu, který používá objektový model aplikace Word se při uložení přidat text do dokumentu.  
  
- Vytváření a spouštění projektů a otestovat ho.  
  
- Čištění dokončený projekt tak, aby doplňku VSTO už nespouští automaticky na vašem vývojovém počítači.  
  
  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Požadavky  
 K dokončení tohoto návodu budete potřebovat následující komponenty:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Microsoft Word  
  
## <a name="create-the-project"></a>Vytvoření projektu  
  
### <a name="to-create-a-new-word-vsto-add-in-project-in-visual-studio"></a>Chcete-li vytvořit nový projekt doplňku VSTO pro Word v sadě Visual Studio  
  
1.  Spustit [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  Na **souboru** nabídky, přejděte k **nový**a potom klikněte na tlačítko **projektu**.  
  
3.  V podokně šablony rozbalte **Visual C#** nebo **jazyka Visual Basic**a potom rozbalte **Office/SharePoint**.  
  
4.  V rozbalených **Office/SharePoint** uzlu, vyberte **Office Add-ins** uzlu.  
  
5.  V seznamu šablon projektu vyberte projekt doplňku VSTO pro Word.  
  
6.  V **název** zadejte **FirstWordAddIn**.  
  
7.  Klikněte na tlačítko **OK**.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] vytvoří **FirstWordAddIn** projekt a otevře soubor kódu ThisAddIn v editoru.  
  
## <a name="write-code-to-add-text-to-the-saved-document"></a>Napsání kódu pro přidání textu k uložené dokumenty  
 V dalším kroku přidejte kód do soubor kódu ThisAddIn. Nový kód používá k přidání často používaný text do každého dokumentu uloženého objektový model aplikace Word. Ve výchozím nastavení obsahuje soubor kódu ThisAddIn následující generovaného kódu:  
  
-   Částečnou definici `ThisAddIn` třídy. Tato třída představuje vstupní bod pro kód a poskytuje přístup k objektovému modelu Wordu. Další informace najdete v tématu [doplňků Program VSTO](../vsto/programming-vsto-add-ins.md). Zbývající část `ThisAddIn` třída je definována v souboru skryté kódu, který byste neměli měnit.  
  
-   `ThisAddIn_Startup` a `ThisAddIn_Shutdown` obslužných rutin událostí. Tyto obslužné rutiny událostí jsou volány při slovo načte a uvolní doplňku VSTO. Pomocí těchto obslužných rutin událostí k inicializaci doplňku VSTO, když je načten a chcete vyčistit prostředky využívané třídou doplňku VSTO, když je uvolněn. Další informace najdete v tématu [události v projektech pro systém Office](../vsto/events-in-office-projects.md).  
  
### <a name="to-add-a-paragraph-of-text-to-the-saved-document"></a>Přidání textu odstavce do uložené dokumenty  
  
1. V soubor kódu ThisAddIn, přidejte následující kód, který `ThisAddIn` třídy. Definuje obslužnou rutinu události pro nový kód <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave> událost, která se vyvolá, když je dokument uložen.  
  
    Když uživatel uloží dokument, obslužná rutina události přidá nový text na začátku dokumentu.  
  
    [!code-vb[Trin_WordAddInTutorial#1](../vsto/codesnippet/VisualBasic/FirstWordAddIn/ThisAddIn.vb#1)]
    [!code-csharp[Trin_WordAddInTutorial#1](../vsto/codesnippet/CSharp/FirstWordAddIn/ThisAddIn.cs#1)]  
  
   > [!NOTE]  
   >  Tento kód používá hodnotu indexu 1 pro přístup k prvního odstavce <xref:Microsoft.Office.Interop.Word._Document.Paragraphs%2A> kolekce. Přestože Visual Basic a Visual C# použít pole založené na 0, spodní hranice pole většina kolekcí v objektovém modelu aplikace Word je 1. Další informace najdete v tématu [psaní kódu v řešeních pro systém Office](../vsto/writing-code-in-office-solutions.md).  
  
2. Pokud používáte C#, přidejte následující kód vyžaduje k `ThisAddIn_Startup` obslužné rutiny události. Tento kód slouží k připojení `Application_DocumentBeforeSave` obslužné rutině události <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave> událostí.  
  
    [!code-csharp[Trin_WordAddInTutorial#2](../vsto/codesnippet/CSharp/FirstWordAddIn/ThisAddIn.cs#2)]  
  
   V předchozích příkladech kódu změnit dokument při uložení, použijte následující objekty:  
  
-   `Application` Pole `ThisAddIn` třídy. `Application` Pole vrátí <xref:Microsoft.Office.Interop.Word.Application> objektu, který představuje aktuální instanci aplikace Word.  
  
-   `Doc` Parametr obslužné rutiny události pro <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave> událostí. `Doc` Parametr je <xref:Microsoft.Office.Interop.Word.Document> objektu, který představuje uložený dokument. Další informace najdete v tématu [přehled modelu objektů aplikace Word](../vsto/word-object-model-overview.md).  
  
## <a name="test-the-project"></a>Testování projektu  
  
### <a name="to-test-the-project"></a>Otestování projektu  
  
1.  Stisknutím klávesy **F5** sestavení a spuštění projektu.  
  
     Při sestavování projektu kód je zkompilován do sestavení, která je zahrnutá ve výstupní složce sestavení pro projekt. Visual Studio také vytvoří sadu položky registru, kterými může zjišťovat a načíst doplňku VSTO ve Wordu a nakonfiguruje nastavení zabezpečení na vývojovém počítači povolit doplňku VSTO pro spuštění. Další informace najdete v tématu [řešení pro systém Office sestavení](../vsto/building-office-solutions.md).  
  
2.  V aplikaci Word uložte aktivní dokument.  
  
3.  Ověřte, že následující text je přidán do dokumentu.  
  
     **Tento text byl přidán s použitím kódu.**  
  
4.  Zavřete aplikaci Word.  
  
## <a name="clean-up-the-project"></a>Vyčistěte projekt  
 Po dokončení vývoje projektu doplňku VSTO sestavení, položky registru a nastavení zabezpečení odeberte z vývojového počítače. V opačném případě doplňku VSTO nadále spustí při každém otevření aplikace Word ve svém vývojovém počítači.  
  
### <a name="to-clean-up-the-completed-project-on-your-development-computer"></a>Chcete-li vyčistit dokončený projekt na vašem vývojovém počítači  
  
1.  V sadě Visual Studio na **sestavení** nabídky, klikněte na tlačítko **Vyčistit řešení**.  
  
## <a name="next-steps"></a>Další kroky  
 Teď, když jste vytvořili základní doplňku VSTO pro Word, můžete další informace o tom, jak vývoj doplňků VSTO z těchto témat:  
  
-   Obecné programování úkolů, které můžete provádět v doplňcích VSTO: [doplňků Program VSTO](../vsto/programming-vsto-add-ins.md).  
  
-   Úkoly programování, které jsou specifické pro doplňky VSTO pro Word: [řešení aplikace Word](../vsto/word-solutions.md).  
  
-   Použití objektového modelu aplikace Word: [přehled modelu objektů aplikace Word](../vsto/word-object-model-overview.md).  
  
-   Přizpůsobení uživatelského rozhraní aplikace Word, například podle přidat vlastní kartu na pás karet nebo vytváření vlastních vlastního podokna úloh: [přizpůsobení uživatelského rozhraní Office](../vsto/office-ui-customization.md).  
  
-   Sestavování a ladění doplňků VSTO pro Word: [řešení pro systém Office sestavení](../vsto/building-office-solutions.md).  
  
-   Nasazení doplňků VSTO pro Word: [nasazení řešení Office](../vsto/deploying-an-office-solution.md).  
  
## <a name="see-also"></a>Viz také:  
 [Přehled vývoje řešení pro Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)   
 [Řešení aplikace Word](../vsto/word-solutions.md)   
 [Programování doplňků VSTO](../vsto/programming-vsto-add-ins.md)   
 [Přehled modelu objektů aplikace Word](../vsto/word-object-model-overview.md)   
 [Přizpůsobení uživatelského rozhraní systému Office](../vsto/office-ui-customization.md)   
 [Vytváření řešení pro systém Office](../vsto/building-office-solutions.md)   
 [Nasazení řešení Office](../vsto/deploying-an-office-solution.md)   
 [Přehled šablon projektů Office](../vsto/office-project-templates-overview.md)  
  
  