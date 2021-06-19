---
title: Soubor DslDefinition.dsl
description: Seznamte se se strukturou souboru DslDefinition. DSL v projektu DSL v řešení DSL nástrojů DSL, které definuje jazyk specifický pro doménu.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, definition file
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 3f2e2ae6e406b8967cb7de49573ce5b26377806e
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2021
ms.locfileid: "112388630"
---
# <a name="the-dsldefinitiondsl-file"></a>Soubor DslDefinition.dsl

Toto téma popisuje strukturu souboru DslDefinition. DSL v projektu DSL [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] řešení, který definuje *jazyk specifický pro doménu*. Soubor DslDefinition. DSL popisuje třídy a vztahy jazyka specifického pro doménu spolu s diagramem, tvary, konektory, formátem serializace a sadou **nástrojů** jazyka specifického pro doménu a jejich editačních nástrojů. V řešení jazyka specifického pro doménu se kód, který definuje tyto nástroje, generuje podle informací v souboru DslDefinition. DSL.

Obecně platí, že pomocí *Návrháře jazyka specifického pro doménu* upravíte soubor DslDefinition. DSL. Nezpracovaný formulář je ale XML a v editoru XML můžete otevřít soubor DslDefinition. DSL. Může být užitečné pochopit, jaké informace soubor obsahuje, a jak je uspořádán pro účely ladění a rozšíření.

Příklady v tomto tématu jsou pořízeny ze šablony řešení diagramu komponent. Chcete-li zobrazit příklad, vytvořte řešení jazyka specifického pro doménu, které je založeno na šabloně řešení modelů komponent. Po vytvoření řešení se soubor DslDefinition. DSL zobrazí v návrháři jazyka Domain-Specific. Zavřete soubor, klikněte na něj pravým tlačítkem **Průzkumník řešení**, přejděte na **otevřít** v, klikněte na **Editor XML** a pak klikněte na **OK**.

## <a name="sections-of-the-dsldefinitiondsl-file"></a>Části souboru DslDefinition. DSL

Kořenový element je \<Dsl> a jeho atributy identifikují název jazyka specifického pro doménu, obor názvů a číslo hlavní a dílčí verze pro správu verzí. `DslDefinitionModel`Schéma definuje obsah a strukturu pro platný soubor DslDefinition. DSL.

Podřízené prvky \<Dsl> kořenového elementu jsou následující:

### <a name="classes"></a>Třídy

Tato část definuje každou doménovou třídu, která generuje třídu v generovaném kódu.

### <a name="relationships"></a>Relace

Tato část definuje všechny relace v modelu. Zdroj a cíl reprezentují dvě strany vztahu.

### <a name="types"></a>Typy

Tato část definuje každý typ a jeho obor názvů. Doménové vlastnosti mají dva typy. `DomainEnumerations` jsou definovány v modelu a generují typy do DomainModel. cs. `ExternalTypes` odkazují na typy, které jsou definovány jinde (například `String` nebo `Int32` ) a negenerují cokoli.

### <a name="shapes"></a>Obrazce

Tato část definuje tvary, které popisují, jak se model zobrazuje v návrháři. Tyto geometrické obrazce jsou mapovány na třídy v modelu v oddílu diagramu.

### <a name="connectors"></a>Konektory

Tato část definuje vzhled konektorů, které se zobrazují v návrháři. Tyto popisy geometrického stylu jsou mapovány na konkrétní vztahy v modelu v oddílu diagramu.

### <a name="xmlserializationbehavior"></a>XmlSerializationBehavior

Tato část definuje schéma serializace a poskytuje další informace o tom, jak jsou jednotlivé třídy uloženy do souboru.

### <a name="explorerbehavior"></a>ExplorerBehavior

V této části se definuje způsob, jakým se zobrazí okno **Průzkumníka DSL** , když uživatel upravuje model.

### <a name="connectionbuilders"></a>ConnectionBuilders

Tato část definuje Tvůrce připojení pro jednotlivé nástroje konektoru (Nástroj pro vytváření odkazů mezi všemi dvěma třídami, které se dají připojit). Tato část určuje, zda lze připojit zdrojovou a cílovou třídu.

### <a name="diagram"></a>Diagram

Tato část definuje diagram a použijete jej k určení vlastností, jako je například barva pozadí a kořenová třída. (Kořenová třída je doménová třída, která je znázorněna v diagramu jako celek.) Oddíl diagramu obsahuje také prvky ShapeMap a ConnectorMap, které určují tvar nebo spojnici, které představují každou doménovou třídu nebo vztah.

### <a name="designer"></a>Návrhář

Tato část definuje návrháře (Editor), který spojuje sadu **nástrojů**, nastavení ověřování, diagram a schéma serializace. Oddíl návrháře také definuje kořenovou třídu modelu, která je obvykle také kořenovou třídou diagramu.

### <a name="explorer"></a>Průzkumník

Tato část identifikuje chování **Průzkumníka DSL** (definované v části XmlSerializationBehavior).

## <a name="monikers-in-the-dsldefinitiondsl-file"></a>Monikery v souboru DslDefinition. DSL

