---
title: Jak balíčky VSPackages přidávají prvky uživatelského rozhraní | Dokumentace Microsoftu
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
- user interfaces, adding elements
- UI element design [Visual Studio SDK], VSPackages
- VSPackages, contributing UI elements
ms.assetid: abc5d9d9-b267-48a1-92ad-75fbf2f4c1b9
caps.latest.revision: 61
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 88b1a71964ddae67241025dd32c1a1384c79765f
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51753376"
---
# <a name="how-vspackages-add-user-interface-elements"></a>Jak balíčky VSPackages přidávají prvky uživatelského rozhraní
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

VSPackage můžete přidat prvky uživatelského rozhraní (UI, například nabídky, panely nástrojů) a nástrojů systému windows se sadou Visual Studio pomocí souboru .vsct.  
  
 Můžete najít pokyny k návrhu pro prvky uživatelského rozhraní na [Visual Studio zkušenosti uživatelů](../../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md).  
  
## <a name="the-visual-studio-command-table-architecture"></a>Architektura sady Visual Studio příkaz tabulky  
 Jak je uvedeno, architektura tabulky příkaz podporuje předchozí architektonických principů. Principy za abstrakce, datové struktury a nástroje pro architekturu tabulka příkazu jsou následující:  
  
-   Existují tři základní typy položek: nabídky, příkazy a skupiny. Nabídky můžou zveřejnit v uživatelském rozhraní jako nabídky, dílčích nabídek, panelů nástrojů nebo okna nástrojů. Příkazy jsou postupy, které uživatel může spustit v prostředí IDE, a může být vystavena jako položky nabídky, tlačítka, seznamy nebo další ovládací prvky. Skupiny jsou kontejnery pro nabídek a příkazů.  
  
-   Každá položka je určená popisující položku, jeho prioritu ve vztahu k jiné položky a příznaky, které upravují chování při jeho definici.  
  
-   Každá položka má umístění, která popisuje nadřazené položky. Položka může mít více nadřazených objektů, aby se může objevit v několika umístěních v uživatelském rozhraní.  
  
     Každý příkaz musí mít skupinu jako jeho nadřazeným prvkem, i když je jediným podřízeným v této skupině. Každý standardní nabídky musí také mít nadřazenou skupinu. Panely nástrojů a oken nástrojů slouží jako jejich nadřazené položky. Skupina může mít jako nadřazeného hlavního řádku nabídek sady Visual Studio, nebo všechny nabídky, nástrojů nebo panelu nástrojů.  
  
### <a name="how-items-are-defined"></a>Jak jsou definovány položky  
 . Vsct soubory jsou ve formátu XML. Souboru .vsct definuje prvky uživatelského rozhraní pro balíček a určuje, kde se zobrazí tyto prvky v integrovaném vývojovém prostředí. Každou nabídku, skupinu nebo příkaz v balíčku poprvé přiřazen identifikátor GUID a ID v `Symbols` oddílu. Ve zbývající části .vsct souboru, každé nabídky, příkaz a skupiny je identifikován jeho kombinace GUID a ID. Následující příklad ukazuje typickou `Symbols` části vygenerovaný balíček šablonou Visual Studio při **příkazu nabídky** vybrány v šabloně.  
  
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
  
 Element nejvyšší úrovně `Symbols` oddíl je [guidsymbol – Element](../../extensibility/guidsymbol-element.md). `GuidSymbol` prvky mapování jména na identifikátory GUID, které používají rozhraní IDE k identifikaci balíčky a jejich součásti.  
  
