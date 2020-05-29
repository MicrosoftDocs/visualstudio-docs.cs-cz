---
title: Zdroj. Soubory vsct | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT files, manual authoring
ms.assetid: e9f715dc-12b7-439b-bdf3-f3dc75e62f1c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8f02c7ec0e453f0758ba2ab13145fcdff11b442a
ms.sourcegitcommit: d20ce855461c240ac5eee0fcfe373f166b4a04a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/29/2020
ms.locfileid: "84173600"
---
# <a name="author-vsct-files"></a>Soubory Author. vsct
Tento dokument ukazuje, jak vytvořit soubor *. vsct* pro přidání položek nabídky, panelů nástrojů a dalších prvků uživatelského rozhraní (UI) do integrovaného vývojového prostředí (IDE) sady Visual Studio. Tyto kroky použijte při přidávání prvků uživatelského rozhraní do balíčku sady Visual Studio (VSPackage), který ještě nemá soubor *. vsct* .

 Pro nové projekty doporučujeme použít šablonu balíčku sady Visual Studio, protože vygeneruje soubor *. vsct* , který v závislosti na vašich volbách již obsahuje požadované prvky pro příkaz nabídky, panel nástrojů nebo vlastní editor. Tento soubor *. vsct* můžete upravit tak, aby splňoval požadavky sady VSPackage. Další informace o tom, jak upravit soubor *. vsct* , najdete v příkladech v tématu [rozšířené nabídky a příkazy](../../extensibility/extending-menus-and-commands.md).

## <a name="author-the-file"></a>Vytvořit soubor
 Vytvořte soubor *. vsct* v těchto fázích: Vytvořte strukturu pro soubory a prostředky, deklarujte prvky uživatelského rozhraní, vložte prvky uživatelského rozhraní do integrovaného vývojového prostředí a přidejte jakékoli specializované chování.

### <a name="file-structure"></a>Struktura souborů
 Základní struktura souboru *. vsct* je kořenový prvek [příkazu](../../extensibility/commandtable-element.md) , který obsahuje element Commands a symbol [elementu.](../../extensibility/commands-element.md) [Symbols](../../extensibility/symbols-element.md)

#### <a name="to-create-the-file-structure"></a>Vytvoření struktury souborů

1. Pomocí kroků v tématu [Postup: vytvoření souboru. vsct](../../extensibility/internals/how-to-create-a-dot-vsct-file.md)do projektu přidejte soubor *. vsct* .

2. Přidejte požadované obory názvů do `CommandTable` prvku, jak je znázorněno v následujícím příkladu:

    ```xml
    <CommandTable xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable"
        xmlns:xs="http://www.w3.org/2001/XMLSchema">

    ```

3. V `CommandTable` elementu přidejte `Commands` element pro hostování všech vlastních nabídek, panelů nástrojů, skupin příkazů a příkazů. Aby bylo možné načíst vlastní prvky uživatelského rozhraní, `Commands` element musí mít svůj `Package` atribut nastavený na název balíčku.

     Za `Commands` element přidejte `Symbols` element pro definování identifikátorů GUID pro balíček a názvy a ID příkazů pro prvky uživatelského rozhraní.

### <a name="include-visual-studio-resources"></a>Zahrnutí prostředků sady Visual Studio
 Použijte prvek [extern](../../extensibility/extern-element.md) pro přístup k souborům, které definují příkazy sady Visual Studio, a nabídek, které jsou požadovány pro vložení prvků uživatelského rozhraní do integrovaného vývojového prostředí (IDE). Pokud budete používat příkazy definované mimo váš balíček, použijte k informování sady Visual Studio element [UsedCommands](../../extensibility/usedcommands-element.md) .

#### <a name="to-include-visual-studio-resources"></a>Zahrnutí prostředků sady Visual Studio

1. V horní části `CommandTable` elementu přidejte jeden `Extern` element pro každý externí soubor, na který se má odkazovat, a nastavte `href` atribut na název souboru. Pro přístup k prostředkům sady Visual Studio můžete odkazovat na následující soubory hlaviček:

   - *Stdidcmd. h*: definuje ID pro všechny příkazy zveřejněné v aplikaci Visual Studio.

   - *Vsshlids. h*: obsahuje ID příkazů pro nabídky sady Visual Studio.

2. Pokud balíček volá jakékoli příkazy, které jsou definovány v aplikaci Visual Studio nebo jinými balíčky, přidejte `UsedCommands` prvek za `Commands` element. Naplňte tento prvek elementem [UsedCommand](../../extensibility/usedcommand-element.md) pro každý příkaz, který zavoláte, který není součástí vašeho balíčku. Nastavte `guid` atributy a `id` `UsedCommand` prvků na identifikátory GUID a ID příkazů, které mají být volány.

   Další informace o tom, jak najít identifikátory GUID a ID příkazů sady Visual Studio, naleznete v tématu [GUID a ID příkazů sady Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-commands.md). Chcete-li volat příkazy z jiných balíčků, použijte identifikátor GUID a ID příkazu, jak je definováno v souboru *. vsct* pro tyto balíčky.

