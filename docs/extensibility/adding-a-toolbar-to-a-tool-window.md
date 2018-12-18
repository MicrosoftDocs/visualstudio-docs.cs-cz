---
title: Přidání panelu nástrojů do panelu nástrojů | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- tool windows, adding toolbars
- toolbars [Visual Studio], adding to tool windows
ms.assetid: 172f64b3-87f8-4292-9c1c-65bffa2b0970
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 59e540ec840bc7aadb2465c7f7c71433bf2ddb27
ms.sourcegitcommit: 0e5289414d90a314ca0d560c0c3fe9c88cb2217c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/19/2018
ms.locfileid: "39150760"
---
# <a name="add-a-toolbar-to-a-tool-window"></a>Přidání panelu nástrojů do panelu nástrojů
Tento návod ukazuje, jak přidat panel nástrojů do panelu nástrojů.  
  
 Panel nástrojů je vodorovný nebo svislý pruh, který obsahuje tlačítka, které jsou vázány na příkazy. Délka panelu nástrojů v okně nástroje je vždy stejný jako šířka nebo výška panelu nástrojů v závislosti na tom, kde je panel ukotven.  
  
 Na rozdíl od panelů nástrojů v rozhraní IDE panelu nástrojů v okně nástroje musí být ukotveno a se nedá přesunout ani upravit. Pokud je v kódu umanaged sady VSPackage, lze ukotvit panelu nástrojů na všech hraničních zařízeních.  
  
 Další informace o tom, jak přidat panel nástrojů najdete v tématu [přidání panelu nástrojů](../extensibility/adding-a-toolbar.md).  
  
## <a name="prerequisites"></a>Požadavky  
 Spouští se v sadě Visual Studio 2015, nenainstalujete sadu Visual Studio SDK ze služby Stažení softwaru. Je zahrnut jako volitelná funkce v instalačním programu sady Visual Studio. VS SDK můžete také nainstalovat později. Další informace najdete v tématu [instalace sady Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="create-a-toolbar-for-a-tool-window"></a>Vytvořit panel nástrojů pro panel nástrojů  
  
1.  Vytvořte projekt VSIX s názvem `TWToolbar` , který obsahuje i příkaz nabídky s názvem **TWTestCommand** a panel nástrojů s názvem **TestToolWindow**. Další informace najdete v tématu [vytváření rozšíření pomocí příkazu nabídky](../extensibility/creating-an-extension-with-a-menu-command.md) a [vytváření rozšíření pomocí panelu nástrojů](../extensibility/creating-an-extension-with-a-tool-window.md). Budete muset přidat šablonu položky příkazu před přidáním šablony okno nástroje.  
  
2.  V *TWTestCommandPackage.vsct*, vyhledejte v části symboly. V uzlu guidsymbol – s názvem guidTWTestCommandPackageCmdSet deklarujte panelu nástrojů a panelu nástrojů skupiny, následujícím způsobem.  
  
    ```xml  
    <IDSymbol name="TWToolbar" value="0x1000" />  
    <IDSymbol name="TWToolbarGroup" value="0x1050" />  
    ```  
  
3.  V horní části `Commands` části, vytvořte `Menus` oddílu. Přidat `Menu` element k definování panelu nástrojů.  
  
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
  
     Panely nástrojů nemůže být vnořena jako dílčích nabídek. Proto není nutné přiřadit nadřazenou položku. Navíc není nutné nastavit prioritu, protože uživatel může přesunout panely nástrojů. Obvykle je počáteční umístění panelu nástrojů definované prostřednictvím kódu programu, ale jsou zachované následné změny uživatelem.  
  
4.  V části skupiny definujte skupinu tak, aby obsahovala příkazů pro panel nástrojů.  
  
    ```xml  
  
    <Group guid="guidTWTestCommandPackageCmdSet" id="TWToolbarGroup" priority="0x0000">  
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TWToolbar" />  
    </Group>  
    ```  
  
5.  V části tlačítka změňte nadřazenou existujícího prvku tlačítko na panelu nástrojů skupiny tak, aby se zobrazí panelu nástrojů.  
  
    ```xml  
    <Button guid="guidTWTestCommandPackageCmdSet" id="TWTestCommandId" priority="0x0100" type="Button">  
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TWToolbarGroup" />  
        <Icon guid="guidImages" id="bmpPic1" />  
        <Strings>  
            <ButtonText>Invoke TWTestCommand</ButtonText>  
        </Strings>  
    </Button>  
    ```  
  
     Ve výchozím nastavení Pokud panel nástrojů nemá žádné příkazy se nezobrazí.  
  
     Vzhledem k tomu, že nový panel nástrojů není automaticky přidáno do okna nástroje, musí explicitně přidána panelu nástrojů. Tento postup je popsán v následujícím oddíle.  
  
## <a name="add-the-toolbar-to-the-tool-window"></a>Přidání panelu nástrojů okno nástroje  
  
1.  V *TWTestCommandPackageGuids.cs* přidejte následující řádky.  
  
    ```csharp  
    public const string guidTWTestCommandPackageCmdSet = "00000000-0000-0000-0000-0000";  // get the GUID from the .vsct file  
    public const int TWToolbar = 0x1000;  
    ```  
  
2.  V *TestToolWindow.cs* přidejte následující příkaz using.  
  
    ```csharp  
    using System.ComponentModel.Design;  
    ```  
  
3.  V konstruktoru TestToolWindow přidejte následující řádek.  
  
    ```csharp  
    this.ToolBar = new CommandID(new Guid(TWTestCommandPackageGuids.guidTWTestCommandPackageCmdSet), TWTestCommandPackageGuids.TWToolbar);  
    ```  
  
## <a name="test-the-toolbar-in-the-tool-window"></a>Test panelu nástrojů v panelu nástrojů  
  
1.  Sestavte projekt a spusťte ladění. Experimentální instanci sady Visual Studio by se zobrazit.  
  
2.  Na **zobrazení / ostatní Windows** nabídky, klikněte na tlačítko **testovací třídy ToolWindow** zobrazíte panel nástrojů.  
  
     Měli byste vidět, že panel nástrojů (vypadá jako výchozí ikona) v horní levé části okna nástroje, pod názvem.  
  
3.  Na panelu nástrojů klikněte na ikonu pro zobrazení zprávy **TWTestCommandPackage uvnitř TWToolbar.TWTestCommand.MenuItemCallback()**.  
  
## <a name="see-also"></a>Viz také:  
 [Přidání panelu nástrojů](../extensibility/adding-a-toolbar.md)