---
title: Vytváření obsahu. Soubory Vsct | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSCT files, manual authoring
ms.assetid: e9f715dc-12b7-439b-bdf3-f3dc75e62f1c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 26a5353531d997ad40b913b5ee223614d6517c55
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49917807"
---
# <a name="author-vsct-files"></a>Vytváření souborů .vsct
Tento dokument ukazuje, jak vytvářet *.vsct* soubor k přidání položek nabídky, panely nástrojů a jiných prvcích uživatelského rozhraní (UI) do integrovaného vývojového prostředí (IDE) sady Visual Studio. Pomocí těchto kroků při přidávání prvků uživatelského rozhraní do balíčku sady Visual Studio (balíček VSPackage správy kódu), který ještě není *.vsct* souboru.  
  
 Pro nové projekty, doporučujeme použít balíček šablony sady Visual Studio, protože ji vygeneruje *.vsct* soubor, který v závislosti na výběrech, už má požadované elementy pro příkaz nabídky, okna nástroje nebo vlastní editor . Tuto hodnotu můžete změnit *.vsct* souboru podle požadavků vašeho balíčku VSPackage. Další informace o tom, jak upravit *.vsct* souboru, podívejte se na příklady v [rozšířit nabídek a příkazů](../../extensibility/extending-menus-and-commands.md).  
  
## <a name="author-the-file"></a>Vytvořte soubor  
 Autor *.vsct* souboru v těchto fází: vytvořte strukturu souborů a prostředků, deklarace prvků uživatelského rozhraní, vložit prvky uživatelského rozhraní v rozhraní IDE a přidejte specializované neovlivní žádné chování.  
  
### <a name="file-structure"></a>Struktura souborů  
 Základní struktura *.vsct* soubor je [commandtable –](../../extensibility/commandtable-element.md) kořenový element, který obsahuje [příkazy](../../extensibility/commands-element.md) elementu a [symboly](../../extensibility/symbols-element.md) elementu.  
  
#### <a name="to-create-the-file-structure"></a>Chcete-li vytvořit strukturu souborů  
  
1.  Přidat *.vsct* soubor do projektu pomocí následujících kroků v [postupy: vytvoření souboru .vsct](../../extensibility/internals/how-to-create-a-dot-vsct-file.md).  
  
2. Přidejte požadované obory názvů `CommandTable` elementu, jak je znázorněno v následujícím příkladu:  
  
    ```xml  
    <CommandTable xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable"   
        xmlns:xs="http://www.w3.org/2001/XMLSchema">  
  
    ```  
  
3.  V `CommandTable` elementu, přidejte `Commands` – element pro hostování všech vlastních nabídkami, panely nástrojů, skupin a příkazy. Tak, aby vaše vlastní elementy uživatelského rozhraní můžete načíst, `Commands` element musí mít jeho `Package` atribut nastaven na hodnotu názvu balíčku.  
  
     Po `Commands` elementu, přidejte `Symbols` element definovat identifikátory GUID pro balíček a názvy a identifikátory příkazů prvků uživatelského rozhraní.  
  
### <a name="include-visual-studio-resources"></a>Zahrnout prostředky sady Visual Studio  
 Použití [Extern](../../extensibility/extern-element.md) – element pro přístup k souborům, které definují příkazy sady Visual Studio a nabídky, které je potřeba vložit vaše prvky uživatelského rozhraní v rozhraní IDE. Pokud budete používat příkazy definované mimo váš balíček, použijte [usedcommands –](../../extensibility/usedcommands-element.md) element informovat sady Visual Studio.  
  
#### <a name="to-include-visual-studio-resources"></a>Chcete zahrnout prostředky sady Visual Studio  
  
1. V horní části `CommandTable` prvku, přidejte jej `Extern` – element pro každé externích souborů se odkazuje, a nastavit `href` atribut pro název souboru. Následující soubory hlaviček pro přístup k prostředkům v sadě Visual Studio může odkazovat:  
  
   -   *Stdidcmd.h*: definuje ID pro všechny příkazy, které jsou vystavené sady Visual Studio.  
  
   -   *Vsshlids.h*: obsahuje ID příkazu pro nabídky sady Visual Studio.  
  
