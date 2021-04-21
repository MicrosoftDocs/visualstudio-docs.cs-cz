---
title: 'Návod: vložení textu do dokumentu z podokna akcí'
description: Vytvoří podokno akcí v dokumentu aplikace Microsoft Word. Přečtěte si, že podokno akce obsahuje dva ovládací prvky, které shromažďují vstup a pak odesílají text do dokumentu.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- smart documents [Office development in Visual Studio], creating in Word
- smart documents [Office development in Visual Studio], adding controls
- actions panes [Office development in Visual Studio], creating in Word
- actions panes [Office development in Visual Studio], adding controls
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 1ac42954e32b30a293abbe031218213948fb103a
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/21/2021
ms.locfileid: "107824975"
---
# <a name="walkthrough-insert-text-into-a-document-from-an-actions-pane"></a>Návod: vložení textu do dokumentu z podokna akcí
  Tento návod ukazuje, jak vytvořit podokno akcí v dokumentu aplikace systém Microsoft Office Word. Podokno akce obsahuje dva ovládací prvky, které shromažďují vstup a pak odesílají text do dokumentu.

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

 Tento návod znázorňuje následující úlohy:

- Navrhněte rozhraní pomocí model Windows Forms ovládacích prvků na ovládacím prvku podokna akcí.

- Po otevření aplikace zobrazit podokno akcí.

> [!NOTE]
> Váš počítač může v následujících pokynech zobrazovat odlišné názvy nebo umístění některých prvků uživatelského rozhraní sady Visual Studio. Tyto prvky jsou určeny edicí sady Visual Studio a použitým nastavením. Další informace najdete v tématu [Přizpůsobení integrovaného vývojového prostředí (IDE) sady Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Požadavky
 K dokončení tohoto návodu budete potřebovat následující komponenty:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] nebo [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)]:

## <a name="create-the-project"></a>Vytvoření projektu
 Prvním krokem je vytvoření projektu wordového dokumentu.

### <a name="to-create-a-new-project"></a>Vytvoření nového projektu

