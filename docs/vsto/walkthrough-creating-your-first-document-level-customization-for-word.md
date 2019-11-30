---
title: Vytvoření prvního přizpůsobení na úrovni dokumentu pro Word
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, creating your first project
- Word [Office development in Visual Studio], creating your first project
- document-level customizations [Office development in Visual Studio], creating your first project
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: c07c3257b8df0e671941ae08bc3738350e017a8a
ms.sourcegitcommit: 3ba2968a4b44643482aadad4d50e1a55bb36b136
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/28/2019
ms.locfileid: "74567009"
---
# <a name="walkthrough-create-your-first-document-level-customization-for-word"></a>Návod: vytvoření prvního přizpůsobení na úrovni dokumentu pro Word

  V tomto úvodním návodu se dozvíte, jak vytvořit přizpůsobení na úrovni dokumentu pro systém Microsoft Office Word. Funkce, které vytvoříte v tomto druhu řešení, jsou k dispozici pouze v případě, že je otevřen konkrétní dokument. Přizpůsobení na úrovni dokumentu nelze použít k provádění změn v rámci aplikace, například zobrazení nové karty na pásu karet, když je otevřen libovolný dokument.

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

 Tento návod znázorňuje následující úlohy:

- Vytvoření projektu dokumentu aplikace Word.

- Přidání textu do dokumentu, který je hostován v návrháři aplikace Visual Studio.

- Psaní kódu, který používá objektový model aplikace Word k přidání textu do přizpůsobeného dokumentu při jeho otevření.

- Sestavení a spuštění projektu pro otestování.

- Vyčištění projektu pro odebrání zbytečných souborů sestavení a nastavení zabezpečení z vývojového počítače.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Požadavky

 K dokončení tohoto návodu budete potřebovat následující komponenty:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- Microsoft Word

## <a name="create-the-project"></a>Vytvoření projektu

### <a name="to-create-a-new-word-document-project-in-visual-studio"></a>Vytvoření nového projektu wordového dokumentu v aplikaci Visual Studio