V celém souboru DslDefinition. DSL můžete použít monikery k vytvoření křížových odkazů na konkrétní položky. Například každá definice vztahu obsahuje zdrojový dílčí oddíl a cílový dílčí oddíl. Každý pododdíl obsahuje moniker třídy objektu, který lze propojit s tímto vztahem:

```xml
<DomainRelationship ...        Name="LibraryHasMembers" Namespace="ExampleNamespace" >    <Source>      <DomainRole ...>
       <RolePlayer>
         <DomainClassMoniker Name="Library" />
       </RolePlayer>
     </DomainRole>
   </Source>
```

Obor názvů odkazované položky (v tomto příkladu je `Library` doménová třída) je obvykle stejný jako odkazující položka (v tomto případě vztah domény LibraryHasMembers). V těchto případech moniker musí poskytovat pouze název třídy. V opačném případě byste měli použít úplnou formu/Namespace/Name:

```xml
<DomainClassMoniker Name="/ExampleNameSpace/Library" />
```

Monikerový systém vyžaduje, aby na stejné úrovni ve stromu XML měly odlišné názvy. Z tohoto důvodu dojde k chybám ověřování při pokusu o uložení definice jazyka specifického pro doménu, která obsahuje například dvě třídy se stejným názvem. Před uložením souboru DslDefinition. DSL byste měli vždycky opravit tyto chyby duplicitních názvů, abyste je mohli správně znovu načíst.

Každý typ má svůj vlastní typ monikeru: DomainClassMoniker, DomainRelationshipMoniker a tak dále.

## <a name="types"></a>Typy

Oddíl Types určuje všechny typy, které soubor DslDefinition. DSL obsahuje jako typy vlastností. Tyto typy spadají do dvou typů: externí typy, jako například System. String a výčtové typy.

### <a name="external-types"></a>Externí typy

Příklad diagramu komponenty obsahuje sadu standardních primitivních typů, i když jsou použity pouze některé z nich.

Každá definice externího typu se skládá pouze z názvu a oboru názvů, jako je například String a System:

```xml
<ExternalType Name="String" Namespace="System" />
```

Místo ekvivalentních klíčových slov kompilátoru, jako je řetězec, se použijí úplné názvy typů.

Externí typy nejsou omezeny na standardní typy knihoven.

### <a name="enumerations"></a>Výčty

Typická specifikace výčtu vypadá podobně jako v tomto příkladu:

```xml
<DomainEnumeration IsFlags="true" Name="PageSort"          Namespace="Fabrikam.Wizard">
  <Literals>
    <EnumerationLiteral Name="Start" Value="1"/>
    <EnumerationLiteral Name="Decision" Value="2"/>
  </Literals>
</DomainEnumeration>
```

Atribut určuje, `IsFlags` zda je generovaný kód předponou `[Flags]` atributu Common Language Runtime (CLR), který určuje, zda lze hodnoty výčtu kombinovat bitové. Pokud je tento atribut nastaven na hodnotu true, měli byste zadat hodnoty mocniny pro hodnoty literálu.

## <a name="classes"></a>Třídy

Většina prvků v jakékoli definici jazyka specifického pro doménu je buď přímo, nebo nepřímo instancí `DomainClass` . Podtřídy `DomainClass` include `DomainRelationship` ,, a `Shape` `Connector` `Diagram` . `Classes`Oddíl souboru DslDefinition. DSL obsahuje seznam tříd domény.

Každá třída má sadu vlastností a může mít základní třídu. V příkladu diagramu komponent `NamedElement` je abstraktní třída, která má `Name` vlastnost, jejíž typ je řetězec:

```xml
<DomainClass Id="ee3161ca-2818-42c8-b522-88f50fc72de8"  Name="NamedElement" Namespace="Fabrikam.CmptDsl5"      DisplayName="Named Element"  InheritanceModifier="Abstract">
  <Properties>
    <DomainProperty Id="ef553cf0-33b5-4e34-a30b-cfcfd86f2261"   Name="Name" DisplayName="Name"  DefaultValue="" Category="" IsElementName="true">
      <Type>
        <ExternalTypeMoniker Name="/System/String" />
      </Type>
    </DomainProperty>
  </Properties>
</DomainClass>
```

`NamedElement` je základem několika dalších tříd, jako `Component` je například, které mají vlastní vlastnosti kromě `Name` vlastnosti, kterou dědí z `NamedElement` . Podřízený uzel BaseClass obsahuje odkaz monikeru. Vzhledem k tomu, že odkazovaná třída je ve stejném oboru názvů, je v monikeru vyžadován pouze jeho název:

```xml
<DomainClass Name="Component" Namespace="Fabrikam.CmptDsl5"              DisplayName="Component">
  <BaseClass>
    <DomainClassMoniker Name="NamedElement" />
  </BaseClass>
  <Properties>
    <DomainProperty Name="Kind" DisplayName="Kind" >
      <Type>
        <ExternalTypeMoniker Name="/System/String" />
      </Type>
    </DomainProperty>
  </Properties>
```

