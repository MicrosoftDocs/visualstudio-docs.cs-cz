---
title: 'Návod: Přidání ovládacích prvků do dokumentu za běhu v doplňku VSTO'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- add-ins [Office development in Visual Studio], adding controls
- application-level add-ins [Office development in Visual Studio], adding controls
- controls [Office development in Visual Studio], adding to documents at run time
- documents [Office development in Visual Studio], adding controls at run time
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 774e26388f5eb25fb0a16dee05557c6bf34a0ff0
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49951584"
---
# <a name="walkthrough-add-controls-to-a-document-at-runtime-in-a-vsto-add-in"></a>Návod: Přidání ovládacích prvků do dokumentu za běhu v doplňku VSTO
  Můžete přidat ovládací prvky do libovolného otevřeného dokumentu aplikace Microsoft Office Word s použitím doplňku VSTO. Tento návod ukazuje, jak používat na pásu karet umožňující uživatelům přidávat <xref:Microsoft.Office.Tools.Word.Controls.Button> nebo <xref:Microsoft.Office.Tools.Word.RichTextContentControl> do dokumentu.  

 **Platí pro:** informace v tomto tématu se vztahují na projekty doplňku VSTO pro Word 2010. Další informace najdete v tématu [Dostupné funkce podle aplikace Office a typu projektu](../vsto/features-available-by-office-application-and-project-type.md).  

 Tento návod znázorňuje následující úlohy:  

- Vytvoření nového projektu doplňku VSTO pro Word.  

- Poskytování uživatelského rozhraní (UI) k přidávání ovládacích prvků do dokumentu.  

- Přidání ovládacích prvků do dokumentu za běhu.  

- Odebrání ovládacích prvků z dokumentu.  

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  

## <a name="prerequisites"></a>Požadavky  
 K dokončení tohoto návodu budete potřebovat následující komponenty:  

-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  

-   [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] nebo [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].  

## <a name="create-a-new-word-add-in-project"></a>Vytvoření nového projektu doplňku aplikace Word  
 Začněte vytvořením projektu doplňku VSTO pro Word.  

### <a name="to-create-a-new-word-vsto-add-in-project"></a>Chcete-li vytvořit nový projekt doplňku VSTO pro Word  

