---
title: Přidání nabídky do panelu nabídek aplikace Visual Studio | Microsoft Docs
description: Naučte se, jak přidat nabídku do řádku nabídek integrovaného vývojového prostředí (IDE) sady Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 3/16/2019
ms.topic: how-to
helpviewer_keywords:
- menus, creating top level
- top-level menus
ms.assetid: 58fc1a31-2aeb-441c-8e48-c7d5cbcfe501
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 6bd568e53c3a74819f642f0593524b314e065afb
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99951560"
---
# <a name="add-a-menu-to-the-visual-studio-menu-bar"></a>Přidání nabídky do řádku nabídek sady Visual Studio

Tento návod ukazuje, jak přidat nabídku do řádku nabídek integrovaného vývojového prostředí (IDE) sady Visual Studio. Panel nabídek rozhraní IDE obsahuje kategorie nabídky, jako je **soubor**, **Úprava**, **zobrazení**, **okno** a **help**.

Před přidáním nové nabídky do řádku nabídek sady Visual Studio zvažte, zda by měly být příkazy umístěny v existující nabídce. Další informace o umístění příkazu naleznete v tématu [nabídky a příkazy pro aplikaci Visual Studio](../extensibility/ux-guidelines/menus-and-commands-for-visual-studio.md).

Nabídky jsou deklarovány v souboru *. vsct* projektu. Další informace o nabídkách a souborech *. vsct* naleznete v tématech [příkazy, nabídky a panely nástrojů](../extensibility/internals/commands-menus-and-toolbars.md).

Po dokončení tohoto návodu můžete vytvořit nabídku s názvem **Nabídka testu** , která obsahuje jeden příkaz.

:::moniker range=">=vs-2019"
> [!NOTE]
> Od sady Visual Studio 2019 jsou nabídky nejvyšší úrovně, které přispěly rozšířeními, umístěné v nabídce **rozšíření** .
:::moniker-end

## <a name="prerequisites"></a>Požadavky