Každá doménová třída (včetně vztahů, tvarů, konektorů a diagramů) může mít tyto atributy a podřízené uzly:

- **ID.** Tento atribut je identifikátor GUID. Pokud nezadáte hodnotu v souboru, Návrhář Domain-Specificho jazyka vytvoří hodnotu. (Na obrázcích v tomto dokumentu je tento atribut obvykle vynechán pro ukládání prostoru.)

- **Název a obor názvů.** Tyto atributy určují název a obor názvů třídy ve vygenerovaném kódu. Dohromady musí být jedinečné v rámci jazyka specifického pro doménu.

- **InheritanceModifier.** Tento atribut je "Abstract", "sealed" nebo None.

- **DisplayName.** Tento atribut je název, který se zobrazí v okně **vlastnosti** . Atribut DisplayName může obsahovat mezery a další interpunkční znaménka.

- **GeneratesDoubleDerived.** Pokud je tento atribut nastaven na hodnotu true, jsou generovány dvě třídy a jedna je podtřídou druhé. Všechny vygenerované metody jsou v základní třídě a konstruktory jsou v podtřídě. Nastavením tohoto atributu můžete přepsat libovolnou vygenerovanou metodu ve vlastním kódu.

- **HasCustomConstructor**. Pokud je tento atribut nastaven na hodnotu true, je z generovaného kódu vynechán konstruktor, takže můžete napsat vlastní verzi.

- **Atributy**. Tento atribut obsahuje atributy CLR generované třídy.

- **BaseClass**. Pokud zadáte základní třídu, musí být stejného typu. Například doménová třída musí mít jako základ jinou doménovou třídu a tvar oddílu musí mít tvar oddílu. Pokud nezadáte základní třídu, třída v generovaném kódu je odvozena ze standardní třídy rozhraní. Například doménová třída je odvozena z `ModelElement` .

- **Vlastnosti**. Tento atribut obsahuje vlastnosti, které jsou udržovány v řízení transakcí a trvalé při uložení modelu.

- **ElementMergeDirectives**. Každá direktiva sloučení element řídí, jak je přidána jiná instance jiné třídy do instance nadřazené třídy. Další podrobnosti o direktivách sloučení elementů najdete dále v tomto tématu.

- Třída jazyka C# je vygenerována pro každou doménovou třídu, která je uvedena v `Classes` části. Třídy jazyka C# jsou vygenerovány v Dsl\GeneratedCode\DomainClasses.cs.

### <a name="properties"></a>Vlastnosti

Každá doménová vlastnost má název a typ. Název musí být jedinečný v rámci třídy domény a jeho přenositelného základu.

Typ musí odkazovat na jednu z těch, které jsou uvedeny v `Types` části. Obecně platí, že moniker musí zahrnovat obor názvů.

```xml
<DomainProperty Name="Name" DisplayName="Name"  DefaultValue="" Category="" IsElementName="true">
  <Type>
    <ExternalTypeMoniker Name="/System/String" />
  </Type>
</DomainProperty>
```

Každá doménová vlastnost může mít také tyto atributy:

- Nelze **Procházet**. Tento atribut určuje, zda se vlastnost zobrazí v okně **vlastnosti** , když uživatel klikne na objekt nadřazené třídy.

- **IsUIReadOnly**. Tento atribut určuje, zda může uživatel změnit vlastnost v okně **vlastnosti** nebo prostřednictvím dekoratér, ve kterém je vlastnost uvedena.

- **Druh**. Tento atribut můžete nastavit na normální, vypočtený nebo nemá CustomStorage. Pokud tento atribut nastavíte na hodnotu vypočítat, je nutné zadat vlastní kód, který určuje hodnotu a vlastnost bude jen pro čtení. Pokud tento atribut nastavíte na nemá CustomStorage, je nutné zadat kód, který získá a nastaví hodnoty.

- **Element elementu**. Pokud je tento atribut nastaven na hodnotu true, jeho hodnota se automaticky nastaví na jedinečnou hodnotu, když je vytvořena instance nadřazené třídy. Tento atribut může být nastaven na hodnotu true pouze pro jednu vlastnost v každé třídě, která musí mít typ String. V příkladu diagramu komponent je `Name` vlastnost v `NamedElement` `IsElementName` nastavena na hodnotu true. Pokaždé, když uživatel vytvoří `Component` prvek (který dědí z `NamedElement` ), název se automaticky inicializuje do nějakého typu "Component6".

- `DefaultValue`. Pokud jste zadali tento atribut, hodnota, kterou jste zadali, je přiřazena tomuto atributu pro nové instance této třídy. Pokud `IsElementName` je nastaveno, atribut DefaultValue Určuje počáteční část nového řetězce.

- **Kategorie** je záhlaví, pod kterým se vlastnost zobrazí v okně **vlastnosti** .

## <a name="relationships"></a>Relace