### <a name="declare-ui-elements"></a>Deklarovat prvky uživatelského rozhraní
 Deklaruje všechny nové prvky uživatelského rozhraní v `Symbols` části souboru *. vsct* .

#### <a name="to-declare-ui-elements"></a>Deklarace prvků uživatelského rozhraní

1. V `Symbols` elementu přidejte tři [GuidSymbol](../../extensibility/guidsymbol-element.md) prvky. Každý `GuidSymbol` element má `name` atribut a `value` atribut. Nastavte `name` atribut tak, aby odrážel účel elementu. `value`Atribut přebírá identifikátor GUID. (Pokud chcete vygenerovat GUID, v nabídce **nástroje** vyberte **vytvořit GUID**a pak zvolte **Formát registru**.)

     První `GuidSymbol` prvek představuje váš balíček a obvykle nemá žádné podřízené položky. Druhý `GuidSymbol` prvek představuje sadu příkazů a bude obsahovat všechny symboly, které definují nabídky, skupiny a příkazy. Třetí `GuidSymbol` prvek představuje úložiště imagí a obsahuje symboly pro všechny ikony pro příkazy. Pokud nemáte žádné příkazy, které používají ikony, můžete třetí `GuidSymbol` prvek vynechat.

2. V `GuidSymbol` elementu, který představuje sadu příkazů, přidejte jeden nebo více elementů [IDSymbol](../../extensibility/idsymbol-element.md) . Každé z nich představuje nabídku, panel nástrojů, skupinu nebo příkaz, které přidáváte do uživatelského rozhraní.

     Pro každý `IDSymbol` prvek nastavte `name` atribut na název, který budete používat pro odkaz na odpovídající nabídku, skupinu nebo příkaz, a pak nastavte `value` element na hexadecimální číslo, které bude představovat jeho ID příkazu. Žádné dva `IDSymbol` prvky, které mají stejnou nadřazenou položku, mohou mít stejnou hodnotu.

3. Pokud některý z prvků uživatelského rozhraní vyžaduje ikony, přidejte `IDSymbol` element pro každou ikonu do `GuidSymbol` prvku, který představuje úložiště imagí.

### <a name="put-ui-elements-in-the-ide"></a>Vložení prvků uživatelského rozhraní do integrovaného vývojového prostředí
 [Nabídky](../../extensibility/menus-element.md), [skupiny](../../extensibility/groups-element.md)a [tlačítka](../../extensibility/buttons-element.md) obsahují definice všech nabídek, skupin a příkazů, které jsou definovány v balíčku. Tyto nabídky, skupiny a příkazy v integrovaném vývojovém prostředí vložte buď pomocí [nadřazeného](../../extensibility/parent-element.md) elementu, který je součástí definice prvku uživatelského rozhraní, nebo pomocí elementu [CommandPlacement](../../extensibility/commandplacement-element.md) , který je definován jinde.

 Každý `Menu` `Group` element, a `Button` má `guid` atribut a `id` atribut. Vždy nastavte `guid` atribut tak, aby odpovídal názvu `GuidSymbol` elementu, který představuje sadu příkazů, a nastavte `id` atribut na název `IDSymbol` prvku, který představuje vaši nabídku, skupinu nebo příkaz v `Symbols` oddílu.

#### <a name="to-define-ui-elements"></a>Definování prvků uživatelského rozhraní

1. Pokud definujete nové nabídky, podnabídky, místní nabídky nebo panely nástrojů, přidejte `Menus` prvek do `Commands` prvku. Pak pro každou nabídku, která má být vytvořena, přidejte prvek [nabídky](../../extensibility/menu-element.md) do `Menus` prvku.

    Nastavte `guid` atributy a `id` `Menu` elementu a pak nastavte `type` atribut na požadovaný druh nabídky. Můžete také nastavit `priority` atribut pro vytvoření relativní pozice nabídky v nadřazené skupině.

   > [!NOTE]
   > `priority`Atribut se nevztahuje na panely nástrojů a kontextové nabídky.