> [!NOTE]
>  GUID balíčku šablonou Visual Studio automaticky generovány. Jedinečný identifikátor GUID můžete také vytvořit kliknutím **Create GUID** na **nástroje** nabídky.  
  
 První `GuidSymbol` elementu "guid [název balíčku] Pkg", je GUID samotném balíčku. Toto je identifikátor GUID, který se používá sada Visual Studio k načtení balíčku. Obvykle nemá podřízené prvky.  
  
 Podle konvence, nabídek a příkazů jsou seskupené v sekundy `GuidSymbol` elementu "guid [název balíčku] CmdSet", a rastrové obrázky mají v části třetí `GuidSymbol` elementu, "guidImages". Nemáte odpovídají této konvenci, ale každé nabídky, skupiny, příkaz a rastrový obrázek musí být podřízeným `GuidSymbol` elementu.  
  
 Ve druhém `GuidSymbol` element, který představuje sadu příkazů balíčku, několik `IDSymbol` elementy. Každý [idsymbol – Element](../../extensibility/idsymbol-element.md) mapuje název na číselnou hodnotu a může představovat nabídky, skupiny nebo příkaz, který je součástí sady příkazů. `IDSymbol` Elementy ve třetím `GuidSymbol` představují rastrové obrázky element, který může sloužit jako ikony pro příkazy. Protože identifikátor GUID a ID dvojice musejí být jedinečné v aplikaci, dva podřízené prvky stejného `GuidSymbol` element může obsahovat stejnou hodnotu.  
  
### <a name="menus-groups-and-commands"></a>Příkazy, nabídky a skupiny  
 Když nabídky, skupiny nebo příkaz má identifikátor GUID a ID, můžete přidat do integrovaného vývojového prostředí. Každý prvek uživatelského rozhraní musí mít následující věci:  
  
-   A `guid` atribut, který odpovídá názvu `GuidSymbol` element, který je definován prvek uživatelského rozhraní v části.  
  
-   `id` Atribut, který odpovídá názvu přidruženého `IDSymbol` elementu.  
  
     Společně `guid` a `id` compose atributy *podpis* prvku uživatelského rozhraní.  
  
-   A `priority` atribut, který určuje umístění prvku uživatelského rozhraní v jeho nadřazené nabídky nebo skupiny.  
  
-   A [nadřazeného elementu](../../extensibility/parent-element.md) , který má `guid` a `id` atributy, které určují podpis nadřazené nabídky nebo skupiny.  
  
#### <a name="menus"></a>Nabídky  
 Každou nabídku je definován jako [Menu Element](../../extensibility/menu-element.md) v `Menus` oddílu. Nabídky musí mít `guid`, `id`, a `priority` atributy a `Parent` element a také následující doplňkové atributy a podřízené položky:  
  
- A `type` atribut, který určuje, zda by měl zobrazit v nabídce v integrovaném vývojovém prostředí jako typ nabídky nebo panelu nástrojů.  
  
- A [Strings – Element](../../extensibility/strings-element.md) , která obsahuje [ButtonText – Element](../../extensibility/buttontext-element.md), který určuje název nabídky v integrovaném vývojovém prostředí a [CommandName – Element](../../extensibility/commandname-element.md), který určuje název, který je používané **příkaz** okna pro přístup k nabídce.  
  
- Volitelné příznaky. A [Command Flag – Element](../../extensibility/command-flag-element.md) může objevit v definici nabídce můžete změnit její vzhled nebo chování v integrovaném vývojovém prostředí.  
  
  Každý `Menu` element musí mít skupinu jako jeho nadřazeným prvkem, pokud není prvek ukotvitelné jako je například panel nástrojů. Ukotvitelné nabídka je vlastní nadřazený objekt. Další informace o nabídkách a hodnoty pro `type` atributu naleznete v tématu [Menu Element](../../extensibility/menu-element.md) dokumentaci.  
  
  Následující příklad ukazuje, které se zobrazí na řádku nabídek sady Visual Studio, vedle položky nabídky **nástroje** nabídky.  
  
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
 Skupinu je to položka, která je definována v `Groups` část souboru .vsct. Skupiny jsou pouze kontejnery. Se nezobrazují v integrovaném vývojovém prostředí s výjimkou jako zřejmý v nabídce. Proto [skupinového elementu](../../extensibility/group-element.md) je definována pouze jeho podpis, priority a nadřazené.  
  
 Skupina může mít nabídku, jinou skupinu nebo samotný jako nadřazený. Nadřazené je však obvykle nabídky nebo panelu nástrojů. V nabídce v předchozím příkladu je podřízeným prvkem `IDG_VS_MM_TOOLSADDINS` skupiny a skupiny je podřízeným prvkem řádku nabídek sady Visual Studio. Skupiny v následujícím příkladu je podřízeným prvkem v nabídce v předchozím příkladu.  
  
