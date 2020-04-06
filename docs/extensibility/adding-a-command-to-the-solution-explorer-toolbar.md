---
title: Přidání příkazu na panel nástrojů Průzkumníka řešení | Dokumenty společnosti Microsoft
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
ms.openlocfilehash: 44a14d87fbb5754d7af35d3add9e438351877a49
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740334"
---
# <a name="add-a-command-to-the-solution-explorer-toolbar"></a>Přidání příkazu na panel nástrojů Průzkumníka řešení
Tento návod ukazuje, jak přidat tlačítko na panel nástrojů **Průzkumníka řešení.**

 Libovolný příkaz na panelu nástrojů nebo nabídce se nazývá tlačítko v sadě Visual Studio. Po klepnutí na tlačítko je spuštěn kód v obslužné rutině příkazu. Související příkazy jsou obvykle seskupeny do jedné skupiny. Nabídky nebo panely nástrojů fungují jako kontejnery pro skupiny. Priorita určuje pořadí, ve kterém se jednotlivé příkazy ve skupině zobrazují v nabídce nebo na panelu nástrojů. Ovládáním jeho viditelnosti můžete zabránit zobrazení tlačítka na panelu nástrojů nebo v nabídce. Příkaz, který je `<VisibilityConstraints>` uveden v části souboru *.vsct,* se zobrazí pouze v přidruženém kontextu. Viditelnost nelze použít pro skupiny.

 Další informace o nabídkách, příkazech panelu nástrojů a souborech *.vsct* naleznete v [tématu Příkazy, nabídky a panely nástrojů](../extensibility/internals/commands-menus-and-toolbars.md).

