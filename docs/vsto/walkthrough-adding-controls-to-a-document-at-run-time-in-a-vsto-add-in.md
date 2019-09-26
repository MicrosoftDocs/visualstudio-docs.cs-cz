---
title: Přidání ovládacích prvků do dokumentu za běhu v doplňku VSTO
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- add-ins [Office development in Visual Studio], adding controls
- application-level add-ins [Office development in Visual Studio], adding controls
- controls [Office development in Visual Studio], adding to documents at run time
- documents [Office development in Visual Studio], adding controls at run time
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 9e8cde57ece3774e94f923387e1a8f7ca71cf797
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2019
ms.locfileid: "71254176"
---
# <a name="walkthrough-add-controls-to-a-document-at-run-time-in-a-vsto-add-in"></a>Návod: Přidání ovládacích prvků do dokumentu za běhu v doplňku VSTO
  Pomocí doplňku VSTO můžete přidat ovládací prvky do libovolného otevřeného dokumentu aplikace Word systém Microsoft Office. Tento návod ukazuje, jak použít pás karet k tomu, aby uživatelé mohli <xref:Microsoft.Office.Tools.Word.Controls.Button> přidat <xref:Microsoft.Office.Tools.Word.RichTextContentControl> nebo do dokumentu.

 **Platí pro:** Informace v tomto tématu se vztahují na projekty doplňku VSTO pro Word 2010. Další informace najdete v tématu [Dostupné funkce podle aplikace Office a typu projektu](../vsto/features-available-by-office-application-and-project-type.md).

 Tento návod znázorňuje následující úlohy:

- Vytváří se nový projekt doplňku VSTO pro Word.

- Poskytnutí uživatelského rozhraní (UI) pro přidání ovládacích prvků do dokumentu.

- Přidání ovládacích prvků do dokumentu v době běhu.

- Odebírání ovládacích prvků z dokumentu.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Požadavky
 K dokončení tohoto návodu budete potřebovat následující komponenty:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)]nebo [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].

## <a name="create-a-new-word-add-in-project"></a>Vytvořit nový projekt doplňku pro Word
 Začněte vytvořením projektu doplňku VSTO pro Word.

### <a name="to-create-a-new-word-vsto-add-in-project"></a>Vytvoření nového projektu doplňku VSTO pro Word

1. Vytvořte projekt doplňku VSTO pro Word s názvem **WordDynamicControls**. Další informace najdete v tématu [jak: Vytváření projektů Office v sadě Visual](../vsto/how-to-create-office-projects-in-visual-studio.md)Studio.

2. Přidejte odkaz na sestavení **Microsoft. Office. Tools. Word. v 4.0. Utilities. dll** . Tento odkaz je vyžadován pro programové přidání model Windows Formsho ovládacího prvku do dokumentu dále v tomto návodu.

## <a name="provide-a-ui-to-add-controls-to-a-document"></a>Poskytněte uživatelské rozhraní pro přidání ovládacích prvků do dokumentu.
 Přidejte vlastní kartu na pás karet ve Wordu. Uživatelé mohou vybrat zaškrtávací políčka na kartě pro přidání ovládacích prvků do dokumentu.

### <a name="to-provide-a-ui-to-add-controls-to-a-document"></a>Poskytnutí uživatelského rozhraní pro přidání ovládacích prvků do dokumentu

1. V nabídce **projekt** klikněte na příkaz **Přidat novou položku**.

2. V dialogovém okně **Přidat novou položku** vyberte možnost **pás karet (vizuální Návrhář)** .

3. Změňte název nového pásu karet na **MyRibbon**a klikněte na **Přidat**.

    Otevře se soubor **MyRibbon.cs** nebo **MyRibbon. vb** v Návrháři pásu karet a zobrazí výchozí kartu a skupinu.

4. V Návrháři pásu karet klikněte na skupinu **Group1** .

5. V okně **vlastnosti** změňte vlastnost **popisek** pro **Group1** na **Přidat ovládací prvky**.

6. Na kartě **ovládací prvky pásu karet Office** na **panelu nástrojů**přetáhněte ovládací prvek **CheckBox** na **Group1**.

7. Klikněte na možnost **checkBox1** a vyberte ji.

8. V okně **vlastnosti** změňte následující vlastnosti.

   | Vlastnost | Value |
   |-----------|-----------------------|
   | **Název** | **addButtonCheckBox** |
   | **Popisek** | **Tlačítko Přidat** |

9. Přidejte druhé zaškrtávací políčko do **Group1**a potom změňte následující vlastnosti.

   | Vlastnost | Value |
   |-----------|---------------------------|
   | **Název** | **addRichTextCheckBox** |
   | **Popisek** | **Přidat ovládací prvek formátovaného textu** |

10. V Návrháři pásu karet poklikejte na tlačítko **Přidat**.

     V editoru kódu se otevře obslužná rutina událostizaškrtávacíhopolíčkaPřidat<xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox.Click> tlačítko.

