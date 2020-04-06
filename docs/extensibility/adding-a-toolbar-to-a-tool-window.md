---
title: Přidání panelu nástrojů do okna nástroje | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- tool windows, adding toolbars
- toolbars [Visual Studio], adding to tool windows
ms.assetid: 172f64b3-87f8-4292-9c1c-65bffa2b0970
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 094515eb94279623974bd7b55cc9923c49625a70
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740242"
---
# <a name="add-a-toolbar-to-a-tool-window"></a>Přidání panelu nástrojů do okna nástroje
Tento návod ukazuje, jak přidat panel nástrojů do okna nástroje.

 Panel nástrojů je vodorovný nebo svislý pruh, který obsahuje tlačítka vázaná na příkazy. Délka panelu nástrojů v okně nástroje je vždy stejná jako šířka nebo výška okna nástroje v závislosti na tom, kde je panel nástrojů ukotven.

 Na rozdíl od panelů nástrojů v ide musí být panel nástrojů v okně nástroje ukotven ý nelze jej přesunout ani přizpůsobit. Pokud Je napsán v uspravovaný kód, panel nástrojů lze ukotvit na libovolné masivu.

 Další informace o přidání panelu nástrojů naleznete v [tématu Přidání panelu nástrojů](../extensibility/adding-a-toolbar.md).

## <a name="prerequisites"></a>Požadavky
 Počínaje Visual Studio 2015 neinstalujete sady Visual Studio SDK ze služby stažení. Je součástí volitelné funkce v nastavení sady Visual Studio. VS SDK můžete také nainstalovat později. Další informace naleznete [v tématu Instalace sady Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-toolbar-for-a-tool-window"></a>Vytvoření panelu nástrojů pro okno nástroje

1. Vytvořte projekt VSIX s názvem, `TWToolbar` který má příkaz nabídky s názvem **TWTestCommand** a okno nástroje s názvem **TestToolWindow**. Další informace naleznete [v tématech Vytvoření rozšíření s příkazem nabídky](../extensibility/creating-an-extension-with-a-menu-command.md) a Vytvoření rozšíření s [oknem nástroje](../extensibility/creating-an-extension-with-a-tool-window.md). Před přidáním šablony okna nástroje je třeba přidat šablonu příkazové položky.

2. V *souboru TWTestCommandPackage.vsct*vyhledejte oddíl Symboly. V uzlu GuidSymbol s názvem guidTWTestCommandPackageCmdSet deklaruje panel nástrojů a skupinu panelu nástrojů následujícím způsobem.

    ```xml
    <IDSymbol name="TWToolbar" value="0x1000" />
    <IDSymbol name="TWToolbarGroup" value="0x1050" />
    ```

3. V horní části `Commands` oddílu `Menus` vytvořte oddíl. Přidejte `Menu` prvek, který definuje panel nástrojů.

    ```xml
    <Menus>
        <Menu guid="guidTWTestCommandPackageCmdSet" id="TWToolbar" type="ToolWindowToolbar">
            <CommandFlag>DefaultDocked</CommandFlag>
            <Strings>
                <ButtonText>Test Toolbar</ButtonText>
                <CommandName>Test Toolbar</CommandName>
            </Strings>
        </Menu>
    </Menus>
    ```

     Panely nástrojů nelze vnořit jako podnabídky. Proto není třeba přiřadit nadřazený. Také není třeba nastavit prioritu, protože uživatel může přesunout panely nástrojů. Počáteční umístění panelu nástrojů je obvykle definovánprogramově, ale následné změny uživatele jsou trvalé.

4. V části Skupiny definujte skupinu, která bude obsahovat příkazy pro panel nástrojů.

    ```xml

    <Group guid="guidTWTestCommandPackageCmdSet" id="TWToolbarGroup" priority="0x0000">
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TWToolbar" />
    </Group>
    ```

5. V části Tlačítka změňte nadřazený prvek existujícího buttonu na skupinu panelu nástrojů tak, aby se zobrazil panel nástrojů.

    ```xml
    <Button guid="guidTWTestCommandPackageCmdSet" id="TWTestCommandId" priority="0x0100" type="Button">
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TWToolbarGroup" />
        <Icon guid="guidImages" id="bmpPic1" />
        <Strings>
            <ButtonText>Invoke TWTestCommand</ButtonText>
        </Strings>
    </Button>
    ```

     Ve výchozím nastavení, pokud panel nástrojů nemá žádné příkazy, nezobrazí se.

     Vzhledem k tomu, že nový panel nástrojů není automaticky přidán do okna nástroje, musí být panel nástrojů přidán explicitně. Tento postup je popsán v následujícím oddíle.

## <a name="add-the-toolbar-to-the-tool-window"></a>Přidání panelu nástrojů do okna nástroje

1. Do *TWTestCommandPackageGuids.cs* přidejte následující řádky.

    ```csharp
    public const string guidTWTestCommandPackageCmdSet = "00000000-0000-0000-0000-0000";  // get the GUID from the .vsct file
    public const int TWToolbar = 0x1000;
    ```

2. V *TestToolWindow.cs* přidejte následující příkaz using.

    ```csharp
    using System.ComponentModel.Design;
    ```

3. V Konstruktoru TestToolWindow přidejte následující řádek.

    ```csharp
    this.ToolBar = new CommandID(new Guid(TWTestCommandPackageGuids.guidTWTestCommandPackageCmdSet), TWTestCommandPackageGuids.TWToolbar);
    ```

## <a name="test-the-toolbar-in-the-tool-window"></a>Testování panelu nástrojů v okně nástroje

1. Sestavení projektu a začít ladění. Měla by se zobrazit experimentální instance sady Visual Studio.

2. V nabídce **Zobrazení / Ostatní Windows** klikněte na Test **ToolWindow** a zobrazte okno nástroje.

     V levém horním rohu okna nástroje, těsně pod názvem, by se měl zobrazit panel nástrojů (vypadá jako výchozí ikona).

3. Na panelu nástrojů klepněte na ikonu pro zobrazení zprávy **TWTestCommandPackage Inside TWToolbar.TWTestCommand.MenuItemCallback()**.

## <a name="see-also"></a>Viz také
- [Přidání panelu nástrojů](../extensibility/adding-a-toolbar.md)
