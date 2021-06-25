---
title: Rozšíření vlastností, Seznam úkolů, výstup, okna Možnosti
description: Zjistěte, jak integrovat informace o okně nástroje v Visual Studio do nové stránky Možnosti a nového nastavení na stránce Vlastnosti.
ms.date: 11/04/2016
ms.custom: SEO-VS-2020
ms.topic: how-to
helpviewer_keywords:
- properties pane
- task list
- output window
- properties window
- tutorials
- tool windows
ms.assetid: 06990510-5424-44b8-9fd9-6481acec5c76
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 3334ba3694ee3c1354c152b013c38472e4b90b72
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2021
ms.locfileid: "112903278"
---
# <a name="extend-the-properties-task-list-output-and-options-windows"></a>Rozšíření oken Vlastnosti, Seznam úkolů, Výstup a Možnosti
Přístup k libovolnému oknu nástroje v Visual Studio. Tento názorný postup ukazuje, jak integrovat  informace o okně nástroje  do nové stránky Možnosti a nové nastavení na stránce Vlastnosti a také jak zapisovat do oken **Seznam úkolů** a **Výstup.**

## <a name="prerequisites"></a>Požadavky
 Od Visual Studio 2015 neinstalujete sadu Visual Studio SDK ze služby Download Center. Je zahrnutá jako volitelná funkce v Visual Studio nastavení. Sadu VS SDK můžete nainstalovat později. Další informace najdete v tématu [Instalace sady Visual Studio SDK.](../extensibility/installing-the-visual-studio-sdk.md)

## <a name="create-an-extension-with-a-tool-window"></a>Vytvoření rozšíření pomocí okna nástroje

1. Vytvořte projekt s názvem **TodoList** pomocí šablony VSIX a přidejte vlastní šablonu položky okna nástroje s názvem **TodoWindow**.

    > [!NOTE]
    > Další informace o vytvoření rozšíření pomocí okna nástroje najdete v tématu [Vytvoření rozšíření pomocí okna nástroje](../extensibility/creating-an-extension-with-a-tool-window.md).

## <a name="set-up-the-tool-window"></a>Nastavení okna nástroje
 Přidejte textové pole, do kterého chcete zadat novou položku todo, tlačítko pro přidání nové položky do seznamu a listBox pro zobrazení položek v seznamu.

1. V *souboru TodoWindow.xaml* odstraňte ovládací prvky Button, TextBox a StackPanel z UserControl.

    > [!NOTE]
    > Tím se neodstraní **button1_Click** události, kterou použijete v pozdějším kroku.

2. Z části **Všechny ovládací prvky WPF** panelu **nástrojů** přetáhněte ovládací **prvek Plátno** do mřížky.

3. Přetáhněte **TextBox**, **Button** a **ListBox** na plátno. Prvky uspořádejte tak, aby textová pole a tlačítko byly na stejné úrovni, a seznam vyplní zbývající část okna pod nimi, jak je vidět na obrázku níže.

     ![Dokončené okno nástroje](../extensibility/media/t5-toolwindow.png "T5-ToolWindow")

4. V podokně XAML vyhledejte Tlačítko a nastavte jeho vlastnost Content na **Přidat.** Znovu připojte obslužnou rutinu události tlačítka k ovládacímu prvku Tlačítko přidáním `Click="button1_Click"` atributu. Blok plátna by měl vypadat takhle:

    ```xml
    <Canvas HorizontalAlignment="Left" Width="306">
        <TextBox x:Name="textBox" HorizontalAlignment="Left" Height="23" Margin="10,10,0,0" TextWrapping="Wrap" Text="TextBox" VerticalAlignment="Top" Width="208"/>
            <Button x:Name="button" Content="Add" HorizontalAlignment="Left" Margin="236,13,0,0" VerticalAlignment="Top" Width="48" Click="button1_Click"/>
            <ListBox x:Name="listBox" HorizontalAlignment="Left" Height="222" Margin="10,56,0,0" VerticalAlignment="Top" Width="274"/>
    </Canvas>
    ```

### <a name="customize-the-constructor"></a>Přizpůsobení konstruktoru

1. Do souboru *TodoWindowControl.xaml.cs* přidejte následující direktivu using:

    ```csharp
    using System;
    ```

2. Přidejte veřejný odkaz na TodoWindow a konstruktor TodoWindowControl převezměte parametr TodoWindow. Kód by měl vypadat takhle:

    ```csharp
    public TodoWindow parent;

    public TodoWindowControl(TodoWindow window)
    {
        InitializeComponent();
        parent = window;
    }
    ```