2. Všechny příkazy v integrovaném vývojovém prostředí sady Visual Studio musí být hostované skupinami příkazů, které jsou přímými podřízenými položkami nabídek a panelů nástrojů. Pokud přidáváte nové nabídky nebo panely nástrojů do integrovaného vývojového prostředí (IDE), musí obsahovat nové skupiny příkazů. Můžete také přidat skupiny příkazů do stávajících nabídek a panelů nástrojů, abyste mohli příkazy vizuálně seskupit.

    Při přidávání nových skupin příkazů je nutné nejprve vytvořit `Groups` prvek a poté jej přidat do [skupiny](../../extensibility/group-element.md) pro každou skupinu příkazů.

    Nastavte `guid` atributy a pro `id` každý `Group` prvek a pak nastavte `priority` atribut pro vytvoření relativní pozice skupiny v nadřazené nabídce. Další informace najdete v tématu [vytvoření opakovaně použitelných skupin tlačítek](../../extensibility/creating-reusable-groups-of-buttons.md).

3. Pokud přidáváte nové příkazy do integrovaného vývojového prostředí (IDE), přidejte `Buttons` element do `Commands` elementu. Potom pro každý příkaz přidejte element [Button](../../extensibility/button-element.md) do `Buttons` elementu.

   1. Nastavte `guid` atributy a pro `id` každý `Button` prvek a pak nastavte `type` atribut na typ tlačítka, které chcete. Můžete také nastavit `priority` atribut pro vytvoření relativní pozice příkazu v nadřazené skupině.

       > [!NOTE]
       > Použijte `type="button"` pro standardní příkazy a tlačítka nabídky na panelech nástrojů.

   2. V `Button` elementu přidejte prvek [řetězce](../../extensibility/strings-element.md) , který obsahuje element [ButtonText](../../extensibility/buttontext-element.md) a element [Command](../../extensibility/commandname-element.md) . `ButtonText`Element poskytuje textový popisek pro položku nabídky nebo popis tlačítka pro tlačítko panelu nástrojů. `CommandName`Element poskytuje název příkazu, který se má použít ve správném příkazu.

   3. Pokud má váš příkaz ikonu, vytvořte v elementu prvek [ikony](../../extensibility/icon-element.md) `Button` a nastavte jeho `guid` `id` atributy na `Bitmap` prvek pro ikonu.

       > [!NOTE]
       > Tlačítka panelu nástrojů musí mít ikony.

   Další informace najdete v tématu [MenuCommands vs. OleMenuCommands](/visualstudio/misc/menucommands-vs-olemenucommands?view=vs-2015).

4. Pokud některý z příkazů vyžaduje ikony, přidejte prvek [rastry](../../extensibility/bitmaps-element.md) do `Commands` elementu. Pak pro každou ikonu přidejte prvek [rastrového obrázku](../../extensibility/bitmap-element.md) do `Bitmaps` prvku. Tady můžete zadat umístění prostředku rastrového obrázku. Další informace najdete v tématu [Přidání ikon do příkazů nabídky](../../extensibility/adding-icons-to-menu-commands.md).

   Můžete spoléhat na nadřazenou strukturu a správně umístit většinu nabídek, skupin a příkazů. U velmi rozsáhlých sad příkazů nebo v případě, že se na více místech musí zobrazit nabídka, skupina nebo příkaz, doporučujeme zadat umístění příkazů.

#### <a name="to-rely-on-parenting-to-place-ui-elements-in-the-ide"></a>Spoléhání na nadřazenou položku k umístění prvků uživatelského rozhraní v rozhraní IDE

1. V případě typických nadřazených prvků vytvořte `Parent` element v `Menu` každém `Group` elementu, a `Command` element, který je definován v balíčku.

    Cílem `Parent` elementu je nabídka nebo skupina, která bude obsahovat nabídku, skupinu nebo příkaz.

   1. Nastavte `guid` atribut na název `GuidSymbol` prvku, který definuje sadu příkazů. Pokud cílový element není součástí vašeho balíčku, použijte identifikátor GUID pro sadu příkazů, jak je definováno v odpovídajícím souboru *. vsct* .

   2. Nastavte `id` atribut tak, aby odpovídal `id` atributu cílové nabídky nebo skupiny. Seznam nabídek a skupin, které jsou zpřístupněny v rámci sady Visual Studio, naleznete v tématu [identifikátory GUID a ID nabídek](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md) nebo [identifikátorů GUID sady Visual Studio a ID panelů nástrojů sady Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md).

   Máte-li v integrovaném vývojovém prostředí (IDE) velký počet prvků uživatelského rozhraní nebo pokud máte prvky, které by měly být zobrazeny na více místech, definujte jejich umístění v prvku [CommandPlacements](../../extensibility/commandplacements-element.md) , jak je znázorněno v následujícím postupu.

#### <a name="to-use-command-placement-to-place-ui-elements-in-the-ide"></a>Použití umístění příkazu k umístění prvků uživatelského rozhraní v integrovaném vývojovém prostředí

1. Za element `Commands` přidejte element `CommandPlacements`.

