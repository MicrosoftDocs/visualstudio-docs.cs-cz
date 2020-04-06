---
title: Jak VSPackages přidat prvky uživatelského rozhraní | Dokumenty společnosti Microsoft
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
ms.openlocfilehash: 3b7d37bfe81c77536871248592d4a2e0734d1c62
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707763"
---
# <a name="how-vspackages-add-user-interface-elements"></a>Jak VSPackages přidat prvky uživatelského rozhraní
VSPackage můžete přidat prvky uživatelského rozhraní (UI), například nabídky, panely nástrojů a okna nástrojů, do sady Visual Studio pomocí souboru *.vsct.*

 Pokyny pro návrh prvků uživatelského rozhraní najdete v [pokynech pro uživatelské prostředí sady Visual Studio](../../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md).

## <a name="the-visual-studio-command-table-architecture"></a>Architektura příkazové tabulky sady Visual Studio
 Jak již bylo uvedeno, architektura tabulky příkazů podporuje výše uvedené principy architektury. Principy za abstrakce, datové struktury a nástroje architektury tabulky příkazu jsou následující:

- Existují tři základní druhy položek: nabídky, příkazy a skupiny. Nabídky mohou být v ui vystaveny jako nabídky, podnabídky, panely nástrojů nebo okna nástrojů. Příkazy jsou postupy, které může uživatel provést v rozhraní IDE a mohou být vystaveny jako položky nabídky, tlačítka, seznamy nebo jiné ovládací prvky. Skupiny jsou kontejnery pro nabídky i příkazy.

- Každá položka je určena definicí, která popisuje položku, její prioritu vzhledem k ostatním položkám a příznaky, které mění její chování.

- Každá položka má umístění, které popisuje nadřazenou položku. Položka může mít více rodičů, takže se může zobrazit na více místech v unovém ui.

     Každý příkaz musí mít skupinu jako nadřazenou položku, i když je jediným podřízeným příkazem v této skupině. Každá standardní nabídka musí mít také nadřazenou skupinu. Panely nástrojů a okna nástrojů fungují jako jejich vlastní rodiče. Skupina může mít jako nadřazenou položku hlavní panel nabídek sady Visual Studio nebo libovolné nabídky, panelu nástrojů nebo okna nástrojů.

### <a name="how-items-are-defined"></a>Jak jsou definovány položky
 Soubor *.vsct* je formátován ve formátu XML. Definuje prvky uživatelského rozhraní pro balíček a určuje, kde se tyto prvky zobrazí v rozhraní IDE. Každé nabídce, skupině nebo příkazu v balíčku je nejprve `Symbols` přiřazenidentifikátor GUID a ID v sekci. Ve zbytku souboru *.vsct* je každá nabídka, příkaz a skupina identifikována kombinací IDENTIFIKÁTORA A ID. Následující příklad ukazuje `Symbols` typický oddíl, jak je generován šablonou balíčku Sady Visual Studio, když je v šabloně vybrán **příkaz nabídky.**

```xml
<Symbols>
  <!-- This is the package guid. -->
  <GuidSymbol name="guidMenuTextPkg" value="{b1253bc6-d266-402b-89e7-5e3d3b22c746}" />

  <!-- This is the guid used to group the menu commands together -->
  <GuidSymbol name="guidMenuTextCmdSet" value="{a633d4e4-6c65-4436-a138-1abeba7c9a69}">

    <IDSymbol name="MyMenuGroup" value="0x1020" />
    <IDSymbol name="cmdidMyCommand" value="0x0100" />
  </GuidSymbol>

  <GuidSymbol name="guidImages" value="{53323d9a-972d-4671-bb5b-9e418480922f}" >
    <IDSymbol name="bmpPic1" value="1" />
    <IDSymbol name="bmpPic2" value="2" />
    <IDSymbol name="bmpPicSearch" value="3" />
    <IDSymbol name="bmpPicX" value="4" />
    <IDSymbol name="bmpPicArrows" value="5" />
  </GuidSymbol>
</Symbols>
```

 Prvek nejvyšší úrovně oddílu `Symbols` je Element [GuidSymbol](../../extensibility/guidsymbol-element.md). `GuidSymbol`elementy mapovat názvy guid, které jsou používány ide k identifikaci balíčků a jejich součástí.

