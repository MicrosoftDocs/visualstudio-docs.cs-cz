---
title: MenuCommands vs. OleMenuCommands | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- commands, creating in VSPackages
- command buttons, creating and placing
- menus, creating commands
ms.assetid: 553d5e07-3e19-4aba-b490-6c7dd05fd82e
caps.latest.revision: 46
manager: jillfra
ms.openlocfilehash: 42c471ca924bfded62db32a956a26c07240459eb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "67624454"
---
# <a name="menucommands-vs-olemenucommands"></a>MenuCommands vs. OleMenuCommands
Příkazy nabídky lze vytvořit odvozením buď z <xref:System.ComponentModel.Design.MenuCommand> objektu nebo z <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> objektu a implementací příslušných obslužných rutin událostí. Ve většině případů můžete použít <xref:System.ComponentModel.Design.MenuCommand> , jako šablonu projektu VSPackage, ale občas může být nutné použít <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> .  
  
 Příkazy, které VSPackage zpřístupňuje pro IDE, musí být viditelné a povolené předtím, než je uživatel může použít. Když jsou příkazy vytvořeny v souboru. vsct pomocí šablony projektu balíčku sady Visual Studio, jsou viditelné a povolené ve výchozím nastavení. Nastavení některých příznaků příkazu, například `DynamicItemStart` , může změnit výchozí chování. Viditelnost, stav povoleno a další vlastnosti příkazu lze změnit také v kódu za běhu, a to přístupem k <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> objektu, který je přidružen k příkazu.  
  
