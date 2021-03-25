---
title: Přidání řadiče nabídky na panel nástrojů | Microsoft Docs
description: Naučte se vytvořit kontroler nabídek a přidat ho do panelu nástrojů panelu nástrojů v sadě Visual Studio a potom implementovat příkazy řadiče nabídky a otestovat ho.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- toolbars [Visual Studio], adding menu controllers
- menus, adding menu controllers to toolbars
- menu controllers, adding to toolbars
ms.assetid: 6af9b0b4-037f-404c-bb40-aaa1970768ea
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 304f4ea11abc332c01603f96b6b67c0bd22e38c6
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105060065"
---
# <a name="add-a-menu-controller-to-a-toolbar"></a>Přidání řadiče nabídky na panel nástrojů
Tento názorný postup sestaví na panelu nástrojů [Přidat panel nástrojů](../extensibility/adding-a-toolbar-to-a-tool-window.md) a ukazuje, jak přidat řadič nabídky do panelu nástrojů okna nástroje. Níže uvedené kroky lze použít také na panelu nástrojů, který je vytvořen v návodu [Přidat panel nástrojů](../extensibility/adding-a-toolbar.md) .

Kontroler nabídek je rozdělený ovládací prvek. Levá strana řadiče nabídky zobrazuje poslední použitý příkaz a můžete ho spustit kliknutím na něj. Pravá strana řadiče nabídky je šipka, kterou po kliknutí otevře seznam dalších příkazů. Když kliknete na příkaz v seznamu, příkaz se spustí a nahradí příkaz na levé straně řadiče nabídky. Tímto způsobem kontroler nabídek funguje jako příkazové tlačítko, které vždy zobrazuje poslední použitý příkaz ze seznamu.

Řadiče nabídek se mohou zobrazovat v nabídkách, ale nejčastěji se používají na panelech nástrojů.

## <a name="prerequisites"></a>Požadavky
Od sady Visual Studio 2015 nenainstalujete sadu Visual Studio SDK z webu Stažení softwaru. V instalačním programu sady Visual Studio je zahrnutý jako volitelná funkce. Sadu VS SDK můžete také nainstalovat později. Další informace najdete v tématu [instalace sady Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-menu-controller"></a>Vytvoření kontroleru nabídek

1. Postupujte podle pokynů popsaných v tématu [Přidání panelu nástrojů do okna nástroje](../extensibility/adding-a-toolbar-to-a-tool-window.md) k vytvoření panelu nástrojů, který obsahuje panel nástrojů.

2. V *TWTestCommandPackage. vsct* přejít do části symboly. V elementu GuidSymbol s názvem **guidTWTestCommandPackageCmdSet** deklarujte svůj kontroler nabídek, skupinu kontrolérů nabídky a tři položky nabídky.

    ```xml
    <IDSymbol name="TestMenuController" value="0x1300" /><IDSymbol name="TestMenuControllerGroup" value="0x1060" /><IDSymbol name="cmdidMCItem1" value="0x0130" /><IDSymbol name="cmdidMCItem2" value="0x0131" /><IDSymbol name="cmdidMCItem3" value="0x0132" />
    ```

3. V části nabídky za poslední položkou nabídky definujte jako nabídku kontroler nabídek.

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

    `TextChanges` `TextIsAnchorCommand` Aby mohl řadič nabídky odrážet poslední vybraný příkaz, musí být zahrnuté příznaky a.

4. V části skupiny za poslední položkou skupiny přidejte skupinu řadičů nabídek.

    ```xml
    <Group guid="guidTWTestCommandPackageCmdSet" id="TestMenuControllerGroup" priority="0x000">
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TestMenuController" />
    </Group>
    ```

    Nastavením řadiče nabídky jako nadřazeného objektu se zobrazí všechny příkazy, které jsou umístěny v této skupině, na řadiči nabídky. `priority`Atribut je vynechán, což nastaví výchozí hodnotu 0, protože se jedná o jedinou skupinu na řadiči nabídky.

5. V části tlačítka za položkou poslední tlačítko přidejte element Button pro každou položku nabídky.

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

6. V tomto okamžiku se můžete podívat na kontroler nabídek. Sestavte projekt a spusťte ladění. Měla by se zobrazit experimentální instance.

   1. V nabídce **Zobrazit/další Windows** otevřete **test panelu**.

   2. Kontroler nabídek se zobrazí na panelu nástrojů v okně nástroje.

   3. Kliknutím na šipku na pravé straně řadiče nabídky zobrazíte tři možné příkazy.

      Všimněte si, že když kliknete na příkaz, název řadiče nabídky se změní a zobrazí se tento příkaz. V další části přidáme kód, který bude tyto příkazy aktivovat.

## <a name="implement-the-menu-controller-commands"></a>Implementace příkazů řadiče nabídky

1. V *TWTestCommandPackageGuids. cs* přidejte identifikátory příkazů pro tři položky nabídky za existující identifikátory příkazů.

    ```csharp
    public const int cmdidMCItem1 = 0x130;
    public const int cmdidMCItem2 = 0x131;
    public const int cmdidMCItem3 = 0x132;
    ```

2. V *TWTestCommand. cs* přidejte následující kód na začátek `TWTestCommand` třídy.

    ```csharp
    private int currentMCCommand; // The currently selected menu controller command
    ```

3. V konstruktoru TWTestCommand po posledním volání `AddCommand` metody přidejte kód pro směrování událostí pro každý příkaz přes stejné obslužné rutiny.

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

4. Přidejte obslužnou rutinu události do třídy **TWTestCommand** k označení vybraného příkazu jako zaškrtnutého.

    ```csharp
    private void OnMCItemQueryStatus(object sender, EventArgs e)
    {
        OleMenuCommand mc = sender as OleMenuCommand;
        if (null != mc)
        {
            mc.Checked = (mc.CommandID.ID == this.currentMCCommand);
        }
    }
    ```

5. Přidejte obslužnou rutinu události, která zobrazí MessageBox, když uživatel vybere příkaz na řadiči nabídky:

    ```csharp
    private void OnMCItemClicked(object sender, EventArgs e)
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

## <a name="testing-the-menu-controller"></a>Testování řadiče nabídky

1. Sestavte projekt a spusťte ladění. Měla by se zobrazit experimentální instance.

2. V nabídce **Zobrazit/další Windows** otevřete **test panelu** .

    Kontroler nabídky se zobrazí na panelu nástrojů v okně nástroje a zobrazí **MC Item 1**.

3. Klikněte na tlačítko řadiče nabídky nalevo od šipky.

    Měli byste vidět tři položky, první z nich je vybraná a má zvýrazněné pole kolem ikony. Klikněte na tlačítko **MC položku 3**.

    Zobrazí se dialogové okno se zprávou **, kterou jste vybrali jako položku řadiče nabídky 3**. Všimněte si, že zpráva odpovídá textu na tlačítku řadiče nabídky. Tlačítko řadič nabídky teď zobrazuje **položku 3**.

## <a name="see-also"></a>Viz také
- [Přidání panelu nástrojů do okna nástroje](../extensibility/adding-a-toolbar-to-a-tool-window.md)
- [Přidání panelu nástrojů](../extensibility/adding-a-toolbar.md)