2. Pokud váš balíček volá všechny příkazy, které jsou definovány pomocí sady Visual Studio nebo další balíčky, přidejte `UsedCommands` elementu po `Commands` elementu. Vyplnit tento element s [usedcommand –](../../extensibility/usedcommand-element.md) – element pro každý příkaz, který je volání není součástí vašeho balíčku. Nastavte `guid` a `id` atributy `UsedCommand` prvků, které mají hodnoty GUID a ID příkazů pro volání. 

   Další informace o tom, jak najít identifikátory GUID a ID sady Visual Studio příkazy najdete v tématu [identifikátory GUID a ID sady Visual Studio příkazy](../../extensibility/internals/guids-and-ids-of-visual-studio-commands.md). Pokud chcete volat příkazy z jiných balíčků, použijte identifikátor GUID a ID příkazu, jak jsou definovány v *.vsct* soubor pro tyto balíčky.
  
### <a name="declare-ui-elements"></a>Deklarovat prvky uživatelského rozhraní  
 Všechny nové prvky uživatelského rozhraní v deklaraci `Symbols` část *.vsct* souboru.  
  
#### <a name="to-declare-ui-elements"></a>Chcete-li deklarovat prvky uživatelského rozhraní  
  
1.  V `Symbols` prvku, přidejte tři [guidsymbol –](../../extensibility/guidsymbol-element.md) elementy. Každý `GuidSymbol` obsahuje element `name` atribut a `value` atribut. Nastavte `name` atribut, aby odrážely účel elementu. `value` Atribut má identifikátor GUID. (Generovat identifikátor GUID na **nástroje** nabídce vyberte možnost **Create GUID**a pak vyberte **formát registru**.)  
  
     První `GuidSymbol` element představuje váš balíček a obvykle nemá žádné podřízené položky. Druhá `GuidSymbol` element představuje příkaz nastavit a bude obsahovat všechny symboly, které definují nabídek, skupiny a příkazy. Třetí `GuidSymbol` element představuje vaše úložiště imagí a obsahuje symboly pro všechny ikony pro příkazy. Pokud máte k dispozici žádné příkazy, které používají ikony, můžete vynechat třetí `GuidSymbol` elementu.  
  
2.  V `GuidSymbol` elementu, který představuje vaši sadu příkazů, přidejte jeden nebo více [idsymbol –](../../extensibility/idsymbol-element.md) elementy. Každá z těchto představují nabídky, nástrojů, skupiny nebo příkaz, který chcete přidat do uživatelského rozhraní.  
  
     Pro každou `IDSymbol` element, nastaven `name` atribut název bude odkazovat na odpovídající nabídky, skupiny nebo příkaz a pak nastavte `value` element šestnáctkového čísla, která bude představovat jeho ID příkazu. Žádné dva `IDSymbol` prvky, které mají stejnou nadřazenou položku může mít stejnou hodnotu.  
  
3.  Pokud některý z vašich prvky uživatelského rozhraní vyžadují ikony, přidejte `IDSymbol` – element pro každé ikony `GuidSymbol` elementu, který představuje vaše úložiště imagí.  
  
### <a name="put-ui-elements-in-the-ide"></a>Vložit prvky uživatelského rozhraní v rozhraní IDE  
 [Nabídky](../../extensibility/menus-element.md), [skupiny](../../extensibility/groups-element.md), a [tlačítka](../../extensibility/buttons-element.md) elementy obsahovat definice pro všechny nabídky, skupiny a příkazy, které jsou definovány v balíčku. Do integrovaného vývojového prostředí pomocí těchto nabídek, skupiny a příkazy [nadřazené](../../extensibility/parent-element.md) element, který je součástí definice prvku uživatelského rozhraní nebo pomocí [commandplacement –](../../extensibility/commandplacement-element.md) element, který je definovaný jinde.  
  
 Každý `Menu`, `Group`, a `Button` obsahuje element `guid` atribut a `id` atribut. Vždycky nastavený `guid` atribut shodovat s názvem `GuidSymbol` elementu, který představuje váš příkaz nastavit a nastavit `id` atribut název `IDSymbol` elementu, který představuje vaše nabídky, skupinu nebo příkaz `Symbols`oddílu.  
  
#### <a name="to-define-ui-elements"></a>Chcete-li definovat prvky uživatelského rozhraní  
  
