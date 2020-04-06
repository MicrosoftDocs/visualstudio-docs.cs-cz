---
title: Přidání nabídky na panel nabídek sady Visual Studio | Dokumenty společnosti Microsoft
ms.date: 3/16/2019
ms.topic: conceptual
helpviewer_keywords:
- menus, creating top level
- top-level menus
ms.assetid: 58fc1a31-2aeb-441c-8e48-c7d5cbcfe501
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 91e5a6e1714dbb87abc67fbf722c3bbd1a194a5b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740308"
---
# <a name="add-a-menu-to-the-visual-studio-menu-bar"></a>Přidání nabídky do panelu nabídek sady Visual Studio

Tento návod ukazuje, jak přidat nabídku do panelu nabídek integrovaného vývojového prostředí sady Visual Studio (IDE). Panel nabídek IDE obsahuje kategorie nabídek, jako je **Soubor**, **Úprava**, **Zobrazení**, **Okno**a **Nápověda**.

Před přidáním nové nabídky do panelu nabídek sady Visual Studio zvažte, zda mají být příkazy umístěny v existující nabídce. Další informace o umístění příkazů naleznete v [tématu Nabídky a příkazy pro visual studio](../extensibility/ux-guidelines/menus-and-commands-for-visual-studio.md).

Nabídky jsou deklarovány v souboru *.vsct* projektu. Další informace o nabídkách a *souborech VSCT naleznete v* [tématu Příkazy, nabídky a panely nástrojů](../extensibility/internals/commands-menus-and-toolbars.md).

Dokončením tohoto návodu můžete vytvořit nabídku s názvem **TestMenu,** která obsahuje jeden příkaz.

> [!NOTE]
> Ve VS 2019 jsou nabídky nejvyšší úrovně, které přispívají rozšířeními, umístěny pod nabídkou **Rozšíření.**

## <a name="prerequisites"></a>Požadavky

