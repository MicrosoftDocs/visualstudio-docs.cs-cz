---
title: Přidání ovladače nabídky na panel nástrojů | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- toolbars [Visual Studio], adding menu controllers
- menus, adding menu controllers to toolbars
- menu controllers, adding to toolbars
ms.assetid: 6af9b0b4-037f-404c-bb40-aaa1970768ea
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d4dcb9e51f6633476a8f0eadea30da513e5ef760
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740327"
---
# <a name="add-a-menu-controller-to-a-toolbar"></a>Přidání ovladače nabídky na panel nástrojů
Tento návod se staví na [panelu nástrojů Přidat do návodu k oknu nástroje](../extensibility/adding-a-toolbar-to-a-tool-window.md) a ukáže, jak přidat ovladač nabídky na panel nástrojů okna nástroje. Zde uvedené kroky lze také použít na panel nástrojů, který je vytvořen v [návodu k přidání panelu nástrojů.](../extensibility/adding-a-toolbar.md)

Řadič nabídky je ovládací prvek rozdělení. Na levé straně ovladače nabídky se zobrazí naposledy použitý příkaz a můžete jej spustit klepnutím. Pravá strana ovladače nabídky je šipka, která po klepnutí otevře seznam dalších příkazů. Po klepnutí na příkaz v seznamu se příkaz spustí a nahradí příkaz na levé straně ovladače nabídky. Tímto způsobem ovladač nabídky funguje jako příkazové tlačítko, které vždy zobrazuje naposledy použitý příkaz ze seznamu.

Ovladače nabídek se mohou zobrazit v nabídkách, ale nejčastěji se používají na panelech nástrojů.

