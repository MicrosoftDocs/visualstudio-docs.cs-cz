---
title: Soubor DslDefinition.dsl | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Domain-Specific Language, definition file
ms.assetid: f3fc3ed7-2438-4e5a-b3d7-fe7e0e8a134c
caps.latest.revision: 24
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 7f61ceef7248c143fd904751da58d32f75dfc0c2
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49937645"
---
# <a name="the-dsldefinitiondsl-file"></a>Soubor DslDefinition.dsl
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Toto téma popisuje strukturu soubor DslDefinition.dsl v projektu Dsl [!INCLUDE[dsl](../includes/dsl-md.md)] řešení, která definuje *jazyka specifického pro doménu*. Soubor DslDefinition.dsl popisuje třídy a vztahy z jazyka specifického pro doménu, společně s diagramu, tvary, konektory, formát serializace a **nástrojů** jazyka specifického pro doménu a jeho Nástroje pro úpravy. V řešení jazyka specifického pro doménu podle informací v souboru DslDefinition.dsl vygenerování kódu, který definuje těchto nástrojů.  
  
 Obecně platí, je použít *návrháře jazyka specifického pro doménu* upravit soubor DslDefinition.dsl. Ale nezpracované podobě je XML a soubor DslDefinition.dsl můžete otevřít v editoru XML. Jste možná pro vás bude užitečné, abyste pochopili, jaké informace tento soubor obsahuje a jakým způsobem je organizována pro účely ladění a rozšíření.  
  
 Příklady v tomto tématu jsou převzaty ze šablony řešení Diagram komponent. Chcete-li zobrazit příklad, vytváření řešení jazyka specifického pro doménu, který je založen na šabloně modely součást řešení. Po vytvoření řešení se zobrazí soubor DslDefinition.dsl v návrháře jazyka specifického pro doménu. Soubor zavřete, klikněte pravým tlačítkem myši v **Průzkumníka řešení**, přejděte na **otevřít v**, klikněte na tlačítko **editoru XML**a potom klikněte na tlačítko **OK**.  
  
## <a name="sections-of-the-dsldefinitiondsl-file"></a>Oddíly soubor DslDefinition.dsl  
 Kořenový element \<Dsl > a jeho atributy určit název jazyka specifického pro doménu, obor názvů, a čísla hlavní verze a podverze pro správu verzí. `DslDefinitionModel` Schéma definuje obsah a strukturu pro platný soubor DslDefinition.dsl.  
  
 Podřízené prvky \<Dsl > kořenový element jsou následující:  
  
 Třídy  
 Tento oddíl definuje každá třída domény, který vygeneruje třídu v generovaném kódu.  
  
 Relace  
 Tento oddíl definuje každá relace v modelu. Zdroj a cíl představují obou stranách relace.  
  
 Typy  
 Tento oddíl definuje každého typu a jeho oborem názvů. Vlastnosti domény má dva typy. `DomainEnumerations` jsou definovány v modelu a generování typů do DomainModel.cs. `ExternalTypes` odkazovat na typy, které jsou definovány jinde (například `String` nebo `Int32`) a nic nejsou generovány.  
  
 Obrazce  
 Tento oddíl definuje tvary, které popisují, jak se model zobrazen v návrháři. Tyto geometrické tvary jsou mapovány na třídy v tomto modelu v části diagramu.  
  
 Konektory  
 Tato část definuje vzhled elementů konektory, které se zobrazí v okně návrháře. Tyto popisy geometrické styl se namapují na konkrétní relace v modelu v části diagramu.  
  
 XmlSerializationBehavior  
 Tato část definuje schéma serializace a poskytuje další informace o tom, jak je každá třída uložit do souboru.  
  
 ExplorerBehavior  
 Tento oddíl definuje způsob, jakým **Průzkumník DSL** okna se zobrazí, když uživatel upravuje model.  
  
 ConnectionBuilders  
 Tento oddíl definuje Tvůrce připojení pro každý konektor nástroje (nástroj pro vytváření vazeb mezi jakékoli dvě třídy, které lze připojit). Tato část určuje, zda lze připojit zdrojové a cílové třídy.  
  
 diagram  
 Tento oddíl definuje diagram a použilo ji k určení vlastnosti, jako je barva pozadí a kořenová třída. (Kořenová třída je doménová třída, která je reprezentována jako celek diagramu.) Diagram naleznete zde také ShapeMap a ConnectorMap elementy, které určují tvar nebo konektor, který představuje každý doménovou třídu nebo vztah.  
  
 Návrhář  
 Tento oddíl definuje návrháře (editoru), která spojuje **nástrojů**, nastavení ověření, diagramu a schéma serializace. V části návrháře také definuje kořenová třída modelu, který je obvykle také kořenová třída diagramu.  
  
 Průzkumník  
 Tato část popisuje **Průzkumník DSL** chování (definované v části XmlSerializationBehavior).  
  