V `Relationships` části jsou uvedeny všechny relace v jazyce specifickém pro doménu. Každé `Domain Relationship` je binární a směrované, propojuje členy zdrojové třídy s členy cílové třídy. Zdrojové a cílové třídy jsou obvykle doménové třídy, ale vztahy k ostatním vztahům jsou také povoleny.

Vztah připojení například spojuje členy třídy pro vystavení s členy třídy InPort. Každá instance propojení relace spojuje instanci externího portu s instancí InPort. Vzhledem k tomu, že je relace hodně mnoho, každý z nich může mít k dispozici mnoho propojení s prostředky a každá instance pro inportování může mít mnoho odkazů na připojení, které cílí na ni.

### <a name="source-and-target-roles"></a>Zdrojové a cílové role

Každý vztah obsahuje zdrojové a cílové role, které mají následující atributy:

- `RolePlayer`Atribut odkazuje na doménovou třídu propojených instancí: mimo port pro zdroj, port pro cíl.

- `Multiplicity`Atribut má čtyři možné hodnoty (ZeroMany, ZeroOne, One a OneMany). Tento atribut odkazuje na počet odkazů tohoto vztahu, které mohou být přidruženy k jednomu aktéru role.

- `PropertyName`Atribut určuje název, který se používá v třídě aktér role pro přístup k objektům na druhém konci. Tento název se používá v šabloně nebo vlastním kódu pro procházení relace. Například `PropertyName` atribut zdrojové role je nastaven na `Targets` . Proto bude fungovat následující kód:

    ```
    OutPort op = ...; foreach (InPort ip in op.Targets) ...
    ```

     Podle konvence jsou názvy vlastností plural, pokud je násobnost ZeroMany nebo OneMany.

     Násobnost role odkazuje na to, kolik opačných rolí může být přidruženo k jednotlivým instancím této role. Například ve vztahu ComponentHasPorts má cílová role `RolePlayer` atribut nastaven na port, `PropertyName` atribut nastavený na součást a `Multiplicity` atribut nastavený na hodnotu ZeroOne. Proto je vhodný kód pro použití této role:

    ```
    ComponentPort p = ...; Component c = p.Component; if (c != null) ...
    ```

- Role `Name` je název, který se používá v rámci třídy Relationship k odkazování na tento konec odkazu. Podle konvence je název role vždycky v jednotném čísle, protože každý odkaz má na každém konci jenom jednu instanci. Následující kód bude fungovat:

    ```
    Connection connectionLink = ...; OutPort op = connectionLink.Source;
    ```

- Ve výchozím nastavení `IsPropertyGenerator` je atribut nastaven na hodnotu true. Pokud je nastavená na false, není ve třídě aktéra role vytvořená žádná vlastnost. (V takovém případě `op.Targets` například nefungují). Je však stále možné použít vlastní kód k procházení vztahu nebo získat přístup k vlastním odkazům, pokud vlastní kód používá vztah explicitně:

    ```
    OutPort op = ...; foreach (InPort ip in Connection.GetTargets(op)) ...
    foreach (Connection link in Connection.GetLinksToTargets(op)) ...
    ```

### <a name="relationship-attributes"></a>Atributy vztahu

Kromě atributů a podřízených uzlů, které jsou k dispozici pro všechny třídy, má každá relace tyto atributy:

- Probíhá **vkládání**. Tento logický atribut určuje, zda je vztah součástí stromu vkládání. Každý model musí tvořit strom se svými vztahy vložení. Každá doménová třída musí být proto cílem alespoň jednoho vztahu vložení, pokud se nejedná o kořen modelu.

- **AllowsDuplicates**. Tento logický atribut, který je ve výchozím nastavení false, se vztahuje pouze na relace, které mají "mnoho" násobnosti na zdroji i v cíli. Určuje, zda mohou uživatelé jazyka propojit jednu dvojici zdrojového a cílového prvku více než jedním propojením stejné relace.

## <a name="designer-and-toolbox-tabs"></a>Karty návrháře a panelu nástrojů

Hlavní část oddílu **Návrháře** souboru DslDefinition. DSL je **karta panelu nástrojů** prvky. Jeden Návrhář může mít několik z těchto elementů, z nichž každý představuje oddíl s přístavou v **sadě nástrojů** vygenerovaných prvků návrháře. Každý element **karta panelu nástrojů** může obsahovat jeden nebo více **Nástroj elementu** prvků, **ConnectionTool** elementy nebo obojí.

Nástroje elementu můžou vytvářet instance konkrétní doménové třídy. Když uživatel přetáhne nástroj elementu do diagramu, výsledek je určen pomocí direktiv sloučení elementů, jak je popsáno v části o direktivách sloučení elementů dále v tomto tématu.

Každý nástroj pro připojení může vyvolat konkrétní Tvůrce připojení. Jeden Tvůrce připojení může vytvořit více než jeden typ relace v závislosti na tom, kde uživatel klikne na myš, jak je popsáno v části o sestavách připojení.

Žádný typ nástroje přímo nevytváří tvary ani konektory. Každá vytvoří instanci doménové třídy nebo doménového vztahu. mapování obrazce a konektoru pak určuje, jak se zobrazí tato doménová třída nebo doménový vztah.

