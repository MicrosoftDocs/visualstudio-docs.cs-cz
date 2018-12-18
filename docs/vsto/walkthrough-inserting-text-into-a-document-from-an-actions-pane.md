---
title: 'Návod: Vložení textu do dokumentu z podokna akcí'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- smart documents [Office development in Visual Studio], creating in Word
- smart documents [Office development in Visual Studio], adding controls
- actions panes [Office development in Visual Studio], creating in Word
- actions panes [Office development in Visual Studio], adding controls
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: b3b9683c5f41b81d529ad6f3347b54131f32f011
ms.sourcegitcommit: 54c65f81a138fc1e8ff1826f7bd9dcec710618cc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/19/2018
ms.locfileid: "51948722"
---
# <a name="walkthrough-insert-text-into-a-document-from-an-actions-pane"></a>Návod: Vložení textu do dokumentu z podokna akcí
  Tento návod ukazuje, jak vytvořit podokna akcí v dokumentu aplikace Microsoft Office Word. V podokně Akce obsahuje dva ovládací prvky, shromažďovat vstup a odešlete textu do dokumentu.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 Tento návod znázorňuje následující úlohy:  
  
-   Návrh rozhraní pomocí ovládacích prvků Windows Forms na ovládací prvek podokna akce.  
  
-   Zobrazte podokno akcí při otevření aplikace.  
  
> [!NOTE]  
>  Váš počítač může v následujících pokynech zobrazovat odlišné názvy nebo umístění některých prvků uživatelského rozhraní sady Visual Studio. Tyto prvky jsou určeny edicí sady Visual Studio a použitým nastavením. Další informace najdete v tématu [přizpůsobení integrovaného vývojového prostředí sady Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="prerequisites"></a>Požadavky  
 K dokončení tohoto návodu budete potřebovat následující komponenty:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] nebo [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].  
  
## <a name="create-the-project"></a>Vytvoření projektu  
 Prvním krokem je vytvoření projektu dokumentu aplikace Word.  
  
### <a name="to-create-a-new-project"></a>Chcete-li vytvořit nový projekt  
  
