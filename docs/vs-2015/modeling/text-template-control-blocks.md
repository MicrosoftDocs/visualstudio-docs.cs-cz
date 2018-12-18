---
title: Řídicí bloky textových šablon | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- text templates, template code
ms.assetid: bad198b9-57a4-4777-bd5b-ab6336c825f3
caps.latest.revision: 34
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 7531e0ace7a6e2b40d8d17555a9b34cfa0e174fa
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49221205"
---
# <a name="text-template-control-blocks"></a>Řídicí bloky textových šablon
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Řídicí bloky umožňují napsat kód v textové šabloně, aby bylo možné odlišit výstup. Existují tři druhy řídicí bloky, které se rozlišují výhradně podle jejich otvírací závorky:  
  
-   `<# Standard control blocks #>` mohou obsahovat příkazy.  
  
-   `<#= Expression control blocks #>` může obsahovat výrazy.  
  
-   `<#+ Class feature control blocks #>` může obsahovat metody, pole a vlastnosti.  
  
## <a name="standard-control-block"></a>Standardní řídicí blok  
 Standardní řídicí bloky obsahují příkazy. Například následující standardní blok načte názvy všech atributů v dokumentu XML:  
  
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
  
 Můžete vložit prostý text uvnitř složeného příkazu `if` nebo `for`. Tento fragment například generuje řádku výstupu v každé iteraci smyčky:  
  
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
>  Vždy pomocí {...} pro vymezení vnořených příkazů, které obsahují Vložit prostý text. Následující příklad nemusí fungovat správně:  
>   
>  `<# if (ShouldPrint) #> Some text. -- WRONG`  
>   
>  Místo toho by měl obsahovat {složené závorky}, následujícím způsobem:  
  
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
 Řídicí bloky výrazu jsou používány pro kód, který poskytuje řetězců, které mají být zapsána do výstupního souboru. Například v příkladu výše, můžete vytisknout názvy atributů do výstupního souboru úpravou blok kódu:  
  
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
  
## <a name="class-feature-control-block"></a>Řídicí blok s funkcí třídy  
 Řídicí bloky s funkcí třídy slouží k přidání metody, vlastnosti, pole nebo dokonce vnořené třídy do textové šablony. Nejběžnější použití nástroje bloky s funkcí třídy je stanovit pomocných funkcí pro kód v ostatních částech textové šablony. Například následující blok funkcí třídy počáteční písmeno názvu atributu (nebo, pokud název obsahuje mezery, převede první písmena všech slov):  
  
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
>  Řídicí blok funkce třídy nesmí následovat standardní řídicí bloky ve stejném souboru šablony. Ale toto omezení se nevztahuje na výsledek použití `<#@include#>` direktivy. Každý vkládaného souboru může mít standardními bloky a bloky s funkcí třídy.  
  
 Můžete vytvořit funkci, která generuje výstup s využitím vkládání služby bloky textu a výraz uvnitř řídicí blok funkcí třídy. Příklad:  
  
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
  
 Tuto funkci lze volat z bloku standard nebo z jiného blok funkcí třídy:  
  
```  
<# foreach (Attribute attribute in item.Attributes)  
{  
  OutputFixedAttributeName(attribute.Name);  
}  
#>  
```  
  
## <a name="how-to-use-control-blocks"></a>Jak používat řídicí bloky  
 Veškerý kód ve všech řídicí bloky výrazu and standard s jednou šablonou (včetně veškerý kód v šablonách zahrnuté) je zkombinovat do formuláře `TransformText()` metoda generovaného kódu. (Další informace o včetně jiných textových šablon pomocí `include` direktiv, viz [direktivy textové šablony T4](../modeling/t4-text-template-directives.md).)  
  
 Je třeba mít na paměti následující aspekty při použití řídicí bloky:  
  
-   **Jazyk.** Můžete buď C# nebo Visual Basic kód v textové šabloně. Výchozí jazyk je C#, ale můžete zadat pomocí jazyka Visual Basic `language` parametr `template` směrnice. (Další informace o `template` direktiv, viz [direktivy textové šablony T4](../modeling/t4-text-template-directives.md).)  
  
     Jazyk, který použijete v řídicích blocích nemá nic společného jazyka nebo formátování textu, který vygenerujete v textové šabloně. Můžete vygenerovat C# s použitím jazyka Visual Basic kódu nebo naopak versa.  
  
     Můžete použít pouze jeden jazyk v dané textové šablony, včetně všech textových šablon, můžete zahrnout `include` směrnice.  
  
-   **Lokální proměnné.** Vzhledem k tomu, že veškerý kód v ovládacím prvku standard a výraz bloky v textové šablony je generován jako jedinou metodu, měli byste si jisti, že pocházejí nedojde ke konfliktům s názvy místních proměnných. Pokud jsou včetně jiných textových šablon, musí se ujistěte, že názvy proměnných jsou jedinečné ve všech součástí šablony. Jeden způsob, jak zajistit tím je přidání řetězec pro každý název místní proměnné identifikace textové šablony, ve kterém byl deklarován.  
  
     Je také vhodné k inicializaci vaší lokální proměnné na hodnoty rozumné při deklaraci, zejména pokud jsou včetně více textových šablon.  
  
-   **Vnořené řídicí bloky.** Řídicí bloky nemusí být vnořena v sobě navzájem. Blok zadaný ovládací prvek musí ukončit vždy před otevřením jiný. Například následující ukazuje, jak vytisknout nějaký text v bloku výrazu jako součást standardní řídicí blok.  
  
    ```  
    <#   
    int x = 10;  
    while (x-- > 0)  
    {  
    #>  
    <#= x #>  
    <# } #>  
    ```  
  
-   **Refaktoring.** Aby bylo možné zachovat textové šablony krátký a pochopitelnější, důrazně doporučujeme zabránit opakování kódu, které budou zohledňovat opakovaně použitelný kód do pomocné funkce v bloky s funkcí třídy nebo tak, že vytvoříte vlastní textové šablony třídy, která dědí ze třídy Microsoft.VisualStudio.TextTemplating.TextTransformation.



