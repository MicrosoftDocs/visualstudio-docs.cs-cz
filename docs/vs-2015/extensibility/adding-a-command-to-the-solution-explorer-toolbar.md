---
title: Přidání příkazu do panelu nástrojů Průzkumník řešení | Dokumentace Microsoftu
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
- toolbars [Visual Studio], adding buttons
- buttons [Visual Studio], adding to Solution Explorer
- Solution Explorer, adding buttons
ms.assetid: f6411557-2f4b-4e9f-b02e-fce12a6ac7e9
caps.latest.revision: 40
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 52e963a202d75c29c65521729e70e062a579d479
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51753649"
---
# <a name="adding-a-command-to-the-solution-explorer-toolbar"></a>Přidání příkazu do panelu nástrojů Průzkumník řešení
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tento návod ukazuje, jak přidat tlačítko **Průzkumníka řešení** nástrojů.  
  
 Jakýkoli příkaz na panelu nástrojů nebo nabídky se nazývá tlačítko v sadě Visual Studio. Po kliknutí na tlačítko je proveden kód v obslužné rutině příkazu. Související příkazy jsou obvykle seskupené dohromady a vytvoří jednu skupinu. Nabídky a panely nástrojů fungují jako kontejnery pro skupiny. Priorita určuje pořadí, ve kterém jednotlivé příkazy ve skupině zobrazí v nabídce nebo na panelu nástrojů. Tlačítko můžete zabránit zobrazené na panelu nástrojů nebo nabídce řízení viditelnost. Příkaz, který je uveden v `<VisibilityConstraints>` část souboru .vsct se zobrazí pouze v kontextu přidružené. Viditelnost nejde použít u skupiny.  
  
 Další informace o nabídkách, příkazy nástrojů a souborů .vsct najdete v tématu [příkazy, nabídky a panely nástrojů](../extensibility/internals/commands-menus-and-toolbars.md).  
  
> [!NOTE]
>  Určuje způsob zobrazení nabídek a příkazů ve vašich balíčcích VSPackage pomocí souborů tabulky příkazů XML (.vsct) namísto soubory konfigurace (.ctc) tabulky příkazů. Další informace najdete v tématu [tabulky příkazů aplikace Visual Studio (. Vsct) soubory](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).  
  
