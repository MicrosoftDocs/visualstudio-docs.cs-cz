---
title: Přizpůsobení File Storage a serializace XML | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
f1_keywords:
- vs.dsltools.dsldesigner.xmlbehavior
helpviewer_keywords:
- Domain-Specific Language, serialization
ms.assetid: 76c53ef1-e3b9-45da-b425-1bddb3c01395
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 0af30f31e7ee63c521a3a7c1acbafbb1cd109832
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/30/2020
ms.locfileid: "85548015"
---
# <a name="customizing-file-storage-and-xml-serialization"></a>Přizpůsobení souborového úložiště a serializace XML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Když uživatel v nástroji uloží instanci nebo *model*určitého jazyka (DSL), vytvoří [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] se soubor XML nebo se aktualizuje. Soubor lze znovu načíst a znovu vytvořit model ve Storu.

 Schéma serializace můžete přizpůsobit úpravou nastavení v části **chování serializace XML** v Průzkumníku DSL. U každé doménové třídy, vlastnosti a vztahu je v rámci **chování serializace XML** uzel. Relace jsou umístěny pod svými zdrojovými třídami. K dispozici jsou také uzly odpovídající třídám Shape, Connector a diagram.

 Můžete také napsat kód programu pro pokročilejší přizpůsobení.

> [!NOTE]
> Pokud chcete model uložit v konkrétním formátu, ale nemusíte ho znovu načítat z tohoto formuláře, zvažte použití textových šablon k vygenerování výstupu z modelu namísto vlastního schématu serializace. Další informace najdete v tématu [generování kódu z jazyka specifického pro doménu](../modeling/generating-code-from-a-domain-specific-language.md).

## <a name="model-and-diagram-files"></a>Soubory modelů a diagramů
 Každý model je obvykle uložen ve dvou souborech:

- Soubor modelu má název, například **Model1. mydsl**. Ukládá prvky modelu a vztahy a jejich vlastnosti. Přípona souboru, například **. mydsl** , je určena vlastností **Extension** uzlu **editoru** v definici DSL.

- Soubor diagramu má název, například **Model1. mydsl. diagram**. Ukládá tvary, konektory a jejich umístění, barvy, tloušťky čar a další podrobnosti o vzhledu diagramu. Pokud uživatel odstraní soubor **. diagram** , podstatné informace v modelu nebudou ztraceny. Ztratí se jenom rozložení diagramu. Při otevření souboru modelu se vytvoří výchozí sada obrazců a konektorů.

#### <a name="to-change-the-file-extension-of-a-dsl"></a>Změna přípony souboru DSL

1. Otevřete definici DSL. V Průzkumníku DSL klikněte na uzel Editor.

2. V okno Vlastnosti upravte vlastnost **přípona** . Nezahrnujte úvodní znak "". "přípony názvu souboru.

3. V Průzkumník řešení změňte název souborů šablon dvou položek v **DslPackage\ProjectItemTemplates**. Názvy těchto souborů mají následující formát:

     `myDsl.diagram`

     `myDsl.myDsl`