> [!NOTE]
> Identifikátory GUID jsou generovány automaticky šablonou balíčku sady Visual Studio. Jedinečný identifikátor GUID můžete také vytvořit klepnutím na tlačítko **Vytvořit identifikátor GUID** v nabídce **Nástroje.**

 První `GuidSymbol` prvek `guid<PackageName>Pkg`, je identifikátor GUID samotného balíčku. Toto je identifikátor GUID, který používá Visual Studio k načtení balíčku. Obvykle nemá podřízené prvky.

 Podle konvence jsou nabídky a příkazy seskupeny `GuidSymbol` `guid<PackageName>CmdSet`pod druhým prvkem a `GuidSymbol` bitmapy `guidImages`jsou pod třetím prvkem . Není nutné dodržovat tuto konvenci, ale každá nabídka, skupina, příkaz `GuidSymbol` a bitmapa musí být podřízený prvek.

 V druhém `GuidSymbol` prvku, který představuje sadu příkazů `IDSymbol` balíček, je několik prvků. Každý [prvek IDSymbol](../../extensibility/idsymbol-element.md) mapuje název na číselnou hodnotu a může představovat nabídku, skupinu nebo příkaz, který je součástí sady příkazů. Prvky `IDSymbol` ve `GuidSymbol` třetím prvku představují rastrové obrázky, které mohou být použity jako ikony pro příkazy. Vzhledem k tomu, že dvojice GUID/ID musí být `GuidSymbol` v aplikaci jedinečné, žádné dvě podřízené položky stejného prvku nesmí mít stejnou hodnotu.

### <a name="menus-groups-and-commands"></a>Nabídky, skupiny a příkazy
 Pokud nabídka, skupina nebo příkaz má identifikátor GUID a ID, lze jej přidat do rozhraní IDE. Každý prvek ui musí mít následující věci:

- Atribut, `guid` který odpovídá názvu `GuidSymbol` prvku, pod kterým je definován prvek uživatelského rozhraní.

- Atribut, `id` který odpovídá názvu `IDSymbol` přidruženého prvku.

     Společně `guid` atributy `id` a tvoří *podpis* prvku ui.

- Atribut, `priority` který určuje umístění prvku ujzěte v nadřazené nabídce nebo skupině.

- [Nadřazený prvek,](../../extensibility/parent-element.md) který má `guid` a `id` atributy, které určují podpis nadřazené nabídky nebo skupiny.

#### <a name="menus"></a>Nabídky
 Každá nabídka je definována jako `Menus` prvek [Menu](../../extensibility/menu-element.md) v sekci. Nabídky musí `guid`mít `id`, `priority` a atributy `Parent` a prvek a také následující další atributy a podřízené položky:

- Atribut, `type` který určuje, zda se má nabídka zobrazit v prostředí IDE jako druh nabídky nebo jako panel nástrojů.

- A [Strings Element,](../../extensibility/strings-element.md) který obsahuje [ButtonText element](../../extensibility/buttontext-element.md), který určuje název nabídky v IDE a [CommandName element](../../extensibility/commandname-element.md), který určuje název, který se používá v okně **Příkaz** pro přístup k nabídce.

- Volitelné příznaky. CommandFlag [prvek](../../extensibility/command-flag-element.md) se může zobrazit v definici nabídky změnit jeho vzhled nebo chování v rozhraní IDE.

  Každý `Menu` prvek musí mít skupinu jako nadřazený prvek, pokud se nejedná o dokovatelný prvek, například panel nástrojů. Dokovatelná nabídka je vlastní nadřazená nabídka. Další informace o nabídkách a `type` hodnotách atributu naleznete v dokumentaci [k prvku Nabídky.](../../extensibility/menu-element.md)

  Následující příklad ukazuje nabídku, která se zobrazí na panelu nabídek sady Visual Studio vedle nabídky **Nástroje.**

```xml
<Menu guid="guidTopLevelMenuCmdSet"
id="TopLevelMenu" priority="0x700" type="Menu">
  <Parent guid="guidSHLMainMenu"
          id="IDG_VS_MM_TOOLSADDINS" />
  <Strings>
    <ButtonText>TestMenu</ButtonText>
    <CommandName>TestMenu</CommandName>
  </Strings>
</Menu>
```

#### <a name="groups"></a>Skupiny
 Skupina je položka, která je `Groups` definována v části souboru *.vsct.* Skupiny jsou jen kontejnery. Nezobrazují se v ide s výjimkou jako dělící čára v nabídce. [Proto je prvek Group](../../extensibility/group-element.md) definován pouze jeho podpisem, prioritou a nadřazeným.

 Skupina může mít nabídku, jinou skupinu nebo sebe sama jako nadřazenou. Nadřazený je však obvykle nabídka nebo panel nástrojů. Nabídka v předchozím příkladu je `IDG_VS_MM_TOOLSADDINS` podřízená skupina a tato skupina je podřízenou položkou panelu nabídek sady Visual Studio. Skupina v následujícím příkladu je podřízená nabídka v předchozím příkladu.

