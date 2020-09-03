---
title: Referenční informace ke schématu fragmentů kódu
ms.date: 03/31/2020
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
ms.openlocfilehash: e31ec2be9ccce0b07b04746d2ed51ab3909cdd2c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "84183675"
---
# <a name="code-snippets-schema-reference"></a>Referenční informace ke schématu fragmentů kódu

Fragmenty kódu technologie IntelliSense jsou předem vytvořené části kódu, které jsou připravené k vložení do vaší aplikace pomocí sady Visual Studio. Svou produktivitu můžete zvýšit tak, že vytvoříte fragmenty kódu, které snižují množství času stráveného zadáváním opakujícího se kódu nebo hledáním ukázek. Pomocí schématu XML fragmentu kódu technologie IntelliSense můžete vytvořit vlastní fragmenty kódu a přidat je do fragmentů kódu, které již aplikace Visual Studio obsahuje.

## <a name="assembly-element"></a>Element Assembly

Určuje název sestavení, na které se odkazuje fragment kódu.

Textovou hodnotou elementu **sestavení** je popisný textový název sestavení, například `System.dll` nebo jeho silný název, jako je například `System,Version=1.0.0.1,Culture=neutral,PublicKeyToken=9b35aa323c18d4fb1` .

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

Určuje jméno autora fragmentu kódu. **Správce fragmentů kódu** zobrazí název uložený v `Author` elementu fragmentu kódu.

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

Dvě vyhrazená slova jsou k dispozici pro použití v textu `Code` prvku: `$end$` a `$selected$` . `$end$` označuje umístění, kam se má umístit kurzor po vložení fragmentu kódu. `$selected$` představuje text vybraný v dokumentu, který má být vložen do fragmentu při jeho vyvolání. Například s ohledem na fragment kódu, který obsahuje:

```
$selected$ is a great color.
```

Pokud je vybráno slovo "Blue", když uživatel vyvolá šablonu, výsledek je:

```
Blue is a great color.
```

`$end$` `$selected$` Ve fragmentu kódu nesmíte použít ani více než jednou. V takovém případě je rozpoznána pouze druhá instance. Daný fragment obsahuje:

```
$selected$ is a great color. I love $selected$.
```

Pokud je vybráno slovo "Blue", výsledek je:

```
 is a great color. I love Blue.
```

Počáteční místo se zobrazí, protože mezi a je mezera `$selected$` `is` .

Všechna ostatní `$` klíčová slova jsou dynamicky definována `<Literal>` v `<Object>` tagu a.

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

- **Jazyk**  -  _Povinný_ atribut, který určuje jazyk fragmentu kódu. Může jít o následující hodnoty:

   |Hodnota|Popis|
   |-----|-----------|
   |`VB`|Identifikuje fragment kódu jazyka Visual Basic.|
   |`CSharp`|Identifikuje fragment kódu jazyka C#.|
   |`CPP`|Identifikuje fragment kódu jazyka C++.|
   |`XAML`|Identifikuje fragment kódu XAML.|
   |`XML`|Identifikuje fragment kódu jazyka XML.|
   |`JavaScript`|Identifikuje fragment kódu jazyka JavaScript.|
   |`TypeScript`|Identifikuje fragment kódu TypeScript.|
   |`SQL`|Identifikuje fragment kódu jazyka SQL.|
   |`HTML`|Identifikuje fragment kódu jazyka HTML.|

- **Druh**  -  _Volitelný_ atribut, který určuje druh kódu, který obsahuje fragment. Může jít o následující hodnoty:

   |Hodnota|Popis|
   |-----|-----------|
   |`method body`|Určuje, že fragment kódu je tělo metody, a proto musí být vložen dovnitř deklarace metody.|
   |`method decl`|Určuje, že fragment kódu je metoda, a proto musí být vložen dovnitř třídy nebo modulu.|
   |`type decl`|Určuje, že fragment kódu je typ, a proto musí být vložen dovnitř třídy, modulu nebo oboru názvů.|
   |`file`|Určuje, že fragment kódu je celý soubor kódu. Tyto fragmenty kódu lze vložit samotné do souboru kódu nebo do oboru názvů.|
   |`any`|Určuje, že fragment kódu lze vložit kamkoli. Tato značka se používá pro fragmenty kódu, které jsou nezávislé na kontextu, například pro komentáře.|