## <a name="paths"></a>Cesty

Cesty k doméně se zobrazí v několika umístěních v souboru DslDefinition. DSL. Tyto cesty určují řadu odkazů z jednoho prvku v modelu (to znamená instance jazyka specifického pro doménu) do jiného. Syntaxe cesty je jednoduchá, ale je podrobná.

Cesty se zobrazí v souboru DslDefinition. DSL ve `<DomainPath>...</DomainPath>` značkách. I když cesty můžou procházet více odkazy, většina příkladů v praxi prochází pouze jedním odkazem.

Cesta se skládá z sekvence segmentů. Každý segment je skok buď z objektu na odkaz, nebo z odkazu na objekt. Proto se směrování obvykle střídavě používá v dlouhém umístění. První segment směrování je z objektu na odkaz, druhým směrováním je objekt na druhém konci propojení, třetí segment směrování je další odkaz atd. Výjimkou příležitostného použití této sekvence je, že vztah je sám zdrojem nebo cílem jiného vztahu.

Každý segment začíná názvem relace. V případě směrování mezi objekty a propojením předchází tento vztah tečku a název vlastnosti: " `Relationship . Property` ". V případě směrování propojení mezi objekty a vztahu předchází vykřičník a název role: " `Relationship ! Role` ".

Příklad diagramu komponenty obsahuje cestu v ParentElementPath ShapeMap pro InPort. Tato cesta začíná takto:

```
    ComponentHasPorts.Component
```

V tomto příkladu je InPort podtřídou třídy ComponentPort a má ComponentHasPorts vztahu. Vlastnost se nazývá součást.

Při psaní v jazyce C# proti tomuto modelu můžete přejít přes propojení v jednom kroku pomocí vlastnosti, kterou vztah generuje na každé ze tříd, které se týkají:

```
     InPort port; ...  Component c = port.Component;
```

V syntaxi cesty ale musíte explicitně provést oba segmenty směrování. Kvůli tomuto požadavku máte přístup k přechodnému propojení snadněji. Následující kód dokončí segment směrování z odkazu na komponentu:

```
    ComponentHasPorts.Component / ! Component
```

(Název relace můžete vynechat, pokud je stejný jako v předchozím segmentu.)

## <a name="element-merge-directives"></a>Direktivy sloučení elementů

Když uživatel jazyka přetáhne položku z panelu **nástrojů** do diagramu, je vytvořena instance třídy nástroje. Mezi tuto instancí a existujícími prvky modelu jsou také provedeny odkazy. Některé položky, například komponenty nebo komentáře, se vytvoří, když  je uživatel jazyka přetáhne z panelu nástrojů na prázdnou část diagramu. Další položky se vytvoří, když je uživatel jazyka přetáhne na jiné prvky hostitele. Například port OutPort nebo InPort se vytvoří, když ho uživatel jazyka přetáhne do komponenty.

Potenciální hostitelská třída, například Component, přijme nový prvek pouze v případě, že hostitelská třída má direktivu sloučení elementů pro třídu nového prvku. Například uzel DomainClass s názvem Name="Component" obsahuje:

```xml
<DomainClass Name="Component" ...> ...
    <ElementMergeDirective>
      <Index>
        <DomainClassMoniker Name="ComponentPort" />
      </Index>
      <LinkCreationPaths>
        <DomainPath>ComponentHasPorts.Ports</DomainPath>
      </LinkCreationPaths>
    </ElementMergeDirective> ...
```

Moniker třídy, který je v uzlu Index, odkazuje na třídu elementu, který lze přijmout. V tomto případě je ComponentPort abstraktní základní třídou InPort a OutPort. Proto může být některý z těchto prvků přijat.

ComponentModel, kořenová třída jazyka, obsahuje direktivy sloučení elementů pro komponenty a komentáře. Uživatel jazyka může přetáhnout položky pro tyto třídy přímo do diagramu, protože prázdné části diagramu představují kořenovou třídu. KomponentModel ale nemá žádnou direktivu sloučení elementů pro ComponentPort. Uživatel jazyka proto nemůže přetáhnout porty InPorts ani OutPorts přímo do diagramu.

Direktiva sloučení elementu určuje, jaké propojení nebo propojení jsou vytvořeny, aby nový prvek mohl integrovat nebo sloučit do existujícího modelu. Pro ComponentPort se vytvoří instance ComponentHasPorts. DomainPath identifikuje vztah a vlastnost nadřazené třídy Ports, do které se přidá nový prvek.

Můžete vytvořit více než jedno propojení na direktivu sloučení elementu zahrnutím více než jedné cesty pro vytvoření odkazu. Jedna z cest musí být vložená.

V cestě pro vytvoření odkazu můžete použít více než jeden segment. V tomto případě poslední segment definuje, jaký odkaz se musí vytvořit. Dřívější segmenty přecházely z nadřazené třídy do objektu, ze kterého by se mělo vytvořit nové propojení.

Například můžete přidat tuto direktivu elementu merge do třídy Component:

