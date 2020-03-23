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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "79301837"
---
# <a name="code-snippets-schema-reference"></a>Referenční informace ke schématu fragmentů kódu

Výstřižky kódu IntelliSense jsou předem navržené části kódu, které jsou připraveny k vložení do aplikace pomocí sady Visual Studio. Svou produktivitu můžete zvýšit tak, že vytvoříte fragmenty kódu, které snižují množství času stráveného zadáváním opakujícího se kódu nebo hledáním ukázek. Pomocí schématu XML výstřižků kódu IntelliSense můžete vytvořit vlastní fragmenty kódu a přidat je do fragmentů kódu, které visual studio již obsahuje.

## <a name="assembly-element"></a>Montážní prvek

Určuje název sestavení, na které se odkazuje fragment kódu.

Textová hodnota elementu **Assembly** je popisný textový název `System.dll`sestavení, například , `System,Version=1.0.0.1,Culture=neutral,PublicKeyToken=9b35aa323c18d4fb1`nebo jeho silný název, například .

```xml
<Assembly>
    AssemblyName
</Assembly>
```

|Nadřazený prvek|Popis|
| - |-----------------|
|[Referenční prvek](../ide/code-snippets-schema-reference.md#reference-element)|Obsahuje informace o odkazech na sestavení vyžadovaných fragmentem kódu.|

Je vyžadována textová hodnota. Tento text určuje sestavení, na které se odkazuje fragment kódu.

## <a name="author-element"></a>Autorprvek

Určuje jméno autora fragmentu kódu. **Správce fragmentů kódu** zobrazí název uložený `Author` v prvku fragmentu kódu.

```xml
<Author>
   Code Snippet Author
</Author>
```

|Nadřazený prvek|Popis|
| - |-----------------|
|[Element záhlaví](../ide/code-snippets-schema-reference.md#header-element)|Obsahuje obecné informace o fragmentu kódu.|

Je vyžadována textová hodnota. Tento text určuje autora fragmentu kódu.

## <a name="code-element"></a>Element kódu

Poskytuje kontejner pro krátké bloky kódu.

### <a name="keywords"></a>Klíčová slova

V textu `Code` prvku jsou k dispozici dvě `$end$` vyhrazená slova: a `$selected$`. `$end$`označuje umístění, kam chcete umístit kurzor po vložení fragmentu kódu. `$selected$`představuje text vybraný v dokumentu, který má být vložen do fragmentu, když je vyvolán. Například daný úryvek, který zahrnuje:

```
$selected$ is a great color.
```

Pokud je slovo "Modrá" vybráno, když uživatel vyvolá šablonu, výsledkem je:

```
Blue is a great color.
```

Ve fragmentu `$end$` kódu `$selected$` nesmíte použít ani jeden nebo vícekrát. Pokud tak učiníte, je rozpoznána pouze druhá instance. Vzhledem k tomu, úryvek, který zahrnuje:

```
$selected$ is a great color. I love $selected$.
```

Pokud je vybráno slovo "Modrá", výsledkem je:

```
 is a great color. I love Blue.
```

Počáteční mezera se zobrazí, `$selected$` protože `is`mezi a .

Všechna `$` ostatní klíčová slova jsou `<Literal>` dynamicky definována ve značkách a. `<Object>`

Následuje struktura Code elementu:

```xml
<Code Language="Language"
    Kind="method body/method decl/type decl/page/file/any"
    Delimiter="Delimiter">
    Code to insert
</Code>
```

Je vyžadována textová hodnota. Tento text určuje kód spolu s literály a objekty, které můžete použít při vložení tohoto fragmentu kódu do souboru kódu.

### <a name="attributes"></a>Atributy

Pro element Code jsou k dispozici tři atributy:

- **Atribut** - _Povinný_ jazyk, který určuje jazyk fragmentu kódu. Může jít o následující hodnoty:

   |Hodnota|Popis|
   |-----|-----------|
   |`VB`|Identifikuje fragment kódu jazyka Visual Basic.|
   |`CSharp`|Identifikuje fragment kódu jazyka C#.|
   |`CPP`|Identifikuje fragment kódu jazyka C++.|
   |`XML`|Identifikuje fragment kódu jazyka XML.|
   |`JavaScript`|Identifikuje fragment kódu jazyka JavaScript.|
   |`TypeScript`|Identifikuje fragment kódu typu TypeScript.|
   |`SQL`|Identifikuje fragment kódu jazyka SQL.|
   |`HTML`|Identifikuje fragment kódu jazyka HTML.|

- **Kind** - _Optional_ atribut, který určuje druh kódu, který fragment obsahuje. Může jít o následující hodnoty:

   |Hodnota|Popis|
   |-----|-----------|
   |`method body`|Určuje, že fragment kódu je tělo metody, a proto musí být vložen dovnitř deklarace metody.|
   |`method decl`|Určuje, že fragment kódu je metoda, a proto musí být vložen dovnitř třídy nebo modulu.|
   |`type decl`|Určuje, že fragment kódu je typ, a proto musí být vložen dovnitř třídy, modulu nebo oboru názvů.|
   |`file`|Určuje, že fragment kódu je celý soubor kódu. Tyto fragmenty kódu lze vložit samotné do souboru kódu nebo do oboru názvů.|
   |`any`|Určuje, že fragment kódu lze vložit kamkoli. Tato značka se používá pro fragmenty kódu, které jsou nezávislé na kontextu, například pro komentáře.|

- **Oddělovač** - _Volitelný_ atribut, který určuje oddělovač používaný k popisu literály a objekty v kódu. Ve výchozím nastavení je `$`oddělovač .

### <a name="parent-element"></a>Nadřazený prvek

|Nadřazený prvek|Popis|
| - |-----------------|
|[Prvek úryvku](../ide/code-snippets-schema-reference.md#snippet-element)|Obsahuje odkazy, direktivy import, deklarace a kód fragmentu kódu.|

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
|`Format`|Požadovaný atribut. Určuje verzi schématu fragmentu kódu. Atribut Format musí být řetězec, který používá syntaxi x.x.x, kde každé písmeno „x“ představuje číselnou hodnotu čísla verze. Visual Studio bude ignorovat fragmenty `Format` kódu s atributy, které nerozumí.|

|Podřízený prvek|Popis|
|-------------------|-----------------|
|[Element záhlaví](../ide/code-snippets-schema-reference.md#header-element)|Požadovaný element. Obsahuje obecné informace o fragmentu kódu. Ve fragmentu `Header` kódu musí být přesně jeden prvek.|
|[Prvek úryvku](../ide/code-snippets-schema-reference.md#snippet-element)|Požadovaný element. Obsahuje kód, který bude vložen sadou Visual Studio. Ve fragmentu `Snippet` kódu musí být přesně jeden prvek.|

|Nadřazený prvek|Popis|
| - |-----------------|
|[Element CodeSnippets](../ide/code-snippets-schema-reference.md#codesnippets-element)|Kořenový element schématu XML fragmentu kódu|

## <a name="codesnippets-element"></a>Element CodeSnippets

Seskupí [prvky CodeSnippet.](../ide/code-snippets-schema-reference.md#codesnippet-element) Tento `CodeSnippets` prvek je kořenovým prvkem schématu XML fragmentu kódu.

```xml
<CodeSnippets>
    <CodeSnippet>... </CodeSnippet>
</CodeSnippets>
```

|Podřízený prvek|Popis|
|-------------------|-----------------|
|[Element CodeSnippet](../ide/code-snippets-schema-reference.md#codesnippet-element)|Volitelný element. Nadřazený element pro všechna data fragmentu kódu. V prvku může `CodeSnippet` být nula `CodeSnippets` nebo více prvků.|

## <a name="declarations-element"></a>Prvek Deklarace

Určuje literály a objekty tvořící části fragmentu kódu, které lze upravovat.

```xml
<Declarations>
    <Literal>... </Literal>
    <Object>... </Object>
</Declarations>
```

|Podřízený prvek|Popis|
|-------------------|-----------------|
|[Doslovný prvek](../ide/code-snippets-schema-reference.md#literal-element)|Volitelný element. Definuje literály fragmentu kódu, které lze upravovat. V prvku může `Literal` být nula `Declarations` nebo více prvků.|
|[Prvek objektu](../ide/code-snippets-schema-reference.md#object-element)|Volitelný element. Definuje objekty fragmentu kódu, které lze upravovat. V prvku může `Object` být nula `Declarations` nebo více prvků.|

|Nadřazený prvek|Popis|
| - |-----------------|
|[Prvek úryvku](../ide/code-snippets-schema-reference.md#snippet-element)|Obsahuje odkazy, direktivy import, deklarace a kód fragmentu kódu.|

## <a name="default-element"></a>Výchozí prvek

Určuje výchozí hodnotu literálu nebo objektu pro fragment kódu technologie IntelliSense.

```xml
<Default>
    Default value
</Default>
```

|Nadřazený prvek|Popis|
| - |-----------------|
|[Doslovný prvek](../ide/code-snippets-schema-reference.md#literal-element)|Definuje pole literálu fragmentu kódu, která lze upravovat.|
|[Prvek objektu](../ide/code-snippets-schema-reference.md#object-element)|Definuje pole objektu fragment kódu, která lze upravovat.|

Je vyžadována textová hodnota. Tento text určuje výchozí hodnotu literálu nebo objektu, pomocí níž budou naplněna pole fragmentu kódu, která lze upravovat.

## <a name="description-element"></a>Prvek popisu

Určuje popisné informace o obsahu fragmentu kódu technologie IntelliSense.

```xml
<Description>
    Code Snippet Description
</Description>
```

|Nadřazený prvek|Popis|
| - |-----------------|
|[Element záhlaví](../ide/code-snippets-schema-reference.md#header-element)|Obsahuje obecné informace o fragmentu kódu.|

Je vyžadována textová hodnota. Tento text popisuje fragment kódu.

## <a name="function-element"></a>Funkční prvek

Určuje funkci, která se má provést, když literál nebo objekt získá fokus v sadě Visual Studio.

> [!NOTE]
> Prvek `Function` je podporován pouze v fragmenty kódu Jazyka C#.

```xml
<Function>
    FunctionName
</Function>
```

|Nadřazený prvek|Popis|
| - |-----------------|
|[Doslovný prvek](../ide/code-snippets-schema-reference.md#literal-element)|Definuje pole literálu fragmentu kódu, která lze upravovat.|
|[Prvek objektu](../ide/code-snippets-schema-reference.md#object-element)|Definuje pole objektu fragment kódu, která lze upravovat.|

Je vyžadována textová hodnota. Tento text určuje funkci, která se má provést, když pole literálu nebo objektu získá fokus v sadě Visual Studio.

## <a name="header-element"></a>Element záhlaví

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

|Podřízený prvek|Popis|
|-------------------|-----------------|
|[Autorprvek](../ide/code-snippets-schema-reference.md#author-element)|Volitelný element. Jméno osoby nebo společnosti, která fragment kódu vytvořila. V prvku může `Author` být nula `Header` nebo jeden prvek.|
|[Prvek popisu](../ide/code-snippets-schema-reference.md#description-element)|Volitelný element. Popis fragmentu kódu. V prvku může `Description` být nula `Header` nebo jeden prvek.|
|[Prvek HelpUrl](../ide/code-snippets-schema-reference.md#helpurl-element)|Volitelný element. Adresa URL s dalšími informacemi o fragmentu kódu. V elementu Header `HelpURL` může být nula nebo jeden prvek. **Poznámka:**  Visual Studio nepoužívá `HelpUrl` prvek. Tento element je součástí schématu XML fragmentu kódu technologie IntelliSense a jakékoli fragmenty kódu, které tento element obsahují, budou úspěšně ověřeny, ale hodnota elementu nebude nikdy použita.|
|[Prvek klíčová slova](../ide/code-snippets-schema-reference.md#keywords-element)|Volitelný element. Seskupí `Keyword` prvky. V prvku může `Keywords` být nula `Header` nebo jeden prvek.|
|[Zástupce prvku](../ide/code-snippets-schema-reference.md#shortcut-element)|Volitelný element. Určuje textovou zkratku, pomocí níž lze fragment kódu vložit. V prvku může `Shortcut` být nula `Header` nebo jeden prvek.|
|[Element SnippetTypes](../ide/code-snippets-schema-reference.md#snippettypes-element)|Volitelný element. Seskupí `SnippetType` prvky. V prvku může `SnippetTypes` být nula `Header` nebo jeden prvek. Pokud neexistují `SnippetTypes` žádné prvky, fragment kódu je vždy platný.|
|[Prvek nadpisu](../ide/code-snippets-schema-reference.md#title-element)|Požadovaný element. Popisný název fragmentu kódu. V `Header` prvku musí `Title` být přesně jeden prvek.|

|Nadřazený prvek|Popis|
| - |-----------------|
|[Element CodeSnippet](../ide/code-snippets-schema-reference.md#codesnippet-element)|Nadřazený element pro všechna data fragmentu kódu.|

## <a name="helpurl-element"></a>Prvek HelpUrl

Určujte adresu URL s dalšími informacemi o fragmentu kódu.

> [!NOTE]
> Visual Studio nepoužívá `HelpUrl` prvek. Tento element je součástí schématu XML fragmentu kódu technologie IntelliSense a jakékoli fragmenty kódu, které tento element obsahují, budou úspěšně ověřeny, ale hodnota elementu nebude nikdy použita.

```xml
<HelpUrl>
    www.microsoft.com
</HelpUrl>
```

|Nadřazený prvek|Popis|
| - |-----------------|
|[Element záhlaví](../ide/code-snippets-schema-reference.md#header-element)|Obsahuje obecné informace o fragmentu kódu.|

Textová hodnota je volitelná. Tento text určuje adresu URL, na níž naleznete další informace o fragmentu kódu.

## <a name="id-element"></a>ID prvek

Určuje jedinečný identifikátor prvku `Literal` `Object` nebo. Žádné dva literály nebo objekty ve stejném fragmentu kódu mohou `ID` mít ve svých prvcích stejnou textovou hodnotu. Literály a objekty `ID` nemohou obsahovat prvek s hodnotou end. Hodnota `$end$` je vyhrazena a slouží k označení umístění pro umístění kurzoru po vložení fragmentu kódu.

```xml
<ID>
    Unique Identifier
</ID>
```

|Nadřazený prvek|Popis|
| - |-----------------|
|[Doslovný prvek](../ide/code-snippets-schema-reference.md#literal-element)|Definuje pole literálu fragmentu kódu, která lze upravovat.|
|[Prvek objektu](../ide/code-snippets-schema-reference.md#object-element)|Definuje pole objektu fragment kódu, která lze upravovat.|

Je vyžadována textová hodnota. Tento text určuje jedinečný identifikátor pro objekt nebo literál.

## <a name="import-element"></a>Prvek importu

Určuje importované obory názvů používané fragmentem kódu Technologie IntelliSense.

```xml
<Import>
    <Namespace>... </Namespace>
</Import>
```

|Podřízený prvek|Popis|
|-------------------|-----------------|
|[Prvek oboru názvů](../ide/code-snippets-schema-reference.md#namespace-element)|Požadovaný element. Určuje obor názvů používaný fragmentem kódu. V `Import` prvku musí `Namespace` být přesně jeden prvek.|

|Nadřazený prvek|Popis|
| - |-----------------|
|[Importuje prvek](../ide/code-snippets-schema-reference.md#imports-element)|Seskupení element pro **import** prvků.|

## <a name="imports-element"></a>Importuje prvek

Seskupí jednotlivé `Import` prvky.

```xml
<Imports>
    <Import>... </Import>
</Imports>
```

|Podřízený prvek|Popis|
|-------------------|-----------------|
|[Prvek importu](../ide/code-snippets-schema-reference.md#import-element)|Volitelný element. Obsahuje naimportované obory názvů pro fragment kódu. V prvku může být nula `Imports` nebo více **importovat** prvky.|

|Nadřazený prvek|Popis|
| - |-----------------|
|[Prvek úryvku](../ide/code-snippets-schema-reference.md#snippet-element)|Obsahuje odkazy, direktivy import, deklarace a kód fragmentu kódu.|

## <a name="keyword-element"></a>Prvek klíčového slova

Určuje vlastní klíčové slovo pro fragment kódu. Klíčová slova fragmentů kódu používá sada Visual Studio a představují standardní způsob pro online poskytovatele obsahu, jak přidávat vlastní klíčová slova pro vyhledávání nebo kategorizaci.

```xml
<Keyword>
    Code Snippet Keyword
</Keyword>
```

|Nadřazený prvek|Popis|
| - |-----------------|
|[Prvek klíčová slova](../ide/code-snippets-schema-reference.md#keywords-element)|Seskupí jednotlivé `Keyword` prvky.|

Je vyžadována textová hodnota. Klíčové slovo fragmentu kódu.

## <a name="keywords-element"></a>Prvek klíčová slova

Seskupí jednotlivé `Keyword` prvky. Klíčová slova fragmentů kódu používá sada Visual Studio a představují standardní způsob pro online poskytovatele obsahu, jak přidávat vlastní klíčová slova pro vyhledávání nebo kategorizaci.

```xml
<Keywords>
    <Keyword>... </Keyword>
    <Keyword>... </Keyword>
</Keywords>
```

|Podřízený prvek|Popis|
|-------------------|-----------------|
|[Prvek klíčového slova](../ide/code-snippets-schema-reference.md#keyword-element)|Volitelný element. Obsahuje jednotlivá klíčová slova pro fragment kódu. V prvku může `Keyword` být nula `Keywords` nebo více prvků.|

|Nadřazený prvek|Popis|
| - |-----------------|
|[Element záhlaví](../ide/code-snippets-schema-reference.md#header-element)|Obsahuje obecné informace o fragmentu kódu.|

## <a name="literal-element"></a>Doslovný prvek

Definuje literály fragmentu kódu, které lze upravovat. Prvek `Literal` se používá k identifikaci nahrazení části kódu, který je zcela obsažen v fragmentu, ale bude pravděpodobně přizpůsobit po vložení do kódu. Jako literály by měly být deklarovány například řetězcové literály, číselné hodnoty a některé názvy proměnných.

Literály a objekty nemohou obsahovat prvek **ID** s hodnotou vybrané nebo koncové hodnoty. Hodnota `$selected$` představuje text vybraný v dokumentu, který má být vložen do fragmentu, když je vyvolán. `$end$`označuje umístění, kam chcete umístit kurzor po vložení fragmentu kódu.

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
|`Editable`|Volitelný `Boolean` atribut. Určuje, zda lze literál po vložení fragmentu kódu upravit. Výchozí hodnota tohoto atributu je `true`.|

|Podřízený prvek|Popis|
|-------------------|-----------------|
|[Výchozí prvek](../ide/code-snippets-schema-reference.md#default-element)|Požadovaný element. Určuje výchozí hodnotu literálu při vložení fragmentu kódu. V `Literal` prvku musí `Default` být přesně jeden prvek.|
|[Funkční prvek](../ide/code-snippets-schema-reference.md#function-element)|Volitelný element. Určuje funkci, která se má provést, když literál získá fokus v sadě Visual Studio. V prvku může `Function` být nula `Literal` nebo jeden prvek.|
|[ID prvek](../ide/code-snippets-schema-reference.md#id-element)|Požadovaný element. Určuje jedinečný identifikátor literálu. V `Literal` prvku musí `ID` být přesně jeden prvek.|
|[Element popisu](../ide/code-snippets-schema-reference.md#tooltip-element)|Volitelný element. Popisuje očekávanou hodnotu a použití literálu. V prvku může být nula `Literal` nebo jeden **popisný popis** prvky.|

|Nadřazený prvek|Popis|
| - |-----------------|
|[Prvek Deklarace](../ide/code-snippets-schema-reference.md#declarations-element)|Obsahuje literály a objekty fragmentu kódu, které lze upravovat.|

## <a name="namespace-element"></a>Prvek oboru názvů

Určuje obor názvů, který musí být naimportován, aby bylo možné fragment kódu zkompilovat a spustit. Obor názvů zadaný `Namespace` v elementu `using` je `Imports` automaticky přidán do směrnice nebo příkazu na začátku kódu, pokud ještě neexistuje.

```xml
<Namespace>
    Namespace
</Namespace>
```

|Nadřazený prvek|Popis|
| - |-----------------|
|[Prvek importu](../ide/code-snippets-schema-reference.md#import-element)|Naimportuje zadaný obor názvů.|

Je vyžadována textová hodnota. Tento text určuje obor názvů, o kterém fragment kódu předpokládá, že bude naimportován.

## <a name="object-element"></a>Prvek objektu

Definuje objekty fragmentu kódu, které lze upravovat. Prvek `Object` se používá k identifikaci položky, která je vyžadována fragmentem kódu, ale pravděpodobně bude definována mimo samotný výstřižek. Jako objekty by měly být deklarovány například ovládací prvky modelu Windows Forms, ovládací prvky technologie ASP.NET nebo instance typů. Deklarace objektu vyžadují, aby byl zadán `Type` typ, který se provádí s elementem.

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
|`Editable`|Volitelný `Boolean` atribut. Určuje, zda lze literál po vložení fragmentu kódu upravit. Výchozí hodnota tohoto atributu je `true`.|

|Podřízený prvek|Popis|
|-------------------|-----------------|
|[Výchozí prvek](../ide/code-snippets-schema-reference.md#default-element)|Požadovaný element. Určuje výchozí hodnotu literálu při vložení fragmentu kódu. V `Literal` prvku musí `Default` být přesně jeden prvek.|
|[Funkční prvek](../ide/code-snippets-schema-reference.md#function-element)|Volitelný element. Určuje funkci, která se má provést, když literál získá fokus v sadě Visual Studio. V prvku může `Function` být nula `Literal` nebo jeden prvek.|
|[ID prvek](../ide/code-snippets-schema-reference.md#id-element)|Požadovaný element. Určuje jedinečný identifikátor literálu. V `Literal` prvku musí `ID` být přesně jeden prvek.|
|[Element popisu](../ide/code-snippets-schema-reference.md#tooltip-element)|Volitelný element. Popisuje očekávanou hodnotu a použití literálu. V prvku může být nula `Literal` nebo jeden **popisný popis** prvky.|
|[Typový prvek](../ide/code-snippets-schema-reference.md#type-element)|Požadovaný element. Určuje typ objektu. V `Object` prvku musí `Type` být přesně jeden prvek.|

|Nadřazený prvek|Popis|
| - |-----------------|
|[Prvek Deklarace](../ide/code-snippets-schema-reference.md#declarations-element)|Obsahuje literály a objekty fragmentu kódu, které lze upravovat.|

## <a name="reference-element"></a>Referenční prvek

Určuje informace o odkazech na sestavení vyžadovaných fragmentem kódu.

```xml
<Reference>
    <Assembly>... </Assembly>
    <Url>... </Url>
</Reference>
```

|Podřízený prvek|Popis|
|-------------------|-----------------|
|[Montážní prvek](../ide/code-snippets-schema-reference.md#assembly-element)|Požadovaný element. Obsahuje název sestavení, na které se odkazuje fragment kódu. V `Reference` prvku musí `Assembly` být přesně jeden prvek.|
|[Prvek url](../ide/code-snippets-schema-reference.md#url-element)|Volitelný element. Obsahuje adresu URL s dalšími informacemi o odkazovaném sestavení. V prvku může `Url` být nula `Reference` nebo jeden prvek.|

|Nadřazený prvek|Popis|
| - |-----------------|
|[Element odkazů](../ide/code-snippets-schema-reference.md#references-element)|Seskupení element `Reference` pro prvky.|

## <a name="references-element"></a>Element odkazů

Seskupí jednotlivé `Reference` prvky.

```xml
<References>
    <Reference>... </Reference>
</References>
```

|Podřízený prvek|Popis|
|-------------------|-----------------|
|[Referenční prvek](../ide/code-snippets-schema-reference.md#reference-element)|Volitelný element. Obsahuje informace o odkazech na sestavení pro fragment kódu. V prvku může `Reference` být nula `References` nebo více prvků.|

|Nadřazený prvek|Popis|
| - |-----------------|
|[Prvek úryvku](../ide/code-snippets-schema-reference.md#snippet-element)|Obsahuje odkazy, direktivy import, deklarace a kód fragmentu kódu.|

## <a name="shortcut-element"></a>Zástupce prvku

Určuje textovou zkratku, pomocí níž lze fragment kódu vložit. Textová hodnota `Shortcut` prvku může obsahovat pouze alfanumerické znaky a podtržítka ( _ ).

> [!CAUTION]
> Podtržítko (_) není podporováno znaky v c++ zástupce úryvku.

```xml
<Shortcut>
    Shortcut Text
</Shortcut>
```

|Nadřazený prvek|Popis|
| - |-----------------|
|[Element záhlaví](../ide/code-snippets-schema-reference.md#header-element)|Obsahuje obecné informace o fragmentu kódu.|

Textová hodnota je volitelná. Tento text slouží jako zkratka pro vkládání fragmentů kódu.

## <a name="snippet-element"></a>Prvek úryvku

Určuje odkazy, direktivy import, deklarace a kód fragmentu kódu.

```xml
<Snippet>
    <References>... </References>
    <Imports>... </Imports>
    <Declarations>... </Declarations>
    <Code>... </Code>
</Snippet>
```

|Podřízený prvek|Popis|
|-------------------|-----------------|
|[Prvek kódu](../ide/code-snippets-schema-reference.md#code-element)|Požadovaný element. Určuje kód, který chcete vložit do souboru dokumentace. V `Snippet` prvku musí `Code` být přesně jeden prvek.|
|[Prvek Deklarace](../ide/code-snippets-schema-reference.md#declarations-element)|Volitelný element. Určuje literály a objekty tvořící části fragmentu kódu, které lze upravovat. V prvku může `Declarations` být nula `Snippet` nebo jeden prvek.|
|[Importuje prvek](../ide/code-snippets-schema-reference.md#imports-element)|Volitelný element. Seskupí jednotlivé `Import` prvky. V prvku může `Imports` být nula `Snippet` nebo jeden prvek.|
|[Element odkazů](../ide/code-snippets-schema-reference.md#references-element)|Volitelný element. Seskupí jednotlivé `Reference` prvky. V prvku může `References` být nula `Snippet` nebo jeden prvek.|

|Nadřazený prvek|Popis|
| - |-----------------|
|[Element CodeSnippet](../ide/code-snippets-schema-reference.md#codesnippet-element)|Umožňuje zadat záhlaví a jeden nebo více fragmentů kódu technologie IntelliSense, které lze vložit do souborů kódu sady Visual Studio.|

## <a name="snippettype-element"></a>Element SnippetType

Určuje, jak sada Visual Studio vloží fragment kódu.

```xml
<SnippetType>
    SurroundsWith/Expansion
</SnippetType>
```

|Nadřazený prvek|Popis|
| - |-----------------|
|[Element SnippetTypes](../ide/code-snippets-schema-reference.md#snippettypes-element)|Seskupí `SnippetType` prvky.|

Textová hodnota musí být jedna z následujících hodnot:

- `SurroundsWith`: umožňuje umístění fragmentu kódu kolem vybrané části kódu.

- `Expansion`: umožňuje vložit fragment kódu do kurzoru.

- `Refactoring`: určuje, že fragment kódu se používá během refaktoringu Jazyka C#. `Refactoring`nelze použít ve vlastních fragmentech kódu.

## <a name="snippettypes-element"></a>Element SnippetTypes

Seskupí jednotlivé `SnippetType` prvky. Pokud `SnippetTypes` prvek není k dispozici, fragment kódu lze vložit kdekoli v kódu.

```xml
<SnippetTypes>
    <SnippetType>... </SnippetType>
    <SnippetType>... </SnippetType>
</SnippetTypes>
```

|Podřízený prvek|Popis|
|-------------------|-----------------|
|[Element SnippetType](../ide/code-snippets-schema-reference.md#snippettype-element)|Volitelný element. Určuje, jak sada Visual Studio vloží fragment kódu do kódu. V prvku může `SnippetType` být nula `SnippetTypes` nebo více prvků.|

|Nadřazený prvek|Popis|
| - |-----------------|
|[Element záhlaví](../ide/code-snippets-schema-reference.md#header-element)|Určuje obecné informace o fragmentu kódu.|

## <a name="title-element"></a>Prvek nadpisu

Určuje název fragmentu kódu. Název uložený `Title` v prvku fragmentu kódu se zobrazí v **výběru fragmentu kódu** a v popisu fragmentu kódu ve **Správci fragmentů kódu**.

```xml
<Title>
    Code Snippet Title
</Title>
```

|Nadřazený prvek|Popis|
| - |-----------------|
|[Element záhlaví](../ide/code-snippets-schema-reference.md#header-element)|Určuje obecné informace o fragmentu kódu.|

Je vyžadována textová hodnota. Tento text určuje název fragmentu kódu.

## <a name="tooltip-element"></a>Element popisu

Popisuje očekávanou hodnotu a použití literálu nebo objektu ve fragmentu kódu. Sada Visual Studio tyto informace zobrazí v popisku při vložení fragmentu kódu do projektu. Text popisku se zobrazí po vložení fragmentu kódu po umístění ukazatele myši na literál nebo objekt.

```xml
<ToolTip>
    ToolTip description
</ToolTip>
```

|Nadřazený prvek|Popis|
| - |-----------------|
|[Doslovný prvek](../ide/code-snippets-schema-reference.md#literal-element)|Definuje pole literálu fragmentu kódu, která lze upravovat.|
|[Prvek objektu](../ide/code-snippets-schema-reference.md#object-element)|Definuje pole objektu fragment kódu, která lze upravovat.|

Je vyžadována textová hodnota. Tento text určuje popisek přidružený k objektu nebo literálu ve fragmentu kódu.

## <a name="type-element"></a>Typový prvek

Určuje typ objektu. Prvek `Object` se používá k identifikaci položky, která je vyžadována fragmentem kódu, ale pravděpodobně bude definována mimo samotný výstřižek. Jako objekty by měly být deklarovány například ovládací prvky modelu Windows Forms, ovládací prvky technologie ASP.NET nebo instance typů. Deklarace objektu vyžadují, aby byl zadán `Type` typ, který se provádí s elementem.

```xml
<Type>
    Type
</Type>
```

|Nadřazený prvek|Popis|
| - |-----------------|
|[Prvek objektu](../ide/code-snippets-schema-reference.md#object-element)|Definuje pole objektu fragment kódu, která lze upravovat.|

Je vyžadována textová hodnota. Tento text určuje typ objektu. Například:

```xml
<Type>System.Data.SqlClient.SqlConnection</Type>
```

## <a name="url-element"></a>Prvek url

Určuje adresu URL s dalšími informacemi o odkazovaném sestavení.

> [!NOTE]
> Prvek `Url` je podporován pouze pro projekty jazyka.

```xml
<Url>
    www.microsoft.com
</Url>
```

|Nadřazený prvek|Popis|
| - |-----------------|
|[Referenční prvek](../ide/code-snippets-schema-reference.md#reference-element)|Určuje odkazy na sestavení vyžadované fragmentem kódu.|

Je vyžadována textová hodnota. Tento text určuje adresu URL s dalšími informacemi o odkazovaném sestavení. Tato adresa URL se zobrazí, pokud odkaz nelze přidat do projektu.

## <a name="see-also"></a>Viz také

- [Fragmenty kódu](../ide/code-snippets.md)
- [Návod: Vytvoření fragmentu kódu](../ide/walkthrough-creating-a-code-snippet.md)