## <a name="prerequisites"></a>Předpoklady  
 Chcete-li postupovat podle tohoto návodu, je nutné nainstalovat sadu Visual Studio SDK. Další informace najdete v tématu [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
## <a name="template-locations-for-the-visual-studio-package-template"></a>Umístění šablon pro šablonu balíčku sady Visual Studio  
 Šablonu balíčku sady Visual Studio najdete v dialogovém okně **Nový projekt** v části **Visual Basic/rozšiřitelnost**, **C#/rozšiřitelnost**nebo **jiné typy projektů a rozšiřitelnost**.  
  
## <a name="creating-a-command"></a>Vytvoření příkazu  
 Všechny příkazy, skupiny příkazů, nabídky, panely nástrojů a okna nástrojů jsou definovány v souboru. vsct. Další informace naleznete v tématu [tabulka příkazů sady Visual Studio (. Vsct) soubory](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).  
  
 Vytváříte-li VSPackage pomocí šablony balíčku, vyberte **příkaz nabídky** k vytvoření souboru. vsct a definování výchozího příkazu nabídky. Další informace najdete v tématu [Vytvoření rozšíření pomocí příkazu nabídky](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
#### <a name="to-add-a-command-to-the-ide"></a>Přidání příkazu do integrovaného vývojového prostředí  
  
1. Otevřete soubor. vsct.  
  
2. V `Symbols` části Najděte element [GuidSymbol](../extensibility/guidsymbol-element.md) , který obsahuje skupiny a příkazy.  
  
3. Vytvořte element [IDSymbol](../extensibility/idsymbol-element.md) pro každou nabídku, skupinu nebo příkaz, který chcete přidat, jak je znázorněno v následujícím příkladu.  
  
   ```xml
   <GuidSymbol name="guidButtonGroupCmdSet" value="{f69209e9-975a-4543-821d-1f4a2c52d737}">
     <IDSymbol name="MyMenuGroup" value="0x1020" />
     <IDSymbol name="cmdidMyCommand" value="0x0100" />
   </GuidSymbol>
   ```
      
    `name`Atributy `GuidSymbol` `IDSymbol` elementů a poskytují dvojici identifikátorů GUID: ID pro každou novou nabídku, skupinu nebo příkaz. `guid`Představuje sadu příkazů, která je definována pro sadu VSPackage. Můžete definovat několik sad příkazů. Každá dvojice identifikátoru GUID: ID musí být jedinečná.  
  
4. V části [tlačítka](../extensibility/buttons-element.md) vytvořte element [Button](../extensibility/button-element.md) pro definování příkazu, jak je znázorněno v následujícím příkladu.  
  
   ```xml
   <Button guid="guidButtonGroupCmdSet" id="cmdidMyCommand" priority="0x0100" type="Button">
     <Parent guid="guidButtonGroupCmdSet" id="MyMenuGroup" />
     <Icon guid="guidImages" id="bmpPic1" />
     <Strings>
       <CommandName>cmdidMyCommand</CommandName>
       <ButtonText>My Command name</ButtonText>
     </Strings>
   </Button>
   ``` 
     
   1. Nastavte `guid` pole a `id` tak, aby ODPOVÍDALa identifikátoru GUID: ID nového příkazu.  
  
   2. Nastavte `priority` atribut.  
  
        `priority`Atribut používá rozhraní. vsct k určení umístění tlačítka mezi ostatními objekty v nadřazené skupině.  
  
        Příkazy, které mají hodnoty nižší priority, jsou zobrazeny výše nebo nalevo od příkazů, které mají hodnoty s vyšší prioritou. Duplicitní hodnoty priority jsou povoleny, ale relativní pozice příkazů, které mají stejnou prioritu, je určena pořadím, ve kterém jsou sady VSPackage zpracovávány v době běhu, a toto pořadí nelze předem určit.  
  
        Vynechání `priority` atributu nastaví hodnotu na 0.  
  
   3. Nastavte `type` atribut. Ve většině případů bude jeho hodnota `"Button"` . Popisy dalších platných typů tlačítek naleznete v tématu [element Button](../extensibility/button-element.md).  
  
5. V definici tlačítka vytvořte element [strings](../extensibility/strings-element.md) , který obsahuje element [ButtonText](../extensibility/buttontext-element.md) , aby obsahoval název nabídky, jak se zobrazuje v integrovaném vývojovém prostředí (IDE), a element [Command](../extensibility/commandname-element.md) , který obsahuje název příkazu, který se používá pro přístup k nabídce v **příkazovém** okně.  
  
    Pokud textový řetězec tlačítka obsahuje znak ' & ', uživatel může nabídku otevřít stisknutím klávesy ALT a znaku, který následuje hned po ' & '.  
  
    Přidáním `Tooltip` elementu se zobrazí obsažený text, který se zobrazí, když uživatel najede ukazatelem myši na tlačítko.  
  
6. Přidejte prvek [ikony](../extensibility/icon-element.md) pro určení ikony, pokud existuje, aby se zobrazila s příkazem. Ikony jsou vyžadovány pro tlačítka na panelech nástrojů, ale ne pro položky nabídky. `guid`A `id` `Icon` elementu musí odpovídat prvkům [rastrového obrázku](../extensibility/bitmap-element.md) definovaného v `Bitmaps` oddílu.  
  
7. Přidejte příznaky příkazu podle potřeby pro změnu vzhledu a chování tlačítka. Chcete-li to provést, přidejte do definice nabídky element [CommandFlag](../extensibility/command-flag-element.md) .  
  
8. Nastavte nadřazenou skupinu příkazu. Nadřazená skupina může být skupina, kterou vytvoříte, skupinu z jiného balíčku nebo skupinu z integrovaného vývojového prostředí (IDE). Například chcete-li přidat příkaz do panelu nástrojů pro úpravy sady Visual Studio, vedle tlačítek **Komentář** a **odebrat komentář** nastavte nadřazený na guidStdEditor: IDG_VS_EDITTOOLBAR_COMMENT. Pokud je nadřazená uživatelem definovaná skupina, musí být podřízenou položkou nabídky, panelu nástrojů nebo panelu nástrojů, která se zobrazí v integrovaném vývojovém prostředí.  
  
    To můžete provést jedním ze dvou způsobů v závislosti na vašem návrhu:  
  
   - V `Button` elementu vytvořte [nadřazený](../extensibility/parent-element.md) element a nastavte jeho `guid` `id` pole a na identifikátor GUID a ID skupiny, která bude hostovat příkaz, označovaný také jako *primární nadřazená skupina*.  
  
        Následující příklad definuje příkaz, který se zobrazí v uživatelsky definované nabídce.  
  
       ```xml
       <Button guid="guidTopLevelMenuCmdSet" id="cmdidTestCommand" priority="0x0100" type="Button">
         <Parent guid="guidTopLevelMenuCmdSet" id="MyMenuGroup" />
         <Icon guid="guidImages" id="bmpPic1" />
         <Strings>
           <CommandName>cmdidTestCommand</CommandName>
           <ButtonText>Test Command</ButtonText>
             </Strings>
       </Button>
       ```
      
   - Element můžete vynechat, `Parent` Pokud se má příkaz umístit pomocí umístění příkazu. Vytvořte element [CommandPlacements](../extensibility/commandplacements-element.md) před `Symbols` oddíl a přidejte element [CommandPlacement](../extensibility/commandplacement-element.md) , který obsahuje a, a, `guid` `id` `priority` a, a, a nadřazený objekt, jak je znázorněno v následujícím příkladu.  
  
   ```xml
   <CommandPlacements>
     <CommandPlacement guid="guidButtonGroupCmdSet" id="cmdidMyCommand" priority="0x105">
       <Parent guid="guidButtonGroupCmdSet" id="MyMenuGroup" />
     </CommandPlacement>
   </CommandPlacements>
   ```
      
      Vytvoření více umístění příkazů, které mají stejné GUID: ID a mají jiné nadřazené položky, způsobí, že se nabídka zobrazí v několika umístěních. Další informace naleznete v tématu [CommandPlacements](../extensibility/commandplacements-element.md) element.  
  
    Další informace o skupinách příkazů a o nadřazeném prvku naleznete v tématu [vytváření opakovaně použitelných skupin tlačítek](../extensibility/creating-reusable-groups-of-buttons.md).  
  
   V tomto okamžiku bude příkaz viditelný v integrovaném vývojovém prostředí, ale nebude mít žádné funkce. Pokud byl příkaz vytvořen šablonou balíčku, ve výchozím nastavení bude mít obslužnou rutinu Click, která zobrazí zprávu.  
  
## <a name="handling-the-new-command"></a>Zpracování nového příkazu  
 Většina příkazů ve spravovaném kódu může být zpracována pomocí rozhraní příkazového řádku (MPF) pomocí přidružení příkazu k <xref:System.ComponentModel.Design.MenuCommand> objektu nebo <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> objektu a implementací jeho obslužných rutin událostí.  
  
 Pro kód, který používá <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> rozhraní přímo pro zpracování příkazů, je nutné implementovat <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> rozhraní a jeho metody. Obě nejdůležitější metody jsou <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> a <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> .  
  
1. Získejte <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService> instanci, jak je znázorněno v následujícím příkladu.  
  
     [!code-csharp[ButtonGroup#21](../snippets/csharp/VS_Snippets_VSSDK/buttongroup/cs/buttongrouppackage.cs#21)]  
  
2. Vytvořte <xref:System.ComponentModel.Design.CommandID> objekt, který má jako svůj parametr identifikátor GUID a ID příkazu, který má být zpracován, jak je znázorněno v následujícím příkladu.  
  
     [!code-csharp[ButtonGroup#22](../snippets/csharp/VS_Snippets_VSSDK/buttongroup/cs/buttongrouppackage.cs#22)]  
  
     Šablona balíčku sady Visual Studio poskytuje dvě kolekce, `GuidList` a `PkgCmdIDList` pro uchování identifikátorů GUID a ID příkazů. Tyto položky jsou vyplněny automaticky pro příkazy, které jsou přidány šablonou, ale pro příkazy, které přidáte ručně, musíte také přidat položku ID do `PkgCmdIdList` třídy.  
  
     Alternativně můžete objekt naplnit <xref:System.ComponentModel.Design.CommandID> pomocí hodnoty nezpracovaného řetězce GUID a celočíselné hodnoty ID.  
  
3. Vytvořte instanci <xref:System.ComponentModel.Design.MenuCommand> <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> objektu nebo, která určuje metodu, která zpracovává příkaz spolu s <xref:System.ComponentModel.Design.CommandID> , jak je znázorněno v následujícím příkladu.  
  
     [!code-csharp[ButtonGroup#23](../snippets/csharp/VS_Snippets_VSSDK/buttongroup/cs/buttongrouppackage.cs#23)]  
  
     <xref:System.ComponentModel.Design.MenuCommand>Je vhodný pro statické příkazy. Dynamické zobrazení položky nabídky vyžadují obslužné rutiny událostí QueryStatus. <xref:Microsoft.VisualStudio.Shell.OleMenuCommand>Přidá <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus> událost, která nastane, když se otevře nabídka hostitel příkazu a některé další vlastnosti, například <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.Text%2A> .  
  
     Příkazy vytvořené šablonou balíčku jsou ve výchozím nastavení předány <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> objektu v `Initialize()` metodě třídy Package.  
  
4. <xref:System.ComponentModel.Design.MenuCommand>Je vhodný pro statické příkazy. Dynamické zobrazení položky nabídky vyžadují obslužné rutiny událostí QueryStatus. <xref:Microsoft.VisualStudio.Shell.OleMenuCommand>Přidá <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus> událost, která nastane, když se otevře nabídka hostitel příkazu a některé další vlastnosti, například <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.Text%2A> .  
  
     Příkazy vytvořené šablonou balíčku jsou ve výchozím nastavení předány <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> objektu v `Initialize()` metodě třídy Package. Průvodce sady Visual Studio implementuje `Initialize` metodu pomocí `MenuCommand` . V případě dynamické položky nabídky je nutné ji změnit na `OleMenuCommand` , jak je znázorněno v následujícím kroku. Chcete-li také změnit text položky nabídky, je nutné přidat příznak příkazu TextChanges do příkazového tlačítka nabídky v souboru. vsct, jak je znázorněno v následujícím příkladu.  
  
    ```xml
    <Button guid="guidMenuTextCmdSet" id="cmdidMyCommand" priority="0x0100" type="Button">
      <Parent guid="guidMenuTextCmdSet" id="MyMenuGroup" />
      <Icon guid="guidImages" id="bmpPic1" />
      <CommandFlag>TextChanges</CommandFlag>
      <Strings>
        <CommandName>cmdidMyCommand</CommandName>
        <ButtonText>My Command name</ButtonText>
      </Strings>
    </Button>
    ```
      
5. Předání příkazu New nabídky <xref:System.ComponentModel.Design.IMenuCommandService.AddCommand%2A> metodě v <xref:System.ComponentModel.Design.IMenuCommandService> rozhraní. To je ve výchozím nastavení provedeno pro příkazy vytvořené šablonou balíčku, jak je znázorněno v následujícím příkladu.  
  
     [!code-csharp[ButtonGroup#24](../snippets/csharp/VS_Snippets_VSSDK/buttongroup/cs/buttongrouppackage.cs#24)]  
  
6. Implementujte metodu, která zpracovává příkaz.  
  
#### <a name="to-implement-querystatus"></a>Implementace QueryStatus  
  
1. K události QueryStatus dojde před zobrazením příkazu. Tím umožníte, aby se vlastnosti tohoto příkazu nastavily v obslužné rutině události předtím, než dorazí uživatele. <xref:Microsoft.VisualStudio.Shell.OleMenuCommand>Přístup k této metodě mají jenom příkazy přidávané jako objekty.  
  
    Přidejte `EventHandler` objekt k <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus> události v <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> objektu, který je vytvořen pro zpracování příkazu, jak je znázorněno v následujícím příkladu ( `menuItem` je <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> instance).  
  
    [!code-csharp[MenuText#14](../snippets/csharp/VS_Snippets_VSSDK/menutext/cs/menutextpackage.cs#14)]
    [!code-vb[MenuText#14](../snippets/visualbasic/VS_Snippets_VSSDK/menutext/vb/menutextpackage.vb#14)]  
  
    `EventHandler`Objektu je dán název metody, která je volána při dotazování na stav příkazu nabídky.  
  
2. Implementujte metodu obslužné rutiny stavu dotazu pro příkaz. `object` `sender` Parametr lze přetypovat na <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> objekt, který se používá k nastavení různých atributů příkazu nabídky, včetně textu. V následující tabulce jsou uvedeny vlastnosti <xref:System.ComponentModel.Design.MenuCommand> třídy (která třída MPF je <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> odvozena z), která odpovídá <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF> příznakům.  
  
   |Vlastnost MenuCommand|Příznak OLECMDF|  
   |--------------------------|------------------|  
   |<xref:System.ComponentModel.Design.MenuCommand.Checked%2A> = `true`|<xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF>|  
   |<xref:System.ComponentModel.Design.MenuCommand.Visible%2A> = `false`|<xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF>|  
   |<xref:System.ComponentModel.Design.MenuCommand.Enabled%2A> = `true`|<xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF>|  
  
    Chcete-li změnit text příkazu nabídky, použijte <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.Text%2A> vlastnost <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> objektu, jak je znázorněno v následujícím příkladu.  
  
    [!code-csharp[MenuText#11](../snippets/csharp/VS_Snippets_VSSDK/menutext/cs/menutextpackage.cs#11)]
    [!code-vb[MenuText#11](../snippets/visualbasic/VS_Snippets_VSSDK/menutext/vb/menutextpackage.vb#11)]  
  
   MPF automaticky zpracuje případ nepodporovaných nebo neznámých skupin. Není-li příkaz přidán k metodě pomocí <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService> <xref:System.ComponentModel.Design.IMenuCommandService.AddCommand%2A> metody, není příkaz podporován.  
  
### <a name="handling-commands-by-using-the-iolecommandtarget-interface"></a>Zpracování příkazů pomocí rozhraní IOleCommandTarget –  
 Pro kód, který používá <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> rozhraní přímo, VSPackage musí implementovat <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> metody a <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> rozhraní. Pokud VSPackage implementuje hierarchii projektu, <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> měla by být místo toho implementovány metody a rozhraní.  
  
 Obě <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> metody a <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> jsou navržené tak, aby přijímaly jedinou sadu příkazů `GUID` a pole ID příkazů jako vstup. Doporučujeme, aby VSPackage v jednom volání plně podporovaly tento koncept více identifikátorů. Pokud však není rozhraní VSPackage voláno z jiných rozhraní VSPackage, můžete předpokládat, že pole příkazů obsahuje pouze jeden identifikátor příkazu, protože <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> metody a jsou spouštěny v dobře definovaném pořadí. Další informace o směrování najdete v tématu [směrování příkazů v VSPackage](../extensibility/internals/command-routing-in-vspackages.md).  
  
 Pro kód, který používá <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> rozhraní přímo pro zpracování příkazů, je nutné implementovat <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> metodu v rozhraní VSPackage následujícím způsobem pro zpracování příkazů.  
  
##### <a name="to-implement-the-querystatus-method"></a>Implementace metody QueryStatus  
  
1. Vrátí se <xref:Microsoft.VisualStudio.VSConstants.S_OK> pro platné příkazy.  
  
2. Nastavte `cmdf` element `prgCmds` parametru.  
  
    Hodnota `cmdf` elementu je logické sjednocení hodnot z <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF> výčtu kombinované pomocí `|` operátoru logického operátoru OR ().  
  
    Použijte odpovídající výčet na základě stavu příkazu:  
  
   - Je-li příkaz podporován:  
  
      `prgCmds[0].cmdf = OLECMDF_SUPPORTED;`  
  
   - Pokud by příkaz neměl být v tuto chvíli neviditelný:  
  
      `prgCmds[0].cmdf |= OLECMDF_INVISIBLE;`  
  
   - Pokud je příkaz zapnutý a zdá se, že jste klikli na:  
  
      `prgCmds[0].cmdf |= OLECMDF_LATCHED;`  
  
      V případě příkazů pro zpracování, které jsou hostovány v nabídce typu `MenuControllerLatched` , je prvním příkazem, který je označen `OLECMDF_LATCHED` příznakem, výchozím příkazem, který je zobrazen v nabídce při spuštění. Další informace o `MenuController` typech nabídek naleznete v tématu [element menu](../extensibility/menu-element.md).  
  
   - Pokud je tento příkaz aktuálně povolený:  
  
      `prgCmds[0].cmdf |= OLECMDF_ENABLED;`  
  
   - Pokud je příkaz součástí místní nabídky a ve výchozím nastavení je skrytý:  
  
      `prgCmds[0] cmdf |= OLECMDF_DEFHIDEONCTXMENU`  
  
   - Pokud příkaz používá `TEXTCHANGES` příznak, nastavte `rgwz` element `pCmdText` parametru na nový text příkazu a nastavte `cwActual` element `pCmdText` parametru na velikost řetězce příkazu.  
  
     V případě chybových podmínek <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> musí metoda zpracovávat následující chybové případy:  
  
   - Pokud identifikátor GUID není znám nebo není podporován, vrátí `OLECMDERR_E_UNKNOWNGROUP` .  
  
   - Pokud je známý identifikátor GUID, ale ID příkazu není známo nebo není podporováno, vraťte se `OLECMDERR_E_NOTSUPPORTED` .  
  
   Implementace VSPackage <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> metody musí také vracet konkrétní kódy chyb v závislosti na tom, zda je příkaz podporován a zda byl příkaz úspěšně zpracován.  
  
##### <a name="to-implement-the-exec-method"></a>Implementace metody exec  
  
- Pokud je příkaz `GUID` Neznámý, vrátí `OLECMDERR_E_UNKNOWNGROUP` .  
  
- Pokud `GUID` je známo, ale ID příkazu je neznámé, vraťte se `OLECMDERR_E_NOTSUPPORTED` .  
  
- Pokud `GUID` ID příkazu a odpovídá páru identifikátorů GUID: ID, který je používán příkazem v souboru. vsct, spusťte kód, který je spojen s příkazem a vrátí <xref:Microsoft.VisualStudio.VSConstants.S_OK> .  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace schématu VSCT XML](../extensibility/vsct-xml-schema-reference.md)   
 [Rozšiřování nabídek a příkazů](../extensibility/extending-menus-and-commands.md)