1. Pokud definujete nové nabídky, podnabídky, místní nabídky nebo panely nástrojů, přidejte `Menus` elementu `Commands` element. Pak pro jednotlivé nabídky, který se má vytvořit, přidejte [nabídky](../../extensibility/menu-element.md) element `Menus` element.  
  
    Nastavte `guid` a `id` atributy `Menu` element a pak nastavte `type` atribut na typ, který chcete nabídky. Můžete také nastavit `priority` atribut vytvořit relativní umístění v nabídce v nadřazené skupině.  
  
   > [!NOTE]
   >  `priority` Atribut se nedá použít u kontextové nabídky a panely nástrojů.  
  
2. Všechny příkazy v integrovaném vývojovém prostředí sady Visual Studio musí být hostovány příkaz skupin, které jsou přímo podřízené nabídek a panelů nástrojů. Pokud přidáváte nové nabídky nebo panely nástrojů rozhraní IDE, tyto musí obsahovat novou skupinu příkazů. Můžete také přidat skupinu příkazů do existující nabídky a panely nástrojů tak, aby vaše příkazy můžete vizuálně seskupit.  
  
    Když přidáte novou skupinu příkazů, musíte nejdřív vytvořit `Groups` prvek a potom přidejte do ní [skupiny](../../extensibility/group-element.md) – element pro každou skupinu příkazů.  
  
    Nastavte `guid` a `id` atributy každého `Group` element a pak nastavte `priority` atribut vytvořit relativní pozici v nabídce nadřazené skupiny. Další informace najdete v tématu [vytváření znovu použitelných skupin tlačítek](../../extensibility/creating-reusable-groups-of-buttons.md).  
  
3. Pokud přidáváte nové příkazy rozhraní IDE, přidejte `Buttons` elementu `Commands` elementu. Pak pro každý příkaz, přidejte [tlačítko](../../extensibility/button-element.md) elementu `Buttons` element.  
  
   1.  Nastavte `guid` a `id` atributy každého `Button` element a pak nastavte `type` atribut na typ, který chcete tlačítko. Můžete také nastavit `priority` atribut vytvořit relativní pozici příkazu v nadřazené skupině.  
  
       > [!NOTE]
       >  Použití `type="button"` pro standardní příkazy a tlačítka na panely nástrojů.  
  
   2.  V `Button` elementu, přidat [řetězce](../../extensibility/strings-element.md) element, který obsahuje [ButtonText](../../extensibility/buttontext-element.md) elementu a [CommandName](../../extensibility/commandname-element.md) elementu. `ButtonText` Element poskytuje textový popisek pro položku nabídky nebo popisu tlačítka pro tlačítko toolbar. `CommandName` Element poskytuje název příkazu, pro použití v příkazu dobře.  
  
   3.  Pokud váš příkaz ikonu, vytvořte [ikonu](../../extensibility/icon-element.md) element v `Button` elementu a nastavte jeho `guid` a `id` atributů `Bitmap` – element pro ikonu.  
  
       > [!NOTE]
       >  Tlačítka panelu nástrojů musí mít ikony.  
  
   Další informace najdete v tématu [MenuCommands vs. OleMenuCommands](../../extensibility/menucommands-vs-olemenucommands.md).  
  
4. Pokud některý z vašich příkazů vyžadují ikony, přidejte [rastrové obrázky](../../extensibility/bitmaps-element.md) elementu `Commands` elementu. Obnovte pro jednotlivé ikony [rastrový obrázek](../../extensibility/bitmap-element.md) elementu `Bitmaps` elementu. To je, kde zadáte umístění prostředku rastrového obrázku. Další informace najdete v tématu [přidání ikon k příkazům nabídky](../../extensibility/adding-icons-to-menu-commands.md).  
  
   Můžete se spolehnout na struktuře vztahy k nadřazeným položkám správně umístit Většina nabídek, skupiny a příkazy. Pro příkaz velmi velké sady nebo když nabídky, skupiny nebo příkazu musí být uvedena na více místech, doporučujeme, že zadáte příkaz umístění.  
  
#### <a name="to-rely-on-parenting-to-place-ui-elements-in-the-ide"></a>Chcete-li využívají vztahy k nadřazeným položkám umístí prvky uživatelského rozhraní v rozhraní IDE  
  
