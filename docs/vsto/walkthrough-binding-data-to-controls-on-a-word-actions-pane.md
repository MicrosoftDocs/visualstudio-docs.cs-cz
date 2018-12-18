---
title: 'Návod: Vytvoření vazby dat s ovládacími prvky v podokně akcí aplikace Word'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- controls [Office development in Visual Studio], data binding
- actions panes [Office development in Visual Studio], data binding
- data binding [Office development in Visual Studio], smart documents
- data binding [Office development in Visual Studio], actions panes
- actions panes [Office development in Visual Studio], binding controls
- smart documents [Office development in Visual Studio], data binding
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 17daf186920be45a70200cd896a390ab74c4c6d0
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49873887"
---
# <a name="walkthrough-bind-data-to-controls-on-a-word-actions-pane"></a>Návod: Vytvoření vazby dat s ovládacími prvky v podokně akcí aplikace Word
  Tento návod ukazuje vytváření datových vazeb k ovládacím prvkům v podokně akcí ve Wordu. Ovládací prvky ukazují záznamů master/detail relace mezi tabulkami v databázi serveru SQL Server.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 Tento návod znázorňuje následující úlohy:  
  
-   Vytvoření podokna akcí pomocí ovládacích prvků Windows Forms, které jsou vázány na data.  
  
-   Pomocí záznamů master/detail relaci pro zobrazení dat v ovládacích prvcích.  
  
-   Zobrazit podokno akcí, když se aplikace otevře.  
  
> [!NOTE]  
>  Váš počítač může v následujících pokynech zobrazovat odlišné názvy nebo umístění některých prvků uživatelského rozhraní sady Visual Studio. Tyto prvky jsou určeny edicí sady Visual Studio a použitým nastavením. Další informace najdete v tématu [přizpůsobení integrovaného vývojového prostředí sady Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="prerequisites"></a>Požadavky  
 K dokončení tohoto návodu budete potřebovat následující komponenty:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] nebo [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].  
  
-   Přístup k serveru s ukázkovou databází Northwind SQL Server.  
  
-   Oprávnění ke čtení a zápis do databáze serveru SQL Server.  
  
## <a name="create-the-project"></a>Vytvoření projektu  
 Prvním krokem je vytvoření projektu dokumentu aplikace Word.  
  
### <a name="to-create-a-new-project"></a>Chcete-li vytvořit nový projekt  
  