Počínaje Visual Studio 2015 neinstalujete sady Visual Studio SDK ze služby stažení. Je součástí volitelné funkce v nastavení sady Visual Studio. VS SDK můžete také nainstalovat později. Další informace naleznete [v tématu Instalace sady Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-vsix-project-that-has-a-custom-command-item-template"></a>Vytvoření projektu VSIX, který má vlastní šablonu položky příkazu

1. Vytvořte projekt VSIX s názvem `TopLevelMenu`. Šablonu projektu VSIX najdete v dialogovém okně **Nový projekt** vyhledáním "vsix".  Další informace naleznete [v tématu Vytvoření rozšíření pomocí příkazu nabídky](../extensibility/creating-an-extension-with-a-menu-command.md).

2. Při otevření projektu přidejte vlastní šablonu položky příkazu s názvem **TestCommand**. V **Průzkumníku řešení**klepněte pravým tlačítkem myši na uzel projektu a vyberte **přidat** >  **novou položku**. V dialogovém okně **Přidat novou položku** přejděte na **Visual C# / Rozšiřitelnost** a vyberte **vlastní příkaz**. V poli **Název** v dolní části okna změňte název příkazového souboru na *TestCommand.cs*.

## <a name="create-a-menu-on-the-ide-menu-bar"></a>Vytvoření nabídky na řádku nabídek IDE

::: moniker range="vs-2017"

1. V **Průzkumníku řešení**otevřete *soubor TestCommandPackage.vsct*.

    Na konci souboru je \<symboly> uzel, \<který obsahuje několik GuidSymbol> uzly. V uzlu s názvem guidTestCommandPackageCmdSet přidejte nový symbol takto:

   ```xml
   <IDSymbol name="TopLevelMenu" value="0x1021"/>
   ```

2. Vytvořte \<prázdný uzel> nabídek \<v uzlu příkazy \<> těsně před> skupin. V \<uzlu Menu> přidejte \<uzel menu> následujícím způsobem:

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

    Hodnoty `guid` `id` a v nabídce určují sadu příkazů a konkrétní nabídku v sadě příkazů.

    `id` A `guid` hodnoty nadřazené pozice nabídky v části panelu nabídek Sady Visual Studio, který obsahuje nabídky nástroje a doplňky.

    Hodnota `CommandName` řetězce určuje, že text by se měl zobrazit v položce nabídky.

3. V \<části Skupiny> \<najděte> \<skupiny a změňte prvek Parent> tak, aby přešel na nabídku, kterou jsme právě přidali:

   ```csharp
   <Groups>
         <Group guid="guidTestCommandPackageCmdSet" id="MyMenuGroup" priority="0x0600">
           <Parent guid="guidTestCommandPackageCmdSet" id="TopLevelMenu"/>
         </Group>
       </Groups>
   ```

    Tím se skupina součástí nové nabídky.

::: moniker-end

::: moniker range=">=vs-2019"

1. V **Průzkumníku řešení**otevřete *soubor TopLevelMenuPackage.vsct*.

    Na konci souboru je \<symboly> uzel, \<který obsahuje několik GuidSymbol> uzly. V uzlu s názvem guidTopLevelMenuPackageCmdSet přidejte nový symbol takto:

   ```xml
   <IDSymbol name="TopLevelMenu" value="0x1021"/>
   ```

2. Vytvořte \<prázdný uzel> nabídek \<v uzlu příkazy \<> těsně před> skupin. V \<uzlu Menu> přidejte \<uzel menu> následujícím způsobem:

   ```xml
   <Menus>
         <Menu guid="guidTopLevelMenuPackageCmdSet" id="TopLevelMenu" priority="0x700" type="Menu">
           <Parent guid="guidSHLMainMenu"
                   id="IDG_VS_MM_TOOLSADDINS" />
           <Strings>
             <ButtonText>TestMenu</ButtonText>
             <CommandName>TestMenu</CommandName>
           </Strings>
       </Menu>
   </Menus>
   ```

    Hodnoty `guid` `id` a v nabídce určují sadu příkazů a konkrétní nabídku v sadě příkazů.

    `id` A `guid` hodnoty nadřazené pozice nabídky v části panelu nabídek Sady Visual Studio, který obsahuje nabídky nástroje a doplňky.

    Hodnota `CommandName` řetězce určuje, že text by se měl zobrazit v položce nabídky.

3. V \<části Skupiny> \<najděte> \<skupiny a změňte prvek Parent> tak, aby přešel na nabídku, kterou jsme právě přidali:

   ```csharp
   <Groups>
         <Group guid="guidTopLevelMenuPackageCmdSet" id="MyMenuGroup" priority="0x0600">
           <Parent guid="guidTopLevelMenuPackageCmdSet" id="TopLevelMenu"/>
         </Group>
       </Groups>
   ```

    Tím se skupina součástí nové nabídky.

::: moniker-end

4. Najděte `Buttons` sekci. Všimněte [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] si, že šablona Package vygenerovala `Button` prvek, který má nadřazenou sadu . `MyMenuGroup` V důsledku toho se tento příkaz zobrazí v nabídce.

## <a name="build-and-test-the-extension"></a>Sestavení a testování rozšíření

1. Sestavení projektu a začít ladění. Měla by se zobrazit instance experimentální instance.

::: moniker range="vs-2017"

2. Řádek nabídek v experimentální instanci by měl obsahovat nabídku **TestMenu.**

::: moniker-end

::: moniker range=">=vs-2019"

2. Nabídka Rozšíření v experimentální **instanci** by měla obsahovat nabídku **TestMenu.**

::: moniker-end

3. V nabídce **TestMenu** klepněte na tlačítko **Vyvolat příkaz k testu**.

     Mělo by se zobrazit okno se zprávou "TestCommand Package Inside TopLevelMenu.TestCommand.MenuItemCallback()".

## <a name="see-also"></a>Viz také

- [Příkazy, nabídky a panely nástrojů](../extensibility/internals/commands-menus-and-toolbars.md)
