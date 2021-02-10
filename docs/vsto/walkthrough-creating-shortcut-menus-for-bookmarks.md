---
title: 'Návod: Vytvoření místních nabídek pro záložky'
description: Naučte se, jak vytvořit místní nabídky pro ovládací prvky záložek v přizpůsobení na úrovni dokumentu pro Microsoft Word.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- context menus, Word
- Bookmark control, events
- shortcut menus, Word
- menus, creating in Office applications
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: aabc7dec0a9965a055bce07cafeca25ac0165037
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99937413"
---
# <a name="walkthrough-create-shortcut-menus-for-bookmarks"></a>Návod: Vytvoření místních nabídek pro záložky
  Tento návod ukazuje, jak vytvořit místní nabídky pro <xref:Microsoft.Office.Tools.Word.Bookmark> ovládací prvky v přizpůsobení na úrovni dokumentu pro aplikaci Word. Když uživatel klikne pravým tlačítkem myši na text v záložce, zobrazí se místní nabídka a uživatel bude mít možnost formátování textu.

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

 Tento návod znázorňuje následující úlohy:

- [Vytvořte projekt](#BKMK_CreateProject).

- [Přidejte text a záložky do dokumentu](#BKMK_addtextandbookmarks).

- [Přidejte příkazy do místní nabídky](#BKMK_AddCmndsShortMenu).

- [Naformátujte text na záložce](#BKMK_formattextbkmk).

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Požadavky
 K dokončení tohoto návodu budete potřebovat následující komponenty:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] nebo [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)]

## <a name="create-the-project"></a><a name="BKMK_CreateProject"></a> Vytvořit projekt
 Prvním krokem je vytvoření projektu wordového dokumentu v aplikaci Visual Studio.

### <a name="to-create-a-new-project"></a>Vytvoření nového projektu

- Vytvořte projekt wordového dokumentu, který má **místní nabídku název své záložky**. V průvodci vyberte možnost **vytvořit nový dokument**. Další informace najdete v tématu [Postupy: vytváření projektů pro systém Office v sadě Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     Visual Studio otevře nový wordový dokument v návrháři a přidá do **Průzkumník řešení** projekt **místní nabídky zástupce moje záložka** .

## <a name="add-text-and-bookmarks-to-the-document"></a><a name="BKMK_addtextandbookmarks"></a> Přidat text a záložky do dokumentu
 Přidejte do dokumentu nějaký text a pak přidejte dvě překrývající se záložky.

### <a name="to-add-text-to-your-document"></a>Přidání textu do dokumentu

- V dokumentu, který se zobrazí v Návrháři projektu, zadejte následující text.

     **Toto je příklad vytvoření místní nabídky při kliknutí pravým tlačítkem myši na text v záložce.**

### <a name="to-add-a-bookmark-control-to-your-document"></a>Přidání ovládacího prvku záložka do dokumentu

1. V **sadě nástrojů** na kartě **ovládací prvky aplikace Word** přetáhněte <xref:Microsoft.Office.Tools.Word.Bookmark> ovládací prvek do dokumentu.

    Zobrazí se dialogové okno **Přidat ovládací prvek záložky** .

2. Vyberte slova "Vytvoření místní nabídky po kliknutí pravým tlačítkem myši na text" a pak klikněte na **OK**.

    `bookmark1` je přidán do dokumentu.

3. Přidejte další <xref:Microsoft.Office.Tools.Word.Bookmark> ovládací prvek do slova "klikněte pravým tlačítkem myši na text v záložce".

    `bookmark2` je přidán do dokumentu.

   > [!NOTE]
   > Slova "klikněte pravým tlačítkem myši na text" jsou v `bookmark1` i `bookmark2` .

   Když přidáte záložku k dokumentu v době návrhu, vytvoří <xref:Microsoft.Office.Tools.Word.Bookmark> se ovládací prvek. Můžete programovat na několika událostech záložky. V případě záložky můžete napsat kód, <xref:Microsoft.Office.Tools.Word.Bookmark.BeforeRightClick> takže když uživatel klikne pravým tlačítkem myši na text v záložce, zobrazí se místní nabídka.

## <a name="add-commands-to-a-shortcut-menu"></a><a name="BKMK_AddCmndsShortMenu"></a> Přidání příkazů do místní nabídky
 Přidejte tlačítka do místní nabídky, která se zobrazí po kliknutí pravým tlačítkem myši na dokument.

### <a name="to-add-commands-to-a-shortcut-menu"></a>Přidání příkazů do místní nabídky

1. Přidejte položku **XML pásu karet** do projektu. Další informace najdete v tématu [Postupy: Začínáme s přizpůsobením pásu karet](../vsto/how-to-get-started-customizing-the-ribbon.md).

2. V **Průzkumník řešení** vyberte **ThisDocument.cs** nebo **ThisDocument. vb**.

3. Na panelu nabídek vyberte možnost **Zobrazit**  >  **kód**.

     V editoru kódu se otevře soubor třídy **ThisDocument** .

4. Do třídy **ThisDocument** přidejte následující kód. Tento kód přepíše metodu CreateRibbonExtensibilityObject a vrátí třídu XML pásu karet do aplikace sady Office.

     [!code-csharp[Trin_Word_Document_Menus#1](../vsto/codesnippet/CSharp/trin_word_document_menus.cs/thisdocument.cs#1)]
     [!code-vb[Trin_Word_Document_Menus#1](../vsto/codesnippet/VisualBasic/trin_word_document_menus.vb/thisdocument.vb#1)]

5. V **Průzkumník řešení** vyberte soubor XML pásu karet. Ve výchozím nastavení se soubor XML pásu karet jmenuje Ribbon1.xml.

6. Na panelu nabídek vyberte možnost **Zobrazit**  >  **kód**.

     V editoru kódu se otevře soubor XML pásu karet.

7. V editoru kódu nahraďte obsah souboru XML pásu karet následujícím kódem.

    ```xml
    <?xml version="1.0" encoding="UTF-8"?>
    <customUI xmlns="http://schemas.microsoft.com/office/2009/07/customui" onLoad="Ribbon_Load">
      <contextMenus>
        <contextMenu idMso="ContextMenuText">
          <button id="BoldButton" label="Bold" onAction="ButtonClick"
               getVisible="GetVisible" />
          <button id="ItalicButton" label="Italic" onAction="ButtonClick"
              getVisible="GetVisible"/>
        </contextMenu>
      </contextMenus>
    </customUI>
    ```

     Tento kód přidá dvě tlačítka do místní nabídky, která se zobrazí po kliknutí pravým tlačítkem myši na dokument.

8. V **Průzkumník řešení** klikněte pravým tlačítkem myši `ThisDocument` a pak klikněte na **Zobrazit kód**.

9. Deklarovat následující proměnné a proměnnou záložky na úrovni třídy.

     [!code-csharp[Trin_Word_Document_Menus#2](../vsto/codesnippet/CSharp/trin_word_document_menus.cs/thisdocument.cs#2)]
     [!code-vb[Trin_Word_Document_Menus#2](../vsto/codesnippet/VisualBasic/trin_word_document_menus.vb/thisdocument.vb#2)]

10. V **Průzkumník řešení** vyberte soubor kódu pásu karet. Ve výchozím nastavení se soubor kódu pásu karet jmenuje **Ribbon1.cs** nebo **Ribbon1. vb**.

11. Na panelu nabídek vyberte možnost **Zobrazit**  >  **kód**.

     V editoru kódu se otevře soubor kódu pásu karet.

12. Do souboru kódu pásu karet přidejte následující metodu. Toto je metoda zpětného volání pro dvě tlačítka, která jste přidali do místní nabídky dokumentu. Tato metoda určuje, zda se tato tlačítka zobrazí v místní nabídce. Tlačítka tučná a kurzíva se zobrazí pouze v případě, že kliknete pravým tlačítkem myši na text v rámci záložky.

     [!code-csharp[Trin_Word_Document_Menus#5](../vsto/codesnippet/CSharp/trin_word_document_menus.cs/ribbon1.cs#5)]
     [!code-vb[Trin_Word_Document_Menus#5](../vsto/codesnippet/VisualBasic/trin_word_document_menus.vb/ribbon1.vb#5)]

## <a name="format-the-text-in-the-bookmark"></a><a name="BKMK_formattextbkmk"></a> Formátování textu v záložce

### <a name="to-format-the-text-in-the-bookmark"></a>Formátování textu v záložce

1. V souboru kódu pásu karet přidejte `ButtonClick` obslužnou rutinu události, která aplikuje formátování na záložku.

     [!code-csharp[Trin_Word_Document_Menus#6](../vsto/codesnippet/CSharp/trin_word_document_menus.cs/ribbon1.cs#6)]
     [!code-vb[Trin_Word_Document_Menus#6](../vsto/codesnippet/VisualBasic/trin_word_document_menus.vb/ribbon1.vb#6)]

2. **Průzkumník řešení** vyberte **ThisDocument.cs** nebo **ThisDocument. vb**.

3. Na panelu nabídek vyberte možnost **Zobrazit**  >  **kód**.

     V editoru kódu se otevře soubor třídy **ThisDocument** .

4. Do třídy **ThisDocument** přidejte následující kód.

     [!code-csharp[Trin_Word_Document_Menus#3](../vsto/codesnippet/CSharp/trin_word_document_menus.cs/thisdocument.cs#3)]
     [!code-vb[Trin_Word_Document_Menus#3](../vsto/codesnippet/VisualBasic/trin_word_document_menus.vb/thisdocument.vb#3)]

    > [!NOTE]
    > Je nutné napsat kód, který zpracuje případ, kde se záložky překrývají. Pokud to neuděláte, bude ve výchozím nastavení pro všechny záložky ve výběru volán kód.

5. V jazyce C# je nutné přidat obslužné rutiny události pro ovládací prvky záložky do <xref:Microsoft.Office.Tools.Word.Document.Startup> události. Informace o vytváření obslužných rutin událostí najdete v tématu [Postupy: vytváření obslužných rutin událostí v projektech pro systém Office](../vsto/how-to-create-event-handlers-in-office-projects.md).

     [!code-csharp[Trin_Word_Document_Menus#4](../vsto/codesnippet/CSharp/trin_word_document_menus.cs/thisdocument.cs#4)]

## <a name="test-the-application"></a>Testování aplikace
 Otestujte dokument, abyste ověřili, že položky nabídky tučné a kurzíva se zobrazí v místní nabídce, když kliknete pravým tlačítkem myši na text v záložce a že je text ve správném formátu.

### <a name="to-test-your-document"></a>Testování dokumentu

1. Stisknutím klávesy **F5** spusťte projekt.

2. Klikněte pravým tlačítkem na první záložku a pak klikněte na **tučné**.

3. Ověřte, že veškerý text v `bookmark1` je formátován tučně.

4. Klikněte pravým tlačítkem myši na text, ve kterém se záložky překrývají, a pak klikněte na **kurzíva**.

5. Ověřte, že veškerý text v `bookmark2` je kurzívou a pouze část textu v `bookmark1` tomto překrytí `bookmark2` je kurzíva.

## <a name="next-steps"></a>Další kroky
 Tady jsou některé úkoly, které mohou být další:

- Napište kód pro reakci na události hostitelských ovládacích prvků v aplikaci Excel. Další informace naleznete v tématu [Návod: program v událostech ovládacího prvku NamedRange](../vsto/walkthrough-programming-against-events-of-a-namedrange-control.md).

- Pomocí zaškrtávacího políčka můžete změnit formátování záložky. Další informace naleznete v tématu [Návod: Změna formátování dokumentu pomocí ovládacích prvků CheckBox](../vsto/walkthrough-changing-document-formatting-using-checkbox-controls.md).

## <a name="see-also"></a>Viz také
- [Návody pomocí aplikace Word](../vsto/walkthroughs-using-word.md)
- [Přizpůsobení uživatelského rozhraní systému Office](../vsto/office-ui-customization.md)
- [Automatizace Wordu pomocí rozšířených objektů](../vsto/automating-word-by-using-extended-objects.md)
- [Ovládací prvek záložek](../vsto/bookmark-control.md)
- [Volitelné parametry v řešeních pro systém Office](../vsto/optional-parameters-in-office-solutions.md)
