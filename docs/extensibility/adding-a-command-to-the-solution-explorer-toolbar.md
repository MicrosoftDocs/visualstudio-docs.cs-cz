---
title: Přidání příkazu na panel Průzkumník řešení panelu | Microsoft Docs
description: Zjistěte, jak přidat tlačítko, které spustí příkaz, na Průzkumník řešení panelu nástrojů v Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- toolbars [Visual Studio], adding buttons
- buttons [Visual Studio], adding to Solution Explorer
- Solution Explorer, adding buttons
ms.assetid: f6411557-2f4b-4e9f-b02e-fce12a6ac7e9
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 0aa75bd1a229be147e3462845a61266a650e072e
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2021
ms.locfileid: "112900236"
---
# <a name="add-a-command-to-the-solution-explorer-toolbar"></a>Přidání příkazu na panel Průzkumník řešení panelu nástrojů
Tento názorný postup ukazuje, jak přidat tlačítko na **Průzkumník řešení** panelu nástrojů.

 Jakýkoli příkaz na panelu nástrojů nebo nabídce se nazývá tlačítko v Visual Studio. Po kliknutí na tlačítko se spustí kód v obslužné rutině příkazu. Související příkazy se obvykle seskupují dohromady a tvoří jednu skupinu. Nabídky nebo panely nástrojů se chová jako kontejnery pro skupiny. Priorita určuje pořadí, ve kterém se jednotlivé příkazy ve skupině zobrazí v nabídce nebo na panelu nástrojů. Zobrazení tlačítka na panelu nástrojů nebo v nabídce můžete zabránit tím, že řídíte jeho viditelnost. Příkaz uvedený v oddílu `<VisibilityConstraints>` souboru *.vsct* se zobrazí pouze v přidruženém kontextu. Viditelnost nelze použít u skupin.

 Další informace o nabídkách, příkazech panelu nástrojů a *souborech .vsct* najdete v tématu [Příkazy, nabídky](../extensibility/internals/commands-menus-and-toolbars.md)a panely nástrojů .

