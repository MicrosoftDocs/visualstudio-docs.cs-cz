---
title: 'Návod: vytvoření prvního doplňku VSTO pro Outlook'
description: Vytvořte doplněk na úrovni aplikace pro aplikaci Microsoft Outlook. Tato funkce je k dispozici pro samotnou aplikaci, bez ohledu na to, která položka Outlooku je otevřená.
ms.custom: SEO-VS-2020
ms.date: 08/14/2019
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application-level add-ins [Office development in Visual Studio], creating your first project
- Office development in Visual Studio, creating your first project
- add-ins [Office development in Visual Studio], creating your first project
- Outlook [Office development in Visual Studio], creating your first project
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 16f735e2902527307ac812922495a2a0cb3b377e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99966588"
---
# <a name="walkthrough-create-your-first-vsto-add-in-for-outlook"></a>Návod: vytvoření prvního doplňku VSTO pro Outlook
  V tomto návodu se dozvíte, jak vytvořit doplněk VSTO pro systém Microsoft Office Outlook. Funkce, které vytvoříte v tomto druhu řešení, jsou k dispozici pro samotnou aplikaci, bez ohledu na to, která položka Outlooku je otevřená. Další informace najdete v tématu [Přehled vývoje řešení pro systém Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md).

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

[!include[Add-ins note](includes/addinsnote.md)]

 Tento návod znázorňuje následující úlohy:

- Vytváření projektu doplňku VSTO pro Outlook pro Outlook

- Psaní kódu, který používá objektový model aplikace Outlook pro přidání textu do předmětu a textu nové e-mailové zprávy.

- Sestavení a spuštění projektu pro otestování.

- Vyčistěte dokončený projekt, aby se tento doplněk VSTO na vývojovém počítači nespouštěl automaticky.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Požadavky
 K dokončení tohoto návodu budete potřebovat následující komponenty:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- Microsoft Outlook

## <a name="create-the-project"></a>Vytvoření projektu

### <a name="to-create-a-new-outlook-project-in-visual-studio"></a>Vytvoření nového projektu Outlooku v aplikaci Visual Studio

