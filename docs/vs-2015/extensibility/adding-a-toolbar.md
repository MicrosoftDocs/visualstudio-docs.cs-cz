---
title: Přidání panelu nástrojů | Dokumentace Microsoftu
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
- toolbars [Visual Studio], adding to IDE
- IDE, adding toolbars
ms.assetid: 17302c25-6f59-4e97-8c85-54f95336a07f
caps.latest.revision: 39
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 038b8e8503a89dd0ec565d3d1b5acf20e6437600
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51787949"
---
# <a name="adding-a-toolbar"></a>Přidání panelu nástrojů
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tento návod ukazuje, jak přidat panel nástrojů Visual Studio IDE.  
  
 Panel nástrojů je vodorovný nebo svislý pruh, který obsahuje tlačítka, které jsou vázány na příkazy. V závislosti na jeho implementace panelu nástrojů v rozhraní IDE může být přemístí, ukotven na žádné straně hlavního okna IDE nebo se zůstat před ostatní okna.  
  
 Kromě toho můžete uživatelům přidání příkazů pro panel nástrojů nebo je z něj odebrat pomocí **vlastní** dialogové okno. Panely nástrojů v balíčcích VSPackage jsou obvykle uživatelsky přizpůsobitelnými. Zpracovává všechna přizpůsobení integrovaného vývojového prostředí a sady VSPackage odpovídá na příkazy. Sady VSPackage nemusí vědět, kde je příkaz fyzicky umístěn.  
  
 Další informace o nabídkách najdete v tématu [příkazy, nabídky a panely nástrojů](../extensibility/internals/commands-menus-and-toolbars.md).  
  
## <a name="prerequisites"></a>Požadavky  
 Spouští se v sadě Visual Studio 2015, nenainstalujete sadu Visual Studio SDK ze služby Stažení softwaru. Je zahrnut jako volitelná funkce v instalačním programu sady Visual Studio. VS SDK můžete také nainstalovat později. Další informace najdete v tématu [instalace sady Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-an-extension-with-a-toolbar"></a>Vytváření rozšíření pomocí panelu nástrojů  
 Vytvořte projekt VSIX s názvem `IDEToolbar`. Přidat šablonu položky příkaz nabídky s názvem **ToolbarTestCommand**. Informace o tom, jak to provést, najdete v tématu [vytváření rozšíření pomocí příkazu nabídky](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
## <a name="creating-a-toolbar-for-the-ide"></a>Vytváření panelů nástrojů pro prostředí IDE  
  
1.  V ToolbarTestCommandPackage.vsct vyhledejte v části symboly. V guidsymbol – element s názvem guidToolbarTestCommandPackageCmdSet přidejte deklarace pro panel nástrojů a panelu nástrojů skupiny, následujícím způsobem.  
  
    ```xml  
    <IDSymbol name="Toolbar" value="0x1000" />  
    <IDSymbol name="ToolbarGroup" value="0x1050" />  
  
    ```  
  
2.  V horní části příkazy vytvořte oddíl nabídky. Přidejte prvek nabídky do části nabídky k definování panelu nástrojů.  
  
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
  
     Panely nástrojů nemůže být vnořena jako dílčích nabídek. Proto nemáte přiřazení nadřazené skupiny. Navíc není nutné nastavit prioritu, protože uživatel může přesunout panely nástrojů. Obvykle je počáteční umístění panelu nástrojů definované prostřednictvím kódu programu, ale jsou zachované následné změny uživatelem.  
  
3.  V [skupiny](../extensibility/groups-element.md) části po položce existující skupiny, definujte [skupiny](../extensibility/group-element.md) element tak, aby obsahovala příkazů pro panel nástrojů.  
  
    ```xml  
    <Group guid="guidToolbarTestCommandPackageCmdSet" id="ToolbarGroup"  
          priority="0x0000">  
      <Parent guid="guidToolbarTestCommandPackageCmdSet" id="Toolbar"/>  
    </Group>  
    ```  
  
4.  Aby se tlačítko zobrazilo na panelu nástrojů. V části tlačítka nahraďte nadřazený blok tlačítka na panelu nástrojů. Výsledného bloku tlačítko by měl vypadat nějak takto:  
  
    ```xml  
    <Button guid="guidToolbarTestCommandPackageCmdSet" id="ToolbarTestCommandId" priority="0x0100" type="Button">  
        <Parent guid= "guidToolbarTestCommandPackageCmdSet" id="ToolbarGroup" />  
                <Icon guid="guidImages" id="bmpPic1" />  
        <Strings>  
            <ButtonText>Invoke ToolbarTestCommand</ButtonText>  
        </Strings>  
    </Button>  
    ```  
  
     Ve výchozím nastavení Pokud panel nástrojů nemá žádné příkazy se nezobrazí.  
  
5.  Sestavte projekt a spusťte ladění. Experimentální instanci aplikace by se zobrazit.  
  
6.  Klikněte pravým tlačítkem na řádku nabídek sady Visual Studio zobrazíte seznam panely nástrojů. Vyberte **testování nástrojů**.  
  
7.  Teď byste měli vidět panelu nástrojů jako ikony napravo od najít v souborech ikonu. Když kliknete na ikonu, zobrazí se okno se zprávou, že **ToolbarTestCommandPackage. Uvnitř IDEToolbar.ToolbarTestCommand.MenuItemCallback()**.  
  
## <a name="see-also"></a>Viz také  
 [Příkazy, nabídky a panely nástrojů](../extensibility/internals/commands-menus-and-toolbars.md)

