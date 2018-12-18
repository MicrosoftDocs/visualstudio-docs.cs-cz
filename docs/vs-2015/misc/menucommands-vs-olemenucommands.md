---
title: MenuCommands Vs. OleMenuCommands | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- commands, creating in VSPackages
- command buttons, creating and placing
- menus, creating commands
ms.assetid: 553d5e07-3e19-4aba-b490-6c7dd05fd82e
caps.latest.revision: 46
manager: douge
ms.openlocfilehash: 3b548a43cabcb097250411c3475f47774c840511
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49911905"
---
# <a name="menucommands-vs-olemenucommands"></a>MenuCommands Vs. OleMenuCommands
Můžete vytvořit příkazy nabídky odvozením buď z <xref:System.ComponentModel.Design.MenuCommand> nebo z <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> objektu a impementling obslužné rutiny události. Ve většině případů můžete použít <xref:System.ComponentModel.Design.MenuCommand>, jak funkce balíčku VSPackage šablony projektu, ale někdy možná muset použít <xref:Microsoft.VisualStudio.Shell.OleMenuCommand>.  
  
 Příkazy, VSPackage zpřístupňují integrovaného vývojového prostředí musí být viditelné a povolené před uživatele můžete využít. Příkazy jsou v souboru .vsct vytvořen pomocí šablony projektu balíček Visual Studio, jsou viditelné a povolené ve výchozím nastavení. Nastavení některých příznaků příkazů, jako například `DynamicItemStart`, můžete změnit výchozí chování. Viditelnost, povoleného stavu a dalších vlastností příkaz lze také změnit v kódu v době běhu díky přístupu <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> objekt, který je přidružený příkaz.  
  