## <a name="monikers-in-the-dsldefinitiondsl-file"></a>Monikery v soubor DslDefinition.dsl  
 V celém souboru DslDefinition.dsl můžete provést křížové odkazy na konkrétní položky zástupných názvů. Například každá definice relace obsahuje dílčí část zdrojového a cílového dílčí část. Každý dílčí část obsahuje zástupný název třídy objektu, který může být propojený s relace:  
  
```  
<DomainRelationship …        Name="LibraryHasMembers" Namespace="ExampleNamespace" >    <Source>      <DomainRole …>  
       <RolePlayer>  
         <DomainClassMoniker Name="Library" />  
       </RolePlayer>  
     </DomainRole>  
   </Source>  
```  
  
 Obvykle, obor názvů odkazované položky (v tomto příkladu `Library` doménové třídy) je stejný jako odkazující položky (v tomto případě doménového vztahu LibraryHasMembers). V těchto případech se musí poskytnout monikeru jenom název třídy. V opačném případě byste měli používat /Namespace/Name úplný formát:  
  
```  
  
<DomainClassMoniker Name="/ExampleNameSpace/Library" />  
  
```  
  
 Moniker systému vyžaduje na stejné úrovni ve stromové struktuře XML odlišné názvy. Z tohoto důvodu se vyskytnou chyby, pokud se pokusíte uložit definice jazyka specifického pro doménu, která má například dvě třídy se stejným názvem. Tyto chyby duplicitní název byste měli napravit a vždy před uložením soubor DslDefinition.dsl, takže je možné jej znovu načíst správně později.  
  
 Každý typ má svůj vlastní typ moniker: DomainClassMoniker, DomainRelationshipMoniker, a tak dále.  
  
## <a name="types"></a>Typy  
 V části typy Určuje všechny typy, které obsahuje soubor DslDefinition.dsl jako typy vlastností. Tyto typy spadají do dvou typů: externí typy, jako je například System.String a výčtové typy.  
  
### <a name="external-types"></a>Externí typy  
 Příklad diagramu komponent obsahuje sadu standardních primitivních typů, i když se používají jenom některé z nich.  
  
 Každá definice typu externího se skládá pouze název a obor názvů, jako je například řetězec a systému:  
  
```  
<ExternalType Name="String" Namespace="System" />  
```  
  
 Úplné názvy typů se používají místo ekvivalentní kompilátoru klíčová slova jako je například "string".  
  
 Externí typy nejsou omezené na standardní typy knihoven.  
  
### <a name="enumerations"></a>Výčty  
 Typické specifikace výčet vypadá podobně jako v tomto příkladu:  
  
```  
<DomainEnumeration IsFlags="true" Name="PageSort"          Namespace="Fabrikam.Wizard">  
  <Literals>  
    <EnumerationLiteral Name="Start" Value="1"/>  
    <EnumerationLiteral Name="Decision" Value="2"/>  
  </Literals>  
</DomainEnumeration>  
```  
  
 `IsFlags` Atribut ovládací prvky, zda má předponu generovaný kód `[Flags]` atribut Common Language Runtime (CLR), která určuje, zda hodnoty výčtu lze kombinovat bitovým operátorem. Pokud tento atribut je nastaven na hodnotu true, je třeba zadat hodnoty power dvě hodnoty literálu.  
  
## <a name="classes"></a>Třídy  
 Většina prvků v jakékoli definice jazyka specifického pro doménu je přímo nebo nepřímo instance `DomainClass`. Podtřídy třídy `DomainClass` zahrnují `DomainRelationship`, `Shape`, `Connector`, a `Diagram`. `Classes` Část soubor DslDefinition.dsl uvádí doménovými třídami.  
  
 Každá třída má sadu vlastností a může mít základní třídu. V příkladu Diagram komponent `NamedElement` je abstraktní třída, která má `Name` vlastnost, jejíž typ je řetězec:  
  
```  
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
  
 `NamedElement` základ některé z jiné třídy, jako je `Component`, který má svou vlastní vlastnosti kromě `Name` vlastnost, která dědí z `NamedElement`. BaseClass podřízený uzel obsahuje odkaz na moniker. Vzhledem k tomu, že třída odkazovaná je ve stejném oboru názvů, je nutný pouze jeho název v monikeru:  
  
```  
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
  
 Každá třída domény (včetně relací, tvary, konektory a diagramy) může mít tyto atributy a podřízené uzly:  
  
-   **ID.** Tento atribut je identifikátor GUID. Pokud nezadáte hodnotu v souboru, návrháře jazyka specifického pro doménu vytvoří hodnotu. (V obrázcích v tomto dokumentu, tento atribut je obvykle vynechána, pro úsporu místa.)  
  
-   **Název a Namespace.** Tyto atributy zadejte název a obor názvů, třídy v generovaném kódu. Společně musí být jedinečný v rámci jazyka specifického pro doménu.  
  
-   **InheritanceModifier.** Tento atribut je "abstraktní", "sealed" nebo žádný.  
  
