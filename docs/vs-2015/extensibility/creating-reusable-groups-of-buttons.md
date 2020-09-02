---
title: Vytváření opakovaně použitelných skupin tlačítek | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- button groups, creating in VSPackages
- VSPackages, creating reusable button groups
- buttons, creating reusable groups
ms.assetid: 0c561617-fb86-476d-8bd1-c6e5e7464c65
caps.latest.revision: 45
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6ac1fd0dc242ae8b8979a3f420f5e1c4d837f62b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "64817664"
---
# <a name="creating-reusable-groups-of-buttons"></a>Vytváření znovu použitelných skupin tlačítek
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Skupina příkazů je kolekce příkazů, které se vždy zobrazují společně v nabídce nebo na panelu nástrojů. Libovolnou skupinu příkazů lze znovu použít přiřazením k různým nadřazeným nabídkám v části CommandPlacements souboru. vsct.  
  
 Skupiny příkazů obvykle obsahují tlačítka, ale mohou obsahovat také další nabídky nebo pole se seznamem.  
  
### <a name="to-create-a-reusable-group-of-buttons"></a>Vytvoření opakovaně použitelné skupiny tlačítek  
  
1. Vytvořte projekt VSIX s názvem `ReusableButtons` . Další informace najdete v tématu [Vytvoření rozšíření pomocí příkazu nabídky](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
2. Po otevření projektu přidejte šablonu vlastní položky příkazu s názvem **ReusableCommand**. V **Průzkumník řešení**klikněte pravým tlačítkem myši na uzel projektu a vyberte **přidat/nová položka**. V dialogovém okně **Přidat novou položku** přejít na **Visual C#/rozšiřitelnost** a vyberte **vlastní příkaz**. V poli **název** v dolní části okna změňte název souboru příkazů na **ReusableCommand.cs**.  
  
3. V souboru. vsct přejít do části symboly a vyhledejte element GuidSymbol, který obsahuje skupiny a příkazy pro projekt. Měl by mít název guidReusableCommandPackageCmdSet.  
  
4. Přidejte IDSymbol pro každé tlačítko, které přidáte do skupiny, jak je uvedeno v následujícím příkladu.  
  
    ```xml  
    <GuidSymbol name="guidReusableCommandPackageCmdSet" value="{7f383b2a-c6b9-4c1d-b4b8-a26dc5b60ca1}">  
        <IDSymbol name="MyMenuGroup" value="0x1020" />  
        <IDSymbol name="ReusableCommandId" value="0x0100" />  
        <IDSymbol name="SecondReusableCommandId" value="0x0200" />  
    </GuidSymbol>  
    ```  
  
     Ve výchozím nastavení Šablona položky příkazu vytvoří skupinu s názvem **MYGROUP** a tlačítko s názvem, který jste zadali, spolu s položkou IDSymbol pro každou z nich.  
  
5. V části skupiny vytvořte prvek skupiny, který má stejné atributy GUID a ID jako ty, které jsou uvedeny v části symboly. Můžete také použít existující skupinu nebo použít položku, která je poskytnuta šablonou příkazu, jak je uvedeno v následujícím příkladu. Tato skupina se zobrazí v nabídce **nástroje** .  
  
    ```xml  
    <Groups>  
        <Group guid="guidReusableCommandPackageCmdSet" id="MyMenuGroup" priority="0x0600">  
              <Parent guid="guidSHLMainMenu" id="IDM_VS_MENU_TOOLS"/>  
        </Group>  
    </Groups>  
    ```  
  
### <a name="to-create-a-group-of-buttons-for-reuse"></a>Vytvoření skupiny tlačítek k opakovanému použití  
  
1. Příkaz nebo nabídku můžete do skupiny umístit buď pomocí skupiny jako nadřazený v definici příkazu nebo nabídky, nebo vložením příkazu nebo nabídky do skupiny pomocí oddílu CommandPlacements.  
  
     V části tlačítka definujte tlačítko, které má vaši skupinu jako nadřazenou, nebo použijte tlačítko poskytované šablonou balíčku, jak je znázorněno v následujícím příkladu.  
  
    ```xml  
    <Button guid="guidReusableCommandPackageCmdSet" id="ReusableCommandId" priority="0x0100" type="Button">  
        <Parent guid="guidReusableCommandPackageCmdSet" id="MyMenuGroup" />  
        <Icon guid="guidImages" id="bmpPic1" />  
        <Strings>  
            <ButtonText>Invoke ReusableCommand</ButtonText>  
        </Strings>  
    </Button>  
    ```  
  
2. Pokud se tlačítko musí objevit ve více než jedné skupině, vytvořte pro něj položku v části CommandPlacements, která se musí umístit za oddíl Commands. Nastavte identifikátory GUID a ID elementu CommandPlacement tak, aby odpovídaly tlačítkům, které chcete umístit, a pak nastavte identifikátor GUID a ID jeho nadřazeného prvku na ty, jak je znázorněno v následujícím příkladu.  
  
    ```xml  
    <CommandPlacements>  
        <CommandPlacement guid="guidReusableCommandPackageCmdSet" id="SecondReusableCommandId" priority="0x105">  
          <Parent guid="guidReusableCommandPackageCmdSet" id="MyMenuGroup" />  
        </CommandPlacement>  
    </CommandPlacements>  
    ```  
  
    > [!NOTE]
    > Hodnota pole Priorita určuje pozici příkazu v nové skupině příkazů. Priority nastavené v elementu CommandPlacement přepisují ty nastavené v definici položky. Příkazy, které mají hodnoty s nižší prioritou, se zobrazí před příkazy, které mají hodnoty s vyšší prioritou. Duplicitní hodnoty priority jsou povoleny, ale relativní umístění příkazů, které mají stejnou hodnotu priority, nelze zaručit, protože pořadí, ve kterém příkaz **devenv/Setup** vytvoří konečné rozhraní z registru, nemusí být konzistentní.  
  
### <a name="to-put-a-reusable-group-of-buttons-on-a-menu"></a>Vložení opakovaně použitelné skupiny tlačítek v nabídce  
  
1. Vytvořte položku v `CommandPlacements` části. Nastavte identifikátor GUID a ID `CommandPlacement` elementu na hodnoty ve vaší skupině a nastavte nadřazený identifikátor GUID a ID na hodnoty cílového umístění.  
  
     Oddíl CommandPlacements by měl být umístěn hned za oddílem Commands:  
  
    ```xml  
    <CommandTable>  
    ...  
      <Commands>... </Commands>  
      <CommandPlacements>... </CommandPlacements>  
    ...   
    </CommandTable>  
    ```  
  
     Skupinu příkazů lze zahrnout do více než jedné nabídky. Nadřazená nabídka může být ta, kterou jste vytvořili, kterou poskytuje [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] (jak je popsáno v ShellCmdDef. vsct nebo SharedCmdDef. vsct), nebo v jednom, která je definována v jiné VSPackage. Počet nadřazených vrstev je neomezený, pokud je nadřazená nabídka nakonec připojena k [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] nebo k místní nabídce, která je zobrazena v VSPackage.  
  
     Následující příklad umístí skupinu na panel nástrojů **Průzkumník řešení** na pravé straně ostatních tlačítek.  
  
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
