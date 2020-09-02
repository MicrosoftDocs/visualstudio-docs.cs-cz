---
title: Jak VSPackage přidávají prvky uživatelského rozhraní | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- user interfaces, adding elements
- UI element design [Visual Studio SDK], VSPackages
- VSPackages, contributing UI elements
ms.assetid: abc5d9d9-b267-48a1-92ad-75fbf2f4c1b9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1d9cc3184009dd98e743064db1b8eb2abe6059d1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "81649600"
---
# <a name="how-vspackages-add-user-interface-elements"></a>Jak prvky VSPackage přidávají prvky uživatelského rozhraní
VSPackage může přidat prvky uživatelského rozhraní (UI), například nabídky, panely nástrojů a okna nástrojů, do sady Visual Studio prostřednictvím souboru *. vsct* .

Pokyny pro návrh pro prvky uživatelského rozhraní najdete v [pokynech pro uživatelské prostředí sady Visual Studio](../../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md).

## <a name="the-visual-studio-command-table-architecture"></a>Architektura tabulek příkazů sady Visual Studio
Jak je uvedeno, architektura tabulkových příkazů podporuje výše uvedené principy architektury. Principy za abstrakcemi, datových struktur a nástrojů architektury tabulek příkazu jsou následující:

- Existují tři základní druhy položek: nabídky, příkazy a skupiny. Nabídky lze zpřístupnit v uživatelském rozhraní jako nabídky, podnabídky, panely nástrojů nebo okna nástrojů. Příkazy jsou postupy, které může uživatel spustit v prostředí IDE a které mohou být zveřejněny jako položky nabídky, tlačítka, seznamy nebo jiné ovládací prvky. Skupiny jsou kontejnery pro nabídky a příkazy.

- Každá položka je určena definicí, která popisuje položku, její prioritu vzhledem k ostatním položkám a příznaky, které upravují její chování.

- Každá položka má umístění, které popisuje nadřazenou položku položky. Položka může mít více nadřazených objektů, aby se mohla objevit v uživatelském rozhraní v několika umístěních.

Každý příkaz musí mít skupinu jako nadřazenou, a to i v případě, že se jedná o jediný podřízený prvek v této skupině. Každá standardní nabídka musí mít také nadřazenou skupinu. Panely nástrojů a okna nástroje fungují jako jejich vlastníci. Skupina může mít jako nadřazené hlavní panel nabídek sady Visual Studio nebo libovolnou nabídku, panel nástrojů nebo okno nástrojů.

### <a name="how-items-are-defined"></a>Princip definování položek
Soubor *. vsct* je ve formátu XML. Definuje prvky uživatelského rozhraní pro balíček a určuje, kde se tyto prvky zobrazí v integrovaném vývojovém prostředí (IDE). Každé nabídce, skupině nebo příkazu v balíčku se nejprve v oddílu přiřadí identifikátor GUID a ID `Symbols` . V celé zbývající části souboru *. vsct* jsou jednotlivé nabídky, příkazy a skupiny označeny identifikátorem GUID a kombinací ID. Následující příklad ukazuje typický `Symbols` oddíl vygenerovaný šablonou balíčku sady Visual Studio při výběru **příkazu nabídky** v šabloně.

```xml
<Symbols>
  <!-- This is the package guid. -->
  <GuidSymbol name="guidMenuTextPkg" value="{b1253bc6-d266-402b-89e7-5e3d3b22c746}" />

  <!-- This is the guid used to group the menu commands together -->
  <GuidSymbol name="guidMenuTextCmdSet" value="{a633d4e4-6c65-4436-a138-1abeba7c9a69}">
    <IDSymbol name="MyMenuGroup" value="0x1020" />
    <IDSymbol name="cmdidMyCommand" value="0x0100" />
  </GuidSymbol>

  <GuidSymbol name="guidImages" value="{53323d9a-972d-4671-bb5b-9e418480922f}">
    <IDSymbol name="bmpPic1" value="1" />
    <IDSymbol name="bmpPic2" value="2" />
    <IDSymbol name="bmpPicSearch" value="3" />
    <IDSymbol name="bmpPicX" value="4" />
    <IDSymbol name="bmpPicArrows" value="5" />
  </GuidSymbol>
</Symbols>
```

