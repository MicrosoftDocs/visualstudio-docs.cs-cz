---
title: 'Návod: vytvoření prvního doplňku VSTO pro Excel'
ms.date: 08/14/2019
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application-level add-ins [Office development in Visual Studio], creating your first project
- Office development in Visual Studio, creating your first project
- add-ins [Office development in Visual Studio], creating your first project
- Excel [Office development in Visual Studio], creating your first project
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 52b683b1f75f2967807f171c204fbf02a2e5db69
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "69548014"
---
# <a name="walkthrough-create-your-first-vsto-add-in-for-excel"></a>Návod: vytvoření prvního doplňku VSTO pro Excel
  V tomto úvodním návodu se dozvíte, jak vytvořit doplněk na úrovni aplikace pro systém Microsoft Office Excel. Funkce, které vytvoříte v tomto druhu řešení, jsou k dispozici pro samotnou aplikaci, bez ohledu na to, které sešity jsou otevřené.

 [!INCLUDE[appliesto_xlallapp](../vsto/includes/appliesto-xlallapp-md.md)]

[!include[Add-ins note](includes/addinsnote.md)]

 Tento návod znázorňuje následující úlohy:

- Vytváření projektu doplňku VSTO pro Excel pro Excel

- Psaní kódu, který používá objektový model aplikace Excel k přidání textu do sešitu, když je uložen.

- Sestavení a spuštění projektu pro otestování.

- Vyčistěte dokončený projekt, aby se tento doplněk VSTO na vývojovém počítači nespouštěl automaticky.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Předpoklady
 K dokončení tohoto návodu budete potřebovat následující komponenty:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] nebo [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)]:

## <a name="create-the-project"></a>Vytvoření projektu

#### <a name="to-create-a-new-excel-vsto-add-in-project-in-visual-studio"></a>Vytvoření nového projektu doplňku VSTO pro Excel v aplikaci Visual Studio