1. Vytvořte projekt wordového dokumentu pomocí podokna název **Moje základní akce**. V průvodci vyberte možnost **vytvořit nový dokument**. Další informace najdete v tématu [Postupy: vytváření projektů pro systém Office v sadě Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     Visual Studio otevře nový wordový dokument v návrháři a přidá projekt **základní akce podokna akcí** do **Průzkumník řešení**.

## <a name="add-text-and-bookmarks-to-the-document"></a>Přidat text a záložky do dokumentu
 V podokně akce bude v dokumentu odeslán text do záložek. Pro návrh dokumentu zadejte nějaký text pro vytvoření základního formuláře.

### <a name="to-add-text-to-your-document"></a>Přidání textu do dokumentu

1. Do dokumentu aplikace Word zadejte následující text:

    **21. března 2008**

    **Název**

    **Adresa**

    **Toto je příklad základního podokna akcí ve Wordu.**

   <xref:Microsoft.Office.Tools.Word.Bookmark>Ovládací prvek lze do dokumentu přidat přetažením ze **sady nástrojů** v aplikaci Visual Studio nebo pomocí dialogového okna **Záložka** v aplikaci Word.

### <a name="to-add-a-bookmark-control-to-your-document"></a>Přidání ovládacího prvku záložka do dokumentu

1. Z karty **ovládací prvky aplikace Word** v **panelu nástrojů** přetáhněte <xref:Microsoft.Office.Tools.Word.Bookmark> ovládací prvek do dokumentu.

     Zobrazí se dialogové okno **Přidat ovládací prvek záložky** .

2. Vyberte **název** slova bez výběru značky odstavce a klikněte na tlačítko **OK**.

    > [!NOTE]
    > Znak odstavce by měl být mimo záložku. Pokud v dokumentu nejsou viditelné znaky odstavce, klikněte na nabídku **nástroje** , přejděte systém Microsoft Office na příkaz **Nástroje aplikace Word** a pak klikněte na tlačítko **Možnosti**. Klikněte na kartu **zobrazení** a zaškrtněte políčko **označení odstavce** v části **značky formátování** v dialogovém okně **Možnosti** .

3. V okně **vlastnosti** změňte vlastnost **název** vlastnosti **bookmark1** na hodnotu **Zobrazit**.

4. Vyberte **adresu** slova bez výběru značky odstavce.

5. Na kartě **vložení** na pásu karet ve skupině **odkazy** klikněte na možnost **Záložka**.

6. V dialogovém **okně záložka** zadejte do pole **název záložky** **ShowAddress** a klikněte na tlačítko **Přidat**.

## <a name="add-controls-to-the-actions-pane"></a>Přidání ovládacích prvků do podokna akce
 Chcete-li navrhnout rozhraní podokna akce, přidejte ovládací prvek podokna akce do projektu a poté přidejte ovládací prvky model Windows Forms do ovládacího prvku podokno akcí.

### <a name="to-add-an-actions-pane-control"></a>Přidání ovládacího prvku podokna akce

1. Vyberte projekt **Moje základní akce** v **Průzkumník řešení**.

2. V nabídce **projekt** klikněte na příkaz **Přidat novou položku**.

3. V dialogovém okně **Přidat novou položku** klikněte na položku **ovládací prvek podokno akce**, pojmenujte ovládací prvek **InsertTextControl** a klikněte na tlačítko **Přidat**.

#### <a name="to-add-windows-form-controls-to-the-actions-pane-control"></a>Přidání ovládacích prvků Windows Form do ovládacího prvku podokno akcí

1. Pokud ovládací prvek podokno akce není viditelný v návrháři, poklikejte na **InsertTextControl**.

2. Na kartě **běžné ovládací prvky** **panelu nástrojů** přetáhněte ovládací prvek **popisek** do ovládacího prvku podokno akcí.

3. Změňte vlastnost **text** ovládacího prvku popisek na **název**.

4. Do ovládacího prvku podokno akcí přidejte ovládací prvek **TextBox** a změňte následující vlastnosti.

    |Vlastnost|Hodnota|
    |--------------|-----------|
    |**Název**|**getName**|
    |**Velikost**|**130, 20**|

5. Přidejte do ovládacího prvku podokno akcí druhý ovládací prvek **popisek** a změňte vlastnost **text** na hodnotu **adresa**.

6. Přidejte druhý ovládací prvek **TextBox** do ovládacího prvku podokno akcí a změňte následující vlastnosti.

    |Vlastnost|Hodnota|
    |--------------|-----------|
    |**Název**|**GetAddress –**|
    |**Přijmout návrat**|**True**|
    |**Multiline**|**True**|
    |**Velikost**|**130, 40**|

7. Přidejte ovládací prvek **tlačítko** do ovládacího prvku podokno akcí a změňte následující vlastnosti.

    |Vlastnost|Hodnota|
    |--------------|-----------|
    |**Název**|**addText**|
    |**Text**|**Insert**|

## <a name="add-code-to-insert-text-into-the-document"></a>Přidat kód pro vložení textu do dokumentu
 V podokně akce napište kód, který vloží text z textových polí do příslušných <xref:Microsoft.Office.Tools.Word.Bookmark> ovládacích prvků v dokumentu. Třídu můžete použít `Globals` pro přístup k ovládacím prvkům na dokumentu z ovládacích prvků v podokně akce. Další informace najdete v tématu [globální přístup k objektům v projektech Office](../vsto/global-access-to-objects-in-office-projects.md).

### <a name="to-insert-text-from-the-actions-pane-in-a-bookmark-in-the-document"></a>Vložení textu z podokna akce na záložce v dokumentu

1. Do <xref:System.Windows.Forms.Control.Click> obslužné rutiny události tlačítka **addText** přidejte následující kód.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/InsertTextControl.cs" id="Snippet8":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/InsertTextControl.vb" id="Snippet8":::

2. V jazyce C# je nutné přidat obslužnou rutinu události pro kliknutí na tlačítko. Tento kód lze umístit do `InsertTextControl` konstruktoru po volání `InitializeComponent` . Informace o vytváření obslužných rutin událostí najdete v tématu [Postupy: vytváření obslužných rutin událostí v projektech pro systém Office](../vsto/how-to-create-event-handlers-in-office-projects.md).

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/InsertTextControl.cs" id="Snippet9":::

## <a name="add-code-to-show-the-actions-pane"></a>Přidat kód pro zobrazení podokna akce
 Chcete-li zobrazit podokno akcí, přidejte ovládací prvek, který jste vytvořili do kolekce ovládacích prvků.

### <a name="to-show-the-actions-pane"></a>Zobrazení podokna akce

1. Vytvoří novou instanci ovládacího prvku podokna akcí ve `ThisDocument` třídě.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs" id="Snippet10":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb" id="Snippet10":::

2. Přidejte následující kód do <xref:Microsoft.Office.Tools.Word.Document.Startup> obslužné rutiny události pro `ThisDocument` .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs" id="Snippet11":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb" id="Snippet11":::

## <a name="test-the-application"></a>Testování aplikace
 Otestujte dokument, abyste ověřili, že se podokno akce otevře při otevření dokumentu a že text zadaný do textových polí je po kliknutí na tlačítko vložen do záložek.

### <a name="to-test-your-document"></a>Testování dokumentu

1. Stisknutím klávesy **F5** spusťte projekt.

2. Potvrďte, že je podokno akce viditelné.

3. Do textových polí v podokně Akce zadejte své jméno a adresu a klikněte na tlačítko **Vložit**.

## <a name="next-steps"></a>Další kroky
 Tady jsou některé úkoly, které mohou být další:

- Vytvoří podokno akce v aplikaci Excel. Další informace najdete v tématu [Postup: Přidání podokna akcí do sešitů aplikace Excel](/previous-versions/visualstudio/visual-studio-2010/e3zbk0hz(v=vs.100)).

- Svázání dat s ovládacími prvky v podokně akcí. Další informace najdete v tématu [Návod: svázání dat s ovládacími prvky v podokně akcí aplikace Word](../vsto/walkthrough-binding-data-to-controls-on-a-word-actions-pane.md).

## <a name="see-also"></a>Viz také
- [Přehled podokna akcí](../vsto/actions-pane-overview.md)
- [Postupy: Přidání podokna akcí do dokumentů aplikace Word nebo sešitů aplikace Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)
- [Postupy: Přidání podokna akcí do sešitů aplikace Excel](/previous-versions/visualstudio/visual-studio-2010/e3zbk0hz(v=vs.100))
- [Postupy: Správa rozložení ovládacích prvků v podoknech akcí](../vsto/how-to-manage-control-layout-on-actions-panes.md)
- [Ovládací prvek záložek](../vsto/bookmark-control.md)