```  
 <Group guid="guidTopLevelMenuCmdSet" id="MyMenuGroup"  
priority="0x0600">  
   <Parent guid="guidTopLevelMenuCmdSet" id="TopLevelMenu"/>  
 </Group>  
```  
  
 Protože je součástí nabídky, tato skupina by obvykle obsahují příkazy. Ale mohou obsahovat také jiných nabídek. To je, jak jsou definované podnabídky, jak je znázorněno v následujícím příkladu.  
  
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
 Příkaz, který je k dispozici rozhraní IDE je definován jako buď [Button Element](../../extensibility/button-element.md) nebo [prvek pole se seznamem](../../extensibility/combo-element.md). Aby se zobrazovaly na nabídky nebo panelu nástrojů, musí mít příkaz skupinu jako jeho nadřazený objekt.  
  
##### <a name="buttons"></a>Tlačítka  
 Tlačítka jsou definovány v `Buttons` oddílu. Všechny položky nabídky, tlačítka nebo jiný element, který uživatel klikne na provedení jednoho příkazu je považován za tlačítko. Seznam funkcí mohou zahrnovat také některé typy tlačítek. Tlačítka mají stejné požadované a volitelné atributy, které mají nabídky, a může mít také [Icon – Element](../../extensibility/icon-element.md) , který určuje identifikátor GUID a ID rastrového obrázku, který představuje tlačítko v integrovaném vývojovém prostředí. Další informace o tlačítka a jejich atributy, najdete v článku [Buttons – Element](../../extensibility/buttons-element.md) dokumentaci.  
  
 Tlačítko v následujícím příkladu je podřízenou skupinu v předchozím příkladu a se zobrazí v integrovaném vývojovém prostředí jako položku nabídky v nabídce nadřazené skupiny.  
  
```  
<Button guid="guidTopLevelMenuCmdSet" id="cmdidTestCommand" priority="0x0100" type="Button">  
  <Parent guid="guidTopLevelMenuCmdSet" id="MyMenuGroup" />  
  <Icon guid="guidImages" id="bmpPic1" />  
  <Strings>  
    <CommandName>cmdidTestCommand</CommandName>  
    <ButtonText>Test Command</ButtonText>  
  </Strings>  
</Button>  
```  
  
##### <a name="combos"></a>Combos –  
 Combos – jsou definovány v `Combos` oddílu. Každý `Combo` element reprezentuje pole rozevíracího seznamu v integrovaném vývojovém prostředí. Pole se seznamem může nebo nemusí být zapisovat i jiní uživatelé, závisí na hodnotě `type` atribut pole se seznamem. Combos – mají stejné prvky a chování, které tlačítka mají a může mít také následující doplňkové atributy:  
  
- A `defaultWidth` atribut, který určuje šířka v pixelech.  
  
- `idCommandList` Atribut, který určuje seznam, který obsahuje položky, které se zobrazí v seznamu. Seznam příkazů musí být deklarována ve stejném `GuidSymbol` uzel, který obsahuje pole se seznamem.  
  
  Následující příklad definuje prvek pole se seznamem.  
  
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
 Musí obsahovat příkazy, které se zobrazí spolu s ikonou `Icon` element, který odkazuje na rastrový obrázek pomocí jeho identifikátoru GUID a ID. Každý rastrového obrázku je definován jako [rastrový obrázek Element](../../extensibility/bitmap-element.md) v `Bitmaps` oddílu. Pouze požadované atributy `Bitmap` definice jsou `guid` a `href`, která odkazuje na zdrojový soubor. Pokud zdrojový soubor pruh prostředků **usedList** atribut je také potřeba, seznam dostupných imagí v pruhu. Další informace najdete v tématu [rastrový obrázek Element](../../extensibility/bitmap-element.md) dokumentaci.  
  