- **Oddělovač**  -  _Volitelný_ atribut, který určuje oddělovač, který se používá k popisu literálů a objektů v kódu. Ve výchozím nastavení je oddělovač `$` .

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
|[Element Header](../ide/code-snippets-schema-reference.md#header-element)|Požadovaný element. Obsahuje obecné informace o fragmentu kódu. Fragment kódu musí obsahovat právě jeden `Header` element.|
|[Element fragmentu](../ide/code-snippets-schema-reference.md#snippet-element)|Požadovaný element. Obsahuje kód, který bude vložen sadou Visual Studio. Fragment kódu musí obsahovat právě jeden `Snippet` element.|

|Nadřazený element|Popis|
| - |-----------------|
|[Element CodeSnippets](../ide/code-snippets-schema-reference.md#codesnippets-element)|Kořenový element schématu XML fragmentu kódu|

## <a name="codesnippets-element"></a>Element CodeSnippets

Seskupuje elementy [codesnippet](../ide/code-snippets-schema-reference.md#codesnippet-element) . `CodeSnippets`Element je kořenovým prvkem schématu XML fragmentu kódu.

```xml
<CodeSnippets>
    <CodeSnippet>... </CodeSnippet>
</CodeSnippets>
```

|Podřízený element|Popis|
|-------------------|-----------------|
|[Element CodeSnippet](../ide/code-snippets-schema-reference.md#codesnippet-element)|Volitelný element. Nadřazený element pro všechna data fragmentu kódu. Element může obsahovat nula nebo více `CodeSnippet` prvků `CodeSnippets` .|

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
|[Element Literal](../ide/code-snippets-schema-reference.md#literal-element)|Volitelný element. Definuje literály fragmentu kódu, které lze upravovat. Element může obsahovat nula nebo více `Literal` prvků `Declarations` .|
|[Element Object](../ide/code-snippets-schema-reference.md#object-element)|Volitelný element. Definuje objekty fragmentu kódu, které lze upravovat. Element může obsahovat nula nebo více `Object` prvků `Declarations` .|

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
> Ne všechny jazyky podporují `function` prvky. Dostupné funkce najdete v dokumentaci ke konkrétnímu jazyku.

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
|[Element Author](../ide/code-snippets-schema-reference.md#author-element)|Volitelný element. Jméno osoby nebo společnosti, která fragment kódu vytvořila. Element může obsahovat nula nebo jeden `Author` element `Header` .|
|[Description – element](../ide/code-snippets-schema-reference.md#description-element)|Volitelný element. Popis fragmentu kódu. Element může obsahovat nula nebo jeden `Description` element `Header` .|
|[Element HelpUrl](../ide/code-snippets-schema-reference.md#helpurl-element)|Volitelný element. Adresa URL s dalšími informacemi o fragmentu kódu. V elementu Header může být nula nebo jeden `HelpURL` element. **Poznámka:**  Visual Studio nepoužívá `HelpUrl` element. Tento element je součástí schématu XML fragmentu kódu technologie IntelliSense a jakékoli fragmenty kódu, které tento element obsahují, budou úspěšně ověřeny, ale hodnota elementu nebude nikdy použita.|
|[Keywords – element](../ide/code-snippets-schema-reference.md#keywords-element)|Volitelný element. Seskupuje `Keyword` prvky. Element může obsahovat nula nebo jeden `Keywords` element `Header` .|
|[Element zástupce](../ide/code-snippets-schema-reference.md#shortcut-element)|Volitelný element. Určuje textovou zkratku, pomocí níž lze fragment kódu vložit. Element může obsahovat nula nebo jeden `Shortcut` element `Header` .|
|[Element SnippetTypes](../ide/code-snippets-schema-reference.md#snippettypes-element)|Volitelný element. Seskupuje `SnippetType` prvky. Element může obsahovat nula nebo jeden `SnippetTypes` element `Header` . Pokud nejsou žádné `SnippetTypes` prvky, fragment kódu je vždy platný.|
|[Title – element](../ide/code-snippets-schema-reference.md#title-element)|Požadovaný element. Popisný název fragmentu kódu. Element musí obsahovat právě jeden `Title` element `Header` .|

|Nadřazený element|Popis|
| - |-----------------|
|[Element CodeSnippet](../ide/code-snippets-schema-reference.md#codesnippet-element)|Nadřazený element pro všechna data fragmentu kódu.|

## <a name="helpurl-element"></a>Element HelpUrl

Určujte adresu URL s dalšími informacemi o fragmentu kódu.

> [!NOTE]
> Visual Studio nepoužívá `HelpUrl` element. Tento element je součástí schématu XML fragmentu kódu technologie IntelliSense a jakékoli fragmenty kódu, které tento element obsahují, budou úspěšně ověřeny, ale hodnota elementu nebude nikdy použita.

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

Určuje jedinečný identifikátor pro `Literal` `Object` element or. Žádné dva literály nebo objekty ve stejném fragmentu kódu nemohou mít ve svých prvcích stejnou textovou hodnotu `ID` . Literály a objekty nemůžou obsahovat `ID` element s hodnotou end. Hodnota `$end$` je vyhrazená a slouží k označení umístění, kam se má umístit kurzor po vložení fragmentu kódu.

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
|[Element Namespace](../ide/code-snippets-schema-reference.md#namespace-element)|Požadovaný element. Určuje obor názvů používaný fragmentem kódu. Element musí obsahovat právě jeden `Namespace` element `Import` .|

|Nadřazený element|Popis|
| - |-----------------|
|[Imports – element](../ide/code-snippets-schema-reference.md#imports-element)|Prvek seskupení pro elementy **Import** .|

## <a name="imports-element"></a>Imports – element

Seskupí jednotlivé `Import` prvky.

```xml
<Imports>
    <Import>... </Import>
</Imports>
```

|Podřízený element|Popis|
|-------------------|-----------------|
|[Import – element](../ide/code-snippets-schema-reference.md#import-element)|Volitelný element. Obsahuje naimportované obory názvů pro fragment kódu. Element může obsahovat nula nebo více elementů **importu** `Imports` .|

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
|[Keywords – element](../ide/code-snippets-schema-reference.md#keywords-element)|Seskupí jednotlivé `Keyword` prvky.|

Je vyžadována textová hodnota. Klíčové slovo fragmentu kódu.

## <a name="keywords-element"></a>Keywords – element

Seskupí jednotlivé `Keyword` prvky. Klíčová slova fragmentů kódu používá sada Visual Studio a představují standardní způsob pro online poskytovatele obsahu, jak přidávat vlastní klíčová slova pro vyhledávání nebo kategorizaci.

```xml
<Keywords>
    <Keyword>... </Keyword>
    <Keyword>... </Keyword>
</Keywords>
```

|Podřízený element|Popis|
|-------------------|-----------------|
|[Element klíčového slova](../ide/code-snippets-schema-reference.md#keyword-element)|Volitelný element. Obsahuje jednotlivá klíčová slova pro fragment kódu. Element může obsahovat nula nebo více `Keyword` prvků `Keywords` .|

|Nadřazený element|Popis|
| - |-----------------|
|[Element Header](../ide/code-snippets-schema-reference.md#header-element)|Obsahuje obecné informace o fragmentu kódu.|

## <a name="literal-element"></a>Element Literal

Definuje literály fragmentu kódu, které lze upravovat. `Literal`Prvek slouží k identifikaci náhrady za část kódu, která je zcela obsažena v rámci fragmentu, ale bude pravděpodobně upravena poté, co je vložena do kódu. Jako literály by měly být deklarovány například řetězcové literály, číselné hodnoty a některé názvy proměnných.

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
|`Editable`|Volitelný `Boolean` atribut. Určuje, zda lze literál po vložení fragmentu kódu upravit. Výchozí hodnota tohoto atributu je `true` .|

|Podřízený element|Popis|
|-------------------|-----------------|
|[Výchozí element](../ide/code-snippets-schema-reference.md#default-element)|Požadovaný element. Určuje výchozí hodnotu literálu při vložení fragmentu kódu. Element musí obsahovat právě jeden `Default` element `Literal` .|
|[Element Function](../ide/code-snippets-schema-reference.md#function-element)|Volitelný element. Určuje funkci, která se má provést, když literál získá fokus v sadě Visual Studio. Element může obsahovat nula nebo jeden `Function` element `Literal` .|
|[Element ID](../ide/code-snippets-schema-reference.md#id-element)|Požadovaný element. Určuje jedinečný identifikátor literálu. Element musí obsahovat právě jeden `ID` element `Literal` .|
|[Element ToolTip](../ide/code-snippets-schema-reference.md#tooltip-element)|Volitelný element. Popisuje očekávanou hodnotu a použití literálu. Element může obsahovat nula nebo jeden element **ToolTip** `Literal` .|

|Nadřazený element|Popis|
| - |-----------------|
|[Element Declarations](../ide/code-snippets-schema-reference.md#declarations-element)|Obsahuje literály a objekty fragmentu kódu, které lze upravovat.|

## <a name="namespace-element"></a>Element Namespace

Určuje obor názvů, který musí být naimportován, aby bylo možné fragment kódu zkompilovat a spustit. Obor názvů zadaný v `Namespace` elementu je automaticky přidán do `using` direktivy nebo `Imports` příkazu na začátku kódu, pokud ještě neexistuje.

```xml
<Namespace>
    Namespace
</Namespace>
```

|Nadřazený element|Popis|
| - |-----------------|
|[Import – element](../ide/code-snippets-schema-reference.md#import-element)|Naimportuje zadaný obor názvů.|

Je vyžadována textová hodnota. Tento text určuje obor názvů, o kterém fragment kódu předpokládá, že bude naimportován.

## <a name="object-element"></a>Element Object

Definuje objekty fragmentu kódu, které lze upravovat. `Object`Element se používá k identifikaci položky, která je požadována fragmentem kódu, ale je pravděpodobně definována mimo samotný fragment kódu. Jako objekty by měly být deklarovány například ovládací prvky modelu Windows Forms, ovládací prvky technologie ASP.NET nebo instance typů. Deklarace objektů vyžadují, aby byl zadán typ, který je proveden s `Type` prvkem.

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
|`Editable`|Volitelný `Boolean` atribut. Určuje, zda lze literál po vložení fragmentu kódu upravit. Výchozí hodnota tohoto atributu je `true` .|

|Podřízený element|Popis|
|-------------------|-----------------|
|[Výchozí element](../ide/code-snippets-schema-reference.md#default-element)|Požadovaný element. Určuje výchozí hodnotu literálu při vložení fragmentu kódu. Element musí obsahovat právě jeden `Default` element `Literal` .|
|[Element Function](../ide/code-snippets-schema-reference.md#function-element)|Volitelný element. Určuje funkci, která se má provést, když literál získá fokus v sadě Visual Studio. Element může obsahovat nula nebo jeden `Function` element `Literal` .|
|[Element ID](../ide/code-snippets-schema-reference.md#id-element)|Požadovaný element. Určuje jedinečný identifikátor literálu. Element musí obsahovat právě jeden `ID` element `Literal` .|
|[Element ToolTip](../ide/code-snippets-schema-reference.md#tooltip-element)|Volitelný element. Popisuje očekávanou hodnotu a použití literálu. Element může obsahovat nula nebo jeden element **ToolTip** `Literal` .|
|[Element Type](../ide/code-snippets-schema-reference.md#type-element)|Požadovaný element. Určuje typ objektu. Element musí obsahovat právě jeden `Type` element `Object` .|

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
|[Element Assembly](../ide/code-snippets-schema-reference.md#assembly-element)|Požadovaný element. Obsahuje název sestavení, na které se odkazuje fragment kódu. Element musí obsahovat právě jeden `Assembly` element `Reference` .|
|[Element URL](../ide/code-snippets-schema-reference.md#url-element)|Volitelný element. Obsahuje adresu URL s dalšími informacemi o odkazovaném sestavení. Element může obsahovat nula nebo jeden `Url` element `Reference` .|

|Nadřazený element|Popis|
| - |-----------------|
|[Odkazuje na element](../ide/code-snippets-schema-reference.md#references-element)|Seskupení elementu pro `Reference` elementy|

## <a name="references-element"></a>Odkazuje na element

Seskupí jednotlivé `Reference` prvky.

```xml
<References>
    <Reference>... </Reference>
</References>
```

|Podřízený element|Popis|
|-------------------|-----------------|
|[Element reference](../ide/code-snippets-schema-reference.md#reference-element)|Volitelný element. Obsahuje informace o odkazech na sestavení pro fragment kódu. Element může obsahovat nula nebo více `Reference` prvků `References` .|

|Nadřazený element|Popis|
| - |-----------------|
|[Element fragmentu](../ide/code-snippets-schema-reference.md#snippet-element)|Obsahuje odkazy, direktivy import, deklarace a kód fragmentu kódu.|

## <a name="shortcut-element"></a>Element zástupce

Určuje textovou zkratku, pomocí níž lze fragment kódu vložit. Textová hodnota `Shortcut` elementu může obsahovat pouze alfanumerické znaky a podtržítka (_).

> [!CAUTION]
> Podtržítka (_) nepodporují znaky v zástupcích fragmentů jazyka C++.

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
|[Element Code](../ide/code-snippets-schema-reference.md#code-element)|Požadovaný element. Určuje kód, který chcete vložit do souboru dokumentace. Element musí obsahovat právě jeden `Code` element `Snippet` .|
|[Element Declarations](../ide/code-snippets-schema-reference.md#declarations-element)|Volitelný element. Určuje literály a objekty tvořící části fragmentu kódu, které lze upravovat. Element může obsahovat nula nebo jeden `Declarations` element `Snippet` .|
|[Imports – element](../ide/code-snippets-schema-reference.md#imports-element)|Volitelný element. Seskupí jednotlivé `Import` prvky. Element může obsahovat nula nebo jeden `Imports` element `Snippet` .|
|[Odkazuje na element](../ide/code-snippets-schema-reference.md#references-element)|Volitelný element. Seskupí jednotlivé `Reference` prvky. Element může obsahovat nula nebo jeden `References` element `Snippet` .|

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
|[Element SnippetTypes](../ide/code-snippets-schema-reference.md#snippettypes-element)|Seskupuje `SnippetType` prvky.|

Textová hodnota musí být jedna z následujících hodnot:

- `SurroundsWith`: umožňuje umístit fragment kódu kolem vybraného kusu kódu.

- `Expansion`: umožňuje vložení fragmentu kódu na pozici kurzoru.

- `Refactoring`: Určuje, zda je fragment kódu použit během refaktoringu jazyka C#. `Refactoring` nelze použít ve vlastních fragmentech kódu.

## <a name="snippettypes-element"></a>Element SnippetTypes

Seskupí jednotlivé `SnippetType` prvky. Pokud `SnippetTypes` element není přítomen, může být fragment kódu vložen kamkoli do kódu.

```xml
<SnippetTypes>
    <SnippetType>... </SnippetType>
    <SnippetType>... </SnippetType>
</SnippetTypes>
```

|Podřízený element|Popis|
|-------------------|-----------------|
|[Element SnippetType](../ide/code-snippets-schema-reference.md#snippettype-element)|Volitelný element. Určuje, jak sada Visual Studio vloží fragment kódu do kódu. Element může obsahovat nula nebo více `SnippetType` prvků `SnippetTypes` .|

|Nadřazený element|Popis|
| - |-----------------|
|[Element Header](../ide/code-snippets-schema-reference.md#header-element)|Určuje obecné informace o fragmentu kódu.|

## <a name="title-element"></a>Title – element

Určuje název fragmentu kódu. Název uložený v `Title` elementu fragmentu kódu se zobrazí ve **výběru fragmentu kódu** a v popisu fragmentu kódu ve **Správci fragmentů kódů**.

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

Určuje typ objektu. `Object`Element se používá k identifikaci položky, která je požadována fragmentem kódu, ale je pravděpodobně definována mimo samotný fragment kódu. Jako objekty by měly být deklarovány například ovládací prvky modelu Windows Forms, ovládací prvky technologie ASP.NET nebo instance typů. Deklarace objektů vyžadují, aby byl zadán typ, který je proveden s `Type` prvkem.

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
> `Url`Element je podporován pouze pro Visual Basic projekty.

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