1. Pro typické vztahy k nadřazeným položkám, vytvořte `Parent` element v každé `Menu`, `Group`, a `Command` element, který je definován v balíčku.  
  
    Cílem `Parent` je prvek nabídky nebo skupinu, která bude obsahovat nabídky, skupiny nebo příkaz.  
  
   1.  Nastavte `guid` atribut název `GuidSymbol` element, který definuje sadu příkazů. Pokud cílový element není součástí vašeho balíčku, použijte identifikátor guid tuto sadu příkazů, jak jsou definovány v odpovídající *.vsct* souboru.  
  
   2.  Nastavte `id` atribut tak, aby odpovídaly `id` atribut target nabídky nebo skupiny. Seznam nabídek a skupiny, které jsou přístupné pomocí sady Visual Studio, naleznete v tématu [identifikátory GUID a ID sady Visual Studio nabídky](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md) nebo [identifikátory GUID a ID sady Visual Studio panely nástrojů](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md).  
  
   Pokud máte velký počet prvků uživatelského rozhraní, umístíte do integrovaného vývojového prostředí, nebo pokud máte prvky, které by se měla objevit na více místech, definovat jejich umístění v [commandplacements –](../../extensibility/commandplacements-element.md) elementu, jak je znázorněno v následujícím postupu.  
  
#### <a name="to-use-command-placement-to-place-ui-elements-in-the-ide"></a>Použití příkazu umístění umístí prvky uživatelského rozhraní v rozhraní IDE  
  
1. Po `Commands` elementu, přidejte `CommandPlacements` elementu.  
  
2. V `CommandPlacements` elementu, přidejte `CommandPlacement` – element pro každou nabídku, skupinu nebo příkaz umístit.  
  
    Každý `CommandPlacement` element nebo `Parent` element umístí jednu nabídku, skupinu nebo příkaz na jednom místě integrovaného vývojového prostředí. Prvek uživatelského rozhraní může mít pouze jednu nadřazenou položku, ale může mít více umístění příkazu. Umístit do víc umístění prvku uživatelského rozhraní, přidejte `CommandPlacement` – element pro každé umístění.  
  
3. Nastavte `guid` a `id` atributy každého `CommandPlacement` element hostování nabídky nebo skupině, stejně jako by pro `Parent` elementu. Můžete také nastavit `priority` atribut vytvořit relativní pozice prvku uživatelského rozhraní.  
  
   Můžete kombinovat umístění podle vztahy k nadřazeným položkám a příkaz umístění. Pro příkaz velmi velké sady, ale doporučujeme použít pouze příkaz umístění.  
  
### <a name="add-specialized-behaviors"></a>Přidejte specializované chování  
 Můžete použít [CommandFlag](../../extensibility/command-flag-element.md) elementu, jestliže chcete upravit chování nabídek a příkazů, například, chcete-li změnit jejich vzhled a viditelnost. Může také ovlivnit, pokud je příkaz viditelný pomocí [visibilityconstraints –](../../extensibility/visibilityconstraints-element.md) element, nebo přidat pomocí klávesové zkratky [klávesové zkratky](../../extensibility/keybindings-element.md) elementu. Určité typy nabídek a příkazů již vestavěné chování specializovaný.  
  
#### <a name="to-add-specialized-behaviors"></a>Chcete-li přidat specializované chování  
  
1. Chcete-li prvek uživatelského rozhraní viditelná pouze v určitých uživatelského rozhraní kontextech, například při načtení řešení, použijte omezení viditelnosti.  
  
   1.  Po `Commands` elementu, přidejte `VisibilityConstraints` elementu.  
  
   2.  Pro každou položku uživatelského rozhraní pro omezení, přidejte [visibilityitem –](../../extensibility/visibilityitem-element.md) elementu.  
  
   3.  Pro každou `VisibilityItem` element, nastaven `guid` a `id` atributů, které mají v nabídce, skupiny, nebo příkaz a pak nastavte `context` atribut kontextu uživatelského rozhraní, který chcete, jak jsou definovány v <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80> třídy.   
  
2. Pokud chcete nastavit viditelnost nebo dostupnost položky uživatelského rozhraní v kódu, použijte nejméně jeden z následujících příznaků příkazů:  
  
   -   `DefaultDisabled`
  
   -   `DefaultInvisible`
  
   -   `DynamicItemStart` 
  
   -   `DynamicVisibility`
  
   -   `NoShowOnMenuController`
  
   -   `NotInTBList`
  
   Další informace najdete v tématu [CommandFlag](../../extensibility/command-flag-element.md) elementu.  
  
