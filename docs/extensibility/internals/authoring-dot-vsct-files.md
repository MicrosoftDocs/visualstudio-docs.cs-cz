---
title: Vytváření. Vsct Soubory | Dokumenty společnosti Microsoft
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
ms.openlocfilehash: dfa276d04e2d312d7ff00b1e9bc0015beb1e254e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710001"
---
# <a name="author-vsct-files"></a>Soubory Autor .vsct
Tento dokument ukazuje, jak vytvořit soubor *.vsct* pro přidání položek nabídky, panelů nástrojů a dalších prvků uživatelského rozhraní (UI) do integrovaného vývojového prostředí sady Visual Studio (IDE). Tyto kroky použijte při přidání prvků uživatelského rozhraní do balíčku sady Visual Studio (VSPackage), který ještě nemá soubor *.vsct.*

 Pro nové projekty doporučujeme použít šablonu balíčku sady Visual Studio, protože generuje soubor *.vsct,* který v závislosti na vašich výběrech již obsahuje požadované prvky pro příkaz nabídky, okno nástroje nebo vlastní editor. Tento soubor *VSCT* můžete upravit tak, aby splňoval požadavky vašeho balíčku VSPackage. Další informace o úpravě souboru *.vsct* naleznete v příkladech v [tématu Rozšířit nabídky a příkazy](../../extensibility/extending-menus-and-commands.md).

## <a name="author-the-file"></a>Vytvoření souboru
 Vytvořte soubor *.vsct* v těchto fázích: Vytvořte strukturu pro soubory a prostředky, deklarujte prvky uživatelského rozhraní, vložte prvky uživatelského rozhraní do rozhraní IDE a přidejte jakékoli specializované chování.

### <a name="file-structure"></a>Struktura souborů
 Základní struktura souboru *.vsct* je kořenový prvek [CommandTable,](../../extensibility/commandtable-element.md) který obsahuje element [Commands](../../extensibility/commands-element.md) a [element Symboly.](../../extensibility/symbols-element.md)

#### <a name="to-create-the-file-structure"></a>Vytvoření struktury souboru

1. Přidejte soubor *.vsct* do projektu podle kroků v [části Postup: Vytvoření souboru .vsct](../../extensibility/internals/how-to-create-a-dot-vsct-file.md).

2. Přidejte do `CommandTable` prvku požadované obory názvů, jak je znázorněno v následujícím příkladu:

    ```xml
    <CommandTable xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable"
        xmlns:xs="http://www.w3.org/2001/XMLSchema">

    ```

3. V `CommandTable` elementu `Commands` přidejte prvek, který bude hostovat všechny vlastní nabídky, panely nástrojů, skupiny příkazů a příkazy. Aby se vaše vlastní prvky `Commands` uživatelského rozhraní `Package` mohly načíst, musí mít prvek svůj atribut nastavený na název balíčku.

     Za `Commands` element přidejte `Symbols` prvek, který definuje identifikátory GUID pro balíček a názvy a ID příkazů pro prvky uživatelského rozhraní.

### <a name="include-visual-studio-resources"></a>Zahrnout prostředky sady Visual Studio
 Pomocí [extern](../../extensibility/extern-element.md) prvek pro přístup k souborům, které definují visual studio příkazy a nabídky, které jsou nutné umístit prvky uživatelského rozhraní v rozhraní IDE. Pokud budete používat příkazy definované mimo balíček, použijte [usedCommands](../../extensibility/usedcommands-element.md) element informovat Visual Studio.

#### <a name="to-include-visual-studio-resources"></a>Zahrnutí prostředků sady Visual Studio

1. V horní části `CommandTable` prvku přidejte jeden `Extern` prvek pro každý externí soubor, na který se má odkazovat, a nastavte `href` atribut na název souboru. Můžete odkazovat na následující soubory hlaviček pro přístup k prostředkům sady Visual Studio:

   - *Stdidcmd.h*: Definuje ID pro všechny příkazy vystavené visual studio.

   - *Vsshlids.h*: Obsahuje ID příkazů pro nabídky sady Visual Studio.

