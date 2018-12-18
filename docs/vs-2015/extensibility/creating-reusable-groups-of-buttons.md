---
title: Vytváření znovu použitelných skupin tlačítek | Dokumentace Microsoftu
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
- button groups, creating in VSPackages
- VSPackages, creating reusable button groups
- buttons, creating reusable groups
ms.assetid: 0c561617-fb86-476d-8bd1-c6e5e7464c65
caps.latest.revision: 45
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 79098eb51d9adc56021d3c57cb8d242edddeb9c3
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51732328"
---
# <a name="creating-reusable-groups-of-buttons"></a>Vytváření znovu použitelných skupin tlačítek
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Skupina příkazu je kolekce příkazů, které se vždy zobrazují společně na nabídku nebo panel nástrojů. Všechny skupiny příkazů je možné znovu po přiřazení k jiné nadřazené nabídky v části commandplacements – souboru .vsct.  
  
 Příkaz skupiny obvykle obsahují tlačítka, ale může taky obsahovat další nabídky nebo pole se seznamem.  
  
### <a name="to-create-a-reusable-group-of-buttons"></a>Chcete-li vytvořit opakovaně použitelných skupin tlačítek  
  
1.  Vytvořte projekt VSIX s názvem `ReusableButtons`. Další informace najdete v tématu [vytváření rozšíření pomocí příkazu nabídky](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
2.  Po otevření projektu přidat vlastní příkaz šablonu položky s názvem **ReusableCommand**. V **Průzkumníka řešení**, klikněte pravým tlačítkem na uzel projektu a vyberte **Add / nová položka**. V **přidat novou položku** dialogové okno, přejděte na **Visual C# / rozšíření** a vyberte **vlastního příkazu**. V **název** pole v dolní části okna, změňte název souboru příkazu **ReusableCommand.cs**.  
  
3.  V souboru .vsct přejděte do části symboly a najděte guidsymbol – element, který obsahuje skupiny a příkazy pro projekt. By měl být pojmenován guidReusableCommandPackageCmdSet.  
  
4.  Přidáte idsymbol – pro každé tlačítko, které přidáte do skupiny, jako v následujícím příkladu.  
  
    ```xml  
    <GuidSymbol name="guidReusableCommandPackageCmdSet" value="{7f383b2a-c6b9-4c1d-b4b8-a26dc5b60ca1}">  
        <IDSymbol name="MyMenuGroup" value="0x1020" />  
        <IDSymbol name="ReusableCommandId" value="0x0100" />  
        <IDSymbol name="SecondReusableCommandId" value="0x0200" />  
    </GuidSymbol>  
    ```  
  
     Ve výchozím nastavení, šablona položky příkaz vytvoří skupinu **MyGroup** tlačítka a tlačítka, který má název, který jste zadali, společně s idsymbol – záznam pro každý.  
  
5.  V části skupiny vytvořte prvek skupiny, který má stejný identifikátor GUID a ID atributy jako ty uvedené v části symboly. Můžete také použít existující skupinu nebo použít položku, která je k dispozici pomocí příkazu šablony, jako v následujícím příkladu. Tato skupina se zobrazí na **nástroje** nabídky  
  
    ```xml  
    <Groups>  
        <Group guid="guidReusableCommandPackageCmdSet" id="MyMenuGroup" priority="0x0600">  
              <Parent guid="guidSHLMainMenu" id="IDM_VS_MENU_TOOLS"/>  
        </Group>  
    </Groups>  
    ```  
  
### <a name="to-create-a-group-of-buttons-for-reuse"></a>Chcete-li vytvořit skupinu tlačítek pro opakované použití  
  
1.  Příkaz nebo nabídky můžete umístit do skupiny pomocí skupiny jako rodič v definici příkazu nebo nabídky nebo vložením příkazu nebo nabídky ve skupině pomocí commandplacements – část.  
  
     V části tlačítka definovat tlačítko, které má vaše skupiny jako jeho nadřazeným prvkem, nebo pomocí tlačítka, která je poskytována balíček šablony, jak je znázorněno v následujícím příkladu.  
  
    ```xml  
    <Button guid="guidReusableCommandPackageCmdSet" id="ReusableCommandId" priority="0x0100" type="Button">  
        <Parent guid="guidReusableCommandPackageCmdSet" id="MyMenuGroup" />  
        <Icon guid="guidImages" id="bmpPic1" />  
        <Strings>  
            <ButtonText>Invoke ReusableCommand</ButtonText>  
        </Strings>  
    </Button>  
    ```  
  
2.  Pokud tlačítko musí být uvedena ve více než jedné skupině, vytvořte záznam pro něj v části commandplacements – musí být umístěné za část příkazy. Nastavení atributů commandplacement – element tak, aby odpovídaly u tlačítka, které chcete umístit GUID a ID a potom nastavte GUID a ID objektů svého nadřízeného elementu na hodnoty cílové skupiny, jak je znázorněno v následujícím příkladu.  
  
    ```xml  
    <CommandPlacements>  
        <CommandPlacement guid="guidReusableCommandPackageCmdSet" id="SecondReusableCommandId" priority="0x105">  
          <Parent guid="guidReusableCommandPackageCmdSet" id="MyMenuGroup" />  
        </CommandPlacement>  
    </CommandPlacements>  
    ```  
  
    > [!NOTE]
    >  Hodnota pole Priorita určuje pozici příkazu v nové skupině příkazu. Nastavení priority v commandplacement – element mají přednost před akcemi nastavené v definici položky. Příkazy, které mají nižší hodnoty priority se zobrazují před příkazy, které mají vyšší hodnoty priority. Priorita duplicitní hodnoty jsou povolené, ale relativní pozice příkazy, které mají stejnou hodnotu priority nemůže být zaručena, protože pořadí, ve kterém **devenv/Setup** příkaz vytvoří konečné rozhraní z registru mohou být nekonzistentní.  
  
### <a name="to-put-a-reusable-group-of-buttons-on-a-menu"></a>Vložit opakovaně použitelných skupin tlačítek v nabídce  
  
1.  Vytvořit položku v `CommandPlacements` oddílu. Nastavte identifikátor GUID a ID `CommandPlacement` element u těch, které vaší skupiny a nastavit nadřazený identifikátor GUID a ID u těch, které v cílovém umístění.  
  
     Commandplacements – oddíl by měl umístit bezprostředně po části příkazy:  
  
    ```xml  
    <CommandTable>  
    ...  
      <Commands>... </Commands>  
      <CommandPlacements>... </CommandPlacements>  
    ...   
    </CommandTable>  
    ```  
  
     Příkaz skupiny můžou být zahrnuté ve více než jednu nabídku. Nadřazené nabídky může být ten, který jste vytvořili, ten, který je poskytnut pomocí [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] (jako je popsáno v ShellCmdDef.vsct nebo SharedCmdDef.vsct), nebo disk, který je definován v jiné VSPackage. Počet vrstev vztahy k nadřazeným položkám je neomezený počet tak dlouho, dokud nabídce nadřazený server připojený k [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] nebo do místní nabídky, který se zobrazí při VSPackage.  
  
     Následující příklad umístí na skupině **Průzkumníka řešení** napravo od ostatních tlačítek panelu nástrojů.  
  
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