> [!NOTE]
> Místo souborů konfigurace tabulky příkazů *(CTC)* použijte soubory XML Command Table (*.vsct*) k definování způsobu zobrazení nabídek a příkazů v balíčcích VSPackages. Další informace naleznete v [tématu Visual Studio Command Table (. Vsct) .](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

## <a name="prerequisites"></a>Požadavky
 Počínaje Visual Studio 2015 neinstalujete sady Visual Studio SDK ze služby stažení. Je součástí volitelné funkce v nastavení sady Visual Studio. VS SDK můžete také nainstalovat později. Další informace naleznete [v tématu Instalace sady Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-an-extension-with-a-menu-command"></a>Vytvoření rozšíření pomocí příkazu nabídky
 Vytvořte projekt VSIX s názvem `SolutionToolbar`. Přidejte šablonu položky příkazu nabídky s názvem **ToolbarButton**. Informace o tom, jak to provést, naleznete [v tématu Vytvoření rozšíření pomocí příkazu nabídky](../extensibility/creating-an-extension-with-a-menu-command.md).

## <a name="add-a-button-to-the-solution-explorer-toolbar"></a>Přidání tlačítka na panel nástrojů Průzkumníka řešení
 Tato část návodu ukazuje, jak přidat tlačítko na panel nástrojů **Průzkumníka řešení.** Po klepnutí na tlačítko je spuštěn kód v metodě zpětného volání.

1. V souboru *ToolbarButtonPackage.vsct* přejděte do oddílu. `<Symbols>` Uzel `<GuidSymbol>` obsahuje skupinu nabídek a příkaz, který byl vygenerován šablonou balíčku. Přidejte `<IDSymbol>` prvek do tohoto uzlu deklarovat skupinu, která bude držet váš příkaz.

    ```xml
    <IDSymbol name="SolutionToolbarGroup" value="0x0190"/>
    ```

2. V `<Groups>` části po existující položce skupiny definujte novou skupinu, kterou jste deklarovali v předchozím kroku.

    ```xml
    <Group guid="guidToolbarButtonPackageCmdSet"
           id="SolutionToolbarGroup" priority="0xF000">
            <Parent guid="guidSHLMainMenu" id="IDM_VS_TOOL_PROJWIN"/>
          </Group>
    ```

     Nastavení nadřazené dvojice `guidSHLMainMenu` GUID:ID a `IDM_VS_TOOL_PROJWIN` umístí tuto skupinu na panel nástrojů **Průzkumníka řešení** a nastavení hodnoty s vysokou prioritou ji umístí za ostatní skupiny příkazů.

3. V `<Buttons>` části změňte nadřazené `<Button>` ID generované položky tak, aby odráželo skupinu, kterou jste definovali v předchozím kroku. Změněný `<Button>` prvek by měl vypadat takto:

    ```xml
    <Button guid="guidToolbarButtonPackageCmdSet" id="ToolbarButtonId" priority="0x0100" type="Button">
        <Parent guid="guidToolbarButtonPackageCmdSet" id="SolutionToolbarGroup" />
        <Icon guid="guidImages" id="bmpPicStrikethrough" />
        <Strings>
            <ButtonText>Invoke ToolbarButton</ButtonText>
        </Strings>
    </Button>
    ```

4. Sestavení projektu a začít ladění. Zobrazí se experimentální instance.

     Panel nástrojů **Průzkumník řešení** by měl zobrazit nové příkazové tlačítko vpravo od existujících tlačítek. Ikona tlačítka je přeškrtnutá.

5. Klikněte na nové tlačítko.

     Dialogové okno se zprávou **ToolbarButtonPackage Inside SolutionToolbar.ToolbarButton.MenuItemCallback()** by mělo být zobrazeno.

## <a name="control-the-visibility-of-a-button"></a>Ovládání viditelnosti tlačítka
 Tato část návodu ukazuje, jak řídit viditelnost tlačítka na panelu nástrojů. Nastavením kontextu na jeden nebo `<VisibilityConstraints>` více projektů v části souboru *SolutionToolbar.vsct* omezíte tlačítko, které se zobrazí pouze v případě, že jsou otevřeny projekty nebo projekty.

### <a name="to-display-a-button-when-one-or-more-projects-are-open"></a>Zobrazení tlačítka při otevření jednoho nebo více projektů

1. V `<Buttons>` části *ToolbarButtonPackage.vsct*přidejte dva příznaky `<Button>` příkazů k `<Strings>` existujícímu prvku mezi značky a. `<Icons>`

   ```xml
   <CommandFlag>DefaultInvisible</CommandFlag>
   <CommandFlag>DynamicVisibility</CommandFlag>
   ```

    Příznaky `DefaultInvisible` `DynamicVisibility` a musí být nastaveny `<VisibilityConstraints>` tak, aby se položky v oddílu mohly projevit.

2. Vytvořte `<VisibilityConstraints>` oddíl, `<VisibilityItem>` který má dvě položky. Nový oddíl vložte hned `</Commands>` za uzavírací značku.

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

    Každá položka viditelnosti představuje podmínku, za které je zobrazeno zadané tlačítko. Chcete-li použít více podmínek, musíte vytvořit více položek pro stejné tlačítko.

3. Sestavení projektu a začít ladění. Zobrazí se experimentální instance.

    Panel nástrojů **Průzkumník řešení** neobsahuje přeškrtnuté tlačítko.

4. Otevřete libovolné řešení, které obsahuje projekt.

    Tlačítko přeškrtnuté se zobrazí na panelu nástrojů vpravo od existujících tlačítek.

5. V nabídce **Soubor** klepněte na tlačítko **Zavřít řešení**. Tlačítko zmizí z panelu nástrojů.

   Viditelnost tlačítka je řízena, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] dokud není načten VSPackage. Po načtení VSPackage viditelnost tlačítka je řízen VSPackage.  Další informace naleznete v [tématu MenuCommands vs. OleMenuCommands](/visualstudio/extensibility/menucommands-vs-olemenucommands?view=vs-2015).

## <a name="see-also"></a>Viz také
- [Příkazy, nabídky a panely nástrojů](../extensibility/internals/commands-menus-and-toolbars.md)
