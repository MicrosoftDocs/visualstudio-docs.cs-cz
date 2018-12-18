---
title: Přidání nabídky do nabídek | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- menus, creating top level
- top-level menus
ms.assetid: 58fc1a31-2aeb-441c-8e48-c7d5cbcfe501
caps.latest.revision: 52
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 440bd2c8c7e1505b8d729274a06440d596690773
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53065886"
---
# <a name="adding-a-menu-to-the-visual-studio-menu-bar"></a>Přidání nabídky do řádku nabídek v sadě Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tento návod ukazuje, jak přidat do nabídky na řádku nabídek sady Visual Studio integrované vývojové prostředí (IDE). Panel nabídek integrovaného vývojového prostředí obsahuje kategorií nabídek, jako **souboru**, **upravit**, **zobrazení**, **okno**, a **pomáhají** .

 Před přidáním nové nabídky na řádku nabídek sady Visual Studio, zvažte, jestli vaše příkazy by měl být umístěn v rámci existující nabídky. Další informace o umístění příkazu najdete v tématu [nabídek a příkazů pro sadu Visual Studio](../extensibility/ux-guidelines/menus-and-commands-for-visual-studio.md).

 Nabídky jsou deklarovány v souboru .vsct projektu. Další informace o nabídkách a soubory .vsct najdete v tématu [příkazy, nabídky a panely nástrojů](../extensibility/internals/commands-menus-and-toolbars.md).

 V tomto návodu, můžete vytvořit nabídky s názvem **TestMenu** , která obsahuje jeden příkaz.

## <a name="prerequisites"></a>Požadavky
 Spouští se v sadě Visual Studio 2015, nenainstalujete sadu Visual Studio SDK ze služby Stažení softwaru. Je zahrnut jako volitelná funkce v instalačním programu sady Visual Studio. VS SDK můžete také nainstalovat později. Další informace najdete v tématu [instalace sady Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="creating-a-vsix-project-that-has-a-custom-command-item-template"></a>Vytvoření projektu VSIX, který obsahuje šablonu položky příkazu vlastní

1.  Vytvořte projekt VSIX s názvem `TopLevelMenu`. Můžete najít šablonu projektu VSIX v **nový projekt** dialogového okna v části **Visual C#** / **rozšiřitelnost**.  Další informace najdete v tématu [vytváření rozšíření pomocí příkazu nabídky](../extensibility/creating-an-extension-with-a-menu-command.md).

2.  Po otevření projektu přidat vlastní příkaz šablonu položky s názvem **TestCommand**. V **Průzkumníka řešení**, klikněte pravým tlačítkem na uzel projektu a vyberte **Add / nová položka**. V **přidat novou položku** dialogové okno, přejděte na **Visual C# / rozšíření** a vyberte **vlastního příkazu**. V **název** pole v dolní části okna, změňte název souboru příkazu **TestCommand.cs**.

## <a name="creating-a-menu-on-the-ide-menu-bar"></a>Vytvoření nabídky na řádku nabídek integrovaného vývojového prostředí

#### <a name="to-create-a-menu"></a>Vytvoření nabídky

1.  V **Průzkumníka řešení**, otevřete TestCommandPackage.vsct.

     Na konci souboru, je \<symboly > uzel, který obsahuje několik \<guidsymbol – > uzlů. V uzlech s názvem guidTestCommandPackageCmdSet přidejte nový symbol následujícím způsobem:

    ```xml
    <IDSymbol name="TopLevelMenu" value="0x1021"/>
    ```

2.  Vytvořte prázdnou \<nabídky > uzlu \<příkazy > uzlu, těsně před \<skupiny >. V \<nabídky > uzel, přidejte \<nabídky > uzlu, následujícím způsobem:

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

     `guid` a `id` hodnoty nabídky určují sadu příkazů a konkrétní nabídky v sadu příkazů.

     `guid` a `id` nadřazených hodnot umístění v nabídce v části řádku nabídek sady Visual Studio, který obsahuje nástroje a Add-ins nabídky.

     Hodnota `CommandName` řetězec Určuje, že by se zobrazit text v položce nabídky.

3.  V \<skupiny > vyhledejte \<skupiny > a změnit \<nadřazené > element tak, aby odkazoval do nabídky jsme právě přidali:

    ```csharp
    <Groups>
          <Group guid="guidTestCommandPackageCmdSet" id="MyMenuGroup" priority="0x0600">
            <Parent guid="guidTestCommandPackageCmdSet" id="TopLevelMenu"/>
          </Group>
        </Groups>
    ```

     Díky tomu je součástí skupiny v nové nabídce.

4.  Najít `Buttons` oddílu. Všimněte si, že [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] generoval balíček šablony `Button` element, který má nadřazený nastavena na `MyMenuGroup`. Tento příkaz v důsledku toho se zobrazí v nabídce.

## <a name="building-and-testing-the-extension"></a>Vytváření a testování rozšíření

1.  Sestavte projekt a spusťte ladění. Instancí experimentální instanci aplikace by se zobrazit.

2.  By měl obsahovat nabídek v experimentální instanci **TestMenu** nabídky.

3.  Na **TestMenu** nabídky, klikněte na tlačítko **vyvolat příkaz Test**.

     Okno se zprávou by měla objevit a zobrazit zprávu "TestCommand balíček uvnitř TopLevelMenu.TestCommand.MenuItemCallback()". To znamená, že nový příkaz funguje.

## <a name="see-also"></a>Viz také
 [Příkazy, nabídky a panely nástrojů](../extensibility/internals/commands-menus-and-toolbars.md)