Element nejvyšší úrovně `Symbols` oddílu je [element GuidSymbol](../../extensibility/guidsymbol-element.md). `GuidSymbol` prvky mapují názvy identifikátorů GUID, které jsou používány rozhraním IDE k identifikaci balíčků a jejich součástí.

> [!NOTE]
> Identifikátory GUID jsou generovány automaticky šablonou balíčku sady Visual Studio. Můžete také vytvořit jedinečný identifikátor GUID kliknutím na **vytvořit GUID** v nabídce **nástroje** .

První `GuidSymbol` prvek `guid<PackageName>Pkg` je identifikátor GUID samotného balíčku. Toto je identifikátor GUID, který sada Visual Studio používá k načtení balíčku. Obvykle nemá podřízené prvky.

Podle konvence jsou nabídky a příkazy seskupeny pod druhým `GuidSymbol` prvkem, `guid<PackageName>CmdSet` a bitmapy jsou pod třetím `GuidSymbol` prvkem `guidImages` . Nemusíte postupovat podle této konvence, ale každá nabídka, skupina, příkaz a bitmapa musí být podřízenou položkou `GuidSymbol` elementu.

V druhém `GuidSymbol` elementu, který představuje sadu příkazů balíčku, je několik `IDSymbol` prvků. Každý [element IDSymbol](../../extensibility/idsymbol-element.md) mapuje název na číselnou hodnotu a může představovat nabídku, skupinu nebo příkaz, který je součástí sady příkazů. `IDSymbol`Prvky třetího `GuidSymbol` elementu reprezentují bitmapy, které mohou být použity jako ikony pro příkazy. Vzhledem k tomu, že páry identifikátorů GUID a IDENTIFIKÁTORů musí být v aplikaci jedinečné, žádné dva podřízené prvky stejného `GuidSymbol` prvku nemohou mít stejnou hodnotu.

### <a name="menus-groups-and-commands"></a>Nabídky, skupiny a příkazy
Pokud má nabídka, skupina nebo příkaz identifikátor GUID a ID, může být přidána do rozhraní IDE. Každý prvek uživatelského rozhraní musí mít následující věci:

- `guid`Atribut, který odpovídá názvu `GuidSymbol` elementu, pod kterým je definován prvek uživatelského rozhraní.

- `id`Atribut, který odpovídá názvu přidruženého `IDSymbol` prvku.

Společně `guid` `id` atributy a tvoří *podpis* prvku uživatelského rozhraní.

- `priority`Atribut, který určuje umístění prvku uživatelského rozhraní v nadřazené nabídce nebo skupině.

- [Nadřazený element](../../extensibility/parent-element.md) , který má `guid` `id` atributy a, které určují signaturu nadřazené nabídky nebo skupiny.

#### <a name="menus"></a>Nabídky
Jednotlivé nabídky jsou definovány jako [prvek nabídky](../../extensibility/menu-element.md) v `Menus` oddílu. Nabídky musí mít atributy, a a `guid` `id` `priority` `Parent` také následující další atributy a podřízené prvky:

- `type`Atribut, který určuje, zda se má nabídka Zobrazit v integrovaném vývojovém prostředí jako typ nabídky nebo jako panel nástrojů.

- [Element Strings](../../extensibility/strings-element.md) , který obsahuje [element ButtonText](../../extensibility/buttontext-element.md), který určuje název nabídky v integrovaném vývojovém prostředí (IDE) a [element Command](../../extensibility/commandname-element.md), který určuje název, který se používá v **příkazovém** okně pro přístup k nabídce.

- Volitelné příznaky. [Element CommandFlag](../../extensibility/command-flag-element.md) se může zobrazit v definici nabídky, aby se změnil jeho vzhled nebo chování v integrovaném vývojovém prostředí (IDE).

Každý `Menu` element musí mít skupinu jako nadřazenou, pokud se nejedná o ukotvit element, jako je například panel nástrojů. Nabídka ukotvit je svým vlastním nadřazeným prvkem. Další informace o nabídkách a hodnotách `type` atributu naleznete v dokumentaci k [elementu nabídky](../../extensibility/menu-element.md) .