### <a name="parenting"></a>Správa nadřazených  
 Následující pravidla určují, jak položku může volat jinou položku jako jeho nadřazený objekt.  
  
|Prvek|Definované v této části tabulky příkazů|Mohou být obsaženy (jako nadřazená nebo podle umístění v `CommandPlacements` části nebo obojí)|Může obsahovat (označované jako nadřazená)|  
|-------------|--------------------------------------------------|---------------------------------------------------------------------------------------------------|---------------------------------------------|  
|Skupina|[Groups – Element](../../extensibility/groups-element.md), rozhraní IDE, ostatní rozšíření VSPackages|Nabídka, skupiny, přímo s příslušnou položkou|Příkazy, nabídky a skupiny|  
|Nabídka|[Menus – Element](../../extensibility/menus-element.md), rozhraní IDE, ostatní rozšíření VSPackages|1 *n* skupiny|0 na *n* skupiny|  
|Panel nástrojů|[Menus – Element](../../extensibility/menus-element.md), rozhraní IDE, ostatní rozšíření VSPackages|Přímo s příslušnou položkou|0 na *n* skupiny|  
|Položka nabídky|[Tlačítka Element](../../extensibility/buttons-element.md), rozhraní IDE, ostatní rozšíření VSPackages|1 *n* ve skupině, přímo s příslušnou položkou|-0 pro *n* skupiny|  
|Tlačítko|[Tlačítka Element](../../extensibility/buttons-element.md), rozhraní IDE, ostatní rozšíření VSPackages|1 *n* ve skupině, přímo s příslušnou položkou||  
|Pole se seznamem|[Combos – Element](../../extensibility/combos-element.md), rozhraní IDE, ostatní rozšíření VSPackages|1 *n* ve skupině, přímo s příslušnou položkou||  
  
### <a name="menu-command-and-group-placement"></a>Nabídky, příkaz a skupiny umístění  
 Nabídky, skupiny nebo příkaz může zobrazit ve více než jedné oblasti v rozhraní IDE. Položky se zobrazí v několika umístěních, musí být přidané na `CommandPlacements` oddíl jako [commandplacement – Element](../../extensibility/commandplacement-element.md). Všechny nabídky, skupiny nebo příkaz lze přidat jako příkaz umístění. Panely nástrojů nelze však umístit tímto způsobem, protože se nemůže objevit v několika umístěních kontextové.  
  
 Příkaz umístění mají `guid`, `id`, a `priority` atributy. Identifikátor GUID a ID musí odpovídat ty položky, který je umístěn. `priority` Atribut určuje umístění položky s ohledem na další položky. Když rozhraní IDE Sloučí dvě nebo více položek, které mají stejnou prioritu, jejich umístění nejsou definovány, protože integrovaného vývojového prostředí nezaručuje, že se balíček prostředků ve stejném pořadí čtení pokaždé, když je sestaven balíček.  
  
 Nabídka nebo skupina se zobrazí v několika umístěních, zobrazí se všechny podřízené objekty z této nabídky nebo skupiny v každé instanci.  
  
## <a name="command-visibility-and-context"></a>Příkaz viditelnost a kontext  
 Při instalaci více balíčků VSPackage připojovaném nabídek, položky nabídky a panely nástrojů může dál sbližuje tyto integrovaného vývojového prostředí. K tomuto problému vyhnout, můžete řídit viditelnost jednotlivé prvky uživatelského rozhraní pomocí *viditelnost omezení* a příznaků příkazů.  
  
