---
title: Zdroj. Soubory vsct | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT files, manual authoring
ms.assetid: e9f715dc-12b7-439b-bdf3-f3dc75e62f1c
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 82960de02c43a7c4002e189d573a914bb2a73f20
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2019
ms.locfileid: "73186650"
---
# <a name="author-vsct-files"></a>Soubory Author. vsct
Tento dokument ukazuje, jak vytvořit soubor *. vsct* pro přidání položek nabídky, panelů nástrojů a dalších prvků uživatelského rozhraní (UI) do integrovaného vývojového prostředí (IDE) sady Visual Studio. Tyto kroky použijte při přidávání prvků uživatelského rozhraní do balíčku sady Visual Studio (VSPackage), který ještě nemá soubor *. vsct* .

 Pro nové projekty doporučujeme použít šablonu balíčku sady Visual Studio, protože vygeneruje soubor *. vsct* , který v závislosti na vašich volbách již obsahuje požadované prvky pro příkaz nabídky, panel nástrojů nebo vlastní editor. Tento soubor *. vsct* můžete upravit tak, aby splňoval požadavky sady VSPackage. Další informace o tom, jak upravit soubor *. vsct* , najdete v příkladech v tématu [rozšířené nabídky a příkazy](../../extensibility/extending-menus-and-commands.md).

## <a name="author-the-file"></a>Vytvořit soubor
 Vytvořte soubor *. vsct* v těchto fázích: Vytvořte strukturu pro soubory a prostředky, deklarujte prvky uživatelského rozhraní, vložte prvky uživatelského rozhraní do integrovaného vývojového prostředí a přidejte jakékoli specializované chování.

### <a name="file-structure"></a>Struktura souborů
 Základní struktura souboru *. vsct* je kořenový prvek [příkazu](../../extensibility/commandtable-element.md) , který obsahuje element Commands a symbol [elementu.](../../extensibility/commands-element.md) [](../../extensibility/symbols-element.md)

#### <a name="to-create-the-file-structure"></a>Vytvoření struktury souborů

1. Pomocí kroků v tématu [Postup: vytvoření souboru. vsct](../../extensibility/internals/how-to-create-a-dot-vsct-file.md)do projektu přidejte soubor *. vsct* .

2. Přidejte požadované obory názvů do prvku `CommandTable`, jak je znázorněno v následujícím příkladu:

    ```xml
    <CommandTable xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable"
        xmlns:xs="http://www.w3.org/2001/XMLSchema">

    ```

3. V elementu `CommandTable` přidejte `Commands` prvek pro hostování všech vlastních nabídek, panelů nástrojů, skupin příkazů a příkazů. Aby bylo možné načíst vlastní prvky uživatelského rozhraní, musí mít `Commands` element svůj atribut `Package` nastaven na název balíčku.

     Po elementu `Commands` přidejte prvek `Symbols` pro definování identifikátorů GUID balíčku a názvy a ID příkazů pro prvky uživatelského rozhraní.

### <a name="include-visual-studio-resources"></a>Zahrnutí prostředků sady Visual Studio
 Použijte prvek [extern](../../extensibility/extern-element.md) pro přístup k souborům, které definují příkazy sady Visual Studio, a nabídek, které jsou požadovány pro vložení prvků uživatelského rozhraní do integrovaného vývojového prostředí (IDE). Pokud budete používat příkazy definované mimo váš balíček, použijte k informování sady Visual Studio element [UsedCommands](../../extensibility/usedcommands-element.md) .

#### <a name="to-include-visual-studio-resources"></a>Zahrnutí prostředků sady Visual Studio

1. V horní části prvku `CommandTable` přidejte jeden `Extern` element pro každý externí soubor, který se má odkazovat, a nastavte atribut `href` na název souboru. Pro přístup k prostředkům sady Visual Studio můžete odkazovat na následující soubory hlaviček:

   - *Stdidcmd. h*: definuje ID pro všechny příkazy zveřejněné v aplikaci Visual Studio.

   - *Vsshlids. h*: obsahuje ID příkazů pro nabídky sady Visual Studio.

