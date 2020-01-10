---
title: T4 – direktiva šablony | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 2b0a8e04-6fee-4c6c-b086-e49fc728a3ed
caps.latest.revision: 12
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 02ab48e2fcd014508277a9bc361cde65d62ef38c
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/10/2020
ms.locfileid: "75850793"
---
# <a name="t4-template-directive"></a>T4 – direktiva Template
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Šablona textu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] T4 obvykle začíná direktivou `template`, která určuje, jak má být šablona zpracována. V textové šabloně a v žádném souboru, který zahrnuje, by neměla existovat více než jedna direktiva šablony.

 Obecný přehled o psaní textových šablon najdete v tématu [Vytvoření textové šablony T4](../modeling/writing-a-t4-text-template.md).

## <a name="using-the-template-directive"></a>Použití direktivy šablony

```
<#@ template [language="VB"] [compilerOptions="options"] [culture="code"] [debug="true"] [hostspecific="true"] [inherits="templateBaseClass"] [visibility="internal"] [linePragmas="false"] #>
```

 Direktiva `template` má několik atributů, které umožňují určit různé aspekty transformace. Všechny tyto atributy jsou volitelné.

## <a name="compileroptions-attribute"></a>Atribut compilerOptions
 Příklad: `compilerOptions="optimize+"`

 Platné hodnoty: všechny platné možnosti kompilátoru. Další informace naleznete v tématu [ C# možnosti kompilátoru uvedené podle kategorie](https://msdn.microsoft.com/library/96437ecc-6502-4cd3-b070-e9386a298e83) a [Visual Basic možnosti kompilátoru uvedené podle kategorie](https://msdn.microsoft.com/library/fbe36f7a-7cfa-4f77-a8d4-2be5958568e3).

 U šablon běhu (předzpracovaných) se ignoruje.

 Tyto možnosti jsou aplikovány, pokud byla šablona převedena do [!INCLUDE[csprcs](../includes/csprcs-md.md)] nebo [!INCLUDE[vb_current_short](../includes/vb-current-short-md.md)]a výsledný kód je zkompilován.

## <a name="culture-attribute"></a>Atribut culture
 Příklad: `culture="de-CH"`

 Platné hodnoty: "", invariantní jazyková verze, což je výchozí hodnota.

 Jazyková verze vyjádřená jako řetězec ve formátu xx-XX. Příklad: en US, ja-JP, de-CH, de-DE. Další informace najdete v tématu <xref:System.Globalization.CultureInfo?displayProperty=fullName>.

 Atribut culture určuje jazykovou verzi použitou při převedení bloku výrazu na text.

## <a name="debug-attribute"></a>Atribut debug
 Příklad:

```
debug="true"
```

 Platné hodnoty: `true, false`. Výchozí hodnota je false.

 Pokud je atribut `debug` `true`, soubor zprostředkujícího kódu bude obsahovat informace, které umožní ladicímu programu identifikovat přesnější pozici v šabloně, kde došlo k přerušení nebo výjimce.

 Pro šablony návrhu se soubor mezilehlého kódu zapíše do adresáře **% TEMP%** .

 Chcete-li v ladicím programu spustit šablonu pro dobu návrhu, uložte textovou šablonu a pak otevřete místní nabídku textové šablony v Průzkumník řešení a zvolte možnost **ladit šablonu T4**.

## <a name="hostspecific-attribute"></a>Atribut hostspecific
 Příklad:

```
hostspecific="true"
```

 Platné hodnoty: `true, false, trueFromBase`. Výchozí hodnota je false.

 Pokud nastavíte hodnotu tohoto atributu na `true`, vlastnost s názvem `Host` je přidána do třídy vygenerované vaší textovou šablonou. Vlastnost je odkaz na hostitele transformačního modulu a je deklarována jako [ITextTemplatingEngineHost](/previous-versions/visualstudio/visual-studio-2012/bb126505(v=vs.110)). Pokud jste definovali vlastního hostitele, lze jej přetypovat na typ vlastního hostitele.

 Protože typ této vlastnosti závisí na typu hostitele, je užitečný pouze při psaní textové šablony, která funguje pouze s konkrétním hostitelem. Vztahuje se na [šablony návrhu](../modeling/design-time-code-generation-by-using-t4-text-templates.md), ale ne na šablony v době [běhu](../modeling/run-time-text-generation-with-t4-text-templates.md).

 Když `hostspecific` `true` a používáte [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], můžete `this.Host` pro přístup k [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] funkcím přetypování na IServiceProvider. Pomocí `Host.ResolvePath(filename)` lze také získat absolutní cestu k souboru v projektu. Příklad:

```csharp
<#@ template debug="false" hostspecific="true" language="C#" #>
<#@ output extension=".txt" #>
<#@ assembly name="EnvDTE" #>
<#@ import namespace="EnvDTE" #>
<#@ import namespace="System.IO" #>
<# // Get the Visual Studio API as a service:
 DTE dte = ((IServiceProvider)this.Host).GetCOMService(typeof(DTE)) as DTE;
#>
Number of projects in this solution: <#=  dte.Solution.Projects.Count #>

<#
 // Find a path within the current project:
 string myFile = File.ReadAllText(this.Host.ResolvePath("MyFile.txt"));
#>
Content of myFile is:
<#= myFile #>

```

 Použijete-li atributy `inherits` a `hostspecific` společně, zadejte Host = "trueFromBase" v odvozené třídě a host = "true" v základní třídě. Tím se zabrání dvojitá definice vlastnosti `Host` ve vygenerovaném kódu.

## <a name="language-attribute"></a>Atribut language
 Příklad: `language="VB"`

 Platné hodnoty: `C#` (výchozí)

 `VB`

 Atribut Language určuje jazyk ([!INCLUDE[vbprvb](../includes/vbprvb-md.md)] nebo [!INCLUDE[csprcs](../includes/csprcs-md.md)]), který se má použít pro zdrojový kód v blocích příkazů a výrazu. Soubor mezikódu, ze kterého je výstup vygenerován, bude používat tento jazyk. Tento jazyk nesouvisí s jazykem, který generuje šablona, což může být libovolný typ textu.

 Příklad:

```vb
<#@ template language="VB" #>
<#@ output extension=".txt" #>
Squares of numbers:
<#
  Dim number As Integer
  For number = 1 To 4
#>
  Square of <#= number #> is <#= number * number #>
<#
  Next number
#>

```

## <a name="inherits-attribute"></a>Atribut inherits
 Můžete určit, že programový kód šablony může dědit z jiné třídy, která může být rovněž vygenerována z textové šablony.

### <a name="inheritance-in-a-run-time-preprocessed-text-template"></a>Dědičnost v textových šablonách běhu (předzpracovaných)
 Dědičnost lze použít mezi textovými šablonami běhu k vytvoření základní šablony, která má několik odvozených variant. Šablony modulu runtime jsou ty, které mají vlastnost **vlastní nástroj** nastavenou na **TextTemplatingFilePreprocessor**. Šablona běhu generuje kód, který lze v aplikaci volat pro vytvoření textu definovaného v šabloně. Další informace najdete v tématu [generování textu v době běhu s textovými šablonami T4](../modeling/run-time-text-generation-with-t4-text-templates.md).

 Pokud nezadáte atribut `inherits`, základní třída a odvozená třída budou vygenerovány z textové šablony. Zadáte-li atribut `inherits`, je vygenerována pouze odvozená třída. Základní třídu můžete napsat ručně, ale musí poskytovat metody, které jsou používány odvozenou třídou.

 Obvykleji se jako základní třída určuje jiná předzpracovaná šablona. Základní šablona poskytuje běžné bloky textu, které mohou být proloženy textem z odvozených šablon. Můžete použít bloky funkcí třídy `<#+ ... #>` k definování metod, které obsahují textové fragmenty. Do základní šablony lze například umístit rámec výstupního textu a poskytnout tak virtuální metody, které lze v odvozených třídách přepsat:

 Textová šablona běhu (předzpracovaná) BaseTemplate.tt:

```scr
This is the common header.
<#
  SpecificFragment1();
#>
A common central text.
<#
  SpecificFragment2();
#>
This is the common footer.
<#+
  // Declare abstract methods
  protected virtual void SpecificFragment1() { }
  protected virtual void SpecificFragment2() { }
#>

```

 Textová šablona běhu (předzpracovaná) DerivedTemplate1.tt:

```csharp
<#@ template language="C#" inherits="BaseTemplate" #>
<#
  // Run the base template:
  base.TransformText();
#>
<#+
// Provide fragments specific to this derived template:
protected override void SpecificFragment1()
{
#>
   Fragment 1 for DerivedTemplate1
<#+
}
protected override void SpecificFragment2()
{
#>
   Fragment 2 for DerivedTemplate1
<#+
}
#>

```

 Kód aplikace pro vyvolání DerivedTemplate1:

```csharp
Console.WriteLine(new DerivedTemplate().TransformText());
```

 Výsledný výstup:

```
This is the common header.
   Fragment 1 for DerivedTemplate1
A common central text.
   Fragment 2 for DerivedTemplate1
This is the common footer.
```

 Základní a odvozené třídy lze sestavit v různých projektech. Nezapomeňte k odkazům odvozených projektů přidat základní projekt nebo sestavení.

 Jako základní třídu lze také použít běžnou ručně psanou třídu. Základní třída musí poskytovat metody používané v odvozené třídě.

> [!WARNING]
> Použijete-li atributy `inherits` a `hostspecific` společně, zadejte hostspecific = "trueFromBase" v odvozené třídě a host = "true" v základní třídě. Tím se zabrání dvojitá definice vlastnosti `Host` ve vygenerovaném kódu.

### <a name="inheritance-in-a-design-time-text-template"></a>Dědičnost v textové šabloně návrhu
 Textová šablona v době návrhu je soubor, pro který je **vlastní nástroj** nastaven na **hodnotu TextTemplatingFileGenerator**. Šablona generuje výstupní soubor kódu nebo textu, který tvoří součást projektu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Při vygenerování výstupního souboru je šablona nejdříve přeložena do souboru programového mezikódu, který není obvykle vidět. Atribut `inherits` určuje základní třídu pro tento zprostředkující kód.

 Pro textovou šablonu návrhu můžete zadat libovolnou základní třídu, která je odvozena od <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation?displayProperty=fullName>. Použijte direktivu `<#@assembly#>` pro načtení sestavení nebo projektu, který obsahuje základní třídu.

 Další informace najdete v [blogu Gareth Novák v tématu "dědičnost v textových šablonách"](https://blogs.msdn.microsoft.com/garethj/2011/01/03/vs2010-sp1-t4-template-inheritance-part-i-sample-metadata/).

## <a name="linepragmas-attribute"></a>Atribut LinePragmas
 Příklad: `linePragmas="false"`

 Platné hodnoty: `true` (výchozí)

 `false`

 Nastavení tohoto atributu na hodnotu false odstraní značky, které identifikují čísla řádků ve vygenerovaném kódu. To znamená, že kompilátor nahlásí jakékoli chyby pomocí čísel řádků generovaného kódu. To vám dává další možnosti ladění, protože se můžete rozhodnout pro ladění textové šablony nebo vygenerovaného kódu.

 Tento atribut může také pomoci, pokud absolutní názvy souborů v direktivách programu způsobují rušivá sloučení ve správě zdrojového kódu.

## <a name="visibility-attribute"></a>Atribut visibility
 Příklad: `visibility="internal"`

 Platné hodnoty: `public` (výchozí)

 `internal`

 V textové šabloně běhu se tímto nastavuje atribut visibility vygenerované třídy. Ve výchozím nastavení je třída součástí veřejného rozhraní API vašeho kódu, ale nastavením `visibility="internal"` můžete zajistit, že pouze váš kód může použít třídu pro generování textu.