> [!NOTE]
> Pomocí souborů tabulky příkazů XML (*.vsct*) místo konfiguračních souborů tabulky příkazů (*.ctc*) definujte, jak se nabídky a příkazy zobrazují v balíčky VSPackage. Další informace najdete v Visual Studio [příkazové tabulky (. Vsct) .](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

## <a name="prerequisites"></a>Požadavky
 Od Visual Studio 2015 neinstalujete sadu Visual Studio SDK ze služby Download Center. Je zahrnutá jako volitelná funkce v Visual Studio nastavení. Sadu VS SDK můžete nainstalovat později. Další informace najdete v tématu [Instalace sady Visual Studio SDK.](../extensibility/installing-the-visual-studio-sdk.md)

## <a name="create-an-extension-with-a-menu-command"></a>Vytvoření rozšíření pomocí příkazu nabídky
 Vytvořte projekt VSIX s názvem `SolutionToolbar` . Přidejte šablonu položky příkazu nabídky s názvem **ToolbarButton**. Informace o tom, jak to provést, najdete v [tématu Vytvoření rozšíření pomocí příkazu nabídky](../extensibility/creating-an-extension-with-a-menu-command.md).

## <a name="add-a-button-to-the-solution-explorer-toolbar"></a>Přidání tlačítka na panel Průzkumník řešení panelu nástrojů
 Tato část návodu ukazuje, jak přidat tlačítko na panel **Průzkumník řešení** panelu nástrojů. Po kliknutí na tlačítko se spustí kód v metodě zpětného volání.

1. V *souboru ToolbarButtonPackage.vsct* přejděte do  `<Symbols>` části . Uzel `<GuidSymbol>`  obsahuje skupinu nabídek a příkaz vygenerovaný šablonou balíčku. Přidejte `<IDSymbol>` do tohoto uzlu element , který deklaruje skupinu, která bude obsahovat váš příkaz.

    ```xml
    <IDSymbol name="SolutionToolbarGroup" value="0x0190"/>
    ```

2. V oddílu za existující položku skupiny definujte novou skupinu, kterou `<Groups>` jste deklaroval v předchozím kroku.

    ```xml
    <Group guid="guidToolbarButtonPackageCmdSet"
           id="SolutionToolbarGroup" priority="0xF000">
            <Parent guid="guidSHLMainMenu" id="IDM_VS_TOOL_PROJWIN"/>
          </Group>
    ```

     Nastavením nadřazeného páru GUID:ID na a jeho seskupením na panelu nástrojů Průzkumník řešení se nastaví hodnota s vysokou prioritou, která ji zasáčí za `guidSHLMainMenu` `IDM_VS_TOOL_PROJWIN` ostatní skupiny příkazů. 

3. V části změňte nadřazené ID vygenerované položky tak, aby odráželo skupinu, kterou jste definovali `<Buttons>` `<Button>` v předchozím kroku. Upravený `<Button>` element by měl vypadat takhle:

    ```xml
    <Button guid="guidToolbarButtonPackageCmdSet" id="ToolbarButtonId" priority="0x0100" type="Button">
        <Parent guid="guidToolbarButtonPackageCmdSet" id="SolutionToolbarGroup" />
        <Icon guid="guidImages" id="bmpPicStrikethrough" />
        <Strings>
            <ButtonText>Invoke ToolbarButton</ButtonText>
        </Strings>
    </Button>
    ```

4. Sestavte projekt a spusťte ladění. Zobrazí se experimentální instance.

     Na **Průzkumník řešení** panelu nástrojů by se mělo zobrazit nové příkazové tlačítko napravo od existujících tlačítek. Ikona tlačítka je přeškrtnutí.

5. Klikněte na nové tlačítko.

     Mělo by se zobrazit dialogové okno se zprávou **ToolbarButtonPackage Inside SolutionToolbar.ToolbarButton.MenuItemCallback().**

## <a name="control-the-visibility-of-a-button"></a>Řízení viditelnosti tlačítka
 Tato část návodu ukazuje, jak řídit viditelnost tlačítka na panelu nástrojů. Nastavením kontextu na jeden nebo více projektů v části souboru `<VisibilityConstraints>` *SolutionToolbar.vsct* omezíte tlačítko tak, aby se objevilo pouze v případě, že je projekt nebo projekty otevřené.

### <a name="to-display-a-button-when-one-or-more-projects-are-open"></a>Zobrazení tlačítka při otevření jednoho nebo více projektů

1. V oddílu `<Buttons>` souboru *ToolbarButtonPackage.vsct* přidejte dva příznaky příkazu do existujícího elementu mezi značky `<Button>` a `<Strings>` `<Icons>` .

   ```xml
   <CommandFlag>DefaultInvisible</CommandFlag>
   <CommandFlag>DynamicVisibility</CommandFlag>
   ```

    Příznaky `DefaultInvisible` `DynamicVisibility` a musí být nastavené tak, aby se položky `<VisibilityConstraints>` v oddílu šly použít.

2. Vytvořte `<VisibilityConstraints>` oddíl, který obsahuje dvě `<VisibilityItem>` položky. Dejte nový oddíl hned za uzavírací `</Commands>` značku.

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

    Každá položka viditelnosti představuje podmínku, pod kterou se zadané tlačítko zobrazuje. Pokud chcete použít více podmínek, musíte pro stejné tlačítko vytvořit více položek.

3. Sestavte projekt a spusťte ladění. Zobrazí se experimentální instance.

    Panel **Průzkumník řešení** panelu nástrojů neobsahuje tlačítko přeškrtnutí.

4. Otevřete libovolné řešení, které obsahuje projekt.

    Přeškrtnuté tlačítko se zobrazí na panelu nástrojů napravo od stávajících tlačítek.

5. V nabídce **Soubor** klikněte na **Zavřít řešení.** Tlačítko z panelu nástrojů zmizí.

   Viditelnost tlačítka se řídí pomocí , [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] dokud se nenačítá balíček VSPackage. Po načtení balíčku VSPackage se viditelnost tlačítka řídí pomocí balíčku VSPackage.  Další informace najdete v tématu [MenuCommands vs. OleMenuCommands.](/previous-versions/visualstudio/visual-studio-2015/misc/menucommands-vs-olemenucommands?preserve-view=true&view=vs-2015)

## <a name="see-also"></a>Viz také
- [Příkazy, nabídky a panely nástrojů](../extensibility/internals/commands-menus-and-toolbars.md)