3. V *souboru TodoWindow.cs* změňte konstruktor TodoWindowControl tak, aby zahrnoval parametr TodoWindow. Kód by měl vypadat takhle:

    ```csharp
    public TodoWindow() : base(null)
    {
        this.Caption = "TodoWindow";
        this.BitmapResourceID = 301;
        this.BitmapIndex = 1;

         this.Content = new TodoWindowControl(this);
    }
    ```

## <a name="create-an-options-page"></a>Vytvoření stránky Možnosti
 Stránku můžete zadat v dialogovém **okně** Možnosti, aby uživatelé mohli změnit nastavení pro okno nástroje. Vytvoření stránky Možnosti vyžaduje jak třídu, která popisuje možnosti, tak záznam v souboru *TodoListPackage.cs* nebo *TodoListPackage.vb.*

1. Přidejte třídu s názvem `ToolsOptions.cs` . `ToolsOptions`Zajistěte, aby třída dědí z třídy <xref:Microsoft.VisualStudio.Shell.DialogPage> .

   ```csharp
   class ToolsOptions : DialogPage
   {
   }
   ```

2. Přidejte následující direktivu using:

   ```csharp
   using Microsoft.VisualStudio.Shell;
   ```

3. Stránka Možnosti v tomto názorném postupu poskytuje pouze jednu možnost s názvem DaysAhead. Přidejte do třídy soukromé pole s názvem **daysAhead** a vlastnost s názvem **DaysAhead:** `ToolsOptions`

   ```csharp
   private double daysAhead;

   public double DaysAhead
   {
       get { return daysAhead; }
       set { daysAhead = value; }
   }
   ```

   Teď musíte projekt uvědomovat na této stránce Možnosti.

### <a name="make-the-options-page-available-to-users"></a>Z dostupných stránek Možnosti uživatelům

1. V *souboru TodoWindowPackage.cs* přidejte <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> do třídy `TodoWindowPackage` :

    ```csharp
    [ProvideOptionPage(typeof(ToolsOptions), "ToDo", "General", 101, 106, true)]
    ```

2. První parametr konstruktoru ProvideOptionPage je typ třídy `ToolsOptions` , kterou jste vytvořili dříve. Druhý parametr, "ToDo", je název kategorie v **dialogovém okně** Možnosti. Třetí parametr " Obecné" je název podkategorie  dialogového okna Možnosti, kde bude stránka Možnosti dostupná. Další dva parametry jsou ID prostředků pro řetězce. první je název kategorie a druhý je název podkategorie. Poslední parametr určuje, jestli je k této stránce možné přistupovat pomocí automatizace.

     Když uživatel otevře stránku Možnosti, měl by vypadat podobně jako na následujícím obrázku.

     ![Stránka Možnosti](../extensibility/media/t5optionspage.gif "T5OptionsPage")

     Všimněte si kategorie **ToDo** a podkategorie **Obecné**.

## <a name="make-data-available-to-the-properties-window"></a>Získejte data dostupná pro okno Vlastnosti
 Informace o seznamu úkolů můžete nastavit tak, že vytvoříte třídu s názvem , která ukládá informace o jednotlivých položkách `TodoItem` v seznamu Úkolů.

1. Přidejte třídu s názvem `TodoItem.cs` .

     Jakmile bude okno nástroje k dispozici uživatelům, položky v prvku ListBox budou reprezentovány položkou TodoItems. Když uživatel vybere jednu z těchto položek v seznamu ListBox, zobrazí se v **okně Vlastnosti** informace o položce.

     Pokud chcete data v okně **Vlastnosti** z dostupných dat změnit na veřejné vlastnosti, které mají dva speciální atributy, `Description` a `Category` . `Description` je text, který se zobrazí v dolní části **okna** Vlastnosti. `Category` určuje, kde se má vlastnost zobrazit, **když** se okno Vlastnosti zobrazí v zobrazení **Zařazeno do** kategorií. Na následujícím obrázku  je okno  Vlastnosti v zobrazení  Zařazeno do kategorií, v kategorii Pole  **úkolů** je vybraná vlastnost Název a v dolní části okna se zobrazí popis vlastnosti Název.

     ![Okno Vlastnosti](../extensibility/media/t5properties.png "T5Properties")

2. Přidejte následující direktivy using do *souboru TodoItem.cs.*

    ```csharp
    using System.ComponentModel;
    using System.Windows.Forms;
    using Microsoft.VisualStudio.Shell.Interop;
    ```