1. Spusťte [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

2. V nabídce **soubor** přejděte na příkaz **Nový**a klikněte na **projekt**.
::: moniker range="vs-2017"
3. V podokně šablony rozbalte položku **Visual C#**  nebo **Visual Basic**a potom rozbalte položku **Office/SharePoint**.

4. V rozbaleném uzlu **Office/SharePoint** vyberte uzel **doplňky VSTO** .

5. V seznamu šablon projektu vyberte projekt dokumentu aplikace VSTO pro Word.

6. Do pole **název** zadejte **FirstDocumentCustomization**.

7. Klikněte na tlačítko **OK**.

8. V **průvodci Visual Studio Tools for Office projektu**vyberte **vytvořit nový dokument** a klikněte na **OK**.
::: moniker-end
::: moniker range=">=vs-2019"
3. V dialogovém okně **vytvořit nový projekt** vyberte projekt **dokumentů aplikace Word VSTO** .

     [!INCLUDE[new-project-dialog-search](../vsto/includes/new-project-dialog-search-md.md)]

4. Klikněte na tlačítko **Další**.

5. Do pole **název** v dialogu **Konfigurovat nový projekt** zadejte **FirstWorkbookCustomization** a klikněte na **vytvořit**.

6. V **průvodci Visual Studio Tools for Office projektu**vyberte **vytvořit nový dokument** a klikněte na **OK**.
::: moniker-end
   - [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] vytvoří projekt **FirstDocumentCustomization** a do projektu přidá dokument **FirstDocumentCustomization** a soubor s kódem ThisDocument. Dokument **FirstDocumentCustomization** se automaticky otevře v návrháři.

## <a name="close-and-reopen-the-document-in-the-designer"></a>Zavřít a znovu otevřít dokument v Návrháři

 Pokud záměrně nebo omylem zavřete dokument v Návrháři během vývoje projektu, můžete ho znovu otevřít.

### <a name="to-close-and-reopen-the-document-in-the-designer"></a>Zavření a opětovné otevření dokumentu v Návrháři

1. Zavřete dokument kliknutím na tlačítko **Zavřít** (X) v okně návrháře.

2. V **Průzkumník řešení**klikněte pravým tlačítkem myši na soubor kódu **ThisDocument** a klikněte na tlačítko **Návrhář zobrazení**.

     \- nebo-

     V **Průzkumník řešení**dvakrát klikněte na soubor kódu **ThisDocument** .

## <a name="add-text-to-the-document-in-the-designer"></a>Přidání textu do dokumentu v Návrháři

 Můžete navrhnout uživatelské rozhraní (UI) vlastního nastavení úpravou dokumentu, který je otevřen v návrháři. Můžete například přidat text, tabulky nebo ovládací prvky aplikace Word. Další informace o použití návrháře naleznete [v tématu projekty sady Office v prostředí Visual Studio](../vsto/office-projects-in-the-visual-studio-environment.md).

### <a name="to-add-text-to-your-document-by-using-the-designer"></a>Přidání textu do dokumentu pomocí návrháře

1. V dokumentu, který je otevřen v návrháři, zadejte následující text.

     **Tento text byl přidán pomocí návrháře.**

## <a name="add-text-to-the-document-programmatically"></a>Přidat text do dokumentu programově

 Dále přidejte kód do souboru kódu ThisDocument. Nový kód používá objektový model aplikace Word k přidání druhého odstavce textu do dokumentu. Ve výchozím nastavení soubor kódu ThisDocument obsahuje následující generovaný kód:

- Částečná definice `ThisDocument` třídy, která představuje programovací model dokumentu a poskytuje přístup k objektovému modelu aplikace Word. Další informace najdete v tématu Přehled objektů [hostitele dokumentu](../vsto/document-host-item.md) a [objektového modelu aplikace Word](../vsto/word-object-model-overview.md). Zbytek `ThisDocument` třídy je definován ve skrytém souboru kódu, který byste neměli upravovat.

- Obslužné rutiny událostí `ThisDocument_Startup` a `ThisDocument_Shutdown`. Tyto obslužné rutiny události jsou volány při otevření a zavření dokumentu. Tyto obslužné rutiny událostí použijte k inicializaci vlastního nastavení při otevření dokumentu a k vyčištění prostředků používaných vaším přizpůsobením při zavření dokumentu. Další informace najdete v tématu [události v projektech Office](../vsto/events-in-office-projects.md).

### <a name="to-add-a-second-paragraph-of-text-to-the-document-by-using-code"></a>Přidání druhého odstavce textu do dokumentu pomocí kódu

1. V **Průzkumník řešení**klikněte pravým tlačítkem na **ThisDocument**a pak klikněte na **Zobrazit kód**.

     Soubor kódu se otevře v aplikaci Visual Studio.

2. `ThisDocument_Startup` obslužnou rutinu události nahraďte následujícím kódem. Když je dokument otevřen, tento kód přidá druhý odstavec textu do dokumentu.

     [!code-vb[Trin_WordDocumentTutorial#1](../vsto/codesnippet/VisualBasic/FirstDocumentCustomization/ThisDocument.vb#1)]
     [!code-csharp[Trin_WordDocumentTutorial#1](../vsto/codesnippet/CSharp/FirstDocumentCustomization/ThisDocument.cs#1)]

    > [!NOTE]
    > Tento kód používá hodnotu indexu 1 pro přístup k prvnímu odstavci ve vlastnosti <xref:Microsoft.Office.Tools.Word.Document.Paragraphs%2A>. I když Visual Basic a C# vizuální použití polí na bázi 0, dolní hranice pole většiny kolekcí v objektovém modelu aplikace Word je 1. Další informace najdete v tématu [psaní kódu v řešeních pro systém Office](../vsto/writing-code-in-office-solutions.md).

## <a name="test-the-project"></a>Testování projektu

### <a name="to-test-your-document"></a>Testování dokumentu

1. Stisknutím klávesy **F5** Sestavte a spusťte projekt.

     Při sestavování projektu je kód zkompilován do sestavení, které je přidruženo k dokumentu. Visual Studio vloží kopii dokumentu a sestavení do výstupní složky sestavení pro projekt a nakonfiguruje nastavení zabezpečení na vývojovém počítači, aby bylo možné vlastní nastavení spustit. Další informace najdete v tématu [sestavování řešení pro systém Office](../vsto/building-office-solutions.md).

2. V dokumentu ověřte, zda se zobrazí následující text.

     **Tento text byl přidán pomocí návrháře.**

     **Tento text byl přidán pomocí kódu.**

3. Zavřete dokument.

## <a name="clean-up-the-project"></a>Vyčištění projektu

 Po dokončení vývoje projektu byste měli odebrat soubory z výstupní složky sestavení a nastavení zabezpečení, které vytvořil proces sestavení.

### <a name="to-clean-up-the-completed-project-on-your-development-computer"></a>Vyčištění dokončeného projektu ve vývojovém počítači

1. V aplikaci Visual Studio v nabídce **sestavení** klikněte na možnost **Vyčistit řešení**.

## <a name="next-steps"></a>Další kroky

 Teď, když jste vytvořili základní přizpůsobení na úrovni dokumentu pro Word, si můžete přečíst další informace o vývoji vlastních nastavení z těchto témat:

- Obecné programovací úkoly, které můžete provádět v přizpůsobení na úrovni dokumentu: [přizpůsobení na úrovni dokumentu programu](../vsto/programming-document-level-customizations.md).

- Úkoly programování, které jsou specifické pro přizpůsobení na úrovni dokumentu pro Word: [řešení pro Word](../vsto/word-solutions.md)

- Použití objektového modelu aplikace Word: [Přehled objektového modelu aplikace Word](../vsto/word-object-model-overview.md).

- Přizpůsobení uživatelského rozhraní aplikace Word, například přidáním vlastní karty na pás karet nebo vytvořením vlastního podokna akcí: [přizpůsobení uživatelského rozhraní systému Office](../vsto/office-ui-customization.md).

- Použití rozšířených objektů aplikace Word poskytovaných řešeními Office v sadě Visual Studio k provádění úloh, které není možné pomocí objektového modelu aplikace Word (například hostování spravovaných ovládacích prvků na dokumentech a vázání ovládacích prvků aplikace Word na data pomocí modelu model Windows Forms datové vazby): [Automatizujte Word pomocí rozšířených objektů](../vsto/automating-word-by-using-extended-objects.md).

- Sestavování a ladění přizpůsobení na úrovni dokumentu pro Word: [sestavování řešení pro systém Office](../vsto/building-office-solutions.md).

- Nasazení přizpůsobení na úrovni dokumentu pro Word: [nasazení řešení pro Office](../vsto/deploying-an-office-solution.md).

## <a name="see-also"></a>Viz také:

- [Přehled &#40;vývoje řešení pro systém Office VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)
- [Řešení pro Word](../vsto/word-solutions.md)
- [Přizpůsobení na úrovni dokumentu programu](../vsto/programming-document-level-customizations.md)
- [Přehled modelu objektů aplikace Word](../vsto/word-object-model-overview.md)
- [Automatizace Wordu pomocí rozšířených objektů](../vsto/automating-word-by-using-extended-objects.md)
- [Přizpůsobení uživatelského rozhraní systému Office](../vsto/office-ui-customization.md)
- [Sestavování řešení pro systém Office](../vsto/building-office-solutions.md)
- [Nasazení řešení pro systém Office](../vsto/deploying-an-office-solution.md)
- [Přehled šablon projektů Office](../vsto/office-project-templates-overview.md)
