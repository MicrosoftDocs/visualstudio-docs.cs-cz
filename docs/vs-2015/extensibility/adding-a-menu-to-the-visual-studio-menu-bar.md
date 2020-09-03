---
title: Přidání nabídky do řádku nabídek | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- menus, creating top level
- top-level menus
ms.assetid: 58fc1a31-2aeb-441c-8e48-c7d5cbcfe501
caps.latest.revision: 52
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 64ab627d785e8b00b5159969a01dc1102df30359
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68184930"
---
# <a name="adding-a-menu-to-the-visual-studio-menu-bar"></a>Přidání nabídky do řádku nabídek v sadě Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tento návod ukazuje, jak přidat nabídku do řádku nabídek integrovaného vývojového prostředí (IDE) sady Visual Studio. Panel nabídek rozhraní IDE obsahuje kategorie nabídky, jako je **soubor**, **Úprava**, **zobrazení**, **okno**a **help**.

 Před přidáním nové nabídky do řádku nabídek sady Visual Studio zvažte, zda by měly být příkazy umístěny v existující nabídce. Další informace o umístění příkazu naleznete v tématu [nabídky a příkazy pro aplikaci Visual Studio](../extensibility/ux-guidelines/menus-and-commands-for-visual-studio.md).

 Nabídky jsou deklarovány v souboru. vsct projektu. Další informace o nabídkách a souborech. vsct naleznete v tématech [příkazy, nabídky a panely nástrojů](../extensibility/internals/commands-menus-and-toolbars.md).

 Po dokončení tohoto návodu můžete vytvořit nabídku s názvem **TestMenu** , která obsahuje jeden příkaz.

## <a name="prerequisites"></a>Předpoklady
 Od sady Visual Studio 2015 nenainstalujete sadu Visual Studio SDK z webu Stažení softwaru. V instalačním programu sady Visual Studio je zahrnutý jako volitelná funkce. Sadu VS SDK můžete také nainstalovat později. Další informace najdete v tématu [instalace sady Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="creating-a-vsix-project-that-has-a-custom-command-item-template"></a>Vytvoření projektu VSIX, který obsahuje šablonu vlastní položky příkazu

1. Vytvořte projekt VSIX s názvem `TopLevelMenu` . Šablonu projektu VSIX můžete najít v dialogovém okně **Nový projekt** v části **Visual C#**  /  **rozšiřitelnost**Visual C#.  Další informace najdete v tématu [Vytvoření rozšíření pomocí příkazu nabídky](../extensibility/creating-an-extension-with-a-menu-command.md).

2. Po otevření projektu přidejte šablonu vlastní položky příkazu s názvem **TestCommand**. V **Průzkumník řešení**klikněte pravým tlačítkem myši na uzel projektu a vyberte **přidat/nová položka**. V dialogovém okně **Přidat novou položku** přejít na **Visual C#/rozšiřitelnost** a vyberte **vlastní příkaz**. V poli **název** v dolní části okna změňte název souboru příkazů na **TestCommand.cs**.

## <a name="creating-a-menu-on-the-ide-menu-bar"></a>Vytvoření nabídky na řádku nabídek rozhraní IDE

#### <a name="to-create-a-menu"></a>Vytvoření nabídky

1. V **Průzkumník řešení**otevřete TestCommandPackage. vsct.

     Na konci souboru je \<Symbols> uzel, který obsahuje několik \<GuidSymbol> uzlů. V uzlu s názvem guidTestCommandPackageCmdSet přidejte nový symbol následujícím způsobem:

    ```xml
    <IDSymbol name="TopLevelMenu" value="0x1021"/>
    ```

2. Vytvořte \<Menus> v uzlu prázdný uzel \<Commands> těsně před \<Groups> . V \<Menus> uzlu přidejte \<Menu> uzel následujícím způsobem:

    ```xml
    <Menus>
          <Menu guid="guidTestCommandPackageCmdSet" id="TopLevelMenu" priority="0x700" type="Menu">
            <Parent guid="guidSHLMainMenu"
                    id="IDG_VS_MM_TOOLSADDINS" />
            <Strings>
              <ButtonText>TestMenu</ButtonText>
              <CommandName>TestMenu</CommandName>
            </Strings>
        </Menu>
    </Menus>
    ```

     `guid`Hodnoty a v `id` nabídce určují sadu příkazů a konkrétní nabídku v sadě příkazů.

     `guid`Hodnoty a `id` nadřazené pozice v nabídce v části řádku nabídek sady Visual Studio, které obsahují nabídky nástroje a doplňky.

     Hodnota `CommandName` řetězce určuje, že se má text zobrazit v položce nabídky.

3. V \<Groups> části vyhledejte \<Group> a změňte element tak, aby \<Parent> odkazoval na nabídku, kterou jste právě přidali:

    ```csharp
    <Groups>
          <Group guid="guidTestCommandPackageCmdSet" id="MyMenuGroup" priority="0x0600">
            <Parent guid="guidTestCommandPackageCmdSet" id="TopLevelMenu"/>
          </Group>
        </Groups>
    ```

     Tím se skupina stane součástí nové nabídky.

4. Vyhledejte `Buttons` část. Všimněte si, že [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Šablona balíčku vygenerovala `Button` prvek, který má svou nadřazenou sadu nastavenou na `MyMenuGroup` . V důsledku toho se tento příkaz zobrazí v nabídce.

## <a name="building-and-testing-the-extension"></a>Sestavení a otestování rozšíření

1. Sestavte projekt a spusťte ladění. Měla by se zobrazit instance experimentální instance.

2. Panel nabídek v experimentální instanci by měl obsahovat **TestMenu** nabídku.

3. V nabídce **TestMenu** klikněte na příkaz **vyvolat test Command**.

     Zobrazí se okno se zprávou a zobrazí se zpráva "balíček TestCommand" v TopLevelMenu. TestCommand. MenuItemCallback () ". To znamená, že nový příkaz funguje.

## <a name="see-also"></a>Viz také
 [Příkazy, nabídky a panely nástrojů](../extensibility/internals/commands-menus-and-toolbars.md)