2. Pokud váš balíček volá všechny příkazy, které jsou definovány Visual Studio nebo jiné balíčky, přidejte `UsedCommands` prvek za `Commands` prvek. Naplňte tento prvek elementem [UsedCommand](../../extensibility/usedcommand-element.md) pro každý volaný příkaz, který není součástí vašeho balíčku. Nastavte `guid` atributy a `id` `UsedCommand` prvků na hodnoty GUID a ID příkazů, které mají být volány.

   Další informace o tom, jak najít identifikátory GUID a ID příkazů sady Visual Studio, naleznete [v tématu GUID a ID příkazů sady Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-commands.md). Chcete-li volat příkazy z jiných balíčků, použijte identifikátor GUID a ID příkazu, jak je definováno v souboru *.vsct* pro tyto balíčky.

### <a name="declare-ui-elements"></a>Deklarovat prvky uživatelského rozhraní
 Deklarujte všechny nové `Symbols` prvky uživatelského rozhraní v části souboru *.vsct.*

#### <a name="to-declare-ui-elements"></a>Deklarování prvků uživatelského rozhraní

1. Do `Symbols` prvku přidejte tři [prvky GuidSymbol.](../../extensibility/guidsymbol-element.md) Každý `GuidSymbol` prvek `name` má atribut `value` a atribut. Nastavte `name` atribut tak, aby odrážel účel prvku. Atribut `value` přebírá identifikátor GUID. (Chcete-li generovat identifikátor GUID, vyberte v nabídce **Nástroje** **možnost Vytvořit identifikátor GUID**a potom vyberte **možnost Formát registru**.)

     První `GuidSymbol` prvek představuje váš balíček a obvykle nemá žádné podřízené objekty. Druhý `GuidSymbol` prvek představuje sadu příkazů a bude obsahovat všechny symboly, které definují nabídky, skupiny a příkazy. Třetí `GuidSymbol` prvek představuje úložiště obrázků a obsahuje symboly pro všechny ikony pro vaše příkazy. Pokud nemáte žádné příkazy, které používají ikony, `GuidSymbol` můžete vynechat třetí prvek.

2. V `GuidSymbol` prvku, který představuje sadu příkazů, přidejte jeden nebo více prvků [IDSymbol.](../../extensibility/idsymbol-element.md) Každý z nich představuje nabídku, panel nástrojů, skupinu nebo příkaz, který přidáváte do uhlavního prostředí.

     Pro `IDSymbol` každý prvek `name` nastavte atribut na název, který budete používat k odkazování na odpovídající `value` nabídku, skupinu nebo příkaz, a nastavte prvek na šestnáctkové číslo, které bude představovat jeho ID příkazu. Žádné `IDSymbol` dva prvky, které mají stejnou nadřazenou položku, nemohou mít stejnou hodnotu.

3. Pokud některý z prvků uživatelského rozhraní `IDSymbol` vyžaduje ikony, `GuidSymbol` přidejte prvek pro každou ikonu do elementu, který představuje úložiště obrázků.

### <a name="put-ui-elements-in-the-ide"></a>Vložit prvky uživatelského rozhraní do rozhraní IDE
 Prvky [Nabídky](../../extensibility/menus-element.md), [Skupiny](../../extensibility/groups-element.md)a [Tlačítka](../../extensibility/buttons-element.md) obsahují definice pro všechny nabídky, skupiny a příkazy, které jsou definovány v balíčku. Vložte tyto nabídky, skupiny a příkazy do rozhraní IDE buď pomocí [nadřazeného](../../extensibility/parent-element.md) prvku, který je součástí definice prvku rozhraní, nebo pomocí elementu [CommandPlacement,](../../extensibility/commandplacement-element.md) který je definován jinde.

 Každý `Menu` `Group`, `Button` a prvek `guid` má `id` atribut a atribut. Vždy nastavte `guid` atribut tak, aby `GuidSymbol` odpovídal názvu prvku, který `id` představuje sadu příkazů, `IDSymbol` a nastavte atribut na název prvku, který představuje nabídku, skupinu nebo příkaz v oddílu. `Symbols`

