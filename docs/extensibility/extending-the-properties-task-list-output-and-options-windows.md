---
title: Rozšíření oken Vlastnosti, Seznam úkolů, Výstup, Možnosti
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- properties pane
- task list
- output window
- properties window
- tutorials
- tool windows
ms.assetid: 06990510-5424-44b8-9fd9-6481acec5c76
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: db14068c97ff6868f5fb73c9ddd790020e99e7c8
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711639"
---
# <a name="extend-the-properties-task-list-output-and-options-windows"></a>Rozšíření oken Vlastnosti, Seznam úkolů, Výstup a Možnosti
V sadě Visual Studio máte přístup k libovolnému oknu nástroje. Tento návod ukazuje, jak integrovat informace o okně nástroje do nové stránky **Možnosti** a nové nastavení na stránce **Vlastnosti** a také jak psát do oken **Seznam úkolů** a **Výstup.**

## <a name="prerequisites"></a>Požadavky
 Počínaje Visual Studio 2015 neinstalujete sady Visual Studio SDK ze služby stažení. Je součástí volitelné funkce v nastavení sady Visual Studio. VS SDK můžete také nainstalovat později. Další informace naleznete [v tématu Instalace sady Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-an-extension-with-a-tool-window"></a>Vytvoření rozšíření s oknem nástroje

1. Vytvořte projekt s názvem **TodoList** pomocí šablony VSIX a přidejte vlastní šablonu položky okna nástroje s názvem **TodoWindow**.

    > [!NOTE]
    > Další informace o vytvoření rozšíření pomocí okna nástroje naleznete v [tématu Vytvoření rozšíření s oknem nástroje](../extensibility/creating-an-extension-with-a-tool-window.md).

## <a name="set-up-the-tool-window"></a>Nastavení okna nástroje
 Přidejte textbox, do kterého chcete zadat novou položku úkolů, tlačítko pro přidání nové položky do seznamu a listbox pro zobrazení položek v seznamu.

1. V *souboru TodoWindow.xaml*odstraňte ovládací prvky Button, TextBox a StackPanel z ovládacího prvku UserControl.

    > [!NOTE]
    > Tím se neodstraní obslužná rutina **události button1_Click,** kterou znovu použijete v pozdějším kroku.

2. V části **Všechny ovládací prvky WPF** v **panelu nástrojů**přetáhněte ovládací prvek **Plátno** do mřížky.

3. Přetáhněte **textbox**, **tlačítko**a **listbox** na základní stránku. Uspořádejte prvky tak, aby textbox a button jsou na stejné úrovni a ListBox vyplní zbytek okna pod nimi, jako na obrázku níže.

     ![Okno dokončeného nástroje](../extensibility/media/t5-toolwindow.png "Okno nástroje T5")

4. V podokně XAML najděte tlačítko a nastavte jeho vlastnost Obsah na **Přidat**. Znovu připojte obslužnou rutinu `Click="button1_Click"` události tlačítka k ovládacímu prvku Button přidáním atributu. Blok Plátno by měl vypadat takto:

    ```xml
    <Canvas HorizontalAlignment="Left" Width="306">
        <TextBox x:Name="textBox" HorizontalAlignment="Left" Height="23" Margin="10,10,0,0" TextWrapping="Wrap" Text="TextBox" VerticalAlignment="Top" Width="208"/>
            <Button x:Name="button" Content="Add" HorizontalAlignment="Left" Margin="236,13,0,0" VerticalAlignment="Top" Width="48" Click="button1_Click"/>
            <ListBox x:Name="listBox" HorizontalAlignment="Left" Height="222" Margin="10,56,0,0" VerticalAlignment="Top" Width="274"/>
    </Canvas>
    ```

### <a name="customize-the-constructor"></a>Přizpůsobení konstruktoru

1. Do *TodoWindowControl.xaml.cs* souboru přidejte následující direktivu using:

    ```csharp
    using System;
    ```

2. Přidejte veřejný odkaz na TodoWindow a mají TodoWindowControl konstruktor trvat TodoWindow parametr. Kód by měl vypadat takto:

    ```csharp
    public TodoWindow parent;

    public TodoWindowControl(TodoWindow window)
    {
        InitializeComponent();
        parent = window;
    }
    ```

3. V *TodoWindow.cs*změňte konstruktor TodoWindowControl tak, aby zahrnoval parametr TodoWindow. Kód by měl vypadat takto:

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
 V dialogovém okně **Možnosti** můžete zadat stránku, aby uživatelé mohli změnit nastavení okna nástroje. Vytvoření stránky Možnosti vyžaduje jak třídu, která popisuje možnosti, tak položku v *souboru TodoListPackage.cs* nebo *TodoListPackage.vb.*

1. Přidejte třídu s názvem `ToolsOptions.cs`. Aby `ToolsOptions` třída dědila z <xref:Microsoft.VisualStudio.Shell.DialogPage>.

   ```csharp
   class ToolsOptions : DialogPage
   {
   }
   ```

2. Přidejte následující pomocí směrnice:

   ```csharp
   using Microsoft.VisualStudio.Shell;
   ```

3. Stránka Možnosti v tomto návodu poskytuje pouze jednu možnost s názvem DaysAhead. Přidejte do `ToolsOptions` třídy soukromé pole s názvem **daysAhead** a vlastnost s názvem **DaysAhead:**

   ```csharp
   private double daysAhead;

   public double DaysAhead
   {
       get { return daysAhead; }
       set { daysAhead = value; }
   }
   ```

   Nyní je nutné, aby projekt vědomi této stránky možnosti.

### <a name="make-the-options-page-available-to-users"></a>Zpřístupnění stránky Možnosti uživatelům

1. V *TodoWindowPackage.cs*přidejte a <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> do `TodoWindowPackage` třídy:

    ```csharp
    [ProvideOptionPage(typeof(ToolsOptions), "ToDo", "General", 101, 106, true)]
    ```

2. První parametr konstruktoru ProvideOptionPage je typ `ToolsOptions`třídy , kterou jste vytvořili dříve. Druhý parametr, "ToDo", je název kategorie v dialogovém okně **Možnosti.** Třetí parametr, "Obecné", je název podkategorie dialogového okna **Možnosti,** kde bude k dispozici stránka Možnosti. Další dva parametry jsou ID prostředků pro řetězce; první je název kategorie a druhý je název podkategorie. Konečný parametr určuje, zda tato stránka lze přistupovat pomocí automatizace.

     Když uživatel otevře stránku Možnosti, měla by se podobat následujícímu obrázku.

     ![Stránka Možnosti](../extensibility/media/t5optionspage.gif "T5OptionsPage")

     Všimněte si kategorie **ToDo** a podkategorie **Obecné**.

## <a name="make-data-available-to-the-properties-window"></a>Zpřístupnění dat v okně Vlastnosti
 Informace seznamu úkolů můžete zpřístupnit vytvořením `TodoItem` třídy s názvem, která ukládá informace o jednotlivých položkách v seznamu úkolů.

1. Přidejte třídu s názvem `TodoItem.cs`.

     Pokud je okno nástroje k dispozici uživatelům, položky v listboxu budou reprezentovány položky TodoItems. Když uživatel vybere jednu z těchto položek v ListBox, okno **Vlastnosti** zobrazí informace o položce.

     Chcete-li zpřístupnit data v okně **Vlastnosti,** přepněte data na `Description` veřejné `Category`vlastnosti, které mají dva speciální atributy a . `Description`je text, který se zobrazí v dolní části okna **Vlastnosti.** `Category`určuje, kde se má vlastnost zobrazit, když se okno **Vlastnosti** zobrazí v zobrazení **Kategorizované.** Na následujícím obrázku je okno **Vlastnosti** v zobrazení **Kategorizované,** je vybrána vlastnost **Název** v kategorii **Pole todo** a v dolní části okna se zobrazí popis vlastnosti **Name.**

     ![Okno Vlastnosti](../extensibility/media/t5properties.png "T5Vlastnosti")

2. Pomocí direktiv přidejte následující příkazy *TodoItem.cs* soubor.

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

     Přidejte dvě `Name` vlastnosti a `DueDate`. Uděláme to a `UpdateList()` `CheckForErrors()` později.

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

4. Přidejte soukromý odkaz na uživatelský ovládací prvek. Přidejte konstruktor, který přebírá uživatelský ovládací prvek a název této položky samávka. Chcete-li najít `daysAhead`hodnotu pro , získá vlastnost stránky Možnosti.

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

5. Vzhledem k `TodoItem` tomu, že instance třídy budou uloženy `ToString` v ListBox a `ToString` ListBox bude volat funkci, musíte přetížit funkci. Přidejte následující kód do *TodoItem.cs*, za konstruktor a před koncem třídy.

    ```csharp
    public override string ToString()
    {
        return name + " Due: " + dueDate.ToShortDateString();
    }
    ```

6. V *TodoWindowControl.xaml.cs*přidejte metody `TodoWindowControl` se zakázaným inzerováním do třídy `CheckForError` pro metody a. `UpdateList` Vložte je za ProcessDialogChar a před koncem souboru.

    ```csharp
    public void CheckForErrors()
    {
    }
    public void UpdateList(TodoItem item)
    {
    }
    ```

     Metoda `CheckForError` bude volat metodu, která má stejný název v nadřazeném objektu a tato metoda zkontroluje, zda došlo k chybám a správně je zpracovat. Metoda `UpdateList` aktualizuje ListBox v nadřazeném ovládacím prvku; metoda je volána `Name` `DueDate` při změně vlastností a v této třídě. Budou realizovány později.

## <a name="integrate-into-the-properties-window"></a>Integrace do okna Vlastnosti
 Nyní napište kód, který spravuje ListBox, který bude vázán na okno **Vlastnosti.**

 Chcete-li číst textovou pole, vytvořit položku TodoItem a přidá ji do pole se seznamem, je nutné změnit obslužnou rutinu kliknutí na tlačítko.

1. Nahraďte `button1_Click` existující funkci kódem, který vytvoří novou položku TodoItem a přidá ji do seznamu ListBox. Volání `TrackSelection()`, které budou definovány později.

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

2. V návrhovém zobrazení vyberte ovládací prvek ListBox. V okně **Vlastnosti** klepněte na tlačítko **Obslužné rutiny události** a vyhledejte událost **SelectionChanged.** Vyplňte textové pole **listBox_SelectionChanged**. Tím přidáte zástupný kód pro obslužnou rutinu SelectionChanged a přiřadí ji k události.

3. Implementujte `TrackSelection()` metodu. Vzhledem k tomu, <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> že budete muset <xref:Microsoft.VisualStudio.Shell.WindowPane.GetService%2A> získat služby, je třeba zpřístupnit TodoWindowControl. Do třídy `TodoWindow` přidejte následující metodu:

    ```
    internal object GetVsService(Type service)
    {
        return GetService(service);
    }
    ```

4. Do *TodoWindowControl.xaml.cs*přidejte následující pomocí direktiv :

    ```csharp
    using System.Runtime.InteropServices;
    using Microsoft.VisualStudio.Shell.Interop;
    using Microsoft.VisualStudio;
    using Microsoft.VisualStudio.Shell;
    ```

5. Vyplňte obslužnou rutinu SelectionChanged takto:

    ```
    private void listBox_SelectionChanged(object sender, SelectionChangedEventArgs e)
    {
        TrackSelection();
    }
    ```

6. Nyní vyplňte funkci TrackSelection, která bude poskytovat integraci s oknem **Vlastnosti.** Tato funkce je volána, když uživatel přidá položku do seznamu listového pole nebo klepne na položku v listovém poli. Přidá obsah ListBox do SelectionContainer a předá SelectionContainer do obslužné <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> rutiny události okna **Vlastnosti.** Služba TrackSelection sleduje vybrané objekty v uživatelském rozhraní (UI) a zobrazuje jejich vlastnosti

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

     Nyní, když máte třídu, kterou může použít okno **Vlastnosti,** můžete integrovat okno **Vlastnosti** s oknem nástroje. Když uživatel klepne na položku v listovém rámečku v okně nástroje, okno **Vlastnosti** by mělo být odpovídajícím způsobem aktualizováno. Podobně když uživatel změní položku ToDo v okně **Vlastnosti,** měla by být aktualizována přidružená položka.

7. Nyní přidejte zbytek kódu funkce UpdateList v *TodoWindowControl.xaml.cs*. By měl přetažení a znovu přidat upravené TodoItem z ListBox.

    ```csharp
    public void UpdateList(TodoItem item)
    {
        var index = listBox.SelectedIndex;
        listBox.Items.RemoveAt(index);
        listBox.Items.Insert(index, item);
        listBox.SelectedItem = index;
    }
    ```

8. Otestujte svůj kód. Sestavení projektu a začít ladění. Experimentální instance by se měla zobrazit.

9. Otevřete stránku**Možnosti** **nástrojů.** >  V levém podokně by se měla zobrazit kategorie ToDo. Kategorie jsou uvedeny v abecedě, takže se podívejte pod Ts.

10. Na stránce Možnosti **todo** by `DaysAhead` se měla zobrazit vlastnost nastavená na **0**. Změňte ji na **2**.

11. V nabídce **Zobrazení / Ostatní Windows** otevřete **todoWindow**. Do textového pole zadejte **Datum ukončení** a klepněte na **tlačítko Přidat**.

12. V seznamu byste měli vidět datum o dva dny později než dnes.

## <a name="add-text-to-the-output-window-and-items-to-the-task-list"></a>Přidání textu do okna Výstup a položek do seznamu úkolů
 Pro **seznam úkolů**vytvoříte nový objekt typu Úkol a potom přidáte tento objekt `Add` Úkol do seznamu **úkolů** voláním jeho metody. Chcete-li zapisovat do `GetPane` okna **Výstup,** volání jeho metoda `OutputString` získat objekt podokna a potom volat metodu panelu objektu.

1. V *TodoWindowControl.xaml.cs*přidejte do `button1_Click` metody kód, který získá **podokno Obecné** v okně **Výstup** (což je výchozí nastavení) a zapíše se do něj. Metoda by měla vypadat takto:

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

2. Chcete-li přidat položky do seznamu úkolů, potřebujete přidat vnořenou třídu do třídy TodoWindowControl. Vnořená třída musí <xref:Microsoft.VisualStudio.Shell.TaskProvider>být odvozena z . Přidejte následující kód na `TodoWindowControl` konec třídy.

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

3. Dále přidejte soukromý `TodoTaskProvider` odkaz `CreateProvider()` a `TodoWindowControl` metodu do třídy. Kód by měl vypadat takto:

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

4. Přidat `ClearError()`, který vymaže seznam úkolů a `ReportError()`, který `TodoWindowControl` přidá položku do seznamu úkolů, do třídy.

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

5. Nyní implementujte metodu `CheckForErrors` takto.

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

## <a name="try-it-out"></a>Vyzkoušejte si to.

1. Sestavení projektu a začít ladění. Zobrazí se experimentální instance.

2. Otevřete **todowindow** **(Zobrazit** > **ostatní windows** > **todowindow**).

3. Zadejte něco do textového pole a klepněte na **tlačítko Přidat**.

     Do seznamu je přidáno datum splatnosti 2 dny po dnešku. Nejsou generovány žádné chyby a **seznam úkolů** (**Zobrazit** > **seznam úkolů**) by neměl mít žádné položky.

4. Nyní změňte nastavení na stránce **Nástroje** > **možnosti** > **ToDo** od **2** zpět na **0**.

5. Do **okna TodoWindow** zadejte něco jiného a pak znovu klikněte na **Přidat.** Tím se spustí chyba a také položka v **seznamu úkolů**.

     Při přidávání položek je počáteční datum nastaveno na nyní plus 2 dny.

6. V nabídce **View** klikněte na **Output** a otevřete okno **Výstup.**

     Všimněte si, že při každém přidání položky se v podokně **Seznam úloh** zobrazí zpráva.

7. Klikněte na jednu z položek v listboxu.

     Okno **Vlastnosti** zobrazí dvě vlastnosti položky.

8. Změňte jednu z vlastností a stiskněte **Enter**.

     Položka je aktualizována v listboxu.
