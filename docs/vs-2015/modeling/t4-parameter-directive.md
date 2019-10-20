---
title: T4 – direktiva parametru | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 1d590387-1d9d-40a5-a72c-65fae7a8bdf3
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7c1849cbccc1a903716ba94d02f47a339d6ce426
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72658562"
---
# <a name="t4-parameter-directive"></a>T4 – direktiva Parameter
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

V šabloně [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] text direktiva `parameter` deklaruje vlastnosti v kódu šablony, které jsou inicializovány z hodnot předaných z externího kontextu. Tyto hodnoty můžete nastavit, pokud píšete kód, který vyvolá transformaci textu.

## <a name="using-the-parameter-directive"></a>Použití direktivy parametru

```
<#@ parameter type="Full.TypeName" name="ParameterName" #>
```

 Direktiva `parameter` deklaruje vlastnosti v kódu šablony, které jsou inicializovány z hodnot předaných z vnějšího kontextu. Tyto hodnoty můžete nastavit, pokud píšete kód, který vyvolá transformaci textu. Hodnoty lze předávat buď ve slovníku `Session`, nebo v <xref:System.Runtime.Remoting.Messaging.CallContext>.

 Můžete deklarovat parametry libovolného typu vzdáleně. To znamená, že typ musí být deklarován s <xref:System.SerializableAttribute>, nebo musí být odvozen od <xref:System.MarshalByRefObject>. To umožňuje předání hodnot parametrů do domény aplikace, ve které je šablona zpracována.

 Můžete například napsat textovou šablonu s následujícím obsahem:

```
<#@ template language="C#" #>

<#@ parameter type="System.Int32" name="TimesToRepeat" #>

<# for (int i = 0; i < TimesToRepeat; i++) { #>
Line <#= i #>
<# } #>

```

## <a name="passing-parameter-values-to-a-template"></a>Předávání hodnot parametrů do šablony
 Pokud píšete rozšíření [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], jako je například příkaz nabídky nebo obslužná rutina události, můžete zpracovat šablonu pomocí služby text šablonování:

```csharp
// Get a service provider – how you do this depends on the context:
IServiceProvider serviceProvider = dte; // or dslDiagram.Store, for example
// Get the text template service:
ITextTemplating t4 = serviceProvider.GetService(typeof(STextTemplating)) as ITextTemplating;
ITextTemplatingSessionHost host = t4 as ITextTemplatingSessionHost;
// Create a Session in which to pass parameters:
host.Session = host.CreateSession();
// Add parameter values to the Session:
session["TimesToRepeat"] = 5;
// Process a text template:
string result = t4.ProcessTemplate("MyTemplateFile.t4",
  System.IO.File.ReadAllText("MyTemplateFile.t4"));

```

## <a name="passing-values-in-the-call-context"></a>Předávání hodnot v kontextu volání
 Hodnoty můžete alternativně předat jako logická data v <xref:System.Runtime.Remoting.Messaging.CallContext>.

 Následující příklad předává hodnoty pomocí obou metod:

```csharp
ITextTemplating t4 = this.Store.GetService(typeof(STextTemplating)) as ITextTemplating;
ITextTemplatingSessionHost host = t4 as ITextTemplatingSessionHost;
host.Session = host.CreateSession();
// Pass a value in Session:
host.Session["p1"] = 32;
// Pass another value in CallContext:
System.Runtime.Remoting.Messaging.CallContext.LogicalSetData("p2", "test");

// Process a small template inline:
string result = t4.ProcessTemplate("",
   "<#@parameter type=\"System.Int32\" name=\"p1\"#>"
 + "<#@parameter type=\"System.String\" name=\"p2\"#>"
 + "Test <#=p1#> <#=p2#>");

// Result value is:
//     Test 32 test

```

## <a name="passing-values-to-a-run-time-preprocessed-text-template"></a>Předávání hodnot do textové šablony běhu (předzpracované)
 Není obvykle nutné použít direktivu `<#@parameter#>` s textovými šablonami run-time (předzpracované). Místo toho můžete definovat další konstruktor nebo nastavitelnou vlastnost pro generovaný kód, pomocí kterého předáte hodnoty parametrů. Další informace najdete v tématu [generování textu v době běhu s textovými šablonami T4](../modeling/run-time-text-generation-with-t4-text-templates.md).

 Pokud však chcete použít `<#@parameter>` v šabloně běhu, můžete do ní předat hodnoty pomocí slovníku relace. Předpokládejme například, že jste soubor vytvořili jako předzpracovaná šablona s názvem `PreTextTemplate1`. Šablonu můžete vyvolat v programu pomocí následujícího kódu.

```csharp
PreTextTemplate1 t = new PreTextTemplate1();
t.Session = new Microsoft.VisualStudio.TextTemplating.TextTemplatingSession();
t.Session["TimesToRepeat"] = 5;
// Add other parameter values to t.Session here.
t.Initialize(); // Must call this to transfer values.
string resultText = t.TransformText();

```

## <a name="obtaining-arguments-from-texttemplateexe"></a>Získání argumentů z TextTemplate. exe

> [!IMPORTANT]
> Direktiva `parameter` nenačítá hodnoty nastavené v parametru `–a` nástroje `TextTransform.exe`. Chcete-li získat tyto hodnoty, nastavte `hostSpecific="true"` v direktivě `template` a použijte `this.Host.ResolveParameterValue("","","argName")`.
