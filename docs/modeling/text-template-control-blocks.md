---
title: Řídicí bloky textových šablon
description: Přečtěte si o řídicích blocích textových šablon a o tom, jak vám řídicí bloky umožňují psát kód v textové šabloně, abyste mohli měnit výstup.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, template code
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 90a4efea7d37b83d3d5ff7a085abcf3439d99263
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2021
ms.locfileid: "112388721"
---
# <a name="text-template-control-blocks"></a>Řídicí bloky textových šablon
Řídicí bloky umožňují psát kód v textové šabloně za účelem odlišování výstupu. Existují tři druhy řídicích bloků, které se rozlišují pomocí jejich otevíracích závorek:

- `<# Standard control blocks #>` může obsahovat příkazy .

- `<#= Expression control blocks #>` může obsahovat výrazy.

- `<#+ Class feature control blocks #>` může obsahovat metody, pole a vlastnosti.

## <a name="standard-control-block"></a>Standardní řídicí blok
 Standardní řídicí bloky obsahují příkazy . Například následující standardní blok získá názvy všech atributů v dokumentu XML:

```
<#@ assembly name="System.Xml.dll" #>
<#@ import namespace="System.Xml" #>

<#
    List<string> allAttributes = new List<string>();
    XmlDocument xDoc = new XmlDocument();
    xDoc.Load(@"E:\CSharp\Overview.xml");
    XmlAttributeCollection attributes = xDoc.Attributes;
    if (attributes.Count > 0)
    {
       foreach (XmlAttribute attr in attributes)
       {
           allAtributes.Add(attr.Name);
       }
     }
#>
```

 Do složeného příkazu, jako je nebo , můžete vložit prostý `if` `for` text. Tento fragment například vygeneruje výstupní řádek v každé iteraci smyčky:

```
<#
       foreach (XmlAttribute attr in attributes)
       {
#>
Found another one!
<#
           allAtributes.Add(attr.Name);
       }
#>
```

> [!WARNING]
> Vždy používejte {...} k oddělení vnořených příkazů, které obsahují vložený prostý text. Následující příklad nemusí fungovat správně:
>
> `<# if (ShouldPrint) #> Some text. -- WRONG`
>
> Místo toho byste měli zahrnout {složené závorky}, a to následujícím způsobem:

```

<#
 if (ShouldPrint)
 {   //  "{" REQUIRED
#>
Some text.
<#
 }
#>
```

## <a name="expression-control-block"></a>Řídicí blok výrazu
 Řídicí bloky výrazů se používají pro kód, který poskytuje řetězce pro zápis do výstupního souboru. Například s výše uvedeným příkladem můžete vytisknout názvy atributů do výstupního souboru úpravou bloku kódu následujícím způsobem:

```
<#
    XmlDocument xDoc = new XmlDocument();
    xDoc.Load(@"E:\CSharp\Overview.xml");
    XmlAttributeCollection attributes = xDoc.Attributes;
    if (attributes != null)
    {
       foreach (XmlAttribute attr in attributes)
       {
#><#= attr.Name #><#
       }
    }
#>
```

## <a name="class-feature-control-block"></a>Řídicí blok funkce třídy
 Řídicí bloky funkcí třídy můžete použít k přidání metod, vlastností, polí nebo dokonce vnořených tříd do textové šablony. Nejběžnějším použitím bloků funkcí třídy je poskytování pomocových funkcí pro kód v jiných částech textové šablony. Například následující blok funkce třídy používá velké písmeno prvního písmene názvu atributu (nebo pokud název obsahuje prázdné znaky, zmenšuje první písmeno každého slova velkým písmenem):

```
<#@ import namespace="System.Globalization" #>
```

```
<#+
    private string FixAttributeName(string name)
    {
        return CultureInfo.CurrentCulture.TextInfo.ToTitleCase(name);
    }
#>
```

> [!NOTE]
> Řídicí blok funkce třídy nesmí být následován standardními řídicími bloky ve stejném souboru šablony. Toto omezení se však nevztahuje na výsledek direktiv `<#@include#>` using. Každý zahrnutý soubor může mít standardní bloky následované bloky funkcí třídy.

 Můžete vytvořit funkci, která generuje výstup vložením bloků textu a výrazů do řídicího bloku funkce třídy. Příklad:

```
<#+
    private void OutputFixedAttributeName(string name)
    {
#>
 Attribute:  <#= CultureInfo.CurrentCulture.TextInfo.ToTitleCase(name) #>
<#+  // <<< Notice that this is also a class feature block.
    }
#>
```

 Tuto funkci můžete volat ze standardního bloku nebo z jiného bloku funkcí třídy:

```
<# foreach (Attribute attribute in item.Attributes)
{
  OutputFixedAttributeName(attribute.Name);
}
#>
```

## <a name="how-to-use-control-blocks"></a>Jak používat řídicí bloky
 Veškerý kód ve všech standardních řídicích blocích a řídicích blocích výrazů v jedné šabloně (včetně veškerého kódu v zahrnutých šablonách) se zkombinuje a vytvoří metodu `TransformText()` generovaného kódu. (Další informace o zahrnutí dalších textových šablon pomocí `include` direktivy najdete v tématu [Direktivy textových](../modeling/t4-text-template-directives.md)šablon T4 .)

 Při používání řídicích bloků byste měli mít na paměti následující skutečnosti:

- **Jazyk.** V textové šabloně můžete Visual Basic kód jazyka C#. Výchozí jazyk je C#, ale můžete Visual Basic pomocí `language` parametru `template` direktivy . (Další informace o direktivě `template` najdete v tématu Direktivy textové šablony [T4](../modeling/t4-text-template-directives.md).)

     Jazyk, který používáte v řídicích blocích, nemá nic společného s jazykem nebo formátem textu vygenerované v textové šabloně. Jazyk C# můžete vygenerovat pomocí Visual Basic kódu nebo naopak.

     V dané textové šabloně můžete použít pouze jeden jazyk, včetně všech textových šablon, které s `include` direktivou zahrníte.

- **Místní proměnné.** Vzhledem k tomu, že se veškerý kód v řídicích blocích standardu a výrazu v textové šabloně generuje jako jedna metoda, měli byste se ujistit, že neexistují žádné konflikty s názvy místních proměnných. Pokud zahrnujete další textové šablony, musíte zajistit, aby názvy proměnných byly v rámci všech zahrnutých šablon jedinečné. Jedním ze způsobů, jak to zajistit, je přidat do každého názvu místní proměnné řetězec identifikující textovou šablonu, ve které byla deklarována.

     Je také vhodné inicializovat místní proměnné na rozumné hodnoty, když je deklarujete, zejména pokud začítáte více textových šablon.

- **Vnoření řídicích bloků** Řídicí bloky nemusí být vnořené mezi sebou. Před otevřením dalšího řídicího bloku musíte vždy ukončit daný řídicí blok. Následující příklad ukazuje, jak vytisknout nějaký text v bloku výrazů jako součást standardního řídicího bloku.

    ```
    <#
    int x = 10;
    while (x-- > 0)
    {
    #>
    <#= x #>
    <# } #>
    ```

- **Refactoring.** Aby byly textové šablony krátké a srozumitelné, důrazně doporučujeme vyhnout se opakování kódu tím, že opakovaně použitelný kód začátečník začátečníkům do pomocných funkcí v blocích funkcí třídy nebo vytvořením vlastní třídy textové šablony, která dědí z třídy Microsoft.VisualStudio.TextTemplating.TextTransformation.