-   **DisplayName.** Tento atribut je název, který se zobrazí **vlastnosti** okna. Atribut DisplayName může obsahovat mezery a interpunkční.  
  
-   **GeneratesDoubleDerived.** Pokud tento atribut je nastaven na hodnotu true, jsou generovány dvě třídy a jeden je podtřídou třídy druhé. Generované metody jsou v základní třídě a konstruktory jsou v podtřídy. Tento atribut nastavíte, můžete přepsat všechny generované metody ve vlastním kódu.  
  
-   **HasCustomConstructor**. Pokud tento atribut je nastaven na hodnotu true, konstruktor je vynecháno z generovaného kódu tak, aby můžete napsat vlastní verzi.  
  
-   **Atributy**. Tento atribut obsahuje atributy CLR generované třídy.  
  
-   **BaseClass**. Pokud zadáte základní třídu, musí být stejného typu. Například doménová třída musí mít jiné doménové třídy jako svůj základ a obrazce oddílu musí mít obrazce oddílu. Pokud nezadáte základní třídy, je odvozena z standardní třídy třídy v generovaném kódu. Například doménová třída je odvozena z `ModelElement`.  
  
-   **Vlastnosti**. Tento atribut obsahuje vlastnosti, které udržuje pod kontrolou transakce a trvalé při uložení modelu.  
  
-   **ElementMergeDirectives**. Každé direktivě sloučení elementů řídí, jak se jinou instancí jiné třídy přidá do instance nadřazené třídy. Další podrobnosti o direktivy sloučení elementů najdete dále v tomto tématu.  
  
-   Třída jazyka C# je vygenerována pro každý doménové třídy, který je uveden v `Classes` oddílu. Třídy jazyka C# jsou generovány v Dsl\GeneratedCode\DomainClasses.cs.  
  
### <a name="properties"></a>Vlastnosti  
 Každá vlastnost domény má název a typ. Název musí být jedinečný v rámci třídy domény a jeho tranzitivní základních tříd.  
  
 Typ musí odkazovat na jeden z uvedených v `Types` oddílu. Obecně platí zástupný název musí obsahovat obor názvů.  
  
```  
<DomainProperty Name="Name" DisplayName="Name"  DefaultValue="" Category="" IsElementName="true">  
  <Type>  
    <ExternalTypeMoniker Name="/System/String" />  
  </Type>  
</DomainProperty>  
```  
  
 Každou vlastnost domény mohou také mít tyto atributy:  
  
-   **IsBrowsable**. Tento atribut určuje, zda vlastnost se zobrazí v **vlastnosti** okno při kliknutí na objekt nadřazené třídy.  
  
-   **IsUIReadOnly**. Tento atribut určuje, jestli uživatel může změnit vlastnost **vlastnosti** okno nebo prostřednictvím dekoratér, ve kterém se zobrazí vlastnosti.  
  
-   **Druh**. Tento atribut nastavíte na normální, vypočtená nebo hodnotu CustomStorage. Pokud tento atribut nastavíte na vypočtené, je nutné zadat vlastní kód, který určuje hodnotu a bude hodnota vlastnosti jen pro čtení. Pokud tento atribut nastavíte na hodnotu CustomStorage, je nutné zadat kód, který získá a nastaví hodnoty.  
  
-   **IsElementName**. Pokud tento atribut je nastaven na hodnotu true, jeho hodnota se automaticky nastaví na jedinečnou hodnotu při vytvoření instance třídy nadřazené. Tento atribut lze nastavit hodnotu true pro pouze jednu vlastnost v každé třídě musí mít typ řetězce. V příkladu Diagram komponent `Name` vlastnost `NamedElement` má `IsElementName` nastavenou na hodnotu true. Vždy, když uživatel vytvoří `Component` – element (který dědí z `NamedElement`), název je automaticky inicializován na něco jako "Component6."  
  
-   `DefaultValue`. Pokud zadáte tento atribut, hodnota, která jste zadali přiřazen tento atribut pro nové instance této třídy. Pokud `IsElementName` má hodnotu DefaultValue – atribut určuje počáteční součástí nového řetězce.  
  
-   **Kategorie** je záhlavím, pod kterým se zobrazí vlastnosti v **vlastnosti** okna.  
  
## <a name="relationships"></a>Relace  
 `Relationships` Části jsou uvedené všechny relace jazyka specifického pro doménu. Každý `Domain Relationship` je binární a přímé propojení členy třídy zdroje pro členy cílové třídy. Zdrojové a cílové třídy jsou obvykle doménové třídy, ale vztahy k jiné vztahy jsou také povoleny.  
  
 Například relace připojení odkazuje členy třídy OutPort na členy třídy InPort. Každý odkaz instance vztahu se připojí k instanci InPort instance OutPort. Vzhledem k tomu, že je relace m: n, každý OutPort může mít mnoho odkazů připojení se zdroji na něj a každou instanci InPort může mít mnoho odkazů připojení, které na ni cílit.  
  