```xml
<DomainClass Name="Component" ...> ...
  <ElementMergeDirective>
    <Index>
       <DomainClassMoniker Name="Comment"/>
    </Index>
    <LinkCreationPaths>
       <DomainPath>          ComponentModelHasComponents . ComponentModel / !ComponentModel         / ComponentModelHasComments.Comments       </DomainPath>
       <DomainPath>CommentsReferenceComponents.Comments</DomainPath>
    </LinkCreationPaths>
  </ElementMergeDirective>
```

Uživatelé jazyka pak mohou přetáhnout komentář na komponentu a vytvořit nový komentář automaticky s odkazem na komponentu.

První cesta pro vytvoření odkazu přejde z na a pak vytvoří `Component` `ComponentModel` instanci vztahu vkládání `ComponentModelHasComments` . Druhá cesta pro vytvoření odkazu vytvoří propojení referenční relace CommentsReferenceComponents z hostitelské komponenty na nový komentář. Všechny cesty pro vytvoření odkazu musí začínát třídou hostitelů a musí končít odkazem, který postupuje směrem k nově vytvořené třídě.

## <a name="xmlclassdata"></a>XmlClassData

Každá třída domény (včetně relací a dalších podtypů) může mít v uzlu další informace, které se zobrazí v části souboru `XmlClassData` `XmlSerializationBehavior` DslDefinition.dsl. Tyto informace se konkrétně týkají, jak jsou instance třídy uloženy v serializovaném tvaru při uložení modelu do souboru.

Velká část generovaného kódu, který `XmlSerializationBehavior` ovlivňuje , je v `Dsl\GeneratedCode\Serializer.cs` .

Každý `XmlClassData` uzel obsahuje tyto podřízené uzly a atributy:

- Uzel monikeru, který odkazuje na třídu, na kterou se data vztahují.

- **XmlPropertyData** pro každou vlastnost, která je definována ve třídě.

- **XmlRelationshipData** pro každou relaci, která je zdrojem ve třídě . (Relace mají také vlastní uzly XmlClassData.)

- **Atribut řetězce TypeName,** který určuje název třídy pomocná serializace ve vygenerované kódu.

- **Řetězec ElementName,** který určuje značku XML serializovaných instancí této třídy. Podle konvence je ElementName obvykle stejný jako název třídy s výjimkou prvního písmene malými písmeny. Ukázkový soubor modelu například začíná následujícím kódem:

    ```xml
    <componentModel ...
    ```

- **MonikerElementName** v serializovaných souborech modelu uživatele Tento atribut zavádí moniker, který odkazuje na tuto třídu.

- **MonikerAttributeName**, který identifikuje název atributu XML v rámci monikeru. V tomto fragmentu serializovaného souboru uživatele autor jazyka specifického pro doménu definoval **MonikerElementName** jako "inPortMoniker" a **MonikerAttributeName** jako "path":

    ```xml
    <inPortMoniker path="//Component2/InPort1" />
    ```

### <a name="connectionbuilders"></a>ConnectionBuilders

Tvůrce připojení je definován pro každý nástroj pro připojení. Každý tvůrce připojení se skládá z jednoho nebo více elementů LinkConnectDirective, z nichž každý obsahuje jeden nebo více prvků SourceDirective a jeden nebo více elementů TargetDirective. Po kliknutí na nástroj pro připojení může uživatel spustit připojení z libovolného obrazce namapovaného na prvek modelu, který se zobrazí v seznamu prvků SourceDirective. Připojení lze poté dokončit u obrazce, který je namapován na prvek, který se zobrazí v seznamu prvků TargetDirective. Instance třídy relace závisí na elementu LinkConnectDirective určeném tím, kde bylo připojení zahájeno.

### <a name="xmlpropertydata"></a>XmlPropertyData

Atribut **DomainPropertyMoniker** identifikuje vlastnost, na kterou data odkazují. Tento atribut musí být vlastnost nadřazené třídy ClassData.

Atribut **XmlName** dává odpovídající název atributu tak, jak by se měl zobrazit v XML. Podle konvence je tento řetězec stejný jako název vlastnosti s výjimkou prvního písmena malými písmeny.

Ve výchozím nastavení je **atribut Representation** nastavený na Attribute. Pokud **representation** je nastavena na Element, podřízený uzel je vytvořen v XML. Pokud **representation** je nastavena na Ignore, vlastnost není serializován.

Atributy **IsMonikerKey** a **IsMonikerQualifier** poskytují vlastnost roli při identifikaci instancí nadřazené třídy. **IsMonikerKey můžete nastavit** na true pro jednu vlastnost, která je definována v třídě nebo zděděna třídou . Tento atribut identifikuje jednotlivou instanci nadřazené třídy. Vlastnost, kterou nastavíte na `IsMonikerKey` , je obvykle název nebo jiný identifikátor klíče. Například vlastnost `Name` string je klíč monikeru pro NamedElement a jeho odvozené třídy. Když uživatel uloží model do souboru, musí tento atribut obsahovat jedinečné hodnoty pro každou instanci mezi svými objekty na stejné úrovni ve stromu vkládacích relací.

