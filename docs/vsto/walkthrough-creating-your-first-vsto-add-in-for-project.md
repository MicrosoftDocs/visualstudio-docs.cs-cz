---
title: 'Návod: vytvoření prvního doplňku VSTO pro projekt'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application-level add-ins [Office development in Visual Studio], creating your first project
- Office development in Visual Studio, creating your first project
- Project [Office development in Visual Studio], creating your first project
- add-ins [Office development in Visual Studio], creating your first project
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 4a84d295a47d3391f27e7101ad815dca0c910aa6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "62981390"
---
# <a name="walkthrough-create-your-first-vsto-add-in-for-project"></a>Návod: vytvoření prvního doplňku VSTO pro projekt
  V tomto návodu se dozvíte, jak vytvořit doplněk VSTO pro systém Microsoft Office projekt. Funkce, které vytvoříte v tomto druhu řešení, jsou k dispozici pro samotnou aplikaci, bez ohledu na to, které projekty jsou otevřené. Další informace najdete v tématu [Přehled vývoje řešení pro systém Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md).

 [!INCLUDE[appliesto_projallapp](../vsto/includes/appliesto-projallapp-md.md)]

 Tento návod znázorňuje následující úlohy:

- Vytváření projektu doplňku VSTO pro projekt.

- Psaní kódu, který používá objektový model projektu, chcete-li přidat úkol do nového projektu.

- Sestavení a spuštění projektu pro otestování.

- Vyčistěte dokončený projekt, aby se tento doplněk VSTO na vývojovém počítači nespouštěl automaticky.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Předpoklady
 K dokončení tohoto návodu budete potřebovat následující komponenty:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Project_15_short](../vsto/includes/project-15-short-md.md)] nebo [!INCLUDE[Project_14_short](../vsto/includes/project-14-short-md.md)]:

## <a name="create-the-project"></a>Vytvoření projektu

### <a name="to-create-a-new-project-in-visual-studio"></a>Vytvoření nového projektu v aplikaci Visual Studio

