---
title: Referenční informace ke schématu fragmentů kódu
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- schema reference [Visual Studio]
- snippets [Visual Studio], schema reference
- code snippets [Visual Studio], schema reference
- IntelliSense Code Snippets, XML Schema
ms.assetid: 58a60621-725f-4763-93b7-62ea5424ef88
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8a39040bb76181a7a36e9d8f7b19aa0b4390c400
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49932439"
---
# <a name="code-snippets-schema-reference"></a>Referenční informace ke schématu fragmentů kódu

Fragmenty kódu technologie IntelliSense jsou předem vytvořené části kódu, které jsou připraveny k vložení do vaší aplikace pomocí sady Visual Studio. Svou produktivitu můžete zvýšit tak, že vytvoříte fragmenty kódu, které snižují množství času stráveného zadáváním opakujícího se kódu nebo hledáním ukázek. Schématu XML fragmentu kódu technologie IntelliSense můžete vytvořit své vlastní fragmenty kódu a přidat je k fragmentům kódu, které sada Visual Studio již obsahuje.

## <a name="assembly-element"></a>Assembly – element

Určuje název sestavení, na které se odkazuje fragment kódu.

Textová hodnota elementu **sestavení** element je buď popisný textový název sestavení, jako například `System.dll`, nebo jeho silný název, například `System,Version=1.0.0.1,Culture=neutral,PublicKeyToken=9b35aa323c18d4fb1`.

```xml
<Assembly>
    AssemblyName
</Assembly>
```

