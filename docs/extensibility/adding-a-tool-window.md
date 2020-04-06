---
title: Přidání okna nástroje | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- tutorials
- tool windows
ms.assetid: 8e16c381-03c8-404e-92ef-3614cdf3150a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 573f01043d8b1b0c2293a3ebf6e0c246a8727d6a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740265"
---
# <a name="add-a-tool-window"></a>Přidání okna nástroje

V tomto návodu se dozvíte, jak vytvořit okno nástroje a integrovat ho do sady Visual Studio následujícími způsoby:

- Přidejte ovládací prvek do okna nástroje.

- Přidejte panel nástrojů do okna nástroje.

- Přidejte příkaz na panel nástrojů.

- Implementujte příkazy.

- Nastavte výchozí polohu okna nástroje.

## <a name="prerequisites"></a>Požadavky

Sada Visual Studio SDK je součástí volitelné funkce v nastavení sady Visual Studio. Další informace naleznete [v tématu Instalace sady Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-tool-window"></a>Vytvoření okna nástroje

1. Vytvořte projekt s názvem **FirstToolWin** pomocí šablony VSIX a přidejte vlastní šablonu položky okna nástroje s názvem **FirstToolWindow**.

    > [!NOTE]
    > Další informace o vytvoření rozšíření pomocí okna nástroje naleznete v [tématu Vytvoření rozšíření s oknem nástroje](../extensibility/creating-an-extension-with-a-tool-window.md).

## <a name="add-a-control-to-the-tool-window"></a>Přidání ovládacího prvku do okna nástroje

1. Odeberte výchozí ovládací prvek. Otevřete *soubor FirstToolWindowControl.xaml* a odstraňte **tlačítko Klikněte na mě!** .

2. V **panelu nástrojů**rozbalte oddíl **Všechny ovládací prvky WPF** a přetáhněte ovládací prvek **média** do formuláře **FirstToolWindowControl.** Vyberte ovládací prvek a v okně **Vlastnosti** pojmenujte tento prvek **mediaElement1**.

## <a name="add-a-toolbar-to-the-tool-window"></a>Přidání panelu nástrojů do okna nástroje
Přidáním panelu nástrojů následujícím způsobem zaručujete, že jeho přechody a barvy jsou konzistentní se zbytkem ide.

1. V **Průzkumníku řešení**otevřete *soubor FirstToolWindowPackage.vsct*. Soubor *.vsct* definuje prvky grafického uživatelského rozhraní (GUI) v okně nástroje pomocí jazyka XML.

2. V `<Symbols>` části vyhledejte `<GuidSymbol>` uzel, `name` jehož atribut je `guidFirstToolWindowPackageCmdSet`. Přidejte následující `<IDSymbol>` dva prvky `<IDSymbol>` do seznamu prvků v tomto uzlu a definujte panel nástrojů a skupinu panelů nástrojů.

    ```xml
    <IDSymbol name="ToolbarID" value="0x1000" />
    <IDSymbol name="ToolbarGroupID" value="0x1001" />
    ```

3. Těsně nad `<Buttons>` oddílem `<Menus>` vytvořte oddíl, který se podobá tomuto:

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

    Existuje několik různých druhů menu. Tato nabídka je panel nástrojů v okně `type` nástroje definovaný jeho atributem. Nastavení `guid` `id` a tvoří plně kvalifikované ID panelu nástrojů. Nabídka je `<Parent>` obvykle obsahující skupina. Panel nástrojů je však definován jako jeho vlastní nadřazený. Proto stejný identifikátor se používá `<Menu>` `<Parent>` pro a prvky. Atribut `priority` je pouze '0'.

4. Panely nástrojů se mnoha způsoby podobají nabídkám. Například stejně jako nabídka může mít skupiny příkazů, panely nástrojů mohou mít také skupiny. (V nabídkách jsou skupiny příkazů odděleny vodorovnými čarami. Na panelech nástrojů nejsou skupiny odděleny oddělovači vizuálů.)

    Přidejte `<Groups>` oddíl, `<Group>` který obsahuje prvek. Definuje skupinu, jejíž ID `<Symbols>` jste deklarovali v části. Přidejte `<Groups>` oddíl hned `<Menus>` za oddíl.

    ```xml
    <Groups>
        <Group guid="guidFirstToolWindowPackageCmdSet" id="ToolbarGroupID" priority="0x0000">
            <Parent guid="guidFirstToolWindowPackageCmdSet" id="ToolbarID" />
        </Group>
    </Groups>
    ```

    Nastavením nadřazeného identifikátoru GUID a ID na identifikátor GUID a ID panelu nástrojů přidáte skupinu na panel nástrojů.

## <a name="add-a-command-to-the-toolbar"></a>Přidání příkazu na panel nástrojů

Přidejte příkaz na panel nástrojů, který se zobrazí jako tlačítko.

1. V `<Symbols>` části deklarujte následující prvky IDSymbol hned za deklarací panelu nástrojů a skupiny panelu nástrojů.

    ```xml
    <IDSymbol name="cmdidWindowsMedia" value="0x0100" />
    <IDSymbol name="cmdidWindowsMediaOpen" value="0x132" />
    ```

2. Přidejte prvek Button `<Buttons>` uvnitř oddílu. Tento prvek se zobrazí na panelu nástrojů v okně nástroje s ikonou **Hledat** (lupa).

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

3. Otevřete *FirstToolWindowCommand.cs* a přidejte následující řádky do třídy hned za existující pole.

    ```csharp
    public const string guidFirstToolWindowPackageCmdSet = "00000000-0000-0000-0000-0000";  // get the GUID from the .vsct file
    public const uint cmdidWindowsMedia = 0x100;
    public const int cmdidWindowsMediaOpen = 0x132;
    public const int ToolbarID = 0x1000;
    ```

    Tím zpřístupníte příkazy v kódu.

## <a name="add-a-mediaplayer-property-to-firsttoolwindowcontrol"></a>Přidání vlastnosti MediaPlayer do nástroje FirstToolWindowControl
Z obslužné rutiny událostí pro ovládací prvky panelu nástrojů musí být váš kód schopen získat přístup k ovládacímu prvku Media Player, který je podřízeným prvkem třídy FirstToolWindowControl.

V **Průzkumníku řešení**klepněte pravým tlačítkem myši na *položku FirstToolWindowControl.xaml*, klepněte na příkaz **Zobrazit kód**a přidejte následující kód do třídy FirstToolWindowControl.

```csharp
public System.Windows.Controls.MediaElement MediaPlayer
{
    get { return mediaElement1; }
}
```

## <a name="instantiate-the-tool-window-and-toolbar"></a>Vytvoření instance okna nástroje a panelu nástrojů
Přidejte panel nástrojů a příkaz nabídky, který vyvolá dialogové okno **Otevřít soubor** a přehraje vybraný mediální soubor.

1. Otevřete *FirstToolWindow.cs* a `using` přidejte následující direktivy:

    ```csharp
    using System.ComponentModel.Design;
    using System.Windows.Forms;
    using Microsoft.VisualStudio.Shell.Interop;
    ```

2. Uvnitř FirstToolWindow třídy přidejte veřejný odkaz na FirstToolWindowControl ovládacího prvku.

    ```csharp
    public FirstToolWindowControl control;
    ```

3. Na konci konstruktoru nastavte tuto proměnnou ovládacího prvku na nově vytvořený ovládací prvek.

    ```csharp
    control = new FirstToolWindowControl();
    base.Content = control;
    ```

4. Vytvořte suverénní stav uvnitř konstruktoru.

    ```csharp
    this.ToolBar = new CommandID(new Guid(FirstToolWindowCommand.guidFirstToolWindowPackageCmdSet),
        FirstToolWindowCommand.ToolbarID);
    this.ToolBarLocation = (int)VSTWT_LOCATION.VSTWT_TOP;
    ```

5. V tomto okamžiku FirstToolWindow konstruktor by měl vypadat takto:

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

6. Přidejte příkaz nabídky na panel nástrojů. Ve třídě FirstToolWindowCommand.cs přidejte následující příkaz pomocí směrnice:

    ```csharp
    using System.Windows.Forms;
    ```

7. Ve třídě FirstToolWindowCommand přidejte následující kód na konci metody ShowToolWindow(). Příkaz ButtonHandler bude implementován v další části.

    ```csharp
    // Create the handles for the toolbar command.
    var mcs = this.ServiceProvider.GetService(typeof(IMenuCommandService)) as OleMenuCommandService;
    var toolbarbtnCmdID = new CommandID(new Guid(FirstToolWindowCommand.guidFirstToolWindowPackageCmdSet),
        FirstToolWindowCommand.cmdidWindowsMediaOpen);
    var menuItem = new MenuCommand(new EventHandler(
        ButtonHandler), toolbarbtnCmdID);
    mcs.AddCommand(menuItem);
    ```

### <a name="to-implement-a-menu-command-in-the-tool-window"></a>Implementace příkazu nabídky v okně nástroje

1. Ve třídě FirstToolWindowCommand přidejte metodu ButtonHandler, která vyvolá dialogové okno **Otevřít soubor.** Pokud byl soubor vybrán, přehraje mediální soubor.

2. Ve třídě FirstToolWindowCommand přidejte soukromý odkaz na okno FirstToolWindow, které se vytvoří v metodě FindToolWindow().

    ```csharp
    private FirstToolWindow window;
    ```

3. Změňte metodu ShowToolWindow() a nastavte okno, které jste definovali výše (tak, aby obslužná rutina příkazu ButtonHandler měla přístup k ovládacímu prvku okna. Zde je kompletní ShowToolWindow() metoda.

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

4. Přidejte metodu ButtonHandler. Vytvoří OpenFileDialog pro uživatele určit mediální soubor přehrát a pak přehraje vybraný soubor.

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

## <a name="set-the-default-position-for-the-tool-window"></a>Nastavení výchozí polohy okna nástroje

Dále zadejte výchozí umístění v ide pro okno nástroje. Informace o konfiguraci okna nástroje jsou v *souboru FirstToolWindowPackage.cs.*

1. V *FirstToolWindowPackage.cs*najděte <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute> atribut `FirstToolWindowPackage` na třídu, která předá FirstToolWindow typ konstruktoru. Chcete-li zadat výchozí pozici, musíte přidat další parametry konstruktoru následující příklad.

    ```csharp
    [ProvideToolWindow(typeof(FirstToolWindow),
        Style = Microsoft.VisualStudio.Shell.VsDockStyle.Tabbed,
        Window = "3ae79031-e1bc-11d0-8f78-00a0c9110057")]
    ```

    První pojmenovaný parametr `Style` je a `Tabbed`jeho hodnota je , což znamená, že okno bude karta v existujícím okně. Dokovací pozice je `Window` určena parametrem n v tomto případě identifikátorem GUID **Průzkumníka řešení**.

    > [!NOTE]
    > Další informace o typech oken v prostředí <xref:EnvDTE.vsWindowType>IDE naleznete v tématu .

## <a name="test-the-tool-window"></a>Testování okna nástroje

1. Stisknutím **klávesy F5** otevřete novou instanci experimentálního sestavení sady Visual Studio.

2. V nabídce **View** přejděte na **položku Jiný systém Windows** a klepněte na příkaz První okno **nástroje**.

    Okno nástroje přehrávače médií by se mělo otevřít ve stejné poloze jako **Průzkumník řešení**. Pokud se stále zobrazuje ve stejné poloze jako dříve, resetujte rozložení okna (**Okno / Obnovit rozložení okna**).

3. Klepněte na tlačítko (má ikonu **Hledat)** v okně nástroje. Vyberte podporovaný zvukový soubor nebo soubor videa, například *C:\windows\media\chimes.wav*, a stiskněte **klávesu Otevřít**.

    Měl bys slyšet zvuk zvonění.

## <a name="see-also"></a>Viz také
- [Příkazy, nabídky a panely nástrojů](../extensibility/internals/commands-menus-and-toolbars.md)
