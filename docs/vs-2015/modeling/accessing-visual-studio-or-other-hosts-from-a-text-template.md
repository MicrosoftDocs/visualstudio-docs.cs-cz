---
title: Přístup k aplikaci Visual Studio 2015 nebo k jiným hostitelům z textové šablony | Microsoft Docs
titleSuffix: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: a68886da-7416-4785-8145-3796bb382cba
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 0e8cedc66d6b52f80239364a3e51b73e93a69aa4
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72655327"
---
# <a name="accessing-visual-studio-or-other-hosts-from-a-text-template"></a>Přístup k prostředí Visual Studio nebo k jiným hostitelům z textové šablony
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

V textové šabloně můžete použít metody a vlastnosti vystavené hostitelem, který šablonu spouští, například [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].

 To platí pro běžné textové šablony, nikoli předzpracované textové šablony.

## <a name="obtaining-access-to-the-host"></a>Získání přístupu k hostiteli

Nastavte `hostspecific="true"` v direktivě `template`. To vám umožní používat `this.Host`, které mají typ [ITextTemplatingEngineHost](/previous-versions/visualstudio/visual-studio-2012/bb126505(v=vs.110)). Tento typ má členy, které můžete použít například k překladu názvů souborů a k protokolování chyb.

### <a name="resolving-file-names"></a>Překládání názvů souborů
 Chcete-li najít úplnou cestu k souboru relativně vzhledem k textové šabloně, použijte tento příkaz. Host. ResolvePath ().

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

### <a name="displaying-error-messages"></a>Zobrazení chybových zpráv
 Tento příklad protokoluje zprávy při transformaci šablony. Pokud je hostitel [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], přidá se do okna chyby.

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

## <a name="using-the-visual-studio-api"></a>Použití rozhraní API sady Visual Studio
 Pokud spouštíte textovou šablonu v [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], můžete použít `this.Host` pro přístup ke službám poskytovaným [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] a jakýmkoli načteným balíčkům nebo rozšířením.

 Nastavte hostspecific = "true" a přetypování `this.Host` na <xref:System.IServiceProvider>.

 Tento příklad získá [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] rozhraní API <xref:EnvDTE.DTE> jako služba:

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

## <a name="using-hostspecific-with-template-inheritance"></a>Použití hostSpecific s děděním šablon
 Určete `hostspecific="trueFromBase"`, pokud použijete také atribut `inherits` a Pokud převezmete ze šablony, která určuje `hostspecific="true"`. Tím se zabrání upozornění kompilátoru na účinek, že vlastnost `Host` byla deklarována dvakrát.
