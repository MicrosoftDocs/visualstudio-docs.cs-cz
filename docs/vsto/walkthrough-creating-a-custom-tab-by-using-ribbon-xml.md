---
title: 'Návod: Vytvoření vlastní karty pomocí kódu XML pásu karet'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Ribbon [Office development in Visual Studio], tabs
- customizing the Ribbon, tabscustom Ribbon, tabs
- Ribbon [Office development in Visual Studio], XML
- XML [Office development in Visual Studio], Ribbon
- Ribbon [Office development in Visual Studio], customizing
- Custom tab [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: e05bd9173b83ec3303a058dcf61ea48a7ef7675c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "64785938"
---
# <a name="walkthrough-create-a-custom-tab-by-using-ribbon-xml"></a>Návod: Vytvoření vlastní karty pomocí kódu XML pásu karet
  Tento návod ukazuje, jak vytvořit vlastní kartu pásu karet pomocí položky **pásu karet (XML)** .

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

 Tento návod znázorňuje následující úlohy:

- Přidání tlačítek na kartu **Doplňky** Karta **Doplňky** je výchozí karta, která je definovaná v souboru XML pásu karet.

- Automatizace systém Microsoft Office Wordu pomocí tlačítek na kartě **Doplňky** .

> [!NOTE]
> Váš počítač může v následujících pokynech zobrazovat odlišné názvy nebo umístění některých prvků uživatelského rozhraní sady Visual Studio. Tyto prvky jsou určeny edicí sady Visual Studio a použitým nastavením. Další informace najdete v tématu [Přizpůsobení integrovaného vývojového prostředí (IDE) sady Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Předpoklady
 K dokončení tohoto návodu budete potřebovat následující komponenty:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- Microsoft Word.

## <a name="create-the-project"></a>Vytvoření projektu
 Prvním krokem je vytvoření projektu doplňku VSTO aplikace Word. Později budete přizpůsobovat kartu **Doplňky** v tomto dokumentu.

### <a name="to-create-a-new-project"></a>Vytvoření nového projektu

1. Vytvořte projekt **doplňku aplikace Word** s názvem **MyRibbonAddIn**.

     Další informace najdete v tématu [Postupy: vytváření projektů pro systém Office v sadě Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] otevře soubor kódu **ThisAddIn.cs** nebo **ThisAddIn. vb** a přidá projekt **MyRibbonAddIn** do **Průzkumník řešení**.

## <a name="create-the-vsto-add-ins-tab"></a>Vytvoření karty VSTO pro Doplňky
 Kartu **Doplňky** vytvoříte tak, že do svého projektu přidáte položku **pásu karet (XML)** . Později v tomto návodu přidáte některá tlačítka na tuto kartu.

### <a name="to-create-the-add-ins-tab"></a>Vytvoření karty Doplňky

1. V nabídce **projekt** klikněte na příkaz **Přidat novou položku**.

2. V dialogovém okně **Přidat novou položku** vyberte možnost **pás karet (XML)**.

3. Změňte název nového pásu karet na **MyRibbon**a klikněte na **Přidat**.

     V návrháři se otevře soubor **MyRibbon.cs** nebo **MyRibbon. vb** . Do projektu se přidá také soubor XML s názvem **MyRibbon.xml** .

4. V **Průzkumník řešení**klikněte pravým tlačítkem myši na **ThisAddIn.cs** nebo **ThisAddIn. vb**a pak klikněte na **Zobrazit kód**.

5. Do třídy **ThisAddIn** přidejte následující kód. Tento kód přepíše `CreateRibbonExtensibilityObject` metodu a vrátí třídu XML pásu karet do aplikace sady Office.

     [!code-csharp[Trin_Ribbon_Custom_Tab_XML#1](../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab_XML_O12/ThisAddIn.cs#1)]
     [!code-vb[Trin_Ribbon_Custom_Tab_XML#1](../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab_XML_O12/ThisAddIn.vb#1)]

6. V **Průzkumník řešení**klikněte pravým tlačítkem na projekt **MyRibbonAddIn** a pak klikněte na **sestavit**. Ověřte, že se projekt vytváří bez chyb.

## <a name="add-buttons-to-the-add-ins-tab"></a>Přidat tlačítka na kartu Doplňky
 Cílem tohoto doplňku VSTO je poskytnout uživatelům způsob, jak do aktivního dokumentu přidat často používaný text a konkrétní tabulku. Chcete-li zadat uživatelské rozhraní, přidejte na kartu **Doplňky** dvě tlačítka úpravou souboru XML pásu karet. Později v tomto návodu budete definovat metody zpětného volání pro tlačítka. Další informace o souboru XML pásu karet naleznete v tématu [XML pásu karet](../vsto/ribbon-xml.md).

### <a name="to-add-buttons-to-the-add-ins-tab"></a>Přidání tlačítek na kartu Doplňky

1. V **Průzkumník řešení**klikněte pravým tlačítkem na **MyRibbon.xml** a pak klikněte na **otevřít**.

2. Nahraďte obsah elementu **karty** následujícím kódem XML. Tento kód XML změní popisek výchozí skupiny ovládacích prvků na **obsah**a přidá dvě nová tlačítka s popisky **Vložit text** a **Vložit tabulku**.

    ```xml
    <tab idMso="TabAddIns">
        <group id="ContentGroup" label="Content">
            <button id="textButton" label="Insert Text"
                 screentip="Text" onAction="OnTextButton"
                 supertip="Inserts text at the cursor location."/>
            <button id="tableButton" label="Insert Table"
                 screentip="Table" onAction="OnTableButton"
                 supertip="Inserts a table at the cursor location."/>
        </group>
    </tab>
    ```

## <a name="automate-the-document-by-using-the-buttons"></a>Automatizace dokumentu pomocí tlačítek
 Chcete-li `onAction` provést akce, když na ně uživatel klikne, je nutné přidat metody zpětného volání pro tlačítka **Vložit text** a **Vložit tabulku** . Další informace o metodách zpětného volání pro ovládací prvky pásu karet naleznete v tématu [XML pásu karet](../vsto/ribbon-xml.md).

### <a name="to-add-callback-methods-for-the-buttons"></a>Přidání metod zpětného volání pro tlačítka

1. V **Průzkumník řešení**klikněte pravým tlačítkem myši na **MyRibbon.cs** nebo **MyRibbon. vb**a pak klikněte na **otevřít**.

2. Do horní části souboru **MyRibbon.cs** nebo **MyRibbon. vb** přidejte následující kód. Tento kód vytvoří alias pro <xref:Microsoft.Office.Interop.Word> obor názvů.

     [!code-csharp[Trin_RibbonButtons#1](../vsto/codesnippet/CSharp/Trin_RibbonButtons/MyRibbon.cs#1)]
     [!code-vb[Trin_RibbonButtons#1](../vsto/codesnippet/VisualBasic/Trin_RibbonButtons/MyRibbon.vb#1)]

3. Do třídy přidejte následující metodu `MyRibbon` . Toto je metoda zpětného volání pro tlačítko **Vložit text** , která přidá řetězec do aktivního dokumentu v aktuálním umístění kurzoru.

     [!code-csharp[Trin_Ribbon_Custom_Tab_XML#2](../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab_XML_O12/MyRibbon.cs#2)]
     [!code-vb[Trin_Ribbon_Custom_Tab_XML#2](../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab_XML_O12/MyRibbon.vb#2)]

4. Do třídy přidejte následující metodu `MyRibbon` . Toto je metoda zpětného volání pro tlačítko pro **vložení tabulky** , která přidá tabulku do aktivního dokumentu v aktuálním umístění kurzoru.

     [!code-csharp[Trin_Ribbon_Custom_Tab_XML#3](../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab_XML_O12/MyRibbon.cs#3)]
     [!code-vb[Trin_Ribbon_Custom_Tab_XML#3](../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab_XML_O12/MyRibbon.vb#3)]

## <a name="testing-the-vsto-add-in"></a>Testování doplňku VSTO
 Při spuštění projektu se otevře aplikace Word a na pásu karet se zobrazí karta s názvem **Doplňky** . Kliknutím na tlačítko **Vložit text** a **Vložit tabulku** na kartě **Doplňky** se kód otestuje.

### <a name="to-test-your-vsto-add-in"></a>Testování doplňku VSTO

1. Stisknutím klávesy **F5** spusťte projekt.

2. Potvrďte, že se na pásu karet zobrazuje karta **Doplňky** .

3. Klikněte na kartu **Doplňky** .

4. Potvrďte, že je na pásu karet zobrazená skupina **obsahu** .

5. Klikněte na tlačítko **Vložit text** ve skupině **obsahu** .

     Do dokumentu se přidá řetězec v aktuálním umístění kurzoru.

6. Klikněte na tlačítko **Vložit tabulku** ve skupině **obsahu** .

     Do dokumentu se přidá tabulka v aktuálním umístění kurzoru.

## <a name="next-steps"></a>Další kroky
 Další informace o tom, jak přizpůsobit uživatelské rozhraní Office, najdete v těchto tématech:

- Přizpůsobení pásu karet jiné aplikace Office. Další informace o aplikacích, které podporují přizpůsobení pásu karet, najdete v tématu [Přehled pásu karet](../vsto/ribbon-overview.md).

- Přizpůsobte pás karet aplikace Office pomocí Návrháře pásu karet. Další informace najdete v tématu [Návrhář pásu karet](../vsto/ribbon-designer.md).

- Vytvoří podokno vlastní akce. Další informace najdete v tématu [Přehled podokna akcí](../vsto/actions-pane-overview.md).

- Přizpůsobení uživatelského rozhraní systém Microsoft Office Outlooku pomocí oblastí formuláře Outlooku Další informace najdete v tématu [Návod: návrh oblasti formuláře aplikace Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md).

## <a name="see-also"></a>Viz také
- [Přehled pásu karet](../vsto/ribbon-overview.md)
- [Pás karet – XML](../vsto/ribbon-xml.md)
- [Návod: Vytvoření vlastní karty pomocí Návrháře pásu karet](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)