2. Pokud balíček volá jakékoli příkazy, které jsou definovány v aplikaci Visual Studio nebo jinými balíčky, přidejte prvek `UsedCommands` za `Commands` prvek. Naplňte tento prvek elementem [UsedCommand](../../extensibility/usedcommand-element.md) pro každý příkaz, který zavoláte, který není součástí vašeho balíčku. Nastavte atributy `guid` a `id` prvků `UsedCommand` na hodnoty GUID a ID příkazů, které se mají volat.

   Další informace o tom, jak najít identifikátory GUID a ID příkazů sady Visual Studio, naleznete v tématu [GUID a ID příkazů sady Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-commands.md). Chcete-li volat příkazy z jiných balíčků, použijte identifikátor GUID a ID příkazu, jak je definováno v souboru *. vsct* pro tyto balíčky.

### <a name="declare-ui-elements"></a>Deklarovat prvky uživatelského rozhraní
 Deklaruje všechny nové prvky uživatelského rozhraní v části `Symbols` souboru *. vsct* .

#### <a name="to-declare-ui-elements"></a>Deklarace prvků uživatelského rozhraní

1. V elementu `Symbols` přidejte tři elementy [GuidSymbol](../../extensibility/guidsymbol-element.md) . Každý element `GuidSymbol` má atribut `name` a atribut `value`. Nastavte atribut `name` tak, aby odrážel účel elementu. Atribut `value` přijímá identifikátor GUID. (Pokud chcete vygenerovat GUID, v nabídce **nástroje** vyberte **vytvořit GUID**a pak zvolte **Formát registru**.)

     První prvek `GuidSymbol` reprezentuje váš balíček a obvykle nemá žádné podřízené položky. Druhý prvek `GuidSymbol` představuje sadu příkazů a bude obsahovat všechny symboly, které definují nabídky, skupiny a příkazy. Třetí `GuidSymbol` element představuje úložiště imagí a obsahuje symboly pro všechny ikony pro příkazy. Pokud nemáte žádné příkazy, které používají ikony, můžete vynechat třetí prvek `GuidSymbol`.

2. V prvku `GuidSymbol`, který představuje sadu příkazů, přidejte jeden nebo více elementů [IDSymbol](../../extensibility/idsymbol-element.md) . Každé z nich představuje nabídku, panel nástrojů, skupinu nebo příkaz, které přidáváte do uživatelského rozhraní.

     Pro každý prvek `IDSymbol` nastavte atribut `name` na název, který budete používat pro odkaz na odpovídající nabídku, skupinu nebo příkaz, a pak nastavte prvek `value` na hexadecimální číslo, které bude představovat jeho ID příkazu. Žádné dva prvky `IDSymbol`, které mají stejnou nadřazenou položku, mohou mít stejnou hodnotu.

3. Pokud některý z prvků uživatelského rozhraní vyžaduje ikony, přidejte `IDSymbol` element pro každou ikonu do `GuidSymbol` elementu, který představuje úložiště imagí.

### <a name="put-ui-elements-in-the-ide"></a>Vložení prvků uživatelského rozhraní do integrovaného vývojového prostředí
 [Nabídky](../../extensibility/menus-element.md), [skupiny](../../extensibility/groups-element.md)a [tlačítka](../../extensibility/buttons-element.md) obsahují definice všech nabídek, skupin a příkazů, které jsou definovány v balíčku. Tyto nabídky, skupiny a příkazy v integrovaném vývojovém prostředí vložte buď pomocí [nadřazeného](../../extensibility/parent-element.md) elementu, který je součástí definice prvku uživatelského rozhraní, nebo pomocí elementu [CommandPlacement](../../extensibility/commandplacement-element.md) , který je definován jinde.

 Každý prvek `Menu`, `Group`a `Button` má atribut `guid` a atribut `id`. Vždy nastavte atribut `guid` tak, aby odpovídal názvu `GuidSymbol` elementu, který představuje sadu příkazů, a nastavte atribut `id` na název `IDSymbol` prvku, který představuje vaši nabídku, skupinu nebo příkaz v sekci `Symbols`.

#### <a name="to-define-ui-elements"></a>Definování prvků uživatelského rozhraní