3. Přidejte `public` modifikátor přístupu do deklarace třídy.

    ```csharp
    public class TodoItem
    {
    }
    ```

     Přidejte dvě vlastnosti a `Name` `DueDate` . A uděláme `UpdateList()` `CheckForErrors()` později.

    ```csharp
    public class TodoItem
    {
        private TodoWindowControl parent;
        private string name;
        [Description("Name of the ToDo item")]
        [Category("ToDo Fields")]
        public string Name
        {
            get { return name; }
            set
            {
                name = value;
                parent.UpdateList(this);
            }
        }

        private DateTime dueDate;
        [Description("Due date of the ToDo item")]
        [Category("ToDo Fields")]
        public DateTime DueDate
        {
            get { return dueDate; }
            set
            {
                dueDate = value;
                parent.UpdateList(this);
                parent.CheckForErrors();
            }
        }
    }
    ```

4. Přidejte privátní odkaz na uživatelský ovládací prvek. Přidejte konstruktor, který převezme uživatelský ovládací prvek a název této položky toDo. Pokud chcete najít hodnotu `daysAhead` pro , získá vlastnost stránky Možnosti.

    ```csharp
    private TodoWindowControl parent;

    public TodoItem(TodoWindowControl control, string itemName)
    {
        parent = control;
        name = itemName;
        dueDate = DateTime.Now;

        double daysAhead = 0;
        IVsPackage package = parent.parent.Package as IVsPackage;
        if (package != null)
        {
            object obj;
            package.GetAutomationObject("ToDo.General", out obj);

            ToolsOptions options = obj as ToolsOptions;
            if (options != null)
            {
                daysAhead = options.DaysAhead;
            }
        }

        dueDate = dueDate.AddDays(daysAhead);
    }
    ```

5. Vzhledem k tomu, že instance třídy budou uloženy v prvku ListBox a listBox bude volat `TodoItem` `ToString` funkci, musíte funkci `ToString` přetížit. Do souboru *TodoItem.cs* přidejte následující kód za konstruktor a před konec třídy .

    ```csharp
    public override string ToString()
    {
        return name + " Due: " + dueDate.ToShortDateString();
    }
    ```

6. V *souboru TodoWindowControl.xaml.cs* přidejte metody zástupných procedur `TodoWindowControl` do třídy pro metody a `CheckForError` `UpdateList` . Umístěte je za ProcessDialogChar a před konec souboru.

    ```csharp
    public void CheckForErrors()
    {
    }
    public void UpdateList(TodoItem item)
    {
    }
    ```

     Metoda zavolá metodu, která má stejný název v nadřazeném objektu, a tato metoda zkontroluje, jestli nedošlo k chybám, a zřídí `CheckForError` je správně. Metoda aktualizuje ListBox v nadřazeném ovládacím prvku. Metoda je volána při změně vlastností a `UpdateList` `Name` v této `DueDate` třídě. Budou implementovány později.

## <a name="integrate-into-the-properties-window"></a>Integrace do okno Vlastnosti
 Teď napište kód, který spravuje ListBox, který bude svázán s **oknem** Vlastnosti.

 Obslužnou rutinu kliknutí na tlačítko musíte změnit tak, aby četla pole TextBox, vytvořila položku TodoItem a přidá ji do prvku ListBox.

1. Nahraďte existující `button1_Click` funkci kódem, který vytvoří novou položku TodoItem a přidá ji do prvku ListBox. Zavolá `TrackSelection()` metodu , která bude definována později.

    ```csharp
    private void button1_Click(object sender, RoutedEventArgs e)
    {
        if (textBox.Text.Length > 0)
        {
            var item = new TodoItem(this, textBox.Text);
            listBox.Items.Add(item);
            TrackSelection();
            CheckForErrors();
        }
    }
    ```

2. V zobrazení Návrh vyberte ovládací prvek ListBox. V okně **Vlastnosti** klikněte na **tlačítko Obslužné rutiny událostí** a vyhledejte událost **SelectionChanged.** Do textového pole zadejte **listBox_SelectionChanged**. Tímto způsobem se přidá zástupná procedura pro obslužnou rutinu SelectionChanged a přiřadí ji k události.

3. Implementujte `TrackSelection()` metodu . Vzhledem k tomu, že budete potřebovat získat služby, musíte objekt přístupně <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> získat pomocí <xref:Microsoft.VisualStudio.Shell.WindowPane.GetService%2A> TodoWindowControl. Do třídy `TodoWindow` přidejte následující metodu:

    ```
    internal object GetVsService(Type service)
    {
        return GetService(service);
    }
    ```

