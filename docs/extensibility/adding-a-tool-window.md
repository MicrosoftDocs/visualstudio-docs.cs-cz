---
title: Přidání okna nástroje | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- tutorials
- tool windows
ms.assetid: 8e16c381-03c8-404e-92ef-3614cdf3150a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 169f386128ccdd79aef6b90a6703f50323b9b6f3
ms.sourcegitcommit: 05487d286ed891a04196aacd965870e2ceaadb68
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/02/2020
ms.locfileid: "85904136"
---
# <a name="add-a-tool-window"></a>Přidat okno nástrojů

V tomto návodu se naučíte, jak vytvořit okno nástroje a jak ho integrovat do sady Visual Studio, a to následujícími způsoby:

- Přidejte ovládací prvek do okna nástroje.

- Umožňuje přidat panel nástrojů do okna nástroje.

- Přidejte příkaz na panel nástrojů.

- Implementujte příkazy.

- Nastavte výchozí umístění panelu nástrojů.

## <a name="prerequisites"></a>Požadavky

Sada Visual Studio SDK je součástí instalačního programu sady Visual Studio jako volitelná funkce. Další informace najdete v tématu [instalace sady Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-tool-window"></a>Vytvořit okno nástroje

1. Vytvořte projekt s názvem **FirstToolWin** pomocí šablony VSIX a přidejte šablonu položky vlastního okna nástroje s názvem **FirstToolWindow**.

    > [!NOTE]
    > Další informace o vytváření rozšíření pomocí okna nástroje naleznete v tématu [Vytvoření rozšíření pomocí okna nástroje](../extensibility/creating-an-extension-with-a-tool-window.md).

## <a name="add-a-control-to-the-tool-window"></a>Přidání ovládacího prvku do okna nástroje

1. Odeberte výchozí ovládací prvek. Otevřete *FirstToolWindowControl. XAML* a odstraňte ho **kliknutím.** .

2. V sadě **nástrojů**rozbalte část **všechny ovládací prvky WPF** a přetáhněte ovládací prvek **mediální prvek** do formuláře **FirstToolWindowControl** . Vyberte ovládací prvek a v okně **vlastnosti** pojmenujte tento element **mediaElement1**.

## <a name="add-a-toolbar-to-the-tool-window"></a>Přidání panelu nástrojů do okna nástroje
Přidáním panelu nástrojů tímto způsobem zaručujete, že jeho přechody a barvy jsou konzistentní se zbytkem rozhraní IDE.

1. V **Průzkumník řešení**otevřete *FirstToolWindowPackage. vsct*. Soubor *. vsct* definuje prvky grafického uživatelského rozhraní (GUI) v okně nástroje pomocí XML.

2. V `<Symbols>` části vyhledejte `<GuidSymbol>` uzel, jehož `name` atribut je `guidFirstToolWindowPackageCmdSet` . Přidejte následující dva `<IDSymbol>` prvky do seznamu `<IDSymbol>` prvků v tomto uzlu pro definování panelu nástrojů a skupiny panelů nástrojů.

    ```xml
    <IDSymbol name="ToolbarID" value="0x1000" />
    <IDSymbol name="ToolbarGroupID" value="0x1001" />
    ```

3. Hned za `<Buttons>` část vytvořte `<Menus>` oddíl, který se podobá této:

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

    Existuje několik různých druhů nabídek. Tato nabídka je panel nástrojů v okně nástroje, které je definováno jeho `type` atributem. `guid`Nastavení a `id` tvoří plně kvalifikované ID panelu nástrojů. Obvykle `<Parent>` je nabídka v nabídce obsahující skupinu. Panel nástrojů je však definován jako svůj vlastní nadřazený objekt. Proto se stejný identifikátor používá pro `<Menu>` `<Parent>` elementy a. `priority`Atribut je pouze "0".

4. Panely nástrojů připomínají nabídky mnoha způsoby. Například podobně jako nabídka může mít skupiny příkazů, panely nástrojů mohou mít také skupiny. (V nabídkách jsou skupiny příkazů oddělené horizontálními čárami. V panelech nástrojů nejsou skupiny odděleny vizuálními oddělovači.)

    Přidejte `<Groups>` oddíl, který obsahuje `<Group>` element. Tím se definuje skupina, jejíž ID jste deklarovali v `<Symbols>` části. Přidejte `<Groups>` oddíl hned za `<Menus>` oddíl.

    ```xml
    <Groups>
        <Group guid="guidFirstToolWindowPackageCmdSet" id="ToolbarGroupID" priority="0x0000">
            <Parent guid="guidFirstToolWindowPackageCmdSet" id="ToolbarID" />
        </Group>
    </Groups>
    ```

    Když nastavíte nadřazený identifikátor GUID a ID na GUID a ID panelu nástrojů, přidáte skupinu na panel nástrojů.

## <a name="add-a-command-to-the-toolbar"></a>Přidání příkazu na panel nástrojů

Přidejte příkaz na panel nástrojů, který se zobrazí jako tlačítko.

1. V `<Symbols>` části deklarujte následující prvky IDSymbol hned za deklaracemi skupiny nástrojů a panelů nástrojů.

    ```xml
    <IDSymbol name="cmdidWindowsMedia" value="0x0100" />
    <IDSymbol name="cmdidWindowsMediaOpen" value="0x132" />
    ```

2. Přidejte do oddílu element Button `<Buttons>` . Tento prvek se zobrazí na panelu nástrojů v okně nástroje s ikonou **hledání** (Lupa).

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

    Díky tomu budou příkazy k dispozici v kódu.

## <a name="add-a-mediaplayer-property-to-firsttoolwindowcontrol"></a>Přidání vlastnosti MediaPlayer do FirstToolWindowControl
Z obslužných rutin událostí pro ovládací prvky panelu nástrojů musí být váš kód schopný získat přístup k ovládacímu prvku Media Player, který je podřízenou třídou FirstToolWindowControl.

V **Průzkumník řešení**klikněte pravým tlačítkem myši na *FirstToolWindowControl. XAML*, klikněte na **Zobrazit kód**a přidejte následující kód do třídy FirstToolWindowControl.

```csharp
public System.Windows.Controls.MediaElement MediaPlayer
{
    get { return mediaElement1; }
}
```

## <a name="instantiate-the-tool-window-and-toolbar"></a>Vytvoření instance okna nástrojů a panelu nástrojů
Přidejte panel nástrojů a příkaz nabídky, který vyvolá dialog **otevřít soubor** a přehraje vybraný mediální soubor.

1. Otevřete *FirstToolWindow.cs* a přidejte následující `using` direktivy:

    ```csharp
    using System.ComponentModel.Design;
    using System.Windows.Forms;
    using Microsoft.VisualStudio.Shell.Interop;
    ```

2. Uvnitř třídy FirstToolWindow přidejte veřejný odkaz na ovládací prvek FirstToolWindowControl.

    ```csharp
    public FirstToolWindowControl control;
    ```

3. Na konci konstruktoru nastavte tuto proměnnou ovládacího prvku na nově vytvořený ovládací prvek.

    ```csharp
    control = new FirstToolWindowControl();
    base.Content = control;
    ```

4. Vytvořte instanci panelu nástrojů uvnitř konstruktoru.

    ```csharp
    this.ToolBar = new CommandID(new Guid(FirstToolWindowCommand.guidFirstToolWindowPackageCmdSet),
        FirstToolWindowCommand.ToolbarID);
    this.ToolBarLocation = (int)VSTWT_LOCATION.VSTWT_TOP;
    ```

5. V tomto okamžiku konstruktor FirstToolWindow by měl vypadat takto:

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

6. Přidejte příkaz nabídky na panel nástrojů. Do třídy FirstToolWindowCommand.cs přidejte následující direktivu using:

    ```csharp
    using System.Windows.Forms;
    ```

7. Ve třídě FirstToolWindowCommand přidejte následující kód na konec metody ShowToolWindow (). Příkaz ButtonHandler se implementuje v další části.

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

1. Ve třídě FirstToolWindowCommand přidejte metodu ButtonHandler, která vyvolá dialogové okno **otevřít soubor** . Po výběru souboru se multimediální soubor přehraje.

2. Ve třídě FirstToolWindowCommand přidejte privátní odkaz do okna FirstToolWindow, které se vytvoří v metodě FindToolWindow ().

    ```csharp
    private FirstToolWindow window;
    ```

3. Změňte metodu ShowToolWindow () pro nastavení okna, které jste definovali výše (aby obslužná rutina příkazu ButtonHandler měla přístup k ovládacímu prvku okna. Toto je kompletní metoda ShowToolWindow ().

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

4. Přidejte metodu ButtonHandler. Vytvoří OpenFileDialog pro uživatele, aby určil mediální soubor, který se má přehrát, a pak přehraje vybraný soubor.

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

## <a name="set-the-default-position-for-the-tool-window"></a>Nastavení výchozí pozice pro okno nástroje

Dále zadejte výchozí umístění v integrovaném vývojovém prostředí pro okno nástroje. Konfigurační informace pro okno nástroje jsou v souboru *FirstToolWindowPackage.cs* .

1. V *FirstToolWindowPackage.cs*vyhledejte <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute> atribut `FirstToolWindowPackage` třídy, který předá typ FirstToolWindow konstruktoru. Chcete-li určit výchozí pozici, je nutné přidat další parametry do konstruktoru následujícím příkladem.

    ```csharp
    [ProvideToolWindow(typeof(FirstToolWindow),
        Style = Microsoft.VisualStudio.Shell.VsDockStyle.Tabbed,
        Window = "3ae79031-e1bc-11d0-8f78-00a0c9110057")]
    ```

    První pojmenovaný parametr je `Style` a jeho hodnota je `Tabbed` , což znamená, že okno bude mít kartu v existujícím okně. Pozice ukotvení je určena `Window` parametrem, n tento případ, identifikátor GUID **Průzkumník řešení**.

    > [!NOTE]
    > Další informace o typech oken v integrovaném vývojovém prostředí naleznete v tématu <xref:EnvDTE.vsWindowType> .

## <a name="test-the-tool-window"></a>Test okna nástroje

1. Stisknutím klávesy **F5** otevřete novou instanci experimentálního sestavení sady Visual Studio.

2. V nabídce **zobrazení** přejděte na položku **ostatní okna** a potom klikněte na tlačítko **první okno nástroje**.

    Okno nástroje Media Player by se mělo otevřít na stejné pozici jako **Průzkumník řešení**. Pokud se stále zobrazuje na stejné pozici jako předtím, resetujte rozložení okna (**rozložení okna/obnovit okno**).

3. Klikněte na tlačítko (má ikonu **hledání** ) v okně nástroje. Vyberte podporovaný zvukový soubor nebo videosoubor, například *C:\windows\media\chimes.wav*, a pak stiskněte **otevřít**.

    Měli byste slyšet zvuk CHIME.

## <a name="see-also"></a>Viz také
- [Příkazy, nabídky a panely nástrojů](../extensibility/internals/commands-menus-and-toolbars.md)