```xml
 <Group guid="guidTopLevelMenuCmdSet" id="MyMenuGroup"
priority="0x0600">
   <Parent guid="guidTopLevelMenuCmdSet" id="TopLevelMenu"/>
 </Group>
```

 Vzhledem k tomu, že je součástí nabídky, tato skupina by obvykle obsahovat příkazy. Může však obsahovat i další nabídky. Tímto způsobem jsou definovány podnabídky, jak je znázorněno v následujícím příkladu.

```xml
<Menu guid="guidTopLevelMenuCmdSet" id="SubMenu"
priority="0x0100" type="Menu">
  <Parent guid="guidTopLevelMenuCmdSet" id="MyMenuGroup"/>
  <Strings>
    <ButtonText>Sub Menu</ButtonText>
    <CommandName>Sub Menu</CommandName>
  </Strings>
</Menu>
```

#### <a name="commands"></a>Příkazy
 Příkaz, který je k dispozici ide je definován jako Button [element](../../extensibility/button-element.md) nebo [Combo element](../../extensibility/combo-element.md). Chcete-li se zobrazit v nabídce nebo panelu nástrojů, musí mít příkaz jako nadřazenou skupinu.

##### <a name="buttons"></a>Tlačítka
 Tlačítka jsou definována `Buttons` v sekci. Za tlačítko se považuje libovolná položka nabídky, tlačítko nebo jiný prvek, na který uživatel klepne, aby provedl jeden příkaz. Některé typy tlačítek mohou také obsahovat funkce seznamu. Tlačítka mají stejné požadované a volitelné atributy, které mají nabídky a může mít také [Icon element,](../../extensibility/icon-element.md) který určuje GUID a ID bitmapy, která představuje tlačítko v rozhraní IDE. Další informace o tlačítkách a jejich atributech naleznete v dokumentaci [k elementu Tlačítka.](../../extensibility/buttons-element.md)

 Tlačítko v následujícím příkladu je podřízený masy skupiny v předchozím příkladu a zobrazí se v ide jako položka nabídky v nadřazené nabídce této skupiny.

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

##### <a name="combos"></a>Komba
 Komba jsou definovány `Combos` v sekci. Každý `Combo` prvek představuje rozevírací seznam v rozhraní IDE. Seznam může nebo nemusí být zapisovatelný uživateli v `type` závislosti na hodnotě atributu combo. Komba mají stejné prvky a chování, které tlačítka mají, a může mít také následující další atributy:

- Atribut, `defaultWidth` který určuje šířku obrazového bodu.

- Atribut, `idCommandList` který určuje seznam obsahující položky, které jsou zobrazeny v seznamu. Seznam příkazů musí být deklarován ve stejném `GuidSymbol` uzlu, který obsahuje kombinaci.

  Následující příklad definuje kombo prvek.

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
 Příkazy, které se zobrazí společně s `Icon` ikonou, musí obsahovat prvek, který odkazuje na bitmapu pomocí jeho identifikátoru GUID a ID. Každá bitmapa je definována jako `Bitmaps` [bitmapový prvek](../../extensibility/bitmap-element.md) v oddílu. Pouze požadované atributy `Bitmap` pro `guid` definici jsou a `href`, které odkazuje na zdrojový soubor. Pokud je zdrojový soubor proužkem prostředků, je také vyžadován atribut **usedList,** aby bylo možné uvést dostupné obrazy v proužku. Další informace naleznete v dokumentaci [k bitmapovým prvkům.](../../extensibility/bitmap-element.md)

### <a name="parenting"></a>Rodičovství
 Následující pravidla určují, jak může položka volat jinou položku jako nadřazenou položku.

|Element|Definováno v této části příkazové tabulky|Může být obsažen (jako rodič, nebo `CommandPlacements` umístěním v sekci, nebo obojí)|Může obsahovat (označované jako rodič)|
|-------------| - | - | - |
|Skupina|[Prvek skupiny](../../extensibility/groups-element.md), IDE, ostatní VSPackages|Nabídka, skupina, samotná položka|Nabídky, skupiny a příkazy|
|Nabídka|[Prvek nabídek](../../extensibility/menus-element.md), IDE, ostatní VSPackages|1 až *n* skupin|0 až *n* skupin|
|Panel nástrojů|[Prvek nabídek](../../extensibility/menus-element.md), IDE, ostatní VSPackages|Samotná položka|0 až *n* skupin|
|Položka nabídky|[Element tlačítka](../../extensibility/buttons-element.md), IDE, ostatní VSPackages|1 až *n* skupin, samotná položka|-0 až *n* skupin|
|Tlačítko|[Element tlačítka](../../extensibility/buttons-element.md), IDE, ostatní VSPackages|1 až *n* skupin, samotná položka||
|Pole se seznamem|[Komba element](../../extensibility/combos-element.md), IDE, ostatní VSPackages|1 až *n* skupin, samotná položka||