##### <a name="visibility-constraints"></a>Omezení viditelnosti  
 Viditelnost omezení je nastaven jako [visibilityitem – Element](../../extensibility/visibilityitem-element.md) v `VisibilityConstraints` oddílu. Přehled omezení definuje konkrétní kontexty uživatelského rozhraní, ve kterých je cílová položka viditelná. Nabídka nebo příkaz, který je zahrnuta v této části je viditelná pouze v případě, že jedna z definovaných kontexty je aktivní. Pokud příkazu nebo nabídky se neodkazuje v této části, je vždy zobrazen ve výchozím nastavení. Tato část se nevztahuje na skupiny.  
  
 `VisibilityItem` elementy musí mít tři atributy, následujícím způsobem: `guid` a `id` cílového prvku uživatelského rozhraní, a `context`. `context` Atribut určuje, kdy cílovou položku se nebude zobrazovat a přijímá libovolný platný kontext jako hodnotu uživatelského rozhraní. Konstanty kontextu uživatelského rozhraní pro sadu Visual Studio jsou členy <xref:Microsoft.VisualStudio.VSConstants> třídy. Každý `VisibilityItem` element může trvat pouze jeden kontext hodnotu. Druhý kontextu použít, vytvořte druhý `VisibilityItem` element, který odkazuje na jedné položce, jak je znázorněno v následujícím příkladu.  
  
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
  
##### <a name="command-flags"></a>Příkaz příznaky  
 Následující příkaz příznaky mohou ovlivnit viditelnost nabídek a příkazů, které se vztahují na.  
  
 AlwaysCreate  
 Nabídka se vytvoří i v případě, že nemá žádné skupiny ani tlačítka.  
  
 Platí pro: `Menu`  
  
 CommandWellOnly  
 Použijte tento příznak Pokud tento příkaz nezobrazí v nabídce nejvyšší úrovně a chcete ji dejte k dispozici pro přizpůsobení další prostředí, například jeho vazbu klíče. Po instalaci sady VSPackage, může uživatel přizpůsobit tyto příkazy tak, že otevřete **možnosti** dialogové okno a poté úpravou příkaz umístění v rámci **klávesnice prostředí** kategorie. Nemá vliv na umístění v místní nabídky, panely nástrojů, nabídky řadiče nebo dílčích nabídek.  
  
 Platné pro: `Button`, `Combo`  
  
 DefaultDisabled  
 Ve výchozím nastavení příkaz zakázaná, pokud není načtena sady VSPackage, která implementuje příkaz nebo nebyla zavolána metoda QueryStatus.  
  
 Platné pro: `Button`, `Combo`  
  
 DefaultInvisible  
 Ve výchozím nastavení příkaz je neviditelný, pokud sady VSPackage, která implementuje příkazu nebyla načtena, nebo nebyla zavolána metoda QueryStatus.  
  
 By měly být kombinované pomocí `DynamicVisibility` příznak.  
  
 Platné pro: `Button`, `Combo`, `Menu`  
  
 DynamicVisibility  
 Viditelnost příkazu můžete změnit pomocí metody QueryStatus nebo kontextu identifikátor GUID, který je součástí `VisibilityConstraints` oddílu.  
  
 Platí pro příkazy, které se zobrazují v nabídkách, ne na panely nástrojů. Položky panelu nástrojů nejvyšší úrovně můžete zakázané, ale není skrytý, pokud příznak OLECMDF_INVISIBLE vrátí z metody QueryStatus.  
  
 V nabídce tento příznak také určuje, že ho automaticky skryt, pokud její členové budou skryti. Tento příznak se obvykle přiřadí podnabídek vzhledem k tomu, že už máte toto chování nabídek nejvyšší úrovně.  
  
 By měly být kombinované pomocí `DefaultInvisible` příznak.  
  
 Platné pro: `Button`, `Combo`, `Menu`  
  
 NoShowOnMenuController  
 Pokud příkaz, který má tento příznak je umístěn na kontroleru nabídky, příkaz se v rozevíracím seznamu nezobrazí.  
  
 Platí pro: `Button`  
  
 Další informace o příznaků příkazů najdete v článku [Command Flag – Element](../../extensibility/command-flag-element.md) dokumentaci.  
  