### <a name="source-and-target-roles"></a>Zdrojové a cílové role  
 Každý vztah obsahuje zdrojové a cílové role, které mají následující atributy:  
  
-   `RolePlayer` Atribut odkazuje na třídu domény propojených instancí: OutPort pro zdroj, InPort pro cíl.  
  
-   `Multiplicity` Atribut má čtyři možných hodnot (hodnotu ZeroMany, ZeroOne, jeden a OneMany). Tento atribut odkazuje na počet odkazy tohoto vztahu, který může být přidružený jeden aktéra role.  
  
-   `PropertyName` Atribut určuje název, který se používá v rolí datedim třídy pro přístup k objektům na druhém konci. Tento název se používá v šabloně nebo vlastní kód pro přechod relaci. Například `PropertyName` atribut zdrojová role je nastaven na `Targets`. Proto bude fungovat následující kód:  
  
    ```  
    OutPort op = …; foreach (InPort ip in op.Targets) ...  
    ```  
  
     Podle konvence jsou v množném čísle, pokud je násobnost hodnotu ZeroMany nebo OneMany názvy vlastností.  
  
     Násobnost atributu role elementu odkazuje na tom, kolik opačné role může být spojen s každou instanci této role. Například ve vztahu ComponentHasPorts má cílová role `RolePlayer` atribut nastaven na Port, `PropertyName` atribut nastaven na komponenty a `Multiplicity` atribut nastaven na hodnotu ZeroOne. Proto je odpovídající kód chcete použít tuto roli:  
  
    ```  
    ComponentPort p = …; Component c = p.Component; if (c != null) …  
    ```  
  
-   Role `Name` je název, který se používá v rámci třídy vztahu k odkazování za tímto účelem odkaz. Podle konvence názvu role je vždy jednotném čísle, protože každý odkaz má pouze jednu instanci na každém konci. Následující kód bude fungovat:  
  
    ```  
    Connection connectionLink = …; OutPort op = connectionLink.Source;  
    ```  
  
-   Ve výchozím nastavení `IsPropertyGenerator` atribut je nastaven na hodnotu true. Pokud je nastavena na hodnotu false, žádná vlastnost je vytvořena na třídy aktéra Role. (V takovém případě `op.Targets`, například nebude fungovat). Je však stále možné použití vlastního kódu pro přechod relaci nebo získat přístup k odkazy sami, pokud vlastní kód explicitně používá relace:  
  
    ```  
    OutPort op = …; foreach (InPort ip in Connection.GetTargets(op)) …  
    foreach (Connection link in Connection.GetLinksToTargets(op)) …  
    ```  
  
### <a name="relationship-attributes"></a>Relace atributů  
 Kromě atributy a podřízené uzly, které jsou k dispozici pro všechny třídy má každý vztah těchto atributů:  
  
-   **IsEmbedding**. Tento logický atribut určuje, zda vztah je součástí stromu vkládání. Každý model musí tvořit stromu s jeho vkládání vztahy. Každé doménové třídy musí být cílem alespoň jeden vztah obsažení, proto, pokud není kořenu modelu.  
  
-   **AllowsDuplicates**. Tento logický atribut, který je ve výchozím nastavení hodnotu false, se vztahuje pouze na vztahy, které mají na zdrojovém i cílovém násobnost n ":". To určuje, zda jazyk uživatele může připojit jedné dvojice zdrojové a cílové elementy ve stejné relaci více než jedno propojení.  
  
## <a name="designer-and-toolbox-tabs"></a>Návrhář a karty panelu nástrojů  
 Hlavní část **návrháře** část soubor DslDefinition.dsl je **karta panelu nástrojů** elementy. Jeden návrhář může mít několik z těchto elementů, z nichž každý představuje zelí oddíl ve vygenerovaném návrháři **nástrojů**. Každý **karta panelu nástrojů** element může obsahovat jeden nebo více **nástroj elementu** prvky, **ConnectionTool** elementy nebo obojí.  
  
 Element nástroje lze vytvořit instance konkrétní doménové třídy. Když uživatel přetáhne nástroj elementu do diagramu, je výsledek určen pomocí direktivy sloučení elementů, jak je popsáno v části o direktivy sloučení elementů dále v tomto tématu.  
  
 Každý nástroj pro připojení můžete vyvolat Tvůrce konkrétní připojení. Jeden Tvůrce připojení můžete vytvořit více než jeden typ vztahu, v závislosti na tom, kde uživatel klikne myší, jak je popsáno v části o tvůrci připojení.  
  
 Ani jedna typu nástroj přímo vytvoří obrazců a konektorů. Každý vytvoří doménovou třídu nebo vztah domény; mapování obrazců a konektorů pak zjistěte, jak se objeví této doménové třídy nebo doménového vztahu.  
  
