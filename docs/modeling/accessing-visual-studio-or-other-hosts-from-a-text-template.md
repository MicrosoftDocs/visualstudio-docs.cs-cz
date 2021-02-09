---
title: Přístup k prostředí Visual Studio nebo k jiným hostitelům z textové šablony
description: Naučte se, jak můžete použít metody a vlastnosti v textové šabloně, které jsou zpřístupněny hostitelem, který šablonu spouští.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 11/04/2016
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: ce008d0a14cbd75cf8a46599ff67bd9e799ee8ce
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99908880"
---
# <a name="access-visual-studio-or-other-hosts-from-a-text-template"></a>Přístup k aplikaci Visual Studio nebo k jiným hostitelům z textové šablony

V textové šabloně můžete použít metody a vlastnosti, které jsou zpřístupněny hostitelem, který šablonu spouští. Visual Studio je příkladem hostitele.

> [!NOTE]
> Můžete použít metody a vlastnosti hostitele v běžných textových šablonách, ale ne v *předzpracovaných* textových šablonách.

## <a name="obtain-access-to-the-host"></a>Získat přístup k hostiteli

Pro přístup k hostiteli nastavte `hostspecific="true"` v `template` direktivě. Nyní můžete použít `this.Host` , který má typ [ITextTemplatingEngineHost](/previous-versions/visualstudio/visual-studio-2012/bb126505(v=vs.110)). Typ [ITextTemplatingEngineHost](/previous-versions/visualstudio/visual-studio-2012/bb126505(v=vs.110)) má členy, které můžete použít k překladu názvů souborů a chyb protokolu, například.

### <a name="resolve-file-names"></a>Přeložit názvy souborů

Chcete-li najít úplnou cestu k souboru relativně k textové šabloně, použijte `this.Host.ResolvePath()` .

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

### <a name="display-error-messages"></a>Zobrazit chybové zprávy

Tento příklad protokoluje zprávy při transformaci šablony. Pokud je hostitel sady Visual Studio, chyby se přidají do **Seznam chyb**.

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

## <a name="use-the-visual-studio-api"></a>Použití rozhraní API sady Visual Studio

Pokud spouštíte textovou šablonu v aplikaci Visual Studio, můžete použít `this.Host` pro přístup ke službám poskytovaným aplikací Visual Studio a jakýmkoli načteným balíčkům nebo rozšířením.

Nastavte hostspecific = "true" a přetypování `this.Host` na <xref:System.IServiceProvider> .

Tento příklad načte rozhraní API sady Visual Studio <xref:EnvDTE.DTE> jako službu:

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

## <a name="use-hostspecific-with-template-inheritance"></a>Použití hostSpecific s děděním šablon

Určete `hostspecific="trueFromBase"` , zda také použijete `inherits` atribut, a Pokud převezmete ze šablony, která určuje `hostspecific="true"` . Pokud ne, může se zobrazit upozornění kompilátoru, že vlastnost `Host` byla deklarována dvakrát.