3. Chcete-li změnit způsob, jakým se zobrazí element nebo dynamicky měnit její vzhled, použijte jednu nebo více z následujících příznaků příkazů:  
  
   -   `AlwaysCreate`  
  
   -   `CommandWellOnly`  
  
   -   `DefaultDocked`  
  
   -   `DontCache`  
  
   -   `DynamicItemStart`  
  
   -   `FixMenuController`  
  
   -   `IconAndText`  
  
   -   `Pict`  
  
   -   `StretchHorizontally`  
  
   -   `TextMenuUseButton`  
  
   -   `TextChanges`  
  
   -   `TextOnly`  
  
   Další informace najdete v tématu [CommandFlag](../../extensibility/command-flag-element.md) elementu.  
  
4. Chcete-li změnit, jak prvek reaguje při přijetí příkazů, použijte nejméně jeden z následujících příznaků příkazů:  
  
   -   `AllowParams`  
  
   -   `CaseSensitive`  
  
   -   `CommandWellOnly`  
  
   -   `FilterKeys`  
  
   -   `NoAutoComplete`  
  
   -   `NoButtonCustomize`  
  
   -   `NoKeyCustomize`  
  
   -   `NoToolbarClose`  
  
   -   `PostExec`  
  
   -   `RouteToDocs`  
  
   -   `TextIsAnchorCommand`  
  
   Další informace najdete v tématu [CommandFlag](../../extensibility/command-flag-element.md) elementu.  
  
5. Závislé nabídky klávesové zkratky připojit k nabídky nebo položky v nabídce, přidat znak ampersand (&) v `ButtonText` – element pro nabídky nebo položky nabídky. Znak, který následuje ampersand je aktivní klávesové zkratky při otevření nadřazené nabídky.  
  
6. Chcete-li připojit nezávislé na nabídku klávesovou zkratku k příkazu, použijte [klávesové zkratky](../../extensibility/keybindings-element.md) elementu. Další informace najdete v tématu [klávesové zkratky](../../extensibility/keybinding-element.md) elementu.  
  
7. Chcete-li lokalizovat text nabídky, použijte `LocCanonicalName` elementu. Další informace najdete v tématu [řetězce](../../extensibility/strings-element.md) elementu.  
  
   Některé typy nabídek a tlačítko zahrnovat specializovaná chování. Následující seznam popisuje některé speciální nabídky a typy tlačítek. U jiných typů, najdete v článku `types` popisy v atributu [nabídky](../../extensibility/menu-element.md), [tlačítko](../../extensibility/button-element.md), a [– pole se seznamem](../../extensibility/combo-element.md) elementy.  
  
   - Pole se seznamem:  
   Pole se seznamem je rozevírací seznam, který jde použít na panelu nástrojů. Pokud chcete přidat pole se seznamem v uživatelském rozhraní, vytvořte [combos –](../../extensibility/combos-element.md) prvek `Commands` elementu. Obnovte `Combos` element `Combo` – element pro každé pole se seznamem pro přidání. `Combo` elementy mají stejné atributy a podřízené objekty jako `Button` elementy a můžou taky `DefaultWidth` a `idCommandList` atributy. `DefaultWidth` Atribut nastavuje šířku v pixelech a `idCommandList` atribut body pro ID příkazu, který se používá k naplnění pole se seznamem. 
  
   - Kontroleru nabídky:  
   Kontroleru nabídky je tlačítko, které má šipku vedle sebe. Kliknutím na šipku otevřete seznam. Přidání kontroleru nabídky do uživatelského rozhraní, vytvořit `Menu` elementu a nastavte jeho `type` atribut `MenuController` nebo `MenuControllerLatched`, v závislosti na chování, které chcete. K naplnění kontroleru nabídky, nastavte ji jako nadřazený `Group` elementu. Kontroleru nabídky se zobrazí všechny podřízené dané skupiny v rozevíracím seznamu.  
  
## <a name="see-also"></a>Viz také:  
 [Rozšíření nabídek a příkazů](../../extensibility/extending-menus-and-commands.md)   
 [Soubory tabulky (.vsct) příkaz pro Visual Studio](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)   
 [Referenční dokumentace schématu VSCT XML](../../extensibility/vsct-xml-schema-reference.md)