## <a name="the-default-serialization-scheme"></a>Výchozí schéma serializace
 Chcete-li vytvořit příklad pro toto téma, byla použita následující definice DSL.

 ![Diagram definice DSL &#45; model struktury řady](../modeling/media/familyt-person.png "FamilyT_Person")

 Tato DSL byla použita k vytvoření modelu, který má následující vzhled na obrazovce.

 ![Diagram stromu rodiny, panel nástrojů a Průzkumník](../modeling/media/familyt-instance.png "FamilyT_Instance")

 Tento model se uložil a pak se znovu otevřel v textovém editoru XML:

```
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

    ```
    <personMoniker name="/f817b728-e920-458e-bb99-98edc469d78f/Elizabeth I" />
    ```

## <a name="understanding-monikers"></a>Principy monikerů
 Monikery slouží k reprezentaci křížových odkazů mezi různými částmi modelu a souborů diagramu. Používají se také v `.diagram` souboru pro odkazy na uzly v souboru modelu. Existují dvě formy monikeru:

- *Monikery ID* mají v nabídce identifikátor GUID cílového prvku. Příklad:

  ```
  <personShapeMoniker Id="f79734c0-3da1-4d72-9514-848fa9e75157" />

  ```

- *Kvalifikované monikery klíčů* identifikují cílový prvek hodnotou určené doménové vlastnosti, která se nazývá klíč monikeru. Moniker cílového prvku je předponou moniker jeho nadřazeného prvku ve stromové struktuře vztahů vložení.

   Následující příklady jsou pořízeny pomocí DSL, v němž existuje doménová třída s názvem album, která má vztah vložení do doménové třídy s názvem Song:

  ```
  <albumMoniker title="/My Favorites/Jazz after Teatime" />
  <songMoniker title="/My Favorites/Jazz after Teatime/Hot tea" />

  ```

   Kvalifikované monikery klíčů budou použity, pokud má cílová třída doménovou vlastnost, pro kterou je možnost **klíč monikeru** nastavená na hodnotu `true` v **chování serializace XML**. V tomto příkladu je tato možnost nastavená pro vlastnosti domény s názvem "title" v doménových třídách "album" a "skladba".

  Kvalifikované monikery klíčů je snazší číst než monikery ID. Pokud máte v úmyslu načíst XML souborů modelu, zvažte použití kvalifikovaných monikerů klíčů. Je však možné, že uživatel nastaví více než jeden prvek tak, aby měl stejný klíč monikeru. Duplicitní klíče by mohly způsobit, že se soubor nenačítá správně. Proto pokud definujete doménovou třídu, na kterou se odkazuje pomocí úplných monikerů klíčů, měli byste zvážit, jak zabránit uživateli v ukládání souboru, který má duplicitní monikery.

#### <a name="to-set-a-domain-class-to-be-referenced-by-id-monikers"></a>Nastavení doménové třídy, na kterou odkazují monikery ID

1. Ujistěte se, že **je klíč monikeru** `false` pro každou doménovou vlastnost třídy a její základní třídy.

    1. V Průzkumníku DSL rozbalte data \Element **serializace XML \\ Behavior\Class data** _\<the domain class>_ **\Element Data**.

    2. Ověřte, že **je klíč monikeru** `false` pro každou doménovou vlastnost.

    3. Pokud má doménová třída základní třídu, opakujte proceduru v této třídě.

2. Nastavte **ID serializace**  =  `true` pro doménovou třídu.

     Tato vlastnost je k dispozici v rámci **chování serializace XML**.

#### <a name="to-set-a-domain-class-to-be-referenced-by-qualified-key-monikers"></a>Chcete-li nastavit doménovou třídu, na kterou budou odkazovat kvalifikované monikery klíčů

- Set **je klíč monikeru** pro doménovou vlastnost existující doménové třídy. Typ vlastnosti musí být `string` .

    1. V Průzkumníku DSL rozbalte data \Element **serializace XML \\ Behavior\Class data** _\<the domain class>_ **\Element Data**a pak vyberte doménovou vlastnost.

    2. V okno Vlastnosti nastavte **klíč moniker** na hodnotu `true` .

- \-ani

     Pomocí nástroje **s pojmenovanou doménovou třídou** vytvořte novou doménovou třídu.

     Tento nástroj vytvoří novou třídu, která má vlastnost domény nazvanou název. **Je název elementu** a **je vlastnosti klíče monikeru** této doménové vlastnosti inicializován na `true` .

- \-ani

     Vytvořte vztah dědičnosti z doménové třídy na jinou třídu, která má vlastnost klíče monikeru.

### <a name="avoiding-duplicate-monikers"></a>Vyloučení duplicitních monikerů
 Použijete-li kvalifikované monikery klíčů, je možné, že dva prvky v modelu uživatele mohou mít stejnou hodnotu ve vlastnosti Key. Například pokud má vaše DSL třídu osoba, která má název vlastnosti, může uživatel nastavit názvy dvou prvků jako stejné. I když se model mohl uložit do souboru, nebude správně znovu načten.

 Existuje několik metod, které se mohou vyhnout této situaci:

- **Is Element Name**  =  `true` Pro klíčovou vlastnost domény je nastaven název elementu. Vyberte vlastnost doména v diagramu definice DSL a pak nastavte hodnotu v okno Vlastnosti.

     Když uživatel vytvoří novou instanci třídy, tato hodnota způsobí, že se vlastnost domain automaticky přiřadí jiné hodnotě. Výchozí chování přidá číslo na konec názvu třídy. To uživateli nebrání v změně názvu na duplicitní, ale v případě, že uživatel nenastavuje hodnotu před uložením modelu, pomáhá.

- Povolte ověřování pro DSL. V Průzkumníku DSL vyberte Editor\Validation a nastavte vlastnosti **používá...** na `true` .

     K dispozici je automaticky generovaná metoda ověřování, která kontroluje nejednoznačnosti. Metoda je v `Load` kategorii ověřování. Tím se zajistí, že uživatel bude upozorněn na to, že nemusí být možné soubor znovu otevřít.

     Další informace najdete v tématu [ověření v jazyce specifickém pro doménu](../modeling/validation-in-a-domain-specific-language.md).

### <a name="moniker-paths-and-qualifiers"></a>Cesty monikerů a kvalifikátory
 Úplný moniker klíče končí klíčem monikeru a je předponou jeho nadřazeného prvku ve stromu vkládání. Pokud je například moniker alba:

```
<albumMoniker title="/My Favorites/Jazz after Teatime" />

```

 Pak může být jedna z písní v tomto albu:

```
<songMoniker title="/My Favorites/Jazz after Teatime/Hot tea" />
```

 Pokud je však místo toho odkazováno na alba pomocí ID, pak budou monikery následující:

```
<albumMoniker Id="77472c3a-9bf9-4085-976a-d97a4745237c" />
<songMoniker title="/77472c3a-9bf9-4085-976a-d97a4745237c/Hot tea" />
```

 Všimněte si, že protože identifikátor GUID je jedinečný, není nikdy nahrazen monikerem jeho nadřazeného objektu.

 Pokud víte, že určitá doménová vlastnost bude mít vždycky jedinečnou hodnotu v rámci modelu, můžete pro tuto vlastnost nastavit **kvalifikátor monikeru** `true` . To způsobí, že se použije jako kvalifikátor bez použití monikeru nadřazeného objektu. Pokud například nakonfigurujete **kvalifikátor monikeru** a **je klíč monikeru** pro vlastnost název domény třídy alba, název modelu nebo identifikátor se nepoužívá v monikerech pro album a jeho vložené podřízené položky:

```
<albumMoniker name="Jazz after Teatime" />
<songMoniker title="/Jazz after Teatime/Hot tea" />

```

## <a name="customizing-the-structure-of-the-xml"></a>Přizpůsobení struktury XML
 Chcete-li provést následující přizpůsobení, rozbalte uzel **chování serializace XML** v Průzkumníku DSL. V rámci doménové třídy rozbalte uzel data elementu, abyste viděli seznam vlastností a relací, které jsou v této třídě napsány jako zdroje. Vyberte relaci a upravte její možnosti v okno Vlastnosti.

- Nastavte **vynechání elementu** na hodnotu true, chcete-li vynechat uzel zdrojové role a opustit pouze seznam cílových elementů. Tuto možnost byste neměli nastavit, pokud existuje více než jedna relace mezi zdrojovou a cílovou třídou.

    ```

    <familyTreeModel ...>
      <!-- The following node is omitted by using Omit Element: -->
      <!-- <people> -->
        <person name="Henry VIII" .../>
        <person name="Elizabeth I" .../>
      <!-- </people> -->
    </familyTreeModel>

    ```

- Nastavte **použít úplný formulář** pro vložení cílových uzlů do uzlů, které představují instance vztahů. Tato možnost se nastaví automaticky při přidání vlastností domény do doménového vztahu.

    ```

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

- Nastavte **element reprezentaci**  =  **Element** tak, aby měl doménovou vlastnost uloženou jako prvek namísto hodnoty atributu.

    ```
    <person name="Elizabeth I" birthYear="1533">
      <deathYear>1603</deathYear>
    </person>
    ```

- Chcete-li změnit pořadí, ve kterém jsou atributy a vztahy serializovány, klikněte pravým tlačítkem myši na položku v části data prvku a použijte příkazy nabídky **Přesunout nahoru** nebo **Přesunout dolů** .

## <a name="major-customization-using-program-code"></a>Hlavní přizpůsobení pomocí kódu programu
 Můžete nahradit části nebo všechny algoritmy serializace.

 Doporučujeme, abyste si prostudovali kód v **Dsl\Generated Code\Serializer.cs** a **SerializationHelper.cs**.

#### <a name="to-customize-the-serialization-of-a-particular-class"></a>Přizpůsobení serializace konkrétní třídy

1. Sada **je vlastní** v uzlu pro danou třídu v **chování serializace XML**.

2. Transformujte všechny šablony, sestavte řešení a prozkoumejte výsledné chyby při kompilaci. Komentáře poblíž každé chyby vysvětlují, jaký kód je třeba zadat.

#### <a name="to-provide-your-own-serialization-for-the-whole-model"></a>Poskytnutí vlastního serializace pro celý model

1. Metody přepisu v Dsl\GeneratedCode\SerializationHelper.cs

## <a name="options-in-xml-serialization-behavior"></a>Možnosti v chování serializace XML
 V Průzkumníku DSL obsahuje uzel chování serializace XML podřízený uzel pro každou třídu domény, vztah, tvar, spojnici a diagram třídy. Pod každým z těchto uzlů je seznam vlastností a vztahů, které jsou v daném elementu napsány. Vztahy jsou reprezentovány v jejich vlastním právu a v rámci jejich zdrojových tříd.

 Následující tabulka shrnuje možnosti, které můžete nastavit v této části definice DSL. V každém případě vyberte prvek v Průzkumníku DSL a nastavte možnosti v okno Vlastnosti.

### <a name="xml-class-data"></a>Data třídy XML
 Tyto prvky se nacházejí v Průzkumníkovi DSL pod **daty serializace XML Behavior\Class**.

|Vlastnost|Popis|
|-|-|
|Má vlastní schéma elementů|Pokud má hodnotu true, znamená to, že doménová třída má schéma vlastního elementu.|
|Je vlastní|Nastavte na **hodnotu true** , pokud chcete zapsat vlastní serializaci a kód deserializace pro tuto doménovou třídu.<br /><br /> Sestavte řešení a prozkoumejte chyby a zjistěte podrobné pokyny.|
|Domain – třída|Doménová třída, na kterou se vztahuje tento uzel dat třídy Jen pro čtení.|
|Název prvku|Název uzlu XML pro prvky této třídy. Výchozí hodnota je nižší verze názvu doménové třídy.|
|Název atributu monikeru|Název atributu použitého v elementech monikeru, který má obsahovat odkaz. Pokud je pole prázdné, použije se název vlastnosti klíče nebo ID.<br /><br /> V tomto příkladu je to "Name":`<personMoniker name="/Mike Nash"/>`|
|Název elementu monikeru|Název XML elementu, který se používá pro monikery, které odkazují na prvky této třídy.<br /><br /> Výchozí hodnota je malá verze názvu třídy s příponou "moniker". Například, `personMoniker`.|
|Název typu monikeru|Název typu XSD vygenerovaného pro monikery v elementech této třídy XSD je ve **schématu Dsl\Generated Code \\ \* Schema. xsd.**|
|ID serializace|Je-li nastavena hodnota true, je identifikátor GUID elementu obsažen v souboru. Tato hodnota musí být true, pokud neexistuje žádná vlastnost, která je označena **klíčovým** slovem MONIKER a DSL definuje referenční vztahy k této třídě.|
|Název typu|Název typu XML vygenerovaného v XSD z určené doménové třídy|
|Poznámky|Neformální poznámky přidružené k tomuto elementu|

### <a name="xml-property-data"></a>Data vlastnosti XML
 Uzly vlastností XML jsou nalezeny v uzlech třídy.

|Vlastnost|Popis|
|-|-|
|Doménová vlastnost|Vlastnost, na kterou se vztahují data konfigurace serializace XML Jen pro čtení.|
|Je klíč monikeru|Při hodnotě true se vlastnost používá jako klíč pro vytváření monikerů, které odkazují na instance této doménové třídy.|
|Je kvalifikátor monikeru|Při hodnotě true se vlastnost používá k vytvoření kvalifikátoru v monikerech. Pokud je hodnota false a pokud SerializeId není pro tuto doménovou třídu true, monikery jsou kvalifikovány monikerem nadřazeného elementu ve stromu vkládání.|
|Obrázek|Pokud je atribut, vlastnost serializována jako atribut XML; je-li element, je serializován jako element; Pokud je ignorováno, není serializováno.|
|Název XML|Název, který se používá pro atribut nebo element XML představující vlastnost Ve výchozím nastavení je to malá verze názvu doménové vlastnosti.|
|Poznámky|Neformální poznámky přidružené k tomuto elementu|

### <a name="xml-role-data"></a>Data role XML
 Uzly dat role se nacházejí v uzlech zdrojové třídy.

|Vlastnost|Popis|
|--------------|-----------------|
|Má vlastní moniker|Nastavte na hodnotu true, pokud chcete zadat vlastní kód pro generování a překlad monikerů, které procházejí touto relací.<br /><br /> Pro podrobné pokyny Sestavte řešení a dvakrát klikněte na chybové zprávy.|
|Doménový vztah|Určuje vztah, pro který tyto možnosti platí. Jen pro čtení.|
|Vynechat element|Pokud je nastaveno na true, uzel XML, který odpovídá zdrojové roli, se ve schématu vynechá.<br /><br /> Pokud existuje více než jedna relace mezi zdrojovou a cílovou třídou, tento uzel role rozlišuje mezi odkazy, které patří do obou vztahů. Proto doporučujeme, abyste v tomto případě tuto možnost nestavili.|
|Název elementu role|Určuje název elementu XML, který je odvozen ze zdrojové role. Výchozí hodnota je název vlastnosti role.|
|Použít úplný formulář|Je-li nastavena hodnota true, je každý cílový element nebo moniker uzavřen v uzlu XML představujícím relaci. Tato hodnota by měla být nastavena na hodnotu true, pokud má vztah své vlastní doménové vlastnosti.|

## <a name="see-also"></a>Viz také
 [Navigace a aktualizace modelu v programovém kódu](../modeling/navigating-and-updating-a-model-in-program-code.md) [generování kódu z jazyka specifického pro doménu](../modeling/generating-code-from-a-domain-specific-language.md)