|Nadřazený element|Popis|
| - |-----------------|
|[Reference – element](../ide/code-snippets-schema-reference.md#reference-element)|Obsahuje informace o odkazech na sestavení vyžadovaných fragmentem kódu.|

 Je vyžadována textová hodnota. Tento text určuje sestavení, na které se odkazuje fragment kódu.

## <a name="author-element"></a>Element Autor

Určuje jméno autora fragmentu kódu. **Správce fragmentů kódů** zobrazí jméno uložené v `Author` element fragmentu kódu.

```xml
<Author>
   Code Snippet Author
</Author>
```

|Nadřazený element|Popis|
| - |-----------------|
|[Header element](../ide/code-snippets-schema-reference.md#header-element)|Obsahuje obecné informace o fragmentu kódu.|

 Je vyžadována textová hodnota. Tento text určuje autora fragmentu kódu.

## <a name="code-element"></a>Element kódu

Poskytuje kontejner pro krátké bloky kódu.

### <a name="keywords"></a>Klíčová slova

Dvě vyhrazená slova jsou k dispozici pro použití v textu `Code` element: `$end$` a `$selected$`. `$end$` označuje umístění, umístěte kurzor po vložení fragmentu kódu. `$selected$` představuje text vybraný v dokumentu, který má být do fragmentu kódu vložen při jeho vyvolání. Mějme například fragment kódu, který obsahuje:

```
$selected$ is a great color.
```

Pokud je vybráno slovo "Blue", když uživatel vyvolá šablonu, výsledek je:

```
Blue is a great color.
```

Nesmíte používat buď `$end$` nebo `$selected$` více než jednou ve fragmentu kódu. Pokud tak učiníte, je rozpoznáno pouze druhou instanci. Zadaný fragment kódu, který obsahuje:

```
$selected$ is a great color. I love $selected$.
```

Pokud je vybráno slovo "Blue", výsledek je:

```
 is a great color. I love Blue.
```

Počáteční místa se zobrazí, protože je mezera mezi `$selected$` a `is`.

Všechny ostatní `$` klíčová slova jsou definována dynamicky ve `<Literal>` a `<Object>` značky.

Toto je struktura prvek kódu:

```xml
<Code Language="Language"
    Kind="method body/method decl/type decl/page/file/any"
    Delimiter="Delimiter">
    Code to insert
</Code>
```

Je vyžadována textová hodnota. Tento text určuje kód spolu s literály a objekty, které můžete použít při vložení tohoto fragmentu kódu do souboru kódu.

### <a name="attributes"></a>Atributy

Tři atributy nejsou k dispozici pro prvek kódu:

- **Jazyk** - _vyžaduje_ atribut, který určuje jazyk fragmentu kódu. Hodnota může být jeden z následujících akcí:

   |Hodnota|Popis|
   |-----|-----------|
   |`VB`|Identifikuje fragment kódu jazyka Visual Basic.|
   |`CSharp`|Identifikuje fragment kódu jazyka C#.|
   |`CPP`|Identifikuje fragment kódu jazyka C++.|
   |`XML`|Identifikuje fragment kódu jazyka XML.|
   |`JavaScript`|Identifikuje fragment kódu jazyka JavaScript.|
   |`SQL`|Identifikuje fragment kódu jazyka SQL.|
   |`HTML`|Identifikuje fragment kódu jazyka HTML.|

- **Druh** - _volitelné_ atribut, který určuje druh kódu, který obsahuje fragment kódu a umístění, ve kterém musí být fragment kódu vložen pro fragment kódu pro kompilaci. Hodnota může být jeden z následujících akcí:

   |Hodnota|Popis|
   |-----|-----------|
   |`method body`|Určuje, že fragment kódu je tělo metody, a proto musí být vložen dovnitř deklarace metody.|
   |`method decl`|Určuje, že fragment kódu je metoda, a proto musí být vložen dovnitř třídy nebo modulu.|
   |`type decl`|Určuje, že fragment kódu je typ, a proto musí být vložen dovnitř třídy, modulu nebo oboru názvů.|
   |`file`|Určuje, že fragment kódu je celý soubor kódu. Tyto fragmenty kódu lze vložit samotné do souboru kódu nebo do oboru názvů.|
   |`any`|Určuje, že fragment kódu lze vložit kamkoli. Tato značka se používá pro fragmenty kódu, které jsou nezávislé na kontextu, například pro komentáře.|

- **Oddělovač** - _volitelné_ atribut, který určuje oddělovač použitý k označení literálů a objektů v kódu. Ve výchozím nastavení, je oddělovač `$`.

### <a name="parent-element"></a>Nadřazený element

|Nadřazený element|Popis|
| - |-----------------|
|[Snippet element](../ide/code-snippets-schema-reference.md#snippet-element)|Obsahuje odkazy, direktivy import, deklarace a kód fragmentu kódu.|

## <a name="codesnippet-element"></a>CodeSnippet element

Umožňuje zadat záhlaví a jeden nebo více fragmentů kódu technologie IntelliSense, které lze vložit do souborů kódu sady Visual Studio.

```xml
<CodeSnippet Format="x.x.x">
    <Header>... </Header>
    <Snippet>... </Snippet>
</CodeSnippet>
```

|Atribut|Popis|
|---------------|-----------------|
|`Format`|Požadovaný atribut. Určuje verzi schématu fragmentu kódu. Atribut Format musí být řetězec, který používá syntaxi x.x.x, kde každé písmeno „x“ představuje číselnou hodnotu čísla verze. Visual Studio bude ignorovat fragmenty kódu s `Format` atributy, které není srozumitelný.|

|Podřízený element.|Popis|
|-------------------|-----------------|
|[Header element](../ide/code-snippets-schema-reference.md#header-element)|Požadovaný element. Obsahuje obecné informace o fragmentu kódu. Musí obsahovat přesně jeden `Header` element ve fragmentu kódu.|
|[Snippet element](../ide/code-snippets-schema-reference.md#snippet-element)|Požadovaný element. Obsahuje kód, který bude vložen sadou Visual Studio. Musí obsahovat přesně jeden `Snippet` element ve fragmentu kódu.|

|Nadřazený element|Popis|
| - |-----------------|
|[Codesnippets – element](../ide/code-snippets-schema-reference.md#codesnippets-element)|Kořenový element schématu XML fragmentu kódu|

## <a name="codesnippets-element"></a>Codesnippets – element

Skupiny [CodeSnippet](../ide/code-snippets-schema-reference.md#codesnippet-element) elementy. `CodeSnippets` Prvek je kořenovým prvkem schématu XML fragmentu kódu.

```xml
<CodeSnippets>
    <CodeSnippet>... </CodeSnippet>
</CodeSnippets>
```

|Podřízený element.|Popis|
|-------------------|-----------------|
|[CodeSnippet element](../ide/code-snippets-schema-reference.md#codesnippet-element)|Volitelný element. Nadřazený element pro všechna data fragmentu kódu. Může být nula nebo více `CodeSnippet` prvky `CodeSnippets` elementu.|

## <a name="declarations-element"></a>Declarations element

Určuje literály a objekty tvořící části fragmentu kódu, které lze upravovat.

```xml
<Declarations>
    <Literal>... </Literal>
    <Object>... </Object>
</Declarations>
```

|Podřízený element.|Popis|
|-------------------|-----------------|
|[Literal element](../ide/code-snippets-schema-reference.md#literal-element)|Volitelný element. Definuje literály fragmentu kódu, které lze upravovat. Může být nula nebo více `Literal` prvky `Declarations` elementu.|
|[Object element](../ide/code-snippets-schema-reference.md#object-element)|Volitelný element. Definuje objekty fragmentu kódu, které lze upravovat. Může být nula nebo více `Object` prvky `Declarations` elementu.|

|Nadřazený element|Popis|
| - |-----------------|
|[Snippet element](../ide/code-snippets-schema-reference.md#snippet-element)|Obsahuje odkazy, direktivy import, deklarace a kód fragmentu kódu.|

## <a name="default-element"></a>Default element

Určuje výchozí hodnotu literálu nebo objektu pro fragment kódu technologie IntelliSense.

```xml
<Default>
    Default value
</Default>
```

|Nadřazený element|Popis|
| - |-----------------|
|[Literal element](../ide/code-snippets-schema-reference.md#literal-element)|Definuje pole literálu fragmentu kódu, která lze upravovat.|
|[Object element](../ide/code-snippets-schema-reference.md#object-element)|Definuje pole objektu fragment kódu, která lze upravovat.|

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
|[Header element](../ide/code-snippets-schema-reference.md#header-element)|Obsahuje obecné informace o fragmentu kódu.|

 Je vyžadována textová hodnota. Tento text popisuje fragment kódu.

## <a name="function-element"></a>Function element

Určuje funkci, která se má provést, když literál nebo objekt získá fokus v sadě Visual Studio.

> [!NOTE]
> `Function` Element je podporován pouze ve fragmentech kódu jazyka C#.

```xml
<Function>
    FunctionName
</Function>
```

|Nadřazený element|Popis|
| - |-----------------|
|[Literal element](../ide/code-snippets-schema-reference.md#literal-element)|Definuje pole literálu fragmentu kódu, která lze upravovat.|
|[Object element](../ide/code-snippets-schema-reference.md#object-element)|Definuje pole objektu fragment kódu, která lze upravovat.|

 Je vyžadována textová hodnota. Tento text určuje funkci, která se má provést, když pole literálu nebo objektu získá fokus v sadě Visual Studio.

## <a name="header-element"></a>Header element

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

|Podřízený element.|Popis|
|-------------------|-----------------|
|[Element Autor](../ide/code-snippets-schema-reference.md#author-element)|Volitelný element. Jméno osoby nebo společnosti, která fragment kódu vytvořila. Může být žádný nebo jeden `Author` prvky `Header` elementu.|
|[Description – element](../ide/code-snippets-schema-reference.md#description-element)|Volitelný element. Popis fragmentu kódu. Může být žádný nebo jeden `Description` prvky `Header` elementu.|
|[Helpurl – element](../ide/code-snippets-schema-reference.md#helpurl-element)|Volitelný element. Adresa URL s dalšími informacemi o fragmentu kódu. Může být žádný nebo jeden `HelpURL` prvků v záhlaví elementu. **Poznámka:** nepoužívá sady Visual Studio `HelpUrl` elementu. Tento element je součástí schématu XML fragmentu kódu technologie IntelliSense a jakékoli fragmenty kódu, které tento element obsahují, budou úspěšně ověřeny, ale hodnota elementu nebude nikdy použita.|
|[Element Keyword](../ide/code-snippets-schema-reference.md#keywords-element)|Volitelný element. Skupiny `Keyword` elementy. Může být žádný nebo jeden `Keywords` prvky `Header` elementu.|
|[Shortcut element](../ide/code-snippets-schema-reference.md#shortcut-element)|Volitelný element. Určuje textovou zkratku, pomocí níž lze fragment kódu vložit. Může být žádný nebo jeden `Shortcut` prvky `Header` elementu.|
|[Snippettypes – element](../ide/code-snippets-schema-reference.md#snippettypes-element)|Volitelný element. Skupiny `SnippetType` elementy. Může být žádný nebo jeden `SnippetTypes` prvky `Header` elementu. Pokud neexistují žádné `SnippetTypes` prvky, fragment kódu je vždy platný.|
|[Title element](../ide/code-snippets-schema-reference.md#title-element)|Požadovaný element. Popisný název fragmentu kódu. Musí obsahovat přesně jeden `Title` prvek `Header` elementu.|

|Nadřazený element|Popis|
| - |-----------------|
|[CodeSnippet element](../ide/code-snippets-schema-reference.md#codesnippet-element)|Nadřazený element pro všechna data fragmentu kódu.|

## <a name="helpurl-element"></a>Helpurl – element

Určujte adresu URL s dalšími informacemi o fragmentu kódu.

> [!NOTE]
> Visual Studio nebude používat `HelpUrl` elementu. Tento element je součástí schématu XML fragmentu kódu technologie IntelliSense a jakékoli fragmenty kódu, které tento element obsahují, budou úspěšně ověřeny, ale hodnota elementu nebude nikdy použita.

```xml
<HelpUrl>
    www.microsoft.com
</HelpUrl>
```

|Nadřazený element|Popis|
| - |-----------------|
|[Header element](../ide/code-snippets-schema-reference.md#header-element)|Obsahuje obecné informace o fragmentu kódu.|

Textová hodnota je volitelná. Tento text určuje adresu URL, na níž naleznete další informace o fragmentu kódu.

## <a name="id-element"></a>Element ID.

Určuje jedinečný identifikátor `Literal` nebo `Object` elementu. Žádné dva literály nebo objekty ve stejném fragmentu kódu mají stejnou textovou hodnotu jejich `ID` elementy. Literály a objekty nesmí obsahovat `ID` element s hodnotou elementu end. Hodnota `$end$` je vyhrazena a používá se k označení umístění, umístěte kurzor po vložení fragmentu kódu.

```xml
<ID>
    Unique Identifier
</ID>
```

|Nadřazený element|Popis|
| - |-----------------|
|[Literal element](../ide/code-snippets-schema-reference.md#literal-element)|Definuje pole literálu fragmentu kódu, která lze upravovat.|
|[Object element](../ide/code-snippets-schema-reference.md#object-element)|Definuje pole objektu fragment kódu, která lze upravovat.|

Je vyžadována textová hodnota. Tento text určuje jedinečný identifikátor pro objekt nebo literál.

## <a name="import-element"></a>Import – element

Určuje naimportované obory názvů používané fragmentem kódu technologie IntelliSense.

> [!NOTE]
> `Import` Element je podporována pouze pro projekty jazyka Visual Basic.

```xml
<Import>
    <Namespace>... </Namespace>
</Import>
```

|Podřízený element.|Popis|
|-------------------|-----------------|
|[Namespace element](../ide/code-snippets-schema-reference.md#namespace-element)|Požadovaný element. Určuje obor názvů používaný fragmentem kódu. Musí obsahovat přesně jeden `Namespace` prvek `Import` elementu.|

|Nadřazený element|Popis|
| - |-----------------|
|[Imports element](../ide/code-snippets-schema-reference.md#imports-element)|Element pro seskupení **Import** elementy.|

## <a name="imports-element"></a>Imports element

Seskupuje jednotlivé `Import` elementy.

> [!NOTE]
> `Imports` Element je podporována pouze pro projekty jazyka Visual Basic.

```xml
<Imports>
    <Import>... </Import>
</Imports>
```

|Podřízený element.|Popis|
|-------------------|-----------------|
|[Import – element](../ide/code-snippets-schema-reference.md#import-element)|Volitelný element. Obsahuje naimportované obory názvů pro fragment kódu. Může být nula nebo více **Import** prvky `Imports` elementu.|

|Nadřazený element|Popis|
| - |-----------------|
|[Snippet element](../ide/code-snippets-schema-reference.md#snippet-element)|Obsahuje odkazy, direktivy import, deklarace a kód fragmentu kódu.|

## <a name="keyword-element"></a>Keyword element

Určuje vlastní klíčové slovo pro fragment kódu. Klíčová slova fragmentů kódu používá sada Visual Studio a představují standardní způsob pro online poskytovatele obsahu, jak přidávat vlastní klíčová slova pro vyhledávání nebo kategorizaci.

```xml
<Keyword>
    Code Snippet Keyword
</Keyword>
```

|Nadřazený element|Popis|
| - |-----------------|
|[Element Keyword](../ide/code-snippets-schema-reference.md#keywords-element)|Seskupuje jednotlivé `Keyword` elementy.|

Je vyžadována textová hodnota. Klíčové slovo fragmentu kódu.

## <a name="keywords-element"></a>Element Keyword

Seskupuje jednotlivé `Keyword` elementy. Klíčová slova fragmentů kódu používá sada Visual Studio a představují standardní způsob pro online poskytovatele obsahu, jak přidávat vlastní klíčová slova pro vyhledávání nebo kategorizaci.

```xml
<Keywords>
    <Keyword>... </Keyword>
    <Keyword>... </Keyword>
</Keywords>
```

|Podřízený element.|Popis|
|-------------------|-----------------|
|[Keyword element](../ide/code-snippets-schema-reference.md#keyword-element)|Volitelný element. Obsahuje jednotlivá klíčová slova pro fragment kódu. Může být nula nebo více `Keyword` prvky `Keywords` elementu.|

|Nadřazený element|Popis|
| - |-----------------|
|[Header element](../ide/code-snippets-schema-reference.md#header-element)|Obsahuje obecné informace o fragmentu kódu.|

## <a name="literal-element"></a>Literal element

Definuje literály fragmentu kódu, které lze upravovat. `Literal` Element slouží k identifikaci můžou nahradit aktuální soubor pro část kódu, který je zcela obsažen ve fragmentu kódu, ale pravděpodobně přizpůsobit po vložení do kódu. Jako literály by měly být deklarovány například řetězcové literály, číselné hodnoty a některé názvy proměnných.

Literály a objekty nesmí obsahovat **ID** element s hodnotou selected nebo end. Hodnota `$selected$` představuje text vybraný v dokumentu, který má být do fragmentu kódu vložen při jeho vyvolání. `$end$` označuje umístění, umístěte kurzor po vložení fragmentu kódu.

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
|`Editable`|Volitelné `Boolean` atribut. Určuje, zda lze literál po vložení fragmentu kódu upravit. Výchozí hodnota tohoto atributu je `true`.|

|Podřízený element.|Popis|
|-------------------|-----------------|
|[Default element](../ide/code-snippets-schema-reference.md#default-element)|Požadovaný element. Určuje výchozí hodnotu literálu při vložení fragmentu kódu. Musí obsahovat přesně jeden `Default` prvek `Literal` elementu.|
|[Function element](../ide/code-snippets-schema-reference.md#function-element)|Volitelný element. Určuje funkci, která se má provést, když literál získá fokus v sadě Visual Studio. Může být žádný nebo jeden `Function` prvky `Literal` elementu.|
|[Element ID.](../ide/code-snippets-schema-reference.md#id-element)|Požadovaný element. Určuje jedinečný identifikátor literálu. Musí obsahovat přesně jeden `ID` prvek `Literal` elementu.|
|[ToolTip – element](../ide/code-snippets-schema-reference.md#tooltip-element)|Volitelný element. Popisuje očekávanou hodnotu a použití literálu. Může být žádný nebo jeden **popisek** prvků v `Literal` elementu.|

|Nadřazený element|Popis|
| - |-----------------|
|[Declarations element](../ide/code-snippets-schema-reference.md#declarations-element)|Obsahuje literály a objekty fragmentu kódu, které lze upravovat.|

## <a name="namespace-element"></a>Namespace element

Určuje obor názvů, který musí být naimportován, aby bylo možné fragment kódu zkompilovat a spustit. Obor názvů zadaný v `Namespace` element se automaticky přidá do `Imports` příkaz na začátku kódu, pokud ještě neexistuje.

> [!NOTE]
> `Namespace` Element je podporována pouze pro projekty jazyka Visual Basic.

```xml
<Namespace>
    Namespace
</Namespace>
```

|Nadřazený element|Popis|
| - |-----------------|
|[Import – element](../ide/code-snippets-schema-reference.md#import-element)|Naimportuje zadaný obor názvů.|

Je vyžadována textová hodnota. Tento text určuje obor názvů, o kterém fragment kódu předpokládá, že bude naimportován.

## <a name="object-element"></a>Object element

Definuje objekty fragmentu kódu, které lze upravovat. `Object` Element slouží k identifikaci položky, která je potřeba ve fragmentu kódu, ale je pravděpodobně definována mimo samotný fragment kódu. Jako objekty by měly být deklarovány například ovládací prvky modelu Windows Forms, ovládací prvky technologie ASP.NET nebo instance typů. Deklarace objektů vyžadují, aby byl zadán typ, který se použije `Type` elementu.

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
|`Editable`|Volitelné `Boolean` atribut. Určuje, zda lze literál po vložení fragmentu kódu upravit. Výchozí hodnota tohoto atributu je `true`.|

|Podřízený element.|Popis|
|-------------------|-----------------|
|[Default element](../ide/code-snippets-schema-reference.md#default-element)|Požadovaný element. Určuje výchozí hodnotu literálu při vložení fragmentu kódu. Musí obsahovat přesně jeden `Default` prvek `Literal` elementu.|
|[Function element](../ide/code-snippets-schema-reference.md#function-element)|Volitelný element. Určuje funkci, která se má provést, když literál získá fokus v sadě Visual Studio. Může být žádný nebo jeden `Function` prvky `Literal` elementu.|
|[Element ID.](../ide/code-snippets-schema-reference.md#id-element)|Požadovaný element. Určuje jedinečný identifikátor literálu. Musí obsahovat přesně jeden `ID` prvek `Literal` elementu.|
|[ToolTip – element](../ide/code-snippets-schema-reference.md#tooltip-element)|Volitelný element. Popisuje očekávanou hodnotu a použití literálu. Může být žádný nebo jeden **popisek** prvků v `Literal` elementu.|
|[Type element](../ide/code-snippets-schema-reference.md#type-element)|Požadovaný element. Určuje typ objektu. Musí obsahovat přesně jeden `Type` prvek `Object` elementu.|

|Nadřazený element|Popis|
| - |-----------------|
|[Declarations element](../ide/code-snippets-schema-reference.md#declarations-element)|Obsahuje literály a objekty fragmentu kódu, které lze upravovat.|

## <a name="reference-element"></a>Reference – element

Určuje informace o odkazech na sestavení vyžadovaných fragmentem kódu.

```xml
<Reference>
    <Assembly>... </Assembly>
    <Url>... </Url>
</Reference>
```

|Podřízený element.|Popis|
|-------------------|-----------------|
|[Assembly – element](../ide/code-snippets-schema-reference.md#assembly-element)|Požadovaný element. Obsahuje název sestavení, na které se odkazuje fragment kódu. Musí obsahovat přesně jeden `Assembly` prvek `Reference` elementu.|
|[URL element](../ide/code-snippets-schema-reference.md#url-element)|Volitelný element. Obsahuje adresu URL s dalšími informacemi o odkazovaném sestavení. Může být žádný nebo jeden `Url` prvky `Reference` elementu.|

|Nadřazený element|Popis|
| - |-----------------|
|[References – element](../ide/code-snippets-schema-reference.md#references-element)|Element pro seskupení `Reference` elementy.|

## <a name="references-element"></a>References – element

Seskupuje jednotlivé `Reference` elementy.

```xml
<References>
    <Reference>... </Reference>
</References>
```

|Podřízený element.|Popis|
|-------------------|-----------------|
|[Reference – element](../ide/code-snippets-schema-reference.md#reference-element)|Volitelný element. Obsahuje informace o odkazech na sestavení pro fragment kódu. Může být nula nebo více `Reference` prvky `References` elementu.|

|Nadřazený element|Popis|
| - |-----------------|
|[Snippet element](../ide/code-snippets-schema-reference.md#snippet-element)|Obsahuje odkazy, direktivy import, deklarace a kód fragmentu kódu.|

## <a name="shortcut-element"></a>Shortcut element

Určuje textovou zkratku, pomocí níž lze fragment kódu vložit. Textová hodnota elementu `Shortcut` element může obsahovat jenom alfanumerické znaky, spojovníky (-) a podtržítka (_).

> [!CAUTION]
> _ a – nejsou podporované znaky v zkratky fragmentu kódu C++.

```xml
<Shortcut>
    Shortcut Text
</Shortcut>
```

|Nadřazený element|Popis|
| - |-----------------|
|[Header element](../ide/code-snippets-schema-reference.md#header-element)|Obsahuje obecné informace o fragmentu kódu.|

 Textová hodnota je volitelná. Tento text slouží jako zkratka pro vkládání fragmentů kódu.

## <a name="snippet-element"></a>Snippet element

Určuje odkazy, direktivy import, deklarace a kód fragmentu kódu.

```xml
<Snippet>
    <References>... </References>
    <Imports>... </Imports>
    <Declarations>... </Declarations>
    <Code>... </Code>
</Snippet>
```

|Podřízený element.|Popis|
|-------------------|-----------------|
|[Code – element](../ide/code-snippets-schema-reference.md#code-element)|Požadovaný element. Určuje kód, který chcete vložit do souboru dokumentace. Musí obsahovat přesně jeden `Code` prvek `Snippet` elementu.|
|[Declarations element](../ide/code-snippets-schema-reference.md#declarations-element)|Volitelný element. Určuje literály a objekty tvořící části fragmentu kódu, které lze upravovat. Může být žádný nebo jeden `Declarations` prvky `Snippet` elementu.|
|[Imports element](../ide/code-snippets-schema-reference.md#imports-element)|Volitelný element. Seskupuje jednotlivé `Import` elementy. Může být žádný nebo jeden `Imports` prvky `Snippet` elementu.|
||Volitelný element. Seskupuje jednotlivé `Reference` elementy. Může být žádný nebo jeden `References` prvky `Snippet` elementu.|

|Nadřazený element|Popis|
| - |-----------------|
|[CodeSnippet element](../ide/code-snippets-schema-reference.md#codesnippet-element)|Umožňuje zadat záhlaví a jeden nebo více fragmentů kódu technologie IntelliSense, které lze vložit do souborů kódu sady Visual Studio.|

## <a name="snippettype-element"></a>Snippettype – element

Určuje, jak sada Visual Studio vloží fragment kódu.

```xml
<SnippetType>
    SurroundsWith/Expansion
</SnippetType>
```

|Nadřazený element|Popis|
| - |-----------------|
|[Snippettypes – element](../ide/code-snippets-schema-reference.md#snippettypes-element)|Skupiny `SnippetType` elementy.|

Textová hodnota musí být jedna z následujících hodnot:

-   `SurroundsWith`: umožňuje umístit kolem vybrané části kódu fragment kódu.

-   `Expansion`: umožňuje fragment kódu vložit na pozici kurzoru.

-   `Refactoring`: Určuje, že fragment kódu je používán během refaktoringu jazyka C#. `Refactoring` nelze použít ve vlastních fragmentech kódu.

## <a name="snippettypes-element"></a>Snippettypes – element

Seskupuje jednotlivé `SnippetType` elementy. Pokud `SnippetTypes` prvek není k dispozici, fragment kódu lze vložit na libovolné místo v kódu.

```xml
<SnippetTypes>
    <SnippetType>... </SnippetType>
    <SnippetType>... </SnippetType>
</SnippetTypes>
```

|Podřízený element.|Popis|
|-------------------|-----------------|
|[Snippettype – element](../ide/code-snippets-schema-reference.md#snippettype-element)|Volitelný element. Určuje, jak sada Visual Studio vloží fragment kódu do kódu. Může být nula nebo více `SnippetType` prvky `SnippetTypes` elementu.|

|Nadřazený element|Popis|
| - |-----------------|
|[Header element](../ide/code-snippets-schema-reference.md#header-element)|Určuje obecné informace o fragmentu kódu.|

## <a name="title-element"></a>Title element

Určuje název fragmentu kódu. Název uložený v `Title` element fragmentu kódu se zobrazí v **Sběrač fragmentů kódu** a v popisu fragmentu kódu v **Správce fragmentů kódů**.

```xml
<Title>
    Code Snippet Title
</Title>
```

|Nadřazený element|Popis|
| - |-----------------|
|[Header element](../ide/code-snippets-schema-reference.md#header-element)|Určuje obecné informace o fragmentu kódu.|

 Je vyžadována textová hodnota. Tento text určuje název fragmentu kódu.

## <a name="tooltip-element"></a>ToolTip – element

Popisuje očekávanou hodnotu a použití literálu nebo objektu ve fragmentu kódu. Sada Visual Studio tyto informace zobrazí v popisku při vložení fragmentu kódu do projektu. Text popisku se zobrazí po vložení fragmentu kódu po umístění ukazatele myši na literál nebo objekt.

```xml
<ToolTip>
    ToolTip description
</ToolTip>
```

|Nadřazený element|Popis|
| - |-----------------|
|[Literal element](../ide/code-snippets-schema-reference.md#literal-element)|Definuje pole literálu fragmentu kódu, která lze upravovat.|
|[Object element](../ide/code-snippets-schema-reference.md#object-element)|Definuje pole objektu fragment kódu, která lze upravovat.|

 Je vyžadována textová hodnota. Tento text určuje popisek přidružený k objektu nebo literálu ve fragmentu kódu.

## <a name="type-element"></a>Type element

Určuje typ objektu. `Object` Element slouží k identifikaci položky, která je potřeba ve fragmentu kódu, ale je pravděpodobně definována mimo samotný fragment kódu. Jako objekty by měly být deklarovány například ovládací prvky modelu Windows Forms, ovládací prvky technologie ASP.NET nebo instance typů. Deklarace objektů vyžadují, aby byl zadán typ, který se použije `Type` elementu.

```xml
<Type>
    Type
</Type>
```

|Nadřazený element|Popis|
| - |-----------------|
|[Object element](../ide/code-snippets-schema-reference.md#object-element)|Definuje pole objektu fragment kódu, která lze upravovat.|

 Je vyžadována textová hodnota. Tento text určuje typ objektu.

## <a name="url-element"></a>URL element

Určuje adresu URL s dalšími informacemi o odkazovaném sestavení.

> [!NOTE]
> `Url` Element je podporována pouze pro projekty jazyka Visual Basic.

```xml
<Url>
    www.microsoft.com
</Url>
```

|Nadřazený element|Popis|
| - |-----------------|
|[Reference – element](../ide/code-snippets-schema-reference.md#reference-element)|Určuje odkazy na sestavení vyžadované fragmentem kódu.|

Je vyžadována textová hodnota. Tento text určuje adresu URL s dalšími informacemi o odkazovaném sestavení. Tato adresa URL se zobrazí, pokud odkaz nelze přidat do projektu.

## <a name="see-also"></a>Viz také:

- [Fragmenty kódu](../ide/code-snippets.md)
- [Návod: Vytvoření fragmentu kódu](../ide/walkthrough-creating-a-code-snippet.md)