## <a name="prerequisites"></a>Požadavky  
 Chcete-li postupovat podle tohoto návodu, je nutné nainstalovat sadu Visual Studio SDK. Další informace najdete v tématu [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
## <a name="template-locations-for-the-visual-studio-package-template"></a>Umístění šablon pro šablony sady Visual Studio balíček  
 Šablony do balíčku Visual Studio můžete najít **nový projekt** dialogového okna v části **jazyka Visual Basic / rozšíření**, **jazyka C# / rozšíření**, nebo **další Typy projektů / rozšíření**.  
  
## <a name="creating-a-command"></a>Vytvoření příkazu  
 Všechny příkazy, pro skupinu příkazů, nabídky, panely nástrojů a okna nástrojů jsou definovány v souboru .vsct. Další informace najdete v tématu [tabulky příkazů aplikace Visual Studio (. Vsct) soubory](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).  
  
 Pokud vytváříte VSPackage pomocí šablony balíčku, vyberte **příkazu nabídky** k vytvoření souboru .vsct a definování příkazu nabídky výchozí. Další informace najdete v tématu [vytváření rozšíření pomocí příkazu nabídky](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
#### <a name="to-add-a-command-to-the-ide"></a>Přidání příkazu do integrovaného vývojového prostředí  
  
1. Otevření souboru .vsct.  
  
2. V `Symbols` části, vyhledejte [guidsymbol –](../extensibility/guidsymbol-element.md) element, který obsahuje skupiny a příkazy.  
  
3. Vytvoření [idsymbol –](../extensibility/idsymbol-element.md) – element pro každou nabídku, skupinu nebo příkaz, který chcete přidat, jak je znázorněno v následujícím příkladu.  
  
   ```xml
   <GuidSymbol name="guidButtonGroupCmdSet" value="{f69209e9-975a-4543-821d-1f4a2c52d737}">
     <IDSymbol name="MyMenuGroup" value="0x1020" />
     <IDSymbol name="cmdidMyCommand" value="0x0100" />
   </GuidSymbol>
   ```
      
    `name` Atributy `GuidSymbol` a `IDSymbol` prvky poskytují pár GUID:ID pro každou novou nabídku, skupinu nebo příkaz. `guid` Představuje sadu příkaz, který je definován pro vaše VSPackage. Můžete definovat více sady příkazů. Každý pár GUID:ID musí být jedinečný.  
  
4. V [tlačítka](../extensibility/buttons-element.md) části, vytvořte [tlačítko](../extensibility/button-element.md) element definovat příkaz, jak je znázorněno v následujícím příkladu.  
  
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
     
   1.  Nastavte `guid` a `id` pole tak, aby odpovídaly GUID:ID nový příkaz.  
  
   2.  Nastavte `priority` atribut.  
  
        `priority` Atribut .vsct používá k určení umístění tlačítka mezi ostatní objekty v své nadřazené skupiny.  
  
        Příkazy, které mají nižší hodnoty priority se zobrazují nad nebo nalevo od příkazy, které mají vyšší hodnoty priority. Priorita duplicitní hodnoty jsou povoleny, ale relativní pozice příkazy, které mají stejnou prioritu je určen podle pořadí, ve kterém jsou zpracovány rozšíření VSPackages v době běhu a pořadí nemůže být předem.  
  
        Vynechání `priority` atribut nastaví její hodnotu na 0.  
  
   3.  Nastavte `type` atribut. Ve většině případů je jeho hodnota bude `"Button"`. Popisy jiných typech tlačítek platný, naleznete v tématu [Button Element](../extensibility/button-element.md).  
  
5. V definici tlačítko vytvořit [řetězce](../extensibility/strings-element.md) element, který obsahuje [ButtonText](../extensibility/buttontext-element.md) element tak, aby obsahovala název nabídky, jak se zobrazí v rozhraní IDE a [CommandName](../extensibility/commandname-element.md) Element tak, aby obsahovala název příkazu, který se používá pro přístup z nabídky **příkaz** okna.  
  
    Pokud tlačítko textový řetězec obsahuje znak "&", může uživatel otevřít stisknutím klávesy ALT v nabídce navíc bezprostředně následuje znak "&".  
  
    Přidávání `Tooltip` prvku způsobí, že obsažený text, který se zobrazí, když uživatel nechá ukazatel myši nad tlačítkem.  
  
6. Přidat [ikonu](../extensibility/icon-element.md) element zadat ikonu, pokud chcete zobrazit pomocí příkazu. Ikony jsou požadovány pro tlačítka na panely nástrojů, ale nikoli pro položky nabídky. `guid` a `id` z `Icon` elementu musí odpovídat názvům [rastrový obrázek](../extensibility/bitmap-element.md) element definovaný v `Bitmaps` oddílu.  
  
7. Podle potřeby, chcete-li změnit vzhled a chování tlačítka přidejte příznaků příkazů. Chcete-li to provést, přidejte [CommandFlag](../extensibility/command-flag-element.md) element v definici nabídky.  
  
8. Nastavte skupinu nadřazeného příkazu. Nadřazená skupina může být skupiny, které vytvoříte, skupinu z jiný balíček nebo skupinu z integrovaného vývojového prostředí. Například pro přidání příkazu do úprav nástrojů sady Visual Studio, vedle položky **komentář** a **odebrat komentář** tlačítka, k guidStdEditor:IDG_VS_EDITTOOLBAR_COMMENT nastavit nadřazený prvek. Pokud nadřazená skupina uživatelem definované, musí být podřízenou položkou nabídky, nástrojů nebo okna nástroje, který se zobrazí v integrovaném vývojovém prostředí.  
  
    Jedním ze dvou způsobů, tento krok lze provést v závislosti na návrhu:  
  
   -   V `Button` elementu, vytvořit [nadřazené](../extensibility/parent-element.md) elementu a nastavte jeho `guid` a `id` polí pro identifikátor Guid a ID skupiny, který bude hostitelem příkazu, označované také jako *primárnínadřazenéskupiny*.  
  
        Následující příklad definuje příkaz, který se zobrazí v nabídce definovaný uživatelem.  
  
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
      
   -   Můžete vynechat `Parent` element, pokud je příkaz, který se umístil pomocí příkazu umístění. Vytvoření [commandplacements –](../extensibility/commandplacements-element.md) prvek před `Symbols` a přidejte [commandplacement –](../extensibility/commandplacement-element.md) element, který má `guid` a `id` příkazu `priority`a nadřazené položky, jak je znázorněno v následujícím příkladu.  
  
   ```xml
   <CommandPlacements>
     <CommandPlacement guid="guidButtonGroupCmdSet" id="cmdidMyCommand" priority="0x105">
       <Parent guid="guidButtonGroupCmdSet" id="MyMenuGroup" />
     </CommandPlacement>
   </CommandPlacements>
   ```
      
        Creating multiple command placements that have the same GUID:ID and have different parents causes a menu to appear in multiple locations. For more information, see [CommandPlacements](../extensibility/commandplacements-element.md) element.  
  
    Další informace o skupinách příkazu a vztahy k nadřazeným položkám najdete v tématu [vytvoření opakovaně použitelného skupiny z tlačítka](../extensibility/creating-reusable-groups-of-buttons.md).  
  
   Příkaz v tomto okamžiku se nebude zobrazovat v integrovaném vývojovém prostředí, ale nebude mít žádné funkce. Pokud příkaz vytvořil balíček šablony, ve výchozím nastavení bude mít obslužnou rutinu kliknutí, který zobrazí zprávu.  
  
## <a name="handling-the-new-command"></a>Zpracování nového příkazu  
 Většina příkazů ve spravovaném kódu může být zpracována podle na spravované Package Framework (MPF) přidružení příkaz s <xref:System.ComponentModel.Design.MenuCommand> objektu nebo <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> objektu a implementace jeho obslužné rutiny událostí.  
  
 Pro kód, který se používá <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> rozhraní přímo pro zpracování příkazů, je nutné implementovat <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> rozhraní a její metody. Dvě nejdůležitější metody jsou <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> a <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A>.  
  
1.  Získejte <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService> instance, jak je znázorněno v následujícím příkladu.  
  
     [!code-csharp[ButtonGroup#21](../snippets/csharp/VS_Snippets_VSSDK/buttongroup/cs/buttongrouppackage.cs#21)]  
  
2.  Vytvoření <xref:System.ComponentModel.Design.CommandID> objekt, který má jako svoje parametry identifikátoru GUID a ID příkazu pro zpracování, jak je znázorněno v následujícím příkladu.  
  
     [!code-csharp[ButtonGroup#22](../snippets/csharp/VS_Snippets_VSSDK/buttongroup/cs/buttongrouppackage.cs#22)]  
  
     Visual Studio balíček šablony obsahuje dvě kolekce `GuidList` a `PkgCmdIDList`, k uložení identifikátory GUID a ID příkazů. Ty se automaticky vyplní pro příkazy, které jsou přidány pomocí šablony, ale pro příkazy, které přidáváte ručně, je nutné přidat také ID položky, která má `PkgCmdIdList` třídy.  
  
     Alternativně můžete naplnit <xref:System.ComponentModel.Design.CommandID> s použitím nezpracované řetězcové hodnoty GUID a celočíselnou hodnotu ID.  
  
3.  Vytvořit instanci buď <xref:System.ComponentModel.Design.MenuCommand> nebo <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> objekt, který určuje metodu, která zpracovává příkaz spolu s <xref:System.ComponentModel.Design.CommandID>, jak je znázorněno v následujícím příkladu.  
  
     [!code-csharp[ButtonGroup#23](../snippets/csharp/VS_Snippets_VSSDK/buttongroup/cs/buttongrouppackage.cs#23)]  
  
     <xref:System.ComponentModel.Design.MenuCommand> Je vhodný pro statické příkazy. Dynamické nabídky zobrazí položky vyžadují QueryStatus obslužných rutin událostí. <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> Přidá <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus> událost, která nastane, pokud se nabídka hostitelů příkazu je otevřený a některé další vlastnosti, jako například <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.Text%2A>.  
  
     Ve výchozím nastavení jsou předány příkazy vytvořené z balíčku šablony <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> objekt `Initialize()` metoda třídy balíčku.  
  
4.  <xref:System.ComponentModel.Design.MenuCommand> Je vhodný pro statické příkazy. Dynamické nabídky zobrazí položky vyžadují QueryStatus obslužných rutin událostí. <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> Přidá <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus> událost, která nastane, pokud se nabídka hostitelů příkazu je otevřený a některé další vlastnosti, jako například <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.Text%2A>.  
  
     Ve výchozím nastavení jsou předány příkazy vytvořené z balíčku šablony <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> objekt `Initialize()` metoda třídy balíčku. Průvodce Visual Studio implementuje `Initialize` metoda pomocí `MenuCommand`. Dynamické nabídky zobrazí položky, je třeba změnit tuto hodnotu na `OleMenuCommand`, jak je znázorněno v následujícím kroku. Navíc pokud chcete změnit text položky nabídky, musíte přidat příkaz příznak TextChanges na příkazové tlačítko nabídky v souboru .vsct jak je znázorněno v následujícím příkladu  
  
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
      
5.  Předejte nový příkaz nabídky <xref:System.ComponentModel.Design.IMenuCommandService.AddCommand%2A> metodu <xref:System.ComponentModel.Design.IMenuCommandService> rozhraní. To lze provést ve výchozím nastavení pro příkazy vytvořených šablonou balíček, jak je znázorněno v následujícím příkladu  
  
     [!code-csharp[ButtonGroup#24](../snippets/csharp/VS_Snippets_VSSDK/buttongroup/cs/buttongrouppackage.cs#24)]  
  
6.  Implementujte metodu, která zpracovává příkaz.  
  
#### <a name="to-implement-querystatus"></a>K implementaci QueryStatus  
  
1. Událost QueryStatus proběhne před zobrazením příkazu. Toto umožňuje vlastnostem nastavit v obslužné rutiny předtím, než uživatel dosáhne příkazu. Jenom příkazy, které jsou přidány jako <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> objektů můžete přístup k této metodě.  
  
    Přidat `EventHandler` objektu <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus> událost v <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> objekt, který je vytvořen pro zpracování příkazu, jak je znázorněno v následujícím příkladu (`menuItem` je <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> instance).  
  
    [!code-csharp[MenuText#14](../snippets/csharp/VS_Snippets_VSSDK/menutext/cs/menutextpackage.cs#14)]
    [!code-vb[MenuText#14](../snippets/visualbasic/VS_Snippets_VSSDK/menutext/vb/menutextpackage.vb#14)]  
  
    `EventHandler` Objektu je přiřazen název metody, která je volána, když je dotazován stav příkazu nabídky.  
  
2. Implementujte metodu dotazu stav obslužné rutiny příkazu. `object` `sender` Může být parametr převeden <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> objektu, který se používá k nastavení různé atributy příkaz nabídky, včetně textu. V následující tabulce jsou uvedeny vlastnosti na <xref:System.ComponentModel.Design.MenuCommand> třídy (které třídu MPF <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> je odvozen od), které odpovídají <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF> příznaky.  
  
   |Vlastnost nabídka – příkaz|Příznak OLECMDF|  
   |--------------------------|------------------|  
   |<xref:System.ComponentModel.Design.MenuCommand.Checked%2A> = `true`|<xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF>|  
   |<xref:System.ComponentModel.Design.MenuCommand.Visible%2A> = `false`|<xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF>|  
   |<xref:System.ComponentModel.Design.MenuCommand.Enabled%2A> = `true`|<xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF>|  
  
    Ke změně textu příkazu nabídky, použijte <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.Text%2A> vlastnost <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> objektu, jak je znázorněno v následujícím příkladu.  
  
    [!code-csharp[MenuText#11](../snippets/csharp/VS_Snippets_VSSDK/menutext/cs/menutextpackage.cs#11)]
    [!code-vb[MenuText#11](../snippets/visualbasic/VS_Snippets_VSSDK/menutext/vb/menutextpackage.vb#11)]  
  
   MPF automaticky zpracovává případ skupiny neznámý nebo nepodporovaný. Pokud příkaz byl přidán do <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService> pomocí <xref:System.ComponentModel.Design.IMenuCommandService.AddCommand%2A> metoda, příkaz se nepodporuje.  
  
### <a name="handling-commands-by-using-the-iolecommandtarget-interface"></a>Zpracování příkazů pomocí iolecommandtarget – rozhraní  
 Pro kód, který se používá <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> přímo rozhraní, sady VSPackage musí implementovat obě <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> a <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> metody <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> rozhraní. Pokud sady VSPackage implementuje hierarchii projektu <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> a <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A> metody <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> rozhraní by měla být implementována místo.  
  
 Jak <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> a <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> metody jsou navrženy pro příjem jediný příkaz set `GUID` a pole ID příkazů jako vstup. Doporučujeme vám, že rozšíření VSPackages plně podporují tento koncept víc ID v jednom volání. Nicméně, tak dlouho, dokud VSPackage není volána z jiných balíčků VSPackage, můžete předpokládat, že příkaz pole obsahuje pouze jedno ID příkazu, protože <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> a <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> metody jsou provedeny v dobře definovaných pořadí. Další informace o směrování najdete v tématu [směrování příkazů v balíčcích VSPackage](../extensibility/internals/command-routing-in-vspackages.md).  
  
 Pro kód, který se používá <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> rozhraní přímo pro zpracování příkazů, je nutné implementovat <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> metoda v balíčku VSPackage pro zpracování příkazů.  
  
##### <a name="to-implement-the-querystatus-method"></a>K implementaci QueryStatus – metoda  
  
1. Vrátí <xref:Microsoft.VisualStudio.VSConstants.S_OK> pro platné příkazy.  
  
2. Nastavte `cmdf` elementu `prgCmds` parametru.  
  
    Hodnota `cmdf` element je logické sjednocení hodnot z <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF> výčet kombinovat pomocí logické OR (`|`) – operátor.  
  
    Použijte příslušné výčet, na základě stavu příkazu:  
  
   - Pokud se příkaz podporuje:  
  
      `prgCmds[0].cmdf = OLECMDF_SUPPORTED;`  
  
   - Pokud v tuto chvíli by měl být neviditelné příkazu:  
  
      `prgCmds[0].cmdf |= OLECMDF_INVISIBLE;`  
  
   - Pokud příkaz je zapnutá a zdá se, kliknul během:  
  
      `prgCmds[0].cmdf |= OLECMDF_LATCHED;`  
  
      V případě zpracování příkazů, které jsou hostované v nabídce Typ `MenuControllerLatched`, první příkaz, který je označen `OLECMDF_LATCHED` příznak je výchozí příkaz, který se zobrazí při spuštění v nabídce. Další informace o `MenuController` naleznete v tématu typy nabídek [Menu Element](../extensibility/menu-element.md).  
  
   - Pokud příkaz je aktuálně povoleno:  
  
      `prgCmds[0].cmdf |= OLECMDF_ENABLED;`  
  
   - Pokud příkaz je součástí místní nabídce a je ve výchozím nastavení skryje:  
  
      `prgCmds[0] cmdf |= OLECMDF_DEFHIDEONCTXMENU`  
  
   - Pokud příkaz používá `TEXTCHANGES` příznak, nastavte `rgwz` elementu `pCmdText` parametr nového textu příkazu a sady `cwActual` elementu `pCmdText` parametr velikosti řetězec příkazu.  
  
     Pro chybové podmínky <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> metoda musí zpracovat tyto případy chyb:  
  
   - Pokud identifikátor GUID je neznámý nebo není podporován, vrátí `OLECMDERR_E_UNKNOWNGROUP`.  
  
   - Pokud je známý identifikátor GUID, ale ID příkazu, který je neznámý nebo není podporována, vrátit `OLECMDERR_E_NOTSUPPORTED`.  
  
   Implementace VSPackage <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> metoda musí vracet také konkrétních kódech chyb, v závislosti na tom, zda je příkaz podporován a určuje, zda příkaz byl úspěšně zpracován.  
  
##### <a name="to-implement-the-exec-method"></a>K implementaci Exec – metoda  
  
-   Pokud příkaz `GUID` neznámý, vrátí `OLECMDERR_E_UNKNOWNGROUP`.  
  
-   Pokud `GUID` je známé, ale příkaz ID neznámý, vraťte `OLECMDERR_E_NOTSUPPORTED`.  
  
-   Pokud `GUID` a ID odpovídat GUID:ID pár, který se používá v příkazu v souboru .vsct, spusťte příkaz kódu, který je přidružený k příkazu a vrátit <xref:Microsoft.VisualStudio.VSConstants.S_OK>.  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace schématu VSCT XML](../extensibility/vsct-xml-schema-reference.md)   
 [Rozšiřování nabídek a příkazů](../extensibility/extending-menus-and-commands.md)