11. Vraťte se do Návrháře pásu karet a dvakrát klikněte na **Přidat ovládací prvek s formátováním textu**.

     V editoru kódu se otevře obslužná rutina událostipřidatovládacíprvekformátovaného<xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox.Click> textu.

    Později v tomto návodu přidáte kód do těchto obslužných rutin událostí pro přidání a odebrání ovládacích prvků v aktivním dokumentu.

## <a name="add-and-remove-controls-on-the-active-document"></a>Přidat nebo odebrat ovládací prvky v aktivním dokumentu
 V kódu doplňku VSTO je před přidáním ovládacího prvku nutné převést aktivní dokument na <xref:Microsoft.Office.Tools.Word.Document> *položku hostitele* . V řešeních pro systém Office lze spravované ovládací prvky přidat pouze k položkám hostitele, které fungují jako kontejnery pro ovládací prvky. V projektech doplňku VSTO lze položky hostitele vytvořit v době běhu pomocí `GetVstoObject` metody.

 Přidejte metody do `ThisAddIn` třídy, které lze volat pro přidání nebo <xref:Microsoft.Office.Tools.Word.Controls.Button> odebrání nebo <xref:Microsoft.Office.Tools.Word.RichTextContentControl> v aktivním dokumentu. Později v tomto návodu budete volat tyto metody z <xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox.Click> obslužných rutin událostí zaškrtávacích políček na pásu karet.

### <a name="to-add-and-remove-controls-on-the-active-document"></a>Přidání a odebrání ovládacích prvků v aktivním dokumentu

1. V **Průzkumník řešení**dvakrát klikněte na *ThisAddIn.cs* nebo *ThisAddIn. vb* pro otevření souboru v editoru kódu.

