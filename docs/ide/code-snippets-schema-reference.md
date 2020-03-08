---
title: Referenční informace ke schématu fragmentů kódu
ms.date: 02/25/2019
ms.topic: reference
helpviewer_keywords:
- schema reference [Visual Studio]
- snippets [Visual Studio], schema reference
- code snippets [Visual Studio], schema reference
- IntelliSense Code Snippets, XML Schema
ms.assetid: 58a60621-725f-4763-93b7-62ea5424ef88
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 22f84fbe5188e74acbf24256444ad11dd9c64347
ms.sourcegitcommit: 3154387056160bf4c36ac8717a7fdc0cd9faf3f9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2020
ms.locfileid: "78410134"
---
# <a name="code-snippets-schema-reference"></a>Referenční informace ke schématu fragmentů kódu

Fragmenty kódu technologie IntelliSense jsou předem vytvořené části kódu, které jsou připravené k vložení do vaší aplikace pomocí sady Visual Studio. Svou produktivitu můžete zvýšit tak, že vytvoříte fragmenty kódu, které snižují množství času stráveného zadáváním opakujícího se kódu nebo hledáním ukázek. Pomocí schématu XML fragmentu kódu technologie IntelliSense můžete vytvořit vlastní fragmenty kódu a přidat je do fragmentů kódu, které již aplikace Visual Studio obsahuje.

## <a name="assembly-element"></a>Element Assembly

Určuje název sestavení, na které se odkazuje fragment kódu.

Textová hodnota prvku **sestavení** je popisný textový název sestavení, například `System.dll`, nebo jeho silný název, například `System,Version=1.0.0.1,Culture=neutral,PublicKeyToken=9b35aa323c18d4fb1`.

```xml
<Assembly>
    AssemblyName
</Assembly>
```