1. Spustit [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

2. V nabídce **soubor** přejděte na příkaz **Nový**a klikněte na **projekt**.

3. V podokně šablony rozbalte položku **Visual C#** nebo **Visual Basic**a potom rozbalte položku **Office/SharePoint**.

4. V rozbaleném uzlu **Office/SharePoint** vyberte uzel **Doplňky Office** .

5. V seznamu šablon projektu vyberte **doplněk excel 2010** nebo **doplněk Excelu 2013**.

6. Do pole **název** zadejte **FirstExcelAddIn**.

7. Klikněte na **OK**.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Vytvoří projekt **FirstExcelAddIn** a otevře soubor s kódem ThisAddIn v editoru.

## <a name="write-code-to-add-text-to-the-saved-workbook"></a>Napsání kódu pro přidání textu do uloženého sešitu
 Dále přidejte kód do souboru kódu ThisAddIn. Nový kód používá objektový model aplikace Excel k vložení často používaného textu do prvního řádku aktivního listu. Aktivní list je list, který se otevře, když uživatel sešit uloží. Ve výchozím nastavení soubor kódu ThisAddIn obsahuje následující generovaný kód:

- Částečná definice `ThisAddIn` třídy. Tato třída poskytuje vstupní bod pro váš kód a poskytuje přístup k objektovému modelu aplikace Excel. Další informace najdete v tématu [programové doplňky VSTO](../vsto/programming-vsto-add-ins.md). Zbytek `ThisAddIn` třídy je definován ve skrytém souboru kódu, který byste neměli upravovat.

- `ThisAddIn_Startup` `ThisAddIn_Shutdown` Obslužné rutiny události a. Tyto obslužné rutiny události jsou volány, když aplikace Excel načte a uvolní doplněk VSTO. Tyto obslužné rutiny událostí použijte k inicializaci doplňku VSTO po jeho načtení a k vyčištění prostředků používaných doplňkem při jeho uvolnění. Další informace najdete v tématu [události v projektech Office](../vsto/events-in-office-projects.md).

### <a name="to-add-a-line-of-text-to-the-saved-workbook"></a>Přidání řádku textu do uloženého sešitu

1. V souboru kódu ThisAddIn přidejte do třídy následující kód `ThisAddIn` . Nový kód definuje obslužnou rutinu události pro <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.WorkbookBeforeSave> událost, která je vyvolána při uložení sešitu.

    Když uživatel sešit uloží, obslužná rutina události přidá nový text na začátek aktivního listu.

    [!code-vb[Trin_ExcelAddInTutorial#1](../vsto/codesnippet/VisualBasic/Trin_ExcelAddInTutorial/ThisAddIn.vb#1)]
    [!code-csharp[Trin_ExcelAddInTutorial#1](../vsto/codesnippet/CSharp/Trin_ExcelAddInTutorial/ThisAddIn.cs#1)]

2. Pokud používáte jazyk C#, přidejte následující požadovaný kód do `ThisAddIn_Startup` obslužné rutiny události. Tento kód slouží k propojení `Application_WorkbookBeforeSave` obslužné rutiny události s <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.WorkbookBeforeSave> událostí.

    [!code-csharp[Trin_ExcelAddInTutorial#2](../vsto/codesnippet/CSharp/Trin_ExcelAddInTutorial/ThisAddIn.cs#2)]

   Chcete-li upravit sešit při jeho uložení, předchozí příklady kódu používají následující objekty:

- `Application`Pole `ThisAddIn` třídy `Application`Pole vrátí <xref:Microsoft.Office.Interop.Excel.Application> objekt, který představuje aktuální instanci aplikace Excel.

- `Wb`Parametr obslužné rutiny události <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.WorkbookBeforeSave> . `Wb`Parametr je <xref:Microsoft.Office.Interop.Excel.Workbook> objekt, který představuje uložený sešit. Další informace najdete v tématu [Přehled modelu objektů aplikace Excel](../vsto/excel-object-model-overview.md).

## <a name="test-the-project"></a>Testování projektu

### <a name="to-test-the-project"></a>Otestování projektu

1. Stisknutím klávesy **F5** Sestavte a spusťte projekt.

     Při sestavování projektu je kód zkompilován do sestavení, které je součástí výstupní složky sestavení pro projekt. Sada Visual Studio také vytvoří sadu položek registru, které umožní aplikaci Excel vyhledat a načíst doplněk VSTO a nakonfiguruje nastavení zabezpečení na vývojovém počítači, aby bylo možné doplněk VSTO spustit. Další informace najdete v tématu [sestavování řešení pro systém Office](../vsto/building-office-solutions.md).

2. V aplikaci Excel sešit uložte.

3. Ověřte, zda je do sešitu přidán následující text.

     **Tento text byl přidán pomocí kódu.**

4. Zavřete aplikaci Excel.

## <a name="clean-up-the-project"></a>Vyčištění projektu
 Po dokončení vývoje projektu odeberte sestavení doplňku VSTO, položky registru a nastavení zabezpečení z vývojového počítače. V opačném případě se doplněk VSTO bude dál spouštět pokaždé, když otevřete Excel na vývojovém počítači.

### <a name="to-clean-up-the-completed-project-on-your-development-computer"></a>Vyčištění dokončeného projektu ve vývojovém počítači

1. V aplikaci Visual Studio v nabídce **sestavení** klikněte na možnost **Vyčistit řešení**.

## <a name="next-steps"></a>Další kroky
 Teď, když jste vytvořili základní doplněk VSTO pro Excel, můžete získat další informace o tom, jak vyvíjet doplňky VSTO z těchto témat:

- Obecné úlohy programování, které můžete provádět v Doplňkech VSTO: [programový doplněk VSTO](../vsto/programming-vsto-add-ins.md).

- Úkoly programování, které jsou specifické pro doplňky Excelu VSTO: [Excelová řešení](../vsto/excel-solutions.md).

- Pomocí objektového modelu aplikace Excel: [Přehled modelu objektů aplikace Excel](../vsto/excel-object-model-overview.md).

- Přizpůsobení uživatelského rozhraní (UI) aplikace Excel, například přidáním vlastní karty na pás karet nebo vytvořením vlastního podokna úloh: [přizpůsobení uživatelského rozhraní systému Office](../vsto/office-ui-customization.md).

- Sestavování a ladění doplňků VSTO pro Excel: [sestavování řešení pro systém Office](../vsto/building-office-solutions.md).

- Nasazují se doplňky VSTO pro Excel: [nasazení řešení pro Office](../vsto/deploying-an-office-solution.md).

## <a name="see-also"></a>Viz také
- [Přehled vývoje řešení pro systém Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)
- [Řešení pro Excel](../vsto/excel-solutions.md)
- [Programové doplňky VSTO](../vsto/programming-vsto-add-ins.md)
- [Přehled modelu objektů aplikace Excel](../vsto/excel-object-model-overview.md)
- [Přizpůsobení uživatelského rozhraní systému Office](../vsto/office-ui-customization.md)
- [Sestavování řešení pro systém Office](../vsto/building-office-solutions.md)
- [Nasazení řešení pro systém Office](../vsto/deploying-an-office-solution.md)
- [Přehled šablon projektů Office](../vsto/office-project-templates-overview.md)
