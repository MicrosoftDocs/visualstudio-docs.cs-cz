---
title: Rozšíření vlastností, seznamu úloh, výstup a možnosti Windows | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- properties pane
- task list
- output window
- properties window
- tutorials
- tool windows
ms.assetid: 06990510-5424-44b8-9fd9-6481acec5c76
caps.latest.revision: 38
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 327d218f22b4629ec919a20ef2800d445e2d652f
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51737824"
---
# <a name="extending-the-properties-task-list-output-and-options-windows"></a>Rozšíření vlastností, seznamu úkolů, oken Výstup a Možnosti
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Jakékoli okno nástroje v sadě Visual Studio můžete přistupovat. Tento návod ukazuje, jak integrovat informace o vaší panelu nástrojů do nového **možnosti** stránky a nové nastavení na **vlastnosti** stránky a také způsob zápisu do **seznamu úkolů** a **výstup** systému windows.  
  
## <a name="prerequisites"></a>Požadavky  
 Spouští se v sadě Visual Studio 2015, nenainstalujete sadu Visual Studio SDK ze služby Stažení softwaru. Je zahrnut jako volitelná funkce v instalačním programu sady Visual Studio. VS SDK můžete také nainstalovat později. Další informace najdete v tématu [instalace sady Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="create-an-extension-with-a-tool-window"></a>Vytváření rozšíření pomocí panelu nástrojů  
  
1.  Vytvoření projektu s názvem **TodoList** VSIX šablony a přidat šablonu vlastního nástroje okna položku s názvem **TodoWindow**.  
  
    > [!NOTE]
    >  Další informace o vytváření rozšíření pomocí panelu nástrojů najdete v tématu [vytváření rozšíření pomocí panelu nástrojů](../extensibility/creating-an-extension-with-a-tool-window.md).  
  
## <a name="set-up-the-tool-window"></a>Vytvořit panel nástrojů  
 Přidáte textové pole pro zadání nová položka ToDo, tlačítko Přidat novou položku do seznamu a seznam pro zobrazení položek v seznamu.  
  
1.  V TodoWindow.xaml odstraňte z uživatelský ovládací prvek tlačítko, textového pole a StackPanel – ovládací prvky.  
  
    > [!NOTE]
    >  Tím nedojde k odstranění **button1_Click** obslužnou rutinu události, která bude znovu použít v pozdějším kroku.  
  
2.  Z **všechny ovládací prvky WPF** část **nástrojů**, přetáhněte **plátna** ovládací prvek mřížky.  
  
3.  Přetáhněte **TextBox**, **tlačítko**a **ListBox** na plátno. Uspořádejte prvky tak, aby textového pole a tlačítko se na stejné úrovni, a objekt ListBox vyplní rest v okně níže, stejně jako v následujícím obrázku.  
  
     ![Dokončení panel nástrojů](../extensibility/media/t5-toolwindow.png "T5 – okno")  
  
4.  V podokně XAML najít tlačítko a nastavte jeho vlastnost obsahu **přidat**. Znovu připojte obslužné rutiny události tlačítka pro ovládací prvek tlačítka tak, že přidáte `Click="button1_Click"` atribut. Blok plátna by měl vypadat nějak takto:  
  
    ```xml  
    <Canvas HorizontalAlignment="Left" Width="306">  
        <TextBox x:Name="textBox" HorizontalAlignment="Left" Height="23" Margin="10,10,0,0" TextWrapping="Wrap" Text="TextBox" VerticalAlignment="Top" Width="208"/>  
            <Button x:Name="button" Content="Add" HorizontalAlignment="Left" Margin="236,13,0,0" VerticalAlignment="Top" Width="48" Click="button1_Click"/>  
            <ListBox x:Name="listBox" HorizontalAlignment="Left" Height="222" Margin="10,56,0,0" VerticalAlignment="Top" Width="274"/>  
    </Canvas>  
    ```  
  
#### <a name="customize-the-constructor"></a>Přizpůsobení konstruktoru  
  
1.  V souboru TodoWindowControl.xaml.cs, přidejte následující příkaz using:  
  
    ```csharp  
    using System;  
    ```  
  
2.  Přidejte veřejný odkaz na TodoWindow a mít konstruktor TodoWindowControl TodoWindow parametr. Kód by měl vypadat takto:  
  
    ```csharp  
    public TodoWindow parent;  
  
    public TodoWindowControl(TodoWindow window)  
    {  
        InitializeComponent();  
        parent = window;  
    }  
    ```  
  
3.  V TodoWindow.cs změňte TodoWindowControl konstruktor zahrnout parametr TodoWindow. Kód by měl vypadat takto:  
  
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
 Můžete zadat stránku **možnosti** dialogové okno tak, aby uživatelé mohou změnit nastavení pro panel nástrojů. Vytvoření stránky možnosti vyžaduje obě třídy, která popisuje možnosti a záznam v souboru TodoListPackage.cs nebo TodoListPackage.vb.  
  
1. Přidejte třídu pojmenovanou `ToolsOptions.cs`. Ujistěte se, ToolsOptions třída dědila z <xref:Microsoft.VisualStudio.Shell.DialogPage>.  
  
   ```csharp  
   class ToolsOptions : DialogPage  
   {  
   }  
   ```  
  
2. Přidejte následující příkaz using:  
  
   ```csharp  
   using Microsoft.VisualStudio.Shell;  
   ```  
  
3. Na stránce Možnosti v tomto názorném postupu obsahuje pouze jednu možnost s názvem DaysAhead. Přidat soukromé pole s názvem **daysAhead** a vlastnost s názvem **DaysAhead** ToolsOptions třídy:  
  
   ```csharp  
   private double daysAhead;  
  
   public double DaysAhead  
   {  
       get { return daysAhead; }  
       set { daysAhead = value; }  
   }  
   ```  
  
   Nyní je třeba projekt vědět, tato stránka možností.  
  
#### <a name="make-the-options-page-available-to-users"></a>Na stránce Možnosti zpřístupnit uživatelům  
  
1.  V TodoWindowPackage.cs, přidejte <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> TodoWindowPackage třídy:  
  
    ```csharp  
    [ProvideOptionPage(typeof(ToolsOptions), "ToDo", "General", 101, 106, true)]  
    ```  
  
2.  První parametr konstruktoru ProvideOptionPage je typ třídy ToolsOptions, který jste vytvořili dříve. Druhý parametr "ToDo", je název kategorie **možnosti** dialogové okno. Třetí parametr, název podkategorie "Obecné", je **možnosti** dialogovému oknu, kde bude k dispozici na stránce Možnosti. Následující dva parametry jsou ID prostředků pro řetězce; Název kategorie je první a druhý je název podkategorie. Poslední parametr určuje, zda tato stránka je přístupná pomocí automatizace.  
  
     Když uživatel otevře vaše stránka Možnosti, by měla vypadat podobně jako na následujícím obrázku.  
  
     ![Stránka Možnosti](../extensibility/media/t5optionspage.gif "T5OptionsPage")  
  
     Všimněte si kategorie **ToDo** a subcategory **Obecné**.  
  
## <a name="make-data-available-to-the-properties-window"></a>Zajištění dostupnosti dat v okně Vlastnosti  
 Informace o seznamu lze můžete zpřístupnit tak, že vytvoříte třídu s názvem TodoItem, která uchovává informace o jednotlivých položek v seznamu úkolů.  
  
1.  Přidejte třídu pojmenovanou `TodoItem.cs`.  
  
     Když je okno nástroje dostupné pro uživatele, položky v seznamu se bude reprezentovat pomocí TodoItems. Když uživatel vybere jeden z těchto položek v seznamu, **vlastnosti** okně se zobrazí informace o položce.  
  
     Chcete-li data zpřístupnit ve **vlastnosti** okně zapnout data do veřejné vlastnosti, které mají speciální dva atributy, `Description` a `Category`. `Description` je text, který se zobrazí v dolní části **vlastnosti** okna. `Category` Určuje, kde vlastnost by měla zobrazit **vlastnosti** okna se zobrazí v **Categorized** zobrazení. Na následujícím obrázku **vlastnosti** je okno v **Categorized** zobrazení, **název** vlastnost v **ToDo pole** kategorie je Vybraná a popis **název** vlastnost se zobrazí v dolní části okna.  
  
     ![Okno vlastností](../extensibility/media/t5properties.png "T5Properties")  
  
2.  Přidejte následující příkazy using TodoItem.cs souboru.  
  
    ```csharp  
    using System.ComponentModel;  
    using System.Windows.Forms;  
    using Microsoft.VisualStudio.Shell.Interop;  
    ```  
  
3.  Přidat `public` modifikátor přístupu k deklaraci třídy.  
  
    ```csharp  
    public class TodoItem  
    {  
    }  
    ```  
  
     Přidejte dvě vlastnosti, název a DueDate. Provedeme UpdateList() a CheckForErrors() později.  
  
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
  
4.  Přidejte privátní odkaz na uživatelský ovládací prvek. Přidejte konstruktor, který přebírá uživatelského ovládacího prvku a název pro tuto položku seznamu úkolů. Najít hodnotu pro daysAhead, získá vlastnost stránky možnosti.  
  
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
  
5.  Protože instance `TodoItem` třídy se uloží v seznamu a seznam bude volat `ToString` funkce, třeba přetížení `ToString` funkce. Přidejte následující kód k TodoItem.cs, po konstruktoru a před ukončením třídy.  
  
    ```csharp  
    public override string ToString()  
    {  
        return name + " Due: " + dueDate.ToShortDateString();  
    }  
    ```  
  
6.  V TodoWindowControl.xaml.cs, přidejte do třídy TodoWindowControl pro metody zástupných procedur `CheckForError` a `UpdateList` metody. Vytvořte z nich po ProcessDialogChar a do konce souboru.  
  
    ```csharp  
    public void CheckForErrors()  
    {  
    }  
    public void UpdateList(TodoItem item)  
    {  
    }  
    ```  
  
     `CheckForError` Metoda bude volat metodu, která má stejný název v nadřazeném objektu a tato metoda zkontroluje, jestli došlo k nějaké chyby a správně zpracovávat. `UpdateList` Metoda aktualizuje objekt ListBox nadřazeného ovládacího prvku; metoda je volána, když `Name` a `DueDate` vlastnosti v této změně třídy. Budou prováděny později.  
  
## <a name="integrate-into-the-properties-window"></a>Integrace do okna Vlastnosti  
 Teď zadejte kód, který spravuje objekt ListBox, které budou svázány s **vlastnosti** okna.  
  
 Je nutné změnit na tlačítko klikněte obslužná rutina se má číst textové pole, vytvoření úkolu a přidá ho do objektu ListBox.  
  
1.  Nahraďte existující `button1_Click` funkce s kódem, který vytvoří nové TodoItem a přidá ho do objektu ListBox. Volá TrackSelection(), která bude obsahovat definici později.  
  
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
  
2.  V návrhovém zobrazení vyberte ovládací prvek ListBox. V **vlastnosti** okno kliknutím **obslužné rutiny událostí** tlačítko a najděte SelectionChanged událost. Zadejte do textového pole **listBox_SelectionChanged**. To přidá zástupnou proceduru pro obslužnou rutinu SelectionChanged a přiřadí ji k události.  
  
3.  Implementujte metodu TrackSelection(). Protože je budete potřebovat získat <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> služby, třeba provedete <xref:Microsoft.VisualStudio.Shell.WindowPane.GetService%2A> přístupné TodoWindowControl. Přidejte následující metodu do třídy TodoWindow:  
  
    ```  
    internal object GetVsService(Type service)  
    {  
        return GetService(service);  
    }  
    ```  
  
4.  Přidejte následující příkazy using do TodoWindowControl.xaml.cs:  
  
    ```csharp  
    using System.Runtime.InteropServices;  
    using Microsoft.VisualStudio.Shell.Interop;  
    using Microsoft.VisualStudio;  
    using Microsoft.VisualStudio.Shell;  
    ```  
  
5.  Obslužná rutina SelectionChanged vyplňte následujícím způsobem:  
  
    ```  
    private void listBox_SelectionChanged(object sender, SelectionChangedEventArgs e)  
    {  
        TrackSelection();  
    }  
    ```  
  
6.  Nyní, vyplňte TrackSelection funkce, který bude zajišťovat integrace s **vlastnosti** okna. Tato funkce je volána, když uživatel přidá položku do seznamu nebo klepne na položku v seznamu. Přidá obsah objektu ListBox SelectionContainer a předává SelectionContainer k **vlastnosti** okna <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> obslužné rutiny události. Služba TrackSelection sleduje vybrané objekty v uživatelském rozhraní (UI) a zobrazí jejich vlastnosti  
  
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
  
     Teď, když máte třídu, která **vlastnosti** okna můžete použít, můžete integrovat **vlastnosti** okna panel nástrojů. Když uživatel klikne na položku v seznamu v panelu nástrojů **vlastnosti** okno by měla být podle nich aktualizuje. Podobně, když uživatel změní položku seznamu úkolů v **vlastnosti** okna, je třeba aktualizovat související položku.  
  
7.  Teď přidejte zbytek kódu funkce UpdateList v TodoWindowControl.xaml.cs. Měli byste ho vyřadit a znovu přidejte upravené TodoItem ze seznamu.  
  
    ```csharp  
    public void UpdateList(TodoItem item)  
    {  
        var index = listBox.SelectedIndex;  
        listBox.Items.RemoveAt(index);  
        listBox.Items.Insert(index, item);  
        listBox.SelectedItem = index;  
    }  
    ```  
  
8.  Otestujte svůj kód. Sestavte projekt a spusťte ladění. Experimentální instanci aplikace by se zobrazit.  
  
9. Otevřít **Nástroje / možnosti** stránky. Měli byste vidět kategorii ToDo v levém podokně. Kategorie jsou uvedeny v abecedním, takže podívejte se do části Ts.  
  
10. Na stránce Možnosti seznamu úkolů, měli vidět DaysAhead nastavenou na **0**. Změňte ho na **2**.  
  
11. V zobrazení / ostatní Windows nabídce otevřete **TodoWindow**. Typ **EndDate** na textové pole a klikněte na **přidat**.  
  
12. V seznamu byste měli vidět dva dny pozdější než dnešní datum.  
  
## <a name="add-text-to-the-output-window-and-items-to-the-task-list"></a>Přidejte Text do okna výstup a položky do seznamu úkolů  
 Pro **seznamu úkolů**, vytvořit nový objekt typu úlohy a pak přidejte tento objekt úlohy **seznamu úkolů** po zavolání jeho metody Add. Zapsat do **výstup** okně volání metody getpane – pro získání objektu podokně a poté zavolejte metodu OutputString podokně objektu.  
  
1.  V TodoWindowControl.xaml.cs v `button1_Click` metodu, přidejte kód pro získání **Obecné** podokně **výstup** okno (což je výchozí hodnota) a do ní zapisovat. Metoda by měla vypadat nějak takto:  
  
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
  
2.  Chcete-li přidat položky do seznamu úkolů, musíte třídy TodoWindowControl přidat vnořené třídy. Vnořené třídy musí být odvozen od <xref:Microsoft.VisualStudio.Shell.TaskProvider>. Přidejte následující kód na konec TodoWindowControl třídy.  
  
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
  
3.  Dále přidejte privátní odkaz na TodoTaskProvider a metodu CreateProvider() TodoWindowControl třídy. Kód by měl vypadat takto:  
  
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
  
4.  Přidejte do třídy TodoWindowControl ClearError(), který zruší seznam úkolů, a ReportError(), které přidá položku do seznamu úkolů.  
  
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
  
5.  Teď implementujte metodu CheckForErrors následujícím způsobem.  
  
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
  
## <a name="trying-it-out"></a>Vyzkoušejte si  
  
1.  Sestavte projekt a spusťte ladění. Zobrazí se experimentální instance.  
  
2.  Otevřete TodoWindow (**zobrazení nebo jiných Windows / TodoWindow**).  
  
3.  Zadejte text do textového pole a potom klikněte na tlačítko **přidat**.  
  
     Termín splnění 2 dní od dnešního dne je přidán do seznamu. Nebudou vygenerovány žádné chyby a **seznamu úkolů** (**zobrazení / úloh seznamu**) by měly obsahovat žádné položky.  
  
4.  Teď změňte nastavení na **nástroje / Možnosti / ToDo** stránku ze **2** zpět **0**.  
  
5.  Zadejte jiný v **TodoWindow** a potom klikněte na tlačítko **přidat** znovu. Tím se spustí chybu a také položku v **seznamu úkolů**.  
  
     S přidáváním položek, počáteční datum je nastaveno na nyní plus 2 dny.  
  
6.  Na **zobrazení** nabídky, klikněte na tlačítko **výstup** otevřít **výstup** okna.  
  
     Všimněte si, že pokaždé, když se, že přidáte položku, zobrazí se zpráva v **seznamu úkolů** podokně.  
  
7.  Klikněte na jednu z položek v seznamu.  
  
     **Vlastnosti** okně se zobrazí dvě vlastnosti položky.  
  
8.  Změňte jednu z vlastností a stiskněte klávesu ENTER.  
  
     Při aktualizaci položky v seznamu.