2. Do `ThisAddIn` třídy přidejte následující kód. Tento kód deklaruje <xref:Microsoft.Office.Tools.Word.Controls.Button> objekty a <xref:Microsoft.Office.Tools.Word.RichTextContentControl> objekty, které reprezentují ovládací prvky, které budou přidány do dokumentu.

     [!code-vb[Trin_WordAddInDynamicControlsWalkthrough#1](../vsto/codesnippet/VisualBasic/Trin_WordAddInDynamicControlsWalkthrough/ThisAddIn.vb#1)]
     [!code-csharp[Trin_WordAddInDynamicControlsWalkthrough#1](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControlsWalkthrough/ThisAddIn.cs#1)]

3. Do `ThisAddIn` třídy přidejte následující metodu. Když uživatel klikne na pás karet na **tlačítko Přidat** , tato metoda přidá <xref:Microsoft.Office.Tools.Word.Controls.Button> k aktuálnímu výběru v dokumentu <xref:Microsoft.Office.Tools.Word.Controls.Button> , pokud je zaškrtnuté políčko, nebo zruší zaškrtnutí políčka.

     [!code-vb[Trin_WordAddInDynamicControlsWalkthrough#2](../vsto/codesnippet/VisualBasic/Trin_WordAddInDynamicControlsWalkthrough/ThisAddIn.vb#2)]
     [!code-csharp[Trin_WordAddInDynamicControlsWalkthrough#2](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControlsWalkthrough/ThisAddIn.cs#2)]

4. Do `ThisAddIn` třídy přidejte následující metodu. Když uživatel klikne na pás karet na zaškrtávací políčko **Přidat ovládací prvek formátovaného textu** , tato metoda <xref:Microsoft.Office.Tools.Word.RichTextContentControl> přidá k aktuálnímu výběru v dokumentu <xref:Microsoft.Office.Tools.Word.RichTextContentControl> , pokud je zaškrtnuté políčko, nebo zruší zaškrtnutí políčka.

     [!code-vb[Trin_WordAddInDynamicControlsWalkthrough#3](../vsto/codesnippet/VisualBasic/Trin_WordAddInDynamicControlsWalkthrough/ThisAddIn.vb#3)]
     [!code-csharp[Trin_WordAddInDynamicControlsWalkthrough#3](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControlsWalkthrough/ThisAddIn.cs#3)]

## <a name="remove-the-button-control-when-the-document-is-saved"></a>Odebrat ovládací prvek tlačítko při uložení dokumentu
 Model Windows Forms ovládací prvky nejsou trvalé při uložení a zavření dokumentu. Nicméně Obálka ActiveX pro každý ovládací prvek zůstává v dokumentu a ohraničení této obálky mohou koncoví uživatelé zobrazit při opětovném otevření dokumentu. Existuje několik způsobů, jak dynamicky vytvořené model Windows Forms ovládací prvky v doplňcích VSTO vyčistit. V tomto návodu programově odeberete <xref:Microsoft.Office.Tools.Word.Controls.Button> ovládací prvek při uložení dokumentu.

### <a name="to-remove-the-button-control-when-the-document-is-saved"></a>Odebrání ovládacího prvku tlačítko při uložení dokumentu

1. V souboru kódu *ThisAddIn.cs* nebo *ThisAddIn. vb* přidejte následující `ThisAddIn` metodu do třídy. Tato metoda je obslužná rutina události pro <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave> událost. Pokud má <xref:Microsoft.Office.Tools.Word.Document> uložený dokument hostitelskou položku, která je k ní přidružená, obslužná rutina události získá hostitelskou položku <xref:Microsoft.Office.Tools.Word.Controls.Button> a odebere ovládací prvek, pokud existuje.

     [!code-vb[Trin_WordAddInDynamicControlsWalkthrough#4](../vsto/codesnippet/VisualBasic/Trin_WordAddInDynamicControlsWalkthrough/ThisAddIn.vb#4)]
     [!code-csharp[Trin_WordAddInDynamicControlsWalkthrough#4](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControlsWalkthrough/ThisAddIn.cs#4)]

2. V C#přidejte následující kód do `ThisAddIn_Startup` obslužné rutiny události. Tento kód je vyžadován v C# pro připojení `Application_DocumentBeforeSave` obslužné rutiny <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave> události k události.

     [!code-csharp[Trin_WordAddInDynamicControlsWalkthrough#5](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControlsWalkthrough/ThisAddIn.cs#5)]

## <a name="add-and-remove-controls-when-the-user-clicks-the-check-boxes-on-the-ribbon"></a>Přidat a odebrat ovládací prvky, když uživatel klikne na zaškrtávací políčka na pásu karet
 Nakonec změňte <xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox.Click> obslužné rutiny události políček, která jste přidali na pás karet, a přidejte nebo odeberte ovládací prvky v dokumentu.

### <a name="to-add-or-remove-controls-when-the-user-clicks-the-check-boxes-on-the-ribbon"></a>Přidání nebo odebrání ovládacích prvků, když uživatel klikne na zaškrtávací políčka na pásu karet

1. V souboru kódu *MyRibbon.cs* nebo *MyRibbon. vb* nahraďte vygenerované `addButtonCheckBox_Click` a `addRichTextCheckBox_Click` obslužné rutiny události následujícím kódem. Tento kód předefinuje tyto obslužné rutiny událostí pro volání `ToggleButtonOnDocument` metod `ToggleRichTextControlOnDocument` a `ThisAddIn` , které jste přidali do třídy dříve v tomto návodu.

     [!code-vb[Trin_WordAddInDynamicControlsWalkthrough#6](../vsto/codesnippet/VisualBasic/Trin_WordAddInDynamicControlsWalkthrough/MyRibbon.vb#6)]
     [!code-csharp[Trin_WordAddInDynamicControlsWalkthrough#6](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControlsWalkthrough/MyRibbon.cs#6)]

## <a name="test-the-solution"></a>Testování řešení
 Ovládací prvky můžete přidat do dokumentu jejich výběrem z vlastní karty na pásu karet. Při uložení dokumentu <xref:Microsoft.Office.Tools.Word.Controls.Button> se ovládací prvek odebere.

### <a name="to-test-the-solution"></a>K otestování řešení.

1. Stisknutím klávesy **F5** spusťte projekt.

2. V aktivním dokumentu stiskněte několikrát klávesu **ENTER** , aby se do dokumentu přidaly nové prázdné odstavce.

3. Vyberte první odstavec.

4. Klikněte na kartu **Doplňky** .

5. Ve skupině **Přidat ovládací prvky** klikněte na tlačítko **Přidat**.

     V prvním odstavci se zobrazí tlačítko.

6. Vyberte poslední odstavec.

7. Ve skupině **Přidat ovládací prvky** klikněte na možnost **Přidat ovládací prvek formátovaného textu**.

     Do posledního odstavce je přidán ovládací prvek obsahu ve formátovaném textu.

8. Uložte dokument.

     Tlačítko je odebráno z dokumentu.

## <a name="next-steps"></a>Další kroky
 Další informace o ovládacích prvcích v doplňcích VSTO najdete v těchto tématech:

- Ukázku, která ukazuje, jak přidat mnoho dalších typů ovládacích prvků do dokumentu za běhu a znovu vytvořit ovládací prvky při opětovném otevření dokumentu, naleznete v ukázce dynamické ovládací prvky doplňku pro aplikace Word v [ukázkách vývoje pro Office a v návodech](../vsto/office-development-samples-and-walkthroughs.md).

- Návod, který ukazuje, jak přidat ovládací prvky do listu pomocí doplňku VSTO pro Excel, najdete v tématu [Názorný postup: Přidejte ovládací prvky na list za běhu v projektu](../vsto/walkthrough-adding-controls-to-a-worksheet-at-run-time-in-vsto-add-in-project.md)doplňku VSTO.

## <a name="see-also"></a>Viz také:
- [Řešení pro Word](../vsto/word-solutions.md)
- [Přidání ovládacích prvků do dokumentů Office v době běhu](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Trvalé dynamické ovládací prvky v dokumentech Office](../vsto/persisting-dynamic-controls-in-office-documents.md)
- [Postupy: Přidání ovládacích prvků model Windows Forms do dokumentů Office](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)
- [Postupy: Přidání ovládacích prvků obsahu do dokumentů aplikace Word](../vsto/how-to-add-content-controls-to-word-documents.md)
- [Rozšiřování dokumentů aplikace Word a excelových sešitů v doplňcích VSTO za běhu](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
