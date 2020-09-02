---
title: 'Návod: svázání dat s ovládacími prvky v podokně akcí aplikace Word'
ms.date: 02/02/2017
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
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: ddeba1539cf68d53f4b9f931d2bcd18a159028fd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "64802659"
---
# <a name="walkthrough-bind-data-to-controls-on-a-word-actions-pane"></a>Návod: svázání dat s ovládacími prvky v podokně akcí aplikace Word
  Tento návod ukazuje datovou vazbu k ovládacím prvkům v podokně akce ve Wordu. Ovládací prvky ukazují relaci hlavního/podrobností mezi tabulkami v SQL Server databázi.

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

 Tento návod znázorňuje následující úlohy:

- Vytvoření podokna akcí s model Windows Forms ovládacími prvky, které jsou vázány na data.

- Použití vztahu Master/Detail k zobrazení dat v ovládacích prvcích.

- Po otevření aplikace zobrazit podokno akcí

> [!NOTE]
> Váš počítač může v následujících pokynech zobrazovat odlišné názvy nebo umístění některých prvků uživatelského rozhraní sady Visual Studio. Tyto prvky jsou určeny edicí sady Visual Studio a použitým nastavením. Další informace najdete v tématu [Přizpůsobení integrovaného vývojového prostředí (IDE) sady Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Předpoklady
 K dokončení tohoto návodu budete potřebovat následující komponenty:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] nebo [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)]:

- Přístup k serveru s ukázkovou databází Northwind SQL Server.

- Oprávnění ke čtení a zápisu do databáze SQL Server.

## <a name="create-the-project"></a>Vytvoření projektu
 Prvním krokem je vytvoření projektu wordového dokumentu.

### <a name="to-create-a-new-project"></a>Vytvoření nového projektu