1. Spustit [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

2. V nabídce **soubor** přejděte na příkaz **Nový**a klikněte na **projekt**.

3. V podokně šablony rozbalte položku **Visual C#** nebo **Visual Basic**a potom rozbalte položku **Office/SharePoint**.

4. V rozbaleném uzlu **Office/SharePoint** vyberte uzel **Doplňky Office** .

5. V seznamu šablon projektu vyberte **doplněk project 2010** nebo **doplněk Project 2013**.

6. Do pole **název** zadejte **FirstProjectAddIn**.

7. Klikněte na **OK**.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Vytvoří projekt **FirstProjectAddIn** a otevře soubor s kódem **ThisAddIn** v editoru.

## <a name="write-code-that-adds-a-new-task-to-a-project"></a>Napsat kód, který přidá nový úkol do projektu
 Dále přidejte kód do souboru kódu ThisAddIn. Nový kód používá objektový model projektu pro přidání nového úkolu do projektu. Ve výchozím nastavení soubor kódu ThisAddIn obsahuje následující generovaný kód:

- Částečná definice `ThisAddIn` třídy. Tato třída poskytuje vstupní bod pro váš kód a poskytuje přístup k objektovému modelu projektu. Další informace najdete v tématu [programové doplňky VSTO](../vsto/programming-vsto-add-ins.md). Zbytek `ThisAddIn` třídy je definován ve skrytém souboru kódu, který byste neměli upravovat.

- `ThisAddIn_Startup` `ThisAddIn_Shutdown` Obslužné rutiny události a. Tyto obslužné rutiny události jsou volány při načtení projektu a uvolnění doplňku VSTO. Tyto obslužné rutiny událostí použijte k inicializaci doplňku VSTO po jeho načtení a k vyčištění prostředků používaných doplňkem VSTO, když se uvolní. Další informace najdete v tématu [události v projektech Office](../vsto/events-in-office-projects.md).

### <a name="to-add-a-task-to-a-new-project"></a>Přidání úkolu do nového projektu

1. V souboru kódu ThisAddIn přidejte do třídy následující kód `ThisAddIn` . Tento kód definuje obslužnou rutinu události pro `NewProject` událost `Microsoft.Office.Interop.MSProject.Application` třídy.

    Když uživatel vytvoří nový projekt, tato obslužná rutina události přidá úkol do projektu.

    [!code-vb[Trin_ProjectAddInTutorial#1](../vsto/codesnippet/VisualBasic/Trin_ProjectAddInTutorial/ThisAddIn.vb#1)]
    [!code-csharp[Trin_ProjectAddInTutorial#1](../vsto/codesnippet/CSharp/Trin_ProjectAddInTutorial/ThisAddIn.cs#1)]

   Chcete-li upravit projekt, tento příklad kódu používá následující objekty:

- `Application`Pole `ThisAddIn` třídy `Application`Pole vrátí `Microsoft.Office.Interop.MSProject.Application` objekt, který představuje aktuální instanci projektu.

- `pj`Parametr obslužné rutiny události pro událost NewProject `pj`Parametr je `Microsoft.Office.Interop.MSProject.Project` objekt, který představuje projekt. Další informace najdete v tématu [řešení projektu](../vsto/project-solutions.md).

1. Pokud používáte jazyk C#, přidejte následující kód do `ThisAddIn_Startup` obslužné rutiny události. Tento kód připojí `Application_Newproject` obslužnou rutinu události k události NewProject.

     [!code-csharp[Trin_ProjectAddInTutorial#2](../vsto/codesnippet/CSharp/Trin_ProjectAddInTutorial/ThisAddIn.cs#2)]

## <a name="test-the-project"></a>Testování projektu
 Při sestavování a spouštění projektu ověřte, zda se nový úkol zobrazí ve výsledném novém projektu.

### <a name="to-test-the-project"></a>Otestování projektu

1. Stisknutím klávesy **F5** Sestavte a spusťte projekt. Spustí se aplikace Microsoft Project a automaticky se otevře nový prázdný projekt.

     Při sestavování projektu je kód zkompilován do sestavení, které je součástí výstupní složky sestavení pro projekt. Sada Visual Studio také vytvoří sadu položek registru, které umožní projektu zjistit a načíst doplněk VSTO, a nakonfiguruje nastavení zabezpečení na vývojovém počítači, aby bylo možné doplněk VSTO spustit. Další informace naleznete v tématu [Přehled procesu sestavení řešení pro systém Office](/previous-versions/visualstudio/visual-studio-2010/h2c9cdc0(v=vs.100)).

2. Ověřte, zda je do prázdného projektu přidána nová úloha.

3. Ověřte, zda je v poli **název úlohy** úkolu zobrazen následující text.

     **Tento text byl přidán pomocí kódu.**

4. Zavřete aplikaci Microsoft Project.

## <a name="clean-up-the-project"></a>Vyčištění projektu
 Po dokončení vývoje projektu odeberte sestavení doplňku VSTO, položky registru a nastavení zabezpečení z vývojového počítače. V opačném případě se doplněk VSTO spustí pokaždé, když ve vývojovém počítači otevřete aplikaci Microsoft Project.

### <a name="to-clean-up-your-project"></a>Vyčištění projektu

1. V aplikaci Visual Studio v nabídce **sestavení** klikněte na možnost **Vyčistit řešení**.

## <a name="next-steps"></a>Další kroky
 Teď, když jste vytvořili základní doplněk VSTO pro Project, můžete získat další informace o tom, jak vyvíjet doplňky VSTO z těchto témat:

- Obecné úlohy programování, které můžete provádět v Doplňkech VSTO pro Project: [programový doplněk VSTO](../vsto/programming-vsto-add-ins.md).

- Použití objektového modelu projektu: [Projektová řešení](../vsto/project-solutions.md).

- Sestavování a ladění doplňku VSTO pro Project: [sestavování řešení pro Office](../vsto/building-office-solutions.md)

- Nasazují se doplňky VSTO pro Project: [nasazení řešení pro Office](../vsto/deploying-an-office-solution.md).

## <a name="see-also"></a>Viz také
- [Programové doplňky VSTO](../vsto/programming-vsto-add-ins.md)
- [Řešení projektu](../vsto/project-solutions.md)
- [Sestavování řešení pro systém Office](../vsto/building-office-solutions.md)
- [Nasazení řešení pro systém Office](../vsto/deploying-an-office-solution.md)
- [Přehled šablon projektů Office](../vsto/office-project-templates-overview.md)