## <a name="prerequisites"></a>Požadavky  
 Spouští se v sadě Visual Studio 2015, nenainstalujete sadu Visual Studio SDK ze služby Stažení softwaru. Je zahrnut jako volitelná funkce v instalačním programu sady Visual Studio. VS SDK můžete také nainstalovat později. Další informace najdete v tématu [instalace sady Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-an-extension-with-a-menu-command"></a>Vytváření rozšíření pomocí příkazu nabídky  
 Vytvořte projekt VSIX s názvem `SolutionToolbar`. Přidat šablonu položky příkaz nabídky s názvem **ToolbarButton**. Informace o tom, jak to provést, najdete v tématu [vytváření rozšíření pomocí příkazu nabídky](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
## <a name="adding-a-button-to-the-solution-explorer-toolbar"></a>Přidání tlačítka na panelu nástrojů Průzkumník řešení  
 Tato část návodu ukazuje, jak přidat tlačítko **Průzkumníka řešení** nástrojů. Po kliknutí na tlačítko spuštění kódu v metodě zpětného volání.  
  
1.  V souboru ToolbarButtonPackage.vsct, přejděte `<Symbols>` oddílu. `<GuidSymbol>` Uzel obsahuje skupiny nabídek a příkaz, který byl vytvořen balíček šablony. Přidat `<IDSymbol>` – element pro tento uzel, chcete-li deklarovat skupiny, která bude obsahovat svých rukou.  
  
    ```xml  
    <IDSymbol name="SolutionToolbarGroup" value="0x0190"/>  
    ```  
  
2.  V `<Groups>` části po položce existující skupiny definovat novou skupinu, která je deklarována v předchozím kroku.  
  
    ```xml  
    <Group guid="guidToolbarButtonPackageCmdSet"  
           id="SolutionToolbarGroup" priority="0xF000">  
            <Parent guid="guidSHLMainMenu" id="IDM_VS_TOOL_PROJWIN"/>  
          </Group>  
    ```  
  
     Nastavení nadřazeného GUID:ID pár `guidSHLMainMenu` a `IDM_VS_TOOL_PROJWIN` umístí na tuto skupinu **Průzkumníku řešení** nástrojů a nastavení hodnoty s vysokou prioritou umístí po další příkaz skupiny.  
  
3.  V `<Buttons>` oddíl, změňte ID nadřazeného generované `<Button>` položky tak, aby odrážely skupině, která jste definovali v předchozím kroku. Upravené `<Button>` prvek by měl vypadat takto:  
  
    ```xml  
    <Button guid="guidToolbarButtonPackageCmdSet" id="ToolbarButtonId" priority="0x0100" type="Button">  
        <Parent guid="guidToolbarButtonPackageCmdSet" id="SolutionToolbarGroup" />  
        <Icon guid="guidImages" id="bmpPicStrikethrough" />  
        <Strings>  
            <ButtonText>Invoke ToolbarButton</ButtonText>  
        </Strings>  
    </Button>  
    ```  
  
4.  Sestavte projekt a spusťte ladění. Zobrazí se experimentální instance.  
  
     **Průzkumníka řešení** nástrojů zobrazeno tlačítko Nový příkaz napravo od existující tlačítka. Ikona tlačítka je přeškrtnutím.  
  
5.  Klikněte na tlačítko Nový.  
  
     Dialogové okno, které se má zpráva **ToolbarButtonPackage uvnitř SolutionToolbar.ToolbarButton.MenuItemCallback()** by se mělo zobrazit.  
  
## <a name="controlling-the-visibility-of-a-button"></a>Řízení viditelnosti tlačítka  
 Tato část návodu ukazuje, jak řídit, zda tlačítko na panelu nástrojů. Tím, že nastavíte na jeden nebo více projektů v kontextu `<VisibilityConstraints>` části souboru SolutionToolbar.vsct omezit tlačítko se zobrazí, pouze pokud projekt nebo projekty jsou otevřené.  
  
#### <a name="to-display-a-button-when-one-or-more-projects-are-open"></a>K zobrazení tlačítka, když jsou otevřené jeden nebo více projektů  
  
1. V `<Buttons>` části ToolbarButtonPackage.vsct, přidejte dvě příznaků příkazů ke stávající `<Button>` elementu, mezi `<Strings>` a `<Icons>` značky.  
  
   ```xml  
   <CommandFlag>DefaultInvisible</CommandFlag>  
   <CommandFlag>DynamicVisibility</CommandFlag>  
   ```  
  
    `DefaultInvisible` a `DynamicVisibility` příznaky musí být nastaven tak této položky `<VisibilityConstraints>` oddíl se projeví.  
  
2. Vytvoření `<VisibilityConstraints>` oddíl, který má dva `<VisibilityItem>` položky. Vložit nový oddíl bezprostředně po zavření `</Commands>` značky.  
  
   ```xml  
   <VisibilityConstraints>  
       <VisibilityItem guid="guidToolbarButtonPackageCmdSet"  
             id="ToolbarButtonId"  
             context="UICONTEXT_SolutionHasSingleProject" />  
       <VisibilityItem guid="guidToolbarButtonPackageCmdSet"  
             id="ToolbarButtonId"  
             context="UICONTEXT_SolutionHasMultipleProjects" />  
   </VisibilityConstraints>  
   ```  
  
    Každá položka viditelnost představuje podmínku, pod kterým se zobrazí určeného tlačítka. Chcete-li použít více podmínek, musíte vytvořit několik záznamů pro stejný tlačítko.  
  
3. Sestavte projekt a spusťte ladění. Zobrazí se experimentální instance.  
  
    **Průzkumníka řešení** panelu nástrojů tlačítko přeškrtnout neobsahuje.  
  
4. Otevřete jakéhokoli řešení, které obsahuje projekt.  
  
    Na panelu nástrojů vpravo od existující tlačítka se zobrazí strikethrough tlačítko.  
  
5. Na **souboru** nabídky, klikněte na tlačítko **zavřít řešení**. Tlačítko dané zařízení zmizí z panelu nástrojů.  
  
   Řídí, zda tlačítko [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] dokud načtení sady VSPackage. Po načtení sady VSPackage, zda tlačítko je řízena sady VSPackage.  Další informace najdete v tématu [MenuCommands Vs. OleMenuCommands](../misc/menucommands-vs-olemenucommands.md).  
  
## <a name="see-also"></a>Viz také  
 [Příkazy, nabídky a panely nástrojů](../extensibility/internals/commands-menus-and-toolbars.md)

