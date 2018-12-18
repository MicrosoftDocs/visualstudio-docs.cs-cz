---
title: T4 – Direktiva Template | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2b0a8e04-6fee-4c6c-b086-e49fc728a3ed
caps.latest.revision: 12
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: dcd11416bc067acaab8855b51969c7e1068e2c97
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49248219"
---
# <a name="t4-template-directive"></a>T4 – direktiva Template
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] textové šablony T4 obvykle začíná `template` – direktiva, která určuje, jak by se měly zpracovat šablonu. V textové šabloně a v žádném souboru, který zahrnuje, by neměla existovat více než jedna direktiva šablony.  
  
 Obecný přehled o psaní textových šablon, naleznete v tématu [vytvoření textové šablony T4](../modeling/writing-a-t4-text-template.md).  
  
## <a name="using-the-template-directive"></a>Použití direktivy šablony  
  
```  
<#@ template [language="VB"] [compilerOptions="options"] [culture="code"] [debug="true"] [hostspecific="true"] [inherits="templateBaseClass"] [visibility="internal"] [linePragmas="false"] #>  
```  
  
 `template` – Direktiva má několik atributů, které vám umožňují určit různé aspekty transformace. Všechny tyto atributy jsou volitelné.  
  
## <a name="compileroptions-attribute"></a>Atribut compilerOptions  
 Příklad:  
 `compilerOptions="optimize+"`  
  
 Platné hodnoty:  
 Všechny platné parametry kompilátoru. Další informace najdete v tématu [jazyka C# možnosti kompilátoru seřazené podle kategorie](http://msdn.microsoft.com/library/96437ecc-6502-4cd3-b070-e9386a298e83) a [jazyka Visual Basic možnosti kompilátoru seřazené podle kategorie](http://msdn.microsoft.com/library/fbe36f7a-7cfa-4f77-a8d4-2be5958568e3).  
  
 U šablon běhu (předzpracovaných) se ignoruje.  
  
 Tyto možnosti se použijí v případě, šablona byla převedena do [!INCLUDE[csprcs](../includes/csprcs-md.md)] nebo [!INCLUDE[vb_current_short](../includes/vb-current-short-md.md)], a výsledný kód je zkompilován.  
  
## <a name="culture-attribute"></a>Atribut culture  
 Příklad:  
 `culture="de-CH"`  
  
 Platné hodnoty:  
 "", invariantní jazyková verze, která je výchozí hodnotou.  
  
 Jazyková verze vyjádřená jako řetězec ve formátu xx-XX. Příklad: en US, ja-JP, de-CH, de-DE. Další informace naleznete v tématu <xref:System.Globalization.CultureInfo?displayProperty=fullName>.  
  
 Atribut culture určuje jazykovou verzi použitou při převedení bloku výrazu na text.  
  
## <a name="debug-attribute"></a>Atribut debug  
 Příklad:  
 ```  
debug="true"  
```  
  
 Platné hodnoty:  
 `true, false`. Výchozí hodnota je false.  
  
 Pokud `debug` atribut je `true`, bude soubor mezikódu obsahovat informace, které umožňují ladicímu programu přesněji určit pozici v šabloně, kde došlo k přerušení nebo výjimek.  
  
 U šablon návrhu bude soubor mezikódu zapsán do vaší **% TEMP %** adresáře.  
  
 Pokud chcete šablonu návrhu spustit v ladicím programu, textovou šablonu uložte pak otevřete místní nabídku textové šablony v Průzkumníku řešení a zvolte **ladit šablonu T4**.  
  
## <a name="hostspecific-attribute"></a>Atribut hostspecific  
 Příklad:  
 ```  
hostspecific="true"  
```  
  
 Platné hodnoty:  
 `true, false, trueFromBase`. Výchozí hodnota je false.  
  
 Pokud nastavíte hodnotu tohoto atributu na `true`, vlastnost s názvem `Host` se přidá do třídy vygenerované textové šablony. Vlastnost je odkazem na hostitelský modul transformace a je deklarován jako <xref:Microsoft.VisualStudio.TextTemplating.ITextTemplatingEngineHost>. Pokud jste definovali vlastního hostitele, lze jej přetypovat na typ vlastního hostitele.  
  
 Protože typ této vlastnosti závisí na typu hostitele, je užitečný pouze při psaní textové šablony, která funguje pouze s konkrétním hostitelem. Se vztahuje na [návrhových šablonách](../modeling/design-time-code-generation-by-using-t4-text-templates.md), ale ne [šablony běhu](../modeling/run-time-text-generation-with-t4-text-templates.md).  
  
 Když `hostspecific` je `true` a používáte [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], můžete přetypovat `this.Host` na IServiceProvider pro přístup k [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] funkce. Můžete také použít `Host.ResolvePath(filename)` k získání absolutní cesty souboru v projektu. Příklad:  
  
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
  
 Pokud používáte `inherits` a `hostspecific` , definujte hostitele = "trueFromBase" v odvozené třídě a host = "true" v základní třídě. To zabraňuje dvojité definici vlastnosti `Host` vlastnost v generovaném kódu.  
  
## <a name="language-attribute"></a>Atribut language  
 Příklad:  
 `language="VB"`  
  
 Platné hodnoty:  
 `C#` (výchozí)  
  
 `VB`  
  
 Atribut language Určuje jazyk ([!INCLUDE[vbprvb](../includes/vbprvb-md.md)] nebo [!INCLUDE[csprcs](../includes/csprcs-md.md)]) pro zdrojový kód v blocích příkazů a výrazů. Soubor mezikódu, ze kterého je výstup vygenerován, bude používat tento jazyk. Tento jazyk nesouvisí s jazykem, který generuje šablona, což může být libovolný typ textu.  
  
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
 Dědičnost lze použít mezi textovými šablonami běhu k vytvoření základní šablony, která má několik odvozených variant. Šablony běhu jsou ty, které mají **Custom Tool** vlastnost nastavena na hodnotu **TextTemplatingFilePreprocessor**. Šablona běhu generuje kód, který lze v aplikaci volat pro vytvoření textu definovaného v šabloně. Další informace najdete v tématu [generování textu za běhu pomocí textových šablon T4](../modeling/run-time-text-generation-with-t4-text-templates.md).  
  
 Pokud nezadáte `inherits` atribut, základní třída a odvozené třídy se generují z textové šablony. Pokud zadáte `inherits` se generuje atribut, pouze odvozené třídy. Základní třídu můžete napsat ručně, ale musí poskytovat metody, které jsou používány odvozenou třídou.  
  
 Obvykleji se jako základní třída určuje jiná předzpracovaná šablona. Základní šablona poskytuje běžné bloky textu, které mohou být proloženy textem z odvozených šablon. Lze použít bloky funkcí tříd `<#+ ... #>` k definici metod obsahujících textové fragmenty. Do základní šablony lze například umístit rámec výstupního textu a poskytnout tak virtuální metody, které lze v odvozených třídách přepsat:  
  
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
>  Pokud používáte `inherits` a `hostspecific` , definujte hostspecific = "trueFromBase" v odvozené třídě a host = "true" v základní třídě. To zabraňuje dvojité definici vlastnosti `Host` vlastnost v generovaném kódu.  
  
### <a name="inheritance-in-a-design-time-text-template"></a>Dědičnost v textové šabloně návrhu  
 Šablona textu v době návrhu je soubor, jehož **Custom Tool** je nastavena na **TextTemplatingFileGenerator**. Tato šablona vygeneruje výstupní soubor kódu nebo textu, který tvoří součást vaší [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] projektu. Při vygenerování výstupního souboru je šablona nejdříve přeložena do souboru programového mezikódu, který není obvykle vidět. `inherits` Atribut určuje základní třídu pro tento mezikód.  
  
 Návrhových textových šablon, můžete zadat libovolnou základní třídu, která je odvozena z <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation?displayProperty=fullName>. Použití `<#@assembly#>` směrnice pro načtení sestavení nebo projekt, který obsahuje základní třídy.  
  
 Další informace najdete v tématu ["Dědičnosti v textových šablon" v blogu Garetha Jonese](http://go.microsoft.com/fwlink/?LinkId=208373).  
  
## <a name="linepragmas-attribute"></a>Atribut LinePragmas  
 Příklad:  
 `linePragmas="false"`  
  
 Platné hodnoty:  
 `true` (výchozí)  
  
 `false`  
  
 Nastavení tohoto atributu na hodnotu false odstraní značky, které identifikují čísla řádků ve vygenerovaném kódu. To znamená, že kompilátor nahlásí jakékoli chyby pomocí čísel řádků generovaného kódu. To vám dává další možnosti ladění, protože se můžete rozhodnout pro ladění textové šablony nebo vygenerovaného kódu.  
  
 Tento atribut může také pomoci, pokud absolutní názvy souborů v direktivách programu způsobují rušivá sloučení ve správě zdrojového kódu.  
  
## <a name="visibility-attribute"></a>Atribut visibility  
 Příklad:  
 `visibility="internal"`  
  
 Platné hodnoty:  
 `public` (výchozí)  
  
 `internal`  
  
 V textové šabloně běhu se tímto nastavuje atribut visibility vygenerované třídy. Ve výchozím nastavení, je třída součástí veřejného rozhraní API kódu, ale tak, že nastavíte `visibility="internal"` abyste měli jistotu, že pouze váš kód může použít třídu generování textu.