## <a name="paths"></a>Cesty  
 Domény cesty zobrazují v několika umístěních v soubor DslDefinition.dsl. Tyto cesty zadejte řadu odkazy z jednoho elementu v modelu (to znamená, že instance jazyka specifického pro doménu) do jiného. Syntaxe cesty je jednoduchý, ale verbose.  
  
 Se cesty zobrazují v soubor DslDefinition.dsl v `<DomainPath>…</DomainPath>` značky. I když cesty můžete procházet více odkazů, většina příkladů v praxi procházejí jenom jedno propojení.  
  
 Cesta se skládá z posloupnost segmenty. Každý segment je směrování z objektu propojení nebo z odkazu na objekt. Proto přesměrování alternativní obvykle dlouhé cestě. První segment směrování je z objektu propojení, druhý segment směrování je objekt na druhém konci odkazu, třetí směrování se na následující odkaz a tak dále. Příležitostné výjimka, která má toto pořadí je kde vztah je zdrojová nebo cílová jiné relace.  
  
 Každý segment začíná název relace. V segmentu propojení objektu relace předchází tečku a název vlastnosti: "`Relationship . Property`". V segmentu odkazu na objekt, vztah předchází vykřičník a název role: "`Relationship ! Role`".  
  
 Příklad diagramu komponent obsahuje cestu ParentElementPath vizuál ShapeMap InPort. Tato cesta začínající následujícím způsobem:  
  
```  
    ComponentHasPorts.Component  
```  
  
 V tomto příkladu InPort je podtřídou třídy ComponentPort a nemá vztah ComponentHasPorts. Vlastnost je názvem komponenty.  
  
 Při zápisu jazyka C# pro tento model, můžete přejít přes odkaz v jednom kroku pomocí vlastnost, která generuje relace na každém tříd, které se týká:  
  
```  
     InPort port; ...  Component c = port.Component;  
```  
  
 Ale je potřeba udělat i směrování explicitně v cestě syntaxi. Kvůli tomuto požadavku můžete snadněji přistupovat zprostředkující odkaz. Následující kód provede směrování z odkazu na komponentu:  
  
```  
    ComponentHasPorts.Component / ! Component  
```  
  
 (Název relace, kde je stejná jako v předchozí segment můžete vynechat.)  
  
## <a name="element-merge-directives"></a>Direktivy sloučení elementů  
 Pokud jazyk uživatel přetáhne položku ze **nástrojů** do diagramu, je vytvořena instance třídy nástroje. Odkazy jsou rovněž mezi tuto instanci a stávající prvky modelu. Některé položky, jako je například součástí nebo komentáře, vytvářejí, když uživatel jazyk přetáhne z **nástrojů** na prázdnou část diagramu. Další položky se vytvoří, když jazyk přetažena je další prvky hostitele. Například k OutPort nebo InPort se vytvoří při jazyk přetažena jeho součásti.  
  
 Potenciální třída hostitele, jako jsou komponenty, přijme nový prvek pouze v případě, že třída hostitele nemá direktivě sloučení pro třídu nového elementu. Například uzel doménová třída s názvem = "Součást" obsahuje:  
  
```  
<DomainClass Name="Component" …> …  
    <ElementMergeDirective>  
      <Index>  
        <DomainClassMoniker Name="ComponentPort" />  
      </Index>  
      <LinkCreationPaths>  
        <DomainPath>ComponentHasPorts.Ports</DomainPath>  
      </LinkCreationPaths>  
    </ElementMergeDirective> …  
```  
  
 Zástupný název třídy, která je pod uzlem Index odkazuje na třídu element, který může přijmout. V takovém případě ComponentPort je abstraktní základní třída InPort a OutPort. Proto mohou být přijaty některý z těchto elementů.  
  
 ComponentModel kořenová třída jazyka, obsahuje direktivy sloučení elementů pro komponenty a komentáře. Jazyk uživatele můžete přetáhnout položky pro tyto třídy přímo do diagramu, protože kořenová třída představují prázdnou část diagramu. ComponentModel však nemá žádná direktiva sloučení elementů pro ComponentPort. Proto jazyk uživatele nebo nelze přetáhnout InPorts OutPorts přímo do diagramu.  
  
 Direktiva sloučení elementů Určuje, jaké odkaz nebo odkazy jsou vytvořeny tak, aby nový prvek můžete integrovat nebo sloučit do existující model. Pro ComponentPort je vytvořena instance ComponentHasPorts. Doménovou cestu relace a vlastnost nadřazené třídy, určuje porty, ke kterým se přidá nový prvek.  
  
 Můžete vytvořit více než jedno propojení v direktivě sloučení zahrnutím více než jednu cestu pro vytvoření odkazu. Jedna z cest musí být vložený.  
  
 Můžete použít více než jeden segment v cestě k vytvoření propojení. Poslední segment v tomto případě definuje, jaké odkaz musí být vytvořeny. Starší segmenty přejděte od nadřazené třídy objektu, ze kterého by měla vytvořen nový odkaz.  
  
 Například můžete přidat tato direktiva sloučení elementů do třídy součásti:  
  
