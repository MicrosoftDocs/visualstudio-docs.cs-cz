---
title: Vytváření opakovaně použitelných skupin tlačítek | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- button groups, creating in VSPackages
- VSPackages, creating reusable button groups
- buttons, creating reusable groups
ms.assetid: 0c561617-fb86-476d-8bd1-c6e5e7464c65
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ddfba6701890f73ce6438ddc03a338912841a37d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739462"
---
# <a name="create-reusable-groups-of-buttons"></a>Vytvoření opakovaně použitelných skupin tlačítek
Skupina příkazů je kolekce příkazů, které se vždy zobrazují společně v nabídce nebo panelu nástrojů. Libovolnou skupinu příkazů lze znovu použít přiřazením k různým nadřazeným nabídkám v části CommandPlacements souboru *.vsct.*

 Skupiny příkazů obvykle obsahují tlačítka, ale mohou také obsahovat jiné nabídky nebo pole se seznamem.

## <a name="to-create-a-reusable-group-of-buttons"></a>Vytvoření opakovaně použitelné skupiny tlačítek

1. Vytvořte projekt VSIX s názvem `ReusableButtons`. Další informace naleznete [v tématu Vytvoření rozšíření pomocí příkazu nabídky](../extensibility/creating-an-extension-with-a-menu-command.md).

2. Při otevření projektu přidejte vlastní šablonu položky příkazu s názvem **ReusableCommand**. V **Průzkumníku řešení**klepněte pravým tlačítkem myši na uzel projektu a vyberte **přidat** > **novou položku**. V dialogovém okně **Přidat novou položku** přejděte na položku**Rozšiřitelnost** **jazyka Visual C#** > a vyberte **vlastní příkaz**. V poli **Název** v dolní části okna změňte název příkazového souboru na *ReusableCommand.cs*.

3. V souboru *.vsct* přejděte do části Symboly a vyhledejte element GuidSymbol, který obsahuje skupiny a příkazy pro projekt. Měl by být pojmenován guidReusableCommandPackageCmdSet.

4. Přidejte Symbol ID pro každé tlačítko, které přidáte do skupiny, jako v následujícím příkladu.

    ```xml
    <GuidSymbol name="guidReusableCommandPackageCmdSet" value="{7f383b2a-c6b9-4c1d-b4b8-a26dc5b60ca1}">
        <IDSymbol name="MyMenuGroup" value="0x1020" />
        <IDSymbol name="ReusableCommandId" value="0x0100" />
        <IDSymbol name="SecondReusableCommandId" value="0x0200" />
    </GuidSymbol>
    ```

     Ve výchozím nastavení vytvoří šablona položky příkazu skupinu s názvem **MyMenuGroup** a tlačítko, které má zadaný název, spolu s položkou IDSymbol pro každou z nich.

5. V části Skupiny vytvořte prvek Skupiny, který má stejné atributy GUID a ID jako ty, které jsou uvedeny v části Symboly. Můžete také použít existující skupinu nebo položku, která je poskytnuta šablonou příkazu, jako v následujícím příkladu. Tato skupina se zobrazí v nabídce **Nástroje.**

    ```xml
    <Groups>
        <Group guid="guidReusableCommandPackageCmdSet" id="MyMenuGroup" priority="0x0600">
              <Parent guid="guidSHLMainMenu" id="IDM_VS_MENU_TOOLS"/>
        </Group>
    </Groups>
    ```

## <a name="to-create-a-group-of-buttons-for-reuse"></a>Vytvoření skupiny tlačítek pro opakované použití

