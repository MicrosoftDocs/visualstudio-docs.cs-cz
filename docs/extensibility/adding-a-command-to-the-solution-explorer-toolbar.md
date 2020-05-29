---
title: Přidání příkazu na panel nástrojů Průzkumník řešení | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- toolbars [Visual Studio], adding buttons
- buttons [Visual Studio], adding to Solution Explorer
- Solution Explorer, adding buttons
ms.assetid: f6411557-2f4b-4e9f-b02e-fce12a6ac7e9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fbb84dd8c8a8240e4fec7791305029304ccce8f7
ms.sourcegitcommit: d20ce855461c240ac5eee0fcfe373f166b4a04a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/29/2020
ms.locfileid: "84183727"
---
# <a name="add-a-command-to-the-solution-explorer-toolbar"></a>Přidání příkazu na panel nástrojů Průzkumník řešení
Tento návod ukazuje, jak přidat tlačítko na panel nástrojů **Průzkumník řešení** .

 Libovolný příkaz na panelu nástrojů nebo v nabídce se nazývá tlačítko v sadě Visual Studio. Po kliknutí na tlačítko je proveden kód v obslužné rutině příkazu. Související příkazy jsou obvykle seskupené dohromady, aby tvořily jednu skupinu. Nabídky nebo panely nástrojů slouží jako kontejnery pro skupiny. Priorita určuje pořadí, ve kterém se jednotlivé příkazy ve skupině zobrazí v nabídce nebo na panelu nástrojů. Můžete zabránit zobrazení tlačítka na panelu nástrojů nebo v nabídce pomocí řízení jeho viditelnosti. Příkaz, který je uveden v `<VisibilityConstraints>` části souboru *. vsct* , se zobrazí pouze v přidruženém kontextu. Viditelnost nelze použít pro skupiny.

 Další informace o nabídkách, příkazech panelů nástrojů a souborech *. vsct* naleznete v tématech [příkazy, nabídky a panely nástrojů](../extensibility/internals/commands-menus-and-toolbars.md).

> [!NOTE]
> Použijte soubory tabulky příkazů XML (*. vsct*) místo souborů konfigurace příkazového řádku (*. ctc*), abyste definovali, jak se nabídky a příkazy zobrazí ve vašich VSPackage. Další informace naleznete v tématu [tabulka příkazů sady Visual Studio (. Vsct) soubory](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).

