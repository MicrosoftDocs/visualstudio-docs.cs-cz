---
title: 'Návod: Vytváření místních nabídek pro záložky'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- context menus, Word
- Bookmark control, events
- shortcut menus, Word
- menus, creating in Office applications
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: ff261fd6032f3c666dfa3d745508586ffede6504
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49884079"
---
# <a name="walkthrough-create-shortcut-menus-for-bookmarks"></a>Návod: Vytváření místních nabídek pro záložky
  Tento návod ukazuje, jak vytvořit místní nabídky pro <xref:Microsoft.Office.Tools.Word.Bookmark> ovládacích prvků v přizpůsobení úrovni dokumentu pro aplikaci Word. Když uživatel klepne pravým tlačítkem myši textu v záložce, místní nabídce se zobrazí a poskytuje možnosti uživatele pro formátování textu.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 Tento návod znázorňuje následující úlohy:  
  
- [Vytvoření projektu](#BKMK_CreateProject).  
  
- [Přidání textu a záložky v dokumentu](#BKMK_addtextandbookmarks).  
  
- [Přidání příkazů pro nabídku](#BKMK_AddCmndsShortMenu).  
  
- [Formátování textu v záložce](#BKMK_formattextbkmk).  
  
  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Požadavky  
 K dokončení tohoto návodu budete potřebovat následující komponenty:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] Nebo [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)]  
  
##  <a name="BKMK_CreateProject"></a> Vytvoření projektu  
 Prvním krokem je vytvoření projektu dokumentu aplikace Word v sadě Visual Studio.  
  
### <a name="to-create-a-new-project"></a>Chcete-li vytvořit nový projekt  
  
-   Vytvoření projektu dokumentu aplikace Word, který má název **Mé záložky nabídku**. V průvodci vyberte **vytvoříte nový textový dokument**. Další informace najdete v tématu [postupy: vytvoření Office projekty v sadě Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     Visual Studio otevře nový Wordový dokument v návrháři a přidá **Mé záložky nabídku** projektu **Průzkumníka řešení**.  
  
##  <a name="BKMK_addtextandbookmarks"></a> Přidání textu a záložky v dokumentu  
 Přidejte do dokumentu nějaký text a pak přidejte dvě překrývající se záložky.  
  
### <a name="to-add-text-to-your-document"></a>Přidání textu do dokumentu  
  
-   V dokumentu, který se zobrazí v Návrháři projektu zadejte následující text.  
  
     **Toto je příklad vytvoření nabídku, když kliknete pravým tlačítkem na textu v záložce.**  
  
### <a name="to-add-a-bookmark-control-to-your-document"></a>Chcete-li přidat ovládací prvek Bookmark do dokumentu  
  
1. V **nástrojů**, z **ovládací prvky aplikace Word** kartu tak, že přetáhnete <xref:Microsoft.Office.Tools.Word.Bookmark> ovládacího prvku do dokumentu.  
  
    **Přidejte ovládací prvek Bookmark** zobrazí se dialogové okno.  
  
2. Výběr slov "Vytvoření nabídku, když kliknete pravým tlačítkem na text" a potom klikněte na tlačítko **OK**.  
  
    `bookmark1` je přidán do dokumentu.  
  
3. Přidejte další <xref:Microsoft.Office.Tools.Word.Bookmark> ovládacího slova "klikněte pravým tlačítkem na text v záložku".  
  
    `bookmark2` je přidán do dokumentu.  
  
   > [!NOTE]  
   >  Slova "klikněte pravým tlačítkem na text" jsou v obou `bookmark1` a `bookmark2`.  
  
   Když přidáte záložku dokumentu v době návrhu <xref:Microsoft.Office.Tools.Word.Bookmark> ovládací prvek vytvořen. Můžete programovat proti několika událostem záložky. Můžete napsat kód <xref:Microsoft.Office.Tools.Word.Bookmark.BeforeRightClick> události záložky tak, že když uživatel klepne pravým tlačítkem myši textu v záložce, zobrazí místní nabídka.  
  
##  <a name="BKMK_AddCmndsShortMenu"></a> Přidání příkazů do místní nabídky  
 Přidání tlačítek do místní nabídky, která se zobrazí, když kliknete pravým tlačítkem na dokument.  
  
### <a name="to-add-commands-to-a-shortcut-menu"></a>Přidání příkazů do místní nabídky  
  
1.  Přidat **kódu XML pásu karet** položky do projektu. Další informace najdete v tématu [postupy: Začínáme s přizpůsobením pásu karet](../vsto/how-to-get-started-customizing-the-ribbon.md).  
  
2.  V **Průzkumníka řešení**vyberte **ThisDocument.cs** nebo **ThisDocument.vb**.  
  
3.  V panelu nabídky zvolte **zobrazení** > **kód**.  
  
     **ThisDocument** soubor třídy se otevře v editoru kódu.  
  
4.  Přidejte následující kód, který **ThisDocument** třídy. Tento kód přepíše metodu CreateRibbonExtensibilityObject a vrátí třídu kódu XML pásu karet do aplikace sady Office.  
  
     [!code-csharp[Trin_Word_Document_Menus#1](../vsto/codesnippet/CSharp/trin_word_document_menus.cs/thisdocument.cs#1)]
     [!code-vb[Trin_Word_Document_Menus#1](../vsto/codesnippet/VisualBasic/trin_word_document_menus.vb/thisdocument.vb#1)]  
  
5.  V **Průzkumníka řešení**, vyberte soubor XML pásu karet. Ve výchozím nastavení je Ribbon1.xml název souboru XML pásu karet.  
  
6.  V panelu nabídky zvolte **zobrazení** > **kód**.  
  
     Soubor xml pásu karet se otevře v editoru kódu.  
  
7.  V editoru kódu nahraďte obsah souboru XML pásu karet s následujícím kódem.  
  
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
  
     Tento kód přidá dvě tlačítka do místní nabídky, která se zobrazí, když kliknete pravým tlačítkem na dokument.  
  
8.  V **Průzkumníka řešení**, klikněte pravým tlačítkem na `ThisDocument`a potom klikněte na tlačítko **zobrazit kód**.  
  
9. Deklarujte následující proměnné a proměnná záložku na úrovni třídy.  
  
     [!code-csharp[Trin_Word_Document_Menus#2](../vsto/codesnippet/CSharp/trin_word_document_menus.cs/thisdocument.cs#2)]
     [!code-vb[Trin_Word_Document_Menus#2](../vsto/codesnippet/VisualBasic/trin_word_document_menus.vb/thisdocument.vb#2)]  
  
10. V **Průzkumníka řešení**, vyberte soubor kódu pásu karet. Ve výchozím nastavení, je název souboru s kódem pásu karet **Ribbon1.cs** nebo **Ribbon1.vb**.  
  
11. V panelu nabídky zvolte **zobrazení** > **kód**.  
  
     Soubor kódu pásu karet se otevře v editoru kódu.  
  
12. V souboru kódu pásu karet přidejte následující metodu. Toto je metoda zpětného volání pro dvě tlačítka, které jste přidali do místní nabídky dokumentu. Tato metoda určuje, zda tato tlačítka zobrazí v místní nabídce. Tučné písmo a kurzíva tlačítka zobrazí pouze v případě, že kliknete pravým tlačítkem na textu v záložce.  
  
     [!code-csharp[Trin_Word_Document_Menus#5](../vsto/codesnippet/CSharp/trin_word_document_menus.cs/ribbon1.cs#5)]
     [!code-vb[Trin_Word_Document_Menus#5](../vsto/codesnippet/VisualBasic/trin_word_document_menus.vb/ribbon1.vb#5)]  
  
##  <a name="BKMK_formattextbkmk"></a> Formátování textu v záložce  
  
### <a name="to-format-the-text-in-the-bookmark"></a>K formátování textu v záložce  
  
1.  Soubor kódu pásu karet, přidejte `ButtonClick` obslužnou rutinu události pro formátování na záložku.  
  
     [!code-csharp[Trin_Word_Document_Menus#6](../vsto/codesnippet/CSharp/trin_word_document_menus.cs/ribbon1.cs#6)]
     [!code-vb[Trin_Word_Document_Menus#6](../vsto/codesnippet/VisualBasic/trin_word_document_menus.vb/ribbon1.vb#6)]  
  
2.  **Průzkumník řešení**vyberte **ThisDocument.cs** nebo **ThisDocument.vb**.  
  
3.  V panelu nabídky zvolte **zobrazení** > **kód**.  
  
     **ThisDocument** soubor třídy se otevře v editoru kódu.  
  
4.  Přidejte následující kód, který **ThisDocument** třídy.  
  
     [!code-csharp[Trin_Word_Document_Menus#3](../vsto/codesnippet/CSharp/trin_word_document_menus.cs/thisdocument.cs#3)]
     [!code-vb[Trin_Word_Document_Menus#3](../vsto/codesnippet/VisualBasic/trin_word_document_menus.vb/thisdocument.vb#3)]  
  
    > [!NOTE]  
    >  Musíte napsat kód pro zpracování případu, kdy záložky překrývat. Pokud tak neučiníte, ve výchozím nastavení, zavolá se kód pro všechny záložky ve výběru.  
  
5.  V jazyce C#, je nutné přidat obslužné rutiny událostí pro ovládacích prvků záložek do <xref:Microsoft.Office.Tools.Word.Document.Startup> událostí. Informace o vytváření obslužných rutin událostí, naleznete v tématu [postupy: vytváření obslužných rutin událostí v projektech pro systém Office](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-csharp[Trin_Word_Document_Menus#4](../vsto/codesnippet/CSharp/trin_word_document_menus.cs/thisdocument.cs#4)]  
  
## <a name="test-the-application"></a>Testování aplikace  
 Otestujte dokumentu a ověřte, že položky nabídky tučný i kurzívu zobrazí v místní nabídce, když kliknete pravým tlačítkem na textu v záložce a že text je ve správném formátu.  
  
### <a name="to-test-your-document"></a>K otestování vašeho dokumentu  
  
1.  Stisknutím klávesy **F5** ke spuštění projektu.  
  
2.  Klikněte pravým tlačítkem v první záložce a potom klikněte na tlačítko **tučné**.  
  
3.  Ověřte, že veškerý text v `bookmark1` je formátován jako tučný.  
  
4.  Klikněte pravým tlačítkem na text, ve kterém záložky překrývají, a potom klikněte na tlačítko **Kurzíva**.  
  
5.  Ověřte, že veškerý text v `bookmark2` je kurzíva a pouze část textu v `bookmark1` , který se překrývá `bookmark2` kurzívy.  
  
## <a name="next-steps"></a>Další kroky  
 Tady jsou některé úlohy, které by mohl pocházet Další:  
  
-   Napsání kódu pro reakci na události hostitelské ovládací prvky v aplikaci Excel. Další informace najdete v tématu [názorný postup: Program ošetření událostí ovládacího prvku NamedRange](../vsto/walkthrough-programming-against-events-of-a-namedrange-control.md).  
  
-   Změna formátování na záložku pomocí zaškrtávacího políčka. Další informace najdete v tématu [návod: Změna formátování dokumentů s použitím ovládacích prvků CheckBox](../vsto/walkthrough-changing-document-formatting-using-checkbox-controls.md).  
  
## <a name="see-also"></a>Viz také:  
 [Návody pro aplikaci Word](../vsto/walkthroughs-using-word.md)   
 [Přizpůsobení uživatelského rozhraní systému Office](../vsto/office-ui-customization.md)   
 [Automatizace aplikace Word s použitím rozšířených objektů](../vsto/automating-word-by-using-extended-objects.md)   
 [BOOKMARK – ovládací prvek](../vsto/bookmark-control.md)   
 [Volitelné parametry v řešeních pro systém Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  