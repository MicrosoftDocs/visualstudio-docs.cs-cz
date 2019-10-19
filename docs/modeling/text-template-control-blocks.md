---
title: Řídicí bloky textových šablon
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, template code
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 128be69d356b371cc34f5e089df25546428bc83f
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72606079"
---
# <a name="text-template-control-blocks"></a>Řídicí bloky textových šablon
Řídicí bloky umožňují psát kód v textové šabloně, aby se lišil výstup. Existují tři druhy řídicích bloků, které jsou rozlišené levou hranatou závorkou:

- `<# Standard control blocks #>` může obsahovat příkazy.

- `<#= Expression control blocks #>` může obsahovat výrazy.

- `<#+ Class feature control blocks #>` může obsahovat metody, pole a vlastnosti.

## <a name="standard-control-block"></a>Standardní řídicí blok
 Standardní řídicí bloky obsahují příkazy. Například následující standardní blok Získá názvy všech atributů v dokumentu XML:

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

 Do složeného příkazu můžete vložit prostý text, například `if` nebo `for`. Například tento fragment generuje výstupní řádek v každé iteraci smyčky:

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
> Vždycky používat {...} pro vymezení vnořených příkazů, které obsahují vložený prostý text. Následující příklad nemusí správně fungovat:
>
> `<# if (ShouldPrint) #> Some text. -- WRONG`
>
> Místo toho byste měli zahrnout {složené závorky} následujícím způsobem:

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
 Řídicí bloky výrazu jsou používány pro kód, který poskytuje řetězce, které mají být zapsány do výstupního souboru. Například s výše uvedeným příkladem lze vytisknout názvy atributů do výstupního souboru úpravou bloku kódu následujícím způsobem:

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
 Pomocí řídicích bloků funkcí třídy lze přidat do textové šablony metody, vlastnosti, pole nebo dokonce vnořené třídy. Nejběžnějším použitím bloků funkcí třídy je poskytnutí pomocných funkcí pro kód v jiných částech textové šablony. Například následující blok funkce třídy na velká písmena první písmeno názvu atributu (nebo, pokud název obsahuje prázdné znaky, má na velká písmena první písmeno každého slova):

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
> Řídicí blok funkce třídy nesmí být následován standardními řídicími bloky ve stejném souboru šablony. Toto omezení se ale nevztahuje na výsledek použití direktiv `<#@include#>`. Každý zahrnutý soubor může mít standardní bloky následované bloky funkcí třídy.

 Můžete vytvořit funkci, která generuje výstup vložením textu a bloků výrazů do řídicího bloku funkce třídy. Příklad:

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

 Tuto funkci můžete zavolat ze standardního bloku nebo z jiného bloku funkce třídy:

```
<# foreach (Attribute attribute in item.Attributes)
{
  OutputFixedAttributeName(attribute.Name);
}
#>
```

## <a name="how-to-use-control-blocks"></a>Používání řídicích bloků
 Veškerý kód ve všech řídicích blocích standardní a ovládací prvky výrazu v jedné šabloně (včetně veškerého kódu v zahrnutých šablonách) je kombinována za účelem vytvoření metody `TransformText()` generovaného kódu. (Další informace o zahrnutí textových šablon s direktivou `include` naleznete v tématu [direktivy textové šablony T4](../modeling/t4-text-template-directives.md).)

 Při používání řídicích bloků byste měli mít na paměti následující skutečnosti:

- **Language.** V textové šabloně můžete C# použít buď kód, nebo Visual Basic. Výchozí jazyk je C#, ale můžete zadat Visual Basic s parametrem `language` direktivy `template`. (Další informace o direktivě `template` naleznete v tématu [direktivy textové šablony T4](../modeling/t4-text-template-directives.md).)

     Jazyk, který používáte v řídicích blocích, nemá žádnou akci s jazykem nebo formátem textu, který vygenerujete v textové šabloně. Můžete vygenerovat C# pomocí Visual Basicho kódu nebo naopak.

     V dané textové šabloně můžete použít jenom jeden jazyk, včetně všech textových šablon, které zahrnete do direktivy `include`.

- **Místní proměnné.** Vzhledem k tomu, že veškerý kód ve standardním a řídicím bloku výrazu v textové šabloně je vygenerován jako jediná metoda, měli byste se ujistit, že nejsou v konfliktu s názvy místních proměnných. Pokud zahrnujete další textové šablony, je nutné zajistit, aby názvy proměnných byly v rámci všech zahrnutých šablon jedinečné. Jedním ze způsobů, jak to zajistit, je přidat řetězec k jednotlivým názvům místních proměnných identifikující textovou šablonu, ve které byla deklarována.

     Je také vhodné inicializovat místní proměnné tak, aby rozumné hodnoty, když je deklarujete, zejména v případě, že zahrnete více textových šablon.

- **Vnořování řídicích bloků.** Řídicí bloky nesmí být vnořené uvnitř sebe. Před otevřením jiného řídicího bloku je nutné vždy ukončit daný ovládací prvek. Následující příklad ukazuje, jak vytisknout nějaký text v bloku výrazu jako součást standardního řídicího bloku.

    ```
    <#
    int x = 10;
    while (x-- > 0)
    {
    #>
    <#= x #>
    <# } #>
    ```

- **Refaktoring.** Aby vaše textové šablony byly krátké a srozumitelné, důrazně doporučujeme vyhnout se opakovanému kódu, a to tak, že použijete opakovaně použitelný kód na pomocné funkce v blocích funkcí třídy nebo vytvoříte vlastní třídu textových šablon, která dědí z třídy Microsoft. VisualStudio. TextTemplating. TextTransformation.