2. Do `CommandPlacements` elementu přidejte `CommandPlacement` element pro každou nabídku, skupinu nebo příkaz.

    Každý `CommandPlacement` element nebo `Parent` element umístí jednu nabídku, skupinu nebo příkaz v jednom umístění IDE. Prvek uživatelského rozhraní může mít pouze jednu nadřazenou položku, ale může mít více umístění příkazů. Chcete-li umístit prvek uživatelského rozhraní do více umístění, přidejte `CommandPlacement` element pro každé umístění.

3. Nastavte `guid` atributy a pro `id` každý `CommandPlacement` prvek na nabídku hostování nebo skupinu, stejně jako u `Parent` prvku. Můžete také nastavit `priority` atribut pro vytvoření relativní pozice prvku uživatelského rozhraní.

   Můžete kombinovat umístění pomocí nadřazeného a umístění příkazů. U velmi rozsáhlých sad příkazů ale doporučujeme použít jenom umístění příkazu.

### <a name="add-specialized-behaviors"></a>Přidat specializované chování
 Pomocí elementu [CommandFlag](../../extensibility/command-flag-element.md) můžete změnit chování nabídek a příkazů, například pro změnu jejich vzhledu a viditelnosti. Můžete také ovlivnit, kdy je příkaz viditelný pomocí elementu [VisibilityConstraints](../../extensibility/visibilityconstraints-element.md) , nebo přidat klávesové zkratky pomocí elementu [vazby](../../extensibility/keybindings-element.md) klíčů. Některé druhy nabídek a příkazů již mají integrované specializované chování.

#### <a name="to-add-specialized-behaviors"></a>Přidání specializovaného chování

1. Aby bylo možné prvek uživatelského rozhraní zobrazit pouze v určitých kontextech uživatelského rozhraní, například při načtení řešení, použijte omezení viditelnosti.

   1. Za element `Commands` přidejte element `VisibilityConstraints`.

   2. Pro každou položku uživatelského rozhraní, která se má omezit, přidejte element [VisibilityItem](../../extensibility/visibilityitem-element.md) .

   3. Pro každý `VisibilityItem` prvek nastavte `guid` atributy a v `id` nabídce, skupině nebo příkazu a pak nastavte `context` atribut na kontext uživatelského rozhraní, který chcete, jak je definováno ve <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80> třídě.

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

5. Chcete-li připojit klávesovou zkratku závislou na nabídce nebo položku v nabídce, přidejte znak ampersand (&) do `ButtonText` prvku nabídky nebo položky nabídky. Znak, který následuje za ampersandem, je aktivní klávesová zkratka, pokud je nadřazená nabídka otevřená.

6. Chcete-li k příkazu připojit klávesovou zkratku nezávislou na nabídce, použijte prvek [vazby](../../extensibility/keybindings-element.md) klíčů. Další informace naleznete v tématu elementu [vazby](../../extensibility/keybinding-element.md) klíčů.

7. Chcete-li lokalizovat text nabídky, použijte `LocCanonicalName` element. Další informace naleznete v tématu element [strings](../../extensibility/strings-element.md) .

   Některé typy nabídek a tlačítek zahrnují specializované chování. Následující seznam popisuje některé specializované typy nabídek a tlačítek. Pro jiné typy viz `types` popisy atributů v [nabídce](../../extensibility/menu-element.md), [tlačítku](../../extensibility/button-element.md)a prvcích [combo](../../extensibility/combo-element.md) .

   - Pole se seznamem: pole se seznamem je rozevírací seznam, který se dá použít na panelu nástrojů. Chcete-li přidat pole se seznamem do uživatelského rozhraní, vytvořte v elementu element [Combos](../../extensibility/combos-element.md) `Commands` . Pak přidejte k `Combos` elementu element a `Combo` pro každé pole se seznamem, které chcete přidat. `Combo`prvky mají stejné atributy a podřízené položky jako `Button` elementy a také `DefaultWidth` atributy a `idCommandList` . `DefaultWidth`Atribut nastaví šířku v pixelech a `idCommandList` atribut odkazuje na ID příkazu, který se používá k naplnění pole se seznamem.

   - Controller nabídky: kontroler nabídek je tlačítko, které má vedle něj šipku. Kliknutím na šipku se otevře seznam. Chcete-li přidat do uživatelského rozhraní řadič nabídky, vytvořte `Menu` element a nastavte jeho `type` atribut na `MenuController` nebo `MenuControllerLatched` , v závislosti na požadovaném chování. Chcete-li naplnit řadič nabídky, nastavte jej jako nadřazený `Group` prvek elementu. Na řadiči nabídky se zobrazí všechny podřízené položky této skupiny v rozevíracím seznamu.

## <a name="see-also"></a>Viz také
- [Rozšiřování nabídek a příkazů](../../extensibility/extending-menus-and-commands.md)
- [Soubory tabulek příkazů sady Visual Studio (. vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
- [Referenční dokumentace schématu VSCT XML](../../extensibility/vsct-xml-schema-reference.md)