Následující příklad ukazuje nabídku, která se zobrazí v řádku nabídek sady Visual Studio vedle nabídky **nástroje** .

```xml
<Menu guid="guidTopLevelMenuCmdSet" id="TopLevelMenu" priority="0x700" type="Menu">
  <Parent guid="guidSHLMainMenu" id="IDG_VS_MM_TOOLSADDINS" />
  <Strings>
    <ButtonText>TestMenu</ButtonText>
    <CommandName>TestMenu</CommandName>
  </Strings>
</Menu>
```

#### <a name="groups"></a>Skupiny
Skupina je položka, která je definována v `Groups` části souboru *. vsct* . Skupiny jsou pouze kontejnery. Nezobrazují se v rozhraní IDE s výjimkou oddělitelné čáry v nabídce. Proto je [prvek skupiny](../../extensibility/group-element.md) definován pouze pomocí jeho signatury, priority a nadřazeného prvku.

Skupina může mít nabídku, jinou skupinu nebo sebe samu jako nadřazenou položku. Nadřazený objekt je však obvykle nabídka nebo panel nástrojů. Nabídka v předchozím příkladu je podřízenou položkou `IDG_VS_MM_TOOLSADDINS` skupiny a tato skupina je podřízenou položkou řádku nabídek sady Visual Studio. Skupina v následujícím příkladu je podřízenou položkou nabídky v předchozím příkladu.

```xml
<Group guid="guidTopLevelMenuCmdSet" id="MyMenuGroup" priority="0x0600">
  <Parent guid="guidTopLevelMenuCmdSet" id="TopLevelMenu"/>
</Group>
```

Vzhledem k tomu, že je součástí nabídky, tato skupina obvykle obsahuje příkazy. Může ale obsahovat i další nabídky. Toto je způsob, jakým jsou definovány podnabídky, jak je znázorněno v následujícím příkladu.

```xml
<Menu guid="guidTopLevelMenuCmdSet" id="SubMenu" priority="0x0100" type="Menu">
  <Parent guid="guidTopLevelMenuCmdSet" id="MyMenuGroup"/>
  <Strings>
    <ButtonText>Sub Menu</ButtonText>
    <CommandName>Sub Menu</CommandName>
  </Strings>
</Menu>
```

#### <a name="commands"></a>Příkazy
Příkaz, který je součástí integrovaného vývojového prostředí, je definován jako [element tlačítka](../../extensibility/button-element.md) nebo [kombinovaný element](../../extensibility/combo-element.md). Aby se zobrazila nabídka nebo panel nástrojů, musí mít příkaz skupinu jako nadřazenou.

##### <a name="buttons"></a>Tlačítka
Tlačítka jsou definována v `Buttons` části. Jakékoli položky nabídky, tlačítko nebo jiný prvek, který uživatel klikne na spustit jediný příkaz, se považuje za tlačítko. Některé typy tlačítek mohou také obsahovat funkce seznamu. Tlačítka mají stejné povinné a volitelné atributy, které mají nabídky, a mohou mít také [prvek ikony](../../extensibility/icon-element.md) , který určuje identifikátor GUID a ID rastrového obrázku, který představuje tlačítko v integrovaném vývojovém prostředí (IDE). Další informace o tlačítkech a jejich atributech naleznete v dokumentaci k [elementům tlačítek](../../extensibility/buttons-element.md) .

Tlačítko v následujícím příkladu je podřízenou skupinou v předchozím příkladu a v rozhraní IDE se zobrazí jako položka nabídky v nadřazené nabídce této skupiny.

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

##### <a name="combos"></a>Combos
Combos jsou definovány v `Combos` oddílu. Každý `Combo` element představuje rozevírací seznam v integrovaném vývojovém prostředí (IDE). Seznam může nebo nemusí být zapisovatelný uživatelům, v závislosti na hodnotě `type` atributu kombinovaného pole. Combos mají stejné prvky a chování jako tlačítka a mohou mít také následující další atributy:

- `defaultWidth`Atribut, který určuje šířku v pixelech.