#### <a name="to-define-ui-elements"></a>Definování prvků uživatelského rozhraní

1. Pokud definujete nové nabídky, podnabídky, místní nabídky nebo panely nástrojů, `Menus` přidejte `Commands` do prvku prvek. Potom pro každou nabídku, která má být `Menus` vytvořena, přidejte Prvek [Menu](../../extensibility/menu-element.md) do prvku.

    Nastavte `guid` atributy a `id` `Menu` prvku a potom `type` nastavte atribut na požadovaný druh nabídky. Můžete také nastavit `priority` atribut pro stanovení relativní pozice nabídky v nadřazené skupině.

   > [!NOTE]
   > Atribut `priority` se nevztahuje na panely nástrojů a místní nabídky.

2. Všechny příkazy v rozhraní IDE sady Visual Studio musí být hostovány skupinami příkazů, které jsou přímými podřízenými nabídkami a panely nástrojů. Pokud přidáváte nové nabídky nebo panely nástrojů do prostředí IDE, musí obsahovat nové skupiny příkazů. Můžete také přidat skupiny příkazů do existujících nabídek a panelů nástrojů, abyste mohli vizuálně seskupit příkazy.

    Když přidáte nové skupiny příkazů, `Groups` musíte nejprve vytvořit prvek a potom k němu přidat prvek [Skupiny](../../extensibility/group-element.md) pro každou skupinu příkazů.

    Nastavte `guid` atributy a `id` `Group` každého prvku a `priority` potom nastavte atribut pro stanovení relativní pozice skupiny v nadřazené nabídce. Další informace naleznete v [tématu Vytvoření opakovaně použitelných skupin tlačítek](../../extensibility/creating-reusable-groups-of-buttons.md).

3. Pokud přidáváte nové příkazy do rozhraní `Buttons` IDE, `Commands` přidejte prvek do prvku. Potom pro každý příkaz [Button](../../extensibility/button-element.md) přidejte Button `Buttons` prvek prvku.

   1. Nastavte `guid` atributy a `id` `Button` jednotlivých prvků a `type` potom nastavte atribut na požadovaný druh tlačítka. Můžete také nastavit `priority` atribut pro stanovení relativní pozice příkazu v nadřazené skupině.

       > [!NOTE]
       > Používá `type="button"` se pro standardní příkazy a tlačítka nabídek na panelech nástrojů.

   2. V `Button` elementu přidejte element [Strings,](../../extensibility/strings-element.md) který obsahuje element [ButtonText](../../extensibility/buttontext-element.md) a element [CommandName.](../../extensibility/commandname-element.md) Prvek `ButtonText` poskytuje textový popisek pro položku nabídky nebo popis pro tlačítko panelu nástrojů. Prvek `CommandName` poskytuje název příkazu, který má být v příkazu dobře použít.

   3. Pokud váš příkaz bude mít ikonu, vytvořte prvek [Icon](../../extensibility/icon-element.md) v `Button` prvku a nastavte jeho `guid` a `id` atributy na `Bitmap` prvek pro ikonu.

       > [!NOTE]
       > Tlačítka panelu nástrojů musí obsahovat ikony.

   Další informace naleznete v [tématu MenuCommands vs. OleMenuCommands](/visualstudio/extensibility/menucommands-vs-olemenucommands?view=vs-2015).