1. Spustit [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

2. V nabídce **soubor** přejděte na příkaz **Nový** a klikněte na **projekt**.

3. V podokně šablony rozbalte položku **Visual C#** nebo **Visual Basic** a potom rozbalte položku **Office/SharePoint**.

4. V rozbaleném uzlu **Office/SharePoint** vyberte uzel **Doplňky Office** .

5. V seznamu šablon projektu vyberte projekt doplňku VSTO pro Outlook.

6. Do pole **název** zadejte **FirstOutlookAddIn**.

7. Klikněte na **OK**.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Vytvoří projekt **FirstOutlookAddIn** a otevře soubor s kódem **ThisAddIn** v editoru.

## <a name="write-code-that-adds-text-to-each-new-mail-message"></a>Napsat kód, který přidá text do každé nové e-mailové zprávy
 Dále přidejte kód do souboru kódu ThisAddIn. Nový kód používá objektový model Outlooku k přidání textu do každé nové e-mailové zprávy. Ve výchozím nastavení soubor kódu ThisAddIn obsahuje následující generovaný kód:

- Částečná definice `ThisAddIn` třídy. Tato třída poskytuje vstupní bod pro váš kód a poskytuje přístup k objektovému modelu aplikace Outlook. Další informace najdete v tématu [programové doplňky VSTO](../vsto/programming-vsto-add-ins.md). Zbytek `ThisAddIn` třídy je definován ve skrytém souboru kódu, který byste neměli upravovat.

- `ThisAddIn_Startup` `ThisAddIn_Shutdown` Obslužné rutiny události a. Tyto obslužné rutiny události jsou volány, když aplikace Outlook načte a uvolní doplněk VSTO. Tyto obslužné rutiny událostí použijte k inicializaci doplňku VSTO po jeho načtení a k vyčištění prostředků používaných doplňkem VSTO, když se uvolní. Další informace najdete v tématu [události v projektech Office](../vsto/events-in-office-projects.md).

### <a name="to-add-text-to-the-subject-and-body-of-each-new-mail-message"></a>Přidání textu do předmětu a textu každé nové e-mailové zprávy

1. V souboru kódu ThisAddIn deklarujte pole s názvem `inspectors` ve `ThisAddIn` třídě. `inspectors`Pole udržuje odkaz na kolekci oken inspektorů v aktuální instanci Outlooku. Tento odkaz zabrání systému uvolňování paměti uvolnit paměť, která obsahuje obslužnou rutinu události pro <xref:Microsoft.Office.Interop.Outlook.InspectorsEvents_Event.NewInspector> událost.

    [!code-vb[Trin_OutlookAddInTutorial#1](../vsto/codesnippet/VisualBasic/Trin_OutlookAddInTutorial/ThisAddIn.vb#1)]
    [!code-csharp[Trin_OutlookAddInTutorial#1](../vsto/codesnippet/CSharp/Trin_OutlookAddInTutorial/ThisAddIn.cs#1)]

2. Nahraďte metodu `ThisAddIn_Startup` následujícím kódem. Tento kód připojí k události obslužnou rutinu události <xref:Microsoft.Office.Interop.Outlook.InspectorsEvents_Event.NewInspector> .

    [!code-vb[Trin_OutlookAddInTutorial#2](../vsto/codesnippet/VisualBasic/Trin_OutlookAddInTutorial/ThisAddIn.vb#2)]
    [!code-csharp[Trin_OutlookAddInTutorial#2](../vsto/codesnippet/CSharp/Trin_OutlookAddInTutorial/ThisAddIn.cs#2)]

3. V souboru kódu ThisAddIn přidejte do třídy následující kód `ThisAddIn` . Tento kód definuje obslužnou rutinu události pro <xref:Microsoft.Office.Interop.Outlook.InspectorsEvents_Event.NewInspector> událost.

    Když uživatel vytvoří novou e-mailovou zprávu, tato obslužná rutina události přidá text do řádku předmětu a textu zprávy.

    [!code-vb[Trin_OutlookAddInTutorial#3](../vsto/codesnippet/VisualBasic/Trin_OutlookAddInTutorial/ThisAddIn.vb#3)]
    [!code-csharp[Trin_OutlookAddInTutorial#3](../vsto/codesnippet/CSharp/Trin_OutlookAddInTutorial/ThisAddIn.cs#3)]

   Chcete-li upravit každou novou e-mailovou zprávu, předchozí příklady kódu používají následující objekty:

- `Application`Pole `ThisAddIn` třídy `Application`Pole vrátí <xref:Microsoft.Office.Interop.Outlook.Application> objekt, který představuje aktuální instanci aplikace Outlook.

- `Inspector`Parametr obslužné rutiny události <xref:Microsoft.Office.Interop.Outlook.InspectorsEvents_Event.NewInspector> . `Inspector`Parametr je <xref:Microsoft.Office.Interop.Outlook.Inspector> objekt, který představuje okno inspektora nové e-mailové zprávy. Další informace najdete v tématu [řešení pro Outlook](../vsto/outlook-solutions.md).

## <a name="test-the-project"></a>Testování projektu
 Při sestavování a spouštění projektu ověřte, zda se text zobrazuje v řádku předmětu a textu nové e-mailové zprávy.

### <a name="to-test-the-project"></a>Otestování projektu

1. Stisknutím klávesy **F5** Sestavte a spusťte projekt.

     Při sestavování projektu je kód zkompilován do sestavení, které je součástí výstupní složky sestavení pro projekt. Sada Visual Studio také vytvoří sadu položek registru, které umožní aplikaci Outlook zjistit a načíst doplněk VSTO a nakonfiguruje nastavení zabezpečení na vývojovém počítači, aby bylo možné doplněk VSTO spustit. Další informace naleznete v tématu [Přehled procesu sestavení řešení pro systém Office](../vsto/walkthrough-creating-your-first-vsto-add-in-for-outlook.md).

2. V Outlooku vytvořte novou e-mailovou zprávu.

3. Ověřte, že se do řádku předmětu a textu zprávy přidal následující text.

     **Tento text byl přidán pomocí kódu.**

4. Zavřete Outlook.

## <a name="clean-up-the-project"></a>Vyčištění projektu
 Po dokončení vývoje projektu odeberte sestavení doplňku VSTO, položky registru a nastavení zabezpečení z vývojového počítače. V opačném případě se doplněk VSTO spustí pokaždé, když otevřete Outlook ve vývojovém počítači.

### <a name="to-clean-up-your-project"></a>Vyčištění projektu

1. V aplikaci Visual Studio v nabídce **sestavení** klikněte na možnost **Vyčistit řešení**.

## <a name="next-steps"></a>Další kroky
 Teď, když jste vytvořili základní doplněk VSTO pro Outlook, můžete získat další informace o tom, jak vyvíjet doplňky VSTO z těchto témat:

- Obecné úlohy programování, které můžete provádět pomocí doplňků VSTO pro Outlook. Další informace najdete v tématu [programové doplňky VSTO](../vsto/programming-vsto-add-ins.md).

- Použití objektového modelu aplikace Outlook. Další informace najdete v tématu [řešení pro Outlook](../vsto/outlook-solutions.md).

- Přizpůsobení uživatelského rozhraní aplikace Outlook, například přidáním vlastní karty na pás karet nebo vytvořením vlastního podokna úloh. Další informace najdete v tématu [přizpůsobení uživatelského rozhraní systému Office](../vsto/office-ui-customization.md).

- Sestavování a ladění doplňků VSTO pro Outlook Další informace najdete v tématu [sestavování řešení pro systém Office](../vsto/building-office-solutions.md).

- Nasazují se doplňky VSTO pro Outlook. Další informace najdete v tématu [nasazení řešení pro Office](../vsto/deploying-an-office-solution.md).

## <a name="see-also"></a>Viz také
- [Programové doplňky VSTO](../vsto/programming-vsto-add-ins.md)
- [Řešení pro Outlook](../vsto/outlook-solutions.md)
- [Přizpůsobení uživatelského rozhraní systému Office](../vsto/office-ui-customization.md)
- [Sestavování řešení pro systém Office](../vsto/building-office-solutions.md)
- [Nasazení řešení pro systém Office](../vsto/deploying-an-office-solution.md)
- [Přehled šablon projektů Office](../vsto/office-project-templates-overview.md)