### <a name="menu-command-and-group-placement"></a>Nabídka, příkaz a umístění skupiny
 Nabídka, skupina nebo příkaz se mohou zobrazit na více než jednom místě v prostředí IDE. Aby se položka zobrazila na více `CommandPlacements` místech, musí být přidána do oddílu jako [element CommandPlacement](../../extensibility/commandplacement-element.md). Jako umístění příkazu lze přidat libovolnou nabídku, skupinu nebo příkaz. Panely nástrojů však nelze umístit tímto způsobem, protože se nemohou zobrazit ve více kontextových umístěních.

 Umístění příkazů `guid`mají `id`, `priority` a atributy. Identifikátor GUID a ID se musí shodovat s identifikátory položky, která je umístěna. Atribut `priority` určuje umístění položky s ohledem na jiné položky. Když ide sloučí dvě nebo více položek, které mají stejnou prioritu, jejich umístění jsou nedefinované, protože ide nezaručuje, že prostředky balíčku jsou čteny ve stejném pořadí při každém stvoření balíčku.

 Pokud se nabídka nebo skupina zobrazí na více místech, zobrazí se v každé instanci všechny podřízené položky této nabídky nebo skupiny.

## <a name="command-visibility-and-context"></a>Viditelnost a kontext příkazu
 Při instalaci více VSPackages, hojnost nabídek, položek nabídky a panely nástrojů může nepořádek IDE. Chcete-li se tomuto problému vyhnout, můžete řídit viditelnost jednotlivých prvků uživatelského rozhraní pomocí *omezení viditelnosti* a příkazové příznaky.

### <a name="visibility-constraints"></a>Omezení viditelnosti
 Omezení viditelnosti je nastaveno jako prvek `VisibilityConstraints` [VisibilityItem](../../extensibility/visibilityitem-element.md) v oddílu. Omezení viditelnosti definuje konkrétní kontexty ui, ve kterých je cílová položka viditelná. Nabídka nebo příkaz, který je součástí této části, je viditelný pouze v případě, že je aktivní jeden z definovaných kontextů. Pokud nabídka nebo příkaz není odkazováno v této části, je vždy viditelné ve výchozím nastavení. Tato část se nevztahuje na skupiny.

 `VisibilityItem`elementy musí mít tři atributy, `guid` `id` a to následovně: a cílový prvek uživatelského rozhraní a `context`. Atribut `context` určuje, kdy bude cílová položka viditelná, a jako svou hodnotu přebírá libovolný platný kontext ui. Kontextové konstanty ui pro Visual <xref:Microsoft.VisualStudio.VSConstants> Studio jsou členy třídy. Každý `VisibilityItem` prvek může trvat pouze jednu hodnotu kontextu. Chcete-li použít druhý kontext, vytvořte druhý `VisibilityItem` prvek, který odkazuje na stejnou položku, jak je znázorněno v následujícím příkladu.

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