1. Pokud definujete nové nabídky, podnabídky, místní nabídky nebo panely nástrojů, přidejte `Menus` element do prvku `Commands`. Pak pro každou nabídku, která má být vytvořena, přidejte prvek [nabídky](../../extensibility/menu-element.md) do prvku `Menus`.

    Nastavte atributy `guid` a `id` elementu `Menu` a pak nastavte atribut `type` na požadovaný druh nabídky. Můžete také nastavit atribut `priority` pro vytvoření relativní pozice nabídky v nadřazené skupině.

   > [!NOTE]
   > Atribut `priority` se nevztahuje na panely nástrojů a kontextové nabídky.

2. Všechny příkazy v integrovaném vývojovém prostředí sady Visual Studio musí být hostované skupinami příkazů, které jsou přímými podřízenými položkami nabídek a panelů nástrojů. Pokud přidáváte nové nabídky nebo panely nástrojů do integrovaného vývojového prostředí (IDE), musí obsahovat nové skupiny příkazů. Můžete také přidat skupiny příkazů do stávajících nabídek a panelů nástrojů, abyste mohli příkazy vizuálně seskupit.

    Když přidáte nové skupiny příkazů, musíte nejprve vytvořit prvek `Groups` a pak ho přidat do [skupiny](../../extensibility/group-element.md) pro každou skupinu příkazů.

    Nastavte atributy `guid` a `id` každého prvku `Group` a pak nastavte atribut `priority` pro vytvoření relativní pozice skupiny v nadřazené nabídce. Další informace najdete v tématu [vytvoření opakovaně použitelných skupin tlačítek](../../extensibility/creating-reusable-groups-of-buttons.md).

3. Pokud přidáváte nové příkazy do integrovaného vývojového prostředí (IDE), přidejte `Buttons` element do prvku `Commands`. Potom pro každý příkaz přidejte element [Button](../../extensibility/button-element.md) do prvku `Buttons`.

   1. Nastavte atributy `guid` a `id` každého prvku `Button` a pak nastavte atribut `type` na typ tlačítka, které chcete. Můžete také nastavit atribut `priority` pro vytvoření relativní pozice příkazu v nadřazené skupině.

       > [!NOTE]
       > Použijte `type="button"` pro standardní příkazy nabídky a tlačítka na panelech nástrojů.

   2. V elementu `Button` přidejte element [strings](../../extensibility/strings-element.md) , který obsahuje element [ButtonText](../../extensibility/buttontext-element.md) a element [Command](../../extensibility/commandname-element.md) . Element `ButtonText` poskytuje textový popisek pro položku nabídky nebo popis tlačítka pro tlačítko panelu nástrojů. Element `CommandName` poskytuje název příkazu, který se má použít ve správném příkazu.

   3. Pokud má váš příkaz ikonu, vytvořte element [Icon](../../extensibility/icon-element.md) v prvku `Button` a nastavte jeho atributy `guid` a `id` na prvek `Bitmap` pro ikonu.

       > [!NOTE]
       > Tlačítka panelu nástrojů musí mít ikony.

   Další informace najdete v tématu [MenuCommands vs. OleMenuCommands](/visualstudio/extensibility/menucommands-vs-olemenucommands?view=vs-2015).

4. Pokud některý z příkazů vyžaduje ikony, přidejte prvek [rastry](../../extensibility/bitmaps-element.md) do prvku `Commands`. Pak pro každou ikonu přidejte prvek [rastrového obrázku](../../extensibility/bitmap-element.md) do prvku `Bitmaps`. Tady můžete zadat umístění prostředku rastrového obrázku. Další informace najdete v tématu [Přidání ikon do příkazů nabídky](../../extensibility/adding-icons-to-menu-commands.md).

   Můžete spoléhat na nadřazenou strukturu a správně umístit většinu nabídek, skupin a příkazů. U velmi rozsáhlých sad příkazů nebo v případě, že se na více místech musí zobrazit nabídka, skupina nebo příkaz, doporučujeme zadat umístění příkazů.

#### <a name="to-rely-on-parenting-to-place-ui-elements-in-the-ide"></a>Spoléhání na nadřazenou položku k umístění prvků uživatelského rozhraní v rozhraní IDE