1.  Vytvoření projektu doplňku VSTO pro Word s názvem **WordDynamicControls**. Další informace najdete v tématu [postupy: vytvoření Office projekty v sadě Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  

2.  Přidejte odkaz na **Microsoft.Office.Tools.Word.v4.0.Utilities.dll** sestavení. Tento odkaz je potřeba programové přidání ovládacího prvku Windows Forms do dokumentů později v tomto názorném postupu.  

## <a name="provide-a-ui-to-add-controls-to-a-document"></a>Zadejte uživatelské rozhraní k přidávání ovládacích prvků do dokumentu  
 Přidáte vlastní kartu na pás karet v aplikaci Word. Uživatelé mohou vybrat zaškrtávací políčka na kartě k přidávání ovládacích prvků do dokumentu.  

### <a name="to-provide-a-ui-to-add-controls-to-a-document"></a>K poskytování uživatelského rozhraní k přidávání ovládacích prvků do dokumentu  

1. Na **projektu** nabídky, klikněte na tlačítko **přidat novou položku**.  

2. V **přidat novou položku** dialogu **pás karet (vizuální návrhář)**.  

3. Změňte název nového pásu karet na **MyRibbon**a klikněte na tlačítko **přidat**.  

    **MyRibbon.cs** nebo **MyRibbon.vb** soubor se otevře v Návrháři pásu karet a zobrazí výchozí kartu a skupinu.  

4. V Návrháři pásu karet klikněte na tlačítko **group1** skupiny.  

5. V **vlastnosti** okno Změnit **popisek** vlastnost **group1** k **přidat ovládací prvky**.  

6. Z **ovládací prvky Ribbon Office** karty **nástrojů**, přetáhněte **zaškrtávací políčko** na ovládací prvek **group1**.  

7. Klikněte na tlačítko **CheckBox1** ji vyberte.  

8. V **vlastnosti** okně změnit následující vlastnosti.  


   | Vlastnost | Hodnota |
   |-----------|-----------------------|
   | **Jméno** | **addButtonCheckBox** |
   | **Popisek** | **Přidání tlačítka** |


9. Přidejte druhý zaškrtnutím políčka **group1**a potom změňte následující vlastnosti.  


   | Vlastnost | Hodnota |
   |-----------|---------------------------|
   | **Jméno** | **addRichTextCheckBox** |
   | **Popisek** | **Přidání ovládacího prvku RTF** |


10. V Návrháři pásu karet klikněte dvakrát na **přidat tlačítko**.  

     <xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox.Click> Obslužná rutina události **přidat tlačítko** zaškrtávacího políčka se otevře v editoru kódu.  

11. Vraťte se do Návrháře pásu karet a dvakrát klikněte na panel **přidat ovládací prvek Text ve formátu RTF**.  

     <xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox.Click> Obslužná rutina události **přidat ovládací prvek Text ve formátu RTF** zaškrtávacího políčka se otevře v editoru kódu.  

    Dále v tomto názorném postupu přidáte kód do těchto obslužných rutin událostí k přidání a odebrání ovládacích prvků v aktivním dokumentu.  

## <a name="add-and-remove-controls-on-the-active-document"></a>Přidání a odebrání ovládacích prvků na aktivní dokument  
 V kódu doplňku VSTO, je nutné převést do aktivního dokumentu <xref:Microsoft.Office.Tools.Word.Document> *hostitelský objekt* předtím, než přidáte ovládací prvek. V řešeních pro systém Office spravované ovládací prvky lze přidat pouze do hostitelské položky, které fungují jako kontejnery pro ovládací prvky. V doplňku VSTO projektů je hostitelské položky vytvořit v době běhu pomocí `GetVstoObject` metody.  

 Přidejte metody, které `ThisAddIn` třídu, která lze volat pro přidání nebo odebrání <xref:Microsoft.Office.Tools.Word.Controls.Button> nebo <xref:Microsoft.Office.Tools.Word.RichTextContentControl> v aktivním dokumentu. Později v tomto návodu budete volat tyto metody ze <xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox.Click> obslužné rutiny událostí zaškrtávacích políček na pásu karet.  

### <a name="to-add-and-remove-controls-on-the-active-document"></a>K přidání a odebrání ovládacích prvků na aktivní dokument  

1.  V **Průzkumníka řešení**, dvakrát klikněte na panel *ThisAddIn.cs* nebo *ThisAddIn.vb* k otevření souboru v editoru kódu.  

2.  Přidejte následující kód, který `ThisAddIn` třídy. Tento kód deklaruje <xref:Microsoft.Office.Tools.Word.Controls.Button> a <xref:Microsoft.Office.Tools.Word.RichTextContentControl> objekty, které představují ovládací prvky, které se přidají do dokumentu.  

     [!code-vb[Trin_WordAddInDynamicControlsWalkthrough#1](../vsto/codesnippet/VisualBasic/Trin_WordAddInDynamicControlsWalkthrough/ThisAddIn.vb#1)]
     [!code-csharp[Trin_WordAddInDynamicControlsWalkthrough#1](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControlsWalkthrough/ThisAddIn.cs#1)]  

3.  Přidejte následující metodu do `ThisAddIn` třídy. Pokud uživatel klikne **přidat tlačítko** zaškrtávací políčko na pásu karet, tato metoda přidá <xref:Microsoft.Office.Tools.Word.Controls.Button> do aktuálního výběru dokumentu, pokud se zaškrtávací políčko zaškrtnuto nebo odebere <xref:Microsoft.Office.Tools.Word.Controls.Button> Pokud není zaškrtnuto zaškrtávací políčko.  

     [!code-vb[Trin_WordAddInDynamicControlsWalkthrough#2](../vsto/codesnippet/VisualBasic/Trin_WordAddInDynamicControlsWalkthrough/ThisAddIn.vb#2)]
     [!code-csharp[Trin_WordAddInDynamicControlsWalkthrough#2](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControlsWalkthrough/ThisAddIn.cs#2)]  

4.  Přidejte následující metodu do `ThisAddIn` třídy. Pokud uživatel klikne **přidat ovládací prvek Text ve formátu RTF** zaškrtávací políčko na pásu karet, tato metoda přidá <xref:Microsoft.Office.Tools.Word.RichTextContentControl> do aktuálního výběru dokumentu, pokud se zaškrtávací políčko zaškrtnuto nebo odebere <xref:Microsoft.Office.Tools.Word.RichTextContentControl> Pokud není zaškrtnuto zaškrtávací políčko.  

     [!code-vb[Trin_WordAddInDynamicControlsWalkthrough#3](../vsto/codesnippet/VisualBasic/Trin_WordAddInDynamicControlsWalkthrough/ThisAddIn.vb#3)]
     [!code-csharp[Trin_WordAddInDynamicControlsWalkthrough#3](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControlsWalkthrough/ThisAddIn.cs#3)]  

## <a name="remove-the-button-control-when-the-document-is-saved"></a>Odebrat ovládací prvek tlačítka, když je dokument uložen  
 Ovládací prvky Windows Forms nejsou trvalé při uložení a pak zavření dokumentu. Ale obálku ActiveX pro každý ovládací prvek zůstane v dokumentu a ohraničení touto obálkou uvidí koncoví uživatelé při opětovném otevření dokumentu. Existuje několik způsobů, jak vyčistit dynamicky generovaný ovládacích prvků Windows Forms v doplňcích VSTO. V tomto podrobném návodu, můžete programově odebrat <xref:Microsoft.Office.Tools.Word.Controls.Button> řídit, kdy je dokument uložen.  

### <a name="to-remove-the-button-control-when-the-document-is-saved"></a>Chcete-li odebrat ovládací prvek tlačítka, když je dokument uložen  

1.  V *ThisAddIn.cs* nebo *ThisAddIn.vb* soubor kódu, přidejte následující metodu do `ThisAddIn` třídy. Tato metoda je obslužná rutina události <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave> událostí. Pokud má uložené dokumenty <xref:Microsoft.Office.Tools.Word.Document> hostitelský objekt, který je spojen s ní obslužná rutina události načte položku hostitele a odebere <xref:Microsoft.Office.Tools.Word.Controls.Button> ovládací prvek, pokud existuje.  

     [!code-vb[Trin_WordAddInDynamicControlsWalkthrough#4](../vsto/codesnippet/VisualBasic/Trin_WordAddInDynamicControlsWalkthrough/ThisAddIn.vb#4)]
     [!code-csharp[Trin_WordAddInDynamicControlsWalkthrough#4](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControlsWalkthrough/ThisAddIn.cs#4)]  

2.  V jazyce C#, přidejte následující kód, který `ThisAddIn_Startup` obslužné rutiny události. Tento kód je vyžadován v jazyce C# pro připojení `Application_DocumentBeforeSave` obslužné rutině události <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave> událostí.  

     [!code-csharp[Trin_WordAddInDynamicControlsWalkthrough#5](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControlsWalkthrough/ThisAddIn.cs#5)]  

## <a name="add-and-remove-controls-when-the-user-clicks-the-check-boxes-on-the-ribbon"></a>Přidání a odebrání ovládacích prvků, když uživatel klikne na tlačítko zaškrtnutí políček na pásu karet  
 Nakonec upravte <xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox.Click> obslužné rutiny událostí zaškrtávacích políček, která jste přidali na pásu karet a přidat nebo odebrat u daného dokumentu řízení.  

### <a name="to-add-or-remove-controls-when-the-user-clicks-the-check-boxes-on-the-ribbon"></a>Přidání nebo odebrání řídí, když uživatel klepne zaškrtávací políčka na pásu karet  

1.  V *MyRibbon.cs* nebo *MyRibbon.vb* soubor kódu, nahraďte generované `addButtonCheckBox_Click` a `addRichTextCheckBox_Click` obslužné rutiny události s následujícím kódem. Tento kód předefinuje těchto obslužných rutin událostí k volání `ToggleButtonOnDocument` a `ToggleRichTextControlOnDocument` metody, které jste přidali do `ThisAddIn` třídy dříve v tomto návodu.  

     [!code-vb[Trin_WordAddInDynamicControlsWalkthrough#6](../vsto/codesnippet/VisualBasic/Trin_WordAddInDynamicControlsWalkthrough/MyRibbon.vb#6)]
     [!code-csharp[Trin_WordAddInDynamicControlsWalkthrough#6](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControlsWalkthrough/MyRibbon.cs#6)]  

## <a name="test-the-solution"></a>Otestování řešení  
 Přidání ovládacích prvků do dokumentu tak, že je vyberete na vlastní kartu na pásu karet. Při ukládání dokumentu, <xref:Microsoft.Office.Tools.Word.Controls.Button> odebrání ovládacího prvku.  

### <a name="to-test-the-solution"></a>Otestování řešení.  

1.  Stisknutím klávesy **F5** ke spuštění projektu.  

2.  V aktivním dokumentu, stiskněte klávesu **Enter** několikrát, chcete-li přidat nový prázdný odstavce do dokumentu.  

3.  Vyberte první odstavec.  

4.  Klikněte na tlačítko **Add-Ins** kartu.  

5.  V **přidat ovládací prvky** klikněte na možnost **přidat tlačítko**.  

     Tlačítko se zobrazí v prvním odstavci.  

6.  Vyberte poslední odstavce.  

7.  V **přidat ovládací prvky** klikněte na možnost **přidat ovládací prvek Text ve formátu RTF**.  

     Ovládací prvek obsahu formátovaného textu se přidá na posledním odstavci.  

8.  Uložte dokument.  

     Tlačítko se odebere z dokumentu.  

## <a name="next-steps"></a>Další kroky  
 Další informace o ovládacích prvcích v doplňcích VSTO z těchto témat:  

-   Příklad, který ukazuje, jak přidat mnoho typů ovládacích prvků do dokumentu za běhu a znovu vytvořte ovládací prvky, když znovu otevřete dokument, naleznete v tématu slova Add-In dynamické ovládací prvky ukázce kódu na [Office Ukázky a návody vývoje](../vsto/office-development-samples-and-walkthroughs.md).  

-   Názorný postup ukazuje, jak přidat ovládací prvky do listu pomocí doplňku VSTO pro Excel, naleznete v tématu [návod: Přidání ovládacích prvků na list za běhu v projektu doplňku VSTO](../vsto/walkthrough-adding-controls-to-a-worksheet-at-run-time-in-vsto-add-in-project.md).  

## <a name="see-also"></a>Viz také:  
 [Řešení aplikace Word](../vsto/word-solutions.md)   
 [Přidání ovládacích prvků do dokumentů Office za běhu](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Uchování dynamických ovládacích prvků v dokumentech Office](../vsto/persisting-dynamic-controls-in-office-documents.md)   
 [Postupy: Přidání ovládacích prvků Windows Forms do dokumentů Office](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)   
 [Postupy: Přidání ovládacích prvků obsahu do dokumentů aplikace Word](../vsto/how-to-add-content-controls-to-word-documents.md)   
 [Rozšíření dokumentů aplikace Word a sešitů aplikace Excel v doplňcích VSTO za běhu](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)  

