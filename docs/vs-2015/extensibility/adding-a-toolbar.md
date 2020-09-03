---
title: Přidání panelu nástrojů | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- toolbars [Visual Studio], adding to IDE
- IDE, adding toolbars
ms.assetid: 17302c25-6f59-4e97-8c85-54f95336a07f
caps.latest.revision: 39
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: de74961715a82dde4e184509094d05145ad0f79c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68184859"
---
# <a name="adding-a-toolbar"></a>Přidání panelu nástrojů
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tento návod ukazuje, jak přidat panel nástrojů do integrovaného vývojového prostředí sady Visual Studio.  
  
 Panel nástrojů je vodorovný nebo svislý pruh, který obsahuje tlačítka, která jsou vázaná na příkazy. V závislosti na jeho implementaci lze přemístit panel nástrojů v INTEGROVANÉm vývojovém prostředí (IDE), které je ukotveno na kterékoli straně hlavního okna IDE, nebo může zůstat před ostatními okny.  
  
 Kromě toho mohou uživatelé přidat příkazy na panel nástrojů nebo je z něj odebrat pomocí dialogového okna **přizpůsobit** . Panely nástrojů v VSPackage jsou obvykle uživatelsky přizpůsobitelné. Rozhraní IDE zpracuje všechna přizpůsobení a rozhraní VSPackage odpoví na příkazy. VSPackage nemusí znát, kde je fyzicky umístěný příkaz.  
  
 Další informace o nabídkách naleznete v tématech [příkazy, nabídky a panely nástrojů](../extensibility/internals/commands-menus-and-toolbars.md).  
  
## <a name="prerequisites"></a>Předpoklady  
 Od sady Visual Studio 2015 nenainstalujete sadu Visual Studio SDK z webu Stažení softwaru. V instalačním programu sady Visual Studio je zahrnutý jako volitelná funkce. Sadu VS SDK můžete také nainstalovat později. Další informace najdete v tématu [instalace sady Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-an-extension-with-a-toolbar"></a>Vytvoření rozšíření pomocí panelu nástrojů  
 Vytvořte projekt VSIX s názvem `IDEToolbar` . Přidejte šablonu položky příkazu nabídky s názvem **ToolbarTestCommand**. Informace o tom, jak to provést, najdete v tématu [Vytvoření rozšíření pomocí příkazu nabídky](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
## <a name="creating-a-toolbar-for-the-ide"></a>Vytvoření panelu nástrojů pro prostředí IDE  
  
1. V ToolbarTestCommandPackage. vsct vyhledejte oddíl symboly. V elementu GuidSymbol s názvem guidToolbarTestCommandPackageCmdSet přidejte deklarace pro panel nástrojů a skupinu panelu nástrojů následujícím způsobem.  
  
    ```xml  
    <IDSymbol name="Toolbar" value="0x1000" />  
    <IDSymbol name="ToolbarGroup" value="0x1050" />  
  
    ```  
  
2. V horní části oddílu příkazy vytvořte oddíl Menus. Přidáním prvku nabídky do oddílu nabídky definujte panel nástrojů.  
  
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
  
     Panely nástrojů nelze vnořovat jako podnabídky. Proto nemusíte přiřazovat nadřazenou skupinu. Také není nutné nastavit prioritu, protože uživatel může přesunout panely nástrojů. Obvykle je prvotní umístění panelu nástrojů definováno programově, ale následné změny uživatele jsou trvalé.  
  
3. V části [skupiny](../extensibility/groups-element.md) po existující položce skupiny definujte prvek [skupiny](../extensibility/group-element.md) , který bude obsahovat příkazy pro panel nástrojů.  
  
    ```xml  
    <Group guid="guidToolbarTestCommandPackageCmdSet" id="ToolbarGroup"  
          priority="0x0000">  
      <Parent guid="guidToolbarTestCommandPackageCmdSet" id="Toolbar"/>  
    </Group>  
    ```  
  
4. Tlačítko se zobrazí na panelu nástrojů. V části tlačítka nahraďte nadřazený blok v tlačítku na panelu nástrojů. Výsledný blok tlačítka by měl vypadat takto:  
  
    ```xml  
    <Button guid="guidToolbarTestCommandPackageCmdSet" id="ToolbarTestCommandId" priority="0x0100" type="Button">  
        <Parent guid= "guidToolbarTestCommandPackageCmdSet" id="ToolbarGroup" />  
                <Icon guid="guidImages" id="bmpPic1" />  
        <Strings>  
            <ButtonText>Invoke ToolbarTestCommand</ButtonText>  
        </Strings>  
    </Button>  
    ```  
  
     Ve výchozím nastavení platí, že pokud panel nástrojů neobsahuje žádné příkazy, nezobrazí se.  
  
5. Sestavte projekt a spusťte ladění. Měla by se zobrazit experimentální instance.  
  
6. Seznam panelů nástrojů získáte tak, že kliknete pravým tlačítkem na panel nabídek sady Visual Studio. Vyberte **panel nástrojů test**.  
  
7. Panel nástrojů by se teď měl zobrazit jako ikona napravo od ikony najít v souborech. Po kliknutí na ikonu by se měla zobrazit okno se zprávou, která říká **ToolbarTestCommandPackage. Uvnitř IDEToolbar. ToolbarTestCommand. MenuItemCallback ()**.  
  
## <a name="see-also"></a>Viz také  
 [Příkazy, nabídky a panely nástrojů](../extensibility/internals/commands-menus-and-toolbars.md)