4. Pokud některý z vašich příkazů vyžaduje ikony, `Commands` přidejte do prvku prvek [Rastry.](../../extensibility/bitmaps-element.md) Potom pro každou ikonu přidejte prvek `Bitmaps` [Bitmap](../../extensibility/bitmap-element.md) do prvku. Toto je místo, kde zadáte umístění bitmapového prostředku. Další informace naleznete v tématu [Přidání ikon do příkazů nabídky](../../extensibility/adding-icons-to-menu-commands.md).

   Můžete se spolehnout na nadřazenou strukturu správně umístit většinu nabídek, skupin a příkazů. U velmi velkých sad příkazů nebo v případě, že se nabídka, skupina nebo příkaz musí zobrazit na více místech, doporučujeme zadat umístění příkazů.

#### <a name="to-rely-on-parenting-to-place-ui-elements-in-the-ide"></a>Chcete-li spoléhat na rodičovství umístit prvky uživatelského rozhraní v rozhraní IDE

1. Pro typické rodičovství `Parent` vytvořte prvek `Menu` `Group`v `Command` každém , a prvek, který je definován v balíčku.

    Cílem `Parent` prvku je nabídka nebo skupina, která bude obsahovat nabídku, skupinu nebo příkaz.

   1. Nastavte `guid` atribut na název `GuidSymbol` prvku, který definuje sadu příkazů. Pokud cílový prvek není součástí balíčku, použijte identifikátor GUID pro tuto sadu příkazů, jak je definováno v odpovídajícím souboru *.vsct.*

   2. Nastavte `id` atribut tak, `id` aby odpovídal atributu cílové nabídky nebo skupiny. Seznam nabídek a skupin, které jsou vystaveny v sadě Visual Studio, naleznete [v tématu GUID a ID nabídek sady Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md) nebo [identifikátorů GUID a ID panelů nástrojů sady Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md).

   Pokud máte velký počet prvků uživatelského rozhraní umístit do rozhraní IDE, nebo pokud máte prvky, které by se měly objevit na více místech, definujte jejich umístění v [CommandPlacements](../../extensibility/commandplacements-element.md) element, jak je znázorněno v následujících krocích.

#### <a name="to-use-command-placement-to-place-ui-elements-in-the-ide"></a>Použití umístění příkazu k umístění prvků uživatelského rozhraní do rozhraní IDE

1. Za element `Commands` přidejte element `CommandPlacements`.

2. Do `CommandPlacements` prvku přidejte `CommandPlacement` prvek pro každou nabídku, skupinu nebo příkaz, který chcete umístit.

    Každý `CommandPlacement` prvek `Parent` nebo prvek umístí jednu nabídku, skupinu nebo příkaz do jednoho umístění rozhraní IDE. Prvek ui může mít pouze jednu nadřazenou položku, ale může mít více umístění příkazů. Chcete-li umístit prvek uj na `CommandPlacement` více místech, přidejte prvek pro každé umístění.

3. Nastavte `guid` atributy a `id` `CommandPlacement` každého prvku do hostitelské nabídky nebo skupiny, stejně `Parent` jako u prvku. Můžete také nastavit `priority` atribut pro stanovení relativní pozice prvku ui.

   Umístění můžete kombinovat podle rodičovství a umístění příkazů. U velmi velkých sad příkazů však doporučujeme použít pouze umístění příkazů.

### <a name="add-specialized-behaviors"></a>Přidání specializovaného chování
 Pomocí elementu [CommandFlag](../../extensibility/command-flag-element.md) můžete změnit chování nabídek a příkazů, například ke změně jejich vzhledu a viditelnosti. Můžete také ovlivnit, když je příkaz viditelný pomocí [visibilityConstraints](../../extensibility/visibilityconstraints-element.md) element nebo přidat klávesové zkratky pomocí [KeyBindings](../../extensibility/keybindings-element.md) element. Některé druhy nabídek a příkazů již mají vestavěné specializované chování.

#### <a name="to-add-specialized-behaviors"></a>Přidání specializovaného chování