1.  Vytvoření projektu Wordového dokumentu s názvem **Moje podokně akcí aplikace Word**. V průvodci vyberte **vytvoříte nový textový dokument**.  
  
     Další informace najdete v tématu [postupy: vytvoření Office projekty v sadě Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     Visual Studio otevře nový Wordový dokument v návrháři a přidá **Moje podokně akcí aplikace Word** projektu **Průzkumníka řešení**.  
  
## <a name="add-controls-to-the-actions-pane"></a>Přidání ovládacích prvků do podokna akcí  
 V tomto návodu budete potřebovat prvek podokna akce, která obsahuje ovládací prvky Windows Forms vázané na data. Přidat zdroj dat do projektu a potom přetáhněte ovládací prvky z **zdroje dat** okna ovládacího prvku podokna akcí.  
  
### <a name="to-add-an-actions-pane-control"></a>Chcete-li přidat ovládací prvek podokna akce  
  
1.  Vyberte **Moje podokně akcí aplikace Word** projekt **Průzkumníka řešení**.  
  
2.  Na **projektu** nabídky, klikněte na tlačítko **přidat novou položku**.  
  
3.  V **přidat novou položku** dialogu **ovládacího prvku podokna akcí**, pojmenujte ho **ActionsControl**a potom klikněte na tlačítko **přidat**.  
  
### <a name="to-add-a-data-source-to-the-project"></a>Chcete-li přidat zdroj dat do projektu  
  
1. Pokud **zdroje dat** okno se nezobrazuje, zobrazit ho tím, na panelu nabídek, výběrem **zobrazení** > **ostatní Windows**  >   **Zdroje dat**.  
  
   > [!NOTE]  
   >  Pokud **zobrazit zdroje dat** není k dispozici, klikněte na dokumentu aplikace Word a zkontrolovat znovu.  
  
2. Klikněte na tlačítko **přidat nový zdroj dat** spustit **Průvodce konfigurací zdroje dat**.  
  
3. Vyberte **databáze** a potom klikněte na tlačítko **Další**.  
  
4. Vyberte datové připojení k ukázkové databázi Northwind systému SQL Server, nebo přidejte nové připojení s použitím **nové připojení** tlačítko.  
  
5. Klikněte na tlačítko **Další**.  
  
6. Uložit připojení, pokud je zaškrtnuto a pak klikněte na tlačítko Vymazat **Další**.  
  
7. Rozbalte **tabulky** uzlu **databázové objekty** okna.  
  
8. Zaškrtněte políčko vedle položky **Dodavatelé** a **produkty** tabulky.  
  
9. Klikněte na tlačítko **Dokončit**.  
  
   Průvodce přidá **dodavatelů** tabulky a **produkty** tabulky **zdroje dat** okno. Také přidá typové datové sady do projektu, který se zobrazuje **Průzkumníka řešení**.  
  
### <a name="to-add-data-bound-windows-forms-controls-to-an-actions-pane-control"></a>Chcete-li přidat ovládací prvky Windows Forms vázané na data na ovládací prvek podokna akce  
  
1.  V **zdroje dat** okna, rozbalte **Dodavatelé** tabulky.  
  
2.  Klikněte na šipku rozevíracího seznamu **název společnosti** uzel a vyberte možnost **– pole se seznamem**.  
  
3.  Přetáhněte **CompanyName** z **zdroje dat** okna ovládacího prvku podokna akcí.  
  
     A <xref:System.Windows.Forms.ComboBox> ovládací prvek je vytvořen na ovládací prvek podokna akce. Ve stejnou dobu <xref:System.Windows.Forms.BindingSource> s názvem `SuppliersBindingSource`, tabulka adaptéru a <xref:System.Data.DataSet> jsou přidány do projektu v panelu komponent.  
  
4.  Vyberte `SuppliersBindingNavigator` v **komponenty** na hlavním panelu a stiskněte klávesu **odstranit**. Nebudete používat `SuppliersBindingNavigator` v tomto názorném postupu.  
  
    > [!NOTE]  
    >  Odstraňuje `SuppliersBindingNavigator` veškerý kód, který byl vygenerován pro něj nebude odstraněn. Můžete odebrat tento kód.  
  
5.  Přesuňte pole se seznamem tak, aby se v popisku a změnit **velikost** vlastnost **171, 21**.  
  
6.  V **zdroje dat** okna, rozbalte **produkty** tabulka, která je podřízenou **Dodavatelé** tabulky.  
  
7.  Klikněte na šipku rozevíracího seznamu **ProductName** uzel a vyberte možnost **ListBox**.  
  
8.  Přetáhněte **ProductName** do ovládacího prvku podokna akcí.  
  
     A <xref:System.Windows.Forms.ListBox> ovládací prvek je vytvořen na ovládací prvek podokna akce. Ve stejnou dobu <xref:System.Windows.Forms.BindingSource> s názvem `ProductBindingSource` a adaptér tabulky jsou přidány do projektu v panelu komponent.  
  
9. Přesunout do seznamu pole tak, aby se v popisku a změnit **velikost** vlastnost **171,95**.  
  
10. Přetáhněte <xref:System.Windows.Forms.Button> z **nástrojů** do podokna akce řízení a umístěte ho pod pole se seznamem.  
  
11. Klikněte pravým tlačítkem myši <xref:System.Windows.Forms.Button>, klikněte na tlačítko **vlastnosti** v místní nabídce a změnit následující vlastnosti.  
  
    |Vlastnost|Hodnota|  
    |--------------|-----------|  
    |**Jméno**|**Vložit**|  
    |**Text**|**Vložit**|  
  
12. Změna velikosti uživatelského ovládacího prvku podle ovládací prvky.  
  
## <a name="set-up-the-data-source"></a>Nastavit zdroj dat  
 Chcete-li nastavit zdroj dat, přidejte kód pro <xref:System.Windows.Forms.UserControl.Load> události ovládacího prvku podokna akcí tak, aby vyplnil ovládacího prvku s daty z <xref:System.Data.DataTable>a nastavte <xref:System.Windows.Forms.Binding.DataSource%2A> a <xref:System.Windows.Forms.BindingSource.DataMember%2A> vlastnosti pro každý ovládací prvek.  
  
### <a name="to-load-the-control-with-data"></a>Načíst ovládací prvek s daty  
  
1.  V <xref:System.Windows.Forms.UserControl.Load> obslužná rutina události `ActionsControl` třídy, přidejte následující kód.  
  
     [!code-vb[Trin_VstcoreActionsPaneWord#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ActionsControl.vb#1)]
     [!code-csharp[Trin_VstcoreActionsPaneWord#1](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ActionsControl.cs#1)]  
  
2.  V jazyce C#, je nutné připojit obslužná rutina události <xref:System.Windows.Forms.UserControl.Load> událostí. Tento kód v můžete umístit `ActionsControl` konstruktor po volání `InitializeComponent`. Další informace o tom, jak vytváření obslužných rutin událostí, naleznete v tématu [postupy: vytváření obslužných rutin událostí v projektech pro systém Office](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#33](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ActionsControl.cs#33)]  
  
### <a name="to-set-data-binding-properties-of-the-controls"></a>Chcete-li nastavit vlastnosti datové vazby ovládacích prvků  
  
1.  Vyberte `CompanyNameComboBox` ovládacího prvku.  
  
2.  V **vlastnosti** okna, klikněte na tlačítko napravo od **DataSource** vlastnosti a vyberte **suppliersBindingSource**.  
  
3.  Klikněte na tlačítko na pravé straně **DisplayMember** vlastnosti a vyberte **CompanyName**.  
  
4.  Rozbalte **DataBindings** vlastnosti, klikněte na tlačítko napravo od **Text** vlastnosti a vyberte **žádný**.  
  
5.  Vyberte `ProductNameListBox` ovládacího prvku.  
  
6.  V **vlastnosti** okna, klikněte na tlačítko napravo od **DataSource** vlastnosti a vyberte **productsBindingSource**.  
  
7.  Klikněte na tlačítko na pravé straně **DisplayMember** vlastnosti a vyberte **ProductName**.  
  
8.  Rozbalte **DataBindings** vlastnosti, klikněte na tlačítko napravo od **SelectedValue** vlastnosti a vyberte **žádný**.  
  
## <a name="add-a-method-to-insert-data-into-a-table"></a>Přidejte metodu k vložení dat do tabulky  
 Další úlohou je číst data z vázané ovládací prvky a vyplnění tabulky v dokumentu aplikace Word. Nejprve vytvořte proceduru pro formátování čísel v tabulce a pak přidejte `AddData` metodu pro vytvoření a formátování tabulek aplikace Word.  
  
### <a name="to-format-the-table-headings"></a>K formátování záhlaví tabulky  
  
1.  V `ActionsControl` třídy, vytvořte metodu k formátování záhlaví tabulky.  
  
     [!code-vb[Trin_VstcoreActionsPaneWord#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ActionsControl.vb#2)]
     [!code-csharp[Trin_VstcoreActionsPaneWord#2](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ActionsControl.cs#2)]  
  
### <a name="to-create-the-table"></a>Pro vytvoření tabulky  
  
1.  V `ActionsControl` třídy, napíše metoda, která vytvoří tabulku, pokud jeden není již neexistuje a přidat data z podokna akcí do tabulky.  
  
     [!code-vb[Trin_VstcoreActionsPaneWord#3](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ActionsControl.vb#3)]
     [!code-csharp[Trin_VstcoreActionsPaneWord#3](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ActionsControl.cs#3)]  
  
### <a name="to-insert-text-into-a-word-table"></a>Vložit text do tabulek aplikace Word  
  
1.  Přidejte následující kód, který <xref:System.Windows.Forms.Control.Click> obslužná rutina události **vložit** tlačítko.  
  
     [!code-vb[Trin_VstcoreActionsPaneWord#4](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ActionsControl.vb#4)]
     [!code-csharp[Trin_VstcoreActionsPaneWord#4](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ActionsControl.cs#4)]  
  
2.  V jazyce C#, je nutné vytvořit obslužná rutina události <xref:System.Windows.Forms.Control.Click> událost tlačítka.  Můžete umístit tento kód v <xref:System.Windows.Forms.UserControl.Load> obslužná rutina události `ActionsControl` třídy.  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#5](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ActionsControl.cs#5)]  
  
## <a name="show-the-actions-pane"></a>Zobrazit podokno akcí  
 V podokně Akce se zobrazí po ovládací prvky jsou přidány do něj.  
  
### <a name="to-show-the-actions-pane"></a>Chcete-li zobrazit podokno akcí  
  
1.  V **Průzkumníka řešení**, klikněte pravým tlačítkem na **ThisDocument.vb** nebo **ThisDocument.cs**a potom klikněte na tlačítko **zobrazit kód** v místní nabídce.  
  
2.  Vytvořit novou instanci ovládacího prvku v horní části `ThisDocument` třídy tak, aby vypadal jako v následujícím příkladu.  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#6](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#6)]
     [!code-vb[Trin_VstcoreActionsPaneWord#6](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#6)]  
  
3.  Přidejte kód, který <xref:Microsoft.Office.Tools.Word.Document.Startup> obslužná rutina události `ThisDocument` tak, aby vypadal jako v následujícím příkladu.  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#7](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#7)]
     [!code-vb[Trin_VstcoreActionsPaneWord#7](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#7)]  
  
## <a name="test-the-application"></a>Testování aplikace  
 Nyní můžete otestovat váš dokument k ověření, že v podokně Akce se zobrazí, když je dokument otevřít. Testování pro vztah záznamů master/detail v ovládacích prvcích v podokně Akce a ujistěte se, že je slovo vložené data tabulky, když **vložit** po kliknutí na tlačítko.  
  
### <a name="to-test-your-document"></a>K otestování vašeho dokumentu  
  
1.  Stisknutím klávesy **F5** ke spuštění projektu.  
  
2.  Potvrďte, že v podokně Akce je viditelný.  
  
3.  V poli se seznamem vyberte požadovanou společnost a ověřte, že položky v **produkty** seznamu pole změnit.  
  
4.  Vyberte produkt, klikněte na tlačítko **vložit** v podokně akcí a ověřte, že jsou přidány informace o produktech do tabulky v aplikaci Word.  
  
5.  Vložte další produkty od různých společností.  
  
## <a name="next-steps"></a>Další kroky  
 Tento návod ukazuje základy vazba dat k ovládacím prvkům v podokně akcí ve Wordu. Tady jsou některé úlohy, které by mohl pocházet Další:  
  
-   Vazba dat k ovládacím prvkům v aplikaci Excel. Další informace najdete v tématu [návod: vytvoření vazby dat k ovládacím prvkům v podokně akcí aplikace Excel](../vsto/walkthrough-binding-data-to-controls-on-an-excel-actions-pane.md).  
  
-   Nasazení projektu. Další informace najdete v tématu [nasazení řešení Office s použitím technologie ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md).  
  
## <a name="see-also"></a>Viz také:  
 [Přehled podokna akcí](../vsto/actions-pane-overview.md)   
 [Postupy: Přidání podokna akcí do dokumentů aplikace Word nebo sešitů aplikace Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)   
 [Vytvoření vazby dat k ovládacím prvkům v řešeních pro systém Office](../vsto/binding-data-to-controls-in-office-solutions.md)  
  
  