```  
<DomainClass Name="Component" …> …  
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
  
 Jazyk uživatele můžete přetáhnout komponentu komentář a mít nový komentář, automaticky se vytvoří s odkazem na komponentu.  
  
 Provádí navigaci z první cesta k vytváření odkazů `Component` k `ComponentModel` a potom vytvoří instanci vztah obsažení `ComponentModelHasComments`. Druhý cesta k vytváření odkazů na nový komentář vytvoří odkaz referenčního vztahu CommentsReferenceComponents z hostitele součástí. Všechny cesty k vytváření odkazů musí začínat znakem třída hostitele a musí končit na odkaz tohoto postupu směrem k nově instance třídy.  
  
## <a name="xmlclassdata"></a>XmlClassData  
 Každá třída domény (včetně vztahů a ostatní podtypy) může mít dodatečné informace uvedené v `XmlClassData` uzlu, který se zobrazí v části `XmlSerializationBehavior` část soubor DslDefinition.dsl. Tyto informace se konkrétně týkají, jak instancí třídy jsou uloženy v serializované podoby při uložení modelu do souboru.  
  
 Velká část generovaného kódu, který `XmlSerializationBehavior` ovlivňuje probíhá `Dsl\GeneratedCode\Serializer.cs`.  
  
 Každý `XmlClassData` uzel obsahuje tyto podřízené uzly a atributy:  
  
-   Zástupný název uzlu, který odkazuje na třídu, na které se vztahují data.  
  
-   **XmlPropertyData** pro každou vlastnost, která je definovaná ve třídě.  
  
-   **XmlRelationshipData** pro každý vztah, který pochází třída. (Relace také mít své vlastní XmlClassData uzly.)  
  
-   **TypeName** atribut řetězce, který určuje název třídy pomocné rutiny serializace v generovaném kódu.  
  
-   **Třída ElementName** řetězec, který určuje značky XML serializovaných instancí této třídy. Podle konvence ElementName je obvykle stejný jako název třídy s výjimkou první písmena jsou malá písmena. Například ukázkový soubor modelu začíná takto:  
  
    ```  
    <componentModel …  
    ```  
  
-   **Název elementu Monikeru** v souborech serializovaný model uživatele. Tento atribut zavádí monikeru, který odkazuje na tuto třídu.  
  
-   **Název atributu Monikeru**, který identifikuje název atributu XML v monikeru. V tomto fragmentu serializovaný soubor uživatele Autor jazyka specifického pro doménu definované **název elementu Monikeru** jako "inPortMoniker" a **název atributu Monikeru** jako "cesty":  
  
    ```  
    <inPortMoniker path="//Component2/InPort1" />  
    ```  
  
### <a name="connectionbuilders"></a>ConnectionBuilders  
 Tvůrce připojení je definována pro každý nástroj pro připojení. Každý Tvůrce připojení se skládá z jednoho nebo více prvků propojovací direktiva odkazu, z nichž každý obsahuje jeden nebo více prvků SourceDirective a jeden nebo více prvků TargetDirective. Po kliknutí na nástroj pro připojení, může uživatel spustit z libovolného tvaru mapován na prvek modelu, který se zobrazí v seznamu elementů SourceDirective připojení. Připojení lze pak provést na obrazec, který se mapuje na element, který se zobrazí v seznamu elementů TargetDirective. Třída vztahu vytvořena instance závisí na element propojovací direktiva odkazu určený začínali připojení.  
  
### <a name="xmlpropertydata"></a>XmlPropertyData  
 A **DomainPropertyMoniker** atribut určuje vlastnost, na který odkazuje data. Tento atribut musí být vlastnost tříd ohraničující třídy.  
  
 **XmlName** atribut poskytuje odpovídající název atributu, který se má zobrazit v souboru XML. Podle konvence je tento řetězec stejný jako název vlastnosti s výjimkou první písmena jsou malá písmena.  
  
 Ve výchozím nastavení **reprezentace** atribut je nastaven na atribut. Pokud **reprezentace** je nastavena na prvek, podřízený uzel je vytvořen v souboru XML. Pokud **reprezentace** je nastaven na hodnotu Ignorovat se neserializuje vlastnost.  
  
 **IsMonikerKey** a **IsMonikerQualifier** atributy poskytují vlastnost roli při určování instancí nadřazené třídy. Můžete nastavit **IsMonikerKey** na hodnotu true pro jednu vlastnost, která je definována v nebo dědí třídu. Tento atribut určuje jednotlivé instance nadřazené třídy. Vlastnost nastavíte na `IsMonikerKey` je obvykle název nebo jiný identifikátor klíče. Například `Name` vlastnost řetězce je klíčem monikeru NamedElement a její odvozené třídy. Když uživatel uloží do souboru modelu, tento atribut musí obsahovat jedinečné hodnoty pro každou instanci mezi uzly na stejné úrovni ve stromové struktuře vkládání vztahy.  
  
 Úplný zástupný název elementu v souboru serializovaný model je cestu z kořene modelu dolů strom vztahů citací klíčem monikeru v každém bodu vložení. Například InPorts jsou vložené v rámci komponenty, které jsou zase vložené v kořenovém modelu. Proto je platný zástupný název:  
  
```  
<inPortMoniker name="//Component2/InPort1" />  
```  
  
 Můžete nastavit **IsMonikerQualifier** atribut pro vlastnosti typu string a poskytují další způsob, jak vytvořit úplný název elementu. Například v soubor DslDefinition.dsl **Namespace** je kvalifikátorem monikeru.  
  
### <a name="xmlrelationshipdata"></a>XmlRelationshipData  
 V rámci souboru serializovaný model odkazy (o vložení a odkaz relací) jsou reprezentovány podřízené uzly zdrojovém konci vztahu. Vložit relace, obsahuje podřízený uzel podstrom. Pro referenční stavy obsahuje podřízený uzel monikeru, který odkazuje na jiné části stromu.  
  
 **XmlRelationshipData** atribut **XmlClassData** atribut definuje, přesně jak vnořené podřízené uzly v rámci zdrojového elementu. Každý vztah, který je zdrojem na doménové třídy má jednu **XmlRelationshipData** atribut.  
  
 **DomainRelationshipMoniker** atribut identifikuje vztahů Source ve třídě.  
  
 **RoleElementName** atribut poskytuje názvu značky XML, který obklopuje podřízený uzel v serializovaných datech.  
  
 Soubor DslDefinition.dsl obsahuje například:  
  
```  
<XmlClassData ElementName="component" …>  
  <DomainClassMoniker Name="Component" />  
  <ElementData>  
    <XmlRelationshipData RoleElementName="ports">  
      <DomainRelationshipMoniker Name="ComponentHasPorts" />  
    </XmlRelationshipData>  