4. Do souboru *TodoWindowControl.xaml.cs* přidejte následující direktivy using :

    ```csharp
    using System.Runtime.InteropServices;
    using Microsoft.VisualStudio.Shell.Interop;
    using Microsoft.VisualStudio;
    using Microsoft.VisualStudio.Shell;
    ```

5. Následujícím způsobem vyplňte obslužnou rutinu SelectionChanged:

    ```
    private void listBox_SelectionChanged(object sender, SelectionChangedEventArgs e)
    {
        TrackSelection();
    }
    ```

6. Teď vyplňte funkci TrackSelection, která zajistí integraci s **oknem** Vlastnosti. Tato funkce se volá, když uživatel přidá položku do prvku ListBox nebo klikne na položku v prvku ListBox. Přidá obsah ListBox do SelectionContainer a předá SelectionContainer **obslužné** rutině události <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> okna Vlastnosti. Služba TrackSelection sleduje vybrané objekty v uživatelském rozhraní a zobrazuje jejich vlastnosti.

    ```csharp
    private SelectionContainer mySelContainer;
    private System.Collections.ArrayList mySelItems;
    private IVsWindowFrame frame = null;

    private void TrackSelection()
    {
        if (frame == null)
        {
            var shell = parent.GetVsService(typeof(SVsUIShell)) as IVsUIShell;
            if (shell != null)
            {
                var guidPropertyBrowser = new
                Guid(ToolWindowGuids.PropertyBrowser);
                shell.FindToolWindow((uint)__VSFINDTOOLWIN.FTW_fForceCreate,
                ref guidPropertyBrowser, out frame);
            }
        }
        if (frame != null)
            {
                frame.Show();
            }
        if (mySelContainer == null)
        {
            mySelContainer = new SelectionContainer();
        }

        mySelItems = new System.Collections.ArrayList();

        var selected = listBox.SelectedItem as TodoItem;
        if (selected != null)
        {
            mySelItems.Add(selected);
        }

        mySelContainer.SelectedObjects = mySelItems;

        ITrackSelection track = parent.GetVsService(typeof(STrackSelection))
                                as ITrackSelection;
        if (track != null)
        {
            track.OnSelectChange(mySelContainer);
        }
    }
    ```

     Teď, když máte třídu, kterou **můžete** použít v okně Vlastnosti, můžete okno **Vlastnosti** integrovat s oknem nástroje. Když uživatel klikne na položku v seznamu ListBox v okně nástroje, mělo by **se okno Vlastnosti** odpovídajícím způsobem aktualizovat. Podobně když uživatel změní položku seznamu todo v **okně Vlastnosti,** měla by se přidružená položka aktualizovat.

7. Teď přidejte zbytek kódu funkce UpdateList do *souboru TodoWindowControl.xaml.cs.* Měl by vypustit a znovu přidat změněný TodoItem ze seznamu ListBox.

    ```csharp
    public void UpdateList(TodoItem item)
    {
        var index = listBox.SelectedIndex;
        listBox.Items.RemoveAt(index);
        listBox.Items.Insert(index, item);
        listBox.SelectedItem = index;
    }
    ```

8. Otestujte svůj kód. Sestavte projekt a spusťte ladění. Měla by se zobrazit experimentální instance.

9. Otevřete stránku  >  **Možnosti** nástrojů. V levém podokně by se měla zobrazit kategorie ToDo. Kategorie jsou uvedeny v abecedním pořadí, takže se podívejte do části TS.

10. Na stránce možnosti **TODO** by se měla zobrazit `DaysAhead` vlastnost nastavená na **hodnotu 0**. Změňte ji na **2**.

11. V nabídce **Zobrazit/další Windows** otevřete **TodoWindow**. Do textového pole zadejte **EndDate** a klikněte na **Přidat**.

12. V poli se seznamem by se mělo zobrazit datum po dvou dnech později než dnes.

## <a name="add-text-to-the-output-window-and-items-to-the-task-list"></a>Přidat text do okna výstup a položky do Seznam úkolů
 Pro **seznam úkolů** vytvoříte nový objekt typu Task a následně do **seznam úkolů** přidáte objekt úlohy voláním jeho `Add` metody. Chcete-li zapisovat do okna **výstup** , zavolejte jeho `GetPane` metodu pro získání objektu podokna a potom zavolejte `OutputString` metodu objektu podokna.

