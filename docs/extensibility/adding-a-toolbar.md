---
title: Přidání panelu nástrojů | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- toolbars [Visual Studio], adding to IDE
- IDE, adding toolbars
ms.assetid: 17302c25-6f59-4e97-8c85-54f95336a07f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 655cd87fe59cf4f42361cc24a63eb56653caae1a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740218"
---
# <a name="add-a-toolbar"></a>Přidání panelu nástrojů
Tento návod ukazuje, jak přidat panel nástrojů do ide Visual Studio.

 Panel nástrojů je vodorovný nebo svislý pruh, který obsahuje tlačítka, která jsou vázána na příkazy. V závislosti na jeho implementaci panelu nástrojů v ide lze přemístit, ukotvené na libovolné straně hlavního okna ide nebo provést zůstat před ostatními okny.

 Kromě toho mohou uživatelé přidávat příkazy na panel nástrojů nebo je z něj odebírat pomocí dialogového okna **Přizpůsobit.** Panely nástrojů v balíčcích VSPackages jsou obvykle uživatelsky přizpůsobitelné. IDE zpracovává všechny přizpůsobení a VSPackage reaguje na příkazy. VSPackage nemusí vědět, kde je příkaz fyzicky umístěn.

 Další informace o nabídkách naleznete v [tématu Příkazy, nabídky a panely nástrojů](../extensibility/internals/commands-menus-and-toolbars.md).

## <a name="prerequisites"></a>Požadavky
 Počínaje Visual Studio 2015 neinstalujete sady Visual Studio SDK ze služby stažení. Je součástí volitelné funkce v nastavení sady Visual Studio. VS SDK můžete také nainstalovat později. Další informace naleznete [v tématu Instalace sady Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-an-extension-with-a-toolbar"></a>Vytvoření rozšíření pomocí panelu nástrojů
 Vytvořte projekt VSIX s názvem `IDEToolbar`. Přidejte šablonu položky příkazu nabídky s názvem **ToolbarTestCommand**. Informace o tom, jak to provést, naleznete [v tématu Vytvoření rozšíření pomocí příkazu nabídky](../extensibility/creating-an-extension-with-a-menu-command.md).

## <a name="create-a-toolbar-for-the-ide"></a>Vytvoření panelu nástrojů pro ide

1. V *souboru ToolbarTestCommandPackage.vsct*vyhledejte oddíl Symboly. V prvku GuidSymbol s názvem guidToolbarTestPackageCmdSet přidejte deklarace pro panel nástrojů a skupinu panelu nástrojů následujícím způsobem.

    ```xml
    <IDSymbol name="Toolbar" value="0x1000" />
    <IDSymbol name="ToolbarGroup" value="0x1050" />

    ```

2. V horní části oddílu Příkazy vytvořte oddíl Nabídky. Přidejte prvek Nabídky do oddílu Nabídky a definujte panel nástrojů.

    ```xml
    <Menus>
        <Menu guid="guidToolbarTestCommandPackageCmdSet" id="Toolbar"
            type="Toolbar" >
            <CommandFlag>DefaultDocked</CommandFlag>
            <Strings>
                <ButtonText>Test Toolbar</ButtonText>
                <CommandName>Test Toolbar</CommandName>
            </Strings>
          </Menu>
    </Menus>
    ```

     Panely nástrojů nelze vnořit jako podnabídky. Proto není třeba přiřadit nadřazenou skupinu. Také není třeba nastavit prioritu, protože uživatel může přesunout panely nástrojů. Počáteční umístění panelu nástrojů je obvykle definovánprogramově, ale následné změny uživatele jsou trvalé.

3. V části [Skupiny](../extensibility/groups-element.md) po existující položce skupiny definujte prvek [Skupiny](../extensibility/group-element.md) tak, aby obsahoval příkazy pro panel nástrojů.

    ```xml
    <Group guid="guidToolbarTestCommandPackageCmdSet" id="ToolbarGroup"
          priority="0x0000">
      <Parent guid="guidToolbarTestCommandPackageCmdSet" id="Toolbar"/>
    </Group>
    ```

4. Zobrazilo se tlačítko na panelu nástrojů. V části Tlačítka nahraďte nadřazený blok v tlačítku na panel nástrojů. Výsledný blok Button by měl vypadat takto:

    ```xml
    <Button guid="guidToolbarTestCommandPackageCmdSet" id="ToolbarTestCommandId" priority="0x0100" type="Button">
        <Parent guid= "guidToolbarTestCommandPackageCmdSet" id="ToolbarGroup" />
                <Icon guid="guidImages" id="bmpPic1" />
        <Strings>
            <ButtonText>Invoke ToolbarTestCommand</ButtonText>
        </Strings>
    </Button>
    ```

     Ve výchozím nastavení, pokud panel nástrojů nemá žádné příkazy, nezobrazí se.

5. Sestavení projektu a začít ladění. Experimentální instance by se měla zobrazit.

6. Kliknutím pravým tlačítkem myši na panel nabídek sady Visual Studio získáte seznam panelů nástrojů. Vyberte **testovat panel nástrojů**.

7. Nyní byste měli vidět panel nástrojů jako ikonu vpravo od ikony Najít v souborech. Po klepnutí na ikonu, měli byste vidět okno se zprávou, která říká **ToolbarTestCommandPackage. Uvnitř IDEToolbar.ToolbarTestCommand.MenuItemCallback()**.

## <a name="see-also"></a>Viz také
- [Příkazy, nabídky a panely nástrojů](../extensibility/internals/commands-menus-and-toolbars.md)
