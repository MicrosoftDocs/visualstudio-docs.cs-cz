---
title: Přizpůsobení souborového úložiště a serializace XML
description: Seznamte se se souborem XML vytvořeným nebo aktualizovaným při uložení instance nebo modelu v rámci domény (DSL) v aplikaci Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.dsltools.dsldesigner.xmlbehavior
helpviewer_keywords:
- Domain-Specific Language, serialization
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: be19b3026010e37108ca1b19096d48a3c8d88ab6
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2021
ms.locfileid: "112389368"
---
# <a name="customize-file-storage-and-xml-serialization"></a>Přizpůsobení úložiště souborů a serializace XML

Když uživatel v aplikaci Visual Studio uloží instanci nebo *model* určitého jazyka (DSL), vytvoří se soubor XML nebo se aktualizuje. Soubor lze znovu načíst a znovu vytvořit model ve Storu.

Schéma serializace můžete přizpůsobit úpravou nastavení v části **chování serializace XML** v Průzkumníku DSL. U každé doménové třídy, vlastnosti a vztahu je v rámci **chování serializace XML** uzel. Relace jsou umístěny pod svými zdrojovými třídami. K dispozici jsou také uzly odpovídající třídám Shape, Connector a diagram.

Můžete také napsat kód programu pro pokročilejší přizpůsobení.

> [!NOTE]
> Pokud chcete model uložit v konkrétním formátu, ale nemusíte ho znovu načítat z tohoto formuláře, zvažte použití textových šablon k vygenerování výstupu z modelu namísto vlastního schématu serializace. Další informace naleznete v tématu [generování kódu z Domain-Specificho jazyka](../modeling/generating-code-from-a-domain-specific-language.md).

## <a name="model-and-diagram-files"></a>Soubory modelů a diagramů

Každý model je obvykle uložen ve dvou souborech:

- Soubor modelu má název, například **Model1. mydsl**. Ukládá prvky modelu a vztahy a jejich vlastnosti. Přípona souboru, například **. mydsl** , je určena vlastností **Extension** uzlu **editoru** v definici DSL.

- Soubor diagramu má název, například **Model1. mydsl. diagram**. Ukládá tvary, konektory a jejich umístění, barvy, tloušťky čar a další podrobnosti o vzhledu diagramu. Pokud uživatel odstraní soubor **. diagram** , podstatné informace v modelu nebudou ztraceny. Ztratí se jenom rozložení diagramu. Při otevření souboru modelu se vytvoří výchozí sada obrazců a konektorů.

### <a name="to-change-the-file-extension-of-a-dsl"></a>Změna přípony souboru DSL

1. Otevřete definici DSL. V Průzkumníku DSL klikněte na uzel Editor.

2. V okno Vlastnosti upravte vlastnost **přípona** . Nezahrnujte úvodní znak "". "přípony názvu souboru.

3. V Průzkumník řešení změňte název souborů šablon dvou položek v **DslPackage\ProjectItemTemplates**. Názvy těchto souborů mají následující formát:

     `myDsl.diagram`

     `myDsl.myDsl`

## <a name="the-default-serialization-scheme"></a>Výchozí schéma serializace

Chcete-li vytvořit příklad pro toto téma, byla použita následující definice DSL.