```  
  
 Proto serializovaný soubor obsahuje:  
  
```  
<component name="Component1"> <!-- parent ->  
   <ports> <!-- role ->  
     <outPort name="OutPort1"> <!-- child element ->  
       …  
     </outPort>  
   </ports> …  
```  
  
 Pokud **UseFullForm** atribut je nastaven na hodnotu true, byla zavedená další úrovně vnoření. Tato vrstva představuje vztah sama. Atribut musí být nastaven na hodnotu true, pokud tento vztah obsahuje vlastnosti.  
  
```  
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
  
```  
<outPort name="OutPort1">  <!-- Parent ->  
   <targets>  <!-- role ->  
     <connection sourceRoleName="X">  <!-- relationship link ->  
         <inPortMoniker name="//Component2/InPort1" /> <!-- child ->  
     </connection>  
    </targets>  
  </outPort>  
```  
  
 (Připojení relace má svůj vlastní datech třídy XML, který poskytuje jeho názvy prvků a atributů.)  
  
 Pokud **možnost OmitElement** atribut je nastaven na hodnotu true, relace je vynechán název role, které zkrátí serializovaný soubor a je jednoznačný, pokud máte více než jeden vztah dvou tříd. Příklad:  
  
```  
<component name="Component3">  
  <!-- only one relationship could get here: ->  
  <outPort name="OutPort1">    
     <targets> …  
```  
  
### <a name="serialization-of-a-domain-specific-language-definition"></a>Serializace definice jazyka specifického pro doménu  
 Soubor DslDefinition.dsl je samotný soubor serializovaná a odpovídá do definice jazyka specifického pro doménu. Následují příklady definice serializace XML:  
  
-   **DSL** je kořenovou třídu uzel a diagramu třídy. Doménová třída doménového vztahu a další prvky jsou vložené v rámci `Dsl`.  
  
-   **Třídy** je **RoleElementName** vztahu mezi jazyka specifického pro doménu a doménovou třídou.  
  
```  
<Dsl Name="CmptDsl5" …>  
  <Classes>  
    <DomainClass Name="NamedElement" InheritanceModifier="Abstract" …  
```  
  
-   **XmlSerializationBehavior** atribut je vložený v části `Dsl` atribut, ale **možnost OmitElement** vztah obsažení byl nastaven atribut. Proto, ne `RoleElementName` zasahující atribut. Naopak **tříd** atribut je `RoleElementName` atribut vztah obsažení mezi **XmlSerializationBehavior** atribut a **XmlClassData** atribut.  
  
```  
<Dsl Name="CmptDsl5" …> …  
  <XmlSerializationBehavior Name="ComponentsSerializationBehavior" >  
    <ClassData>  
      <XmlClassData …>…</XmlClassData>  
      <XmlClassData …>…</XmlClassData>  
```  
  
-   ConnectorHasDecorators je vztah obsažení mezi `Connector` a `Decorator`. `UseFullForm` je nastavená tak, aby zobrazil název relace s její seznam vlastností pro každý odkaz z objektu konektoru. Ale `OmitElement` má také nastavit tak, aby žádné `RoleElementName` obklopuje více odkazy, které jsou vložené v `Connector`:  
  