- `idCommandList`Atribut, který určuje seznam obsahující položky, které jsou zobrazeny v seznamu. Seznam příkazů musí být deklarován ve stejném `GuidSymbol` uzlu, který obsahuje pole se seznamem.

Následující příklad definuje prvek kombinované.

```xml
<Combos>
  <Combo guid="guidFirstToolWinCmdSet"
         id="cmdidWindowsMediaFilename"
         priority="0x0100" type="DynamicCombo"
         idCommandList="cmdidWindowsMediaFilenameGetList"
         defaultWidth="130">
    <Parent guid="guidFirstToolWinCmdSet"
            id="ToolbarGroupID" />
    <CommandFlag>IconAndText</CommandFlag>
    <CommandFlag>CommandWellOnly</CommandFlag>
    <CommandFlag>StretchHorizontally</CommandFlag>
    <Strings>
      <CommandName>Filename</CommandName>
      <ButtonText>Enter a Filename</ButtonText>
    </Strings>
  </Combo>
</Combos>
```

##### <a name="bitmaps"></a>Bitmapy
Příkazy, které se zobrazí spolu s ikonou, musí obsahovat `Icon` element, který odkazuje na rastrový obrázek pomocí identifikátoru GUID a ID. Jednotlivé bitmapy jsou definovány jako [rastrový prvek](../../extensibility/bitmap-element.md) v `Bitmaps` oddílu. Jedinými požadovanými atributy pro `Bitmap` definici jsou `guid` a `href` , které odkazují na zdrojový soubor. Pokud je zdrojový soubor pruhem prostředků, vyžaduje se také atribut **usedList** , aby se vypisovat dostupné obrázky v pruhu. Další informace naleznete v dokumentaci k [elementu rastrového obrázku](../../extensibility/bitmap-element.md) .

### <a name="parenting"></a>Nadřazené vztahy
Následující pravidla určují, jak může položka zavolat jinou položku jako nadřazenou.

|Prvek|Definováno v této části tabulky příkazů|Může být obsažena (jako nadřazená nebo podle umístění v `CommandPlacements` části nebo obojí)|Může obsahovat (označované jako nadřazené)|
|-------------| - | - | - |
|Seskupení|[Groups – element](../../extensibility/groups-element.md), IDE, jiné sady VSPackage|Nabídka, skupina, samotná položka|Nabídky, skupiny a příkazy|
|Nabídka|[Menu – element](../../extensibility/menus-element.md), rozhraní IDE, jiné sady VSPackage|1 až *n* skupin|0 až *n* skupin|
|Panel nástrojů|[Menu – element](../../extensibility/menus-element.md), rozhraní IDE, jiné sady VSPackage|Samotná položka|0 až *n* skupin|
|Položka nabídky|[Buttons – Element](../../extensibility/buttons-element.md), rozhraní IDE, jiné sady VSPackage|1 až *n* skupin, samotná položka|-0 až *n* skupin|
|Tlačítko|[Buttons – Element](../../extensibility/buttons-element.md), rozhraní IDE, jiné sady VSPackage|1 až *n* skupin, samotná položka||
|Pole se seznamem|[Element Combos](../../extensibility/combos-element.md), rozhraní IDE, jiné sady VSPackage|1 až *n* skupin, samotná položka||

### <a name="menu-command-and-group-placement"></a>Umístění nabídek, příkazů a skupin
Nabídka, skupina nebo příkaz se mohou objevit ve více než jednom umístění v integrovaném vývojovém prostředí (IDE). Položka, která se má zobrazit ve více umístěních, musí být přidána do `CommandPlacements` oddílu jako [element CommandPlacement](../../extensibility/commandplacement-element.md). Všechny nabídky, skupiny nebo příkazy lze přidat jako umístění příkazu. Panely nástrojů však nelze tímto způsobem umístit, protože se nemohou vyskytovat v několika kontextově citlivých umístěních.

Místo pro příkazy mají `guid` `id` atributy, a `priority` . Identifikátor GUID a ID se musí shodovat s položkou, která je umístěna. `priority`Atribut určuje umístění položky s ohledem na jiné položky. Když rozhraní IDE sloučí dvě nebo více položek, které mají stejnou prioritu, jejich umístění nejsou definována, protože rozhraní IDE nezaručuje, že prostředky balíčku budou čteny ve stejném pořadí pokaždé, když je balíček sestaven.