|Nadřazený element|Popis|
| - |-----------------|
|[Element reference](../ide/code-snippets-schema-reference.md#reference-element)|Obsahuje informace o odkazech na sestavení vyžadovaných fragmentem kódu.|

Je vyžadována textová hodnota. Tento text určuje sestavení, na které se odkazuje fragment kódu.

## <a name="author-element"></a>Element Author

Určuje jméno autora fragmentu kódu. **Správce fragmentů kódu** zobrazí název uložený v prvku `Author` fragmentu kódu.

```xml
<Author>
   Code Snippet Author
</Author>
```

|Nadřazený element|Popis|
| - |-----------------|
|[Element Header](../ide/code-snippets-schema-reference.md#header-element)|Obsahuje obecné informace o fragmentu kódu.|

Je vyžadována textová hodnota. Tento text určuje autora fragmentu kódu.

## <a name="code-element"></a>Element kódu

Poskytuje kontejner pro krátké bloky kódu.

### <a name="keywords"></a>Klíčová slova

K dispozici jsou dvě vyhrazená slova pro použití v textu prvku `Code`: `$end$` a `$selected$`. `$end$` označuje umístění, kam se má umístit kurzor po vložení fragmentu kódu. `$selected$` představuje text vybraný v dokumentu, který má být vložen do fragmentu při jeho vyvolání. Například s ohledem na fragment kódu, který obsahuje:

```
$selected$ is a great color.
```

Pokud je vybráno slovo "Blue", když uživatel vyvolá šablonu, výsledek je:

```
Blue is a great color.
```

Ve fragmentu kódu nesmíte použít buď `$end$`, nebo `$selected$` více než jednou. V takovém případě je rozpoznána pouze druhá instance. Daný fragment obsahuje:

```
$selected$ is a great color. I love $selected$.
```

Pokud je vybráno slovo "Blue", výsledek je:

```
 is a great color. I love Blue.
```

Počáteční místo se zobrazí, protože je mezi `$selected$` a `is`mezera.

Všechna ostatní klíčová slova `$` jsou dynamicky definována v rámci značek `<Literal>` a `<Object>`.

Následuje struktura prvku kódu:

```xml
<Code Language="Language"
    Kind="method body/method decl/type decl/page/file/any"
    Delimiter="Delimiter">
    Code to insert
</Code>
```

Je vyžadována textová hodnota. Tento text Určuje kód spolu s literály a objekty, které lze použít, když je tento fragment kódu vložen do souboru kódu.

### <a name="attributes"></a>Atributy

Pro element kódu jsou k dispozici tři atributy:

- **Jazyk** - _požadovaný_ atribut, který určuje jazyk fragmentu kódu. Hodnota může být jedna z následujících:

   |Hodnota|Popis|
   |-----|-----------|
   |`VB`|Identifikuje fragment kódu jazyka Visual Basic.|
   |`CSharp`|Identifikuje fragment kódu jazyka C#.|
   |`CPP`|Identifikuje fragment kódu jazyka C++.|
   |`XML`|Identifikuje fragment kódu jazyka XML.|
   |`JavaScript`|Identifikuje fragment kódu jazyka JavaScript.|
   |`TypeScript`|Identifikuje fragment kódu TypeScript.|
   |`SQL`|Identifikuje fragment kódu jazyka SQL.|
   |`HTML`|Identifikuje fragment kódu jazyka HTML.|

- **Druh** - _nepovinný_ atribut, který určuje druh kódu, který fragment obsahuje. Hodnota může být jedna z následujících:

   |Hodnota|Popis|
   |-----|-----------|
   |`method body`|Určuje, že fragment kódu je tělo metody, a proto musí být vložen dovnitř deklarace metody.|
   |`method decl`|Určuje, že fragment kódu je metoda, a proto musí být vložen dovnitř třídy nebo modulu.|
   |`type decl`|Určuje, že fragment kódu je typ, a proto musí být vložen dovnitř třídy, modulu nebo oboru názvů.|
   |`file`|Určuje, že fragment kódu je celý soubor kódu. Tyto fragmenty kódu lze vložit samotné do souboru kódu nebo do oboru názvů.|
   |`any`|Určuje, že fragment kódu lze vložit kamkoli. Tato značka se používá pro fragmenty kódu, které jsou nezávislé na kontextu, například pro komentáře.|

- **Oddělovač** - _nepovinný_ atribut, který určuje oddělovač, který se používá k popisu literálů a objektů v kódu. Ve výchozím nastavení je oddělovač `$`.

### <a name="parent-element"></a>Nadřazený element

|Nadřazený element|Popis|
| - |-----------------|
|[Element fragmentu](../ide/code-snippets-schema-reference.md#snippet-element)|Obsahuje odkazy, direktivy import, deklarace a kód fragmentu kódu.|

## <a name="codesnippet-element"></a>Element CodeSnippet

Umožňuje zadat záhlaví a jeden nebo více fragmentů kódu technologie IntelliSense, které lze vložit do souborů kódu sady Visual Studio.

```xml
<CodeSnippet Format="x.x.x">
    <Header>... </Header>
    <Snippet>... </Snippet>
</CodeSnippet>
```

|Atribut|Popis|
|---------------|-----------------|
|`Format`|Požadovaný atribut. Určuje verzi schématu fragmentu kódu. Atribut Format musí být řetězec, který používá syntaxi x.x.x, kde každé písmeno „x“ představuje číselnou hodnotu čísla verze. Visual Studio bude ignorovat fragmenty kódu s `Format` atributy, které nerozumí.|

|Podřízený element|Popis|
|-------------------|-----------------|
|[Element Header](../ide/code-snippets-schema-reference.md#header-element)|Požadovaný element. Obsahuje obecné informace o fragmentu kódu. Ve fragmentu kódu musí být přesně jeden `Header` element.|
|[Element fragmentu](../ide/code-snippets-schema-reference.md#snippet-element)|Požadovaný element. Obsahuje kód, který bude vložen sadou Visual Studio. Ve fragmentu kódu musí být přesně jeden `Snippet` element.|

|Nadřazený element|Popis|
| - |-----------------|
|[Element CodeSnippets](../ide/code-snippets-schema-reference.md#codesnippets-element)|Kořenový element schématu XML fragmentu kódu|

## <a name="codesnippets-element"></a>Element CodeSnippets

Seskupuje elementy [codesnippet](../ide/code-snippets-schema-reference.md#codesnippet-element) . Element `CodeSnippets` je kořenovým prvkem schématu XML fragmentu kódu.

```xml
<CodeSnippets>
    <CodeSnippet>... </CodeSnippet>
</CodeSnippets>
```

|Podřízený element|Popis|
|-------------------|-----------------|
|[Element CodeSnippet](../ide/code-snippets-schema-reference.md#codesnippet-element)|Volitelný element. Nadřazený element pro všechna data fragmentu kódu. V elementu `CodeSnippets` může být nula nebo více `CodeSnippet` prvků.|

## <a name="declarations-element"></a>Element Declarations

Určuje literály a objekty tvořící části fragmentu kódu, které lze upravovat.

```xml
<Declarations>
    <Literal>... </Literal>
    <Object>... </Object>
</Declarations>
```

|Podřízený element|Popis|
|-------------------|-----------------|
|[Element Literal](../ide/code-snippets-schema-reference.md#literal-element)|Volitelný element. Definuje literály fragmentu kódu, které lze upravovat. V elementu `Declarations` může být nula nebo více `Literal` prvků.|
|[Element Object](../ide/code-snippets-schema-reference.md#object-element)|Volitelný element. Definuje objekty fragmentu kódu, které lze upravovat. V elementu `Declarations` může být nula nebo více `Object` prvků.|

|Nadřazený element|Popis|
| - |-----------------|
|[Element fragmentu](../ide/code-snippets-schema-reference.md#snippet-element)|Obsahuje odkazy, direktivy import, deklarace a kód fragmentu kódu.|

## <a name="default-element"></a>Výchozí element

Určuje výchozí hodnotu literálu nebo objektu pro fragment kódu technologie IntelliSense.

```xml
<Default>
    Default value
</Default>
```

|Nadřazený element|Popis|
| - |-----------------|
|[Element Literal](../ide/code-snippets-schema-reference.md#literal-element)|Definuje pole literálu fragmentu kódu, která lze upravovat.|
|[Element Object](../ide/code-snippets-schema-reference.md#object-element)|Definuje pole objektu fragment kódu, která lze upravovat.|

Je vyžadována textová hodnota. Tento text určuje výchozí hodnotu literálu nebo objektu, pomocí níž budou naplněna pole fragmentu kódu, která lze upravovat.

## <a name="description-element"></a>Description – element

Určuje popisné informace o obsahu fragmentu kódu technologie IntelliSense.

```xml
<Description>
    Code Snippet Description
</Description>
```

|Nadřazený element|Popis|
| - |-----------------|
|[Element Header](../ide/code-snippets-schema-reference.md#header-element)|Obsahuje obecné informace o fragmentu kódu.|

Je vyžadována textová hodnota. Tento text popisuje fragment kódu.

## <a name="function-element"></a>Element Function

Určuje funkci, která se má provést, když literál nebo objekt získá fokus v sadě Visual Studio.

> [!NOTE]
> Element `Function` je podporován pouze ve C# fragmentech kódu.

```xml
<Function>
    FunctionName
</Function>
```

|Nadřazený element|Popis|
| - |-----------------|
|[Element Literal](../ide/code-snippets-schema-reference.md#literal-element)|Definuje pole literálu fragmentu kódu, která lze upravovat.|
|[Element Object](../ide/code-snippets-schema-reference.md#object-element)|Definuje pole objektu fragment kódu, která lze upravovat.|

Je vyžadována textová hodnota. Tento text určuje funkci, která se má provést, když pole literálu nebo objektu získá fokus v sadě Visual Studio.

## <a name="header-element"></a>Element Header

Určuje obecné informace o fragmentu kódu technologie IntelliSense.

```xml
<Header>
    <Title>... </Title>
    <Author>... </Author>
    <Description>... </Description>
    <HelpUrl>... </HelpUrl>
    <SnippetTypes>... </SnippetTypes>
    <Keywords>... </Keywords>
    <Shortcut>... </Shortcut>
</Header>
```

|Podřízený element|Popis|
|-------------------|-----------------|
|[Element Author](../ide/code-snippets-schema-reference.md#author-element)|Volitelný element. Jméno osoby nebo společnosti, která fragment kódu vytvořila. V elementu `Header` může být nula nebo jeden `Author` elementů.|
|[Description – element](../ide/code-snippets-schema-reference.md#description-element)|Volitelný element. Popis fragmentu kódu. V elementu `Header` může být nula nebo jeden `Description` elementů.|
|[Element HelpUrl](../ide/code-snippets-schema-reference.md#helpurl-element)|Volitelný element. Adresa URL s dalšími informacemi o fragmentu kódu. V elementu Header může být nula nebo jeden `HelpURL` elementů. **Poznámka:**  Visual Studio nepoužívá element `HelpUrl`. Tento element je součástí schématu XML fragmentu kódu technologie IntelliSense a jakékoli fragmenty kódu, které tento element obsahují, budou úspěšně ověřeny, ale hodnota elementu nebude nikdy použita.|
|[Keywords – element](../ide/code-snippets-schema-reference.md#keywords-element)|Volitelný element. Skupiny `Keyword` prvky. V elementu `Header` může být nula nebo jeden `Keywords` elementů.|
|[Element zástupce](../ide/code-snippets-schema-reference.md#shortcut-element)|Volitelný element. Určuje textovou zkratku, pomocí níž lze fragment kódu vložit. V elementu `Header` může být nula nebo jeden `Shortcut` elementů.|
|[Element SnippetTypes](../ide/code-snippets-schema-reference.md#snippettypes-element)|Volitelný element. Skupiny `SnippetType` prvky. V elementu `Header` může být nula nebo jeden `SnippetTypes` elementů. Pokud nejsou k dispozici žádné prvky `SnippetTypes`, fragment kódu je vždy platný.|
|[Title – element](../ide/code-snippets-schema-reference.md#title-element)|Požadovaný element. Popisný název fragmentu kódu. V elementu `Header` musí být právě jeden prvek `Title`.|

|Nadřazený element|Popis|
| - |-----------------|
|[Element CodeSnippet](../ide/code-snippets-schema-reference.md#codesnippet-element)|Nadřazený element pro všechna data fragmentu kódu.|

## <a name="helpurl-element"></a>Element HelpUrl

Určujte adresu URL s dalšími informacemi o fragmentu kódu.

> [!NOTE]
> Visual Studio nepoužívá element `HelpUrl`. Tento element je součástí schématu XML fragmentu kódu technologie IntelliSense a jakékoli fragmenty kódu, které tento element obsahují, budou úspěšně ověřeny, ale hodnota elementu nebude nikdy použita.

```xml
<HelpUrl>
    www.microsoft.com
</HelpUrl>
```

|Nadřazený element|Popis|
| - |-----------------|
|[Element Header](../ide/code-snippets-schema-reference.md#header-element)|Obsahuje obecné informace o fragmentu kódu.|

Textová hodnota je volitelná. Tento text určuje adresu URL, na níž naleznete další informace o fragmentu kódu.

## <a name="id-element"></a>Element ID

Určuje jedinečný identifikátor `Literal` nebo `Object` elementu. Žádné dva literály nebo objekty ve stejném fragmentu kódu nemohou mít stejnou textovou hodnotu ve svých `ID` elementech. Literály a objekty nesmí obsahovat element `ID` s hodnotou end. Hodnota `$end$` je vyhrazena a slouží k označení umístění, kam má být umístěn kurzor po vložení fragmentu kódu.

```xml
<ID>
    Unique Identifier
</ID>
```

|Nadřazený element|Popis|
| - |-----------------|
|[Element Literal](../ide/code-snippets-schema-reference.md#literal-element)|Definuje pole literálu fragmentu kódu, která lze upravovat.|
|[Element Object](../ide/code-snippets-schema-reference.md#object-element)|Definuje pole objektu fragment kódu, která lze upravovat.|

Je vyžadována textová hodnota. Tento text určuje jedinečný identifikátor pro objekt nebo literál.

## <a name="import-element"></a>Import – element

Určuje importované obory názvů používané fragmentem kódu technologie IntelliSense.

```xml
<Import>
    <Namespace>... </Namespace>
</Import>
```

|Podřízený element|Popis|
|-------------------|-----------------|
|[Element Namespace](../ide/code-snippets-schema-reference.md#namespace-element)|Požadovaný element. Určuje obor názvů používaný fragmentem kódu. V elementu `Import` musí být právě jeden prvek `Namespace`.|

|Nadřazený element|Popis|
| - |-----------------|
|[Imports – element](../ide/code-snippets-schema-reference.md#imports-element)|Prvek seskupení pro elementy **Import** .|

## <a name="imports-element"></a>Imports – element

Seskupí jednotlivé prvky `Import`.

```xml
<Imports>
    <Import>... </Import>
</Imports>
```

|Podřízený element|Popis|
|-------------------|-----------------|
|[Importovat element](../ide/code-snippets-schema-reference.md#import-element)|Volitelný element. Obsahuje naimportované obory názvů pro fragment kódu. V elementu `Imports` může existovat nula nebo více elementů **importu** .|

|Nadřazený element|Popis|
| - |-----------------|
|[Element fragmentu](../ide/code-snippets-schema-reference.md#snippet-element)|Obsahuje odkazy, direktivy import, deklarace a kód fragmentu kódu.|

## <a name="keyword-element"></a>Element klíčového slova

Určuje vlastní klíčové slovo pro fragment kódu. Klíčová slova fragmentů kódu používá sada Visual Studio a představují standardní způsob pro online poskytovatele obsahu, jak přidávat vlastní klíčová slova pro vyhledávání nebo kategorizaci.

```xml
<Keyword>
    Code Snippet Keyword
</Keyword>
```

|Nadřazený element|Popis|
| - |-----------------|
|[Keywords – element](../ide/code-snippets-schema-reference.md#keywords-element)|Seskupí jednotlivé prvky `Keyword`.|

Je vyžadována textová hodnota. Klíčové slovo fragmentu kódu.

## <a name="keywords-element"></a>Keywords – element

Seskupí jednotlivé prvky `Keyword`. Klíčová slova fragmentů kódu používá sada Visual Studio a představují standardní způsob pro online poskytovatele obsahu, jak přidávat vlastní klíčová slova pro vyhledávání nebo kategorizaci.

```xml
<Keywords>
    <Keyword>... </Keyword>
    <Keyword>... </Keyword>
</Keywords>
```

|Podřízený element|Popis|
|-------------------|-----------------|
|[Element klíčového slova](../ide/code-snippets-schema-reference.md#keyword-element)|Volitelný element. Obsahuje jednotlivá klíčová slova pro fragment kódu. V elementu `Keywords` může být nula nebo více `Keyword` prvků.|

|Nadřazený element|Popis|
| - |-----------------|
|[Element Header](../ide/code-snippets-schema-reference.md#header-element)|Obsahuje obecné informace o fragmentu kódu.|

## <a name="literal-element"></a>Element Literal

Definuje literály fragmentu kódu, které lze upravovat. Element `Literal` slouží k identifikaci náhrady za část kódu, která je zcela obsažena v rámci fragmentu, ale bude pravděpodobně upravena poté, co je vložena do kódu. Jako literály by měly být deklarovány například řetězcové literály, číselné hodnoty a některé názvy proměnných.

Literály a objekty nesmí obsahovat element **ID** s hodnotou Selected nebo end. Hodnota `$selected$` představuje text vybraný v dokumentu, který má být vložen do fragmentu při jeho vyvolání. `$end$` označuje umístění, kam se má umístit kurzor po vložení fragmentu kódu.

```xml
<Literal Editable="true/false">
   <ID>... </ID>
   <ToolTip>... </ToolTip>
   <Default>... </Default>
   <Function>... </Function>
</Literal>
```

|Atribut|Popis|
|---------------|-----------------|
|`Editable`|Volitelný atribut `Boolean`. Určuje, zda lze literál po vložení fragmentu kódu upravit. Výchozí hodnota tohoto atributu je `true`.|

|Podřízený element|Popis|
|-------------------|-----------------|
|[Výchozí element](../ide/code-snippets-schema-reference.md#default-element)|Požadovaný element. Určuje výchozí hodnotu literálu při vložení fragmentu kódu. V elementu `Literal` musí být právě jeden prvek `Default`.|
|[Element Function](../ide/code-snippets-schema-reference.md#function-element)|Volitelný element. Určuje funkci, která se má provést, když literál získá fokus v sadě Visual Studio. V elementu `Literal` může být nula nebo jeden `Function` elementů.|
|[Element ID](../ide/code-snippets-schema-reference.md#id-element)|Požadovaný element. Určuje jedinečný identifikátor literálu. V elementu `Literal` musí být právě jeden prvek `ID`.|
|[Element ToolTip](../ide/code-snippets-schema-reference.md#tooltip-element)|Volitelný element. Popisuje očekávanou hodnotu a použití literálu. V prvku `Literal` může být nula nebo jeden prvek **ToolTip** .|

|Nadřazený element|Popis|
| - |-----------------|
|[Element Declarations](../ide/code-snippets-schema-reference.md#declarations-element)|Obsahuje literály a objekty fragmentu kódu, které lze upravovat.|

## <a name="namespace-element"></a>Element Namespace

Určuje obor názvů, který musí být naimportován, aby bylo možné fragment kódu zkompilovat a spustit. Obor názvů zadaný v prvku `Namespace` je automaticky přidán do direktivy `using` nebo `Imports` příkaz na začátku kódu, pokud ještě neexistuje.

```xml
<Namespace>
    Namespace
</Namespace>
```

|Nadřazený element|Popis|
| - |-----------------|
|[Importovat element](../ide/code-snippets-schema-reference.md#import-element)|Naimportuje zadaný obor názvů.|

Je vyžadována textová hodnota. Tento text určuje obor názvů, o kterém fragment kódu předpokládá, že bude naimportován.

## <a name="object-element"></a>Element Object

Definuje objekty fragmentu kódu, které lze upravovat. Element `Object` slouží k identifikaci položky, která je požadována fragmentem kódu, ale je pravděpodobně definována mimo samotný fragment kódu. Jako objekty by měly být deklarovány například ovládací prvky modelu Windows Forms, ovládací prvky technologie ASP.NET nebo instance typů. Deklarace objektů vyžadují, aby byl zadán typ, který se provádí pomocí elementu `Type`.

```xml
<Object Editable="true/false">
    <ID>... </ID>
    <Type>... </Type>
    <ToolTip>... </ToolTip>
    <Default>... </Default>
    <Function>... </Function>
</Object>
```

|Atribut|Popis|
|---------------|-----------------|
|`Editable`|Volitelný atribut `Boolean`. Určuje, zda lze literál po vložení fragmentu kódu upravit. Výchozí hodnota tohoto atributu je `true`.|

|Podřízený element|Popis|
|-------------------|-----------------|
|[Výchozí element](../ide/code-snippets-schema-reference.md#default-element)|Požadovaný element. Určuje výchozí hodnotu literálu při vložení fragmentu kódu. V elementu `Literal` musí být právě jeden prvek `Default`.|
|[Element Function](../ide/code-snippets-schema-reference.md#function-element)|Volitelný element. Určuje funkci, která se má provést, když literál získá fokus v sadě Visual Studio. V elementu `Literal` může být nula nebo jeden `Function` elementů.|
|[Element ID](../ide/code-snippets-schema-reference.md#id-element)|Požadovaný element. Určuje jedinečný identifikátor literálu. V elementu `Literal` musí být právě jeden prvek `ID`.|
|[Element ToolTip](../ide/code-snippets-schema-reference.md#tooltip-element)|Volitelný element. Popisuje očekávanou hodnotu a použití literálu. V prvku `Literal` může být nula nebo jeden prvek **ToolTip** .|
|[Element Type](../ide/code-snippets-schema-reference.md#type-element)|Požadovaný element. Určuje typ objektu. V elementu `Object` musí být právě jeden prvek `Type`.|

|Nadřazený element|Popis|
| - |-----------------|
|[Element Declarations](../ide/code-snippets-schema-reference.md#declarations-element)|Obsahuje literály a objekty fragmentu kódu, které lze upravovat.|

## <a name="reference-element"></a>Element reference

Určuje informace o odkazech na sestavení vyžadovaných fragmentem kódu.

```xml
<Reference>
    <Assembly>... </Assembly>
    <Url>... </Url>
</Reference>
```

|Podřízený element|Popis|
|-------------------|-----------------|
|[Element Assembly](../ide/code-snippets-schema-reference.md#assembly-element)|Požadovaný element. Obsahuje název sestavení, na které se odkazuje fragment kódu. V elementu `Reference` musí být právě jeden prvek `Assembly`.|
|[Element URL](../ide/code-snippets-schema-reference.md#url-element)|Volitelný element. Obsahuje adresu URL s dalšími informacemi o odkazovaném sestavení. V elementu `Reference` může být nula nebo jeden `Url` elementů.|

|Nadřazený element|Popis|
| - |-----------------|
|[Odkazuje na element](../ide/code-snippets-schema-reference.md#references-element)|Prvek seskupení pro prvky `Reference`.|

## <a name="references-element"></a>Odkazuje na element

Seskupí jednotlivé prvky `Reference`.

```xml
<References>
    <Reference>... </Reference>
</References>
```

|Podřízený element|Popis|
|-------------------|-----------------|
|[Element reference](../ide/code-snippets-schema-reference.md#reference-element)|Volitelný element. Obsahuje informace o odkazech na sestavení pro fragment kódu. V elementu `References` může být nula nebo více `Reference` prvků.|

|Nadřazený element|Popis|
| - |-----------------|
|[Element fragmentu](../ide/code-snippets-schema-reference.md#snippet-element)|Obsahuje odkazy, direktivy import, deklarace a kód fragmentu kódu.|

## <a name="shortcut-element"></a>Element zástupce

Určuje textovou zkratku, pomocí níž lze fragment kódu vložit. Textová hodnota prvku `Shortcut` může obsahovat pouze alfanumerické znaky a podtržítka (_).

> [!CAUTION]
> Podtržítka (_) není v C++ zástupcových zkratkách podporován znaků.

```xml
<Shortcut>
    Shortcut Text
</Shortcut>
```

|Nadřazený element|Popis|
| - |-----------------|
|[Element Header](../ide/code-snippets-schema-reference.md#header-element)|Obsahuje obecné informace o fragmentu kódu.|

Textová hodnota je volitelná. Tento text slouží jako zkratka pro vkládání fragmentů kódu.

## <a name="snippet-element"></a>Element fragmentu

Určuje odkazy, direktivy import, deklarace a kód fragmentu kódu.

```xml
<Snippet>
    <References>... </References>
    <Imports>... </Imports>
    <Declarations>... </Declarations>
    <Code>... </Code>
</Snippet>
```

|Podřízený element|Popis|
|-------------------|-----------------|
|[Element Code](../ide/code-snippets-schema-reference.md#code-element)|Požadovaný element. Určuje kód, který chcete vložit do souboru dokumentace. V elementu `Snippet` musí být právě jeden prvek `Code`.|
|[Element Declarations](../ide/code-snippets-schema-reference.md#declarations-element)|Volitelný element. Určuje literály a objekty tvořící části fragmentu kódu, které lze upravovat. V elementu `Snippet` může být nula nebo jeden `Declarations` elementů.|
|[Imports – element](../ide/code-snippets-schema-reference.md#imports-element)|Volitelný element. Seskupí jednotlivé prvky `Import`. V elementu `Snippet` může být nula nebo jeden `Imports` elementů.|
|[Odkazuje na element](../ide/code-snippets-schema-reference.md#references-element)|Volitelný element. Seskupí jednotlivé prvky `Reference`. V elementu `Snippet` může být nula nebo jeden `References` elementů.|

|Nadřazený element|Popis|
| - |-----------------|
|[Element CodeSnippet](../ide/code-snippets-schema-reference.md#codesnippet-element)|Umožňuje zadat záhlaví a jeden nebo více fragmentů kódu technologie IntelliSense, které lze vložit do souborů kódu sady Visual Studio.|

## <a name="snippettype-element"></a>Element SnippetType

Určuje, jak sada Visual Studio vloží fragment kódu.

```xml
<SnippetType>
    SurroundsWith/Expansion
</SnippetType>
```

|Nadřazený element|Popis|
| - |-----------------|
|[Element SnippetTypes](../ide/code-snippets-schema-reference.md#snippettypes-element)|Skupiny `SnippetType` prvky.|

Textová hodnota musí být jedna z následujících hodnot:

- `SurroundsWith`: umožňuje umístit fragment kódu kolem vybraného kusu kódu.

- `Expansion`: umožňuje vložení fragmentu kódu na pozici kurzoru.

- `Refactoring`: Určuje, zda se fragment kódu používá během C# refaktoringu. `Refactoring` nelze použít ve vlastních fragmentech kódu.

## <a name="snippettypes-element"></a>Element SnippetTypes

Seskupí jednotlivé prvky `SnippetType`. Pokud `SnippetTypes` prvek není k dispozici, může být fragment kódu vložen kamkoli do kódu.

```xml
<SnippetTypes>
    <SnippetType>... </SnippetType>
    <SnippetType>... </SnippetType>
</SnippetTypes>
```

|Podřízený element|Popis|
|-------------------|-----------------|
|[Element SnippetType](../ide/code-snippets-schema-reference.md#snippettype-element)|Volitelný element. Určuje, jak sada Visual Studio vloží fragment kódu do kódu. V elementu `SnippetTypes` může být nula nebo více `SnippetType` prvků.|

|Nadřazený element|Popis|
| - |-----------------|
|[Element Header](../ide/code-snippets-schema-reference.md#header-element)|Určuje obecné informace o fragmentu kódu.|

## <a name="title-element"></a>Title – element

Určuje název fragmentu kódu. Název uložený v prvku `Title` fragmentu kódu se zobrazí ve **výběru fragmentu kódu** a v popisu fragmentu kódu ve **Správci fragmentů kódu**.

```xml
<Title>
    Code Snippet Title
</Title>
```

|Nadřazený element|Popis|
| - |-----------------|
|[Element Header](../ide/code-snippets-schema-reference.md#header-element)|Určuje obecné informace o fragmentu kódu.|

Je vyžadována textová hodnota. Tento text určuje název fragmentu kódu.

## <a name="tooltip-element"></a>Element ToolTip

Popisuje očekávanou hodnotu a použití literálu nebo objektu ve fragmentu kódu. Sada Visual Studio tyto informace zobrazí v popisku při vložení fragmentu kódu do projektu. Text popisku se zobrazí po vložení fragmentu kódu po umístění ukazatele myši na literál nebo objekt.

```xml
<ToolTip>
    ToolTip description
</ToolTip>
```

|Nadřazený element|Popis|
| - |-----------------|
|[Element Literal](../ide/code-snippets-schema-reference.md#literal-element)|Definuje pole literálu fragmentu kódu, která lze upravovat.|
|[Element Object](../ide/code-snippets-schema-reference.md#object-element)|Definuje pole objektu fragment kódu, která lze upravovat.|

Je vyžadována textová hodnota. Tento text určuje popisek přidružený k objektu nebo literálu ve fragmentu kódu.

## <a name="type-element"></a>Element Type

Určuje typ objektu. Element `Object` slouží k identifikaci položky, která je požadována fragmentem kódu, ale je pravděpodobně definována mimo samotný fragment kódu. Jako objekty by měly být deklarovány například ovládací prvky modelu Windows Forms, ovládací prvky technologie ASP.NET nebo instance typů. Deklarace objektů vyžadují, aby byl zadán typ, který se provádí pomocí elementu `Type`.

```xml
<Type>
    Type
</Type>
```

|Nadřazený element|Popis|
| - |-----------------|
|[Element Object](../ide/code-snippets-schema-reference.md#object-element)|Definuje pole objektu fragment kódu, která lze upravovat.|

Je vyžadována textová hodnota. Tento text určuje typ objektu. Příklad:

```xml
<Type>System.Data.SqlClient.SqlConnection</Type>
```

## <a name="url-element"></a>Element URL

Určuje adresu URL s dalšími informacemi o odkazovaném sestavení.

> [!NOTE]
> Element `Url` je podporován pouze pro projekty Visual Basic.

```xml
<Url>
    www.microsoft.com
</Url>
```

|Nadřazený element|Popis|
| - |-----------------|
|[Element reference](../ide/code-snippets-schema-reference.md#reference-element)|Určuje odkazy na sestavení vyžadované fragmentem kódu.|

Je vyžadována textová hodnota. Tento text určuje adresu URL s dalšími informacemi o odkazovaném sestavení. Tato adresa URL se zobrazí, pokud odkaz nelze přidat do projektu.

## <a name="see-also"></a>Viz také

- [Fragmenty kódu](../ide/code-snippets.md)
- [Návod: Vytvoření fragmentu kódu](../ide/walkthrough-creating-a-code-snippet.md)