##### <a name="general-requirements"></a>Obecné požadavky  
 Váš příkaz musí projít následující série testů předtím, než je možné zobrazit a povoleno:  
  
-   Příkaz je správně umístěná.  
  
-   `DefaultInvisible` Není nastaven příznak.  
  
-   Nadřazené nabídky nebo panelu nástrojů je viditelný.  
  
-   Příkaz není kvůli kontextu položku v neviditelná [visibilityconstraints – Element](../../extensibility/visibilityconstraints-element.md) oddílu.  
  
-   VSPackage kód, který implementuje <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> rozhraní zobrazuje a umožňuje svých rukou. Žádný kód rozhraní zachytili ji a u něj.  
  
-   Když uživatel klikne na svých rukou, bude v souladu s postupem, který je popsaný v [algoritmus směrování](../../extensibility/internals/command-routing-algorithm.md).  
  
## <a name="calling-pre-defined-commands"></a>Volání metody předdefinovaných příkazů  
 [Usedcommands – Element](../../extensibility/usedcommands-element.md) rozšíření VSPackages umožňuje přístup k příkazům, které jsou k dispozici další balíčky VSPackages nebo integrovaného vývojového prostředí. K tomuto účelu vytvořte [usedcommand – Element](../../extensibility/usedcommand-element.md) , který má identifikátor GUID a ID příkazu k použití. Tím se zajistí, že příkaz načtou pomocí sady Visual Studio, i když to není součástí aktuální konfiguraci sady Visual Studio. Další informace najdete v tématu [usedcommand – Element](../../extensibility/usedcommand-element.md).  
  
## <a name="interface-element-appearance"></a>Vzhled elementu rozhraní  
 Důležité informace pro výběr a umístění prvků příkazu jsou následující:  
  
-   [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] nabízí mnoho prvků uživatelského rozhraní, které se zobrazují odlišně v závislosti na umístění.  
  
-   Prvek uživatelského rozhraní, který je definován pomocí `DefaultInvisible` příznak se nezobrazí v integrovaném vývojovém prostředí, pokud to není buď zobrazí jeho implementace VSPackage <xref:EnvDTE.IDTCommandTarget.QueryStatus%2A> metodu, nebo ve spojení s konkrétním kontextu uživatelského rozhraní v `VisibilityConstraints` oddílu.  
  
-   Úspěšně umístěné příkaz se nemusí zobrazit. Toto je vzhledem k tomu, že rozhraní IDE automaticky skryje nebo zobrazí některé příkazy, v závislosti na rozhraní, které sady VSPackage má (nebo ne) implementováno. Například na VSPackage provádění některých sestavení rozhraní položky související s buildem nabídky způsobí, že má být zobrazen automaticky.  
  
-   Použití `CommandWellOnly` příznak v definici prvku uživatelského rozhraní znamená, že příkaz lze přidat pouze pomocí vlastního nastavení.  
  
-   Příkazy mohou být k dispozici pouze v určitých uživatelského rozhraní kontextech, například pouze v případě, že po integrovaného vývojového prostředí v návrhovém zobrazení, zobrazí se dialogové okno.  
  
-   Způsobí některé prvky uživatelského rozhraní, který se má zobrazit v integrovaném vývojovém prostředí, musí implementovat jedno nebo více rozhraní nebo napsat kód.  
  
## <a name="see-also"></a>Viz také  
 [Rozšiřování nabídek a příkazů](../../extensibility/extending-menus-and-commands.md)