Pokud se nabídka nebo skupina zobrazí ve více umístěních, všechny podřízené položky této nabídky nebo skupiny se zobrazí v každé instanci.

## <a name="command-visibility-and-context"></a>Viditelnost příkazů a kontext
Je-li nainstalováno více rozhraní VSPackage, procházejí nabídky, položky nabídky a panely nástrojů, což může být zbytečné. Chcete-li se tomuto problému vyhnout, můžete ovládat viditelnost jednotlivých prvků uživatelského rozhraní pomocí *omezení viditelnosti* a příznaků příkazů.

### <a name="visibility-constraints"></a>Omezení viditelnosti
Omezení viditelnosti je nastaveno jako [element VisibilityItem](../../extensibility/visibilityitem-element.md) v `VisibilityConstraints` oddílu. Omezení viditelnosti definuje konkrétní kontexty uživatelského rozhraní, ve kterém je cílová položka viditelná. Nabídka nebo příkaz, které jsou součástí této části, jsou viditelné pouze v případě, že je aktivní jeden z definovaných kontextů. Pokud v této části není odkaz na nabídku nebo příkaz, je ve výchozím nastavení vždy zobrazen. Tato část se nevztahuje na skupiny.

`VisibilityItem` elementy musí mít tři atributy následujícím způsobem: `guid` a `id` cílového prvku uživatelského rozhraní a `context` . `context`Atribut určuje, kdy bude cílová položka viditelná, a jako její hodnotu převede libovolný platný kontext uživatelského rozhraní. Konstanty kontextu uživatelského rozhraní pro Visual Studio jsou členy <xref:Microsoft.VisualStudio.VSConstants> třídy. Každý `VisibilityItem` prvek může mít pouze jednu hodnotu kontextu. Chcete-li použít druhý kontext, vytvořte druhý `VisibilityItem` prvek, který odkazuje na stejnou položku, jak je znázorněno v následujícím příkladu.

```xml
<VisibilityConstraints>
  <VisibilityItem guid="guidSolutionToolbarCmdSet"
        id="cmdidTestCmd"
        context="UICONTEXT_SolutionHasSingleProject" />
  <VisibilityItem guid="guidSolutionToolbarCmdSet"
        id="cmdidTestCmd"
        context="UICONTEXT_SolutionHasMultipleProjects" />
</VisibilityConstraints>
```

### <a name="command-flags"></a>Příznaky příkazu
Následující příznaky příkazu mohou ovlivnit viditelnost nabídek a příkazů, na které se vztahují.

`AlwaysCreate` Nabídka se vytvoří i v případě, že nemá žádné skupiny ani tlačítka.

Platí pro: `Menu`

`CommandWellOnly` Použijte tento příznak, pokud se příkaz nezobrazí v nabídce nejvyšší úrovně a chcete ho zpřístupnit pro další přizpůsobení prostředí, například vytvořit vazbu na klíč. Po instalaci sady VSPackage může uživatel tyto příkazy přizpůsobit otevřením dialogového okna **Možnosti** a úpravou umístění příkazu v kategorii **prostředí klávesnice** . Nemá vliv na umístění v místních nabídkách, panelech nástrojů, řadičích nabídek nebo podnabídkách.

Platí pro: `Button` , `Combo`

`DefaultDisabled` Ve výchozím nastavení je příkaz zakázán, pokud není načtena VSPackage, který implementuje příkaz, nebo nebyla volána metoda QueryStatus.

Platí pro: `Button` , `Combo`

`DefaultInvisible` Ve výchozím nastavení je příkaz neviditelný, pokud není načtena VSPackage, který implementuje příkaz, nebo nebyla volána metoda QueryStatus.

By měl být kombinován s `DynamicVisibility` příznakem.

Platné pro: `Button` , `Combo` , `Menu`

`DynamicVisibility` Viditelnost příkazu lze změnit pomocí `QueryStatus` metody nebo identifikátoru GUID kontextu, který je obsažen v `VisibilityConstraints` oddílu.

