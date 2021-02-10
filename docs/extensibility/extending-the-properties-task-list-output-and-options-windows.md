---
title: Rozšířené vlastnosti, Seznam úkolů, výstup, možnosti Windows
description: Naučte se integrovat informace o okně nástrojů v aplikaci Visual Studio na novou stránku možností a nové nastavení na stránce vlastností.
ms.date: 11/04/2016
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 2586618b16afa8f8bfd6b7aa529486adf1d9ce41
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99938132"
---
# <a name="extend-the-properties-task-list-output-and-options-windows"></a>Rozšíříte okna vlastnosti, Seznam úkolů, výstup a možnosti.
Můžete získat přístup k libovolnému oknu nástrojů v aplikaci Visual Studio. Tento návod ukazuje, jak integrovat informace o okně nástroje na novou stránku **možností** a nové nastavení na stránce **vlastnosti** a také jak zapisovat do oken **seznam úkolů** a **výstupu** .

## <a name="prerequisites"></a>Požadavky
 Od sady Visual Studio 2015 nenainstalujete sadu Visual Studio SDK z webu Stažení softwaru. V instalačním programu sady Visual Studio je zahrnutý jako volitelná funkce. Sadu VS SDK můžete také nainstalovat později. Další informace najdete v tématu [instalace sady Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-an-extension-with-a-tool-window"></a>Vytvoření rozšíření s oknem nástrojů

1. Vytvořte projekt s názvem **TodoList** pomocí šablony VSIX a přidejte šablonu položky vlastního okna nástroje s názvem **TodoWindow**.

    > [!NOTE]
    > Další informace o vytváření rozšíření pomocí okna nástroje naleznete v tématu [Vytvoření rozšíření pomocí okna nástroje](../extensibility/creating-an-extension-with-a-tool-window.md).

## <a name="set-up-the-tool-window"></a>Nastavení okna nástrojů
 Přidejte textové pole, ve kterém chcete zadat novou položku ToDo, tlačítko pro přidání nové položky do seznamu a seznam pro zobrazení položek v seznamu.

1. V souboru *TodoWindow. XAML* odstraňte ovládací prvky Button, TextBox a StackPanel z prvku UserControl.

    > [!NOTE]
    > Tato akce neodstraní obslužnou rutinu události **Button1_Click** , kterou budete znovu používat v pozdějším kroku.

2. V části **všechny ovládací prvky WPF** ovládacího prvku **panel nástrojů** přetáhněte ovládací prvek **plátno** na mřížku.

3. Přetáhněte na plátno **textové pole**, **tlačítko** a **seznam** . Uspořádejte prvky tak, aby textové pole a tlačítko byly na stejné úrovni, a seznam vyplní zbývající část okna pod nimi, jak je znázorněno na obrázku níže.

     ![Okno nástroje dokončeno](../extensibility/media/t5-toolwindow.png "T5-ToolWindow")

4. V podokně XAML najděte tlačítko a nastavte jeho vlastnost obsah na **Přidat**. Znovu připojte obslužnou rutinu události tlačítka k ovládacímu prvku tlačítko přidáním `Click="button1_Click"` atributu. Blok plátna by měl vypadat takto:

    ```xml
    <Canvas HorizontalAlignment="Left" Width="306">
        <TextBox x:Name="textBox" HorizontalAlignment="Left" Height="23" Margin="10,10,0,0" TextWrapping="Wrap" Text="TextBox" VerticalAlignment="Top" Width="208"/>
            <Button x:Name="button" Content="Add" HorizontalAlignment="Left" Margin="236,13,0,0" VerticalAlignment="Top" Width="48" Click="button1_Click"/>
            <ListBox x:Name="listBox" HorizontalAlignment="Left" Height="222" Margin="10,56,0,0" VerticalAlignment="Top" Width="274"/>
    </Canvas>
    ```

### <a name="customize-the-constructor"></a>Přizpůsobení konstruktoru

1. Do souboru *TodoWindowControl.XAML.cs* přidejte následující direktivu using:

    ```csharp
    using System;
    ```

2. Přidejte veřejný odkaz na TodoWindow a mít konstruktor TodoWindowControl, který převezme parametr TodoWindow. Kód by měl vypadat takto:

    ```csharp
    public TodoWindow parent;

    public TodoWindowControl(TodoWindow window)
    {
        InitializeComponent();
        parent = window;
    }
    ```

3. V *TodoWindow.cs* změňte konstruktor TodoWindowControl tak, aby zahrnoval parametr TodoWindow. Kód by měl vypadat takto:

    ```csharp
    public TodoWindow() : base(null)
    {
        this.Caption = "TodoWindow";
        this.BitmapResourceID = 301;
        this.BitmapIndex = 1;

         this.Content = new TodoWindowControl(this);
    }
    ```

## <a name="create-an-options-page"></a>Vytvoření stránky možnosti
 Stránku můžete v dialogovém okně **Možnosti** zadat tak, aby uživatelé mohli měnit nastavení okna nástroje. Vytvoření stránky možnosti vyžaduje třídu, která popisuje možnosti a položku v souboru *TodoListPackage.cs* nebo *TodoListPackage. vb* .

1. Přidejte třídu s názvem `ToolsOptions.cs` . Nastavit `ToolsOptions` třídu jako děděnou z <xref:Microsoft.VisualStudio.Shell.DialogPage> .

   ```csharp
   class ToolsOptions : DialogPage
   {
   }
   ```

2. Přidejte následující direktivu using:

   ```csharp
   using Microsoft.VisualStudio.Shell;
   ```

3. Stránka možnosti v tomto návodu poskytuje jenom jednu možnost s názvem DaysAhead. Přidejte soukromé pole s názvem **daysAhead** a vlastnost s názvem **daysAhead** do `ToolsOptions` třídy:

   ```csharp
   private double daysAhead;

   public double DaysAhead
   {
       get { return daysAhead; }
       set { daysAhead = value; }
   }
   ```

   Nyní je nutné, aby se projekt dozvěděl na této stránce možností.

### <a name="make-the-options-page-available-to-users"></a>Zpřístupnění stránky možnosti uživatelům

1. V *TodoWindowPackage.cs* přidejte <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> do `TodoWindowPackage` třídy:

    ```csharp
    [ProvideOptionPage(typeof(ToolsOptions), "ToDo", "General", 101, 106, true)]
    ```

2. Prvním parametrem konstruktoru ProvideOptionPage je typ třídy `ToolsOptions` , kterou jste vytvořili dříve. Druhým parametrem "ToDo" je název kategorie v dialogovém okně **Možnosti** . Třetí parametr "Obecné" je název podkategorie dialogového okna **Možnosti** , kde bude k dispozici stránka Možnosti. Následující dva parametry jsou ID prostředků pro řetězce; první je název kategorie a druhý je název podkategorie. Konečný parametr určuje, zda je k této stránce možné přistupovat pomocí automatizace.

     Když uživatel otevře stránku s možnostmi, měl by vypadat podobně jako na následujícím obrázku.

     ![Stránka možnosti](../extensibility/media/t5optionspage.gif "T5OptionsPage")

     Všimněte si, že kategorie **TODO** a podkategorie jsou **Obecné**.

## <a name="make-data-available-to-the-properties-window"></a>Zpřístupnění dat okno Vlastnosti
 K dispozici jsou informace o seznamu úkolů, a to vytvořením třídy s názvem `TodoItem` , která ukládá informace o jednotlivých položkách v seznamu TODO.

1. Přidejte třídu s názvem `TodoItem.cs` .

     Když je okno nástroje dostupné pro uživatele, položky v seznamu se reprezentují pomocí TodoItems. Když uživatel vybere jednu z těchto položek v seznamu, zobrazí se v okně **vlastnosti** informace o položce.

     Chcete-li zpřístupnit data v okně **vlastnosti** , převeďte data na veřejné vlastnosti, které mají dva speciální atributy `Description` a `Category` . `Description` je text, který se zobrazí v dolní části okna **vlastnosti** . `Category` Určuje, kde se má vlastnost zobrazit při zobrazení okna **vlastnosti** v zobrazení **kategorized** . Na následujícím obrázku je okno **vlastnosti** v zobrazení **kategorizované** , je vybrána vlastnost **název** v kategorii **pole TODO** a popis vlastnosti **název** se zobrazí v dolní části okna.

     ![Okno vlastností](../extensibility/media/t5properties.png "T5Properties")

2. Do souboru *TodoItem.cs* přidejte následující direktivy using.

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

     Přidejte dvě vlastnosti `Name` a `DueDate` . Provedeme `UpdateList()` a `CheckForErrors()` později.

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

4. Přidejte soukromý odkaz na uživatelský ovládací prvek. Přidejte konstruktor, který převezme uživatelský ovládací prvek a název této položky ToDo. Chcete-li zjistit hodnotu pro `daysAhead` , získá vlastnost stránky možnosti.

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

5. Vzhledem k tomu, že instance `TodoItem` třídy budou uloženy v seznamu a seznam bude volat `ToString` funkci, je nutné `ToString` funkci přetížit. Přidejte následující kód do *TodoItem.cs*, za konstruktor a před koncem třídy.

    ```csharp
    public override string ToString()
    {
        return name + " Due: " + dueDate.ToShortDateString();
    }
    ```

6. V *TodoWindowControl.XAML.cs* přidejte do třídy metody zástupných procedur `TodoWindowControl` pro `CheckForError` `UpdateList` metody a. Umístěte je po ProcessDialogChar a před koncem souboru.

    ```csharp
    public void CheckForErrors()
    {
    }
    public void UpdateList(TodoItem item)
    {
    }
    ```

     `CheckForError`Metoda zavolá metodu, která má stejný název v nadřazeném objektu, a tato metoda ověří, zda došlo k chybám, a správně je zpracuje. `UpdateList`Metoda aktualizuje seznam v nadřazeném ovládacím prvku; metoda je volána, když dojde ke `Name` `DueDate` změně vlastností a v této třídě. Budou implementovány později.

## <a name="integrate-into-the-properties-window"></a>Integrace do okno Vlastnosti
 Nyní napíšete kód, který spravuje seznam, který bude svázán s oknem **vlastností** .

 Musíte změnit obslužnou rutinu kliknutí na tlačítko, aby přečetla textové pole, vytvořila TodoItem a přidala ho do seznamu.

1. Nahraďte existující `button1_Click` funkci kódem, který vytvoří nový TodoItem a přidá ho do seznamu. Volá `TrackSelection()` , která bude definována později.

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

2. V zobrazení Návrh vyberte ovládací prvek ListBox. V okně **vlastnosti** klikněte na tlačítko **obslužné rutiny události** a vyhledejte událost **SelectionChanged** . Do textového pole zadejte **listBox_SelectionChanged**. Tím přidáte zástupnou proceduru pro obslužnou rutinu SelectionChanged a přiřadíte ji k události.

3. Implementujte `TrackSelection()` metodu. Vzhledem k tomu, že budete potřebovat získat <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> služby, je potřeba zpřístupnit <xref:Microsoft.VisualStudio.Shell.WindowPane.GetService%2A> TodoWindowControl. Do třídy `TodoWindow` přidejte následující metodu:

    ```
    internal object GetVsService(Type service)
    {
        return GetService(service);
    }
    ```

4. Do *TodoWindowControl.XAML.cs* přidejte následující direktivy using:

    ```csharp
    using System.Runtime.InteropServices;
    using Microsoft.VisualStudio.Shell.Interop;
    using Microsoft.VisualStudio;
    using Microsoft.VisualStudio.Shell;
    ```

5. Vyplňte obslužnou rutinu SelectionChanged následujícím způsobem:

    ```
    private void listBox_SelectionChanged(object sender, SelectionChangedEventArgs e)
    {
        TrackSelection();
    }
    ```

6. Nyní vyplňte funkci TrackSelection, která zajistí integraci s oknem **vlastností** . Tato funkce se volá, když uživatel přidá položku do seznamu nebo klikne na položku v seznamu. Přidá obsah seznamu do SelectionContainer a předá SelectionContainer  <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> obslužné rutině události okna vlastností. Služba TrackSelection sleduje vybrané objekty v uživatelském rozhraní (UI) a zobrazuje jejich vlastnosti.

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

     Teď, když máte třídu, kterou může použít okno **vlastnosti** , můžete integrovat okno **vlastnosti** s oknem nástrojů. Když uživatel klikne na položku v seznamu v okně nástroje, mělo by se odpovídajícím způsobem aktualizovat okno **vlastnosti** . Podobně platí, že když uživatel změní položku ToDo v okně **vlastnosti** , měla by se aktualizovat přidružená položka.

7. Nyní do *TodoWindowControl.XAML.cs* přidejte zbytek kódu funkce UpdateList. Mělo by se odstranit a znovu přidat upravený TodoItem ze seznamu.

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

9. Otevřete stránku   >  **Možnosti** nástrojů. V levém podokně by se měla zobrazit kategorie ToDo. Kategorie jsou uvedeny v abecedním pořadí, takže se podívejte do části TS.

10. Na stránce možnosti **TODO** by se měla zobrazit `DaysAhead` vlastnost nastavená na **hodnotu 0**. Změňte ji na **2**.

11. V nabídce **Zobrazit/další Windows** otevřete **TodoWindow**. Do textového pole zadejte **EndDate** a klikněte na **Přidat**.

12. V poli se seznamem by se mělo zobrazit datum po dvou dnech později než dnes.

## <a name="add-text-to-the-output-window-and-items-to-the-task-list"></a>Přidat text do okna výstup a položky do Seznam úkolů
 Pro **seznam úkolů** vytvoříte nový objekt typu Task a následně do **seznam úkolů** přidáte objekt úlohy voláním jeho `Add` metody. Chcete-li zapisovat do okna **výstup** , zavolejte jeho `GetPane` metodu pro získání objektu podokna a potom zavolejte `OutputString` metodu objektu podokna.

1. V *TodoWindowControl.XAML.cs* v `button1_Click` metodě přidejte kód pro získání **obecného** podokna okna **výstup** (což je výchozí nastavení) a zapište do něj. Metoda by měla vypadat takto:

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
