---
title: Tvorba textové šablony T4
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, syntax
- text templates, guide
- text templates, functions that generate text
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 0d697f1fed2a7b17862ff4c6f72488674859f754
ms.sourcegitcommit: 768d7877fe826737bafdac6c94c43ef70bf45076
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/02/2018
ms.locfileid: "50967295"
---
# <a name="writing-a-t4-text-template"></a>Tvorba textové šablony T4
Textová šablona obsahuje text, který z ní bude vygenerován. Například šablonu, která vytvoří webovou stránku bude obsahovat "\<html >..." a všechny ostatní standardní části stránky HTML. Do šablony jsou *řídicí bloky*, což jsou fragmenty kódu programu. Řídicí bloky poskytují různé hodnoty a umožňují, aby části textu byly podmíněné a opakované.

 Tato struktura usnadňuje vývoj šablon, protože lze začít s prototypem generovaného souboru a postupně vkládat řídicí bloky, které změní výsledek.

 Textové šablony se skládají z těchto částí:

-   **Direktivy** – prvky, které určují způsob zpracování šablony.

-   **Textové bloky** – obsah, který je zkopírován přímo do výstupu.

-   **Řídicí bloky** – programový kód, který do textu vloží hodnoty proměnných a řídí podmíněné nebo opakované části textu.

Pokud chcete vyzkoušet příklady v tomto tématu, zkopírujte je do souboru šablony podle popisu v [vytvoření kódu v době návrhu pomocí textových šablon T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md). Po úpravě souboru šablony jej uložte a poté zkontrolujte výstupní **.txt** souboru.

## <a name="directives"></a>Direktivy
 Direktivy textové šablony poskytují obecné pokyny modulu šablon textu o tom, jak generovat kód transformace a výstupní soubor.

 Například následující direktiva určuje, že výstupní soubor má mít příponu .txt:

```
<#@ output extension=".txt" #>
```

 Další informace o direktivách najdete v tématu [direktivy textové šablony T4](../modeling/t4-text-template-directives.md).

## <a name="text-blocks"></a>Bloky textu
 Blok textu vloží text přímo do výstupního souboru. Pro bloky textu neexistuje žádné zvláštní formátování. Například následující textová šablona vytvoří textový soubor, který obsahuje slovo „Hello“:

```
<#@ output extension=".txt" #>
Hello
```

## <a name="control-blocks"></a>Řídicí bloky
 Řídicí bloky jsou části programového kódu, které slouží k transformaci šablon. Výchozí jazyk je C#, ale chcete-li použít jazyk [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)], lze tuto direktivu napsat na začátku souboru:

```
<#@ template language="VB" #>
```

 Jazyk, ve kterém píšete kód v řídicích blocích, nesouvisí s jazykem textu, který je generován.

### <a name="standard-control-blocks"></a>Standardní řídicí bloky
 Standardní řídicí blok je část programového kódu, která generuje část výstupního souboru.

 V souboru šablony lze používat libovolný počet textových bloků se standardními řídicími bloky. Nelze však umístit jeden řídicí blok uvnitř jiného. Každý standardní řídicí blok je ohraničen symboly `<# ... #>`.

 Například následující řídicí blok a blok textu způsobí, že výstupní soubor bude obsahovat řádek „0, 1, 2, 3, 4 Hello!“:

```
<#
    for(int i = 0; i < 4; i++)
    {
        Write(i + ", ");
    }
    Write("4");
#> Hello!
```

 Namísto použití explicitních příkazů `Write()` lze text a kód prokládat. Následující příklad vytiskne "Hello!" čtyřikrát:

```
<#
    for(int i = 0; i < 4; i++)
    {
#>
Hello!
<#
    }
#>
```

 Blok textu lze vložit všude, kde je v kódu povolen příkaz `Write();`.

> [!NOTE]
>  Při vložení textového bloku do složeného příkazu, jako je například smyčky nebo podmínky, vždy používejte složené závorky {...} Chcete-li obsahující textový blok.

### <a name="expression-control-blocks"></a>Řídicí bloky výrazu
 Řídicí blok výrazu vyhodnotí výraz a převede jej na řetězec. Ten je vložen do výstupního souboru.

 Řídicí bloky výrazu jsou odděleny symboly `<#= ... #>`.

 Například následující řídicí blok způsobí, že výstupní soubor obsahuje text „5“:

```
<#= 2 + 3 #>
```

 Všimněte si, že počáteční symbol má tři znaky „<#=“.

 Výraz může obsahovat jakoukoli proměnnou, která je v rozsahu. Tento blok například vytiskne řádky s čísly:

```
<#@ output extension=".txt" #>
<#
    for(int i = 0; i < 4; i++)
    {
#>
This is hello number <#= i+1 #>: Hello!
<#
    }
#>
```

### <a name="class-feature-control-blocks"></a>Řídicí bloky s funkcí třídy
 Řídicí blok s funkcí třídy definuje vlastnosti, metody nebo jiný kód, který by neměl být zařazen do hlavní transformace. Bloky s funkcí třídy jsou často používány pro pomocné funkce.  Obvykle jsou bloky s funkcí třídy umístěny do samostatných souborů tak, aby mohly být [zahrnuté](#Include) ve více než jedné textové šablony.

 Řídicí bloky s funkcí třídy jsou ohraničeny pomocí symbolů `<#+ ... #>`.

 Například následující soubor šablony deklaruje a používá metodu:

```
<#@ output extension=".txt" #>
Squares:
<#
    for(int i = 0; i < 4; i++)
    {
#>
    The square of <#= i #> is <#= Square(i+1) #>.
<#
    }
#>
That is the end of the list.
<#+   // Start of class feature block
private int Square(int i)
{
    return i*i;
}
#>
```

 Funkce třídy musí být umístěny na konci souboru, ve kterém jsou zapsány. Lze však provést `<#@include#>` souboru, který obsahuje funkce třídy, i když je direktiva `include` následována standardními bloky a textem.

 Další informace o řídicích blocích naleznete v tématu [řídicí bloky textových šablon](../modeling/text-template-control-blocks.md).

### <a name="class-feature-blocks-can-contain-text-blocks"></a>Bloky s funkcí třídy mohou obsahovat textové bloky.
 Lze zapsat metodu, která generuje text. Příklad:

```
List of Squares:
<#
   for(int i = 0; i < 4; i++)
   {  WriteSquareLine(i); }
#>
End of list.
<#+   // Class feature block
private void WriteSquareLine(int i)
{
#>
   The square of <#= i #> is <#= i*i #>.
<#+
}
#>
```

 Metodu, která generuje text, je vhodné umístit do samostatného souboru, který může obsahovat více než jedna šablona.

## <a name="using-external-definitions"></a>Použití externích definic

### <a name="assemblies"></a>Sestavení
 Bloky kódu šablony mohou používat typy, které jsou definovány nejčastěji používanými sestaveními rozhraní .NET, jako například System.dll. Kromě toho můžete odkazovat na jiné sestavení rozhraní .NET nebo na vlastní sestavení. Lze zadat cestu nebo silný název sestavení:

```
<#@ assembly name="System.Xml" #>
```

 Měli byste používat absolutní názvy cest nebo v názvu cesty použít standardní názvy maker. Příklad:

```
<#@ assembly name="$(SolutionDir)library\MyAssembly.dll" #>
```

 Direktiva assembly nemá žádný účinek [Předzpracované textové šablony](../modeling/run-time-text-generation-with-t4-text-templates.md).

 Další informace najdete v tématu [T4 – Direktiva Assembly](../modeling/t4-assembly-directive.md).

### <a name="namespaces"></a>Jmenné prostory
 Direktiva import je stejná jako klauzule `using` v jazyce C# nebo klauzule `imports` v jazyce Visual Basic. Umožňuje odkazovat na typy v kódu bez použití plně kvalifikovaného názvu:

```
<#@ import namespace="System.Xml" #>
```

 Můžete použít tolik direktiv `assembly` a `import`, kolik chcete. Je nutné je umístit před textové a řídicí bloky.

 Další informace najdete v tématu [T4 – Direktiva Import](../modeling/t4-import-directive.md).

### <a name="Include"></a> Vložení kódu a textu
 Direktiva `include` vloží text z jiného souboru šablony. Tato direktiva například vloží obsah souboru `test.txt`.

```
<#@ include file="c:\test.txt" #>
```

 Vložený obsah se zpracuje téměř jako kdyby byl součástí textové šablony, která ho vkládá. Můžete však vložit soubor obsahující blok s funkcí třídy `<#+...#>`, i když za direktivou include následuje běžný text a standardní řídicí bloky.

 Další informace najdete v tématu [T4 – direktiva zahrnují](../modeling/t4-include-directive.md).

### <a name="utility-methods"></a>Pomocné metody
 Existuje několik metod, jako je `Write()`, které jsou v řídicím bloku vždy k dispozici. Patří sem metody, které napomáhají odsadit výstup a oznamovat chyby.

 Lze také napsat vlastní sadu pomocných metod.

 Další informace najdete v tématu [pomocné metody textových šablon](../modeling/text-template-utility-methods.md).

## <a name="transforming-data-and-models"></a>Transformace dat a modelů
 Nejužitečnějším použitím textových šablon je generování materiálu na základě obsahu zdroje, jako je model, databáze nebo datový soubor. Šablona extrahuje a přeformátuje data. Pomocí sady šablon lze tyto zdroje transformovat do více souborů.

 Existuje několik způsobů čtení zdrojového souboru.

 **Čtení souboru v textové šabloně**. Toto je nejjednodušší způsob, jak vložit data do šablony:

```
<#@ import namespace="System.IO" #>
<# string fileContent = File.ReadAllText(@"C:\myData.txt"); ...
```

 **Načtení souboru jako modelu navigaci**. Výkonnější metodou je načíst data jako model, kterým kód textové šablony může procházet. Lze například načíst soubor XML a procházet jím pomocí výrazů XPath. Můžete také použít [xsd.exe](http://go.microsoft.com/fwlink/?LinkId=178765) k vytvoření sadu tříd, pomocí kterých můžete číst XML data.

 **Úprava souboru modelu ve formuláři nebo diagramu.** [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] poskytuje nástroje, které umožňují upravit model, jako je diagram nebo formulář Windows. Můžete tak tento model snáze prodiskutovat s uživateli generované aplikace. [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] také vytvoří sadu typově silných tříd, které odrážejí strukturu modelu. Další informace najdete v tématu [generování kódu z jazyka specifického pro doménu](../modeling/generating-code-from-a-domain-specific-language.md).

### <a name="relative-file-paths-in-design-time-templates"></a>Relativní cesty k souborům v návrhových šablonách
 V [návrhová textová šablona](../modeling/design-time-code-generation-by-using-t4-text-templates.md), pokud chcete odkazovat na soubor v relativním umístění vzhledem k textu šablony, použijte `this.Host.ResolvePath()`. Je také nutné nastavit hodnotu `hostspecific="true"` v direktivě `template`:

```
<#@ template hostspecific="true" language="C#" #>
<#@ output extension=".txt" #>
<#@ import namespace="System.IO" #>
<#
 // Find a path within the same project as the text template:
 string myFile = File.ReadAllText(this.Host.ResolvePath("MyFile.txt"));
#>
Content of MyFile.txt is:
<#= myFile #>
```

Lze také získat další služby, které jsou poskytovány tímto hostitelem. Další informace najdete v tématu [přístup k sadě Visual Studio nebo k jiným hostitelům z šablony](/previous-versions/visualstudio/visual-studio-2010/gg604090\(v\=vs.100\)).

### <a name="design-time-text-templates-run-in-a-separate-appdomain"></a>Návrhové textové šablony běží v oddělené doméně AppDomain.

 Byste měli vědět, který [návrhová textová šablona](../modeling/design-time-code-generation-by-using-t4-text-templates.md) běží v doméně AppDomain, která je oddělená od hlavní aplikace. Ve většině případů to není důležité, ale v některých složitých případech lze narazit na omezení. Pokud například chcete předat data do nebo ze šablony ze samostatné služby, musí tato služba poskytovat serializovatelné rozhraní API.

 (To neplatí u [šablony textu za běhu](../modeling/run-time-text-generation-with-t4-text-templates.md), která obsahuje kód, který je sestaven společně se zbytkem kódu.)

## <a name="editing-templates"></a>Úpravy šablon
 Speciální editory textových šablon lze stáhnout z online galerie správce rozšíření. Na **nástroje** nabídky, klikněte na tlačítko **Správce rozšíření**. Klikněte na tlačítko **Online galerie**a potom použijte nástroj hledání.

## <a name="related-topics"></a>Související témata

|Úloha|Téma|
|-|-|
|Vytvoření šablony|[Pokyny pro zápis textových šablon T4](../modeling/guidelines-for-writing-t4-text-templates.md)|
|Generování textu pomocí kódu programu|[Struktura textové šablony](../modeling/writing-a-t4-text-template.md)|
|Generování souborů v řešení sady Visual Studio.|[Vytvoření kódu v době návrhu pomocí textových šablon T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md)|
|Spuštění generování textu mimo sadu Visual Studio.|[Generování souborů pomocí nástroje TextTransform](../modeling/generating-files-with-the-texttransform-utility.md)|
|Transformujte svá data ve formě jazyka specifického pro doménu.|[Vytváření kódu z jazyka specifického pro doménu](../modeling/generating-code-from-a-domain-specific-language.md)|
|Procesory direktiv pro transformaci zdrojích dat zápisu.|[Přizpůsobení transformace textu T4](../modeling/customizing-t4-text-transformation.md)|