Platí pro příkazy, které se zobrazují v nabídkách, nikoli na panelech nástrojů. Položky panelu nástrojů nejvyšší úrovně lze zakázat, ale ne skryté, pokud `OLECMDF_INVISIBLE` je příznak vrácen z `QueryStatus` metody.

V nabídce je tento příznak také označovat, že by měl být automaticky skrytý, pokud jsou jeho členové skryti. Tento příznak je obvykle přiřazen podnabídkám, protože nabídky nejvyšší úrovně již mají toto chování.

By měl být kombinován s `DefaultInvisible` příznakem.

Platné pro: `Button` , `Combo` , `Menu`

`NoShowOnMenuController` Pokud je příkaz, který má tento příznak, umístěn na řadiči nabídky, příkaz se nezobrazí v rozevíracím seznamu.

Platí pro: `Button`

Další informace o příznacích příkazu naleznete v dokumentaci k [elementu CommandFlag](../../extensibility/command-flag-element.md) .

#### <a name="general-requirements"></a>Obecné požadavky
Příkaz musí před zobrazením a povolením předat následující sérii testů:

- Příkaz je umístěný správně.

- `DefaultInvisible`Příznak není nastaven.

- Zobrazí se nadřazená nabídka nebo panel nástrojů.

- Příkaz není neviditelný, protože kontextová položka v oddílu [element VisibilityConstraints](../../extensibility/visibilityconstraints-element.md) .

- Kód VSPackage, který implementuje <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> rozhraní, zobrazuje a povoluje váš příkaz. Nezachytil se žádný kód rozhraní a Nejednalo se o něj.

- Když uživatel klikne na váš příkaz, může se jednat o postup, který je popsaný v tématu [algoritmus směrování](../../extensibility/internals/command-routing-algorithm.md).

## <a name="call-pre-defined-commands"></a>Volání předem definovaných příkazů
[Element UsedCommands](../../extensibility/usedcommands-element.md) umožňuje VSPackage přistupovat k příkazům, které jsou k dispozici v jiných rozhraních VSPackage nebo IDE. Chcete-li to provést, vytvořte [element UsedCommand](../../extensibility/usedcommand-element.md) , který obsahuje identifikátor GUID a ID příkazu, který chcete použít. Tím se zajistí, že se příkaz načte v aplikaci Visual Studio, i když není součástí aktuální konfigurace sady Visual Studio. Další informace naleznete v tématu [UsedCommand element](../../extensibility/usedcommand-element.md).

## <a name="interface-element-appearance"></a>Vzhled prvku rozhraní
Pokyny pro výběr a umístění prvků příkazu jsou následující:

- [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] nabízí mnoho prvků uživatelského rozhraní, které se liší v závislosti na umístění.

- Prvek uživatelského rozhraní, který je definován pomocí `DefaultInvisible` příznaku, nebude zobrazen v integrovaném vývojovém prostředí, pokud není buď zobrazen implementací <xref:EnvDTE.IDTCommandTarget.QueryStatus%2A> metody VSPackage metody, nebo přidružený ke konkrétnímu kontextu uživatelského rozhraní v `VisibilityConstraints` oddílu.

- Nemůžete zobrazit i úspěšně umístěný příkaz. Důvodem je, že rozhraní IDE automaticky skrývá nebo zobrazuje některé příkazy v závislosti na rozhraních, která VSPackage (nebo není) implementováno. Například implementace sady VSPackage některých rozhraní buildu způsobí, že se automaticky zobrazí položky nabídky související s sestavením.

- Použití `CommandWellOnly` příznaku v definici prvku uživatelského rozhraní znamená, že příkaz lze přidat pouze úpravou.

- Příkazy mohou být k dispozici pouze v určitých kontextech uživatelského rozhraní, například pouze v případě, že se zobrazí dialogové okno, když je prostředí IDE v návrhovém zobrazení.

- Aby se některé prvky uživatelského rozhraní zobrazovaly v integrovaném vývojovém prostředí, musíte implementovat jedno nebo víc rozhraní nebo napsat nějaký kód.

## <a name="see-also"></a>Viz také
- [Rozšiřování nabídek a příkazů](../../extensibility/extending-menus-and-commands.md)