1. Vytvořte projekt wordového dokumentu pomocí **podokna akce název moje aplikace Word**. V průvodci vyberte možnost **vytvořit nový dokument**.

     Další informace najdete v tématu [Postupy: vytváření projektů pro systém Office v sadě Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     Visual Studio otevře nový wordový dokument v návrháři a přidá projekt **podokna akce mých slov** do **Průzkumník řešení**.

## <a name="add-controls-to-the-actions-pane"></a>Přidání ovládacích prvků do podokna akce
 Pro tento návod budete potřebovat ovládací prvek podokna akce, který obsahuje ovládací prvky pro model Windows Forms vázané na data. Přidejte do projektu zdroj dat a přetáhněte ovládací prvky z okna **zdroje dat** do ovládacího prvku podokno akcí.

### <a name="to-add-an-actions-pane-control"></a>Přidání ovládacího prvku podokna akce

1. Vyberte projekt **podokna akce v aplikaci Word** v **Průzkumník řešení**.

2. V nabídce **projekt** klikněte na příkaz **Přidat novou položku**.

3. V dialogovém okně **Přidat novou položku** vyberte možnost **ovládací prvek podokno akce**, pojmenujte ji **ActionsControl**a pak klikněte na tlačítko **Přidat**.

### <a name="to-add-a-data-source-to-the-project"></a>Přidání zdroje dat do projektu

1. Pokud není okno **zdroje dat** viditelné, zobrazte ho tak, že v řádku nabídek vyberete možnost **Zobrazit**  >  **ostatní**  >  **zdroje dat**Windows.

   > [!NOTE]
   > Pokud možnost **Zobrazit zdroje dat** není k dispozici, klikněte na dokument aplikace Word a pak znovu zkontrolujte.

2. Kliknutím na tlačítko **Přidat nový zdroj dat** spusťte **Průvodce konfigurací zdroje dat**.

3. Vyberte **databáze** a pak klikněte na **Další**.

4. Vyberte datové připojení k ukázce databáze Northwind SQL Server databázi nebo přidejte nové připojení pomocí tlačítka **nové připojení** .

5. Klikněte na **Next** (Další).

6. Zrušte zaškrtnutí políčka Uložit připojení, pokud je vybráno, a poté klikněte na tlačítko **Další**.

7. Rozbalte uzel **tabulky** v okně **objekty databáze** .

8. Zaškrtněte políčko vedle tabulky **Dodavatelé** a **produkty** .

9. Klikněte na **Finish** (Dokončit).

   Průvodce přidá tabulku **Dodavatelé** a **produkty** do okna **zdroje dat** . Také přidá do projektu typovou datovou sadu, která je viditelná v **Průzkumník řešení**.

### <a name="to-add-data-bound-windows-forms-controls-to-an-actions-pane-control"></a>Přidání ovládacích prvků model Windows Forms vázaných na data do ovládacího prvku podokna akcí

1. V okně **zdroje dat** rozbalte tabulku **Dodavatelé** .

2. Klikněte na šipku rozevíracího seznamu v uzlu **název společnosti** a vyberte položku **ComboBox**.

3. Přetáhněte **CompanyName** z okna **zdroje dat** do ovládacího prvku podokno akcí.

     <xref:System.Windows.Forms.ComboBox>Ovládací prvek je vytvořen v ovládacím prvku podokno akce. Ve stejnou dobu se <xref:System.Windows.Forms.BindingSource> `SuppliersBindingSource` <xref:System.Data.DataSet> do projektu v zásobníku komponent přidají pouze pojmenované, adaptér s tabulkou a.

4. `SuppliersBindingNavigator`V části přihrádka **součásti** vyberte a stiskněte klávesu **Delete**. V tomto návodu nebudete používat `SuppliersBindingNavigator` .

    > [!NOTE]
    > Odstraněním se `SuppliersBindingNavigator` neodebere veškerý kód, který se pro něj vygeneroval. Tento kód můžete odebrat.

5. Přesuňte pole se seznamem tak, aby bylo pod popiskem, a změňte vlastnost **Size** na **171, 21**.

6. V okně **zdroje dat** rozbalte tabulku Products ( **produkty** ), která je podřízenou položkou tabulky **Dodavatelé** .

7. V uzlu **NázevVýrobku** klikněte na šipku rozevíracího seznamu a vyberte položku **seznam**.

8. Přetáhněte **NázevVýrobku** do ovládacího prvku podokno akcí.

     <xref:System.Windows.Forms.ListBox>Ovládací prvek je vytvořen v ovládacím prvku podokno akce. Současně se <xref:System.Windows.Forms.BindingSource> `ProductBindingSource` do projektu v zásobníku komponent přidají pouze pojmenované a tabulkové adaptéry.

9. Přesuňte seznam tak, aby byl pod popiskem, a změňte vlastnost **Size** na hodnotu **171, 95**.

10. Přetáhněte <xref:System.Windows.Forms.Button> z **panelu nástrojů** do ovládacího prvku podokno akcí a umístěte jej pod seznam.

11. Klikněte pravým tlačítkem myši na <xref:System.Windows.Forms.Button> , v místní nabídce klikněte na **vlastnosti** a změňte následující vlastnosti.

    |Vlastnost|Hodnota|
    |--------------|-----------|
    |**Název**|**Insert**|
    |**Text**|**Insert**|

12. Změňte velikost uživatelského ovládacího prvku tak, aby odpovídala ovládacím prvkům.

## <a name="set-up-the-data-source"></a>Nastavení zdroje dat
 Chcete-li nastavit zdroj dat, přidejte kód do <xref:System.Windows.Forms.UserControl.Load> události ovládacího prvku podokna akce pro vyplnění ovládacího prvku daty z rozhraní <xref:System.Data.DataTable> a nastavte <xref:System.Windows.Forms.Binding.DataSource%2A> <xref:System.Windows.Forms.BindingSource.DataMember%2A> vlastnosti a pro každý ovládací prvek.

### <a name="to-load-the-control-with-data"></a>Načtení ovládacího prvku s daty

1. V <xref:System.Windows.Forms.UserControl.Load> obslužné rutině události `ActionsControl` třídy přidejte následující kód.

     [!code-vb[Trin_VstcoreActionsPaneWord#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ActionsControl.vb#1)]
     [!code-csharp[Trin_VstcoreActionsPaneWord#1](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ActionsControl.cs#1)]

2. V jazyce C# je nutné k události připojit obslužnou rutinu události <xref:System.Windows.Forms.UserControl.Load> . Tento kód lze umístit do `ActionsControl` konstruktoru po volání `InitializeComponent` . Další informace o tom, jak vytvořit obslužné rutiny událostí, naleznete v tématu [How to: Create event handlers in Office Projects](../vsto/how-to-create-event-handlers-in-office-projects.md).

     [!code-csharp[Trin_VstcoreActionsPaneWord#33](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ActionsControl.cs#33)]

### <a name="to-set-data-binding-properties-of-the-controls"></a>Nastavení vlastností datových vazeb ovládacích prvků

1. Vyberte `CompanyNameComboBox` ovládací prvek.

2. V okně **vlastnosti** klikněte na tlačítko napravo od vlastnosti **DataSource** a vyberte **suppliersBindingSource**.

3. Klikněte na tlačítko napravo od vlastnosti **DisplayMember** a vyberte **CompanyName**.

4. Rozbalte vlastnost **DataBindings** , klikněte na tlačítko napravo od vlastnosti **text** a vyberte možnost **žádná**.

5. Vyberte `ProductNameListBox` ovládací prvek.

6. V okně **vlastnosti** klikněte na tlačítko napravo od vlastnosti **DataSource** a vyberte **ProductsBindingSource**.

7. Klikněte na tlačítko napravo od vlastnosti **DisplayMember** a vyberte **NázevVýrobku**.

8. Rozbalte vlastnost **DataBindings** , klikněte na tlačítko napravo od vlastnosti **SelectedValue** a vyberte **None (žádné**).

## <a name="add-a-method-to-insert-data-into-a-table"></a>Přidání metody pro vložení dat do tabulky
 Dalším úkolem je přečíst data z vázaných ovládacích prvků a naplnit tabulku v dokumentu aplikace Word. Nejprve vytvořte proceduru pro formátování nadpisů v tabulce a potom přidejte `AddData` metodu pro vytvoření a formátování tabulky aplikace Word.

### <a name="to-format-the-table-headings"></a>Formátování záhlaví tabulky

1. Ve `ActionsControl` třídě vytvořte metodu pro formátování záhlaví tabulky.

     [!code-vb[Trin_VstcoreActionsPaneWord#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ActionsControl.vb#2)]
     [!code-csharp[Trin_VstcoreActionsPaneWord#2](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ActionsControl.cs#2)]

### <a name="to-create-the-table"></a>Vytvoření tabulky

1. Ve `ActionsControl` třídě napište metodu, která vytvoří tabulku, pokud ještě neexistuje, a přidejte data z podokna akce do tabulky.

     [!code-vb[Trin_VstcoreActionsPaneWord#3](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ActionsControl.vb#3)]
     [!code-csharp[Trin_VstcoreActionsPaneWord#3](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ActionsControl.cs#3)]

### <a name="to-insert-text-into-a-word-table"></a>Vložení textu do tabulky aplikace Word

1. Přidejte následující kód do <xref:System.Windows.Forms.Control.Click> obslužné rutiny události tlačítka **Vložit** .

     [!code-vb[Trin_VstcoreActionsPaneWord#4](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ActionsControl.vb#4)]
     [!code-csharp[Trin_VstcoreActionsPaneWord#4](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ActionsControl.cs#4)]

2. V jazyce C# je nutné vytvořit obslužnou rutinu události pro <xref:System.Windows.Forms.Control.Click> Událost tlačítka.  Tento kód lze umístit do <xref:System.Windows.Forms.UserControl.Load> obslužné rutiny události `ActionsControl` třídy.

     [!code-csharp[Trin_VstcoreActionsPaneWord#5](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ActionsControl.cs#5)]

## <a name="show-the-actions-pane"></a>Zobrazit podokno akcí
 Podokno akce se zobrazí po přidání ovládacích prvků do něj.

### <a name="to-show-the-actions-pane"></a>Zobrazení podokna akce

1. V **Průzkumník řešení**klikněte pravým tlačítkem na **ThisDocument. vb** nebo **ThisDocument.cs**a pak klikněte na **Zobrazit kód** v místní nabídce.

2. Vytvořte novou instanci ovládacího prvku v horní části `ThisDocument` třídy tak, aby vypadala jako v následujícím příkladu.

     [!code-csharp[Trin_VstcoreActionsPaneWord#6](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#6)]
     [!code-vb[Trin_VstcoreActionsPaneWord#6](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#6)]

3. Přidejte kód do <xref:Microsoft.Office.Tools.Word.Document.Startup> obslužné rutiny události pro, aby vypadal `ThisDocument` jako v následujícím příkladu.

     [!code-csharp[Trin_VstcoreActionsPaneWord#7](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#7)]
     [!code-vb[Trin_VstcoreActionsPaneWord#7](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#7)]

## <a name="test-the-application"></a>Testování aplikace
 Nyní můžete testovat dokument a ověřit tak, že se podokno akce zobrazí při otevření dokumentu. Otestujte vztah hlavní/podrobnosti v ovládacích prvcích podokna akce a ujistěte se, že jsou data v tabulce aplikace Word při kliknutí na tlačítko **Vložit** vyplněna.

### <a name="to-test-your-document"></a>Testování dokumentu

1. Stisknutím klávesy **F5** spusťte projekt.

2. Potvrďte, že je podokno akce viditelné.

3. V poli se seznamem vyberte společnost a ověřte, že se položky v seznamu **produkty** změnily.

4. Vyberte produkt, v podokně Akce klikněte na možnost **Vložit** a ověřte, zda jsou do tabulky v aplikaci Word přidány podrobnosti o produktu.

5. Vložte další produkty z různých společností.

## <a name="next-steps"></a>Další kroky
 Tento názorný postup ukazuje základy vázání dat k ovládacím prvkům v podokně akcí ve Wordu. Tady jsou některé úkoly, které mohou být další:

- Svázání dat s ovládacími prvky v aplikaci Excel. Další informace najdete v tématu [Návod: svázání dat s ovládacími prvky v podokně akcí aplikace Excel](../vsto/walkthrough-binding-data-to-controls-on-an-excel-actions-pane.md).

- Nasazení projektu. Další informace najdete v tématu [nasazení řešení pro systém Office pomocí technologie ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md).

## <a name="see-also"></a>Viz také
- [Přehled podokna akcí](../vsto/actions-pane-overview.md)
- [Postupy: Přidání podokna akcí do dokumentů aplikace Word nebo sešitů aplikace Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)
- [Vázání dat k ovládacím prvkům v řešeních pro systém Office](../vsto/binding-data-to-controls-in-office-solutions.md)
