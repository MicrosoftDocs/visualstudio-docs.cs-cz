---
title: Vytvoření prvního přizpůsobení na úrovni dokumentu pro Excel
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, creating your first project
- Excel [Office development in Visual Studio], creating your first project
- document-level customizations [Office development in Visual Studio], creating your first project
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 8d45461c7dab250cd43d7a25d8693658c7b8e164
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "74566986"
---
# <a name="walkthrough-create-your-first-document-level-customization-for-excel"></a>Návod: vytvoření prvního přizpůsobení na úrovni dokumentu pro Excel

  V tomto úvodním návodu se dozvíte, jak vytvořit přizpůsobení na úrovni dokumentu pro systém Microsoft Office Excel. Funkce, které vytvoříte v tomto druhu řešení, jsou k dispozici pouze v případě, že je otevřen konkrétní sešit. Přizpůsobení na úrovni dokumentu nemůžete použít k provádění změn v rámci aplikace, například zobrazení nové karty na pásu karet, když je otevřen libovolný sešit.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 Tento návod znázorňuje následující úlohy:

- Vytváření projektu excelového sešitu.

- Přidání textu do listu, který je hostován v návrháři sady Visual Studio.

- Psaní kódu, který používá objektový model aplikace Excel k přidání textu do přizpůsobeného listu při jeho otevření.

- Sestavení a spuštění projektu pro otestování.

- Vyčištění dokončeného projektu pro odebrání zbytečných souborů sestavení a nastavení zabezpečení z vývojového počítače.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Požadavky

 K dokončení tohoto návodu budete potřebovat následující komponenty:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] nebo [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)]:

## <a name="create-the-project"></a>Vytvoření projektu

### <a name="to-create-a-new-excel-workbook-project-in-visual-studio"></a>Vytvoření nového projektu excelového sešitu v aplikaci Visual Studio