1. Chcete-li prvek ui zobrazit pouze v určitých kontextech ui, například při načtení řešení, použijte omezení viditelnosti.

   1. Za element `Commands` přidejte element `VisibilityConstraints`.

   2. Pro každou položku ui omezit, přidejte [VisibilityItem](../../extensibility/visibilityitem-element.md) element.

   3. Pro `VisibilityItem` každý prvek `guid` nastavte `id` atributy a na nabídku, skupinu `context` nebo příkaz a potom nastavte atribut na <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80> požadovaný kontext ui, jak je definováno ve třídě.

2. Chcete-li nastavit viditelnost nebo dostupnost položky uj v kódu, použijte jeden nebo více z následujících příznaků příkazu:

   - `DefaultDisabled`

   - `DefaultInvisible`

   - `DynamicItemStart`

   - `DynamicVisibility`

   - `NoShowOnMenuController`

   - `NotInTBList`

   Další informace naleznete v elementu [CommandFlag.](../../extensibility/command-flag-element.md)

3. Chcete-li změnit vzhled prvku nebo dynamicky změnit jeho vzhled, použijte jeden nebo více z následujících příznaků příkazu:

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

   Další informace naleznete v elementu [CommandFlag.](../../extensibility/command-flag-element.md)

4. Chcete-li změnit způsob reakce prvku při přijímání příkazů, použijte jeden nebo více z následujících příznaků příkazu:

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

   Další informace naleznete v elementu [CommandFlag.](../../extensibility/command-flag-element.md)

5. Chcete-li k nabídce nebo k položce v nabídce připojit klávesovou zkratku `ButtonText` závislou na nabídce, přidejte do prvku nabídky nebo položky nabídky znak ampersand (&). Znak, který následuje ampersand je aktivní klávesová zkratka při otevření nadřazené nabídky.

6. Chcete-li k příkazu připojit klávesovou zkratku nezávislou na nabídce, použijte element [KeyBindings.](../../extensibility/keybindings-element.md) Další informace naleznete [v keybinding](../../extensibility/keybinding-element.md) elementu.

7. Chcete-li lokalizovat text `LocCanonicalName` nabídky, použijte prvek. Další informace naleznete [v](../../extensibility/strings-element.md) řetězci elementu.

   Některé typy nabídek a tlačítek obsahují specializované chování. Následující seznam popisuje některé specializované nabídky a typy tlačítek. Další typy naleznete `types` v popisech atributů v panelech [Menu](../../extensibility/menu-element.md), [Button](../../extensibility/button-element.md)a [Combo.](../../extensibility/combo-element.md)

   - Pole se seznamem: Pole se seznamem je rozevírací seznam, který lze použít na panelu nástrojů. Chcete-li do operačního rozhraní přidat pole se `Commands` seznamem, vytvořte v prvku prvek [Combos.](../../extensibility/combos-element.md) Pak přidejte `Combos` do `Combo` prvku prvek pro každý pole se seznamem přidat. `Combo`prvky mají stejné atributy `Button` a podřízené jako prvky a také mají `DefaultWidth` a `idCommandList` atributy. Atribut `DefaultWidth` nastaví šířku v obrazových bodech a `idCommandList` atribut odkazuje na ID příkazu, který se používá k naplnění pole se seznamem.

   - Ovladač nabídky: Ovladač nabídky je tlačítko, které má šipku vedle něj. Kliknutím na šipku se otevře seznam. Chcete-li do hlavního rozhraní přidat `Menu` řadič nabídky, vytvořte prvek a nastavte jeho `type` atribut na `MenuController` nebo `MenuControllerLatched`v závislosti na požadovaném chování. Chcete-li naplnit řadič nabídky, nastavte `Group` jej jako nadřazený prvek. V rozbalovacím seznamu se zobrazí všechny podřízené položky této skupiny.

## <a name="see-also"></a>Viz také
- [Rozšíření nabídek a příkazů](../../extensibility/extending-menus-and-commands.md)
- [Soubory příkazů sady Visual Studio (.vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
- [Odkaz na schéma XML VSCT](../../extensibility/vsct-xml-schema-reference.md)