1. V případě typických nadřazených prvků vytvořte `Parent` element v každém elementu `Menu`, `Group`a `Command`, který je definován v balíčku.

    Cílem prvku `Parent` je nabídka nebo skupina, která bude obsahovat nabídku, skupinu nebo příkaz.

   1. Nastavte atribut `guid` na název `GuidSymbol` elementu, který definuje sadu příkazů. Pokud cílový element není součástí vašeho balíčku, použijte identifikátor GUID pro sadu příkazů, jak je definováno v odpovídajícím souboru *. vsct* .

   2. Nastavte atribut `id` tak, aby odpovídal atributu `id` cílové nabídky nebo skupiny. Seznam nabídek a skupin, které jsou zpřístupněny v rámci sady Visual Studio, naleznete v tématu [identifikátory GUID a ID nabídek](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md) nebo [identifikátorů GUID sady Visual Studio a ID panelů nástrojů sady Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md).

   Máte-li v integrovaném vývojovém prostředí (IDE) velký počet prvků uživatelského rozhraní nebo pokud máte prvky, které by měly být zobrazeny na více místech, definujte jejich umístění v prvku [CommandPlacements](../../extensibility/commandplacements-element.md) , jak je znázorněno v následujícím postupu.

#### <a name="to-use-command-placement-to-place-ui-elements-in-the-ide"></a>Použití umístění příkazu k umístění prvků uživatelského rozhraní v integrovaném vývojovém prostředí

1. Po elementu `Commands` přidejte prvek `CommandPlacements`.

2. V elementu `CommandPlacements` přidejte `CommandPlacement` prvek pro každou nabídku, skupinu nebo příkaz.

    Každý prvek `CommandPlacement` nebo prvek `Parent` umístí jednu nabídku, skupinu nebo příkaz v jednom umístění IDE. Prvek uživatelského rozhraní může mít pouze jednu nadřazenou položku, ale může mít více umístění příkazů. Chcete-li umístit prvek uživatelského rozhraní do více umístění, přidejte `CommandPlacement` element pro každé umístění.

3. Nastavte atributy `guid` a `id` každého prvku `CommandPlacement` na nabídku hostování nebo skupinu, stejně jako u prvku `Parent`. Můžete také nastavit atribut `priority` pro vytvoření relativní pozice prvku uživatelského rozhraní.

   Můžete kombinovat umístění pomocí nadřazeného a umístění příkazů. U velmi rozsáhlých sad příkazů ale doporučujeme použít jenom umístění příkazu.

### <a name="add-specialized-behaviors"></a>Přidat specializované chování
 Pomocí elementu [CommandFlag](../../extensibility/command-flag-element.md) můžete změnit chování nabídek a příkazů, například pro změnu jejich vzhledu a viditelnosti. Můžete také ovlivnit, kdy je příkaz viditelný pomocí elementu [VisibilityConstraints](../../extensibility/visibilityconstraints-element.md) , nebo přidat klávesové zkratky pomocí elementu [vazby](../../extensibility/keybindings-element.md) klíčů. Některé druhy nabídek a příkazů již mají integrované specializované chování.

#### <a name="to-add-specialized-behaviors"></a>Přidání specializovaného chování

1. Aby bylo možné prvek uživatelského rozhraní zobrazit pouze v určitých kontextech uživatelského rozhraní, například při načtení řešení, použijte omezení viditelnosti.

   1. Po elementu `Commands` přidejte prvek `VisibilityConstraints`.

   2. Pro každou položku uživatelského rozhraní, která se má omezit, přidejte element [VisibilityItem](../../extensibility/visibilityitem-element.md) .

   3. Pro každý prvek `VisibilityItem` nastavte atributy `guid` a `id` na nabídku, skupinu nebo příkaz a pak nastavte atribut `context` na kontext uživatelského rozhraní, který chcete, jak je definováno ve třídě <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80>.

2. Chcete-li nastavit viditelnost nebo dostupnost položky uživatelského rozhraní v kódu, použijte jeden nebo více následujících příznaků příkazu:

   - `DefaultDisabled`

   - `DefaultInvisible`

   - `DynamicItemStart`

   - `DynamicVisibility`

   - `NoShowOnMenuController`

   - `NotInTBList`

   Další informace naleznete v tématu [CommandFlag](../../extensibility/command-flag-element.md) element.