V serializovaném souboru modelu je úplným monikerem elementu cesta z kořenového adresáře modelu ve stromu vkládaného vztahu a v každém bodě uvozuje klíč monikeru. Například porty InPorts jsou vložené v komponentách, které jsou zase vložené v kořenovém adresáři modelu. Platným monikerem je proto:

```xml
<inPortMoniker name="//Component2/InPort1" />
```

Můžete nastavit atribut **IsMonikerQualifier** pro vlastnost řetězce a poskytnout další způsob, jak vytvořit úplný název elementu. Například v souboru DslDefinition.dsl je obor **názvů** kvalifikátor monikeru.

### <a name="xmlrelationshipdata"></a>XmlRelationshipData

V rámci serializovaného souboru modelu jsou odkazy (vztahů vložení i odkazu) reprezentovány podřízenými uzly zdrojového konce relace. Pro vkládání relací obsahuje podřízený uzel podstrom. Pro referenční relace obsahuje podřízený uzel moniker, který odkazuje na jinou část stromu.

Atribut **XmlRelationshipData** v atributu **XmlClassData** přesně definuje způsob vnoření podřízených uzlů do zdrojového elementu. Každá relace, která je zdrojem ve třídě Domény, má jeden **atribut XmlRelationshipData.**

Atribut **DomainRelationshipMoniker** identifikuje jednu z relací, které jsou zdrojem ve třídě .

Atribut **RoleElementName** poskytuje název značky XML, který uzavírá podřízený uzel v serializovaných datech.

Například soubor DslDefinition.dsl obsahuje:

```xml
<XmlClassData ElementName="component" ...>
  <DomainClassMoniker Name="Component" />
  <ElementData>
    <XmlRelationshipData RoleElementName="ports">
      <DomainRelationshipMoniker Name="ComponentHasPorts" />
    </XmlRelationshipData>
```

Proto serializovaný soubor obsahuje:

```xml
<component name="Component1"> <!-- parent -->
   <ports> <!-- role -->
     <outPort name="OutPort1"> <!-- child element -->
       ...
     </outPort>
   </ports> ...
```

Pokud je **atribut UseFullForm** nastavený na hodnotu true, zavádí se další vrstva vnoření. Tato vrstva představuje samotnou relaci. Pokud má relace vlastnosti, musí být atribut nastavený na hodnotu true.

```xml
<XmlClassData ElementName="outPort">
   <DomainClassMoniker Name="OutPort" />
   <ElementData>
     <XmlRelationshipData UseFullForm="true" RoleElementName="targets">
       <DomainRelationshipMoniker Name="Connection" />
     </XmlRelationshipData>
   </ElementData>
 </XmlClassData>
```

Serializovaný soubor obsahuje:

```xml
<outPort name="OutPort1">  <!-- Parent -->
   <targets>  <!-- role -->
     <connection sourceRoleName="X">  <!-- relationship link -->
         <inPortMoniker name="//Component2/InPort1" /> <!-- child -->
     </connection>
    </targets>
  </outPort>
```

(Relace připojení má vlastní data třídy XML, která poskytují názvy elementů a atributů.)

Pokud je atribut **OmitElement** nastavený na hodnotu true, název role relace je vynechán, což zkřížuje serializovaný soubor a je jednoznačné, pokud tyto dvě třídy nemají více než jednu relaci. Příklad:

```xml
<component name="Component3">
  <!-- only one relationship could get here: -->
  <outPort name="OutPort1">
     <targets> ...
```

### <a name="serialization-of-a-domain-specific-language-definition"></a>Serializace definice Domain-Specific jazyka

Soubor DslDefinition.dsl je sám o sobě serializovaný soubor a odpovídá definici jazyka specifické pro doménu. Tady je několik příkladů definic serializace XML:

- **Dsl** je uzel RootClass a třída diagramu. DomainClass, DomainRelationship a další prvky jsou vložené v rámci `Dsl` .

- **Třídy** jsou **RoleElementName** vztahu mezi Domain-Specific Language a DomainClass.

```xml
<Dsl Name="CmptDsl5" ...>
  <Classes>
    <DomainClass Name="NamedElement" InheritanceModifier="Abstract" ...
```

- Atribut **XmlSerializationBehavior** je vložen pod atributem , ale `Dsl` atribut **OmitElement** byl nastaven u vztahu vkládání. Proto se `RoleElementName` to nehne žádným atributům. Naproti tomu atribut **ClassData** je atribut vztahu vkládání mezi atributem `RoleElementName` **XmlSerializationBehavior** a **atributem XmlClassData.**

```xml
<Dsl Name="CmptDsl5" ...> ...
  <XmlSerializationBehavior Name="ComponentsSerializationBehavior" >
    <ClassData>
      <XmlClassData ...>...</XmlClassData>
      <XmlClassData ...>...</XmlClassData>
```

