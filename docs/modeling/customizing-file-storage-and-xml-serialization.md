---
title: Přizpůsobení souborového úložiště a serializace XML
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.dsltools.dsldesigner.xmlbehavior
helpviewer_keywords:
- Domain-Specific Language, serialization
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 8a21067eab6e55f3fb031e57fa2257b0d40a7eb6
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49886458"
---
# <a name="customize-file-storage-and-xml-serialization"></a>Přizpůsobení úložiště souborů a serializace XML

Když uživatel uloží instanci, nebo *modelu*, jazyka specifického pro doménu (DSL) v sadě Visual Studio, se vytvoří nebo aktualizuje soubor XML. Soubor je možné znovu zavést, znovu vytvořte model v Store.

Schéma serializace můžete přizpůsobit úpravou nastavení v části **chování serializace Xml** v Průzkumník DSL. Je uzel v rámci **chování serializace Xml** pro každou doménovou třídou, vlastnost a relace. Relace se nachází v jejich zdrojových tříd. Existují také uzly odpovídající tvar, konektor a diagram tříd.

Můžete také napsat kód programu pro pokročilejší přizpůsobení.

> [!NOTE]
> Pokud chcete uložit model v určitém formátu, ale není potřeba ho znovu načíst formulář, zvažte použití textových šablon generovat výstup z modelu, namísto schéma vlastní serializace. Další informace najdete v tématu [generování kódu z jazyka specifického pro doménu](../modeling/generating-code-from-a-domain-specific-language.md).

## <a name="model-and-diagram-files"></a>Model a soubory diagramu

Každý model je obvykle uložen ve dvou souborech:

-   Soubor modelu má název například **Model1.mydsl**. Ukládá prvků modelu a vztahy a jejich vlastnosti. Přípona souboru, jako **.mydsl** závisí **FileExtension** vlastnost **Editor** uzlu v definici DSL.

-   Soubor diagramu má název například **Model1.mydsl.diagram**. Ukládají se tvary, konektory a jejich pozice, barvy, tlouštěk čáry a další podrobnosti o vzhled diagramu. Pokud uživatel odstraní **.diagram** souboru, důležité informace v modelu nedojde ke ztrátě. Rozložení diagramu je ztraceny. Při otevření souboru modelu výchozí sadu obrazců a konektorů se vytvoří.

### <a name="to-change-the-file-extension-of-a-dsl"></a>Chcete-li změnit příponu souboru DSL

1.  Otevřete definici DSL. V Průzkumníku DSL klikněte na uzel Editor.

2.  V okně Vlastnosti upravte **FileExtension** vlastnost. Nezahrnují počáteční "." z přípony názvu souboru.

3.  V Průzkumníku řešení, změňte název soubory šablon dvou položek v **DslPackage\ProjectItemTemplates**. Tyto soubory obsahují názvy, které tento formát:

     `myDsl.diagram`

     `myDsl.myDsl`

## <a name="the-default-serialization-scheme"></a>Výchozí schéma serializace

Chcete-li vytvořit příklad pro toto téma, byl použit následující definici DSL.