![Diagram definice DSL &#45; model struktury řady](../modeling/media/familyt_person.png)

Tato DSL byla použita k vytvoření modelu, který má následující vzhled na obrazovce.

![Diagram stromu rodiny, panel nástrojů a Průzkumník](../modeling/media/familyt_instance.png)

Tento model se uložil a pak se znovu otevřel v textovém editoru XML:

```xml
<?xml version="1.0" encoding="utf-8"?>
<familyTreeModel xmlns:dm0="http://schemas.microsoft.com/VisualStudio/2008/DslTools/Core" dslVersion="1.0.0.0" Id="f817b728-e920-458e-bb99-98edc469d78f" xmlns="http://schemas.microsoft.com/dsltools/FamilyTree">
  <people>
    <person name="Henry VIII" birthYear="1491" deathYear="1547" age="519">
      <children>
        <personMoniker name="/f817b728-e920-458e-bb99-98edc469d78f/Elizabeth I" />
        <personMoniker name="/f817b728-e920-458e-bb99-98edc469d78f/Mary" />
      </children>
    </person>
    <person name="Elizabeth I" birthYear="1533" deathYear="1603" age="477" />
    <person name="Mary" birthYear="1515" deathYear="1558" age="495" />
  </people>
</familyTreeModel>
```

Všimněte si následujících bodů o serializovaném modelu:

- Každý uzel XML má název, který je stejný jako název třídy domény, s tím rozdílem, že počáteční písmeno je malé. Příklad: `familyTreeModel` a `person`.

- Vlastnosti domény, jako je název a BirthYear, jsou serializovány jako atributy v uzlech XML. Počáteční znak názvu vlastnosti se znovu převede na malá písmena.

- Každý vztah je serializován jako uzel XML vnořený uvnitř zdrojového elementu end relace. Uzel má stejný název jako vlastnost zdrojové role, ale s malým počátečním znakem.

     Například v definici DSL je role, která je pojmenovaná **osoba** , ve třídě **FamilyTree** zdrojová.  V jazyce XML je tento stav reprezentován uzlem s názvem, který je vnořen v rámci `people` `familyTreeModel` uzlu.

- Cílový konec každé relace vložení je serializován jako uzel vnořený do relace. `people`Uzel například obsahuje několik `person` uzlů.

- Cílový konec každého referenčního vztahu je serializován jako *moniker*, který zakóduje odkaz na cílový element.

     Například v rámci `person` uzlu může existovat `children` relace. Tento uzel obsahuje monikery, jako například:

    ```xml
    <personMoniker name="/f817b728-e920-458e-bb99-98edc469d78f/Elizabeth I" />
    ```

## <a name="understand-monikers"></a>Vysvětlení monikerů

Monikery slouží k reprezentaci křížových odkazů mezi různými částmi modelu a souborů diagramu. Používají se také v `.diagram` souboru pro odkazy na uzly v souboru modelu. Existují dvě formy monikeru:

- *Monikery ID* mají v nabídce identifikátor GUID cílového prvku. Příklad:

    ```xml
    <personShapeMoniker Id="f79734c0-3da1-4d72-9514-848fa9e75157" />
    ```

- *Kvalifikované monikery klíčů* identifikují cílový prvek hodnotou určené doménové vlastnosti, která se nazývá klíč monikeru. Moniker cílového prvku je předponou moniker jeho nadřazeného prvku ve stromové struktuře vztahů vložení.

     Následující příklady jsou pořízeny pomocí DSL, v němž existuje doménová třída s názvem album, která má vztah vložení do doménové třídy s názvem Song:

    ```xml
    <albumMoniker title="/My Favorites/Jazz after Teatime" />
    <songMoniker title="/My Favorites/Jazz after Teatime/Hot tea" />
    ```

     Kvalifikované monikery klíčů budou použity, pokud má cílová třída doménovou vlastnost, pro kterou je možnost **klíč monikeru** nastavená na hodnotu `true` v **chování serializace XML**. V tomto příkladu je tato možnost nastavená pro vlastnosti domény s názvem "title" v doménových třídách "album" a "skladba".

Kvalifikované monikery klíčů je snazší číst než monikery ID. Pokud máte v úmyslu načíst XML souborů modelu, zvažte použití kvalifikovaných monikerů klíčů. Je však možné, že uživatel nastaví více než jeden prvek tak, aby měl stejný klíč monikeru. Duplicitní klíče by mohly způsobit, že se soubor nenačítá správně. Proto pokud definujete doménovou třídu, na kterou se odkazuje pomocí úplných monikerů klíčů, měli byste zvážit, jak zabránit uživateli v ukládání souboru, který má duplicitní monikery.

### <a name="to-set-a-domain-class-to-be-referenced-by-id-monikers"></a>Nastavení doménové třídy, na kterou odkazují monikery ID

1. Ujistěte se, že **je klíč monikeru** `false` pro každou doménovou vlastnost třídy a její základní třídy.

    1. V Průzkumníku DSL rozbalte **\\ \<the domain class> data \Element serializace XML Behavior\Class data**.

    2. Ověřte, že **je klíč monikeru** `false` pro každou doménovou vlastnost.

    3. Pokud má doménová třída základní třídu, opakujte proceduru v této třídě.

2. Nastavte **ID serializace**  =  `true` pro doménovou třídu.

     Tato vlastnost je k dispozici v rámci **chování serializace XML**.

### <a name="to-set-a-domain-class-to-be-referenced-by-qualified-key-monikers"></a>Chcete-li nastavit doménovou třídu, na kterou budou odkazovat kvalifikované monikery klíčů

- Set **je klíč monikeru** pro doménovou vlastnost existující doménové třídy. Typ vlastnosti musí být `string` .

    1. V Průzkumníku DSL rozbalte data **\Element serializace XML Behavior\Class data \\ \<the domain class>** a pak vyberte doménovou vlastnost.

    2. V okno Vlastnosti nastavte **klíč moniker** na hodnotu `true` .

- \- ani

     Pomocí nástroje **s pojmenovanou doménovou třídou** vytvořte novou doménovou třídu.

     Tento nástroj vytvoří novou třídu, která má vlastnost domény nazvanou název. **Je název elementu** a **je vlastnosti klíče monikeru** této doménové vlastnosti inicializován na `true` .

- \- ani

     Vytvořte vztah dědičnosti z doménové třídy na jinou třídu, která má vlastnost klíče monikeru.

### <a name="avoid-duplicate-monikers"></a>Vyhněte se duplicitním Monikerům

Použijete-li kvalifikované monikery klíčů, je možné, že dva prvky v modelu uživatele mohou mít stejnou hodnotu ve vlastnosti Key. Například pokud má vaše DSL třídu osoba, která má název vlastnosti, může uživatel nastavit názvy dvou prvků jako stejné. I když se model mohl uložit do souboru, nebude správně znovu načten.

Existuje několik metod, které se mohou vyhnout této situaci:

-   =  `true` Pro klíčovou vlastnost domény je nastaven název elementu. Vyberte vlastnost doména v diagramu definice DSL a pak nastavte hodnotu v okno Vlastnosti.

     Když uživatel vytvoří novou instanci třídy, tato hodnota způsobí, že se vlastnost domain automaticky přiřadí jiné hodnotě. Výchozí chování přidá číslo na konec názvu třídy. To uživateli nebrání v změně názvu na duplicitní, ale v případě, že uživatel nenastavuje hodnotu před uložením modelu, pomáhá.

- Povolte ověřování pro DSL. V Průzkumníku DSL vyberte Editor\Validation a nastavte vlastnosti **používá...** na `true` .

     K dispozici je automaticky vygenerovaná metoda ověřování, která kontroluje nejednoznačnosti. Metoda je v `Load` kategorii ověřování. Tím se zajistí, že uživatel bude upozorněn na to, že nemusí být možné soubor znovu otevřít.

     Další informace najdete v tématu [ověřování v Domain-Specificm jazyce](../modeling/validation-in-a-domain-specific-language.md).

### <a name="moniker-paths-and-qualifiers"></a>Cesty monikerů a kvalifikátory

Kvalifikovaný moniker klíče končí klíčem monikeru a má ve stromu vkládání předponu monikeru jeho nadřazeného parametru. Pokud je například monikerem monikeru Funkce:

```xml
<albumMoniker title="/My Favorites/Jazz after Teatime" />
```

Jedním z skladb v této oblasti by pak mohl být:

```xml
<songMoniker title="/My Favorites/Jazz after Teatime/Hot tea" />
```

Pokud se ale místo toho odkazuje na monikery podle ID, budou monikery následující:

```xml
<albumMoniker Id="77472c3a-9bf9-4085-976a-d97a4745237c" />
<songMoniker title="/77472c3a-9bf9-4085-976a-d97a4745237c/Hot tea" />
```

Všimněte si, že vzhledem k tomu, že identifikátor GUID je jedinečný, nikdy před něj není předpona monikeru jeho nadřazeného objektu.

Pokud víte, že konkrétní vlastnost domény bude mít vždy jedinečnou hodnotu v rámci modelu, můžete nastavit kvalifikátor is **moniker** na `true` pro vlastnost. To způsobí, že se použije jako kvalifikátor, bez použití monikeru nadřazeného objektu. Pokud například nastavíte vlastnosti **Is Moniker Qualifier** a **Is Moniker Key** pro vlastnost Domény nadpisu třídy Na, název nebo identifikátor modelu se v monikerech Pro a jeho vložené děti nepoužívali:

```xml
<albumMoniker name="Jazz after Teatime" />
<songMoniker title="/Jazz after Teatime/Hot tea" />
```

## <a name="customize-the-structure-of-the-xml"></a>Přizpůsobení struktury XML

Chcete-li provést následující přizpůsobení, rozbalte uzel Chování **serializace XML** v průzkumníku DSL. Pod doménovou třídou rozbalte uzel Data elementu a zobrazte seznam vlastností a relací, které jsou zdrojem v této třídě. Vyberte relaci a upravte její možnosti v okno Vlastnosti.

- Pokud **chcete vynechat zdrojový uzel** role a nechat jen seznam cílových elementů, nastavte vynechat element na true. Tuto možnost byste neměli nastavovat, pokud existuje více než jedna relace mezi zdrojovou a cílovou třídou.

    ```xml
    <familyTreeModel ...>
      <!-- The following node is omitted by using Omit Element: -->
      <!-- <people> -->
        <person name="Henry VIII" .../>
        <person name="Elizabeth I" .../>
      <!-- </people> -->
    </familyTreeModel>
    ```

- Pokud **chcete vložit cílové** uzly do uzlů představujících instance relace, nastavte možnost Použít celý formulář. Tato možnost se nastaví automaticky při přidání vlastností domény do vztahu domény.

    ```xml
    <familyTreeModel ...>
      <people>
        <!-- The following node is inserted by using Use Full Form: -->
        <familyTreeModelHasPeople myRelationshipProperty="x1">
          <person name="Henry VIII" .../>
        </familyTreeModelHasPeople>
        <familyTreeModelHasPeople myRelationshipProperty="x2">
          <person name="Elizabeth I" .../>
        </familyTreeModelHasPeople>
      </people>
    </familyTreeModel>
    ```

- Nastavte **Representation** Element tak, aby se vlastnost domény uložila  =   jako prvek místo jako hodnota atributu.

    ```xml
    <person name="Elizabeth I" birthYear="1533">
      <deathYear>1603</deathYear>
    </person>
    ```

- Pokud chcete změnit pořadí, ve kterém jsou atributy a relace serializovány, klikněte pravým tlačítkem na položku v části Data elementu a použijte příkazy nabídky Přesunout nahoru **nebo** Přesunout dolů. 

## <a name="major-customization-using-program-code"></a>Hlavní přizpůsobení pomocí kódu programu

Můžete nahradit části nebo všechny algoritmy serializace.

Doporučujeme prostudovat si kód **v dsl\Generated Code\Serializer.cs** a **SerializationHelper.cs**.

### <a name="to-customize-the-serialization-of-a-particular-class"></a>Přizpůsobení serializace konkrétní třídy

1. Nastavení **je vlastní** v uzlu pro třídu v rámci chování **serializace XML**.

2. Transformujte všechny šablony, sestavte řešení a prozkoumejte výsledné chyby kompilace. Komentáře u každé chyby vysvětlují, jaký kód musíte zadat.

### <a name="to-provide-your-own-serialization-for-the-whole-model"></a>Chcete-li poskytnout vlastní serializace pro celý model

1. Přepsání metod v Dsl\GeneratedCode\SerializationHelper.cs

## <a name="options-in-xml-serialization-behavior"></a>Možnosti v chování serializace XML

V Průzkumníku DSL uzel Chování serializace XML obsahuje podřízený uzel pro každou třídu domény, vztah, tvar, konektor a třídu diagramu. Pod každým z těchto uzlů je seznam vlastností a relací, které jsou zdrojem tohoto prvku. Relace jsou reprezentovány jak vlastními, tak ve zdrojových třídách.

Následující tabulka shrnuje možnosti, které můžete nastavit v této části definice DSL. V každém případě vyberte prvek v Průzkumníku DSL a nastavte možnosti v okno Vlastnosti.

### <a name="xml-class-data"></a>Data třídy XML

Tyto prvky se nacházejí v průzkumníku DSL v **části Chování serializace XML\Data třídy**.

|Vlastnost|Popis|
|-|-|
|Má vlastní schéma elementu|Pokud je true, znamená to, že třída domény má vlastní schéma elementu.|
|Je vlastní|Nastavte na **hodnotu True,** pokud chcete napsat vlastní serializace a deserializace kódu pro tuto třídu domény.<br /><br /> Sestavte řešení a prozkoumejte chyby, abyste zjistili podrobné pokyny.|
|Domain – třída|Doménová třída, na kterou se vztahuje tento uzel dat třídy. Jen pro čtení.|
|Název prvku|Název uzlu XML pro prvky této třídy. Výchozí hodnota je malá verze názvu třídy domény.|
|Název atributu monikeru|Název atributu použitého v elementech monikeru, který obsahuje odkaz. Pokud je tato možnost prázdná, použije se název vlastnosti nebo ID klíče.<br /><br /> V tomto příkladu je to "name":  `<personMoniker name="/Mike Nash"/>`|
|Název elementu monikeru|Název elementu xml používaného pro monikery, které odkazují na prvky této třídy.<br /><br /> Výchozí hodnota je malá verze názvu třídy s příponou "Moniker". Například, `personMoniker`.|
|Název typu monikeru|Název typu xsd vygenerovaného pro monikery prvků této třídy. XSD je v **souboru Dsl\Generated Code \\ \* Schema.xsd.**|
|Serializovat ID|Pokud je true, identifikátor GUID elementu je zahrnutý v souboru . To musí být true, pokud není žádná vlastnost označená jako Is **Moniker Key** a DSL definuje referenční relace k této třídě.|
|Název typu|Název typu XML vygenerovaný v souboru xsd z určené třídy domény.|
|Poznámky|Neformální poznámky přidružené k tomuto prvku|

### <a name="xml-property-data"></a>Data vlastností XML

Uzly vlastností XML se nacházejí v uzlech třídy.

|Vlastnost|Popis|
|-|-|
|Vlastnost domény|Vlastnost, na kterou platí konfigurační data serializace XML. Jen pro čtení.|
|Je klíč monikeru|Pokud je true, vlastnost se používá jako klíč pro vytváření monikerů, které odkazují na instance této třídy domény.|
|Je kvalifikátor monikeru|Pokud je true, vlastnost se použije k vytvoření kvalifikátoru v monikerech. Pokud je false a SerializeId není true pro tuto třídu domény, jsou monikery kvalifikovány monikerem nadřazeného prvku ve stromu vkládání.|
|Reprezentace|Pokud Attribute, vlastnost je serializován jako atribut XML; Pokud element, je serializován jako element; Pokud Ignore, není serializován.|
|Název XML|Název použitý pro atribut xml nebo element představující vlastnost . Ve výchozím nastavení je to malá verze názvu vlastnosti domény.|
|Poznámky|Neformální poznámky přidružené k tomuto prvku|

### <a name="xml-role-data"></a>Data role XML

Uzly dat rolí se nacházejí v uzlech zdrojové třídy.

|Vlastnost|Popis|
|-|-|
|Má vlastní moniker|Nastavte tuto hodnotu na true, pokud chcete zadat vlastní kód pro generování a řešení monikerů, které procházují tento vztah.<br /><br /> Podrobné pokyny zobrazíte tak, že sestavíte řešení a poklikáte na chybové zprávy.|
|Vztah domény|Určuje relaci, na kterou se tyto možnosti vztahují. Jen pro čtení.|
|Vynechat element|Pokud je true, uzel XML, který odpovídá zdrojové roli, je ze schématu vynechán.<br /><br /> Pokud existuje více než jedna relace mezi zdrojovou a cílovou třídou, tento uzel role rozlišuje mezi propojeními, která patří do těchto dvou relací. Proto doporučujeme tuto možnost nenastavovat.|
|Název elementu role|Určuje název elementu XML, který je odvozen od zdrojové role. Výchozí hodnota je název vlastnosti role.|
|Použití úplného formuláře|Pokud je true, každý cílový prvek nebo moniker je uzavřen v uzlu XML představující vztah. Pokud má relace vlastní vlastnosti domény, měla by být nastavená na hodnotu true.|

## <a name="see-also"></a>Viz také

- [Navigace v modelu a aktualizace modelu v kódu programu](../modeling/navigating-and-updating-a-model-in-program-code.md)
- [Vytváření kódu z jazyka specifického pro doménu](../modeling/generating-code-from-a-domain-specific-language.md)