Od sady Visual Studio 2015 nenainstalujete sadu Visual Studio SDK z webu Stažení softwaru. V instalačním programu sady Visual Studio je zahrnutý jako volitelná funkce. Sadu VS SDK můžete také nainstalovat později. Další informace najdete v tématu [instalace sady Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-vsix-project-that-has-a-custom-command-item-template"></a>Vytvoření projektu VSIX, který obsahuje šablonu vlastní položky příkazu

1. Vytvořte projekt VSIX s názvem `TopLevelMenu` . Šablonu projektu VSIX můžete najít v dialogovém okně **Nový projekt** hledáním "VSIX".  Další informace najdete v tématu [Vytvoření rozšíření pomocí příkazu nabídky](../extensibility/creating-an-extension-with-a-menu-command.md).

::: moniker range="vs-2017"

2. Po otevření projektu přidejte šablonu vlastní položky příkazu s názvem **TestCommand**. V **Průzkumník řešení** klikněte pravým tlačítkem myši na uzel projektu a vyberte možnost **Přidat**  >   **novou položku**. V dialogovém okně **Přidat novou položku** přejít na **Visual C#/rozšiřitelnost** a vyberte **vlastní příkaz**. V poli **název** v dolní části okna změňte název souboru příkazů na *TestCommand.cs*.

::: moniker-end

::: moniker range=">=vs-2019"

2. Po otevření projektu přidejte šablonu vlastní položky příkazu s názvem **TestCommand**. V **Průzkumník řešení** klikněte pravým tlačítkem myši na uzel projektu a vyberte možnost **Přidat**  >   **novou položku**. V dialogovém okně **Přidat novou položku** přejdete na **Visual C#/rozšiřitelnost** a vyberte **příkaz**. V poli **název** v dolní části okna změňte název souboru příkazů na *TestCommand.cs*.

::: moniker-end

## <a name="create-a-menu-on-the-ide-menu-bar"></a>Vytvoření nabídky na řádku nabídek rozhraní IDE

::: moniker range="vs-2017"

1. V **Průzkumník řešení** otevřete *TestCommandPackage. vsct*.

    Na konci souboru je `<Symbols>` uzel, který obsahuje několik `<GuidSymbol>` uzlů. V uzlu s názvem `guidTestCommandPackageCmdSet` přidejte nový symbol následujícím způsobem:

   ```xml
   <IDSymbol name="TopLevelMenu" value="0x1021"/>
   ```

2. Vytvořte `<Menus>` v uzlu prázdný uzel `<Commands>` těsně před `<Groups>` . V `<Menus>` uzlu přidejte `<Menu>` uzel následujícím způsobem:

   ```xml
   <Menus>
         <Menu guid="guidTestCommandPackageCmdSet" id="TopLevelMenu" priority="0x700" type="Menu">
           <Parent guid="guidSHLMainMenu"
                   id="IDG_VS_MM_TOOLSADDINS" />
           <Strings>
             <ButtonText>Test Menu</ButtonText>
           </Strings>
       </Menu>
   </Menus>
   ```

    `guid`Hodnoty a v `id` nabídce určují sadu příkazů a konkrétní nabídku v sadě příkazů.

    `guid`Hodnoty a `id` nadřazené pozice v nabídce v části řádku nabídek sady Visual Studio, které obsahují nabídky nástroje a doplňky.

    `<ButtonText>`Prvek určuje, že se má text zobrazit v položce nabídky.

3. V `<Groups>` části vyhledejte `<Group>` a změňte element tak, aby `<Parent>` odkazoval na nabídku, kterou jste právě přidali:

   ```xml
   <Groups>
       <Group guid="guidTestCommandPackageCmdSet" id="MyMenuGroup" priority="0x0600">
           <Parent guid="guidTestCommandPackageCmdSet" id="TopLevelMenu"/>
       </Group>
   </Groups>
   ```

    Tím se skupina stane součástí nové nabídky.

::: moniker-end

::: moniker range=">=vs-2019"

1. V **Průzkumník řešení** otevřete *TopLevelMenuPackage. vsct*.

    Na konci souboru je `<Symbols>` uzel, který obsahuje několik `<GuidSymbol>` uzlů. V uzlu s názvem `guidTopLevelMenuPackageCmdSet` přidejte nový symbol následujícím způsobem:

   ```xml
   <IDSymbol name="TopLevelMenu" value="0x1021"/>
   ```

2. Vytvořte `<Menus>` v uzlu prázdný uzel `<Commands>` těsně před `<Groups>` . V `<Menus>` uzlu přidejte `<Menu>` uzel následujícím způsobem:

   ```xml
   <Menus>
         <Menu guid="guidTopLevelMenuPackageCmdSet" id="TopLevelMenu" priority="0x700" type="Menu">
           <Parent guid="guidSHLMainMenu"
                   id="IDG_VS_MM_TOOLSADDINS" />
           <Strings>
             <ButtonText>Test Menu</ButtonText>
           </Strings>
       </Menu>
   </Menus>
   ```

    `guid`Hodnoty a v `id` nabídce určují sadu příkazů a konkrétní nabídku v sadě příkazů.

    `guid`Hodnoty a `id` nadřazené pozice v nabídce v části řádku nabídek sady Visual Studio, které obsahují nabídky nástroje a doplňky.

    `<ButtonText>`Prvek určuje, že se má text zobrazit v položce nabídky.

3. V `<Groups>` části vyhledejte `<Group>` a změňte element tak, aby `<Parent>` odkazoval na nabídku, kterou jste právě přidali:

   ```xml
   <Groups>
       <Group guid="guidTopLevelMenuPackageCmdSet" id="MyMenuGroup" priority="0x0600">
           <Parent guid="guidTopLevelMenuPackageCmdSet" id="TopLevelMenu"/>
       </Group>
   </Groups>
   ```

    Tím se skupina stane součástí nové nabídky.

::: moniker-end

4. V `<Buttons>` části vyhledejte `<Button>` uzel. Poté v `<Strings>` uzlu změňte `<ButtonText>` element na `Test Command` .

    Všimněte si, že [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Šablona balíčku vygenerovala `Button` prvek, který má svou nadřazenou sadu nastavenou na `MyMenuGroup` . V důsledku toho se tento příkaz zobrazí v nabídce.

## <a name="build-and-test-the-extension"></a>Sestavení a otestování rozšíření

1. Sestavte projekt a spusťte ladění. Měla by se zobrazit instance experimentální instance.

::: moniker range="vs-2017"

2. Panel nabídek v experimentální instanci by měl obsahovat nabídku **nabídky testu** .

::: moniker-end

::: moniker range=">=vs-2019"

2. Nabídka **rozšíření** v experimentální instanci by měla obsahovat nabídku **nabídky testu** .

::: moniker-end

3. V nabídce **test** vyberte **příkaz Test**.

    Zobrazí se okno se zprávou a zobrazí se zpráva "TestCommand uvnitř TopLevelMenu. TestCommand. MenuItemCallback ()".

## <a name="see-also"></a>Viz také

- [Příkazy, nabídky a panely nástrojů](../extensibility/internals/commands-menus-and-toolbars.md)
