---
title: Přidání panelu nástrojů do okna nástroje | Microsoft Docs
description: Naučte se, jak přidat panel nástrojů, který obsahuje tlačítka, která jsou vázaná na příkazy, do panelu nástrojů v integrovaném vývojovém prostředí (IDE) sady Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- tool windows, adding toolbars
- toolbars [Visual Studio], adding to tool windows
ms.assetid: 172f64b3-87f8-4292-9c1c-65bffa2b0970
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: c0152de94eb74fff902ced4d61c749f7cca3a277
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99951339"
---
# <a name="add-a-toolbar-to-a-tool-window"></a>Přidání panelu nástrojů do okna nástrojů
Tento návod ukazuje, jak přidat panel nástrojů do okna nástroje.

 Panel nástrojů je vodorovný nebo svislý pruh, který obsahuje tlačítka vázaná na příkazy. Délka panelu nástrojů v okně nástroje je vždy stejná jako šířka nebo výška okna nástroje v závislosti na tom, kde je panel nástrojů ukotven.

 Na rozdíl od panelů nástrojů v integrovaném vývojovém prostředí musí být panel nástrojů v okně nástroje ukotven a nelze jej přesunout ani přizpůsobit. Pokud rozhraní VSPackage je napsáno v kódu umanaged, lze panel nástrojů ukotvit na jakémkoli okraji.

 Další informace o tom, jak přidat panel nástrojů, najdete v tématu [Přidání panelu nástrojů](../extensibility/adding-a-toolbar.md).

## <a name="prerequisites"></a>Požadavky
 Od sady Visual Studio 2015 nenainstalujete sadu Visual Studio SDK z webu Stažení softwaru. V instalačním programu sady Visual Studio je zahrnutý jako volitelná funkce. Sadu VS SDK můžete také nainstalovat později. Další informace najdete v tématu [instalace sady Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-toolbar-for-a-tool-window"></a>Vytvoření panelu nástrojů pro okno nástroje

1. Vytvořte projekt VSIX s názvem `TWToolbar` , který má příkaz nabídky s názvem **TWTestCommand** a okno nástrojů s názvem **TestToolWindow**. Další informace najdete v tématu [Vytvoření rozšíření pomocí příkazu nabídky](../extensibility/creating-an-extension-with-a-menu-command.md) a [Vytvoření rozšíření s oknem nástrojů](../extensibility/creating-an-extension-with-a-tool-window.md). Před přidáním šablony okna nástroje je nutné přidat šablonu položky příkazu.

2. V *TWTestCommandPackage. vsct* vyhledejte oddíl symboly. V uzlu GuidSymbol s názvem guidTWTestCommandPackageCmdSet deklarujte panel nástrojů a skupinu panelů nástrojů následujícím způsobem.

    ```xml
    <IDSymbol name="TWToolbar" value="0x1000" />
    <IDSymbol name="TWToolbarGroup" value="0x1050" />
    ```

3. V horní části `Commands` oddílu vytvořte `Menus` oddíl. Přidejte `Menu` prvek pro definování panelu nástrojů.

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

     Panely nástrojů nelze vnořovat jako podnabídky. Proto nemusíte přiřazovat nadřazený objekt. Nemusíte také nastavit prioritu, protože uživatel může přesouvat panely nástrojů. Obvykle je prvotní umístění panelu nástrojů definováno programově, ale následné změny uživatele jsou trvalé.

4. V části skupiny definujte skupinu, která bude obsahovat příkazy pro panel nástrojů.

    ```xml

    <Group guid="guidTWTestCommandPackageCmdSet" id="TWToolbarGroup" priority="0x0000">
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TWToolbar" />
    </Group>
    ```

5. V části tlačítka změňte nadřazeného prvku existujícího tlačítka na skupinu panelů nástrojů tak, aby se panel nástrojů zobrazil.

    ```xml
    <Button guid="guidTWTestCommandPackageCmdSet" id="TWTestCommandId" priority="0x0100" type="Button">
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TWToolbarGroup" />
        <Icon guid="guidImages" id="bmpPic1" />
        <Strings>
            <ButtonText>Invoke TWTestCommand</ButtonText>
        </Strings>
    </Button>
    ```

     Ve výchozím nastavení platí, že pokud panel nástrojů neobsahuje žádné příkazy, nezobrazí se.

     Vzhledem k tomu, že nový panel nástrojů není přidán automaticky do okna nástroje, musí být panel nástrojů přidán explicitně. Tento postup je popsán v následujícím oddíle.

## <a name="add-the-toolbar-to-the-tool-window"></a>Přidat panel nástrojů do okna nástroje

1. Do *TWTestCommandPackageGuids.cs* přidejte následující řádky.

    ```csharp
    public const string guidTWTestCommandPackageCmdSet = "00000000-0000-0000-0000-0000";  // get the GUID from the .vsct file
    public const int TWToolbar = 0x1000;
    ```

2. Do *TestToolWindow.cs* přidejte následující příkaz using.

    ```csharp
    using System.ComponentModel.Design;
    ```

3. V konstruktoru TestToolWindow přidejte následující řádek.

    ```csharp
    this.ToolBar = new CommandID(new Guid(TWTestCommandPackageGuids.guidTWTestCommandPackageCmdSet), TWTestCommandPackageGuids.TWToolbar);
    ```

## <a name="test-the-toolbar-in-the-tool-window"></a>Test panelu nástrojů v okně nástroje

1. Sestavte projekt a spusťte ladění. Měla by se zobrazit experimentální instance sady Visual Studio.

2. V nabídce **Zobrazit/další Windows** klikněte na **test panelu** . zobrazí se okno nástroje.

     Měl by se zobrazit panel nástrojů (vypadá jako výchozí ikona) v levém horním rohu okna nástroje, a to hned pod nadpisem.

3. Na panelu nástrojů klikněte na ikonu, aby se zobrazila zpráva **TWTestCommandPackage uvnitř TWToolbar. TWTestCommand. MenuItemCallback ()**.

## <a name="see-also"></a>Viz také
- [Přidat panel nástrojů](../extensibility/adding-a-toolbar.md)
