---
title: Přístup k prostředí Visual Studio nebo k jiným hostitelům z textové šablony
titleSuffix: ''
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 9bb7bce5cb047018540599c9488fa4471dad2d1c
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53059295"
---
# <a name="access-visual-studio-or-other-hosts-from-a-text-template"></a>Přístup k sadě Visual Studio nebo k jiným hostitelům z textové šablony

V textové šabloně můžete použít metody a vlastnosti, které jsou vystavené na hostitele, který provede šablony. Visual Studio je příkladem hostitele.

> [!NOTE]
> V pravidelných textových šablon, ale ne v můžete použít hostitele metody a vlastnosti *předzpracovaná* textových šablon.

## <a name="obtain-access-to-the-host"></a>Získat přístup k hostiteli

Chcete-li získat přístup k hostiteli, nastavte `hostspecific="true"` v `template` směrnice. Nyní můžete pomocí `this.Host`, která má typ <xref:Microsoft.VisualStudio.TextTemplating.ITextTemplatingEngineHost>. <xref:Microsoft.VisualStudio.TextTemplating.ITextTemplatingEngineHost> Typ obsahuje členy, které používáte, třeba k překladu názvů souborů a protokoly chyb.

### <a name="resolve-file-names"></a>Přeložit názvy souborů

Chcete-li najít úplnou cestu k souboru relativně vzhledem k textu šablony, použijte `this.Host.ResolvePath()`.

```csharp
<#@ template hostspecific="true" language="C#" #>
<#@ output extension=".txt" #>
<#@ import namespace="System.IO" #>
<#
 // Find a path within the same project as the text template:
 string myFile = File.ReadAllText(this.Host.ResolvePath("MyFile.txt"));
#>
Content of myFile is:
<#= myFile #>
```

### <a name="display-error-messages"></a>Zobrazení chybových zpráv

V tomto příkladu se zaprotokoluje při transformaci šablony. Pokud je hostitel Visual Studio, chyby se přidají do **seznam chyb**.

```csharp
<#@ template hostspecific="true" language="C#" #>
<#@ output extension=".txt" #>
<#@ import namespace="System.CodeDom.Compiler" #>
<#
  string message = "test message";
  this.Host.LogErrors(new CompilerErrorCollection()
    { new CompilerError(
       this.Host.TemplateFile, // Identify the source of the error.
       0, 0, "0",   // Line, column, error ID.
       message) }); // Message displayed in error window.
#>
```

## <a name="use-the-visual-studio-api"></a>Pomocí sady Visual Studio rozhraní API

Pokud se spuštění textové šablony v sadě Visual Studio, můžete použít `this.Host` pro přístup ke službám poskytuje Visual Studio a všechny balíčky a rozšíření, která jsou načtena.

Nastavit hostspecific = "true" a přetypovat `this.Host` k <xref:System.IServiceProvider>.

V tomto příkladu získává rozhraní API sady Visual Studio, <xref:EnvDTE.DTE>, jako služba:

```csharp
<#@ template hostspecific="true" language="C#" #>
<#@ output extension=".txt" #>
<#@ assembly name="EnvDTE" #>
<#@ import namespace="EnvDTE" #>
<#
 IServiceProvider serviceProvider = (IServiceProvider)this.Host;
 DTE dte = serviceProvider.GetService(typeof(DTE)) as DTE;
#>
Number of projects in this solution: <#=  dte.Solution.Projects.Count #>
```

## <a name="use-hostspecific-with-template-inheritance"></a>Pomocí šablony dědičnosti hostSpecific

Zadejte `hostspecific="trueFromBase"` Pokud používáte také `inherits` atribut, a pokud je zděděn ze šablony, která určuje `hostspecific="true"`. Pokud to neuděláte, může se zobrazit upozornění, které kompilátor vlastnost `Host` byla deklarována dvakrát.