- ConnectorHasDecorators je vztah vkládání mezi a `Connector` `Decorator` . `UseFullForm` byla nastavena tak, aby se název relace zobrazí se seznamem vlastností pro každé propojení z objektu Konektor. Byla ale také nastavena tak, aby žádné spojení neuzavříto více `OmitElement` `RoleElementName` odkazů, které jsou vloženy do `Connector` objektu :

```xml
<Connector Name="AssociationLink" ...>
  <ConnectorHasDecorators Position="TargetTop" ...>
    <TextDecorator Name="TargetRoleName"   />
  </ConnectorHasDecorators>
  <ConnectorHasDecorators Position="SourceTop" ...>
    <TextDecorator Name="SourceRoleName"   />
  </ConnectorHasDecorators>
</Connector>
```

## <a name="shapes-and-connectors"></a>Obrazce a konektory

Definice tvarů a konektorů dědí atributy a podřízené uzly z tříd domény kromě následujících:

- `Color``Line``Style`a atributy.

- **ExposesFillColorAsProperty** a několik podobných atributů. Tyto logické atributy tvoří odpovídající proměnnou vlastnosti uživatelem. Obecně platí, že když uživatel jazyka klikne na obrazec  v diagramu, vlastnosti, které se zobrazí v okně Vlastnosti, jsou vlastnosti instance třídy domény, na kterou je obrazec mapován. Pokud je nastavená hodnota true, zobrazí se také vlastnost `ExposesFillColorAsProperty` samotného tvaru.

- **ShapeHasDecorators**: Instance tohoto atributu se vyskytuje pro každý text, ikonu nebo dekorátor rozbalení/sbalení. (V souboru DslDefinition.dsl `ShapeHasDecorators` je relace s `UseFullForm` nastavenou na true.)

## <a name="shape-maps"></a>Mapy obrazce

Mapy obrazců určují, jak se instance dané třídy domény zobrazují na obrazovce reprezentované obrazcem. Mapy obrazce i konektoru se zobrazí `Diagram` v části souboru DslDefinition.dsl.

Stejně jako v následujícím příkladu mají prvky minimálně moniker třídy `ShapeMap` domény, moniker tvaru a `ParentElementPath` element:

```xml
<ShapeMap>
  <DomainClassMoniker Name="InPort" />
  <ParentElementPath>
    <DomainPath>ComponentHasPorts.Component/!Component</DomainPath>
  </ParentElementPath>
  <PortMoniker Name="InPortShape" />
</ShapeMap>
```

Primární funkce elementu je tak, aby se stejná třída objektů v různých kontextech jeví jako `ParentElementPath` jiný tvar. Pokud by například objekt mohl být také vložen do komentáře, může se pro tento účel zobrazit `InPort` `InPort` jako jiný tvar.

Za druhé cesta určuje, jak tvar souvisí s nadřazeným tvarem. Mezi tvary v souboru DslDefinition.dsl není definována žádná struktura vkládání. Strukturu musíte odvodit z map obrazce. Nadřazený tvar je tvar, který je namapován na prvek domény, který identifikuje cesta k nadřazenému prvku. V tomto případě cesta identifikuje komponentu, ke které `InPort` patří. V jiné mapě obrazce je třída Component mapována na ComponentShape. Nový tvar je proto podřízený tvar jeho `InPort` komponenty `ComponentShape` .

Pokud byste k diagramu místo toho připojili tvar InPort, cesta k nadřazenému elementu by k modelu komponent, který je namapovaný na diagram, muset přijmout další krok:

```
ComponentHasPorts . Component / ! Component /    ComponentModelHasComponents . ComponentModel / ! ComponentModel
```

Kořen modelu nemá mapový tvar. Místo toho se na kořen odkazuje přímo z diagramu, který má `Class` element:

```xml
<Diagram Name="ComponentDiagram" >
    <Class>
      <DomainClassMoniker Name="ComponentModel" />
    </Class>...
```

### <a name="decorator-maps"></a>Dekoratérské mapy

Mapa dekoratéru přidruží vlastnost v mapované třídě k dekorátoru ve tvaru. Pokud je vlastnost výčtový nebo logický typ, může její hodnota určit, zda je dekorátor viditelný. Pokud je dekorátor dekorátorem textu, může se zobrazit hodnota vlastnosti a uživatel ji může upravit.

### <a name="compartment-shape-maps"></a>Mapy obrazce přihrádky

Mapy obrazců oddílů jsou podtypy map obrazců.

## <a name="connector-maps"></a>Mapy konektorů

Minimální mapa konektoru odkazuje na konektor a relaci:

```xml
<ConnectorMap>
  <ConnectorMoniker Name="CommentLink" />
  <DomainRelationshipMoniker Name="CommentsReferenceComponents" />
</ConnectorMap>
```

Mapy konektorů mohou také obsahovat mapy dekoratérů.

## <a name="see-also"></a>Viz také

- [Nástroje DSL glosář](/previous-versions/bb126564(v=vs.100))
- [Jak se definuje jazyk specifický pro doménu](../modeling/how-to-define-a-domain-specific-language.md)
- [Porozumění modelům, třídám a vztahům](../modeling/understanding-models-classes-and-relationships.md)