1. Spustit [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

2. V nabídce **soubor** přejděte na příkaz **Nový**a klikněte na **projekt**.
::: moniker range="vs-2017"
3. V podokně šablony rozbalte položku **Visual C#** nebo **Visual Basic**a potom rozbalte položku **Office/SharePoint**.

4. V rozbaleném uzlu **Office/SharePoint** vyberte uzel **doplňky VSTO** .

5. V seznamu šablon projektu vyberte projekt Excel VSTO pro sešit.

6. Do pole **název** zadejte **FirstWorkbookCustomization**.

7. Klikněte na **OK**.

8. V **průvodci Visual Studio Tools for Office projektu**vyberte **vytvořit nový dokument** a klikněte na **OK**.
::: moniker-end
::: moniker range=">=vs-2019"
3. V dialogovém okně **vytvořit nový projekt** vyberte projekt **SEŠITU aplikace Excel VSTO** .

     [!INCLUDE[new-project-dialog-search](../vsto/includes/new-project-dialog-search-md.md)]

4. Klikněte na **Next** (Další).

5. Do pole **název** v dialogu **Konfigurovat nový projekt** zadejte **FirstWorkbookCustomization** a klikněte na **vytvořit**.

6. V **průvodci Visual Studio Tools for Office projektu**vyberte **vytvořit nový dokument** a klikněte na **OK**.
::: moniker-end
   - [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Vytvoří projekt **FirstWorkbookCustomization** a přidá následující soubory do projektu.

   - *FirstWorkbookCustomization*. xlsx – představuje excelový sešit v projektu. Obsahuje všechny listy a grafy.

   - List1 (soubor *. vb* pro Visual Basic nebo soubor *. cs* pro Visual C#) – list, který poskytuje návrhovou plochu a kód pro první list v sešitu. Další informace najdete v tématu [položka hostitele na listu](../vsto/worksheet-host-item.md).

   - List2 (soubor *. vb* pro Visual Basic nebo soubor *. cs* pro Visual C#) – list, který poskytuje návrhovou plochu a kód pro druhý list v sešitu.

   - Sheet3 (soubor *. vb* pro soubor Visual Basic nebo *. cs* pro jazyk Visual C#) – list, který poskytuje návrhovou plochu a kód pro třetí list v sešitu.

   - ThisWorkbook (soubor *. vb* pro Visual Basic nebo soubor *. cs* pro Visual C#) – obsahuje návrhovou plochu a kód pro přizpůsobení na úrovni sešitu. Další informace najdete v tématu [položka hostitele sešitu](../vsto/workbook-host-item.md).

     Soubor kódu List1 se automaticky otevře v návrháři.

## <a name="close-and-reopen-worksheets-in-the-designer"></a>Zavření a opětovné otevření listů v Návrháři

 Pokud záměrně nebo omylem zavřete sešit nebo list v Návrháři během vývoje projektu, můžete ho znovu otevřít.

### <a name="to-close-and-reopen-a-worksheet-in-the-designer"></a>Zavření a opětovné otevření listu v Návrháři

1. Zavřete sešit kliknutím na tlačítko **Zavřít** (X) v okně návrháře.

2. V **Průzkumník řešení**klikněte pravým tlačítkem myši na soubor s kódem **List1** a klikněte na tlačítko **Návrhář zobrazení**.

     \- ani

     V **Průzkumník řešení**dvakrát klikněte na soubor s kódem **List1** .

## <a name="add-text-to-a-worksheet-in-the-designer"></a>Přidání textu do listu v Návrháři

 Můžete navrhnout uživatelské rozhraní (UI) vlastního nastavení úpravou listu, který je otevřen v návrháři. Například můžete přidat text do buněk, použít vzorce nebo přidat ovládací prvky aplikace Excel. Další informace o použití návrháře naleznete [v tématu projekty sady Office v prostředí Visual Studio](../vsto/office-projects-in-the-visual-studio-environment.md).

### <a name="to-add-text-to-a-worksheet-by-using-the-designer"></a>Přidání textu do listu pomocí návrháře

1. Na listu, který je otevřen v návrháři, vyberte buňku **a1**a zadejte následující text.

     **Tento text byl přidán pomocí návrháře.**

> [!WARNING]
> Pokud přidáte tento řádek textu do buňky **a2**, bude v tomto příkladu přepsán jiným kódem.

## <a name="add-text-to-a-worksheet-programmatically"></a>Přidání textu do listu prostřednictvím kódu programu

 Dále přidejte kód do souboru kódu List1. Nový kód používá objektový model aplikace Excel k přidání druhého řádku textu do sešitu. Ve výchozím nastavení soubor s kódem List1 obsahuje následující generovaný kód:

- Částečná definice `Sheet1` třídy, která představuje programovací model listu a poskytuje přístup k objektovému modelu aplikace Excel. Další informace najdete v článku Přehled [hostitelského](../vsto/worksheet-host-item.md) a [objektového modelu aplikace Word](../vsto/word-object-model-overview.md). Zbytek `Sheet1` třídy je definován ve skrytém souboru kódu, který byste neměli upravovat.

- `Sheet1_Startup` `Sheet1_Shutdown` Obslužné rutiny události a. Tyto obslužné rutiny události jsou volány, když aplikace Excel načte a uvolní vaše přizpůsobení. Tyto obslužné rutiny událostí použijte k inicializaci vlastního nastavení po jeho načtení a k vyčištění prostředků používaných vaším přizpůsobením při jeho uvolnění. Další informace najdete v tématu [události v projektech Office](../vsto/events-in-office-projects.md).

### <a name="to-add-a-second-line-of-text-to-the-worksheet-by-using-code"></a>Přidání druhého řádku textu do listu pomocí kódu

1. V **Průzkumník řešení**klikněte pravým tlačítkem na **List1**a pak klikněte na **Zobrazit kód**.

     Soubor kódu se otevře v aplikaci Visual Studio.

2. Proměnnou `Sheet1_Startup` obslužné rutiny události nahraďte následujícím kódem. Při otevření List1 přidá tento kód druhý řádek textu do listu.

     [!code-csharp[Trin_ExcelWorkbookTutorial#1](../vsto/codesnippet/CSharp/Trin_ExcelWorkbookTutorial/Sheet1.cs#1)]
     [!code-vb[Trin_ExcelWorkbookTutorial#1](../vsto/codesnippet/VisualBasic/Trin_ExcelWorkbookTutorial/Sheet1.vb#1)]

## <a name="test-the-project"></a>Testování projektu

### <a name="to-test-your-workbook"></a>Test sešitu

1. Stisknutím klávesy **F5** Sestavte a spusťte projekt.

     Při sestavování projektu je kód zkompilován do sestavení, které je přidruženo k sešitu. Visual Studio vloží kopii sešitu a sestavení do výstupní složky sestavení pro projekt a nakonfiguruje nastavení zabezpečení na vývojovém počítači, aby bylo možné vlastní nastavení spustit. Další informace najdete v tématu [sestavování řešení pro systém Office](../vsto/building-office-solutions.md).

2. V sešitu ověřte, zda se zobrazí následující text.

     **Tento text byl přidán pomocí návrháře.**

     **Tento text byl přidán pomocí kódu.**

3. Zavřete sešit.

## <a name="clean-up-the-project"></a>Vyčištění projektu

 Po dokončení vývoje projektu byste měli odebrat soubory z výstupní složky sestavení a nastavení zabezpečení, které vytvořil proces sestavení.

### <a name="to-clean-up-the-completed-project-on-your-development-computer"></a>Vyčištění dokončeného projektu ve vývojovém počítači

1. V aplikaci Visual Studio v nabídce **sestavení** klikněte na možnost **Vyčistit řešení**.

## <a name="next-steps"></a>Další kroky

 Teď, když jste vytvořili základní přizpůsobení na úrovni dokumentu pro Excel, si můžete přečíst další informace o vývoji vlastních nastavení z těchto témat:

- Obecné programovací úkoly, které můžete provádět v přizpůsobení na úrovni dokumentu: [přizpůsobení na úrovni dokumentu programu](../vsto/programming-document-level-customizations.md).

- Úkoly programování, které jsou specifické pro přizpůsobení na úrovni dokumentu v aplikaci Excel: [řešení aplikace Excel](../vsto/excel-solutions.md).

- Pomocí objektového modelu aplikace Excel: [Přehled modelu objektů aplikace Excel](../vsto/excel-object-model-overview.md).

- Přizpůsobení uživatelského rozhraní aplikace Excel, například přidáním vlastní karty na pás karet nebo vytvořením vlastního podokna akcí: [přizpůsobení uživatelského rozhraní systému Office](../vsto/office-ui-customization.md).

- Použití rozšířených objektů aplikace Excel poskytovaných vývojářskými nástroji Office v sadě Visual Studio k provádění úloh, které není možné pomocí modelu objektu aplikace Excel (například hostování spravovaných ovládacích prvků na dokumentech a vazba ovládacích prvků aplikace Excel na data pomocí modelu model Windows Forms datové vazby): [Automatizujte aplikaci Excel pomocí rozšířených objektů](../vsto/automating-excel-by-using-extended-objects.md).

- Sestavování a ladění přizpůsobení na úrovni dokumentu pro aplikaci Excel: [sestavování řešení pro systém Office](../vsto/building-office-solutions.md).

- Nasazení přizpůsobení na úrovni dokumentu pro Excel: [nasaďte řešení pro Office](../vsto/deploying-an-office-solution.md).

## <a name="see-also"></a>Viz také

- [Přehled vývoje řešení pro systém Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)
- [Řešení pro Excel](../vsto/excel-solutions.md)
- [Přizpůsobení na úrovni dokumentu programu](../vsto/programming-document-level-customizations.md)
- [Přehled modelu objektů aplikace Excel](../vsto/excel-object-model-overview.md)
- [Automatizace Excelu pomocí rozšířených objektů](../vsto/automating-excel-by-using-extended-objects.md)
- [Přizpůsobení uživatelského rozhraní systému Office](../vsto/office-ui-customization.md)
- [Sestavování řešení pro systém Office](../vsto/building-office-solutions.md)
- [Nasazení řešení pro systém Office](../vsto/deploying-an-office-solution.md)
- [Přehled šablon projektů Office](../vsto/office-project-templates-overview.md)