1. V souboru *TodoWindowControl. XAML. cs* v `button1_Click` metodě přidejte kód, který získá **Obecné** podokno okna **výstup** (což je výchozí nastavení), a zapište do něj. Metoda by měla vypadat takto:

    ```csharp
    private void button1_Click(object sender, EventArgs e)
    {
        if (textBox.Text.Length > 0)
        {
            var item = new TodoItem(this, textBox.Text);
            listBox.Items.Add(item);

            var outputWindow = parent.GetVsService(
                typeof(SVsOutputWindow)) as IVsOutputWindow;
            IVsOutputWindowPane pane;
            Guid guidGeneralPane = VSConstants.GUID_OutWindowGeneralPane;
            outputWindow.GetPane(ref guidGeneralPane, out pane);
            if (pane != null)
            {
                 pane.OutputString(string.Format(
                    "To Do item created: {0}\r\n",
                 item.ToString()));
        }
            TrackSelection();
            CheckForErrors();
        }
    }
    ```

2. Chcete-li přidat položky do Seznam úkolů, je nutné přidat vnořenou třídu do třídy TodoWindowControl. Vnořená třída musí být odvozena od třídy <xref:Microsoft.VisualStudio.Shell.TaskProvider> . Do konce třídy přidejte následující kód `TodoWindowControl` .

    ```csharp
    [Guid("72de1eAD-a00c-4f57-bff7-57edb162d0be")]
    public class TodoWindowTaskProvider : TaskProvider
    {
        public TodoWindowTaskProvider(IServiceProvider sp)
            : base(sp)
        {
        }
    }
    ```

3. Dále přidejte soukromý odkaz na `TodoTaskProvider` a `CreateProvider()` metodu do `TodoWindowControl` třídy. Kód by měl vypadat takto:

    ```csharp
    private TodoWindowTaskProvider taskProvider;
    private void CreateProvider()
    {
        if (taskProvider == null)
        {
            taskProvider = new TodoWindowTaskProvider(parent);
            taskProvider.ProviderName = "To Do";
        }
    }
    ```

4. Add `ClearError()` , který vymaže seznam úkolů a `ReportError()` přidá položku do seznam úkolů do `TodoWindowControl` třídy.

    ```csharp
    private void ClearError()
    {
        CreateProvider();
        taskProvider.Tasks.Clear();
    }
    private void ReportError(string p)
    {
        CreateProvider();
        var errorTask = new Task();
        errorTask.CanDelete = false;
        errorTask.Category = TaskCategory.Comments;
        errorTask.Text = p;

        taskProvider.Tasks.Add(errorTask);

        taskProvider.Show();

        var taskList = parent.GetVsService(typeof(SVsTaskList))
            as IVsTaskList2;
        if (taskList == null)
        {
            return;
        }

        var guidProvider = typeof(TodoWindowTaskProvider).GUID;
         taskList.SetActiveProvider(ref guidProvider);
    }
    ```

5. Nyní implementujte `CheckForErrors` metodu následujícím způsobem.

    ```csharp
    public void CheckForErrors()
    {
        foreach (TodoItem item in listBox.Items)
        {
            if (item.DueDate < DateTime.Now)
            {
                ReportError("To Do Item is out of date: "
                    + item.ToString());
            }
        }
    }
    ```

## <a name="try-it-out"></a>Vyzkoušet

1. Sestavte projekt a spusťte ladění. Objeví se experimentální instance.

2. Otevřete **TodoWindow** (**Zobrazit**  >  **Další Windows**  >  **TodoWindow**).

3. Do textového pole zadejte něco a pak klikněte na **Přidat**.

     Datum splatnosti 2 dny od dnešního dne je přidáno do pole seznam. Nejsou generovány žádné chyby a **seznam úkolů** (**zobrazení**  >  **seznam úkolů**) by neměl mít žádné položky.

4. Teď změňte nastavení na stránce možnosti **nástrojů**  >    >  **TODO** **2** zpátky na **0**.

5. Do **TodoWindow** zadejte něco jiného a pak klikněte na **Přidat** znovu. Tím se aktivuje chyba a také záznam v **seznam úkolů**.

     Když přidáváte položky, počáteční datum je nastaveno na nyní plus 2 dny.

6. V nabídce **zobrazení** klikněte na možnost **výstup** . otevře se okno **výstup** .

     Všimněte si, že pokaždé, když přidáte položku, se zobrazí zpráva v podokně **seznam úkolů** .

7. Klikněte na jednu z položek v seznamu.

     V okně **vlastnosti** se zobrazí dvě vlastnosti položky.

8. Změňte jednu z vlastností a potom stiskněte klávesu **ENTER**.

     Položka je aktualizována v seznamu.