```  
<Connector Name="AssociationLink" …>  
  <ConnectorHasDecorators Position="TargetTop" …>  
    <TextDecorator Name="TargetRoleName"   />  
  </ConnectorHasDecorators>  
  <ConnectorHasDecorators Position="SourceTop" …>  
    <TextDecorator Name="SourceRoleName"   />  
  </ConnectorHasDecorators>  
</Connector>  
```  
  
## <a name="shapes-and-connectors"></a>Obrazců a konektorů  
 Definice obrazců a konektorů zdědí atributy a podřízené uzly z doménové třídy, kromě následujících akcí:  
  
-   `Color` a `Line``Style` atributy.  
  
-   **ExposesFillColorAsProperty** a několik podobných atributů. Tyto logické atributy provést odpovídající vlastnost proměnnou tímto uživatelem. Obecně platí, po kliknutí jazyk obrazec v diagramu, vlastnosti, která se zobrazují **vlastnosti** okna jsou instance třídy domény, ke kterému je namapována na obrazec. Pokud `ExposesFillColorAsProperty` je nastavena na hodnotu true, vlastnost obrazce, samotné se také zobrazí.  
  
-   **ShapeHasDecorators**. Pro každý text, ikony nebo dekorátoru Rozbalit/sbalit dojde k instanci tohoto atributu. (V souboru DslDefinition.dsl `ShapeHasDecorators` je vztah s `UseFullForm` nastavenou na hodnotu true.)  
  
## <a name="shape-maps"></a>Mapy obrazců  
 Mapy obrazců určují vzhled instancí třídy danou doménu na obrazovce, reprezentovaný obrazce. Map obrazců a konektorů se zobrazí v rámci `Diagram` část soubor DslDefinition.dsl.  
  
 Stejně jako v následujícím příkladu `ShapeMap` elementy mají na minimum, moniker doménové třídy, moniker obrazce a `ParentElementPath` element:  
  
```  
<ShapeMap>  
  <DomainClassMoniker Name="InPort" />  
  <ParentElementPath>  
    <DomainPath>ComponentHasPorts.Component/!Component</DomainPath>  
  </ParentElementPath>  
  <PortMoniker Name="InPortShape" />  
</ShapeMap>  
```  
  
 Primární funkce `ParentElementPath` element je tak, aby stejné třídy objektů se může zobrazit jako jiný tvar v různých kontextech. Například pokud `InPort` může také vložit komentář, `InPort` může zobrazit jako jiný tvar pro tento účel.  
  
 Za druhé cesta Určuje, jak tvar má vztah k nadřazené úloze. Bez vkládání struktura je definována mezi tvary v soubor DslDefinition.dsl. Musíte odvodit strukturu z mapy obrazců. Nadřazený obrazec je tvar, který je namapovaný na doménový element, který identifikuje cesta k nadřazenému elementu. V takovém případě cestu identifikuje součásti ke kterému `InPort` patří. V jiném mapový tvar komponentní třída namapován na ComponentShape. Proto nové `InPort` tvar se stane podřízený tvar jeho součásti `ComponentShape`.  
  
 Pokud jste se připojili InPort obrazec diagramu místo toho, cesta k nadřazenému elementu by měla mít další krok k modelu, která se mapuje na diagram:  
  
```  
ComponentHasPorts . Component / ! Component /    ComponentModelHasComponents . ComponentModel / ! ComponentModel  
```  
  
 Kořen modelu nemá mapa obrazce. Místo toho se kořenové odkazuje přímo z diagramu, který má `Class` element:  
  
```  
<Diagram Name="ComponentDiagram" >  
    <Class>  
      <DomainClassMoniker Name="ComponentModel" />  
    </Class>…  
```  
  
### <a name="decorator-maps"></a>Mapy dekoratérů  
 Mapa dekoratéru přidruží vlastnosti ve třídě mapované na dekoratér obrazce. Pokud je vlastnost typu výčtu nebo logická, jeho hodnota můžete určit, jestli je dekoratér viditelný. Pokud je dekoratér dekoratér text, hodnota vlastnosti může objevit, a uživatel může upravovat jeho.  
  
### <a name="compartment-shape-maps"></a>Mapy obrazců oddílů  
 Mapy obrazců oddílů jsou podtypy map obrazců.  
  
## <a name="connector-maps"></a>Mapy konektorů  
 Mapa konektoru minimální odkazuje konektoru a relace:  
  
```  
<ConnectorMap>  
  <ConnectorMoniker Name="CommentLink" />  
  <DomainRelationshipMoniker Name="CommentsReferenceComponents" />  
</ConnectorMap>  
```  
  
 Mapy konektorů může také obsahovat mapy dekoratérů.  
  
## <a name="see-also"></a>Viz také  
 [Glosář nástrojů jazyka specifického pro doménu](http://msdn.microsoft.com/en-us/ca5e84cb-a315-465c-be24-76aa3df276aa)   
 [Jak se definuje jazyk specifický pro doménu](../modeling/how-to-define-a-domain-specific-language.md)   
 [Porozumění modelům, třídám a vztahům](../modeling/understanding-models-classes-and-relationships.md)