### <a name="command-flags"></a>Příznaky příkazů
 Následující příznaky příkazů mohou ovlivnit viditelnost nabídek a příkazů, na které se vztahují.

 `AlwaysCreate`Nabídka je vytvořena i v případě, že nemá žádné skupiny nebo tlačítka.

 Platí pro:`Menu`

 `CommandWellOnly`Tento příznak použijte, pokud se příkaz nezobrazí v nabídce nejvyšší úrovně a chcete jej zpřístupnit pro další přizpůsobení prostředí, například jeho vazbu na klíč. Po instalaci balíčku VSPackage může uživatel tyto příkazy přizpůsobit otevřením dialogového okna **Možnosti** a úpravou umístění příkazů v kategorii **Prostředí klávesnice.** Nemá vliv na umístění v místních nabídkách, panelech nástrojů, řadičích nabídek nebo podnabídkách.

 Platí pro: `Button`,`Combo`

 `DefaultDisabled`Ve výchozím nastavení je příkaz zakázán, pokud není načten balíček VSPackage, který příkaz implementuje, nebo nebyla volána metoda QueryStatus.

 Platí pro: `Button`,`Combo`

 `DefaultInvisible`Ve výchozím nastavení je příkaz neviditelný, pokud není načten vbalíček VSPackage, který příkaz implementuje, nebo nebyla volána metoda QueryStatus.

 By měl být `DynamicVisibility` kombinován s vlajkou.

 Platí `Button`pro: `Combo`, ,`Menu`

 `DynamicVisibility`Viditelnost příkazu lze změnit pomocí `QueryStatus` metody nebo identifikátoru GUID kontextu, `VisibilityConstraints` který je součástí oddílu.

 Platí pro příkazy, které se zobrazují v nabídkách, nikoli na panelech nástrojů. Položky panelu nástrojů nejvyšší úrovně mohou být `OLECMDF_INVISIBLE` zakázány, ale `QueryStatus` nejsou skryté, když je příznak vrácen z metody.

 V nabídce tento příznak také označuje, že by měl být automaticky skryt, když jsou jeho členové skryti. Tento příznak je obvykle přiřazen k podnabídkám, protože nabídky nejvyšší úrovně již toto chování mají.

 By měl být `DefaultInvisible` kombinován s vlajkou.

 Platí `Button`pro: `Combo`, ,`Menu`

 `NoShowOnMenuController`Pokud je příkaz s tímto příznakem umístěn na řadiči nabídky, příkaz se v rozevíracím seznamu nezobrazí.

 Platí pro:`Button`

 Další informace o vlajkách příkazů naleznete v dokumentaci [k elementu CommandFlag.](../../extensibility/command-flag-element.md)

#### <a name="general-requirements"></a>Obecné požadavky
 Váš příkaz musí projít následující řadou testů, aby mohl být zobrazen a povolen:

- Příkaz je umístěn správně.

- Příznak `DefaultInvisible` není nastaven.

- Zobrazí se nadřazená nabídka nebo panel nástrojů.

- Příkaz není neviditelný z důvodu zadání kontextu v části [prvku VisibilityConstraints.](../../extensibility/visibilityconstraints-element.md)

- VSPackage kód, který <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> implementuje rozhraní zobrazí a umožňuje příkaz. Žádný kód rozhraní ho nezachytil a nejednal podle ní.

- Když uživatel klepne na váš příkaz, stane se předmětem postupu, který je popsán v [algoritmu směrování](../../extensibility/internals/command-routing-algorithm.md).

## <a name="call-pre-defined-commands"></a>Volání předdefinovaných příkazů
 The [UsedCommands Element](../../extensibility/usedcommands-element.md) umožňuje VSPackages pro přístup k příkazům, které jsou poskytovány jinými Balíčky VSPackages nebo IDE. Chcete-li to provést, vytvořte [prvek UsedCommand,](../../extensibility/usedcommand-element.md) který má identifikátor GUID a ID příkazu, který chcete použít. Tím zajistíte, že příkaz bude načten visual studio, i v případě, že není součástí aktuální konfigurace sady Visual Studio. Další informace naleznete v tématu [UsedCommand element](../../extensibility/usedcommand-element.md).

## <a name="interface-element-appearance"></a>Vzhled prvku rozhraní
 Důležité informace pro výběr a umístění prvků příkazu jsou následující:

- [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]nabízí mnoho prvků uživatelského rozhraní, které se v závislosti na umístění zobrazují odlišně.

- Prvek rozhraní, který je definován `DefaultInvisible` pomocí příznaku se nezobrazí v rozhraní IDE, pokud je zobrazen <xref:EnvDTE.IDTCommandTarget.QueryStatus%2A> jeho VSPackage implementace metody nebo `VisibilityConstraints` spojené s konkrétní kontext rozhraní v části.

- Dokonce i úspěšně umístěný příkaz nemusí být zobrazen. Důvodem je, že rozhraní IDE automaticky skryje nebo zobrazí některé příkazy, v závislosti na rozhraní, která VSPackage má (nebo nemá) implementována. Například implementace VSPackage některé rozhraní sestavení způsobí, že položky nabídky související s sestavením, které mají být automaticky zobrazeny.

- Použití `CommandWellOnly` příznaku v definici prvku uživatelského rozhraní znamená, že příkaz lze přidat pouze vlastním nastavením.

- Příkazy mohou být k dispozici pouze v určitých kontextech rozhraní, například pouze v případě, že dialogové okno se zobrazí, když je rozhraní IDE v návrhovém zobrazení.

- Chcete-li způsobit, že některé prvky uživatelského rozhraní, které mají být zobrazeny v rozhraní IDE, je nutné implementovat jedno nebo více rozhraní nebo napsat nějaký kód.

## <a name="see-also"></a>Viz také
- [Rozšíření nabídek a příkazů](../../extensibility/extending-menus-and-commands.md)
