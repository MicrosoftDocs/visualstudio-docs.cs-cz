---
title: Referenční dokumentace schématu fragmentů kódu | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- schema reference [Visual Studio]
- snippets [Visual Studio], schema reference
- code snippets [Visual Studio], schema reference
- IntelliSense Code Snippets, XML Schema
ms.assetid: 58a60621-725f-4763-93b7-62ea5424ef88
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 19a14972d36bcb7070e0604b47caab55f41d0126
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49188105"
---
# <a name="code-snippets-schema-reference"></a>Fragmenty kódu – odkaz schématu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Fragmenty kódu technologie IntelliSense jsou předem vytvořené části kódu, které jsou připraveny k vložení do vaší aplikace pomocí [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Svou produktivitu můžete zvýšit tak, že vytvoříte fragmenty kódu, které snižují množství času stráveného zadáváním opakujícího se kódu nebo hledáním ukázek. Schématu XML fragmentu kódu technologie IntelliSense můžete použít k vytvoření své vlastní fragmenty kódu a přidat k fragmentům kódu, který [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] již obsahuje.  
  
## <a name="intellisense-code-snippets-schema-elements"></a>Elementy schématu fragmentů kódu technologie IntelliSense  
  
||||  
|-|-|-|  
|[Assembly – Element](../ide/code-snippets-schema-reference.md#assembly)|[Helpurl – Element](../ide/code-snippets-schema-reference.md#helpurl)|[References – Element](../ide/code-snippets-schema-reference.md#references)|  
|[Element Autor](../ide/code-snippets-schema-reference.md#author)|[Element ID.](../ide/code-snippets-schema-reference.md#id)|[Shortcut Element](../ide/code-snippets-schema-reference.md#shortcut)|  
|[Code – Element](../ide/code-snippets-schema-reference.md#code)|[Import – Element](../ide/code-snippets-schema-reference.md#import)|[Snippet Element](../ide/code-snippets-schema-reference.md#snippet)|  
|[CodeSnippet Element](../ide/code-snippets-schema-reference.md#codesnippet)|[Imports Element](../ide/code-snippets-schema-reference.md#imports)|[Snippettype – Element](../ide/code-snippets-schema-reference.md#snippettype)|  
|[Codesnippets – Element](../ide/code-snippets-schema-reference.md#codesnippets)|[Keyword Element](../ide/code-snippets-schema-reference.md#keyword)|[Snippettypes – Element](../ide/code-snippets-schema-reference.md#snippettypes)|  
|[Declarations Element](../ide/code-snippets-schema-reference.md#declarations)|[Element Keyword](../ide/code-snippets-schema-reference.md#keywords)|[Title Element](../ide/code-snippets-schema-reference.md#title)|  
|[Default Element](../ide/code-snippets-schema-reference.md#default)|[Literal Element](../ide/code-snippets-schema-reference.md#literal)|[ToolTip – Element](../ide/code-snippets-schema-reference.md#tooltip)|  
|[Description – Element](../ide/code-snippets-schema-reference.md#description)|[Namespace Element](../ide/code-snippets-schema-reference.md#namespace)|[Type Element](../ide/code-snippets-schema-reference.md#type)|  
|[Function Element](../ide/code-snippets-schema-reference.md#function)|[Object Element](../ide/code-snippets-schema-reference.md#object)|[URL Element](../ide/code-snippets-schema-reference.md#url)|  
|[Header Element](../ide/code-snippets-schema-reference.md#header)|[Reference – Element](../ide/code-snippets-schema-reference.md#reference)||  
  
##  <a name="assembly"></a> Assembly – Element  
 Určuje název sestavení, na které se odkazuje fragment kódu.  
  
> [!NOTE]
>  `Assembly` Prvek je podporován pouze fragmenty kódu jazyka Visual Basic.  
  
 Textová hodnota elementu **sestavení** element je buď popisný textový název sestavení, jako například `System.dll`, nebo jeho silný název, například `System,Version=1.0.0.1,Culture=neutral,PublicKeyToken=9b35aa323c18d4fb1`.  
  
```xml  
<Assembly>  
    AssemblyName  
</Assembly>  
```  
  
|Nadřazený element|Popis|  
|--------------------|-----------------|  
|[Reference – Element](../ide/code-snippets-schema-reference.md#reference)|Obsahuje informace o odkazech na sestavení vyžadovaných fragmentem kódu.|  
  
 Je vyžadována textová hodnota. Tento text určuje sestavení, na které se odkazuje fragment kódu.  
  
##  <a name="author"></a> Element Autor  
 Určuje jméno autora fragmentu kódu. **Správce fragmentů kódů** zobrazí jméno uložené v `Author` element fragmentu kódu.  
  
```xml  
<Author>  
   Code Snippet Author  
</Author>  
  
```  
  
|Nadřazený element|Popis|  
|--------------------|-----------------|  
|[Header Element](../ide/code-snippets-schema-reference.md#header)|Obsahuje obecné informace o fragmentu kódu.|  
  
 Je vyžadována textová hodnota. Tento text určuje autora fragmentu kódu.  
  
##  <a name="code"></a> Code – Element  
 Poskytuje kontejner pro krátké bloky kódu.  
  
 Dvě vyhrazená slova jsou k dispozici pro použití v textu `Code` element: `$end$` a `$selected$`. `$end$` označuje umístění, umístěte kurzor po vložení fragmentu kódu. `$selected$` představuje text vybraný v dokumentu, který má být do fragmentu kódu vložen při jeho vyvolání. Mějme například fragment kódu, který obsahuje:  
  
```xml  
$selected$ is a great color.  
```  
  
 Pokud je vybráno slovo "Blue", když uživatel vyvolá šablonu, výsledek je:  
  
```xml  
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
  
```xml  
<Code Language="Language"  
    Kind="method body/method decl/type decl/page/file/any"  
    Delimiter="Delimiter">  
    Code to insert  
</Code>  
```  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`Delimiter`|Nepovinný atribut. Určuje oddělovač použitý k označení literálů a objektů v kódu. Ve výchozím nastavení, je oddělovač `$`.|  
|`Kind`|Nepovinný atribut. Určuje druh kódu, který fragment kódu obsahuje, a umístění, do kterého musí být fragment kódu vložen, aby jej bylo možné zkompilovat. Dostupné hodnoty jsou `method body`, `method decl`, `type decl`, `file`, a `any`.|  
|`Language`|Požadovaný atribut. Určuje jazyk fragmentu kódu.|  
  
|Hodnota atributu Kind|Popis|  
|--------------------------|-----------------|  
|`method body`|Určuje, že fragment kódu je tělo metody, a proto musí být vložen dovnitř deklarace metody.|  
|`method decl`|Určuje, že fragment kódu je metoda, a proto musí být vložen dovnitř třídy nebo modulu.|  
|`type decl`|Určuje, že fragment kódu je typ, a proto musí být vložen dovnitř třídy, modulu nebo oboru názvů.|  
|`file`|Určuje, že fragment kódu je celý soubor kódu. Tyto fragmenty kódu lze vložit samotné do souboru kódu nebo do oboru názvů.|  
|`any`|Určuje, že fragment kódu lze vložit kamkoli. Tato značka se používá pro fragmenty kódu, které jsou nezávislé na kontextu, například pro komentáře.|  
  
|Hodnota atributu Language|Popis|  
|------------------------------|-----------------|  
|`VB`|Identifikuje fragment kódu jazyka Visual Basic.|  
|`CSharp`|Identifikuje fragment kódu jazyka C#.|  
|`CPP`|Identifikuje fragment kódu jazyka C++.|  
|`XML`|Identifikuje fragment kódu jazyka XML.|  
|`JavaScript`|Identifikuje fragment kódu jazyka JavaScript.|  
|`SQL`|Identifikuje fragment kódu jazyka SQL.|  
|`HTML`|Identifikuje fragment kódu jazyka HTML.|  
  
|Nadřazený element|Popis|  
|--------------------|-----------------|  
|[Snippet Element](../ide/code-snippets-schema-reference.md#snippet)|Obsahuje odkazy, direktivy import, deklarace a kód fragmentu kódu.|  
  
 Je vyžadována textová hodnota. Tento text určuje kód spolu s literály a objekty, které lze použít při vložení tohoto fragmentu kódu do projektu.  
  
##  <a name="codesnippet"></a> CodeSnippet Element  
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
  
|Podřízený element|Popis|  
|-------------------|-----------------|  
|[Header Element](../ide/code-snippets-schema-reference.md#header)|Požadovaný element. Obsahuje obecné informace o fragmentu kódu. Musí obsahovat přesně jeden `Header` element ve fragmentu kódu.|  
|[Snippet Element](../ide/code-snippets-schema-reference.md#snippet)|Požadovaný element. Obsahuje kód, který bude vložen sadou Visual Studio. Musí obsahovat přesně jeden `Snippet` element ve fragmentu kódu.|  
  
|Nadřazený element|Popis|  
|--------------------|-----------------|  
|[Codesnippets – Element](../ide/code-snippets-schema-reference.md#codesnippets)|Kořenový element schématu XML fragmentu kódu|  
  
##  <a name="codesnippets"></a> Codesnippets – Element  
 Skupiny [CodeSnippet Element](../ide/code-snippets-schema-reference.md#codesnippet)elementy. `CodeSnippets` Prvek je kořenovým prvkem schématu XML fragmentu kódu.  
  
```xml  
<CodeSnippets>  
    <CodeSnippet>... </CodeSnippet>  
</CodeSnippets>  
  
```  
  
|Podřízený element|Popis|  
|-------------------|-----------------|  
|[CodeSnippet Element](../ide/code-snippets-schema-reference.md#codesnippet)|Volitelný element. Nadřazený element pro všechna data fragmentu kódu. Může být nula nebo více `CodeSnippet` prvky `CodeSnippets` elementu.|  
  
##  <a name="declarations"></a> Declarations Element  
 Určuje literály a objekty tvořící části fragmentu kódu, které lze upravovat.  
  
```xml  
<Declarations>  
    <Literal>... </Literal>  
    <Object>... </Object>  
</Declarations>  
  
```  
  
|Podřízený element|Popis|  
|-------------------|-----------------|  
|[Literal Element](../ide/code-snippets-schema-reference.md#literal)|Volitelný element. Definuje literály fragmentu kódu, které lze upravovat. Může být nula nebo více `Literal` prvky `Declarations` elementu.|  
|[Object Element](../ide/code-snippets-schema-reference.md#object)|Volitelný element. Definuje objekty fragmentu kódu, které lze upravovat. Může být nula nebo více `Object` prvky `Declarations` elementu.|  
  
|Nadřazený element|Popis|  
|--------------------|-----------------|  
|[Snippet Element](../ide/code-snippets-schema-reference.md#snippet)|Obsahuje odkazy, direktivy import, deklarace a kód fragmentu kódu.|  
  
##  <a name="default"></a> Default Element  
 Určuje výchozí hodnotu literálu nebo objektu pro fragment kódu technologie IntelliSense.  
  
```xml  
<Default>  
    Default value  
</Default>  
  
```  
  
|Nadřazený element|Popis|  
|--------------------|-----------------|  
|[Literal Element](../ide/code-snippets-schema-reference.md#literal)|Definuje pole literálu fragmentu kódu, která lze upravovat.|  
|[Object Element](../ide/code-snippets-schema-reference.md#object)|Definuje pole objektu fragment kódu, která lze upravovat.|  
  
 Je vyžadována textová hodnota. Tento text určuje výchozí hodnotu literálu nebo objektu, pomocí níž budou naplněna pole fragmentu kódu, která lze upravovat.  
  
##  <a name="description"></a> Description – Element  
 Určuje popisné informace o obsahu fragmentu kódu technologie IntelliSense.  
  
```xml  
<Description>  
    Code Snippet Description  
</Description>  
```  
  
|Nadřazený element|Popis|  
|--------------------|-----------------|  
|[Header Element](../ide/code-snippets-schema-reference.md#header)|Obsahuje obecné informace o fragmentu kódu.|  
  
 Je vyžadována textová hodnota. Tento text popisuje fragment kódu.  
  
##  <a name="function"></a> Function Element  
 Určuje funkci, která se má provést, když literál nebo objekt získá fokus v sadě Visual Studio.  
  
> [!NOTE]
>  `Function` Element je podporován pouze ve fragmentech kódu jazyka Visual C#.  
  
```xml  
<Function>  
    FunctionName  
</Function>  
```  
  
|Nadřazený element|Popis|  
|--------------------|-----------------|  
|[Literal Element](../ide/code-snippets-schema-reference.md#literal)|Definuje pole literálu fragmentu kódu, která lze upravovat.|  
|[Object Element](../ide/code-snippets-schema-reference.md#object)|Definuje pole objektu fragment kódu, která lze upravovat.|  
  
 Je vyžadována textová hodnota. Tento text určuje funkci, která se má provést, když pole literálu nebo objektu získá fokus v sadě Visual Studio.  
  
##  <a name="header"></a> Header Element  
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
|[Element Autor](../ide/code-snippets-schema-reference.md#author)|Volitelný element. Jméno osoby nebo společnosti, která fragment kódu vytvořila. Může být žádný nebo jeden `Author` prvky `Header` elementu.|  
|[Description – Element](../ide/code-snippets-schema-reference.md#description)|Volitelný element. Popis fragmentu kódu. Může být žádný nebo jeden `Description` prvky `Header` elementu.|  
|[Helpurl – Element](../ide/code-snippets-schema-reference.md#helpurl)|Volitelný element. Adresa URL s dalšími informacemi o fragmentu kódu. Může být žádný nebo jeden `HelpURL` prvků v záhlaví elementu. **Poznámka:** nepoužívá sady Visual Studio `HelpUrl` elementu. Tento element je součástí schématu XML fragmentu kódu technologie IntelliSense a jakékoli fragmenty kódu, které tento element obsahují, budou úspěšně ověřeny, ale hodnota elementu nebude nikdy použita.|  
|[Element Keyword](../ide/code-snippets-schema-reference.md#keywords)|Volitelný element. Skupiny `Keyword` elementy. Může být žádný nebo jeden `Keywords` prvky `Header` elementu.|  
|[Shortcut Element](../ide/code-snippets-schema-reference.md#shortcut)|Volitelný element. Určuje textovou zkratku, pomocí níž lze fragment kódu vložit. Může být žádný nebo jeden `Shortcut` prvky `Header` elementu.|  
|[Snippettypes – Element](../ide/code-snippets-schema-reference.md#snippettypes)|Volitelný element. Skupiny `SnippetType` elementy. Může být žádný nebo jeden `SnippetTypes` prvky `Header` elementu. Pokud neexistují žádné `SnippetTypes` prvky, fragment kódu je vždy platný.|  
|[Title Element](../ide/code-snippets-schema-reference.md#title)|Požadovaný element. Popisný název fragmentu kódu. Musí obsahovat přesně jeden `Title` prvek `Header` elementu.|  
  
|Nadřazený element|Popis|  
|--------------------|-----------------|  
|[CodeSnippet Element](../ide/code-snippets-schema-reference.md#codesnippet)|Nadřazený element pro všechna data fragmentu kódu.|  
  
##  <a name="helpurl"></a> Helpurl – Element  
 Určujte adresu URL s dalšími informacemi o fragmentu kódu.  
  
> [!NOTE]
>  Visual Studio nebude používat `HelpUrl` elementu. Tento element je součástí schématu XML fragmentu kódu technologie IntelliSense a jakékoli fragmenty kódu, které tento element obsahují, budou úspěšně ověřeny, ale hodnota elementu nebude nikdy použita.  
  
```xml  
<HelpUrl>  
    www.microsoft.com  
</HelpUrl>  
  
```  
  
|Nadřazený element|Popis|  
|--------------------|-----------------|  
|[Header Element](../ide/code-snippets-schema-reference.md#header)|Obsahuje obecné informace o fragmentu kódu.|  
  
 Textová hodnota je volitelná. Tento text určuje adresu URL, na níž naleznete další informace o fragmentu kódu.  
  
##  <a name="id"></a> Element ID.  
 Určuje jedinečný identifikátor `Literal` nebo `Object` elementu. Žádné dva literály nebo objekty ve stejném fragmentu kódu mají stejnou textovou hodnotu jejich `ID` elementy. Literály a objekty nesmí obsahovat `ID` element s hodnotou elementu end. Hodnota `$end$` je vyhrazena a používá se k označení umístění, umístěte kurzor po vložení fragmentu kódu.  
  
```xml  
<ID>  
    Unique Identifier  
</ID>  
  
```  
  
|Nadřazený element|Popis|  
|--------------------|-----------------|  
|[Literal Element](../ide/code-snippets-schema-reference.md#literal)|Definuje pole literálu fragmentu kódu, která lze upravovat.|  
|[Object Element](../ide/code-snippets-schema-reference.md#object)|Definuje pole objektu fragment kódu, která lze upravovat.|  
  
 Je vyžadována textová hodnota. Tento text určuje jedinečný identifikátor pro objekt nebo literál.  
  
##  <a name="import"></a> Import – Element  
 Určuje naimportované obory názvů používané fragmentem kódu technologie IntelliSense.  
  
> [!NOTE]
>  `Import` Element je podporována pouze pro projekty jazyka Visual Basic.  
  
```xml  
<Import>  
    <Namespace>... </Namespace>  
</Import>  
  
```  
  
|Podřízený element|Popis|  
|-------------------|-----------------|  
|[Namespace Element](../ide/code-snippets-schema-reference.md#namespace)|Požadovaný element. Určuje obor názvů používaný fragmentem kódu. Musí obsahovat přesně jeden `Namespace` prvek `Import` elementu.|  
  
|Nadřazený element|Popis|  
|--------------------|-----------------|  
|[Imports Element](../ide/code-snippets-schema-reference.md#imports)|Element pro seskupení **Import** elementy.|  
  
##  <a name="imports"></a> Imports Element  
 Seskupuje jednotlivé `Import` elementy.  
  
> [!NOTE]
>  `Imports` Element je podporována pouze pro projekty jazyka Visual Basic.  
  
```xml  
<Imports>  
    <Import>... </Import>  
<Imports>  
```  
  
|Podřízený element|Popis|  
|-------------------|-----------------|  
|[Import – Element](../ide/code-snippets-schema-reference.md#import)|Volitelný element. Obsahuje naimportované obory názvů pro fragment kódu. Může být nula nebo více **Import** prvky `Imports` elementu.|  
  
|Nadřazený element|Popis|  
|--------------------|-----------------|  
|[Snippet Element](../ide/code-snippets-schema-reference.md#snippet)|Obsahuje odkazy, direktivy import, deklarace a kód fragmentu kódu.|  
  
##  <a name="keyword"></a> Keyword Element  
 Určuje vlastní klíčové slovo pro fragment kódu. Klíčová slova fragmentů kódu používá sada Visual Studio a představují standardní způsob pro online poskytovatele obsahu, jak přidávat vlastní klíčová slova pro vyhledávání nebo kategorizaci.  
  
```xml  
<Keyword>  
    Code Snippet Keyword  
</Keyword>  
```  
  
|Nadřazený element|Popis|  
|--------------------|-----------------|  
|[Element Keyword](../ide/code-snippets-schema-reference.md#keywords)|Seskupuje jednotlivé `Keyword` elementy.|  
  
 Je vyžadována textová hodnota. Klíčové slovo fragmentu kódu.  
  
##  <a name="keywords"></a> Element Keyword  
 Seskupuje jednotlivé `Keyword` elementy. Klíčová slova fragmentů kódu používá sada Visual Studio a představují standardní způsob pro online poskytovatele obsahu, jak přidávat vlastní klíčová slova pro vyhledávání nebo kategorizaci.  
  
```xml  
<Keywords>  
    <Keyword>... </Keyword>  
    <Keyword>... </Keyword>  
<Keywords>  
```  
  
|Podřízený element|Popis|  
|-------------------|-----------------|  
|[Keyword Element](../ide/code-snippets-schema-reference.md#keyword)|Volitelný element. Obsahuje jednotlivá klíčová slova pro fragment kódu. Může být nula nebo více `Keyword` prvky `Keywords` elementu.|  
  
|Nadřazený element|Popis|  
|--------------------|-----------------|  
|[Header Element](../ide/code-snippets-schema-reference.md#header)|Obsahuje obecné informace o fragmentu kódu.|  
  
##  <a name="literal"></a> Literal Element  
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
  
|Podřízený element|Popis|  
|-------------------|-----------------|  
|[Default Element](../ide/code-snippets-schema-reference.md#default)|Požadovaný element. Určuje výchozí hodnotu literálu při vložení fragmentu kódu. Musí obsahovat přesně jeden `Default` prvek `Literal` elementu.|  
|[Function Element](../ide/code-snippets-schema-reference.md#function)|Volitelný element. Určuje funkci, která se má provést, když literál získá fokus v sadě Visual Studio. Může být žádný nebo jeden `Function` prvky `Literal` elementu.|  
|[Element ID.](../ide/code-snippets-schema-reference.md#id)|Požadovaný element. Určuje jedinečný identifikátor literálu. Musí obsahovat přesně jeden `ID` prvek `Literal` elementu.|  
|[ToolTip – Element](../ide/code-snippets-schema-reference.md#tooltip)|Volitelný element. Popisuje očekávanou hodnotu a použití literálu. Může být žádný nebo jeden **popisek** prvků v `Literal` elementu.|  
  
|Nadřazený element|Popis|  
|--------------------|-----------------|  
|[Declarations Element](../ide/code-snippets-schema-reference.md#declarations)|Obsahuje literály a objekty fragmentu kódu, které lze upravovat.|  
  
##  <a name="namespace"></a> Namespace Element  
 Určuje obor názvů, který musí být naimportován, aby bylo možné fragment kódu zkompilovat a spustit. Obor názvů zadaný v `Namespace` element se automaticky přidá do `Imports` příkaz na začátku kódu, pokud ještě neexistuje.  
  
> [!NOTE]
>  `Namespace` Element je podporována pouze pro projekty jazyka Visual Basic.  
  
```xml  
<Namespace>  
    Namespace  
</Namespace>  
```  
  
|Nadřazený element|Popis|  
|--------------------|-----------------|  
|[Import – Element](../ide/code-snippets-schema-reference.md#import)|Naimportuje zadaný obor názvů.|  
  
 Je vyžadována textová hodnota. Tento text určuje obor názvů, o kterém fragment kódu předpokládá, že bude naimportován.  
  
##  <a name="object"></a> Object Element  
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
  
|Podřízený element|Popis|  
|-------------------|-----------------|  
|[Default Element](../ide/code-snippets-schema-reference.md#default)|Požadovaný element. Určuje výchozí hodnotu literálu při vložení fragmentu kódu. Musí obsahovat přesně jeden `Default` prvek `Literal` elementu.|  
|[Function Element](../ide/code-snippets-schema-reference.md#function)|Volitelný element. Určuje funkci, která se má provést, když literál získá fokus v sadě Visual Studio. Může být žádný nebo jeden `Function` prvky `Literal` elementu.|  
|[Element ID.](../ide/code-snippets-schema-reference.md#id)|Požadovaný element. Určuje jedinečný identifikátor literálu. Musí obsahovat přesně jeden `ID` prvek `Literal` elementu.|  
|[ToolTip – Element](../ide/code-snippets-schema-reference.md#tooltip)|Volitelný element. Popisuje očekávanou hodnotu a použití literálu. Může být žádný nebo jeden **popisek** prvků v `Literal` elementu.|  
|[Type Element](../ide/code-snippets-schema-reference.md#type)|Požadovaný element. Určuje typ objektu. Musí obsahovat přesně jeden `Type` prvek `Object` elementu.|  
  
|Nadřazený element|Popis|  
|--------------------|-----------------|  
|[Declarations Element](../ide/code-snippets-schema-reference.md#declarations)|Obsahuje literály a objekty fragmentu kódu, které lze upravovat.|  
  
##  <a name="reference"></a> Reference – Element  
 Určuje informace o odkazech na sestavení vyžadovaných fragmentem kódu.  
  
> [!NOTE]
>  `Reference` Element je podporována pouze pro projekty jazyka Visual Basic.  
  
```xml  
<Reference>  
    <Assembly>... </Assembly>  
    <Url>... </Url>  
</Reference>  
```  
  
|Podřízený element|Popis|  
|-------------------|-----------------|  
|[Assembly – Element](../ide/code-snippets-schema-reference.md#assembly)|Požadovaný element. Obsahuje název sestavení, na které se odkazuje fragment kódu. Musí obsahovat přesně jeden `Assembly` prvek `Reference` elementu.|  
|[URL Element](../ide/code-snippets-schema-reference.md#url)|Volitelný element. Obsahuje adresu URL s dalšími informacemi o odkazovaném sestavení. Může být žádný nebo jeden `Url` prvky `Reference` elementu.|  
  
|Nadřazený element|Popis|  
|--------------------|-----------------|  
|[References – Element](../ide/code-snippets-schema-reference.md#references)|Element pro seskupení `Reference` elementy.|  
  
##  <a name="references"></a> References – Element  
 Seskupuje jednotlivé `Reference` elementy.  
  
> [!NOTE]
>  `References` Element je podporována pouze pro projekty jazyka Visual Basic.  
  
```xml  
<References>  
    <Reference>... </Reference>  
</References>  
```  
  
|Podřízený element|Popis|  
|-------------------|-----------------|  
|[Reference – Element](../ide/code-snippets-schema-reference.md#reference)|Volitelný element. Obsahuje informace o odkazech na sestavení pro fragment kódu. Může být nula nebo více `Reference` prvky `References` elementu.|  
  
|Nadřazený element|Popis|  
|--------------------|-----------------|  
|[Snippet Element](../ide/code-snippets-schema-reference.md#snippet)|Obsahuje odkazy, direktivy import, deklarace a kód fragmentu kódu.|  
  
##  <a name="shortcut"></a> Shortcut Element  
 Určuje textovou zkratku, pomocí níž lze fragment kódu vložit. Textová hodnota elementu `Shortcut` element může obsahovat jenom alfanumerické znaky, spojovníky (-) a podtržítka (_).  
  
> [!CAUTION]
>  _ a – nejsou podporované znaky pro zkratky fragmentu kódu v jazyce C++.  
  
```xml  
<Shortcut>  
    Shortcut Text  
</Shortcut>  
```  
  
|Nadřazený element|Popis|  
|--------------------|-----------------|  
|[Header Element](../ide/code-snippets-schema-reference.md#header)|Obsahuje obecné informace o fragmentu kódu.|  
  
 Textová hodnota je volitelná. Tento text slouží jako zkratka pro vkládání fragmentů kódu.  
  
##  <a name="snippet"></a> Snippet Element  
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
|[Code – Element](../ide/code-snippets-schema-reference.md#code)|Požadovaný element. Určuje kód, který chcete vložit do souboru dokumentace. Musí obsahovat přesně jeden `Code` prvek `Snippet` elementu.|  
|[Declarations Element](../ide/code-snippets-schema-reference.md#declarations)|Volitelný element. Určuje literály a objekty tvořící části fragmentu kódu, které lze upravovat. Může být žádný nebo jeden `Declarations` prvky `Snippet` elementu.|  
|[Imports Element](../ide/code-snippets-schema-reference.md#imports)|Volitelný element. Seskupuje jednotlivé `Import` elementy. Může být žádný nebo jeden `Imports` prvky `Snippet` elementu.|  
||Volitelný element. Seskupuje jednotlivé `Reference` elementy. Může být žádný nebo jeden `References` prvky `Snippet` elementu.|  
  
|Nadřazený element|Popis|  
|--------------------|-----------------|  
|[CodeSnippet Element](../ide/code-snippets-schema-reference.md#codesnippet)|Umožňuje zadat záhlaví a jeden nebo více fragmentů kódu technologie IntelliSense, které lze vložit do souborů kódu sady Visual Studio.|  
  
##  <a name="snippettype"></a> Snippettype – Element  
 Určuje, jak sada Visual Studio vloží fragment kódu.  
  
```xml  
<SnippetType>  
    SurroundsWith/Expansion  
<SnippetType>  
```  
  
|Nadřazený element|Popis|  
|--------------------|-----------------|  
|[Snippettypes – Element](../ide/code-snippets-schema-reference.md#snippettypes)|Skupiny `SnippetType` elementy.|  
  
 Textová hodnota musí být jedna z následujících hodnot:  
  
-   `SurroundsWith`: umožňuje umístit kolem vybrané části kódu fragment kódu.  
  
-   `Expansion`: umožňuje fragment kódu vložit na pozici kurzoru.  
  
-   `Refactoring`: Určuje, že fragment kódu je používán během refaktoringu jazyka Visual C#. `Refactoring` nelze použít ve vlastních fragmentech kódu.  
  
##  <a name="snippettypes"></a> Snippettypes – Element  
 Seskupuje jednotlivé `SnippetType` elementy. Pokud `SnippetTypes` prvek není k dispozici, fragment kódu lze vložit na libovolné místo v kódu.  
  
```xml  
<SnippetTypes>  
    <SnippetType>... </SnippetType>  
    <SnippetType>... </SnippetType>  
<SnippetTypes>  
```  
  
|Podřízený element|Popis|  
|-------------------|-----------------|  
|[Snippettype – Element](../ide/code-snippets-schema-reference.md#snippettype)|Volitelný element. Určuje, jak sada Visual Studio vloží fragment kódu do kódu. Může být nula nebo více `SnippetType` prvky `SnippetTypes` elementu.|  
  
|Nadřazený element|Popis|  
|--------------------|-----------------|  
|[Header Element](../ide/code-snippets-schema-reference.md#header)|Určuje obecné informace o fragmentu kódu.|  
  
##  <a name="title"></a> Title Element  
 Určuje název fragmentu kódu. Název uložený v `Title` element fragmentu kódu se zobrazí v **Sběrač fragmentů kódu** a v popisu fragmentu kódu v **Správce fragmentů kódů**.  
  
```xml  
<Title>  
    Code Snippet Title  
<Title>  
```  
  
|Nadřazený element|Popis|  
|--------------------|-----------------|  
|[Header Element](../ide/code-snippets-schema-reference.md#header)|Určuje obecné informace o fragmentu kódu.|  
  
 Je vyžadována textová hodnota. Tento text určuje název fragmentu kódu.  
  
##  <a name="tooltip"></a> ToolTip – Element  
 Popisuje očekávanou hodnotu a použití literálu nebo objektu ve fragmentu kódu. Sada Visual Studio tyto informace zobrazí v popisku při vložení fragmentu kódu do projektu. Text popisku se zobrazí po vložení fragmentu kódu po umístění ukazatele myši na literál nebo objekt.  
  
```xml  
<ToolTip>  
    ToolTip description  
</ToolTip>  
```  
  
|Nadřazený element|Popis|  
|--------------------|-----------------|  
|[Literal Element](../ide/code-snippets-schema-reference.md#literal)|Definuje pole literálu fragmentu kódu, která lze upravovat.|  
|[Object Element](../ide/code-snippets-schema-reference.md#object)|Definuje pole objektu fragment kódu, která lze upravovat.|  
  
 Je vyžadována textová hodnota. Tento text určuje popisek přidružený k objektu nebo literálu ve fragmentu kódu.  
  
##  <a name="type"></a> Type Element  
 Určuje typ objektu. `Object` Element slouží k identifikaci položky, která je potřeba ve fragmentu kódu, ale je pravděpodobně definována mimo samotný fragment kódu. Jako objekty by měly být deklarovány například ovládací prvky modelu Windows Forms, ovládací prvky technologie ASP.NET nebo instance typů. Deklarace objektů vyžadují, aby byl zadán typ, který se použije `Type` elementu.  
  
```xml  
<Type>  
    Type  
</Type>  
```  
  
|Nadřazený element|Popis|  
|--------------------|-----------------|  
|[Object Element](../ide/code-snippets-schema-reference.md#object)|Definuje pole objektu fragment kódu, která lze upravovat.|  
  
 Je vyžadována textová hodnota. Tento text určuje typ objektu.  
  
##  <a name="url"></a> URL Element  
 Určuje adresu URL s dalšími informacemi o odkazovaném sestavení.  
  
> [!NOTE]
>  `Url` Element je podporována pouze pro projekty jazyka Visual Basic.  
  
```xml  
<Url>  
    www.microsoft.com  
</Url>  
```  
  
|Nadřazený element|Popis|  
|--------------------|-----------------|  
|[Reference – Element](../ide/code-snippets-schema-reference.md#reference)|Určuje odkazy na sestavení vyžadované fragmentem kódu.|  
  
 Je vyžadována textová hodnota. Tento text určuje adresu URL s dalšími informacemi o odkazovaném sestavení. Tato adresa URL se zobrazí, pokud odkaz nelze přidat do projektu.  
  
## <a name="see-also"></a>Viz také  
 [Fragmenty kódu](../ide/code-snippets.md)   
 [Návod: Vytvoření fragmentu kódu](../ide/walkthrough-creating-a-code-snippet.md)