3. Chcete-li změnit způsob zobrazení prvku nebo změnit jeho vzhled dynamicky, použijte jeden nebo více následujících příznaků příkazu:

   - `AlwaysCreate`

   - `CommandWellOnly`

   - `DefaultDocked`

   - `DontCache`

   - `DynamicItemStart`

   - `FixMenuController`

   - `IconAndText`

   - `Pict`

   - `StretchHorizontally`

   - `TextMenuUseButton`

   - `TextChanges`

   - `TextOnly`

   Další informace naleznete v tématu [CommandFlag](../../extensibility/command-flag-element.md) element.

4. Chcete-li změnit způsob, jakým element reaguje při přijímání příkazů, použijte jeden nebo více následujících příznaků příkazu:

   - `AllowParams`

   - `CaseSensitive`

   - `CommandWellOnly`

   - `FilterKeys`

   - `NoAutoComplete`

   - `NoButtonCustomize`

   - `NoKeyCustomize`

   - `NoToolbarClose`

   - `PostExec`

   - `RouteToDocs`

   - `TextIsAnchorCommand`

   Další informace naleznete v tématu [CommandFlag](../../extensibility/command-flag-element.md) element.

5. Chcete-li připojit klávesovou zkratku závislou na nabídce nebo položku v nabídce, přidejte znak ampersand (&) do prvku `ButtonText` pro položku nabídky nebo položky nabídky. Znak, který následuje za ampersandem, je aktivní klávesová zkratka, pokud je nadřazená nabídka otevřená.

6. Chcete-li k příkazu připojit klávesovou zkratku nezávislou na nabídce, použijte prvek [vazby](../../extensibility/keybindings-element.md) klíčů. Další informace naleznete v tématu elementu [vazby](../../extensibility/keybinding-element.md) klíčů.

7. Chcete-li lokalizovat text nabídky, použijte prvek `LocCanonicalName`. Další informace naleznete v tématu element [strings](../../extensibility/strings-element.md) .

   Některé typy nabídek a tlačítek zahrnují specializované chování. Následující seznam popisuje některé specializované typy nabídek a tlačítek. Další typy naleznete v tématu `types` popisy atributů v [nabídce](../../extensibility/menu-element.md), [tlačítku](../../extensibility/button-element.md)a v prvcích [combo](../../extensibility/combo-element.md) .

   - Pole se seznamem: pole se seznamem je rozevírací seznam, který se dá použít na panelu nástrojů. Chcete-li přidat pole se seznamem do uživatelského rozhraní, vytvořte element [Combos](../../extensibility/combos-element.md) v elementu `Commands`. Pak přidejte do prvku `Combos` prvek `Combo` pro každé pole se seznamem, které chcete přidat. prvky `Combo` mají stejné atributy a podřízené položky jako `Button` prvky a mají také atributy `DefaultWidth` a `idCommandList`. Atribut `DefaultWidth` nastaví šířku v pixelech a atribut `idCommandList` odkazuje na ID příkazu, který se používá k naplnění pole se seznamem.

   - Controller nabídky: kontroler nabídek je tlačítko, které má vedle něj šipku. Kliknutím na šipku se otevře seznam. Chcete-li přidat do uživatelského rozhraní řadič nabídky, vytvořte `Menu` element a nastavte jeho atribut `type` na `MenuController` nebo `MenuControllerLatched`v závislosti na požadovaném chování. Chcete-li naplnit řadič nabídky, nastavte jej jako nadřazený prvek prvku `Group`. Na řadiči nabídky se zobrazí všechny podřízené položky této skupiny v rozevíracím seznamu.

## <a name="see-also"></a>Viz také:
- [Rozšiřování nabídek a příkazů](../../extensibility/extending-menus-and-commands.md)
- [Soubory tabulek příkazů sady Visual Studio (. vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
- [Referenční dokumentace schématu VSCT XML](../../extensibility/vsct-xml-schema-reference.md)