1. Příkaz nebo nabídku můžete umístit do skupiny buď pomocí skupiny jako nadřazené položky v definici příkazu nebo nabídky, nebo umístěním příkazu nebo nabídky do skupiny pomocí oddílu CommandPlacements.

     V části Tlačítka definujte tlačítko, které má vaši skupinu jako nadřazenou skupinu, nebo použijte tlačítko, které poskytuje šablona balíčku, jak je znázorněno v následujícím příkladu.

    ```xml
    <Button guid="guidReusableCommandPackageCmdSet" id="ReusableCommandId" priority="0x0100" type="Button">
        <Parent guid="guidReusableCommandPackageCmdSet" id="MyMenuGroup" />
        <Icon guid="guidImages" id="bmpPic1" />
        <Strings>
            <ButtonText>Invoke ReusableCommand</ButtonText>
        </Strings>
    </Button>
    ```

2. Pokud se tlačítko musí zobrazit ve více než jedné skupině, vytvořte pro něj položku v části CommandPlacements, která musí být umístěna za oddíl Příkazy. Nastavte atributy GUID a ID elementu CommandPlacement tak, aby odpovídaly atributům tlačítka, které chcete umístit, a potom nastavte identifikátor GUID a ID jeho nadřazeného prvku na atributy cílové skupiny, jak je znázorněno v následujícím příkladu.

    ```xml
    <CommandPlacements>
        <CommandPlacement guid="guidReusableCommandPackageCmdSet" id="SecondReusableCommandId" priority="0x105">
          <Parent guid="guidReusableCommandPackageCmdSet" id="MyMenuGroup" />
        </CommandPlacement>
    </CommandPlacements>
    ```

    > [!NOTE]
    > Hodnota pole Priorita určuje pozici příkazu v nové skupině příkazů. Priority nastavené v elementu CommandPlacement přepíší ty, které jsou nastaveny v definici položky. Příkazy s nižšími hodnotami priority jsou zobrazeny před příkazy, které mají vyšší hodnoty priority. Duplicitní hodnoty priority jsou povoleny, ale relativní umístění příkazů, které mají stejnou hodnotu priority nelze zaručit, protože pořadí, ve kterém příkaz **devenv /setup** vytvoří konečné rozhraní z registru nemusí být konzistentní.

## <a name="to-put-a-reusable-group-of-buttons-on-a-menu"></a>V nabídce umístit opakovaně použitelnou skupinu tlačítek

1. Vytvořte položku `CommandPlacements` v oddílu. Nastavte identifikátor GUID a `CommandPlacement` ID prvku na identifikátory vaší skupiny a nastavte nadřazený identifikátor GUID a ID na identifikátory cílového umístění.

    Sekce CommandPlacements by měla být umístěna hned za oddíl emaprovátek příkazy:

   ```xml
   <CommandTable>
   ...
     <Commands>... </Commands>
     <CommandPlacements>... </CommandPlacements>
   ...
   </CommandTable>
   ```

    Skupinu příkazů lze zahrnout do více než jedné nabídky. Nadřazená nabídka může být ta, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] kterou jste vytvořili, která je dodána (jak je popsáno v *shellcmddef.vsct* nebo *SharedCmdDef.vsct*) nebo ta, která je definována v jiném VSPackage. Počet vrstev rodičovství je neomezený, pokud je nadřazená nabídka nakonec připojena k [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] místní nabídce, která je zobrazena v balíčku VSPackage.

    Následující příklad umístí skupinu na panelu nástrojů **Průzkumníka řešení** napravo od ostatních tlačítek.

   ```xml
   <CommandPlacements>
       <CommandPlacement guid="guidReusableCommandPackageCmdSet" id="MyMenuGroup" priority="0xF00">
         <Parent guid="guidSHLMainMenu" id="IDM_VS_TOOL_PROJWIN"/>
       </CommandPlacement>
   </CommandPlacements>
   ```

   ```xml
   <CommandPlacements>
     <CommandPlacement guid="guidButtonGroupCmdSet" id="MyMenuGroup"
         priority="0x605">
       <Parent guid="guidSHLMainMenu" id="IDM_VS_MENU_TOOLS" />
     </CommandPlacement>
   </CommandPlacements>

   ```
