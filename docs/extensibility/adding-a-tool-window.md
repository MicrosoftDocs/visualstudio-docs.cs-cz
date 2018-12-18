---
title: Přidání panelu nástrojů | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- tutorials
- tool windows
ms.assetid: 8e16c381-03c8-404e-92ef-3614cdf3150a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 550e483ec2a8cd4b4126e4c0838dc8d2870af59c
ms.sourcegitcommit: 0e5289414d90a314ca0d560c0c3fe9c88cb2217c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/19/2018
ms.locfileid: "39151928"
---
# <a name="add-a-tool-window"></a>Přidání panelu nástrojů
V tomto podrobném návodu se dozvíte, jak vytvořit okno nástroje a integrovat do sady Visual Studio následujícími způsoby:  
  
-   Přidání ovládacího prvku pro panel nástrojů.  
  
-   Přidání panelu nástrojů do panelu nástrojů.  
  
-   Přidání příkazu do panelu nástrojů.  
  
-   Implementace příkazu.  
  
-   Nastavte výchozí umístění pro panel nástrojů.  
  
## <a name="prerequisites"></a>Požadavky  
 Spouští se v sadě Visual Studio 2015, nenainstalujete sadu Visual Studio SDK ze služby Stažení softwaru. Je zahrnut jako volitelná funkce v instalačním programu sady Visual Studio. VS SDK můžete také nainstalovat později. Další informace najdete v tématu [instalace sady Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="create-a-tool-window"></a>Vytvoření panelu nástrojů  
  
1.  Vytvoření projektu s názvem **FirstToolWin** VSIX šablony a přidat šablonu vlastního nástroje okna položku s názvem **FirstToolWindow**.  
  
    > [!NOTE]
    >  Další informace o vytváření rozšíření pomocí panelu nástrojů najdete v tématu [vytváření rozšíření pomocí panelu nástrojů](../extensibility/creating-an-extension-with-a-tool-window.md).  
  
## <a name="add-a-control-to-the-tool-window"></a>Přidání ovládacího prvku panel nástrojů  
  
1.  Odeberte výchozí ovládací prvek. Otevřít *FirstToolWindowControl.xaml* a odstranit **klikněte na mě!** tlačítko.  
  
2.  V **nástrojů**, rozbalte **všechny ovládací prvky WPF** části a přetáhněte ji **mediálního prvku** ovládací prvek **FirstToolWindowControl** formuláře. Vyberte ovládací prvek a **vlastnosti** okna, název tohoto elementu **mediaElement1**.  
  
## <a name="add-a-toolbar-to-the-tool-window"></a>Přidání panelu nástrojů okno nástrojů  
 Přidáním panel nástrojů následujícím způsobem zaručit, že jsou konzistentní se zbytkem prostředí IDE jeho přechody a barvy.  
  
1.  V **Průzkumníka řešení**, otevřete *FirstToolWindowPackage.vsct*. *.Vsct* soubor definuje prvky grafického uživatelského rozhraní (GUI) v okně nástroje s využitím XML.  
  
2.  V `<Symbols>` části, vyhledejte `<GuidSymbol>` uzel jehož `name` atribut je `guidFirstToolWindowPackageCmdSet`. Přidejte následující dva `<IDSymbol>` prvků do seznamu `<IDSymbol>` prvky v tomto uzlu k definování panelu nástrojů a panelu nástrojů skupiny.  
  
    ```xml  
    <IDSymbol name="ToolbarID" value="0x1000" />  
    <IDSymbol name="ToolbarGroupID" value="0x1001" />  
    ```  
  
3.  Přímo nad `<Buttons>` části, vytvořte `<Menus>` oddíl, který vypadá takto:  
  
    ```xml  
    <Menus>  
        <Menu guid="guidFirstToolWindowPackageCmdSet" id="ToolbarID" priority="0x0000" type="ToolWindowToolbar">  
            <Parent guid="guidFirstToolWindowPackageCmdSet" id="ToolbarID" />  
            <Strings>  
                <ButtonText>Tool Window Toolbar</ButtonText>  
                <CommandName>Tool Window Toolbar</CommandName>  
            </Strings>  
        </Menu>  
    </Menus>  
    ```  
  
     Existují různé druhy nabídky. Tato nabídka je panel nástrojů v okně nástroje určené jeho `type` atribut. `guid` a `id` nastavení tvoří plně kvalifikované ID panelu nástrojů. Obvykle `<Parent>` nabídky je skupině obsahující. Panel nástrojů je však definován jako svůj vlastní nadřazený. Proto se používá stejný identifikátor pro `<Menu>` a `<Parent>` elementy. `priority` Atribut je právě "0".  
  
4.  Panely nástrojů se podobají nabídky mnoha způsoby. Například stejně jako nabídka může mít skupiny příkazů, panely nástrojů mohou také můžete mít skupiny. (V nabídkách, příkaz skupiny jsou odděleny vodorovné čáry. Na panely nástrojů skupiny nejsou odděleny visual oddělovače.)  
  
     Přidat `<Groups>` oddíl, který obsahuje `<Group>` elementu. To definuje skupinu, do jehož Identifikátor deklarovaný v `<Symbols>` oddílu. Přidat `<Groups>` části hned za `<Menus>` oddílu.  
  
    ```xml  
    <Groups>  
       <Group guid="guidFirstToolWindowPackageCmdSet" id="ToolbarGroupID" priority="0x0000">  
           <Parent guid="guidFirstToolWindowPackageCmdSet" id="ToolbarID" />  
       </Group>  
    </Groups>  
    ```  
  
     Nastavením nadřazený identifikátor GUID a ID identifikátoru GUID a ID panelu nástrojů, přidejte skupinu do panelu nástrojů.  
  
## <a name="add-a-command-to-the-toolbar"></a>Přidání příkazu do panelu nástrojů  
 Přidání příkazu do panelu nástrojů, který je zobrazen jako tlačítko.  
  
1.  V `<Symbols>` části, deklarujte následující prvky idsymbol – stačí po panelu nástrojů a nástrojů deklarace skupiny.  
  
    ```xml  
    <IDSymbol name="cmdidWindowsMedia" value="0x0100" />  
    <IDSymbol name="cmdidWindowsMediaOpen" value="0x132" />  
    ```  
  
2.  Přidejte tlačítko prvek uvnitř `<Buttons>` oddílu. Tento prvek se zobrazí na panelu nástrojů v okně nástroje s **hledání** ikonu (s ikonou lupy).  
  
    ```xml  
    <Button guid="guidFirstToolWindowPackageCmdSet" id="cmdidWindowsMediaOpen" priority="0x0101" type="Button">  
        <Parent guid="guidFirstToolWindowPackageCmdSet" id="ToolbarGroupID"/>  
        <Icon guid="guidImages" id="bmpPicSearch" />  
        <Strings>  
            <CommandName>cmdidWindowsMediaOpen</CommandName>  
            <ButtonText>Load File</ButtonText>  
        </Strings>  
    </Button>  
    ```  
  
3.  Otevřít *FirstToolWindowCommand.cs* a přidejte následující řádky ve třídě bezprostředně po existujících polí.  
  
    ```csharp  
    public const string guidFirstToolWindowPackageCmdSet = "00000000-0000-0000-0000-0000";  // get the GUID from the .vsct file  
    public const uint cmdidWindowsMedia =        0x100;   
    public const int cmdidWindowsMediaOpen = 0x132;  
    public const int ToolbarID = 0x1000;  
    ```  
  
     To zpřístupňuje příkazům v kódu.  
  
## <a name="add-a-mediaplayer-property-to-firsttoolwindowcontrol"></a>Přidání vlastnosti MediaPlayer FirstToolWindowControl  
 Z obslužné rutiny událostí pro ovládací prvky panelu nástrojů musí být váš kód přístup k ovládací prvek Media Player, který je podřízeným prvkem FirstToolWindowControl třídy.  
  
 V **Průzkumníka řešení**, klikněte pravým tlačítkem na *FirstToolWindowControl.xaml*, klikněte na tlačítko **zobrazit kód**a přidejte následující kód do třídy FirstToolWindowControl.  
  
```csharp  
public System.Windows.Controls.MediaElement MediaPlayer  
{  
    get { return mediaElement1; }  
}  
```  
  
## <a name="instantiate-the-tool-window-and-toolbar"></a>Vytvoření instance panelu nástrojů a panelu nástrojů  
 Přidání panelu nástrojů a příkaz nabídky, která volá **otevřít soubor** dialogové okno a přehraje mediální soubor.  
  
1.  Otevřít *FirstToolWindow.cs* a přidejte následující `using` příkazy.  
  
    ```csharp  
    using System.ComponentModel.Design;  
    using System.Windows.Forms;  
    using Microsoft.VisualStudio.Shell.Interop;   
    ```  
  
2.  Uvnitř třídy FirstToolWindow přidejte veřejný odkaz na ovládací prvek FirstToolWindowControl.  
  
    ```csharp  
    public FirstToolWindowControl control;  
    ```  
  
3.  Na konci konstruktoru nastavte tuto proměnnou ovládacího prvku na nově vytvořený ovládací prvek.  
  
    ```csharp  
    control = new FirstToolWindowControl();   
    base.Content = control;  
    ```  
  
4.  Vytvoření panelu nástrojů uvnitř konstruktoru instance.  
  
    ```csharp  
    this.ToolBar = new CommandID(new Guid(FirstToolWindowCommand.guidFirstToolWindowPackageCmdSet),   
        FirstToolWindowCommand.ToolbarID);  
    this.ToolBarLocation = (int)VSTWT_LOCATION.VSTWT_TOP;  
    ```  
  
5.  V tomto okamžiku FirstToolWindow konstruktor by měl vypadat takto:  
  
    ```csharp  
    public FirstToolWindow() : base(null)  
    {  
        this.Caption = "FirstToolWindow";  
        this.BitmapResourceID = 301;  
        this.BitmapIndex = 1;  
        control = new FirstToolWindowControl();  
        base.Content = control;  
        this.ToolBar = new CommandID(new Guid(FirstToolWindowCommand.guidFirstToolWindowPackageCmdSet),   
            FirstToolWindowCommand.ToolbarID);  
            this.ToolBarLocation = (int)VSTWT_LOCATION.VSTWT_TOP;  
    }  
    ```  
  
6.  Přidání příkazu nabídky do panelu nástrojů. Ve třídě FirstToolWindowCommand.cs přidejte následující příkaz using  
  
    ```csharp  
    using System.Windows.Forms;  
    ```  
  
7.  Ve třídě FirstToolWindowCommand přidejte následující kód na konci metody ShowToolWindow(). Příkaz ButtonHandler budou implementovány v další části.  
  
    ```csharp  
    // Create the handles for the toolbar command.   
    var mcs = this.ServiceProvider.GetService(typeof(IMenuCommandService)) as OleMenuCommandService;  
    var toolbarbtnCmdID = new CommandID(new Guid(FirstToolWindowCommand.guidFirstToolWindowPackageCmdSet),  
        FirstToolWindowCommand.cmdidWindowsMediaOpen);  
    var menuItem = new MenuCommand(new EventHandler(  
        ButtonHandler), toolbarbtnCmdID);  
    mcs.AddCommand(menuItem);  
    ```  
  
### <a name="to-implement-a-menu-command-in-the-tool-window"></a>Implementace příkazu nabídky v panelu nástrojů  
  
1.  Ve třídě FirstToolWindowCommand přidejte ButtonHandler metodu, která volá **otevřít soubor** dialogového okna. Pokud byl vybrán soubor, hraje mediální soubor.  
  
2.  Ve třídě FirstToolWindowCommand přidejte privátní odkaz do okna FirstToolWindow, která se vytvoří v metodě FindToolWindow().  
  
    ```csharp  
    private FirstToolWindow window;  
    ```  
  
3.  Změnit metodu ShowToolWindow() nastavujete časové období, které jste definovali výše (tak, aby obslužná rutina příkazu ButtonHandler můžete přístup k ovládacímu prvku okna. Tady je úplná metoda ShowToolWindow().  
  
    ```csharp  
    private void ShowToolWindow(object sender, EventArgs e)  
    {  
        window = (FirstToolWindow) this.package.FindToolWindow(typeof(FirstToolWindow), 0, true);  
        if ((null == window) || (null == window.Frame))  
        {  
                            throw new NotSupportedException("Cannot create tool window");  
        }  
  
        IVsWindowFrame windowFrame = (IVsWindowFrame)window.Frame;  
                Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure(windowFrame.Show());  
  
         var mcs = this.ServiceProvider.GetService(typeof(IMenuCommandService)) as OleMenuCommandService;  
        var toolbarbtnCmdID = new CommandID(new Guid(FirstToolWindowCommandguidFirstToolWindowPackageCmdSet),  
            FirstToolWindowCommand.cmdidWindowsMediaOpen);  
        var menuItem = new MenuCommand(new EventHandler(  
            ButtonHandler), toolbarbtnCmdID);  
        mcs.AddCommand(menuItem);  
    }  
    ```  
  
4.  Přidejte metodu ButtonHandler. Vytvoří OpenFileDialog pro uživatele, aby zadal do souboru média přehrajete, a potom hraje vybraný soubor.  
  
    ```csharp  
    private void ButtonHandler(object sender, EventArgs arguments)  
    {  
        OpenFileDialog openFileDialog = new OpenFileDialog();  
        DialogResult result = openFileDialog.ShowDialog();  
        if (result == DialogResult.OK)  
        {  
            window.control.MediaPlayer.Source = new System.Uri(openFileDialog.FileName);  
        }  
    }  
    ```  
  
## <a name="set-the-default-position-for-the-tool-window"></a>Nastavte výchozí umístění pro panel nástrojů  
 Dále určete výchozí umístění v integrovaném vývojovém prostředí pro panel nástrojů. Informace o konfiguraci pro panel nástrojů se *FirstToolWindowPackage.cs* souboru.  
  
1.  V *FirstToolWindowPackage.cs*, vyhledejte <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute> atribut na `FirstToolWindowPackage` třídu, která předá FirstToolWindow typ konstruktoru. Chcete-li určit výchozí pozici, je nutné přidat další parametry konstruktoru následující ukázka.  
  
    ```csharp  
    [ProvideToolWindow(typeof(FirstToolWindow),  
        Style = Microsoft.VisualStudio.Shell.VsDockStyle.Tabbed,  
        Window = "3ae79031-e1bc-11d0-8f78-00a0c9110057")]  
    ```  
  
     První parametr s názvem `Style` a jeho hodnota může být `Tabbed`, což znamená, že v okně budou karty ve stávajícím okně. Je určené pozici ukotvení `Window` parametr, n takovém případě identifikátor GUID **Průzkumníka řešení**.  
  
    > [!NOTE]
    >  Další informace o typech oken v integrovaném vývojovém prostředí najdete v tématu <xref:EnvDTE.vsWindowType>.  
  
## <a name="test-the-tool-window"></a>Testovací okno nástroje  
  
1.  Stisknutím klávesy **F5** otevřít novou instanci třídy experimentální sestavení sady Visual Studio.  
  
2.  Na **zobrazení** nabídky, přejděte k **ostatní Windows** a potom klikněte na tlačítko **první okno nástroje**.  
  
     Panel nástrojů media player měla otevřít na stejné pozici jako **Průzkumníka řešení**. Pokud se stále zobrazí na stejné pozici jako předtím, resetovat rozložení okna (**okno / resetovat rozložení okna**).  
  
3.  Klikněte na tlačítko (má **hledání** ikonu) v panelu nástrojů. Vyberte podporovanou zvuk nebo video soubor, například *C:\windows\media\chimes.wav*, stiskněte klávesu **otevřít**.  
  
     Měli byste slyšet zvuk gongu.  
  
## <a name="see-also"></a>Viz také:  
 [Příkazy, nabídky a panely nástrojů](../extensibility/internals/commands-menus-and-toolbars.md)