## <a name="prerequisites"></a>Požadavky
 Od sady Visual Studio 2015 nenainstalujete sadu Visual Studio SDK z webu Stažení softwaru. V instalačním programu sady Visual Studio je zahrnutý jako volitelná funkce. Sadu VS SDK můžete také nainstalovat později. Další informace najdete v tématu [instalace sady Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-an-extension-with-a-menu-command"></a>Vytvoření rozšíření pomocí příkazu nabídky
 Vytvořte projekt VSIX s názvem `SolutionToolbar` . Přidejte šablonu položky příkazu nabídky s názvem **ToolBarButton**. Informace o tom, jak to provést, najdete v tématu [Vytvoření rozšíření pomocí příkazu nabídky](../extensibility/creating-an-extension-with-a-menu-command.md).

## <a name="add-a-button-to-the-solution-explorer-toolbar"></a>Přidání tlačítka na panel nástrojů Průzkumník řešení
 V této části návodu se dozvíte, jak přidat tlačítko na panel nástrojů **Průzkumník řešení** . Při kliknutí na tlačítko je spuštěn kód v metodě zpětného volání.

1. V souboru *ToolbarButtonPackage. vsct* přejít na `<Symbols>` část. `<GuidSymbol>`Uzel obsahuje skupinu nabídek a příkaz, který byl vygenerován šablonou balíčku. Přidejte `<IDSymbol>` element do tohoto uzlu, který deklaruje skupinu, která bude obsahovat váš příkaz.

    ```xml
    <IDSymbol name="SolutionToolbarGroup" value="0x0190"/>
    ```

2. V `<Groups>` části po existující položce skupiny Definujte novou skupinu, kterou jste deklarovali v předchozím kroku.

    ```xml
    <Group guid="guidToolbarButtonPackageCmdSet"
           id="SolutionToolbarGroup" priority="0xF000">
            <Parent guid="guidSHLMainMenu" id="IDM_VS_TOOL_PROJWIN"/>
          </Group>
    ```

     Nastavení nadřazené identifikátory GUID: ID na `guidSHLMainMenu` a `IDM_VS_TOOL_PROJWIN` vloží tuto skupinu na panel nástrojů **Průzkumník řešení** a nastavením hodnoty s vysokou prioritou se vloží za ostatní skupiny příkazů.

3. V `<Buttons>` části změňte nadřazené ID vygenerované `<Button>` položky tak, aby odráželo skupinu, kterou jste definovali v předchozím kroku. Změněný `<Button>` element by měl vypadat takto:

    ```xml
    <Button guid="guidToolbarButtonPackageCmdSet" id="ToolbarButtonId" priority="0x0100" type="Button">
        <Parent guid="guidToolbarButtonPackageCmdSet" id="SolutionToolbarGroup" />
        <Icon guid="guidImages" id="bmpPicStrikethrough" />
        <Strings>
            <ButtonText>Invoke ToolbarButton</ButtonText>
        </Strings>
    </Button>
    ```

4. Sestavte projekt a spusťte ladění. Objeví se experimentální instance.

     Na panelu nástrojů **Průzkumník řešení** by se mělo zobrazit nové příkazové tlačítko napravo od stávajících tlačítek. Ikona tlačítka je přeškrtnuté.

5. Klikněte na tlačítko Nový.

     Mělo by se zobrazit dialogové okno, které obsahuje zprávu **ToolbarButtonPackage uvnitř SolutionToolbar. ToolBarButton. MenuItemCallback ()** .

## <a name="control-the-visibility-of-a-button"></a>Řízení viditelnosti tlačítka
 V této části návodu se dozvíte, jak ovládat viditelnost tlačítka na panelu nástrojů. Nastavením kontextu na jeden nebo více projektů v `<VisibilityConstraints>` části souboru *SolutionToolbar. vsct* omezíte tlačítko tak, aby se zobrazilo pouze v případě, že je projekt nebo projekty otevřeny.

### <a name="to-display-a-button-when-one-or-more-projects-are-open"></a>Chcete-li zobrazit tlačítko při otevření jednoho nebo více projektů

1. V `<Buttons>` části *ToolbarButtonPackage. vsct*přidejte do stávajícího prvku dva příznaky příkazu `<Button>` mezi `<Strings>` `<Icons>` značky a.

   ```xml
   <CommandFlag>DefaultInvisible</CommandFlag>
   <CommandFlag>DynamicVisibility</CommandFlag>
   ```

    `DefaultInvisible` `DynamicVisibility` Musí být nastavené příznaky a, aby položky v `<VisibilityConstraints>` oddílu mohly platit.

2. Vytvořte `<VisibilityConstraints>` oddíl, který má dvě `<VisibilityItem>` položky. Novou část vložte hned za uzavírací `</Commands>` značku.

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

    Každá položka viditelnosti představuje podmínku, pod kterou se zobrazí zadané tlačítko. Chcete-li použít více podmínek, je třeba vytvořit více položek pro stejné tlačítko.

3. Sestavte projekt a spusťte ladění. Objeví se experimentální instance.

    Panel nástrojů **Průzkumník řešení** neobsahuje tlačítko přeškrtnuté.

4. Otevřete jakékoli řešení, které obsahuje projekt.

    Tlačítko přeškrtnuté se zobrazí na panelu nástrojů vpravo od stávajících tlačítek.

5. V nabídce **soubor** klikněte na příkaz **Zavřít řešení**. Tlačítko zmizí z panelu nástrojů.

   Viditelnost tlačítka je ovládána, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] dokud není načteno VSPackage. Po načtení balíčku VSPackage je viditelnost tlačítka ovládána VSPackage.  Další informace najdete v tématu [MenuCommands vs. OleMenuCommands](/visualstudio/misc/menucommands-vs-olemenucommands?view=vs-2015).

## <a name="see-also"></a>Viz také
- [Příkazy, nabídky a panely nástrojů](../extensibility/internals/commands-menus-and-toolbars.md)