## <a name="prerequisites"></a>Požadavky
Počínaje Visual Studio 2015 neinstalujete sady Visual Studio SDK ze služby stažení. Je součástí volitelné funkce v nastavení sady Visual Studio. VS SDK můžete také nainstalovat později. Další informace naleznete [v tématu Instalace sady Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-menu-controller"></a>Vytvoření ovladače nabídky

1. Postupujte podle postupů popsaných v [části Přidání panelu nástrojů do okna nástroje](../extensibility/adding-a-toolbar-to-a-tool-window.md) a vytvořte okno nástroje, které má panel nástrojů.

2. V *souboru TWTestCommandPackage.vsct*přejděte do části Symboly. V prvku GuidSymbol s názvem **guidTWTestCommandPackageCmdSet**deklarujte řadič nabídky, skupinu řadičů nabídek a tři položky nabídky.

    ```xml
    <IDSymbol name="TestMenuController" value="0x1300" /><IDSymbol name="TestMenuControllerGroup" value="0x1060" /><IDSymbol name="cmdidMCItem1" value="0x0130" /><IDSymbol name="cmdidMCItem2" value="0x0131" /><IDSymbol name="cmdidMCItem3" value="0x0132" />
    ```

3. V části Nabídky po poslední položce nabídky definujte ovladač nabídky jako nabídku.

    ```xml
    <Menu guid="guidTWTestCommandPackageCmdSet" id="TestMenuController" priority="0x0100" type="MenuController">
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TWToolbarGroup" />
        <CommandFlag>IconAndText</CommandFlag>
        <CommandFlag>TextChanges</CommandFlag>
        <CommandFlag>TextIsAnchorCommand</CommandFlag>
        <Strings>
            <ButtonText>Test Menu Controller</ButtonText>
            <CommandName>Test Menu Controller</CommandName>
        </Strings>
    </Menu>
    ```

    Příznaky `TextChanges` `TextIsAnchorCommand` a musí být zahrnuty, aby řadič nabídky odrážel poslední vybraný příkaz.

4. V části Skupiny přidejte po poslední položce skupiny skupinu řadiče nabídky.

    ```xml
    <Group guid="guidTWTestCommandPackageCmdSet" id="TestMenuControllerGroup" priority="0x000">
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TestMenuController" />
    </Group>
    ```

    Nastavením řadiče nabídky jako nadřazeného se všechny příkazy umístěné v této skupině zobrazí v kontroleru nabídky. Atribut `priority` je vynechán, který jej nastaví na výchozí hodnotu 0, protože je jedinou skupinou na řadiči nabídky.

5. V části Tlačítka po poslední položce tlačítka přidejte prvek Button pro každou položku nabídky.

    ```xml
    <Button guid="guidTWTestCommandPackageCmdSet" id="cmdidMCItem1" priority="0x0000" type="Button">
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TestMenuControllerGroup" />
        <Icon guid="guidImages" id="bmpPic1" />
        <CommandFlag>IconAndText</CommandFlag>
        <Strings>
            <ButtonText>MC Item 1</ButtonText>
            <CommandName>MC Item 1</CommandName>
        </Strings>
    </Button>
    <Button guid="guidTWTestCommandPackageCmdSet" id="cmdidMCItem2" priority="0x0100" type="Button">
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TestMenuControllerGroup" />
        <Icon guid="guidImages" id="bmpPic2" />
        <CommandFlag>IconAndText</CommandFlag>
        <Strings>
            <ButtonText>MC Item 2</ButtonText>
            <CommandName>MC Item 2</CommandName>
        </Strings>
    </Button>
    <Button guid="guidTWTestCommandPackageCmdSet" id="cmdidMCItem3" priority="0x0200" type="Button">
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TestMenuControllerGroup" />
        <Icon guid="guidImages" id="bmpPicSearch" />
        <CommandFlag>IconAndText</CommandFlag>
        <Strings>
            <ButtonText>MC Item 3</ButtonText>
            <CommandName>MC Item 3</CommandName>
        </Strings>
    </Button>
    ```

6. V tomto okamžiku se můžete podívat na řadič nabídky. Sestavení projektu a začít ladění. Měli byste vidět experimentální instanci.

   1. V nabídce **Zobrazení / Ostatní Windows** otevřete možnost Test **ToolWindow**.

   2. Na panelu nástrojů v okně nástroje se zobrazí ovladač nabídky.

   3. Kliknutím na šipku na pravé straně ovladače nabídky zobrazíte tři možné příkazy.

      Všimněte si, že po klepnutí na příkaz se název ovladače nabídky změní, aby se tento příkaz zobrazil. V další části přidáme kód pro aktivaci těchto příkazů.

## <a name="implement-the-menu-controller-commands"></a>Implementace příkazů řadiče nabídky

1. V *TWTestCommandPackageGuids.cs*přidejte ID příkazů pro tři položky nabídky za existující ID příkazů.

    ```csharp
    public const int cmdidMCItem1 = 0x130;
    public const int cmdidMCItem2 = 0x131;
    public const int cmdidMCItem3 = 0x132;
    ```

2. V *TWTestCommand.cs*přidejte následující kód na `TWTestCommand` začátek třídy.

    ```csharp
    private int currentMCCommand; // The currently selected menu controller command
    ```

3. V konstruktoru TWTestCommand po posledním `AddCommand` volání metody přidejte kód pro směrování událostí pro každý příkaz prostřednictvím stejných obslužných rutin.

    ```csharp
    for (int i = TWTestCommandPackageGuids.cmdidMCItem1; i <=
        TWTestCommandPackageGuids.cmdidMCItem3; i++)
    {
        CommandID cmdID = new
        CommandID(new Guid(TWTestCommandPackageGuids.guidTWTestCommandPackageCmdSet), i);
        OleMenuCommand mc = new OleMenuCommand(new
          EventHandler(OnMCItemClicked), cmdID);
        mc.BeforeQueryStatus += new EventHandler(OnMCItemQueryStatus);
        commandService.AddCommand(mc);
        // The first item is, by default, checked. 
        if (TWTestCommandPackageGuids.cmdidMCItem1 == i)
        {
            mc.Checked = true;
            this.currentMCCommand = i;
        }
    }
    ```

4. Přidejte obslužnou rutinu události do třídy **TWTestCommand** a označte vybraný příkaz jako zaškrtnutý.

    ```csharp
    private void OnMCItemQueryStatus(object sender, EventArgs e)
    {
        OleMenuCommand mc = sender as OleMenuCommand;
        if (null != mc)
        {
            mc.Checked = (mc.CommandID.ID == this.currentMCCommand);
        }
    }
    ```

5. Přidejte obslužnou rutinu události, která zobrazí messagebox, když uživatel vybere příkaz na řadiči nabídky:

    ```csharp
    private void OnMCItemClicked(object sender, EventArgs e)
    {
        OleMenuCommand mc = sender as OleMenuCommand;
        if (null != mc)
        {
            string selection;
            switch (mc.CommandID.ID)
            {
                case c.cmdidMCItem1:
                    selection = "Menu controller Item 1";
                    break;

                case TWTestCommandPackageGuids.cmdidMCItem2:
                    selection = "Menu controller Item 2";
                    break;

                case TWTestCommandPackageGuids.cmdidMCItem3:
                    selection = "Menu controller Item 3";
                    break;

                default:
                    selection = "Unknown command";
                    break;
            }
            this.currentMCCommand = mc.CommandID.ID;

            IVsUIShell uiShell =
              (IVsUIShell) ServiceProvider.GetService(typeof(SVsUIShell));
            Guid clsid = Guid.Empty;
            int result;
            uiShell.ShowMessageBox(
                    0,
                    ref clsid,
                    "Test Tool Window Toolbar Package",
                    string.Format(CultureInfo.CurrentCulture,
                                 "You selected {0}", selection),
                    string.Empty,
                    0,
                    OLEMSGBUTTON.OLEMSGBUTTON_OK,
                    OLEMSGDEFBUTTON.OLEMSGDEFBUTTON_FIRST,
                    OLEMSGICON.OLEMSGICON_INFO,
                    0,
                    out result);
        }
    }
    ```

## <a name="testing-the-menu-controller"></a>Testování ovladače nabídky

1. Sestavení projektu a začít ladění. Měli byste vidět experimentální instanci.

2. Otevřete **okno testovacího nástroje** v nabídce Zobrazení / Ostatní **Windows.**

    V panelu nástrojů v okně nástroje se zobrazí kontrolka nabídky a zobrazí **položku MC 1**.

3. Klepněte na tlačítko ovladače nabídky vlevo od šipky.

    Měli byste vidět tři položky, z nichž první je vybrána a má pole zvýraznění kolem ikony. Klepněte na **položku MC 3**.

    Zobrazí se dialogové okno se **zprávou: Vybraná položka menu Položka 3**. Všimněte si, že zpráva odpovídá textu na tlačítku řadiče nabídky. Na tlačítku ovladače nabídky se nyní zobrazí **položka MC 3**.

## <a name="see-also"></a>Viz také
- [Přidání panelu nástrojů do okna nástroje](../extensibility/adding-a-toolbar-to-a-tool-window.md)
- [Přidání panelu nástrojů](../extensibility/adding-a-toolbar.md)