![Diagramem definice DSL &#45; řady stromu modelu](../modeling/media/familyt_person.png)

Tento DSL byla použita k vytvoření modelu, který má následující vzhled na obrazovce.

![Řada stromového diagramu, nástrojů a Průzkumníku](../modeling/media/familyt_instance.png)

Tento model byl uložen a pak znovu otevřít v textovém editoru XML:

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

Všimněte si následujících o serializovaný model:

-   Každý uzel XML má název, který je stejný jako název třídy domény, s tím rozdílem, že je počáteční písmeno malá písmena. Například `familyTreeModel` a `person`.

-   Vlastnosti domény, jako je název a roknarozeni serializují jako atributy v uzlů XML. Znovu počáteční znaky názvu vlastnosti je převeden na malá písmena.

-   Každý vztah je serializován jako uzel XML vnořit do zdroje konci vztahu. Uzel má stejný název jako vlastnost zdrojové role, ale s počáteční znak malé písmeno.

     Například v definici DSL, která se nazývá role **lidé** pochází na **FamilyTree** třídy.  V souboru XML, to představuje uzel s názvem `people` vnořené uvnitř `familyTreeModel` uzlu.

-   Konci každý vztah obsažení serializován jako uzel vnořen v souladu s relace. Například `people` uzel obsahuje několik `person` uzly.

-   Cílový element end relace každý odkaz je serializován jako *moniker*, který kóduje odkaz na target element.

     Třeba v části `person` uzlu, může být `children` vztah. Tento uzel obsahuje monikery, například:

    ```xml
    <personMoniker name="/f817b728-e920-458e-bb99-98edc469d78f/Elizabeth I" />
    ```

## <a name="understand-monikers"></a>Vysvětlení Monikery

Monikery se používá k reprezentování křížové odkazy mezi různé části soubory modelu a diagram. Používají se také v `.diagram` souboru pro odkazování na uzly v souboru modelu. Existují dvě formy moniker:

-   *ID monikery* citovat identifikátor GUID cílového prvku. Příklad:

    ```xml
    <personShapeMoniker Id="f79734c0-3da1-4d72-9514-848fa9e75157" />
    ```

-   *Kvalifikovaný klíče monikery* identifikovat podle hodnoty určené doménové vlastnost s názvem klíčem monikeru cílového prvku. Moniker jeho nadřazený element ve stromové struktuře vkládání relace má předponu moniker cílového prvku.

     Následující příklady jsou převzaty z DSL existuje ve kterém je doménovou třídu s názvem alb, která má vztah obsažení k doméně třídy s názvem skladby:

    ```xml
    <albumMoniker title="/My Favorites/Jazz after Teatime" />
    <songMoniker title="/My Favorites/Jazz after Teatime/Hot tea" />
    ```

     Kvalifikovaný klíče monikery bude použit, pokud cílová třída obsahuje doménová vlastnost, jehož možnost **je klíčem Monikeru** je nastavena na `true` v **chování serializace Xml**. V tomto příkladu je tato možnost nastavena pro vlastnosti domény v doménové třídy "Album" a "Skladby" s názvem "Title".

Jsou tyto monikery kvalifikovaný klíče čitelnější než ID monikery. Pokud máte v plánu XML soubory modelu čtení osobami, zvažte použití kvalifikovaný zástupných názvů klíčů. Nicméně je možné pro uživatele nastavit více než jeden element stejný klíč moniker. Duplicitní klíče může způsobit, že není soubor znovu načíst správně. Proto pokud definujete doménovou třídou, která je popsána pomocí kvalifikovaného zástupných názvů klíčů, měli byste zvážit způsoby, jak uživateli zabránit v uložení souboru, který má duplicitní monikery.

### <a name="to-set-a-domain-class-to-be-referenced-by-id-monikers"></a>Chcete-li nastavit doménová třída může odkazovat monikery ID

1.  Ujistěte se, že **je klíčem Monikeru** je `false` pro každou doménovou vlastnost ve třídě a její základní třídy.

    1.  V okně Průzkumník DSL, rozbalte **Data Behavior\Class serializace Xml\\\<doménová třída > \Element Data**.

    2.  Ověřte, že **je klíčem Monikeru** je `false` pro každou doménovou vlastnost.

    3.  Pokud má doménová třída základní třídu, opakujte postup v dané třídě.

2.  Nastavte **serializovat Id**  =  `true` pro doménovou třídu.

     Tato vlastnost najdete v části **chování serializace Xml**.

### <a name="to-set-a-domain-class-to-be-referenced-by-qualified-key-monikers"></a>Chcete-li nastavit doménová třída může odkazovat kvalifikovaný zástupných názvů klíčů

-   Nastavte **je klíčem Monikeru** doménovou vlastnost existující doménové třídy. Typ vlastnosti musí být `string`.

    1.  V okně Průzkumník DSL, rozbalte **Data Behavior\Class serializace Xml\\\<doménová třída > \Element Data**a potom vyberte vlastnost domain.

    2.  V okně Vlastnosti nastavte **je klíčem Monikeru** k `true`.

-   \- nebo –

     Vytvořit novou pomocí třídy domény **doménovou třídu s názvem** nástroj.

     Tento nástroj vytvoří novou třídu, která má doménová vlastnost, která volá název. **Je název elementu** a **je klíčem Monikeru** vlastnosti této vlastnosti domény jsou inicializovány na hodnotu `true`.

-   \- nebo –

     Vytvořte vztah dědičnosti z třídy domény na jinou třídu, která má klíčovou vlastnost moniker.

### <a name="avoid-duplicate-monikers"></a>Vyhněte se duplicitní Monikery

Pokud používáte kvalifikovaný zástupných názvů klíčů, je možné, že dva prvky v modelu uživatel může mít stejnou hodnotu ve vlastnosti klíče. Například pokud vaše DSL neobsahuje třídu osoba, která má vlastnost Name, uživatel může nastavit názvy dvou prvků být stejné. I když modelu může být uložen do souboru, to nebude znovu načíst správně.

Existuje několik metod, které se vyhnout této situaci:

-   Nastavte **je název elementu**  =  `true` pro vlastnost klíče domény. Vyberte vlastnost domény v definici DSL diagramu a potom v okně Vlastnosti nastavte hodnotu.

     Když uživatel vytvoří novou instanci třídy, tato hodnota způsobí, že vlastnost domain pro automaticky přiřadit jinou hodnotu. Výchozí chování přidá číslo na konec názvu třídy. Přesto uživateli možnost měnit název duplicitní, ale je v případě, když uživatel není nastavená hodnota před uložením modelu.

-   Povolení ověřování pro DSL. V Průzkumníku DSL vyberte Editor\Validation a nastavte **používá...**  vlastností `true`.

     Je automaticky generované ověřování, která kontroluje pro metodu nejednoznačnosti. Metoda je `Load` ověření kategorie. Tím je zajištěno, že uživatel, zobrazí upozornění, že nemusí být možné znovuotevření daného souboru.

     Další informace najdete v tématu [ověřování v jazyka specifického pro doménu](../modeling/validation-in-a-domain-specific-language.md).

### <a name="moniker-paths-and-qualifiers"></a>Zástupný název cesty a kvalifikátory

Kvalifikovaný klíče zástupný název končí klíčem monikeru a předchází zástupný název svého nadřazeného objektu ve stromové struktuře vkládání. Například, pokud je moniker alba:

```xml
<albumMoniker title="/My Favorites/Jazz after Teatime" />
```

Pak může být jedna z skladeb nějž:

```xml
<songMoniker title="/My Favorites/Jazz after Teatime/Hot tea" />
```

Ale pokud alb je odkazováno dle ID místo toho, pak zástupných názvů by měl vypadat takto:

```xml
<albumMoniker Id="77472c3a-9bf9-4085-976a-d97a4745237c" />
<songMoniker title="/77472c3a-9bf9-4085-976a-d97a4745237c/Hot tea" />
```

Všimněte si, že vzhledem k tomu, že je jedinečný identifikátor GUID, to je nikdy předchází zástupný název svého nadřazeného objektu.

Pokud znáte konkrétní doménová vlastnost, která bude mít vždy jedinečná hodnota v rámci modelu, můžete nastavit **kvalifikátorem Monikeru je** k `true` pro tuto vlastnost. To způsobí, že má být použit jako kvalifikátoru, bez použití monikeru nadřazeného prvku. Například, pokud nastavíte **kvalifikátorem Monikeru je** a **je klíčem Monikeru** pro vlastnost název domény alba třídy, název nebo identifikátor modelu se nepoužívá v monikery pro alba a jeho embedded podřízené položky:

```xml
<albumMoniker name="Jazz after Teatime" />
<songMoniker title="/Jazz after Teatime/Hot tea" />
```

## <a name="customize-the-structure-of-the-xml"></a>Přizpůsobení struktura XML

Chcete-li provést následující úpravy, rozbalte **chování serializace Xml** uzel v Průzkumník DSL. V části doménovou třídou rozbalte uzel Data elementu zobrazíte seznam vlastností a vztahů, které pocházejí na tuto třídu. Vyberte vztah a upravit jeho možnosti v okně Vlastnosti.

-   Nastavte **vynechat Element** chcete vynechat, nechte zdrojový uzel role, byste museli opustit prostý seznam cílových elementů na hodnotu true. Neměli nastavte tuto možnost, pokud existuje více než jeden vztah mezi zdrojové a cílové třídy.

    ```xml
    <familyTreeModel ...>
      <!-- The following node is omitted by using Omit Element: -->
      <!-- <people> -->
        <person name="Henry VIII" .../>
        <person name="Elizabeth I" .../>
      <!-- </people> -->
    </familyTreeModel>
    ```

-   Nastavte **použijte úplný formát** vložit cílové uzly do uzlů představujících instance relace. Tato možnost je nastavena automaticky při přidání vlastnosti domény do doménového vztahu.

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

-   Nastavte **reprezentace** = **Element** mít doménovou vlastnost uložený jako prvek místo jako hodnotu atributu.

    ```xml
    <person name="Elizabeth I" birthYear="1533">
      <deathYear>1603</deathYear>
    </person>
    ```

-   Změna pořadí serializovat atributy a vztahy, klikněte pravým tlačítkem na položku v rámci elementu Data a použít **nahoru** nebo **přesunout dolů** příkazů nabídky.

## <a name="major-customization-using-program-code"></a>Hlavní přizpůsobení pomocí kódu programu

Můžete nahradit části nebo všechny algoritmy serializace.

Doporučujeme, abyste si prostudovali kód v **Dsl\Generated Code\Serializer.cs** a **SerializationHelper.cs**.

### <a name="to-customize-the-serialization-of-a-particular-class"></a>K přizpůsobení serializaci určité třídy

1.  Nastavte **je vlastní** v uzlu pro danou třídu v rámci **chování serializace Xml**.

2.  Transformovat všechny šablony, sestavte řešení a zjistěte případné chyby kompilace. Jaký kód je nutné zadat vysvětlují komentáře u každé chyby.

### <a name="to-provide-your-own-serialization-for-the-whole-model"></a>Chcete-li zadat vlastní serializace pro celý model

1.  Přepište metody v Dsl\GeneratedCode\SerializationHelper.cs

## <a name="options-in-xml-serialization-behavior"></a>Možnosti v chování serializace Xml

V Průzkumníku DSL uzel chování serializace Xml obsahuje podřízený uzel pro každou doménovou třídu, relace, tvar, konektor a diagram tříd. Pod každým z těchto uzlů je uveden seznam vlastností a vztahů zdroje na prvku. Vztahy jsou reprezentovány ve své vlastní vpravo a pod jejich zdrojové třídy.

Následující tabulka shrnuje možnosti, které můžete nastavit v této části definici DSL. V každém případě vyberte element v nástroji Průzkumník DSL a nastavte možnosti v okně Vlastnosti.

### <a name="xml-class-data"></a>Data třídy XML

Tyto prvky se nacházejí v Průzkumník DSL pod **Data Behavior\Class serializace Xml**.

|||
|-|-|
|Vlastnost|Popis|
|Obsahuje vlastní schéma elementů|Při hodnotě True označuje, jestli má doménová třída vlastní schéma elementů|
|Vlastní|Nastavte na **True** Pokud budete chtít napsat vlastní kód serializace a deserializace pro tuto doménovou třídu.<br /><br /> Sestavte řešení a zjistěte chyby zjistit podrobné pokyny.|
|Doménová třída|Doménová třída, ke kterému se vztahuje tento datový uzel třídy. Jen pro čtení.|
|Název elementu|Název uzlu XML pro elementy této třídy. Výchozí hodnota je malá verzi třídy název domény.|
|Název atributu monikeru|Název atributu použitého v elementech monikeru, obsahují odkaz. Pokud je pole prázdné, název vlastnosti klíče nebo ID. se používá.<br /><br /> V tomto příkladu je "name":  `<personMoniker name="/Mike Nash"/>`|
|Název elementu monikeru|Název elementu xml použitého pro monikery v, které odkazují na prvky této třídy.<br /><br /> Výchozí hodnota je malá verzi příponu "Moniker" název třídy. Například `personMoniker`.|
|Zástupný název typu|Název typu xsd vygenerovaného pro monikery v elementech této třídy. XSD je v **Dsl\Generated kód\\\*Schema.xsd**|
|Serializace Id|Při hodnotě True se element identifikátoru GUID je součástí souboru. Toto musí být true, pokud není žádná vlastnost, která je označena **je klíčem Monikeru** a DSL definuje vztahy odkazu do této třídy.|
|Název typu|Název typu xml vygenerovaného v xsd z určené doménové třídy.|
|Poznámky|Neformální poznámky přidružené k tento element|

### <a name="xml-property-data"></a>Data vlastnosti XML

XML – vlastnost uzly jsou nalezené pod uzly třídy.

|||
|-|-|
|Vlastnost|Popis|
|Doménová vlastnost|Vlastnost, ke které se vztahují data konfigurace serializace xml. Jen pro čtení.|
|Je klíčem Monikeru|Při hodnotě True se vlastnost používá jako klíč k vytváření monikerů, které odkazují na instance této třídy domény.|
|Je kvalifikátorem Monikeru|Při hodnotě True se vlastnost používá k vytvoření kvalifikátoru v monikerech. Pokud má hodnotu false a SerializeId neplatí pro tuto třídu domény, jsou monikery kvalifikována moniker nadřazený element ve stromové struktuře vkládání.|
|Reprezentace|Pokud je atribut vlastnost serializuje jako atribut xml; Pokud Element, bude serializována jako element; Pokud ignorovat, nejde serializovat.|
|Název XML|Název použitý pro atribut nebo element xml představující vlastnost. Ve výchozím nastavení toto je verze malá vlastnost názvu domény.|
|Poznámky|Neformální poznámky přidružené k tento element|

### <a name="xml-role-data"></a>Data XML Role

Datové uzly role jsou nalezené pod uzly třída zdroje.

|Vlastnost|Popis|
|-|-|
|Má vlastní Monikeru|Nastavte na hodnotu true, pokud chcete poskytnout vlastní kód pro generování a jejich řešení zástupných názvů, které přecházejí přes tuto relaci.<br /><br /> Podrobné pokyny najdete sestavte řešení a potom dvakrát klikněte na chybové zprávy.|
|Doménový vztah|Určuje vztah, na kterou se vztahují tyto možnosti. Jen pro čtení.|
|Vynechat – Element|Při hodnotě true je ve schématu vynechá uzel XML odpovídající zdrojové roli.<br /><br /> Pokud existuje více než jeden vztah mezi zdrojové a cílové třídy, tento uzel role rozlišuje mezi odkazy, které patří do dvou relací. Proto doporučujeme tuto možnost v tomto případě nenastavujte.|
|Název elementu role|Určuje název elementu XML, který je odvozený od zdrojové role. Výchozí hodnota je název vlastnosti role.|
|Použijte úplný formát|Při hodnotě true se každý target element nebo moniker je uzavřený v uzlu XML představující vztah. Měla by být nastavena na hodnotu true, pokud tento vztah obsahuje vlastnosti vlastní domény.|

## <a name="see-also"></a>Viz také

- [Navigace v modelu a aktualizace modelu v kódu programu](../modeling/navigating-and-updating-a-model-in-program-code.md)
- [Vytváření kódu z jazyka specifického pro doménu](../modeling/generating-code-from-a-domain-specific-language.md)