1.  Vytvoření projektu Wordového dokumentu s názvem **Moje základní podokna akcí**. V průvodci vyberte **vytvoříte nový textový dokument**. Další informace najdete v tématu [postupy: vytvoření Office projekty v sadě Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     Visual Studio otevře nový Wordový dokument v návrháři a přidá **Moje základní podokna akcí** projektu **Průzkumníka řešení**.  
  
## <a name="add-text-and-bookmarks-to-the-document"></a>Přidání textu a záložky v dokumentu  
 Podokna akcí odešle text do záložky v dokumentu. Navrhnout dokumentu, zadejte nějaký text k vytvoření základní formulář.  
  
### <a name="to-add-text-to-your-document"></a>Přidání textu do dokumentu  
  
1. Zadejte následující text do dokumentu aplikace Word:  
  
    **21. března 2008**  
  
    **Jméno**  
  
    **Adresa**  
  
    **Toto je příklad základní akce podokna ve Wordu.**  
  
   Můžete přidat <xref:Microsoft.Office.Tools.Word.Bookmark> ovládacího prvku do dokumentu z jeho přetažením **nástrojů** v sadě Visual Studio nebo pomocí **záložku** dialogové okno v aplikaci Word.  
  
### <a name="to-add-a-bookmark-control-to-your-document"></a>Chcete-li přidat ovládací prvek Bookmark do dokumentu  
  
1.  Z **ovládací prvky aplikace Word** karty **nástrojů**, přetáhněte <xref:Microsoft.Office.Tools.Word.Bookmark> ovládacího prvku do dokumentu.  
  
     **Přidejte ovládací prvek Bookmark** zobrazí se dialogové okno.  
  
2.  Vybrat slovo **název**, bez výběru značku odstavce a klikněte na tlačítko **OK**.  
  
    > [!NOTE]  
    >  Značku odstavce by měla být mimo záložky. Pokud značek odstavů nejsou viditelné v dokumentu, klikněte na tlačítko **nástroje** nabídky, přejděte **nástroje sady Microsoft Office Word** a potom klikněte na tlačítko **možnosti**. Klikněte na tlačítko **zobrazení** kartu a vyberte **odstavců** zaškrtávací políčko **značky formátování** část **možnosti** dialogové okno.  
  
3.  V **vlastnosti** okno Změnit **název** vlastnost **Bookmark1** k **showName**.  
  
4.  Vybrat slovo **adresu**, nevybírejte značku odstavce.  
  
5.  Na **vložit** kartu na pásu karet v **odkazy** klikněte na možnost **záložku**.  
  
6.  V **záložku** dialogovém okně **showAddress** v **název záložky** pole a klikněte na tlačítko **přidat**.  
  
## <a name="add-controls-to-the-actions-pane"></a>Přidání ovládacích prvků do podokna akcí  
 K návrhu rozhraní podokna akcí, přidejte ovládací prvek podokna akcí do projektu a pak přidejte ovládací prvky Windows Forms do ovládacího prvku podokna akcí.  
  
### <a name="to-add-an-actions-pane-control"></a>Chcete-li přidat ovládací prvek podokna akce  
  
1.  Vyberte **Moje základní podokna akcí** projekt **Průzkumníka řešení**.  
  
2.  Na **projektu** nabídky, klikněte na tlačítko **přidat novou položku**.  
  
3.  V **přidat novou položku** dialogové okno, klikněte na tlačítko **ovládacího prvku podokna akcí**, ovládací prvek pojmenujte **InsertTextControl,** a klikněte na tlačítko **přidat**.  
  
#### <a name="to-add-windows-form-controls-to-the-actions-pane-control"></a>Přidání ovládacích prvků formulářů Windows do ovládacího prvku podokna akcí  
  
1.  Pokud ovládací prvek podokna akce není viditelný v návrháři, klikněte dvakrát na **InsertTextControl**.  
  
2.  Z **běžné ovládací prvky** karty **nástrojů**, přetáhněte **popisek** ovládacího prvku na ovládací prvek podokna akce.  
  
3.  Změnit **Text** vlastnost ovládacího prvku popisku **název**.  
  
4.  Přidat **Textbox** ovládací prvek ovládacího prvku podokna akcí a změnit následující vlastnosti.  
  
    |Vlastnost|Hodnota|  
    |--------------|-----------|  
    |**Jméno**|**GetName –**|  
    |**Velikost**|**130, 20**|  
  
5.  Přidejte druhý **popisek** ovládací prvek ovládacího prvku podokna akcí a změnit **Text** vlastnost **adresu**.  
  
6.  Přidejte druhý **Textbox** ovládací prvek ovládacího prvku podokna akcí a změnit následující vlastnosti.  
  
    |Vlastnost|Hodnota|  
    |--------------|-----------|  
    |**Jméno**|**GetAddress**|  
    |**Přijímá Return**|**Hodnota TRUE**|  
    |**Multiline**|**Hodnota TRUE**|  
    |**Velikost**|**130, 40**|  
  
7.  Přidat **tlačítko** ovládací prvek ovládacího prvku podokna akcí a změnit následující vlastnosti.  
  
    |Vlastnost|Hodnota|  
    |--------------|-----------|  
    |**Jméno**|**addText**|  
    |**Text**|**Vložit**|  
  
## <a name="add-code-to-insert-text-into-the-document"></a>Přidejte kód pro vložení textu do dokumentu  
 V podokně Akce napsat kód, který vloží text z textového pole do příslušné <xref:Microsoft.Office.Tools.Word.Bookmark> ovládací prvky v dokumentu. Můžete použít `Globals` pro přístup k u daného dokumentu řízení z ovládacích prvků v podokně Akce. Další informace najdete v tématu [globální přístup k objektům v projektech Office](../vsto/global-access-to-objects-in-office-projects.md).  
  
### <a name="to-insert-text-from-the-actions-pane-in-a-bookmark-in-the-document"></a>Chcete-li vložit text z podokna akcí v záložky v dokumentu  
  
1.  Přidejte následující kód, který <xref:System.Windows.Forms.Control.Click> obslužná rutina události **addText** tlačítko.  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#8](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/InsertTextControl.cs#8)]
     [!code-vb[Trin_VstcoreActionsPaneWord#8](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/InsertTextControl.vb#8)]  
  
2.  V jazyce C# je nutné přidat obslužnou rutinu události pro kliknutí na tlačítko. Tento kód v můžete umístit `InsertTextControl` konstruktor po volání `InitializeComponent`. Informace o vytváření obslužných rutin událostí, naleznete v tématu [postupy: vytváření obslužných rutin událostí v projektech pro systém Office](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#9](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/InsertTextControl.cs#9)]  
  
## <a name="add-code-to-show-the-actions-pane"></a>Přidejte kód k zobrazení podokna akcí  
 Zobrazit podokno akcí, přidejte ovládací prvek, který jste vytvořili do kolekce ovládacích prvků.  
  
### <a name="to-show-the-actions-pane"></a>Chcete-li zobrazit podokno akcí  
  
1.  Vytvořit novou instanci ovládacího prvku podokna akcí v `ThisDocument` třídy.  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#10](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#10)]
     [!code-vb[Trin_VstcoreActionsPaneWord#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#10)]  
  
2.  Přidejte následující kód, který <xref:Microsoft.Office.Tools.Word.Document.Startup> obslužná rutina události `ThisDocument`.  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#11](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#11)]
     [!code-vb[Trin_VstcoreActionsPaneWord#11](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#11)]  
  
## <a name="test-the-application"></a>Testování aplikace  
 Testujte váš dokument k ověření, že při otevření dokumentu a, že text zadaný do textového pole je vložen do záložky po kliknutí na tlačítko se otevře v podokně Akce.  
  
### <a name="to-test-your-document"></a>K otestování vašeho dokumentu  
  
1.  Stisknutím klávesy **F5** ke spuštění projektu.  
  
2.  Potvrďte, že v podokně Akce je viditelný.  
  
3.  Zadejte název a adresu do textových polí v podokně Akce a klikněte na tlačítko **vložit**.  
  
## <a name="next-steps"></a>Další kroky  
 Tady jsou některé úlohy, které by mohl pocházet Další:  
  
-   Vytvořte podokna akcí v aplikaci Excel. Další informace najdete v tématu [postupy: Přidání podokna akcí k Excelovým sešitům](/previous-versions/visualstudio/visual-studio-2010/e3zbk0hz(v=vs.100)).  
  
-   Vytvoření vazby dat k ovládacím prvkům v podokně Akce. Další informace najdete v tématu [návod: vytvoření vazby dat s ovládacími prvky v podokně akcí aplikace Word](../vsto/walkthrough-binding-data-to-controls-on-a-word-actions-pane.md).  
  
## <a name="see-also"></a>Viz také:  
 [Přehled podokna akcí](../vsto/actions-pane-overview.md)   
 [Postupy: Přidání podokna akcí do dokumentů aplikace Word nebo sešitů aplikace Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)   
 [Postupy: Přidání podokna akcí k Excelovým sešitům](/previous-versions/visualstudio/visual-studio-2010/e3zbk0hz(v=vs.100))   
 [Postupy: Správa rozložení ovládacích prvků v podoknech akcí](../vsto/how-to-manage-control-layout-on-actions-panes.md)   
 [BOOKMARK – ovládací prvek](../vsto/bookmark-control.md)  
  
  